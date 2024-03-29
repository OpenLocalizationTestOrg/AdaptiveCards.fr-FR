---
title: Kit de développement logiciel Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: e565606f4a112d4f1fa08e2989f392f1abf0887f
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732536"
---
# <a name="extensibility---android"></a>Extensibilité-Android

Le convertisseur Android peut être étendu pour prendre en charge plusieurs scénarios, notamment:
* [Analyse personnalisée des éléments de carte](#custom-parsing-of-card-elements)
* [Rendu personnalisé d’éléments de carte](#custom-rendering-of-card-elements)
* [Rendu personnalisé des actions](#custom-rendering-of-actions) (Depuis v 1.2)
* [Chargement d’images personnalisées](#custom-image-loading) (Depuis v 1.0.1)
* [Chargement de support personnalisé](#custom-media-loading) (Depuis v 1.1)

## <a name="custom-parsing-of-card-elements"></a>Analyse personnalisée des éléments de carte

Vous pouvez étendre l’analyseur pour prendre en charge les éléments de carte que vous avez définis. Par exemple, imaginons que nous ayons un nouveau type d’élément qui ressemble à ceci:
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

Les lignes suivantes montrent comment l’analyser dans un CardElement qui s’étend à partir de BaseCardElement:
```java
public class MyCustomCardElement extends BaseCardElement
{

    public MyCustomCardElement(CardElementType type) {
        super(type);
    }

    public String getMyTypeData()
    {
        return myTypeData;
    }

    public void setMyTypeData(String data)
    {
        myTypeData = data;
    }

    private String myTypeData;
}

public class MyCardElementParser extends BaseCardElementParser
{
    @Override
    public BaseCardElement Deserialize(ElementParserRegistration elementParserRegistration, ActionParserRegistration actionParserRegistration, JsonValue value)
    {
        MyCustomCardElement element = new CustomCardElement(CardElementType.Custom);
        element.SetElementTypeString("MyType");
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setMyTypeData(obj.getString("secret"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setMyTypeData("Failed");
        }
        return element;
    }
}
```

Il s’agit de l’enregistrement de l’analyseur et de l’obtention d’un objet AdaptiveCard qui contient l’élément personnalisé:
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

Le rendu de l’élément personnalisé est ensuite rendu

## <a name="custom-rendering-of-card-elements"></a>Rendu personnalisé d’éléments de carte

> [!IMPORTANT]
>
> **Liste des modifications avec rupture**
>
> [Modifications avec rupture pour v 1.2](#breaking-changes-for-v12)

Pour définir notre propre convertisseur personnalisé pour notre type, nous devons d’abord créer une classe qui s’étend ```BaseCardElementRenderer```de:
```java
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(Context context, FragmentManager fragmentManager, ViewGroup viewGroup, BaseCardElement baseCardElement, Vector<IInputHandler> inputActionHandlerList, ICardActionHandler cardActionHandler, HostConfig hostConfig, ContainerStyle containerStyle) {

        //Call findImplObj on baseCardElement to get the instance we returned at parse. We can then cast that object to our type
        CustomCardElement element = (CustomCardElement) baseCardElement.findImplObj();

        //Create some view and add it to the view group
        TextView textView = new TextView(context);
        textView.setText(element.getMyTypeData());
        textView.setAllCaps(true);
        viewGroup.addView(textView);

        //return the view
        return textView;
    }
}
```

Nous enregistrons ensuite ce convertisseur comme suit:
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a>Modifications avec rupture pour v 1.2

La ```render``` méthode a été modifiée pour inclure ```RenderedAdaptiveCard``` le paramètre ```ContainerStyle``` et a été modifiée pour un RenderArgs où le ContainerStyle est maintenant contenu, de sorte qu’une classe qui étend BaseCardElementRenderer doit se présenter comme suit

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a>Analyse personnalisée des actions de carte

De même que l’analyse d’éléments de carte personnalisés dans v 1.2, il est possible d’analyser des actions personnalisées. Par exemple, imaginons que nous ayons un nouveau type d’action qui ressemble à ceci:
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

Les lignes suivantes montrent comment l’analyser dans un ActionElement qui s’étend à partir de ```BaseActionElement```:
```java
public class MyActionElement extends BaseActionElement
{
    public MyActionElement(ActionType type) 
    {
        super(type);
    }

    public String getActionData()
    {
        return mActionData;
    }

    public void setActionData(String s)
    {
        mActionData = s;
    }

    private String mActionData;
    public static final String MyActionId = "myAction";
}

public class MyActionParser extends ActionElementParser
{
    @Override
    public BaseActionElement Deserialize(ParseContext context, JsonValue value)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setActionData(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setActionData("Failure");
        }
        return element;
    }

    @Override
    public BaseActionElement DeserializeFromString(ParseContext context, String jsonString)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        try {
            JSONObject obj = new JSONObject(jsonString);
            element.setBackwardString(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setBackwardString("Failure");
        }
        return element;
    }
}
```

Et les lignes suivantes montrent comment inscrire l’analyseur et récupérer un objet AdaptiveCard qui contient l’élément d’action personnalisé:
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

Le prochain rendu de l’action personnalisée

## <a name="custom-rendering-of-actions"></a>Rendu personnalisé des actions

Pour définir notre propre convertisseur d’action personnalisé pour notre type, nous devons d’abord créer une classe qui s' ```BaseActionElementRenderer```étend de:
```java
public class MyActionRenderer extends BaseActionElementRenderer
{
    @Override
    public Button render(RenderedAdaptiveCard renderedCard,
                         Context context,
                         FragmentManager fragmentManager,
                         ViewGroup viewGroup,
                         BaseActionElement baseActionElement,
                         ICardActionHandler cardActionHandler,
                         HostConfig hostConfig,
                         RenderArgs renderArgs)
    {
        Button myActionButton = new Button(context);

        CustomActionElement customAction = (CustomActionElement) baseActionElement.findImplObj();

        myActionButton.setBackgroundColor(getResources().getColor(R.color.greenActionColor));
        myActionButton.setText(customAction.getMessage());
        myActionButton.setAllCaps(false);
        myActionButton.setOnClickListener(new BaseActionElementRenderer.ActionOnClickListener(renderedCard, baseActionElement, cardActionHandler));

        viewGroup.addView(myActionButton);

        return myActionButton;
    }
}
```

Nous enregistrons ensuite ce convertisseur comme suit:
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a>Rendu personnalisé des actions

[!IMPORTANT]
> Les modifications apportées au rendu personnalisé des actions sont planifiées pour v 1.2 mais ne sont pas encore terminées

## <a name="custom-image-loading"></a>Chargement d’images personnalisées

### <a name="ionlineimageloader"></a>IOnlineImageLoader

> [!IMPORTANT]
> **Un seul IOnlineImageLoader peut être inscrit et il est prioritaire par rapport à la méthode par défaut de récupération des images.**

Pour permettre aux développeurs d’accéder à des images qui n’ont pas pu être téléchargées ou récupérées à partir d’une source en ligne ou qui ont nécessité des étapes précédentes avant qu’elles puissent être récupérées, le IOnlineImageLoader a été ajouté pour résoudre ce type de situation. Pour implémenter un OnlineImageLoader, vous devez implémenter la méthode uniquement 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

Voici un exemple de OnlineImageLoader qui modifie toutes les images d’une image CAT

```java
public class OnlineImageLoader implements IOnlineImageLoader
{
    public OnlineImageLoader(){}

    @Override
    public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
    {
        String catImnageUri = "http://adaptivecards.io/content/cats/1.png";
        byte[] bytes = HttpRequestHelper.get(catImnageUri);
        if (bytes == null)
        {
            throw new IOException("Failed to retrieve content from " + catImnageUri);
        }

        Bitmap bitmap = BitmapFactory.decodeByteArray(bytes, 0, bytes.length);

        if (bitmap == null)
        {
            throw new IOException("Failed to convert content to bitmap: " + new String(bytes));
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

Enfin, pour inscrire ce chargeur d’image, vous devez ajouter cette ligne uniquement à votre code.

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a>IResourceResolver (deprecates IOnlineImageLoader)

Pour v 1.2, la prise en charge de la ResourceResolvers complète a été ajoutée au convertisseur Android. L’implémentation d’un programme de résolution de ressources est très similaire à celle d’un IOnlineImageLoader, mais le fait d’avoir ResourceResolvers permet à un développeur d’ajouter plusieurs façons de récupérer des images à partir de n’importe quel type de source dans une seule carte. pour cela, il suffit de lier chaque ResourceResolver à un préfixe unique qui sera interrogé lors de la tentative de récupération d’une image. 

Vous pouvez implémenter un ResourceResolver similaire à celui-ci

```java
public class ResourceResolver implements IResourceResolver
{
    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);
        byte[] decodedByteArray = Util.getBytes(decodedDataUri);
        bitmap = BitmapFactory.decodeByteArray(decodedByteArray, 0, decodedByteArray.length);

        return new HttpRequestResult<>(bitmap);
    }

    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);

        if (uri.startsWith("data:image/svg")) {
            String svgString = AdaptiveBase64Util.ExtractDataFromUri(uri);
            String decodedSvgString = URLDecoder.decode(svgString, "UTF-8");
            Sharp sharp = Sharp.loadString(decodedSvgString);
            Drawable drawable = sharp.getDrawable();
            bitmap = ImageUtil.drawableToBitmap(drawable, maxWidth);
        }
        else
        {
            try
            {
                return genericImageLoaderAsync.loadDataUriImage(uri);
            }
            catch (Exception e)
            {
                return new HttpRequestResult<>(e);
            }
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

Comme mentionné précédemment, vous pouvez inscrire plusieurs ResourceResolvers, pour inscrire un ResourceResolver, vous pouvez le faire

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a>Transformation d’un IOnlineImageLoader en IResourceResolver 

La transformation d’un IOnlineImageLoader en IResourceResolver est une tâche relativement simple, car les méthodes de la dernière tentative de conservation de la même manière que le IOnlineImageLoader le permettent.

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

Comme vous pouvez le voir, les modifications les plus importantes sont

* ```loadOnlineImage(String, GenericImageLoaderAsync)```a été renommé en```resolveImageResource(String, GenericImageLoaderAsync)```
* une surcharge pour ```resolveImageResource(String, GenericImageLoaderAsync)``` a été ajoutée ```resolveImageResource(String, GenericImageLoaderAsync, int)``` comme afin de prendre en charge les scénarios où la largeur maximale est requise

## <a name="custom-media-loading"></a>Chargement de support personnalisé

> [!IMPORTANT]
> **N’oubliez pas ```IOnlineMediaLoader``` queaétéajoutéauniveaudel’API23ouAndroidM```MediaDataSource```**

Outre l’inclusion de l’élément multimédia, a également été l’inclusion de l’interface IOnlineMediaLoader, qui permet aux développeurs de substituer le [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) utilisé pour l’élément mediaPlayer sous-jacent. **(Requires android M)**

La première chose à faire est de créer une classe qui implémente IOnlineImageLoader

```java
@RequiresApi(api = Build.VERSION_CODES.M)
public class OnlineMediaLoader implements IOnlineMediaLoader
{
    /* This class checks if the media source exists */
    public class OnlineFileAvailableChecker extends AsyncTask<String, Void, Boolean>
    {
        public OnlineFileAvailableChecker(String uri)
        {
            m_uri = uri;
        }

        @Override
        protected Boolean doInBackground(String... strings) {
            // if the provided uri is a valid uri or is valid with the resource resolver, then use that
            // otherwise, try to get the media from a local file
            try
            {
                HttpRequestHelper.query(m_uri);
                return true;
            }
            catch (Exception e)
            {
                // Do nothing if the media was not found at all
                e.printStackTrace();
                return false;
            }
        }

        private String m_uri;
   }

       
   @Override
   public MediaDataSource loadOnlineMedia(MediaSourceVector mediaSources, IMediaDataSourceOnPreparedListener mediaDataSourceOnPreparedListener)
   {
       final long mediaSourcesSize = mediaSources.size();
       for(int i = 0; i < mediaSourcesSize; i++)
       {
           String mediaUri = mediaSources.get(i).GetUrl();

           OnlineFileAvailableChecker checker = new OnlineFileAvailableChecker(mediaUri);
           try
           {
               Boolean fileExists = checker.execute("").get();
               if(fileExists)
               {
                   return new MediaDataSourceImpl(mediaUri, mediaDataSourceOnPreparedListener);
               }
           }
           catch (Exception e) { }
       }
       return null;
    }
}
```

Une fois cette classe implémentée, vous pouvez inscrire votre classe OnlineMediaLoader en ajoutant 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```

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
# <a name="extensibility---android"></a><span data-ttu-id="06c1f-102">Extensibilité-Android</span><span class="sxs-lookup"><span data-stu-id="06c1f-102">Extensibility - Android</span></span>

<span data-ttu-id="06c1f-103">Le convertisseur Android peut être étendu pour prendre en charge plusieurs scénarios, notamment:</span><span class="sxs-lookup"><span data-stu-id="06c1f-103">The Android renderer can be extended to support multiple scenarios including:</span></span>
* [<span data-ttu-id="06c1f-104">Analyse personnalisée des éléments de carte</span><span class="sxs-lookup"><span data-stu-id="06c1f-104">Custom Parsing of Card Elements</span></span>](#custom-parsing-of-card-elements)
* [<span data-ttu-id="06c1f-105">Rendu personnalisé d’éléments de carte</span><span class="sxs-lookup"><span data-stu-id="06c1f-105">Custom Rendering of Card Elements</span></span>](#custom-rendering-of-card-elements)
* <span data-ttu-id="06c1f-106">[Rendu personnalisé des actions](#custom-rendering-of-actions) (Depuis v 1.2)</span><span class="sxs-lookup"><span data-stu-id="06c1f-106">[Custom Rendering of Actions](#custom-rendering-of-actions) (Since v1.2)</span></span>
* <span data-ttu-id="06c1f-107">[Chargement d’images personnalisées](#custom-image-loading) (Depuis v 1.0.1)</span><span class="sxs-lookup"><span data-stu-id="06c1f-107">[Custom Image Loading](#custom-image-loading) (Since v1.0.1)</span></span>
* <span data-ttu-id="06c1f-108">[Chargement de support personnalisé](#custom-media-loading) (Depuis v 1.1)</span><span class="sxs-lookup"><span data-stu-id="06c1f-108">[Custom Media Loading](#custom-media-loading) (Since v1.1)</span></span>

## <a name="custom-parsing-of-card-elements"></a><span data-ttu-id="06c1f-109">Analyse personnalisée des éléments de carte</span><span class="sxs-lookup"><span data-stu-id="06c1f-109">Custom Parsing of Card Elements</span></span>

<span data-ttu-id="06c1f-110">Vous pouvez étendre l’analyseur pour prendre en charge les éléments de carte que vous avez définis.</span><span class="sxs-lookup"><span data-stu-id="06c1f-110">You may extend the parser to support card elements that you have defined.</span></span> <span data-ttu-id="06c1f-111">Par exemple, imaginons que nous ayons un nouveau type d’élément qui ressemble à ceci:</span><span class="sxs-lookup"><span data-stu-id="06c1f-111">For example, say we have a new element type that looks like this:</span></span>
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

<span data-ttu-id="06c1f-112">Les lignes suivantes montrent comment l’analyser dans un CardElement qui s’étend à partir de BaseCardElement:</span><span class="sxs-lookup"><span data-stu-id="06c1f-112">Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:</span></span>
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

<span data-ttu-id="06c1f-113">Il s’agit de l’enregistrement de l’analyseur et de l’obtention d’un objet AdaptiveCard qui contient l’élément personnalisé:</span><span class="sxs-lookup"><span data-stu-id="06c1f-113">And this is how to register the parser and get an AdaptiveCard object that contains the custom element:</span></span>
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

<span data-ttu-id="06c1f-114">Le rendu de l’élément personnalisé est ensuite rendu</span><span class="sxs-lookup"><span data-stu-id="06c1f-114">Next comes rendering the custom element</span></span>

## <a name="custom-rendering-of-card-elements"></a><span data-ttu-id="06c1f-115">Rendu personnalisé d’éléments de carte</span><span class="sxs-lookup"><span data-stu-id="06c1f-115">Custom Rendering of Card Elements</span></span>

> [!IMPORTANT]
>
> <span data-ttu-id="06c1f-116">**Liste des modifications avec rupture**</span><span class="sxs-lookup"><span data-stu-id="06c1f-116">**List of Breaking Changes**</span></span>
>
> [<span data-ttu-id="06c1f-117">Modifications avec rupture pour v 1.2</span><span class="sxs-lookup"><span data-stu-id="06c1f-117">Breaking changes for v1.2</span></span>](#breaking-changes-for-v12)

<span data-ttu-id="06c1f-118">Pour définir notre propre convertisseur personnalisé pour notre type, nous devons d’abord créer une classe qui s’étend ```BaseCardElementRenderer```de:</span><span class="sxs-lookup"><span data-stu-id="06c1f-118">To define our own custom renderer for our type, we must first create a class that extends from ```BaseCardElementRenderer```:</span></span>
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

<span data-ttu-id="06c1f-119">Nous enregistrons ensuite ce convertisseur comme suit:</span><span class="sxs-lookup"><span data-stu-id="06c1f-119">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a><span data-ttu-id="06c1f-120">Modifications avec rupture pour v 1.2</span><span class="sxs-lookup"><span data-stu-id="06c1f-120">Breaking changes for v1.2</span></span>

<span data-ttu-id="06c1f-121">La ```render``` méthode a été modifiée pour inclure ```RenderedAdaptiveCard``` le paramètre ```ContainerStyle``` et a été modifiée pour un RenderArgs où le ContainerStyle est maintenant contenu, de sorte qu’une classe qui étend BaseCardElementRenderer doit se présenter comme suit</span><span class="sxs-lookup"><span data-stu-id="06c1f-121">The ```render``` method was changed to include the ```RenderedAdaptiveCard``` parameter and ```ContainerStyle``` was changed for a RenderArgs where the ContainerStyle is now contained so a class that extends BaseCardElementRenderer should look like this</span></span>

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a><span data-ttu-id="06c1f-122">Analyse personnalisée des actions de carte</span><span class="sxs-lookup"><span data-stu-id="06c1f-122">Custom Parsing of Card Actions</span></span>

<span data-ttu-id="06c1f-123">De même que l’analyse d’éléments de carte personnalisés dans v 1.2, il est possible d’analyser des actions personnalisées.</span><span class="sxs-lookup"><span data-stu-id="06c1f-123">Similarly to parsing custom card elements in v1.2 the possibility to parse custom actions was introduced.</span></span> <span data-ttu-id="06c1f-124">Par exemple, imaginons que nous ayons un nouveau type d’action qui ressemble à ceci:</span><span class="sxs-lookup"><span data-stu-id="06c1f-124">For example, say we have a new action type that looks like this:</span></span>
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

<span data-ttu-id="06c1f-125">Les lignes suivantes montrent comment l’analyser dans un ActionElement qui s’étend à partir de ```BaseActionElement```:</span><span class="sxs-lookup"><span data-stu-id="06c1f-125">Then the following lines demonstrate how to parse it into a ActionElement that extends from the ```BaseActionElement```:</span></span>
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

<span data-ttu-id="06c1f-126">Et les lignes suivantes montrent comment inscrire l’analyseur et récupérer un objet AdaptiveCard qui contient l’élément d’action personnalisé:</span><span class="sxs-lookup"><span data-stu-id="06c1f-126">And the next lines demonstrate how to register the parser and get an AdaptiveCard object that contains the custom action element:</span></span>
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="06c1f-127">Le prochain rendu de l’action personnalisée</span><span class="sxs-lookup"><span data-stu-id="06c1f-127">Next comes rendering the custom action</span></span>

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="06c1f-128">Rendu personnalisé des actions</span><span class="sxs-lookup"><span data-stu-id="06c1f-128">Custom Rendering of Actions</span></span>

<span data-ttu-id="06c1f-129">Pour définir notre propre convertisseur d’action personnalisé pour notre type, nous devons d’abord créer une classe qui s' ```BaseActionElementRenderer```étend de:</span><span class="sxs-lookup"><span data-stu-id="06c1f-129">To define our own custom action renderer for our type, we must first create a class that extends from ```BaseActionElementRenderer```:</span></span>
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

<span data-ttu-id="06c1f-130">Nous enregistrons ensuite ce convertisseur comme suit:</span><span class="sxs-lookup"><span data-stu-id="06c1f-130">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="06c1f-131">Rendu personnalisé des actions</span><span class="sxs-lookup"><span data-stu-id="06c1f-131">Custom rendering of actions</span></span>

[!IMPORTANT]
> <span data-ttu-id="06c1f-132">Les modifications apportées au rendu personnalisé des actions sont planifiées pour v 1.2 mais ne sont pas encore terminées</span><span class="sxs-lookup"><span data-stu-id="06c1f-132">Changes to the custom rendering of actions are planned for v1.2 but are not completed yet</span></span>

## <a name="custom-image-loading"></a><span data-ttu-id="06c1f-133">Chargement d’images personnalisées</span><span class="sxs-lookup"><span data-stu-id="06c1f-133">Custom image loading</span></span>

### <a name="ionlineimageloader"></a><span data-ttu-id="06c1f-134">IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="06c1f-134">IOnlineImageLoader</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06c1f-135">**Un seul IOnlineImageLoader peut être inscrit et il est prioritaire par rapport à la méthode par défaut de récupération des images.**</span><span class="sxs-lookup"><span data-stu-id="06c1f-135">**Only one IOnlineImageLoader can be registered and it takes precedence against the default way of retrieving images**</span></span>

<span data-ttu-id="06c1f-136">Pour permettre aux développeurs d’accéder à des images qui n’ont pas pu être téléchargées ou récupérées à partir d’une source en ligne ou qui ont nécessité des étapes précédentes avant qu’elles puissent être récupérées, le IOnlineImageLoader a été ajouté pour résoudre ce type de situation.</span><span class="sxs-lookup"><span data-stu-id="06c1f-136">In order to allow developers to get images that could not just be downloaded or retrieved from an online source or required previous steps before they could be retrieved, the IOnlineImageLoader was added to solve this kind of situations.</span></span> <span data-ttu-id="06c1f-137">Pour implémenter un OnlineImageLoader, vous devez implémenter la méthode uniquement</span><span class="sxs-lookup"><span data-stu-id="06c1f-137">To implement an OnlineImageLoader you must only implement the method</span></span> 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

<span data-ttu-id="06c1f-138">Voici un exemple de OnlineImageLoader qui modifie toutes les images d’une image CAT</span><span class="sxs-lookup"><span data-stu-id="06c1f-138">Here's an example of an OnlineImageLoader which changes all images for a cat image</span></span>

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

<span data-ttu-id="06c1f-139">Enfin, pour inscrire ce chargeur d’image, vous devez ajouter cette ligne uniquement à votre code.</span><span class="sxs-lookup"><span data-stu-id="06c1f-139">Finally, to register this image loader, you must only add this line to your code.</span></span>

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a><span data-ttu-id="06c1f-140">IResourceResolver (deprecates IOnlineImageLoader)</span><span class="sxs-lookup"><span data-stu-id="06c1f-140">IResourceResolver (deprecates IOnlineImageLoader)</span></span>

<span data-ttu-id="06c1f-141">Pour v 1.2, la prise en charge de la ResourceResolvers complète a été ajoutée au convertisseur Android.</span><span class="sxs-lookup"><span data-stu-id="06c1f-141">For v1.2, the support for full ResourceResolvers was added to the android renderer.</span></span> <span data-ttu-id="06c1f-142">L’implémentation d’un programme de résolution de ressources est très similaire à celle d’un IOnlineImageLoader, mais le fait d’avoir ResourceResolvers permet à un développeur d’ajouter plusieurs façons de récupérer des images à partir de n’importe quel type de source dans une seule carte. pour cela, il suffit de lier chaque ResourceResolver à un préfixe unique qui sera interrogé lors de la tentative de récupération d’une image.</span><span class="sxs-lookup"><span data-stu-id="06c1f-142">The implementation of a resource resolver is really similar to that of a IOnlineImageLoader but having ResourceResolvers allows a developer to add multiple ways to retrieve images from any kind of source in a single card, this is done by linking each ResourceResolver to a unique prefix which will be queried when trying to retrieve an image.</span></span> 

<span data-ttu-id="06c1f-143">Vous pouvez implémenter un ResourceResolver similaire à celui-ci</span><span class="sxs-lookup"><span data-stu-id="06c1f-143">You can implement a ResourceResolver similar to this</span></span>

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

<span data-ttu-id="06c1f-144">Comme mentionné précédemment, vous pouvez inscrire plusieurs ResourceResolvers, pour inscrire un ResourceResolver, vous pouvez le faire</span><span class="sxs-lookup"><span data-stu-id="06c1f-144">As mentioned previously, you can register multiple ResourceResolvers, to register a ResourceResolver you can do this</span></span>

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a><span data-ttu-id="06c1f-145">Transformation d’un IOnlineImageLoader en IResourceResolver</span><span class="sxs-lookup"><span data-stu-id="06c1f-145">Transforming an IOnlineImageLoader to an IResourceResolver</span></span> 

<span data-ttu-id="06c1f-146">La transformation d’un IOnlineImageLoader en IResourceResolver est une tâche relativement simple, car les méthodes de la dernière tentative de conservation de la même manière que le IOnlineImageLoader le permettent.</span><span class="sxs-lookup"><span data-stu-id="06c1f-146">Transforming an IOnlineImageLoader to an IResourceResolver is a fairly easy task as the methods for the latter were tried to keep as similar as the IOnlineImageLoader as possible</span></span>

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

<span data-ttu-id="06c1f-147">Comme vous pouvez le voir, les modifications les plus importantes sont</span><span class="sxs-lookup"><span data-stu-id="06c1f-147">As you can see, the biggest changes are</span></span>

* <span data-ttu-id="06c1f-148">```loadOnlineImage(String, GenericImageLoaderAsync)```a été renommé en```resolveImageResource(String, GenericImageLoaderAsync)```</span><span class="sxs-lookup"><span data-stu-id="06c1f-148">```loadOnlineImage(String, GenericImageLoaderAsync)``` was renamed to ```resolveImageResource(String, GenericImageLoaderAsync)```</span></span>
* <span data-ttu-id="06c1f-149">une surcharge pour ```resolveImageResource(String, GenericImageLoaderAsync)``` a été ajoutée ```resolveImageResource(String, GenericImageLoaderAsync, int)``` comme afin de prendre en charge les scénarios où la largeur maximale est requise</span><span class="sxs-lookup"><span data-stu-id="06c1f-149">an overload for ```resolveImageResource(String, GenericImageLoaderAsync)``` was added as ```resolveImageResource(String, GenericImageLoaderAsync, int)``` in order to support scenarios where the max width is required</span></span>

## <a name="custom-media-loading"></a><span data-ttu-id="06c1f-150">Chargement de support personnalisé</span><span class="sxs-lookup"><span data-stu-id="06c1f-150">Custom Media Loading</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06c1f-151">**N’oubliez pas ```IOnlineMediaLoader``` queaétéajoutéauniveaudel’API23ouAndroidM```MediaDataSource```**</span><span class="sxs-lookup"><span data-stu-id="06c1f-151">**Remember ```IOnlineMediaLoader``` requires ```MediaDataSource``` which was added in API level 23 or Android M**</span></span>

<span data-ttu-id="06c1f-152">Outre l’inclusion de l’élément multimédia, a également été l’inclusion de l’interface IOnlineMediaLoader, qui permet aux développeurs de substituer le [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) utilisé pour l’élément mediaPlayer sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="06c1f-152">Along with the inclusion of the media element, also was the inclusion of the IOnlineMediaLoader interface which allows developers to override the [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) used for the underlying mediaPlayer element.</span></span> <span data-ttu-id="06c1f-153">**(Requires android M)**</span><span class="sxs-lookup"><span data-stu-id="06c1f-153">**(Requires android M)**</span></span>

<span data-ttu-id="06c1f-154">La première chose à faire est de créer une classe qui implémente IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="06c1f-154">The first needed thing to do is creating a class that implements IOnlineImageLoader</span></span>

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

<span data-ttu-id="06c1f-155">Une fois cette classe implémentée, vous pouvez inscrire votre classe OnlineMediaLoader en ajoutant</span><span class="sxs-lookup"><span data-stu-id="06c1f-155">Once this class has been implemented, you can register your OnlineMediaLoader class by adding</span></span> 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
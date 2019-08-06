---
title: Outils cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: f0c5a61d3406e1defffefc575ee0a6ec78fba93d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733026"
---
# <a name="tools-and-samples"></a><span data-ttu-id="7fb5a-102">Outils et exemples</span><span class="sxs-lookup"><span data-stu-id="7fb5a-102">Tools and Samples</span></span>

## <a name="card-designer"></a><span data-ttu-id="7fb5a-103">Concepteur de cartes</span><span class="sxs-lookup"><span data-stu-id="7fb5a-103">Card Designer</span></span> 

<span data-ttu-id="7fb5a-104">Vous avez besoin d’un outil pour concevoir vos cartes?</span><span class="sxs-lookup"><span data-stu-id="7fb5a-104">Need for a tool to design your cards?</span></span> <span data-ttu-id="7fb5a-105">Ne cherchez pas plus loin que le concepteur de cartes adaptatives basé sur le navigateur à l’adresse[https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="7fb5a-105">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="7fb5a-106">[![capture d’écran du concepteur](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="7fb5a-106">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

### <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="7fb5a-107">Incorporer le concepteur dans votre application</span><span class="sxs-lookup"><span data-stu-id="7fb5a-107">Embed the designer into your app</span></span>

<span data-ttu-id="7fb5a-108">Mais pourquoi y envoyer vos utilisateurs quand vous pouvez **incorporer le concepteur de cartes directement dans votre application Web** à l’aide de notre bibliothèque JavaScript.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-108">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="7fb5a-109">Consultez le package [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) pour commencer.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-109">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

## <a name="schema-validation"></a><span data-ttu-id="7fb5a-110">Validation de schéma</span><span class="sxs-lookup"><span data-stu-id="7fb5a-110">Schema validation</span></span>

<span data-ttu-id="7fb5a-111">La validation de schéma est un moyen puissant de faciliter la création d’outils et de les activer.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-111">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

<span data-ttu-id="7fb5a-112">Nous avons fourni un [fichier de schéma JSON](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) complet pour la modification et la validation des cartes adaptatives dans JSON.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-112">We have provided a complete [JSON Schema file](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) for editing and validating adaptive cards in json.</span></span> <span data-ttu-id="7fb5a-113">Notez que la version de l’URL de schéma est une version plus récente de cartes adaptatives ayant une URL correspondante.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-113">Note that the schema URL is versioned, newer versions of Adaptive Cards will have a corresponding URL.</span></span>

<span data-ttu-id="7fb5a-114">Dans Visual Studio et Visual Studio code vous pouvez obtenir une fonctionnalité IntelliSense automatique en `$schema` incluant une référence.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-114">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![bad](media/tools/invalidjson1.png)

![saisie semi-automatique](media/tools/autocomplete.png)

## <a name="example"></a><span data-ttu-id="7fb5a-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="7fb5a-117">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a><span data-ttu-id="7fb5a-118">Extension de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7fb5a-118">Visual Studio Code Extension</span></span>

<span data-ttu-id="7fb5a-119">Nous avons créé une extension Visual Studio code qui vous permet de visualiser la carte que vous modifiez en temps réel dans l’éditeur lui-même.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-119">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![extension](media/tools/vscode-extension.png)

<span data-ttu-id="7fb5a-121">Pour installer, ouvrez le Marketplace des extensions et recherchez la visionneuse de **cartes adaptatives**.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-121">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![marketplace](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="7fb5a-123">Usage</span><span class="sxs-lookup"><span data-stu-id="7fb5a-123">Usage</span></span>

<span data-ttu-id="7fb5a-124">Lorsque vous modifiez un fichier. JSON avec une propriété de carte `$schema` adaptative, vous pouvez l’afficher à l’aide `Ctrl+Shift+V A`de.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-124">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="7fb5a-125">Options</span><span class="sxs-lookup"><span data-stu-id="7fb5a-125">Options</span></span>

<span data-ttu-id="7fb5a-126">Le paramètre de Visual Studio Code suivant est disponible pour la visionneuse AdaptiveCards.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-126">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="7fb5a-127">Cela peut être défini dans les paramètres utilisateur ou les paramètres de l’espace de travail.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-127">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="7fb5a-128">Exemple de visualiseur WPF</span><span class="sxs-lookup"><span data-stu-id="7fb5a-128">WPF Visualizer Sample</span></span>

<span data-ttu-id="7fb5a-129">L' [exemple de projet de visualiseur WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) vous permet de visualiser des cartes à l’aide de WPF/XAML sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-129">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="7fb5a-130">Un `hostconfig` éditeur est intégré pour la modification et l’affichage des paramètres de configuration de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-130">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="7fb5a-131">Enregistrez ces paramètres en tant que JSON pour les utiliser dans le rendu de votre application.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-131">Save these settings as a JSON to use them in rendering in your application.</span></span>

![visualiseur WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="7fb5a-133">Exemple de ImageRender WPF</span><span class="sxs-lookup"><span data-stu-id="7fb5a-133">WPF ImageRender Sample</span></span>

<span data-ttu-id="7fb5a-134">L' [exemple de projet ImageRender](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) transforme toute carte en un format png à partir de la ligne de commande à l’aide de WPF.</span><span class="sxs-lookup"><span data-stu-id="7fb5a-134">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 

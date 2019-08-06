---
title: Rendre une carte-SDK WPF .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 1445754d968ee531dc1e2b1816df1189c286d479
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732716"
---
# <a name="render-a-card---net-wpf"></a><span data-ttu-id="e595d-102">Rendre une carte-.NET WPF</span><span class="sxs-lookup"><span data-stu-id="e595d-102">Render a card - .NET WPF</span></span>

<span data-ttu-id="e595d-103">Voici comment afficher une carte à l’aide du kit de développement logiciel (SDK) WPF .NET.</span><span class="sxs-lookup"><span data-stu-id="e595d-103">Here's how to render a card using the .NET WPF SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="e595d-104">**`Media`avec les URL HTTPs ne fonctionneront pas dans WPF**</span><span class="sxs-lookup"><span data-stu-id="e595d-104">**`Media` with HTTPS URLs will not work in WPF**</span></span>
> 
> <span data-ttu-id="e595d-105">En raison d’un [bogue dans le contrôle MEDIAELEMENT WPF](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) , nous ne sommes pas en mesure d’afficher le média fourni via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e595d-105">Due to a [bug in the WPF MediaElement control](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) we aren't able to render media that is served via HTTPS.</span></span> <span data-ttu-id="e595d-106">Vous devez utiliser des URL http dans `Media` l’élément jusqu’à ce que ce soit traité.</span><span class="sxs-lookup"><span data-stu-id="e595d-106">You should use HTTP URLs in the `Media` element until this is addressed.</span></span>  

## <a name="instantiate-a-renderer"></a><span data-ttu-id="e595d-107">Instancier un convertisseur</span><span class="sxs-lookup"><span data-stu-id="e595d-107">Instantiate a renderer</span></span>

<span data-ttu-id="e595d-108">Créez une instance de la bibliothèque de convertisseurs.</span><span class="sxs-lookup"><span data-stu-id="e595d-108">Create an instance of the renderer library.</span></span> 

```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Wpf;
// ...

// Create a card renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// If using the Xceed package, enable the enhanced input
renderer.UseXceedElementRenderers();

// For fun, check the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion;
```

## <a name="render-a-card-to-xaml"></a><span data-ttu-id="e595d-109">Rendu d’une carte en XAML</span><span class="sxs-lookup"><span data-stu-id="e595d-109">Render a card to XAML</span></span>

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard("1.0")
{
    Body = { new AdaptiveTextBlock() { Text = "Hello World" } }
};

try
{
    // Render the card
    RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

    // Get the FrameworkElement
    // Add this to your app's UI somewhere
    FrameworkElement fe = renderedCard.FrameworkElement;

    // (Optional) Check for any renderer warnings
    // This includes things like an unknown element type found in the card
    // Or the card exceeded the maximum number of supported actions, etc
    IList<AdaptiveWarning> warnings = renderedCard.Warnings;
}
catch(AdaptiveException ex)
{
    // Failed rendering
}
```


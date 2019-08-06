---
title: Rendre une carte-SDK HTML .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 0280e37506e1034572f518b1f596e8f1a3bb30be
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732811"
---
# <a name="render-a-card---net-html"></a><span data-ttu-id="60669-102">Rendre une carte-.NET HTML</span><span class="sxs-lookup"><span data-stu-id="60669-102">Render a card - .NET HTML</span></span>

<span data-ttu-id="60669-103">Voici comment afficher une carte à l’aide du kit de développement logiciel (SDK) HTML .NET.</span><span class="sxs-lookup"><span data-stu-id="60669-103">Here's how to render a card using the .NET HTML SDK.</span></span>

## <a name="instantiate-a-renderer"></a><span data-ttu-id="60669-104">Instancier un convertisseur</span><span class="sxs-lookup"><span data-stu-id="60669-104">Instantiate a renderer</span></span>

<span data-ttu-id="60669-105">L’étape suivante consiste à créer une instance du convertisseur.</span><span class="sxs-lookup"><span data-stu-id="60669-105">The next step is to create an instance of the renderer.</span></span> 

```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Html;
// ... 

// Create a card renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// For fun, check the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion; // 1.0
```

## <a name="render-a-card-to-html"></a><span data-ttu-id="60669-106">Rendu d’une carte en HTML</span><span class="sxs-lookup"><span data-stu-id="60669-106">Render a card to HTML</span></span>

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard()
{
    Body = { new AdaptiveTextBlock() { Text = "Hello World" } }
};

try
{
    // Render the card
    RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

    // Get the output HTML 
    HtmlTag html = renderedCard.Html;

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

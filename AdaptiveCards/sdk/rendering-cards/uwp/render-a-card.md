---
title: Rendu d’une carte-Kit de développement logiciel (SDK) UWP
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d7e101bbabfccf162797a3a8e154028f29bdc84b
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732546"
---
# <a name="render-a-card---uwp"></a><span data-ttu-id="4ef96-102">Rendu d’une carte UWP</span><span class="sxs-lookup"><span data-stu-id="4ef96-102">Render a card - UWP</span></span>

<span data-ttu-id="4ef96-103">Voici comment afficher une carte à l’aide du kit de développement logiciel (SDK) UWP.</span><span class="sxs-lookup"><span data-stu-id="4ef96-103">Here's how to render a card using the UWP SDK.</span></span>

## <a name="create-an-instance-of-your-renderer"></a><span data-ttu-id="4ef96-104">Créer une instance de votre convertisseur</span><span class="sxs-lookup"><span data-stu-id="4ef96-104">Create an instance of your renderer</span></span>

<span data-ttu-id="4ef96-105">Créez une instance de la bibliothèque de convertisseurs.</span><span class="sxs-lookup"><span data-stu-id="4ef96-105">Create an instance of the renderer library.</span></span> 

```csharp
using AdaptiveCards.Rendering.Uwp;
// ...

var renderer = new AdaptiveCardRenderer();
```

## <a name="create-a-card-from-a-json-string"></a><span data-ttu-id="4ef96-106">Créer une carte à partir d’une chaîne JSON</span><span class="sxs-lookup"><span data-stu-id="4ef96-106">Create a card from a JSON string</span></span>

```csharp
var card = AdaptiveCard.FromJsonString(jsonString);
```

## <a name="create-a-card-from-a-json-object"></a><span data-ttu-id="4ef96-107">Créer une carte à partir d’un objet JSON</span><span class="sxs-lookup"><span data-stu-id="4ef96-107">Create a card from a JSON object</span></span>

```csharp
var card = AdaptiveCard.FromJson(jsonObject);
```

## <a name="render-a-card"></a><span data-ttu-id="4ef96-108">Rendre une carte</span><span class="sxs-lookup"><span data-stu-id="4ef96-108">Render a card</span></span>

<span data-ttu-id="4ef96-109">Acquérir une carte à partir d’une source et la restituer.</span><span class="sxs-lookup"><span data-stu-id="4ef96-109">Acquire a card from a source and render it.</span></span>

```csharp
RenderedAdaptiveCard renderedAdaptiveCard =  renderer.RenderAdaptiveCard(card);

// Check if the render was successful
if (renderedAdaptiveCard.FrameworkElement != null)
{
    // Get the framework element
    var uiCard = renderedAdaptiveCard.FrameworkElement;

    // Add it to your UI
    myGrid.Children.Add(uiCard);
}
```

## <a name="example"></a><span data-ttu-id="4ef96-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="4ef96-110">Example</span></span>

<span data-ttu-id="4ef96-111">Voici un exemple du convertisseur UWP.</span><span class="sxs-lookup"><span data-stu-id="4ef96-111">Here is an example from the UWP renderer.</span></span>

```csharp
var renderer = new AdaptiveCardRenderer();
var card = AdaptiveCard.FromJsonString(jsonString);
var renderedAdaptiveCard = renderer.RenderAdaptiveCard(card.AdaptiveCard);
if (renderedAdaptiveCard.FrameworkElement != null)
{
    myGrid.Children.Add(renderedAdaptiveCard.FrameworkElement);
}
...
```
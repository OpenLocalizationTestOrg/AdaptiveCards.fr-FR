---
title: Styles natifs-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: c3190fbb31480f92c774d233476436ee2cfc52b3
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733021"
---
# <a name="native-styling---android"></a><span data-ttu-id="6dc05-102">Styles natifs-Android</span><span class="sxs-lookup"><span data-stu-id="6dc05-102">Native styling - Android</span></span>

<span data-ttu-id="6dc05-103">Le style natif n’est pas pris en charge sur le convertisseur Android, v 1.2 introduit la prise en charge du style de certaines propriétés:</span><span class="sxs-lookup"><span data-stu-id="6dc05-103">Native styling is not supported on the android renderer, v1.2 introduces the support for styling some properties:</span></span>

## <a name="action-sentiment"></a><span data-ttu-id="6dc05-104">Sentiment d’action</span><span class="sxs-lookup"><span data-stu-id="6dc05-104">Action Sentiment</span></span>

<span data-ttu-id="6dc05-105">Le sentiment d’action est inclus dans **v 1.2** et, bien qu’il ne prend pas en charge autant de styles que d’autres versions, les actions avec un sentiment *destructif* ou *positif* peuvent être stylisées en implémentant un style valide et en ajoutant la ligne suivante dans le styles. xml pour votre projet</span><span class="sxs-lookup"><span data-stu-id="6dc05-105">Action sentiment is included in **v1.2** and while not supporting as many styles as other versions, actions with *destructive* or *positive* sentiment can be styled by implementing a valid style and adding the following line into the styles.xml for your project</span></span>

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a><span data-ttu-id="6dc05-106">Action en ligne</span><span class="sxs-lookup"><span data-stu-id="6dc05-106">Inline Action</span></span>

<span data-ttu-id="6dc05-107">Les entrées de texte avec une action Inline permettent de styliser l’action rendue.</span><span class="sxs-lookup"><span data-stu-id="6dc05-107">Text inputs with an inline action allows styling for the action being rendered.</span></span> <span data-ttu-id="6dc05-108">Cela permet de styliser l’action en tant que bouton (adaptiveInlineAction) ou en tant qu’image (adaptiveInlineActionImage)</span><span class="sxs-lookup"><span data-stu-id="6dc05-108">This allows styling the action as a button (adaptiveInlineAction) or as an image (adaptiveInlineActionImage)</span></span>

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> <span data-ttu-id="6dc05-109">Tous les noms d’éléments doivent être conservés comme indiqué ici, car le convertisseur recherche ces noms exacts</span><span class="sxs-lookup"><span data-stu-id="6dc05-109">All item names must be kept as shown here as the renderer looks for those exact names</span></span>

---
title: SDK JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 55360658d74ca384b0e6090631a7f5db463e968a
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732906"
---
# <a name="getting-started---javascript"></a><span data-ttu-id="f28e6-102">Prise en main-JavaScript</span><span class="sxs-lookup"><span data-stu-id="f28e6-102">Getting started - JavaScript</span></span>

<span data-ttu-id="f28e6-103">Comme nous l’avons décrit dans [prise en main](../../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle objet de carte sérialisée JSON.</span><span class="sxs-lookup"><span data-stu-id="f28e6-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="f28e6-104">Il s’agit d’un kit de développement logiciel (SDK) JavaScript permettant de générer du code HTML côté client dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="f28e6-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f28e6-105">**Dernières modifications de v 0.5**</span><span class="sxs-lookup"><span data-stu-id="f28e6-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="f28e6-106">Package renommé `microsoft-adaptivecards` en`adaptivecards`</span><span class="sxs-lookup"><span data-stu-id="f28e6-106">Package renamed from `microsoft-adaptivecards` to `adaptivecards`</span></span>
> 1. <span data-ttu-id="f28e6-107">Le statique `AdaptiveCards.setHostConfig()` a été déplacé vers un membre d’instance `AdaptiveCard`de.</span><span class="sxs-lookup"><span data-stu-id="f28e6-107">The static `AdaptiveCards.setHostConfig()` has been moved to an instance member of `AdaptiveCard`.</span></span> <span data-ttu-id="f28e6-108">Par exemple,`myCard.hostConfig = {}`</span><span class="sxs-lookup"><span data-stu-id="f28e6-108">E.g., `myCard.hostConfig = {}`</span></span> 
> 1. <span data-ttu-id="f28e6-109">`HostConfig`a été renommé et déplacé plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="f28e6-109">`HostConfig` has gone though various renames and moves.</span></span> <span data-ttu-id="f28e6-110">Voir la configuration de l’hôte [Sample. JSON](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) pour la structure actuelle</span><span class="sxs-lookup"><span data-stu-id="f28e6-110">See the [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) Host Config for current structure</span></span>
> 1. <span data-ttu-id="f28e6-111">Certaines modifications de schéma ont également été apportées à la version préliminaire v 0,5, qui sont [décrites ici](https://github.com/Microsoft/AdaptiveCards/pull/633)</span><span class="sxs-lookup"><span data-stu-id="f28e6-111">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>
> 1. <span data-ttu-id="f28e6-112">La fonction `renderCard()` statique a été supprimée, car elle était redondante avec les méthodes de la classe.</span><span class="sxs-lookup"><span data-stu-id="f28e6-112">The static `renderCard()` function was removed as it was redundant with the class methods.</span></span> <span data-ttu-id="f28e6-113">Utilisez `adaptiveCard.render()` comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="f28e6-113">Use `adaptiveCard.render()` as described below.</span></span> 


## <a name="install"></a><span data-ttu-id="f28e6-114">Installer</span><span class="sxs-lookup"><span data-stu-id="f28e6-114">Install</span></span>

### <a name="node"></a><span data-ttu-id="f28e6-115">Nœud</span><span class="sxs-lookup"><span data-stu-id="f28e6-115">Node</span></span>

<span data-ttu-id="f28e6-116">[![installation de NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="f28e6-116">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards --save
```

### <a name="cdn"></a><span data-ttu-id="f28e6-117">CDN</span><span class="sxs-lookup"><span data-stu-id="f28e6-117">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="f28e6-118">Usage</span><span class="sxs-lookup"><span data-stu-id="f28e6-118">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="f28e6-119">Importer le module</span><span class="sxs-lookup"><span data-stu-id="f28e6-119">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="f28e6-120">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f28e6-120">Next steps</span></span>

<span data-ttu-id="f28e6-121">Consultez [rendu d’une carte](render-a-card.md) pour les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f28e6-121">See [Render a card](render-a-card.md) for the next steps!</span></span>

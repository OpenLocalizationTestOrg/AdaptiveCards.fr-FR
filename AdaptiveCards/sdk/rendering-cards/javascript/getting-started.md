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
# <a name="getting-started---javascript"></a>Prise en main-JavaScript

Comme nous l’avons décrit dans [prise en main](../../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle objet de carte sérialisée JSON. Il s’agit d’un kit de développement logiciel (SDK) JavaScript permettant de générer du code HTML côté client dans le navigateur.

> [!IMPORTANT]
> **Dernières modifications de v 0.5**
> 
> 1. Package renommé `microsoft-adaptivecards` en`adaptivecards`
> 1. Le statique `AdaptiveCards.setHostConfig()` a été déplacé vers un membre d’instance `AdaptiveCard`de. Par exemple,`myCard.hostConfig = {}` 
> 1. `HostConfig`a été renommé et déplacé plusieurs fois. Voir la configuration de l’hôte [Sample. JSON](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) pour la structure actuelle
> 1. Certaines modifications de schéma ont également été apportées à la version préliminaire v 0,5, qui sont [décrites ici](https://github.com/Microsoft/AdaptiveCards/pull/633)
> 1. La fonction `renderCard()` statique a été supprimée, car elle était redondante avec les méthodes de la classe. Utilisez `adaptiveCard.render()` comme décrit ci-dessous. 


## <a name="install"></a>Installer

### <a name="node"></a>Nœud

[![installation de NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)

```console
npm install adaptivecards --save
```

### <a name="cdn"></a>CDN

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a>Usage

### <a name="import-the-module"></a>Importer le module

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a>Étapes suivantes

Consultez [rendu d’une carte](render-a-card.md) pour les étapes suivantes.

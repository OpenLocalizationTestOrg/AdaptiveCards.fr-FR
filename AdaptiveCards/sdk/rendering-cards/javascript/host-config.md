---
title: Configuration de l’hôte-SDK JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: a011ffc43c2990cd8eb568b9f1c449cf541f9a70
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732896"
---
# <a name="host-config---javascript"></a>Host config - JavaScript

```js
// Create an AdaptiveCard instance
var adaptiveCard = new AdaptiveCards.AdaptiveCard();

// Set its hostConfig property unless you want to use the default Host Config
// Host Config defines the style and behavior of a card
adaptiveCard.hostConfig = new AdaptiveCards.HostConfig({
    fontFamily: "Segoe UI, Helvetica Neue, sans-serif"
    // More host config options
});

// Render the card to an HTML element:
var renderedCard = adaptiveCard.render();
```

## <a name="customization"></a>Personnalisation

Il existe trois façons de personnaliser le rendu de carte adaptative: 
1. Configuration de l’hôte
2. Styles CSS
3. Rendu d’élément personnalisé

### <a name="hostconfig"></a>HostConfig 

Une configuration d' [hôte](../../../rendering-cards/host-config.md) est un objet de configuration partagé que tous les convertisseurs comprennent. Cela vous permet de définir des styles courants (par exemple, famille de polices, tailles de police, espacement par défaut) et des comportements (par exemple, nombre maximal d’actions) qui seront interprétés automatiquement par chaque convertisseur de plateforme. 

L’objectif est que l’interface utilisateur native générée par chaque convertisseur de plateforme semble très similaire avec un minimum de travail de votre part.

```javascript
var renderOptions = {
    ...
    hostConfig: {
        // Define your host config object here
        // See the HostConfig docs for details
    }
};
```
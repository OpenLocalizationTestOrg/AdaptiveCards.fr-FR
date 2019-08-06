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
# <a name="native-styling---android"></a>Styles natifs-Android

Le style natif n’est pas pris en charge sur le convertisseur Android, v 1.2 introduit la prise en charge du style de certaines propriétés:

## <a name="action-sentiment"></a>Sentiment d’action

Le sentiment d’action est inclus dans **v 1.2** et, bien qu’il ne prend pas en charge autant de styles que d’autres versions, les actions avec un sentiment *destructif* ou *positif* peuvent être stylisées en implémentant un style valide et en ajoutant la ligne suivante dans le styles. xml pour votre projet

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a>Action en ligne

Les entrées de texte avec une action Inline permettent de styliser l’action rendue. Cela permet de styliser l’action en tant que bouton (adaptiveInlineAction) ou en tant qu’image (adaptiveInlineActionImage)

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> Tous les noms d’éléments doivent être conservés comme indiqué ici, car le convertisseur recherche ces noms exacts

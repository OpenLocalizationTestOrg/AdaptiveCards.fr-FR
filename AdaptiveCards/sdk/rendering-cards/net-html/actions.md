---
title: Actions-SDK HTML .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f577c0bab73e2bd1f75bb22dd7a41a7dbfd63307
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732851"
---
# <a name="actions---net-html"></a>Actions-HTML .NET

La carte `actions` de niveau supérieur est restituée sous `<button>`forme de code html. Dans la mesure où il s’agit d’une bibliothèque côté serveur, vous pouvez associer des gestionnaires d’événements côté client lorsque vous appuyez sur les boutons. Chaque `<button>` dans le code html aura des attributs que vous pouvez utiliser pour associer le comportement approprié.

Certains éléments ont une `selectAction` propriété (Container, Columns, image) qui les rend programmes appelables. Si un élément a un `selectAction` convertisseur, ajoute une classe CSS de `ac-selectable`, ainsi que les attributs ci-dessous.

Type d’action | Classe CSS | Attributs supplémentaires
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | `data-ac-url`(la `url` propriété de la carte)
`Action.Submit` | `ac-action-submit` | `data-ac-data`(la `data` propriété de la carte)
`Action.ShowCard` | `ac-action-showCard` | `data-ac-showcardid`(le `id` `<div>` du contenant la carte interne)
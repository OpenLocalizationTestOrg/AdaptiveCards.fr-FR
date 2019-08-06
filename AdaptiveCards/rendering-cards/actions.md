---
title: Actions
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34283b52f0c4902c71ea33634676832c7dfec5c9
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733106"
---
# <a name="actions"></a>Actions

Par défaut, les actions s’affichent sous la forme de boutons sur la carte, mais c’est à votre application qu’il faut faire en sorte qu’elles se comportent comme prévu. Chaque kit de développement logiciel (SDK `OnAction` ) a l’équivalent d’un événement que vous devez gérer.

* **Action. OpenURL** : ouvre le spécifié `url`.  
* **Action. Submit** : prenez le résultat de l’envoi et envoyez-le à la source. La façon dont vous l’envoyez à la source de la carte dépend entièrement de vous.
* **Action. ShowCard** : appelle une boîte de dialogue et affiche la sous-carte dans cette boîte de dialogue. Notez que vous devez uniquement gérer cela si `ShowCardActionMode` a la `popup`valeur.
---
title: Gestion de la parole
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: ea46a1c2c14a4cd2aded9672d7493561bbebbd16
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732616"
---
# <a name="handling-speech"></a>Gestion de la parole

Pour prendre en charge les cartes adaptatives `speak` vocales, la propriété contient des informations sur la façon dont une carte doit être lue à haute voix à un utilisateur.

La balise Speech peut être annotée à l’aide du [balisage SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx). SSML vous donne la possibilité de contrôler la vitesse, le ton et l’inflexion de la parole.  Elle vous permet même de diffuser du contenu audio ou un rendu d’un flux audio TTS à partir de votre propre service, ce qui vous donne une grande quantité de personnalisation.

Il existe 2 modèles pour l’utilisation des propriétés Speak par une application hôte:
* **en cas de remise** : lorsqu’une carte est remise, un client peut choisir de lire la propriété Speak de la carte pour décrire la carte dans son ensemble.
* à **la demande** -afin de prendre en charge un modèle d’accessibilité plus riche, le schéma prend en charge une balise Speak par élément.  
Cela permet aux clients de lire chaque élément auprès des destinataires ayant des exigences d’accessibilité.


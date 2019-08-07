---
title: Reconnaissance vocale et avancée
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 468d090dff0511f40cb7e5eedc4f4a18fa12aa3c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732666"
---
# <a name="speech-and-advanced-customization"></a>Reconnaissance vocale et avancée
Nous vivons dans une ère d’interaction vocale via des services tels que Cortana.  Les cartes adaptatives sont conçues à partir du premier jour pour prendre en charge la reconnaissance vocale, ce qui permet de créer de nouveaux scénarios pratiques complets.

La `speak` balise permet de remettre la carte adaptative à un environnement dans lequel un affichage visuel n’est pas une expérience principale, par exemple dans un tableau de bord de voiture pendant la conduite. 

## <a name="speak-property"></a>Speak, propriété
Pour prendre en charge la reconnaissance `speak` vocale, nous disposons d’une propriété qui contient du texte à indiquer à l’utilisateur. Le texte peut être annoté à l’aide du langage[SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)(speech synthesis Markup Language). SSML contrôle la vitesse, le ton et l’inflexion de la parole.  Il vous permet même de diffuser du contenu audio ou un flux audio TTS à partir de votre propre service, ce qui vous offre une grande flexibilité pour la personnalisation.

Il existe deux modèles pour l’utilisation des propriétés Speak par une application hôte:

* **En cas de remise** : lorsqu’une carte est remise, le client peut choisir de lire la propriété Speak de la carte pour décrire la carte dans son ensemble.
* À **la demande** -afin de prendre en charge un modèle d’accessibilité plus riche, le schéma prend en charge une balise Speak pour chaque élément. Le client peut lire une propriété Speak pour chaque élément de la carte.

### <a name="examples"></a>Exemples

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a>Conception de contenu vocal

Le contenu conçu pour la reconnaissance vocale est différent du contenu conçu pour l’affichage visuel. Lorsque vous concevez une carte, vous concevez une expérience visuelle entière pour présenter des informations à un utilisateur d’une manière qui les éclaircit. Lors de la conception de la reconnaissance vocale, vous devez réfléchir à la façon de décrire verbalement le contenu d’une manière qui l’éclaircit.  

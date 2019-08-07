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
# <a name="handling-speech"></a><span data-ttu-id="44e7b-102">Gestion de la parole</span><span class="sxs-lookup"><span data-stu-id="44e7b-102">Handling speech</span></span>

<span data-ttu-id="44e7b-103">Pour prendre en charge les cartes adaptatives `speak` vocales, la propriété contient des informations sur la façon dont une carte doit être lue à haute voix à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="44e7b-103">To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.</span></span>

<span data-ttu-id="44e7b-104">La balise Speech peut être annotée à l’aide du [balisage SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span><span class="sxs-lookup"><span data-stu-id="44e7b-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="44e7b-105">SSML vous donne la possibilité de contrôler la vitesse, le ton et l’inflexion de la parole.</span><span class="sxs-lookup"><span data-stu-id="44e7b-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="44e7b-106">Elle vous permet même de diffuser du contenu audio ou un rendu d’un flux audio TTS à partir de votre propre service, ce qui vous donne une grande quantité de personnalisation.</span><span class="sxs-lookup"><span data-stu-id="44e7b-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="44e7b-107">Il existe 2 modèles pour l’utilisation des propriétés Speak par une application hôte:</span><span class="sxs-lookup"><span data-stu-id="44e7b-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="44e7b-108">**en cas de remise** : lorsqu’une carte est remise, un client peut choisir de lire la propriété Speak de la carte pour décrire la carte dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="44e7b-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="44e7b-109">à **la demande** -afin de prendre en charge un modèle d’accessibilité plus riche, le schéma prend en charge une balise Speak par élément.</span><span class="sxs-lookup"><span data-stu-id="44e7b-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="44e7b-110">Cela permet aux clients de lire chaque élément auprès des destinataires ayant des exigences d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="44e7b-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>


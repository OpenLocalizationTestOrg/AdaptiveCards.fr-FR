---
title: Cartes adaptatives pour les développeurs de robots
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: a50f2e6f145ae2c4571d6b20b61b9ad182ca7ba5
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733166"
---
# <a name="adaptive-cards-for-bot-developers"></a>Cartes adaptatives pour les développeurs de robots

Les cartes adaptatives conviennent parfaitement aux robots. Ils vous permettent de créer une carte une seule fois et de l’afficher parfaitement dans plusieurs applications, telles que Microsoft Teams, votre propre site Web, et bien plus encore.

> [!NOTE]
> Skype n’est pas pris en charge dans la version préliminaire actuelle. Pour obtenir la dernière version, consultez la page [État du partenaire](../resources/partners.md) .

## <a name="try-it-out"></a>Faites un essai

Cliquez sur le lien suivant et [communiquez avec notre bot](http://contososcubademo.azurewebsites.net/). Disons `I'm looking for scuba` et cela vous aidera à faire le voyage de vos rêves.  

Toutes les réponses du bot sont créées avec des cartes adaptatives.

[![Capture d’écran de conversation](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)

**Obtenir le code**: le code [](https://github.com/matthidinger/ContosoScubaBot
) source complet du robot de recherche contoso se trouve sur GitHub.


## <a name="bot-framework-integration"></a>Intégration de bot Framework

Avec le [robot Framework](https://dev.botframework.com/) , vous pouvez écrire un seul robot capable de discuter avec des utilisateurs sur plusieurs «canaux», tels que Skype, Microsoft Teams, Facebook Messenger, etc.

## <a name="walkthrough"></a>Procédure pas à pas

C’est assez simple pour ajouter une carte adaptative à votre bot.

### <a name="step-0-start-with-a-basic-message"></a>Étape 0 : Démarrer avec un message de base

Voici une charge utile de l' `message` infrastructure bot standard qui peut être remise à n’importe quel canal et afficher du texte à l’utilisateur.

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a>Étape 1 : Ajouter une carte adaptative`attachment`

Pour ajouter une certaine richesse au-delà du simple texte, le robot Framework `attachments`a un concept de. 

Attachez une carte adaptative qui affiche du texte personnalisé.

![Carte adaptative de base](media/bots/hello-adaptivecards.png)

```json
{
  "type": "message",
  "text": "Plain text is ok, but sometimes I long for more...",
  "attachments": [
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "TextBlock",
            "text": "Hello World!",
            "size": "large"
          },
          {
            "type": "TextBlock",
            "text": "*Sincerely yours,*"
          },
          {
            "type": "TextBlock",
            "text": "Adaptive Cards",
            "separation": "none"
          }
        ],
        "actions": [
          {
            "type": "Action.OpenUrl",
            "url": "http://adaptivecards.io",
            "title": "Learn More"
          }
        ]
      }
    }
  ]
}
```

### <a name="step-2-build-even-richer-cards"></a>Étape 2 : Créez des cartes encore plus riches 

Les cartes adaptatives offrent bien plus qu’un simple texte personnalisable. 

Vous pouvez : 

* Ajouter `Images` à votre carte
* Organisez votre contenu `Containers` avec et`Columns`
* Ajouter plusieurs types de`Actions`
* Collecter `Input` auprès de vos utilisateurs
* Avoir une carte`show another card`
* [Consultez l’Explorateur de schémas complet](http://adaptivecards.io/explorer/)! 

## <a name="platform-sdks"></a>Kits de développement Platform SDK

Si votre bot est développé à l’aide de .NET ou de NodeJS, nous avons des bibliothèques qui facilitent la création de cartes adaptatives.

Plateforme|Installer|En savoir plus
--------|-------|----------
.NET | `Install-Package AdaptiveCards -IncludePrerelease` | [Documentation .NET de bot Framework](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
NodeJS | `npm install adaptivecards` | [NodeJS docs de bot Framework](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a>État du canal

L’infrastructure bot vous permet de publier votre robot sur plusieurs canaux. Nous travaillons avec différents canaux pour fournir une prise en charge complète des cartes adaptatives. Pour obtenir la dernière version, consultez la page [État du partenaire](../resources/partners.md) .


## <a name="dive-in"></a>Plongez-vous!

Nous n’avons fait qu’effleurer la surface de ce didacticiel. veuillez consulter les liens ci-dessous pour découvrir d’autres façons d’améliorer votre robot.

* [Parcourir les exemples de cartes](http://adaptivecards.io/samples/) pour l’inspiration
* Utiliser l' [Explorateur de schémas](http://adaptivecards.io/explorer) pour apprendre les éléments disponibles
* Créer une carte à l’aide du [visualiseur interactif](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Soyez en contact](http://adaptivecards.io/connect) avec vos commentaires

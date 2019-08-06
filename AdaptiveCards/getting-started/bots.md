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
# <a name="adaptive-cards-for-bot-developers"></a><span data-ttu-id="21090-102">Cartes adaptatives pour les développeurs de robots</span><span class="sxs-lookup"><span data-stu-id="21090-102">Adaptive Cards for Bot Developers</span></span>

<span data-ttu-id="21090-103">Les cartes adaptatives conviennent parfaitement aux robots.</span><span class="sxs-lookup"><span data-stu-id="21090-103">Adaptive Cards are a great fit for Bots.</span></span> <span data-ttu-id="21090-104">Ils vous permettent de créer une carte une seule fois et de l’afficher parfaitement dans plusieurs applications, telles que Microsoft Teams, votre propre site Web, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="21090-104">They let you author a card once and have it render beautifully inside multiple apps, like  Microsoft Teams, your own website, and more.</span></span>

> [!NOTE]
> <span data-ttu-id="21090-105">Skype n’est pas pris en charge dans la version préliminaire actuelle.</span><span class="sxs-lookup"><span data-stu-id="21090-105">Skype is not supported in the current preview.</span></span> <span data-ttu-id="21090-106">Pour obtenir la dernière version, consultez la page [État du partenaire](../resources/partners.md) .</span><span class="sxs-lookup"><span data-stu-id="21090-106">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>

## <a name="try-it-out"></a><span data-ttu-id="21090-107">Faites un essai</span><span class="sxs-lookup"><span data-stu-id="21090-107">Try it out</span></span>

<span data-ttu-id="21090-108">Cliquez sur le lien suivant et [communiquez avec notre bot](http://contososcubademo.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="21090-108">Click the following link and [talk to our Scuba Bot](http://contososcubademo.azurewebsites.net/).</span></span> <span data-ttu-id="21090-109">Disons `I'm looking for scuba` et cela vous aidera à faire le voyage de vos rêves.</span><span class="sxs-lookup"><span data-stu-id="21090-109">Say `I'm looking for scuba` and it'll help you book the scuba trip of your dreams.</span></span>  

<span data-ttu-id="21090-110">Toutes les réponses du bot sont créées avec des cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="21090-110">All of the bot's responses are created with Adaptive Cards.</span></span>

<span data-ttu-id="21090-111">[![Capture d’écran de conversation](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span><span class="sxs-lookup"><span data-stu-id="21090-111">[![Scuba chat screenshot](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span></span>

<span data-ttu-id="21090-112">**Obtenir le code**: le code [](https://github.com/matthidinger/ContosoScubaBot
) source complet du robot de recherche contoso se trouve sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="21090-112">**Get the code**: the full [Contoso Scuba Bot source code](https://github.com/matthidinger/ContosoScubaBot
) can be found on GitHub.</span></span>


## <a name="bot-framework-integration"></a><span data-ttu-id="21090-113">Intégration de bot Framework</span><span class="sxs-lookup"><span data-stu-id="21090-113">Bot Framework Integration</span></span>

<span data-ttu-id="21090-114">Avec le [robot Framework](https://dev.botframework.com/) , vous pouvez écrire un seul robot capable de discuter avec des utilisateurs sur plusieurs «canaux», tels que Skype, Microsoft Teams, Facebook Messenger, etc.</span><span class="sxs-lookup"><span data-stu-id="21090-114">With the [Bot Framework](https://dev.botframework.com/) you can write a single bot that is able to chat with users across multiple "channels", like Skype, Microsoft Teams, Facebook Messenger, etc.</span></span>

## <a name="walkthrough"></a><span data-ttu-id="21090-115">Procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="21090-115">Walkthrough</span></span>

<span data-ttu-id="21090-116">C’est assez simple pour ajouter une carte adaptative à votre bot.</span><span class="sxs-lookup"><span data-stu-id="21090-116">It's pretty straight forward to add an Adaptive Card to your bot.</span></span>

### <a name="step-0-start-with-a-basic-message"></a><span data-ttu-id="21090-117">Étape 0 : Démarrer avec un message de base</span><span class="sxs-lookup"><span data-stu-id="21090-117">Step 0: Start with a basic message</span></span>

<span data-ttu-id="21090-118">Voici une charge utile de l' `message` infrastructure bot standard qui peut être remise à n’importe quel canal et afficher du texte à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="21090-118">Here's a standard Bot Framework `message` payload that can be delivered to any channel and display text to the user.</span></span>

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a><span data-ttu-id="21090-119">Étape 1 : Ajouter une carte adaptative`attachment`</span><span class="sxs-lookup"><span data-stu-id="21090-119">Step 1: Add an Adaptive Card `attachment`</span></span>

<span data-ttu-id="21090-120">Pour ajouter une certaine richesse au-delà du simple texte, le robot Framework `attachments`a un concept de.</span><span class="sxs-lookup"><span data-stu-id="21090-120">To add some richness beyond just text, the Bot Framework has a concept of `attachments`.</span></span> 

<span data-ttu-id="21090-121">Attachez une carte adaptative qui affiche du texte personnalisé.</span><span class="sxs-lookup"><span data-stu-id="21090-121">Let's attach an Adaptive Card that displays custom text.</span></span>

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

### <a name="step-2-build-even-richer-cards"></a><span data-ttu-id="21090-123">Étape 2 : Créez des cartes encore plus riches</span><span class="sxs-lookup"><span data-stu-id="21090-123">Step 2: Build even richer cards</span></span> 

<span data-ttu-id="21090-124">Les cartes adaptatives offrent bien plus qu’un simple texte personnalisable.</span><span class="sxs-lookup"><span data-stu-id="21090-124">Adaptive Cards offer much more than just customizable text.</span></span> 

<span data-ttu-id="21090-125">Vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="21090-125">You can:</span></span> 

* <span data-ttu-id="21090-126">Ajouter `Images` à votre carte</span><span class="sxs-lookup"><span data-stu-id="21090-126">Add `Images` to your card</span></span>
* <span data-ttu-id="21090-127">Organisez votre contenu `Containers` avec et`Columns`</span><span class="sxs-lookup"><span data-stu-id="21090-127">Organize your content with `Containers` and `Columns`</span></span>
* <span data-ttu-id="21090-128">Ajouter plusieurs types de`Actions`</span><span class="sxs-lookup"><span data-stu-id="21090-128">Add multiple types of `Actions`</span></span>
* <span data-ttu-id="21090-129">Collecter `Input` auprès de vos utilisateurs</span><span class="sxs-lookup"><span data-stu-id="21090-129">Collect `Input` from your users</span></span>
* <span data-ttu-id="21090-130">Avoir une carte`show another card`</span><span class="sxs-lookup"><span data-stu-id="21090-130">Have one card `show another card`</span></span>
* <span data-ttu-id="21090-131">[Consultez l’Explorateur de schémas complet](http://adaptivecards.io/explorer/)!</span><span class="sxs-lookup"><span data-stu-id="21090-131">[Check out the full schema explorer](http://adaptivecards.io/explorer/)!</span></span> 

## <a name="platform-sdks"></a><span data-ttu-id="21090-132">Kits de développement Platform SDK</span><span class="sxs-lookup"><span data-stu-id="21090-132">Platform SDKs</span></span>

<span data-ttu-id="21090-133">Si votre bot est développé à l’aide de .NET ou de NodeJS, nous avons des bibliothèques qui facilitent la création de cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="21090-133">If your bot is developed using .NET or NodeJS we have libraries to make building Adaptive Cards even easier.</span></span>

<span data-ttu-id="21090-134">Plateforme</span><span class="sxs-lookup"><span data-stu-id="21090-134">Platform</span></span>|<span data-ttu-id="21090-135">Installer</span><span class="sxs-lookup"><span data-stu-id="21090-135">Install</span></span>|<span data-ttu-id="21090-136">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="21090-136">Learn more</span></span>
--------|-------|----------
<span data-ttu-id="21090-137">.NET</span><span class="sxs-lookup"><span data-stu-id="21090-137">.NET</span></span> | `Install-Package AdaptiveCards -IncludePrerelease` | [<span data-ttu-id="21090-138">Documentation .NET de bot Framework</span><span class="sxs-lookup"><span data-stu-id="21090-138">Bot Framework .NET Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
<span data-ttu-id="21090-139">NodeJS</span><span class="sxs-lookup"><span data-stu-id="21090-139">NodeJS</span></span> | `npm install adaptivecards` | [<span data-ttu-id="21090-140">NodeJS docs de bot Framework</span><span class="sxs-lookup"><span data-stu-id="21090-140">Bot Framework NodeJS Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a><span data-ttu-id="21090-141">État du canal</span><span class="sxs-lookup"><span data-stu-id="21090-141">Channel status</span></span>

<span data-ttu-id="21090-142">L’infrastructure bot vous permet de publier votre robot sur plusieurs canaux.</span><span class="sxs-lookup"><span data-stu-id="21090-142">The Bot Framework lets you publish your bot to multiple channels.</span></span> <span data-ttu-id="21090-143">Nous travaillons avec différents canaux pour fournir une prise en charge complète des cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="21090-143">We're working with various channels to provide full support for Adaptive Cards.</span></span> <span data-ttu-id="21090-144">Pour obtenir la dernière version, consultez la page [État du partenaire](../resources/partners.md) .</span><span class="sxs-lookup"><span data-stu-id="21090-144">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>


## <a name="dive-in"></a><span data-ttu-id="21090-145">Plongez-vous!</span><span class="sxs-lookup"><span data-stu-id="21090-145">Dive in!</span></span>

<span data-ttu-id="21090-146">Nous n’avons fait qu’effleurer la surface de ce didacticiel. veuillez consulter les liens ci-dessous pour découvrir d’autres façons d’améliorer votre robot.</span><span class="sxs-lookup"><span data-stu-id="21090-146">We've just scratched the surface in this tutorial, so please take a look at the links below to explore more ways that Adaptive Cards can enhance your bot.</span></span>

* <span data-ttu-id="21090-147">[Parcourir les exemples de cartes](http://adaptivecards.io/samples/) pour l’inspiration</span><span class="sxs-lookup"><span data-stu-id="21090-147">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="21090-148">Utiliser l' [Explorateur de schémas](http://adaptivecards.io/explorer) pour apprendre les éléments disponibles</span><span class="sxs-lookup"><span data-stu-id="21090-148">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="21090-149">Créer une carte à l’aide du [visualiseur interactif](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="21090-149">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="21090-150">[Soyez en contact](http://adaptivecards.io/connect) avec vos commentaires</span><span class="sxs-lookup"><span data-stu-id="21090-150">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>

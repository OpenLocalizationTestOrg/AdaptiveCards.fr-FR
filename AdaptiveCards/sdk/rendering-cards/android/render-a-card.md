---
title: Rendu d’une carte-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 5ced7a2217ef6ef475aa344d92ad2f5e567266f8
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733001"
---
# <a name="render-a-card---android"></a><span data-ttu-id="35dd1-102">Rendu d’une carte Android</span><span class="sxs-lookup"><span data-stu-id="35dd1-102">Render a card - Android</span></span>

<span data-ttu-id="35dd1-103">Voici comment afficher une carte à l’aide de l’Android SDK.</span><span class="sxs-lookup"><span data-stu-id="35dd1-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="35dd1-104">Créer une instance d’objet carte adaptative à partir du texte JSON</span><span class="sxs-lookup"><span data-stu-id="35dd1-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> <span data-ttu-id="35dd1-105">**Modifications avec rupture pour v 1.2**</span><span class="sxs-lookup"><span data-stu-id="35dd1-105">**Breaking changes for v1.2**</span></span>
> 

1. <span data-ttu-id="35dd1-106">Le paramètre ElementParserRegistration est passé à ParseContext, qui comprend un ElementParserRegistration et un objet ActionParserRegistration</span><span class="sxs-lookup"><span data-stu-id="35dd1-106">ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionParserRegistration object</span></span>

```java
ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="35dd1-107">ou Gestionnaire de configuration</span><span class="sxs-lookup"><span data-stu-id="35dd1-107">or</span></span>

```java
ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

## <a name="render-a-card"></a><span data-ttu-id="35dd1-108">Rendre une carte</span><span class="sxs-lookup"><span data-stu-id="35dd1-108">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.getView();
```

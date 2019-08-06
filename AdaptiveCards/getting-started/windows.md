---
title: Cartes adaptatives pour les développeurs Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: c9ea788cfbc8e365cdece1cd8f42c3718b7bc3e7
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733116"
---
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="214e9-102">Cartes adaptatives pour les développeurs Windows</span><span class="sxs-lookup"><span data-stu-id="214e9-102">Adaptive Cards for Windows Developers</span></span>



## <a name="timeline"></a><span data-ttu-id="214e9-103">Chronologie</span><span class="sxs-lookup"><span data-stu-id="214e9-103">Timeline</span></span>

<span data-ttu-id="214e9-104">La première expérience Windows pour la prise en charge des cartes adaptatives est la chronologie, une nouvelle expérience introduite pour la première fois dans Windows 10 1803.</span><span class="sxs-lookup"><span data-stu-id="214e9-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![Chronologie](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="214e9-106">API UserActivity</span><span class="sxs-lookup"><span data-stu-id="214e9-106">UserActivity API</span></span>

<span data-ttu-id="214e9-107">L' [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API est celle qui remplit une activité dans la chronologie.</span><span class="sxs-lookup"><span data-stu-id="214e9-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="214e9-108">La carte adaptative sera fournie par le biais de `Content` la propriété `VisualElement`de, comme indiqué ci-dessous:</span><span class="sxs-lookup"><span data-stu-id="214e9-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a><span data-ttu-id="214e9-109">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="214e9-109">Learn more</span></span>

<span data-ttu-id="214e9-110">Cette session à la build 2017 couvre les activités des utilisateurs dans detial.</span><span class="sxs-lookup"><span data-stu-id="214e9-110">This session at Build 2017 covers User Activities in detial.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="214e9-111">Autres surfaces Windows</span><span class="sxs-lookup"><span data-stu-id="214e9-111">Other Windows Surfaces</span></span>
<span data-ttu-id="214e9-112">Nous n’avons rien à partager pour l’instant, mais nous travaillons à l’incorporation de cartes adaptatives dans d’autres expériences Windows.</span><span class="sxs-lookup"><span data-stu-id="214e9-112">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="214e9-113">Plongez-vous!</span><span class="sxs-lookup"><span data-stu-id="214e9-113">Dive in!</span></span>

<span data-ttu-id="214e9-114">Nous n’avons pas encore rayé la surface de ce didacticiel. vous pouvez donc revenir en arrière et parcourir les liens ci-dessous pour en savoir plus sur les cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="214e9-114">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="214e9-115">[Parcourir les exemples de cartes](http://adaptivecards.io/samples/) pour l’inspiration</span><span class="sxs-lookup"><span data-stu-id="214e9-115">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="214e9-116">Utiliser l' [Explorateur de schémas](http://adaptivecards.io/explorer) pour apprendre les éléments disponibles</span><span class="sxs-lookup"><span data-stu-id="214e9-116">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="214e9-117">Créer une carte à l’aide du [visualiseur interactif](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="214e9-117">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="214e9-118">[Soyez en contact](http://adaptivecards.io/connect) avec vos commentaires</span><span class="sxs-lookup"><span data-stu-id="214e9-118">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>

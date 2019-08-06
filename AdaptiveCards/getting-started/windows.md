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
# <a name="adaptive-cards-for-windows-developers"></a>Cartes adaptatives pour les développeurs Windows



## <a name="timeline"></a>Chronologie

La première expérience Windows pour la prise en charge des cartes adaptatives est la chronologie, une nouvelle expérience introduite pour la première fois dans Windows 10 1803. 

![Chronologie](media/windows/timeline.png)

### <a name="useractivity-api"></a>API UserActivity

L' [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API est celle qui remplit une activité dans la chronologie.

La carte adaptative sera fournie par le biais de `Content` la propriété `VisualElement`de, comme indiqué ci-dessous:

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a>En savoir plus

Cette session à la build 2017 couvre les activités des utilisateurs dans detial.

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a>Autres surfaces Windows
Nous n’avons rien à partager pour l’instant, mais nous travaillons à l’incorporation de cartes adaptatives dans d’autres expériences Windows.

## <a name="dive-in"></a>Plongez-vous!

Nous n’avons pas encore rayé la surface de ce didacticiel. vous pouvez donc revenir en arrière et parcourir les liens ci-dessous pour en savoir plus sur les cartes adaptatives.

* [Parcourir les exemples de cartes](http://adaptivecards.io/samples/) pour l’inspiration
* Utiliser l' [Explorateur de schémas](http://adaptivecards.io/explorer) pour apprendre les éléments disponibles
* Créer une carte à l’aide du [visualiseur interactif](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Soyez en contact](http://adaptivecards.io/connect) avec vos commentaires

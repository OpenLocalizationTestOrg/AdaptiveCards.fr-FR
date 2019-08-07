---
title: Rendu de cartes à l’intérieur de votre application
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: a562a05a91676dc5e6d8b51690acc4788802fb99
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732606"
---
# <a name="rendering-cards-inside-your-application"></a>Rendu de cartes à l’intérieur de votre application

Il est facile d’afficher des cartes adaptatives à l’intérieur de votre application. Nous fournissons des kits de développement logiciel (SDK) pour toutes les plateformes courantes, et fournissons une [spécification détaillée](implement-a-renderer.md) pour créer votre propre convertisseur de carte adaptative.

1. **Installez un kit de développement logiciel de rendu** pour votre plateforme cible.
2. **Créez une instance de convertisseur** configurée avec le style, les règles et les gestionnaires d’événements d’action de votre application.
3. **Restituer une carte à l’interface utilisateur native** , automatiquement avec un style à votre application.

## <a name="adaptive-cards-sdks"></a>Kits de développement logiciel de cartes adaptatives

|Plateforme|Installer|Build|Docs|Statut|
|---|---|---|---|---|
| JavaScript | [![installation de NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/nodejs)| [Documents](../sdk/rendering-cards/javascript/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20564.svg) |
| WPF .NET | [![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet)| [Documents](../sdk/rendering-cards/net-wpf/getting-started.md) | ![État de la Build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| .NET HTML | [![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Html.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Html) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet) | [Documents](../sdk/rendering-cards/net-html/getting-started.md) | ![État de la Build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| Windows UWP | [![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Uwp.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Uwp) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/uwp) | [Documents](../sdk/rendering-cards/uwp/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20583.svg) |
| Android | [![Maven central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/android) | [Documents](../sdk/rendering-cards/android/getting-started.md) | ![État de la Build](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/17651.svg)
| iOS | [![CocoaPods](https://img.shields.io/cocoapods/v/AdaptiveCards.svg)](https://cocoapods.org/pods/AdaptiveCards) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/ios) | [Documents](../sdk/rendering-cards/ios/getting-started.md) |  ![État de la Build](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/16990.svg) |

## <a name="create-an-instance-of-the-renderer"></a>Créer une instance du convertisseur

L’étape suivante consiste à créer une instance d’un `AdaptiveCardRenderer`. 

### <a name="hook-up-action-events"></a>Événements d’action de raccordement

Par défaut, les actions s’affichent sous la forme de boutons sur la carte, mais c’est à votre application qu’il faut faire en sorte qu’elles se comportent comme prévu. Chaque kit de développement logiciel (SDK `OnAction` ) a l’équivalent d’un événement que vous devez gérer.

* **Action. OpenURL** : ouvre le spécifié `url`.  
* **Action. Submit** : prenez le résultat de l’envoi et envoyez-le à la source. La façon dont vous l’envoyez à la source de la carte dépend entièrement de vous.
* **Action. ShowCard** : appelle une boîte de dialogue et affiche la sous-carte dans cette boîte de dialogue. Notez que vous devez uniquement gérer cela si `ShowCardActionMode` a la `popup`valeur.

## <a name="render-a-card"></a>Rendre une carte

Une fois que vous avez acquis une charge utile de carte, appelez simplement le convertisseur et transmettez la carte. Vous devez récupérer un objet d’interface utilisateur natif composé du contenu de la carte. Maintenant, il vous suffit de placer cette interface utilisateur quelque part dans votre application.

## <a name="customization"></a>Personnalisation

Il existe plusieurs façons de personnaliser ce qui est rendu. 

### <a name="hostconfig"></a>HostConfig

Un [HostConfig](host-config.md) est un objet de configuration multiplateforme et partagé qui contrôle le style et le comportement de base des cartes à l’intérieur de votre application. Il définit des éléments tels que les tailles de police, l’espacement entre les éléments, les couleurs, le nombre d’actions prises en charge, etc. 

### <a name="native-platform-styling"></a>Style de plateforme Native

La plupart des infrastructures d’interface utilisateur vous permettent d’appliquer un style à la carte rendue à l’aide du style de l’infrastructure d’interface utilisateur native. Par exemple, en HTML, vous pouvez spécifier des classes CSS pour le code HTML, ou en XAML, vous pouvez passer un ResourceDictionary personnalisé pour un contrôle affiné de la sortie.

### <a name="customize-per-element-rendering"></a>Personnaliser le rendu par élément

Chaque kit de développement logiciel (SDK) vous permet de remplacer le rendu d’un élément, ou même d’ajouter la prise en charge des éléments entièrement nouveaux que vous définissez.  Par exemple, vous pouvez modifier le `Input.Date` convertisseur pour émettre votre propre contrôle personnalisé tout en conservant le reste de la sortie du convertisseur. Ou vous pouvez ajouter la prise en charge `Rating` d’un élément personnalisé que vous définissez.




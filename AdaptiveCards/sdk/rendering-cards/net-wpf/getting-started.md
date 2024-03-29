---
title: SDK .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 999f8ac3cd6a18fbbfc8b8bbdcf47465d8bb314f
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732731"
---
# <a name="getting-started---net-wpf"></a>Prise en main-WPF .NET

Comme nous l’avons décrit dans [prise en main](../../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle objet de carte sérialisée JSON. Cette bibliothèque permet de rendre facilement ce JSON dans l’interface utilisateur WPF que vous pouvez utiliser dans votre application.

## <a name="nuget-install"></a>Installation de NuGet

[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a>Xceed package d’entrée amélioré

Ce package facultatif améliore les contrôles d’entrée de carte adaptative au-delà de ce que WPF prête à l’emploi. Il a une dépendance sur`Extended.Wpf.Toolkit`

[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a>Exemple de visualiseur WPF

![Capture d’écran du visualiseur](../../../resources/media/tools/wpfvisualizer.png)

L' [exemple du visualiseur WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) vous permet de visualiser des cartes à l’aide de WPF.  Un `Host Config` éditeur est intégré pour la modification et l’affichage des paramètres de configuration de l’ordinateur hôte. Enregistrez ces paramètres en tant que JSON pour les utiliser dans le rendu de votre application.

## <a name="next-steps"></a>Étapes suivantes

Consultez [rendu d’une carte](render-a-card.md) pour les étapes suivantes.

---
title: Configuration de l’hôte-SDK iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34d28ef0f0cd7200965fb6967bb2f252f6a47456
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732931"
---
# <a name="host-config---ios"></a>Configuration de l’hôte-iOS

L’hôte peut être configuré par le biais de HostConfig qui peuvent être générés par une chaîne JSON

```objective-c
ACOParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
```

La valeur par défaut de HostConfig peut être instanciée

```objective-c
ACOHostConfig *defaultConfig = [[ACHostConfig alloc] init];
```

## <a name="render-a-card-using-host-config"></a>Rendu d’une carte à l’aide de la configuration d’hôte

Rederer utilise une carte adaptative et une configuration d’hôte. HostConfig peut être Nil et, s’il est Nil, la valeur par défaut est utilisée.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```
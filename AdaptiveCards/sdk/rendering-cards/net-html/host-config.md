---
title: Configuration de l’hôte-SDK HTML .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: a51b64f5f9783a187d7c3eb56c563a1d4497d3e2
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732821"
---
# <a name="host-config---net-html"></a>Configuration de l’hôte-HTML .NET

Une configuration d' [hôte](../../../rendering-cards/host-config.md) est un objet de configuration partagé que tous les convertisseurs comprennent. Cela vous permet de définir des styles courants (par exemple, famille de polices, tailles de police, espacement par défaut) et des comportements (par exemple, nombre maximal d’actions) qui seront interprétés automatiquement par chaque convertisseur de plateforme. 

L’objectif est que l’interface utilisateur native générée par chaque convertisseur de plateforme semble très similaire avec un minimum de travail de votre part.

```csharp
// Construct programmatically
renderer.HostConfig = new AdaptiveHostConfig() 
{
    FontFamily = "Comic Sans",
    FontSizes = {
        Small = 15,
        Default = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};

// Or parse from JSON
renderer.HostConfig  = AdaptiveHostConfig.FromJson(@"{
    ""fontFamily"": ""Comic Sans"",
    ""fontSizes"": {
        ""small"": 25,
        ""default"": 26,
        ""medium"": 27,
        ""large"": 28,
        ""extraLarge"": 29
    }
}");
```
---
title: Configuration de l’hôte-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 2828a379d8fda151b1cfca51e5898135186333ae
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733011"
---
# <a name="host-config---android"></a>Configuration de l’hôte-Android

Pour personnaliser le convertisseur, vous fournissez une instance de l’objet HostConfig. (Consultez [schéma de configuration](../../../rendering-cards/host-config.md) de l’hôte pour obtenir une description complète.)

Pour créer un objet HostConfig à partir d’une chaîne, utilisez la méthode DeserializeFromString

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```
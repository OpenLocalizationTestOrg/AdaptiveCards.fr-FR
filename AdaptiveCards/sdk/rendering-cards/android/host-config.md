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
# <a name="host-config---android"></a><span data-ttu-id="db3e5-102">Configuration de l’hôte-Android</span><span class="sxs-lookup"><span data-stu-id="db3e5-102">Host config - Android</span></span>

<span data-ttu-id="db3e5-103">Pour personnaliser le convertisseur, vous fournissez une instance de l’objet HostConfig.</span><span class="sxs-lookup"><span data-stu-id="db3e5-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="db3e5-104">(Consultez [schéma de configuration](../../../rendering-cards/host-config.md) de l’hôte pour obtenir une description complète.)</span><span class="sxs-lookup"><span data-stu-id="db3e5-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="db3e5-105">Pour créer un objet HostConfig à partir d’une chaîne, utilisez la méthode DeserializeFromString</span><span class="sxs-lookup"><span data-stu-id="db3e5-105">To Create a HostConfig object from a string, use the DeserializeFromString method</span></span>

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```
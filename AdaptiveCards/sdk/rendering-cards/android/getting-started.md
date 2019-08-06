---
title: Kit de développement logiciel Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 4723175bf94685c22d99fb15f3d1887ac37b8c57
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733006"
---
# <a name="getting-started---android"></a><span data-ttu-id="27504-102">Prise en main-Android</span><span class="sxs-lookup"><span data-stu-id="27504-102">Getting started - Android</span></span>

<span data-ttu-id="27504-103">Il s’agit d’un convertisseur qui cible les contrôles Android natifs.</span><span class="sxs-lookup"><span data-stu-id="27504-103">This is a renderer which targets Android native controls.</span></span>

## <a name="install-maven-package"></a><span data-ttu-id="27504-104">Installer le package Maven</span><span class="sxs-lookup"><span data-stu-id="27504-104">Install Maven package</span></span>

<span data-ttu-id="27504-105">[![Maven central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span><span class="sxs-lookup"><span data-stu-id="27504-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span></span>

<span data-ttu-id="27504-106">Vous pouvez trouver les packages publiés</span><span class="sxs-lookup"><span data-stu-id="27504-106">You can find the published packages</span></span> ![ici](https://search.maven.org/search?q=g:io.adaptivecards)

<span data-ttu-id="27504-108">Pour inclure la bibliothèque à votre projet, vous devez inclure cette ligne dans votre projet gradle. Build dans la section dépendances.</span><span class="sxs-lookup"><span data-stu-id="27504-108">To include library to your project you must include this line into your project gradle.build under the dependencies section</span></span>

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
<span data-ttu-id="27504-109">Vous devez modifier le numéro de version en fonction de la version que vous souhaitez inclure dans votre projet</span><span class="sxs-lookup"><span data-stu-id="27504-109">You need to change the version number depending on the version you want to include into your project</span></span>

## <a name="add-import"></a><span data-ttu-id="27504-110">Ajouter à l’importation</span><span class="sxs-lookup"><span data-stu-id="27504-110">Add import</span></span>

<span data-ttu-id="27504-111">Pour inclure le modèle objet, ajoutez cette importation</span><span class="sxs-lookup"><span data-stu-id="27504-111">To include the object model, add this import</span></span>

```
 import io.adaptivecards.objectmodel.*;
```

<span data-ttu-id="27504-112">Pour inclure le convertisseur, ajoutez cette importation</span><span class="sxs-lookup"><span data-stu-id="27504-112">To include the renderer, add this import</span></span>

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a><span data-ttu-id="27504-113">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="27504-113">Next steps</span></span>

<span data-ttu-id="27504-114">Consultez [rendu d’une carte](render-a-card.md) pour les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="27504-114">See [Render a card](render-a-card.md) for the next steps!</span></span>

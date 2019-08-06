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
# <a name="getting-started---android"></a>Prise en main-Android

Il s’agit d’un convertisseur qui cible les contrôles Android natifs.

## <a name="install-maven-package"></a>Installer le package Maven

[![Maven central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)

Vous pouvez trouver les packages publiés ![ici](https://search.maven.org/search?q=g:io.adaptivecards)

Pour inclure la bibliothèque à votre projet, vous devez inclure cette ligne dans votre projet gradle. Build dans la section dépendances.

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
Vous devez modifier le numéro de version en fonction de la version que vous souhaitez inclure dans votre projet

## <a name="add-import"></a>Ajouter à l’importation

Pour inclure le modèle objet, ajoutez cette importation

```
 import io.adaptivecards.objectmodel.*;
```

Pour inclure le convertisseur, ajoutez cette importation

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a>Étapes suivantes

Consultez [rendu d’une carte](render-a-card.md) pour les étapes suivantes.

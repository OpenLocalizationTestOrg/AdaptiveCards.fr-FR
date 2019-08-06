---
title: Feuille de route des cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: b11edbedca83bb26d2990d029a220165f68bc1ca
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733091"
---
# <a name="future-work"></a>Travail futur

Bien que nous ayons réalisé une excellente progression de la définition des cartes adaptatives, il y a toujours beaucoup de travail à faire. Notre espoir est que, par l’intermédiaire de communautés de développeurs actives comme botness et d’excellents partenaires tels que la marge et la Kik, nous pouvons créer un très grand écosystème de cartes multiplateformes.

## <a name="roadmap"></a>Présentation

Vous pouvez voir notre feuille [de route actuelle (non finale) ici](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog). Notez que tout ce qui se trouve ici peut faire l’objet de modifications et qu’il ne s’agit pas d’une garantie d’expédition.

## <a name="future-ideas"></a>Idées futures

Voici quelques idées futures, qui sont simplement à l’étape Brainstorm. Si vous êtes intéressé par ces derniers, faites-le nous savoir dans un commentaire.

### <a name="great-looking-cards-from-data"></a>Cartes attrayantes à partir des données

Nous savons que de nombreux auteurs de cartes possèdent déjà des données bien définies sous-jacentes à leurs cartes. Notre plan consiste à explorer un modèle de création de modèles qui permettrait la génération de cartes (côté serveur ou côté client) en fonction des données et d’un référentiel de modèles bien définis et personnalisables.

### <a name="make-cards-responsive"></a>Rendre les cartes réactives

Les dispositions de carte doivent être réactives pour libérer de l’espace. Les cartes adaptatives sont adaptables aux différents appareils, aux styles UX et aux infrastructures d’interface utilisateur, mais elles ne sont pas encore réactives. Des propriétés supplémentaires doivent être définies sur les éléments qui permettent aux producteurs de cartes de fournir les indications nécessaires aux bibliothèques de rendu afin qu’elles puissent modifier intelligemment la disposition d’une manière qui maintient l’objectif de la carte.

### <a name="responsive-exploration"></a>Exploration réactive

* Ajoutez une propriété **importance** qui annote l’importance du contenu. Le contenu moins important peut être supprimé pour tenir dans l’espace disponible
* Ajoutez des **contraintes** et des propriétés de **stratégie** décrivant comment réagir lorsque les contraintes ne peuvent pas être satisfaites. 
  * Masquer le contenu ou réduire le contenu à une taille plus petite.
  * Ajoutez un seuil qui, lorsqu’il est dépassé `columnSet` , passe au carrousel de colonnes.

### <a name="new-element-types"></a>Nouveaux types d’éléments

* Mount? -incorporer une carte dans une carte avec interactivité ou revenir à la bitmap
* *Quels éléments souhaitez-vous ou avez besoin*?

### <a name="new-rendering-libraries"></a>Nouvelles bibliothèques de rendu

* Réagir?
* Xamarin?
* *Quelles infrastructures souhaitez-vous?*

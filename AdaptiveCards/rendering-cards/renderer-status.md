---
title: État du convertisseur
author: matthidinger
ms.author: mahiding
ms.date: 10/12/2018
ms.topic: article
ms.openlocfilehash: 63426b2250407cc40af8c46975c10f57d1028a40
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733086"
---
# <a name="renderer-status"></a>État du convertisseur
Les tableaux ci-dessous indiquent l’état actuel de chaque convertisseur, en fonction de leurs versions publiées publiques.

### <a name="parsing"></a>Analyse

|Fonctionnalités | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Échecs de validation de retour | ✅ | ✅ | ✅ | ✅ | ✅ |
|Analyser les propriétés inconnues | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="card-rendering"></a>Rendu de la carte

|Fonctionnalités | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Vérifier la version prise en charge | ✅ | ✅ | ✅ | ✅ | ✅  |
|Rendre le schéma complet | ✅ | ✅ | ✅ | ✅ | ✅ |
|Barre des actions de rendu | ✅ | ✅ | ✅ | ✅ | ✅ |
|Ignorer les éléments inconnus | ✅ | ✅ | ✅ | ✅ | ✅ |
|Prise en charge de la configuration de l’hôte | ✅ | ✅ | ✅ | ✅ | ✅ |
|Style de plateforme Native | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="element-rendering"></a>Rendu des éléments

|Fonctionnalités | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Espacement et séparateur | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Format de DATE/heure de TextBlock](../authoring-cards/text-features.md#datetime-formatting-and-localization) | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Prise en charge de la démarque TextBlock](../authoring-cards/text-features.md#markdown) | ✅* | ✅ | ✅ | ✅ | ✅ |
|Prise en charge complète des entrées | ✅ | ✅ | ✅ | ✅ | ✅ |

\*Le convertisseur HTML n’inclut pas la prise en charge intégrée de la démarque afin de réduire la taille de la bibliothèque et de permettre aux applications consommatrices d’utiliser leur processeur de démarque par défaut. En revanche, le convertisseur HTML utilise automatiquement la démarque (s’il est chargé).

### <a name="extensibility"></a>Extensibilité

|Fonctionnalités | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Remplacer le convertisseur d’élément | ✅ | ✅ | ✅ | ✅ | ✅ |
|Ajouter un nouveau convertisseur d’élément | ✅ | ✅ | ✅ | ✅ | ✅ |
|Supprimer le convertisseur d’élément | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Remplacer/ajouter/supprimer le convertisseur d’action](https://github.com/Microsoft/AdaptiveCards/issues/1671) | ✅ | ✅ | ❌ | ✅ | ✅ |

### <a name="actions"></a>Actions

| Fonctionnalités | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
| Prise en charge d’action. OpenUrl | ✅ | ✅ | ✅ | ✅ | ✅  |
| Action. prise en charge ShowCard  | ✅ | ✅ | ✅ | ✅ | ✅ |
| Action. envoyer le support  | ✅ | ✅ | ✅ | ✅ | ✅  |
| support selectAction | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="events"></a>Events

|       Fonctionnalités        | HTML | .NET | UWP | iOS | Android | 
|----------------------------|------|------|-----|-----|---------|
| Visibilité de l’élément modifiée |  ✅   |  ❌   |  ❌  |  ❌  | ❌ |


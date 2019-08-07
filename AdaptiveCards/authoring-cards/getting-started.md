---
title: Prise en main
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: c9a0ad07ba5fefbcdc35239591c02fe0720b5b66
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732651"
---
# <a name="getting-started"></a>Prise en main 

Une carte adaptative est un modèle objet de carte sérialisée JSON.

## <a name="adaptive-card-structure"></a>Structure de carte adaptative

La structure de base d’une carte est la suivante:

* `AdaptiveCard`-L’objet racine décrit le AdaptiveCard lui-même, y compris sa composition d’éléments, ses actions, comment il doit être parlé et la version de schéma requise pour le rendre.
* `body`-Le corps de la carte est constitué de blocs de construction connus sous `elements`le nom de. Les éléments peuvent être composés dans des arrangements presque infinis pour créer de nombreux types de cartes. 
* `actions`-De nombreuses cartes possèdent un ensemble d’actions qu’un utilisateur peut effectuer. Cette propriété décrit les actions qui sont généralement rendues dans une «barre d’action» en bas.

### <a name="example-card"></a>Exemple de carte

Cet exemple de carte comprend une seule ligne de texte suivie d’une image.

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png"
        }
    ]
}
```

## <a name="type-property"></a>Propriété `Type`

Chaque élément a une `type` propriété qui identifie le type d’objet dont il s’agit. En examinant la carte ci-dessus, vous pouvez voir que nous avons `TextBlock` deux éléments `Image`, un et un.

Tous les éléments de carte adaptative sont empilés verticalement et **se développent jusqu’à la largeur de leur parent** ( `display: block` en HTML). Toutefois, vous pouvez utiliser un `ColumnSet` pour créer des colonnes côte à côte de conteneurs.

## <a name="adaptive-elements"></a>Éléments adaptatifs

Les éléments les plus fondamentaux sont les suivants:

* **TextBlock** -ajoute un bloc de texte avec des propriétés pour contrôler l’apparence du texte
* **Image** -ajoute une image avec des propriétés pour contrôler l’apparence de l’image

## <a name="container-elements"></a>Éléments de conteneur

Les cartes peuvent également avoir des conteneurs, qui réorganisent une collection d’éléments enfants.

* **Container** -définit une collection d’éléments
* **ColumnSet/Column** -définit une collection de colonnes, chaque colonne étant un conteneur
* **FactSet** -conteneur de faits
* **ImageSet** : conteneur d’images pour que l’interface utilisateur puisse afficher l’expérience de la Galerie de photos appropriée pour une collection d’images.

## <a name="input-elements"></a>Éléments d’entrée

Les éléments d’entrée vous permettent de demander à l’interface utilisateur native de générer des formulaires simples:

* **Input. Text** -obtient le contenu de texte de l’utilisateur
* **Input. date** : obtenir une date à partir de l’utilisateur
* **Input. Time** : obtenir une heure de l’utilisateur
* **Input. Number** -obtenir un numéro de l’utilisateur
* **Input. ChoiceSet** : donnez à l’utilisateur un ensemble de choix et faites-le choisir
* **Input. Toggle** : donne à l’utilisateur un choix unique entre deux éléments et les choisit

## <a name="actions"></a>Actions

Actions ajoutez des boutons à la carte. Elles peuvent effectuer diverses actions, telles que l’ouverture d’une URL ou l’envoi de données.

* **Action. OpenURL** : le bouton ouvre une URL externe pour l’affichage
* **Action. ShowCard** : demande une sous-carte à afficher à l’utilisateur.
* **Action. Submit** : demandez à tous les éléments d’entrée d’être regroupés dans un objet qui est ensuite envoyé via une méthode définie par l’application hôte.

> **Exemple d’action. Submit**: Avec Skype, une action. Submit envoie une activité bot Framework bot au bot avec la propriété **value** contenant un objet avec toutes les données d’entrée qui lui sont associées.

## <a name="learn-more"></a>En savoir plus

* [Parcourir les exemples de cartes](http://adaptivecards.io/samples/) pour l’inspiration
* Utiliser l' [Explorateur de schémas](http://adaptivecards.io/explorer) pour parcourir les éléments disponibles
* Créer une carte à l’aide du [visualiseur interactif](http://adaptivecards.io/visualizer/)
* [Soyez en contact](http://adaptivecards.io/connect) avec vos commentaires

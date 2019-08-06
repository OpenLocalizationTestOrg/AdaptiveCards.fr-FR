---
title: Implémentation d’un convertisseur
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: 607ce40e70e0e54e61a572853a521d2dd70a5c23
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732611"
---
# <a name="adaptive-card-renderer-specification"></a>Spécification du convertisseur de carte adaptative

La spécification suivante décrit comment implémenter un convertisseur de carte adaptative sur une plate-forme d’interface utilisateur.

> [!IMPORTANT]
> 
> Ce contenu n’est pas encore terminé. Revenez plus tard.

## <a name="sdk-versioning"></a>Contrôle de version du SDK

1. La version principale et la version mineure du `schema` SDK doivent correspondre à la version. 
1. Le correctif/la build **doit** être utilisé pour les mises à jour du convertisseur qui n’ont pas de modifications de schéma.

## <a name="parsing-json"></a>Analyser JSON

### <a name="error-conditions"></a>Conditions d’erreur
1. Un analyseur **doit** vérifier qu’il s’agit d’un contenu JSON valide
1. Un analyseur **doit** effectuer une validation par rapport au schéma (propriétés requises, etc.)
1. Les erreurs ci-dessus **doivent** être signalées à l’application hôte (exception ou équivalent)

### <a name="unknown-types"></a>Types inconnus
1. Si des «types» inconnus sont détectés, ils **doivent être supprimés** du résultat
1. Toute modification de la charge utile (comme ci-dessus) **doit** être signalée comme avertissement à l’application hôte

### <a name="unknown-properties"></a>Propriétés inconnues
1. Un analyseur **doit** inclure **des propriétés supplémentaires** sur les éléments

### <a name="additional-considerations"></a>Considérations supplémentaires
1. La `speak` propriété peut contenir le balisage SSML et **doit** être retournée à l’application hôte telle qu’elle est spécifiée

## <a name="parsing-host-config"></a>Analyse de la configuration de l’hôte
1. TODO

## <a name="versioning"></a>Gestion de version

1. Un convertisseur **doit** implémenter une version particulière du schéma. 
1. Le `AdaptiveCard` constructeur **doit** attribuer à `version` la propriété une valeur par défaut en fonction de la version du schéma actuel 
1. Si `version` un convertisseur rencontre une propriété dans le `AdaptiveCard` qui est supérieur à la version prise en charge, il **doit** retourner à la `fallbackText` place.

## <a name="rendering"></a>Rendu

Un `AdaptiveCard` est constitué d' `body` un `actions`et d’un. Est une collection de `CardElement`s qu’un convertisseur doit énumérer et afficher dans l’ordre. `body` 

1. Chaque élément **doit** s’étendre à la largeur de son parent ( `display: block` en HTML).
1. Un convertisseur **doit** ignorer les types d’éléments inconnus et continuer le rendu du reste de la charge utile.

### <a name="spacing-and-separators"></a>Espacement et séparateurs

1. La `spacing` propriété sur chaque élément influence la quantité d’espace entre l’élément **actuel** et celui qui le précède.
1. L’espacement ne doit s’appliquer **que** s’il est en réalité un élément qui le précède. (Par exemple, ne s’applique pas au premier élément d’un tableau)
1. Un convertisseur **doit** Rechercher la quantité d’espace à utiliser à partir de l' `hostConfig` espacement pour la valeur enum appliquée à l’élément actuel.
1. Si l’élément a `separator` la `true`valeur, une ligne visible **doit** être dessinée entre l’élément actuel et celui qui le précède.
1. La ligne de séparation **doit** être dessinée `container.style.default.foregroundColor`à l’aide de.
1. Un séparateur **doit** être dessiné uniquement si l’élément **n’est pas** le premier dans le tableau.

### <a name="columns"></a>Colonnes

1. `Column`Doit être interprété par «auto», «stretch» ou un rapport pondéré. `width`

### <a name="textblock"></a>TextBlock

1. Un TextBlock **doit** prendre une seule ligne, sauf si `wrap` la propriété `true`est. 
1. Le bloc de texte **doit** supprimer tout texte excédentaire avec des points de suspension (...)

#### <a name="markdown"></a>Markdown

1. Les cartes adaptatives autorisent un sous-ensemble de démarque et `TextBlock`doivent être prises en charge dans. 
1. Voir les [conditions requises](../authoring-cards/text-features.md) de la démarque complète

#### <a name="formatting-functions"></a>Fonctions de mise en forme

1. `TextBlock`autorise les [fonctions de mise en forme de date et d’heure](../authoring-cards/text-features.md) qui **doivent** être prises en charge sur chaque convertisseur.
1. **Toutes les défaillances doivent** afficher la chaîne brute dans la carte. Aucun message convivial n’a été tenté. (L’objectif est de permettre au développeur de savoir immédiatement qu’il y a un problème)

1. TODO: Inclure Regex

### <a name="images"></a>Images

1. Un convertisseur **doit** autoriser les applications hôtes à savoir quand toutes les images http ont été téléchargées et que la carte est «entièrement rendue»
1. Un convertisseur **doit** inspecter le paramètre de `maxImageSize` configuration de l’hôte lors du téléchargement des images http
1. Un convertisseur **doit** prendre en `.png` charge et`.jpeg`
1. Un convertisseur **doit** prendre en `.gif` charge les images

### <a name="host-config"></a>Configuration de l’hôte

* TODO: Que doivent être les valeurs par défaut? Doivent-ils tous les partager? Devons-nous incorporer un fichier hostConfig. JSON commun dans les fichiers binaires?
* TODO: Je pense que HostConfig a également besoin d’une version pour l’analyse?

[`HostConfig`](host-config.md)est un objet de configuration partagé qui spécifie la façon dont un convertisseur de carte adaptative génère l’interface utilisateur.  

Cela permet aux propriétés qui ne sont pas indépendantes de la plateforme d’être partagées entre les convertisseurs sur différents périphériques et plateformes. Il permet également de créer des outils qui vous donnent une idée de l’apparence de la carte pour un environnement donné.

1. Les convertisseurs **doivent** exposer un paramètre de **configuration d’hôte** pour héberger des applications
1. Un style **doit** être appliqué à tous les éléments en fonction de leurs paramètres de configuration d’hôte respectifs

### <a name="native-platform-styling"></a>Style de plateforme Native

1. Chaque type d’élément **doit** attacher un style de plateforme natif à l’élément d’interface utilisateur généré. Par exemple, dans le code HTML, nous avons ajouté une classe CSS aux types d’éléments et, en XAML, nous affectons un style spécifique.

## <a name="extensibility"></a>Extensibilité 

1. Un convertisseur **doit** autoriser les applications hôtes à remplacer les convertisseurs d’éléments par défaut. Par exemple, remplacez `TextBlock` le rendu par sa propre logique.
1. Un convertisseur **doit** autoriser les applications hôtes à inscrire des types d’éléments personnalisés. Par exemple, ajout de la prise en `Rating` charge d’un élément personnalisé
1. Un convertisseur **doit** autoriser les applications hôtes à supprimer la prise en charge d’un élément par défaut. Par exemple, supprimez `Action.Submit` -les s’ils ne souhaitent pas qu’ils soient pris en charge.

## <a name="actions"></a>Actions

1. Si HostConfig `supportsInteractivity` est `false`, un convertisseur **ne doit** afficher aucune action.
1. La `actions` propriété **doit** être rendue sous forme de boutons dans un type de barre d’action, généralement au bas de la carte. 
1. Quand un bouton est frappé, il **doit** permettre à l’application hôte de gérer l’événement. 
1. L’événement **doit** transmettre toutes les propriétés associées avec l’action
1. L’événement **doit** passer le `AdaptiveCard` qui a été exécuté

Action | Comportement
--- | ---
**Action.OpenUrl** | Ouvrir une URL externe pour l’affichage
**Action.ShowCard** | Demande une sous-carte à afficher à l’utilisateur.
**Action.Submit** | Demandez à ce que tous les éléments d’entrée soient regroupés dans un objet qui est ensuite envoyé via une méthode définie par l’application hôte.

### <a name="actionopenurl"></a>Action.OpenUrl
1. `Action.OpenUrl`**Doit** ouvrir une URL à l’aide du mécanisme de plateforme natif
1. Si ce n’est pas possible, il **doit** déclencher un événement à l’application hôte pour gérer l’ouverture de l’URL. Cet événement **doit** permettre à l’application hôte de remplacer le comportement par défaut. Par exemple, laissez-les ouvrir l’URL dans leur propre application.

### <a name="actionshowcard"></a>Action.ShowCard

1. `Action.ShowCard`**Doit** être pris en charge d’une certaine manière, en fonction du paramètre hostConfig. Il existe deux modes: inline et Popup. Les cartes en ligne **doivent** basculer automatiquement la visibilité de la carte. En mode contextuel, un événement **doit** être déclenché sur l’application hôte pour afficher la carte d’une certaine façon.

### <a name="actionsubmit"></a>Action. Submit

L’action Submit se comporte comme un envoi de formulaire HTML, sauf que lorsque le code HTML déclenche généralement une requête HTTP, les cartes adaptatives la laissent à chaque application hôte pour déterminer ce que signifie «envoi». 

1. Lorsque ce **doit** déclencher un événement, l’utilisateur appuie sur l’action appelée.  
1. La `data` propriété **doit** être incluse dans la charge utile de rappel.
1. Pour `Action.Submit`, un convertisseur **doit** rassembler toutes les entrées sur la carte et récupérer leurs valeurs. 

### <a name="selectaction"></a>selectAction

1. Si la configuration `supportedInteractivity` de `false` l’hôte `selectAction` est, un **ne doit pas être** rendu en tant que cible tactile.
1. `Image`, `ColumnSet`et `Column` offrent une`selectAction` propriété, qui **doit** être exécutée lorsque l’utilisateur l’appelle, par exemple, en appuyant sur l’élément.

## <a name="inputs"></a>Entrées

1. Si HostConfig `supportsInteractivity` est `false` un convertisseur **ne doit pas** afficher d’entrées.
2. Les entrées **doivent être** rendues avec la fidélité la plus élevée possible. Par exemple, un `Input.Date` peut idéalement offrir un sélecteur de dates à un utilisateur, mais si cela n’est pas possible sur la pile de l’interface utilisateur, le convertisseur **doit** revenir au rendu d’une zone de texte standard.
3. Un convertisseur **doit** afficher le `placeholderText` si possible
4. Un convertisseur **n’a pas** à implémenter la validation de l’entrée. Les utilisateurs de cartes adaptatives doivent prévoir de valider toutes les données reçues à leur extrémité.
5. La liaison de la valeur d’entrée **doit** être correctement placée dans une séquence d’échappement

6. L’objet **doit** être retourné à l’application hôte comme suit:

   Nous n’offrons aucune promesse de validation d’entrée dans les cartes adaptatives, c’est pourquoi il s’agit de la partie réceptrice pour analyser correctement la réponse. Par exemple, une entrée. Number pourrait renvoyer «Hello» et doit être préparé pour cela.


## <a name="events"></a>Events

1. Un convertisseur **doit** déclencher un événement lorsque la visibilité d’un élément a changé, ce qui permet à l’application hôte de faire défiler la carte vers la position.

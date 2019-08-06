---
title: Vue d’ensemble des cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d62bae9259a45dd828028e4f866d18fc75924b0c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733111"
---
# <a name="adaptive-cards-overview"></a>Vue d’ensemble des cartes adaptatives 

Les cartes adaptatives sont un format d’échange de cartes ouvert qui permet aux développeurs d’échanger du contenu d’interface utilisateur de manière commune et cohérente.

<video controls width="100%" poster="./content/videoposter.png">
    <source src="https://adaptivecardsblob.blob.core.windows.net/assets/AdaptiveCardsOverviewVideo.mp4" type="video/mp4">
</video>

## <a name="how-they-work"></a>Fonctionnement

Les [**auteurs de cartes**](authoring-cards/getting-started.md) décrivent leur contenu sous la forme d’un objet JSON simple. Ce contenu peut ensuite être rendu en mode natif dans une [**application hôte**](rendering-cards/getting-started.md), ce qui s’adapte automatiquement à l’apparence et à la convivialité de l’hôte.

Par exemple, contoso bot peut créer une carte adaptative via l’infrastructure bot et, lorsqu’elle est remise à Skype, elle ressemble à une carte Skype. Lorsque cette même charge utile est envoyée à Microsoft Teams, elle est semblable à celle de Microsoft Teams. Au fur et à mesure que d’autres applications hôtes commencent à prendre en charge les cartes adaptatives, cette même charge s’illumine automatiquement dans ces applications, tout en restant totalement natives pour l’application.

Les utilisateurs gagnent, car tout se sent familier. Les applications hôtes gagnent parce qu’elles contrôlent l’expérience utilisateur. Et les auteurs de cartes gagnent, car leur contenu obtient une portée plus large sans aucun travail supplémentaire.

## <a name="goals"></a>Objectifs 

Les objectifs des cartes adaptatives sont les suivants:

* **Portable** -vers n’importe quelle application, périphérique et infrastructure d’interface utilisateur
* **Open** -Libraries and Schema sont Open source et Shared
* **Faible coût** -facile à définir, facile à utiliser
* **Expressif** -ciblé à la fin du contenu que les développeurs souhaitent produire
* **Purement déclaratifs** -aucun code n’est nécessaire ou autorisé
* **Styles automatiquement** vers l’expérience utilisateur et les directives de la personnalisation de l’application hôte

## <a name="for-card-authors"></a>Pour les auteurs de cartes
Les cartes adaptatives sont idéales pour les auteurs de cartes:

* **Un schéma** : vous recevez un seul format, ce qui réduit le coût de la création d’une carte et l’optimisation du nombre d’emplacements qu’elle peut utiliser.
* **Expression plus riche** : votre contenu peut s’aligner plus étroitement avec les choix que vous souhaitez, car vous avez une palette plus riche avec laquelle peindre.
* **Large portée** : votre contenu fonctionnera sur un ensemble plus large d’applications sans avoir à apprendre de nouveaux schémas.
* **Contrôles d’entrée** : votre carte peut inclure des contrôles d’entrée pour la collecte d’informations auprès de l’utilisateur qui consulte la carte.
* **Amélioration des outils** : un écosystème de cartes ouvert signifie de meilleurs outils partagés par tout le monde.

## <a name="for-experience-owners"></a>Pour les propriétaires de l’expérience
Si vous êtes un développeur d’applications qui souhaite exploiter un écosystème de contenu tiers, vous apprécierez les cartes adaptatives car:

* **Expérience utilisateur cohérente** : vous garantissez une expérience cohérente pour vos utilisateurs, car vous êtes propriétaire du style de la carte rendue.
* **Performances natives** : vous bénéficiez de performances natives, car il cible directement votre infrastructure d’interface utilisateur.
* **Safe** : le contenu est distribué dans des charges utiles sûres. vous n’avez donc pas besoin d’ouvrir votre infrastructure d’interface utilisateur dans un balisage brut et un script.
* **Facile à implémenter** : vous pouvez utiliser les bibliothèques de l’étagère pour une intégration facile sur toute plateforme que vous prenez en charge. 
* **Documentation gratuite** : vous gagnez du temps, car vous n’avez pas besoin d’inventer, d’implémenter et de documenter un schéma propriétaire.
* **Outils partagés** : vous gagnez du temps, car vous n’êtes pas obligé de créer des outils personnalisés.

## <a name="core-design-principles"></a>Principes de conception de base 

Les cartes adaptatives sont pilotées par un ensemble de [principes de guidage](resources/principles.md) qui ont été utiles pour maintenir la conception sur piste. 

### <a name="semantic-instead-of-pixel-perfect"></a>Sémantique au lieu de pixel-parfait
Nous nous efforçons autant que possible d’utiliser des valeurs et des concepts sémantiques au lieu de la disposition pure pixel-Perfect parfaite. Les exemples d’expressions sémantiques apparaissent dans les couleurs, les tailles et les éléments tels que FactSet et ImageSet. Tout cela permet à l’application hôte de prendre de meilleures décisions sur l’apparence réelle.

### <a name="card-authors-own-the-content-host-app-owns-the-look-and-feel"></a>Les auteurs de cartes possèdent le contenu, l’application hôte possède l’apparence et la convivialité
Les auteurs de cartes possèdent ce qu’ils veulent, mais l’application qui l’affiche est l’apparence et la convivialité de la carte dans le contexte de leur application.

### <a name="keep-it-simple-but-expressive"></a>Restez simple, mais expressif
Nous souhaitons que les cartes adaptatives soient expressifs et à usage général, mais nous ne souhaitons pas créer une infrastructure d’interface utilisateur.  L’objectif est de créer une couche intermédiaire qui est «suffisamment expressif» de la même façon que la démarque est suffisamment expressif pour les documents.

En mettant l’accent sur la simplicité et l’expressivité, la démarque a créé une description simple et cohérente du contenu du document.  De la même façon, nous pensons que les cartes adaptatives peuvent créer un moyen simple et expressif de décrire le contenu de la carte.

### <a name="when-in-doubt-keep-it-out"></a>En cas de doute, faites-le
Il est plus facile de l’ajouter ultérieurement, puis d’être en ligne avec une erreur. Si nous avons découvert que nous nous sommes penchés sur l’ajout ou non d’un événement, nous avons choisi de le sortir.  Il est toujours plus facile d’ajouter une propriété que de vivre avec un héritage que nous ne souhaitons pas avoir à prendre en charge.


## <a name="build-2018-session"></a>Build 2018 session

La session suivante de la build 2018 met en évidence des cartes adaptatives dans les robots, Cortana, Outlook et Windows. 

<iframe src="https://medius.studios.ms/Embed/Video/BRK2401?SFYT=true" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

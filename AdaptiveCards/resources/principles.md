---
title: Motivations et principes
author: matthidinger
ms.author: mahiding
ms.date: 5/14/2018
ms.topic: article
ms.openlocfilehash: 243ad63fc585c5afc3fa396b86ff6261e8a7ee93
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732561"
---
# <a name="motivations-and-principles"></a>Motivations et principes

Vous trouverez ci-dessous les motivations et les principes govering l’évolution du format de carte adaptative.

## <a name="motivations-behind-the-format"></a>Motivations derrière le format

Au début du 2016, plusieurs équipes de Microsoft (y compris Outlook, Windows et l’infrastructure de robot) sont parvenues à la réalisation de tout ce qu’elles souhaitaient tout à fait similaires («cartes») et que chacune d’elles conçoit indépendamment leurs propres solutions:

- Windows avait son propre format de vignettes et de notifications dynamiques
-  L’infrastructure bot utilisait un ensemble de modèles de carte prédéfinis que les développeurs peuvent choisir lors de l’envoi de messages de bot
- Outlook utilisait son propre format MessageCard pour sa fonctionnalité de messages actionnables

En même temps, d’autres plateformes, telles que LINE, FaceBook Messenger, la marge, etc., définissent leur propre format «carte» propriétaire. Par conséquent, quelques employés de Microsoft ont rassemblé et commencé un effort pour définir un format de carte unique et ouvert, ainsi qu’un ensemble de kits de développement logiciel (SDK) qui:

- Faciliterait l’échange de cartes entre les hôtes
- Permet à chaque hôte de garder le contrôle sur le style des cartes pour garantir la cohérence visuelle
- Permet à une application hôte d’afficher facilement des cartes avec un minimum d’effort via des kits de développement logiciel (SDK) prêts à l’emploi
- Et cela fournirait également de la valeur à des tiers et finit par être largement adopté par le secteur

## <a name="principles-governing-adaptive-cards"></a>Principes régissant les cartes adaptatives

1.  **La carte adaptative est un format de carte _simple_ et _déclaratif_**

    1.  Elle n’est pas destinée à être un remplacement ou une alternative HTML ou XAML
    2.  Il n’y a **pas de «code-behind»** avec les cartes adaptatives
        1. Les auteurs de cartes ne peuvent pas incorporer de code personnalisé/arbitraire avec leurs charges utiles, et par conséquent, un hôte de carte adaptative n’a jamais besoin d’exécuter du code tiers.
        2. Dynamisme et l’interactivité sont atteints uniquement via le balisage déclaratif
    3.  Cela garantit que l’effort nécessaire pour créer un kit de développement logiciel (SDK) de carte adaptative pour une nouvelle plateforme demeure raisonnable

2.  **Le format carte adaptative ne peut pas imposer l’utilisation d’une technologie sous-jacente particulière.**

    1.  Le format de carte adaptative ne repose pas sur JavaScript, C#, Python ou tout autre langage
    2.  De même, il ne repose pas sur HTML ou XAML, ni sur toute autre infrastructure graphique/d’interface utilisateur
    3.  Ainsi, les cartes adaptatives peuvent être rendues en mode natif sur n’importe quelle plateforme tant qu’un convertisseur existe

3.  **Le format de carte adaptative est une _propriété partagée_**

    1.  Avec ses kits de développement logiciel (SDK), le format doit être open source et sa communauté évolutive
    2.  Le format n’est donc pas détenu ni piloté par une équipe

4.  **Le format de carte adaptative n’est pas conçu «uniquement pour l’utilisation de Microsoft»**

    1.  Au lieu de cela, il est conçu pour répondre aux besoins d’un large éventail d’applications et de cas d’utilisation

5.  **Le _groupe de travail carte adaptative_ régit l’évolution du format**

    1.  Ce groupe de travail se compose d’un ensemble d’employés Microsoft qui sont tous impliqués dans la réussite du format
    2.  Le groupe de travail effectue des réunions hebdomadaires (actuellement le lundi) au cours desquelles les propositions de fonctionnalités sont revues, les problèmes ouverts sont discutés et l’avancement global des éléments de travail vNext est suivi
    3.  Le groupe de travail utilise les commentaires de la communauté à grande échelle, y compris les équipes Microsoft internes, pour décider de la façon dont le format évolue
        1. Tout le monde peut participer au groupe de travail en ouvrant des problèmes dans GitHub (voir ci-dessous)
        2. Les problèmes/demandes de fonctionnalités enracinés dans l’utilisation réelle de l’infrastructure des cartes adaptatives (en tant qu’ordinateur hôte ou en tant qu’auteur de la carte) ont le plus d’impact sur l’avenir du format
    4.  Pour être approuvé par le groupe de travail, les nouvelles fonctionnalités proposées sont les suivantes:
        1. Doivent être justifiées par des cas d’usage de la vie réelle
        2. Doit avoir une spécification fonctionnelle
    5.  Une nouvelle fonctionnalité approuvée est ajoutée au backlog et est prise en compte pour vNext
        1. Les critères utilisés pour hiérarchiser les nouvelles fonctionnalités incluent l’ampleur des scénarios que la fonctionnalité active, sa complexité/maintenabilité et bien plus encore.
        2. En cas de doute, n’oubliez pas! Il est beaucoup plus facile d’introduire une fonctionnalité bien conçue plus tard que de vivre avec une erreur infinie.
    6.  Toutes les nouvelles fonctionnalités sont implémentées dans tous les kits de développement logiciel pris en charge
    7.  Toutes les nouvelles fonctionnalités sont documentées et associées à une carte de test publiée dans le dossier Samples.
    8.  Les nouvelles versions du format et des kits de développement logiciel (SDK) passent par une phase bêta
    9.  La planification de publication du schéma de carte adaptative et des versions du kit de développement logiciel (SDK) est motivée par la qualité, pas la date

6.  **Interopérabilité**
    1.  Les cartes créées conformément au format documenté (par exemple, n’utilisant aucune extension spécifique à l’hôte) s’affichent correctement dans n’importe quel ordinateur hôte qui prend en charge les cartes adaptatives.
    2.  Les seules exceptions à ces principes sont les suivantes:
        1.  Certains hôtes n’autorisent pas l’interactivité et n’affichent donc pas les entrées et les actions
        2.  L’exécution de l’action. les actions d’envoi sont à la discrétion de l’hôte, et tous les ordinateurs hôtes ne gèrent pas nécessairement toutes les actions. soumettre les charges utiles. En outre, certains hôtes peuvent ne pas prendre en charge l’action. soumettre du tout

7.  **Le format doit être extensible**

    1.  Les hôtes doivent avoir la liberté d’ajouter la prise en charge des éléments personnalisés ou des actions personnalisées qui vont au-delà de ce que le format est capable
    2.  Ceci est particulièrement important pour les actions, car différents hôtes ne prennent pas nécessairement en charge le même ensemble d’actions.
    3.  Ces ajouts sont à la discrétion de l’hôte
        1. Il ne s’agit pas d’un ajout *de facto* à la spécification de carte adaptative
        2. Par conséquent, ils rendent une charge utile qui les utilise incompatible avec le format de carte adaptative standard.
        3. Elles peuvent toutefois être présentées au groupe de travail et proposées en tant que nouvelles fonctionnalités pour une version future du format, comme décrit au point #5

8.  **Les auteurs de cartes possèdent le contenu, les applications hôtes possèdent l’apparence et la convivialité**

    1.  Les applications hôtes imposent leur style afin que les cartes aient l’air d’être des extensions natives de l’expérience de l’application
    2.  Les auteurs de cartes peuvent toujours spécifier le style, mais uniquement via des expressions sémantiques de couleurs, de tailles, etc.

9.  **Les kits de développement logiciel (SDK) seront fournis pour les plateformes de développement les plus populaires**

    1.  Les kits de développement logiciel (SDK) facilitent le rendu des charges utiles de cartes adaptatives dans n’importe quel hôte
    2.  Cela garantit que la barrière à l’entrée est aussi faible que possible pour les développeurs tiers et les équipes Microsoft

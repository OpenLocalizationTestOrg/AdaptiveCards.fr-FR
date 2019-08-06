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
# <a name="future-work"></a><span data-ttu-id="44eec-102">Travail futur</span><span class="sxs-lookup"><span data-stu-id="44eec-102">Future work</span></span>

<span data-ttu-id="44eec-103">Bien que nous ayons réalisé une excellente progression de la définition des cartes adaptatives, il y a toujours beaucoup de travail à faire.</span><span class="sxs-lookup"><span data-stu-id="44eec-103">While we have made excellent progress defining adaptive cards, there is still lots of work to do.</span></span> <span data-ttu-id="44eec-104">Notre espoir est que, par l’intermédiaire de communautés de développeurs actives comme botness et d’excellents partenaires tels que la marge et la Kik, nous pouvons créer un très grand écosystème de cartes multiplateformes.</span><span class="sxs-lookup"><span data-stu-id="44eec-104">Our hope is that through active developer communities like botness, and great partners like Slack and Kik, we can create a great ecosystem of cross-platform cards.</span></span>

## <a name="roadmap"></a><span data-ttu-id="44eec-105">Présentation</span><span class="sxs-lookup"><span data-stu-id="44eec-105">Roadmap</span></span>

<span data-ttu-id="44eec-106">Vous pouvez voir notre feuille [de route actuelle (non finale) ici](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span><span class="sxs-lookup"><span data-stu-id="44eec-106">You can see our [current (non-final) roadmap here](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span></span> <span data-ttu-id="44eec-107">Notez que tout ce qui se trouve ici peut faire l’objet de modifications et qu’il ne s’agit pas d’une garantie d’expédition.</span><span class="sxs-lookup"><span data-stu-id="44eec-107">Note that anything on here is subject to change, and is not a guarantee of shipping.</span></span>

## <a name="future-ideas"></a><span data-ttu-id="44eec-108">Idées futures</span><span class="sxs-lookup"><span data-stu-id="44eec-108">Future ideas</span></span>

<span data-ttu-id="44eec-109">Voici quelques idées futures, qui sont simplement à l’étape Brainstorm.</span><span class="sxs-lookup"><span data-stu-id="44eec-109">The following are some future ideas we have, which are simply in the brainstorm stage.</span></span> <span data-ttu-id="44eec-110">Si vous êtes intéressé par ces derniers, faites-le nous savoir dans un commentaire.</span><span class="sxs-lookup"><span data-stu-id="44eec-110">If you're interested in any of these, let us know in a comment.</span></span>

### <a name="great-looking-cards-from-data"></a><span data-ttu-id="44eec-111">Cartes attrayantes à partir des données</span><span class="sxs-lookup"><span data-stu-id="44eec-111">Great looking Cards from Data</span></span>

<span data-ttu-id="44eec-112">Nous savons que de nombreux auteurs de cartes possèdent déjà des données bien définies sous-jacentes à leurs cartes.</span><span class="sxs-lookup"><span data-stu-id="44eec-112">We know many card authors already have well-defined data behind their cards.</span></span> <span data-ttu-id="44eec-113">Notre plan consiste à explorer un modèle de création de modèles qui permettrait la génération de cartes (côté serveur ou côté client) en fonction des données et d’un référentiel de modèles bien définis et personnalisables.</span><span class="sxs-lookup"><span data-stu-id="44eec-113">Our plan is to explore a templating model that would allow cards to be generated (server side or client side) based on the data and a repository of well-defined and customizable templates.</span></span>

### <a name="make-cards-responsive"></a><span data-ttu-id="44eec-114">Rendre les cartes réactives</span><span class="sxs-lookup"><span data-stu-id="44eec-114">Make cards responsive</span></span>

<span data-ttu-id="44eec-115">Les dispositions de carte doivent être réactives pour libérer de l’espace.</span><span class="sxs-lookup"><span data-stu-id="44eec-115">Card layouts should be reactive to available space.</span></span> <span data-ttu-id="44eec-116">Les cartes adaptatives sont adaptables aux différents appareils, aux styles UX et aux infrastructures d’interface utilisateur, mais elles ne sont pas encore réactives.</span><span class="sxs-lookup"><span data-stu-id="44eec-116">Adaptive cards are adaptable to different devices, ux styles and and ui frameworks, but they are not reactive yet.</span></span> <span data-ttu-id="44eec-117">Des propriétés supplémentaires doivent être définies sur les éléments qui permettent aux producteurs de cartes de fournir les indications nécessaires aux bibliothèques de rendu afin qu’elles puissent modifier intelligemment la disposition d’une manière qui maintient l’objectif de la carte.</span><span class="sxs-lookup"><span data-stu-id="44eec-117">Additional properties must be defined on elements which allow card producers to provide the necessary hints to the rendering libraries so that they can intelligently change the layout in a way which maintains the intent of the card.</span></span>

### <a name="responsive-exploration"></a><span data-ttu-id="44eec-118">Exploration réactive</span><span class="sxs-lookup"><span data-stu-id="44eec-118">Responsive exploration</span></span>

* <span data-ttu-id="44eec-119">Ajoutez une propriété **importance** qui annote l’importance du contenu.</span><span class="sxs-lookup"><span data-stu-id="44eec-119">Add an **importance** property which annotates importance of content.</span></span> <span data-ttu-id="44eec-120">Le contenu moins important peut être supprimé pour tenir dans l’espace disponible</span><span class="sxs-lookup"><span data-stu-id="44eec-120">Less important content can be dropped to fit available space</span></span>
* <span data-ttu-id="44eec-121">Ajoutez des **contraintes** et des propriétés de **stratégie** décrivant comment réagir lorsque les contraintes ne peuvent pas être satisfaites.</span><span class="sxs-lookup"><span data-stu-id="44eec-121">Add **constraints** and **policy** properties describing how to react when constraints can't be met.</span></span> 
  * <span data-ttu-id="44eec-122">Masquer le contenu ou réduire le contenu à une taille plus petite.</span><span class="sxs-lookup"><span data-stu-id="44eec-122">Hide content or collapse content to smaller size.</span></span>
  * <span data-ttu-id="44eec-123">Ajoutez un seuil qui, lorsqu’il est dépassé `columnSet` , passe au carrousel de colonnes.</span><span class="sxs-lookup"><span data-stu-id="44eec-123">Add a threshold that, when exceeded, changes `columnSet` to carousel of columns.</span></span>

### <a name="new-element-types"></a><span data-ttu-id="44eec-124">Nouveaux types d’éléments</span><span class="sxs-lookup"><span data-stu-id="44eec-124">New element types</span></span>

* <span data-ttu-id="44eec-125">Mount?</span><span class="sxs-lookup"><span data-stu-id="44eec-125">Maps?</span></span> <span data-ttu-id="44eec-126">-incorporer une carte dans une carte avec interactivité ou revenir à la bitmap</span><span class="sxs-lookup"><span data-stu-id="44eec-126">- embed a map into a card with interactivity or fallback to bitmap</span></span>
* <span data-ttu-id="44eec-127">*Quels éléments souhaitez-vous ou avez besoin*?</span><span class="sxs-lookup"><span data-stu-id="44eec-127">*What elements do you want or need*?</span></span>

### <a name="new-rendering-libraries"></a><span data-ttu-id="44eec-128">Nouvelles bibliothèques de rendu</span><span class="sxs-lookup"><span data-stu-id="44eec-128">New rendering libraries</span></span>

* <span data-ttu-id="44eec-129">Réagir?</span><span class="sxs-lookup"><span data-stu-id="44eec-129">React?</span></span>
* <span data-ttu-id="44eec-130">Xamarin?</span><span class="sxs-lookup"><span data-stu-id="44eec-130">Xamarin?</span></span>
* <span data-ttu-id="44eec-131">*Quelles infrastructures souhaitez-vous?*</span><span class="sxs-lookup"><span data-stu-id="44eec-131">*What frameworks do you want?*</span></span>

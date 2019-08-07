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
# <a name="getting-started"></a><span data-ttu-id="c400a-102">Prise en main</span><span class="sxs-lookup"><span data-stu-id="c400a-102">Getting Started</span></span> 

<span data-ttu-id="c400a-103">Une carte adaptative est un modèle objet de carte sérialisée JSON.</span><span class="sxs-lookup"><span data-stu-id="c400a-103">An Adaptive Card is a JSON-serialized card object model.</span></span>

## <a name="adaptive-card-structure"></a><span data-ttu-id="c400a-104">Structure de carte adaptative</span><span class="sxs-lookup"><span data-stu-id="c400a-104">Adaptive Card structure</span></span>

<span data-ttu-id="c400a-105">La structure de base d’une carte est la suivante:</span><span class="sxs-lookup"><span data-stu-id="c400a-105">The basic structure of a card is as follows:</span></span>

* <span data-ttu-id="c400a-106">`AdaptiveCard`-L’objet racine décrit le AdaptiveCard lui-même, y compris sa composition d’éléments, ses actions, comment il doit être parlé et la version de schéma requise pour le rendre.</span><span class="sxs-lookup"><span data-stu-id="c400a-106">`AdaptiveCard` - The root object describes the AdaptiveCard itself, including its element makeup, its actions, how it should be spoken, and the schema version required to render it.</span></span>
* <span data-ttu-id="c400a-107">`body`-Le corps de la carte est constitué de blocs de construction connus sous `elements`le nom de.</span><span class="sxs-lookup"><span data-stu-id="c400a-107">`body` - The body of the card is made up of building-blocks known as `elements`.</span></span> <span data-ttu-id="c400a-108">Les éléments peuvent être composés dans des arrangements presque infinis pour créer de nombreux types de cartes.</span><span class="sxs-lookup"><span data-stu-id="c400a-108">Elements can be composed in nearly infinite arrangements to create many types of cards.</span></span> 
* <span data-ttu-id="c400a-109">`actions`-De nombreuses cartes possèdent un ensemble d’actions qu’un utilisateur peut effectuer.</span><span class="sxs-lookup"><span data-stu-id="c400a-109">`actions` - Many cards have a set of actions a user may take on it.</span></span> <span data-ttu-id="c400a-110">Cette propriété décrit les actions qui sont généralement rendues dans une «barre d’action» en bas.</span><span class="sxs-lookup"><span data-stu-id="c400a-110">This property describes those actions which typically get rendered in an "action bar" at the bottom.</span></span>

### <a name="example-card"></a><span data-ttu-id="c400a-111">Exemple de carte</span><span class="sxs-lookup"><span data-stu-id="c400a-111">Example Card</span></span>

<span data-ttu-id="c400a-112">Cet exemple de carte comprend une seule ligne de texte suivie d’une image.</span><span class="sxs-lookup"><span data-stu-id="c400a-112">This sample card which includes a single line of text followed by an image.</span></span>

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

## <a name="type-property"></a><span data-ttu-id="c400a-113">Propriété `Type`</span><span class="sxs-lookup"><span data-stu-id="c400a-113">`Type` property</span></span>

<span data-ttu-id="c400a-114">Chaque élément a une `type` propriété qui identifie le type d’objet dont il s’agit.</span><span class="sxs-lookup"><span data-stu-id="c400a-114">Every element has a `type` property which identifies what kind of object it is.</span></span> <span data-ttu-id="c400a-115">En examinant la carte ci-dessus, vous pouvez voir que nous avons `TextBlock` deux éléments `Image`, un et un.</span><span class="sxs-lookup"><span data-stu-id="c400a-115">Looking at the above card, you can see we have two elements, a `TextBlock` and an `Image`.</span></span>

<span data-ttu-id="c400a-116">Tous les éléments de carte adaptative sont empilés verticalement et **se développent jusqu’à la largeur de leur parent** ( `display: block` en HTML).</span><span class="sxs-lookup"><span data-stu-id="c400a-116">All Adaptive Card elements **stack vertically** and **expand to the width of their parent** (think `display: block` in HTML).</span></span> <span data-ttu-id="c400a-117">Toutefois, vous pouvez utiliser un `ColumnSet` pour créer des colonnes côte à côte de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="c400a-117">However, you can use a `ColumnSet` to create side-by-side columns of containers.</span></span>

## <a name="adaptive-elements"></a><span data-ttu-id="c400a-118">Éléments adaptatifs</span><span class="sxs-lookup"><span data-stu-id="c400a-118">Adaptive Elements</span></span>

<span data-ttu-id="c400a-119">Les éléments les plus fondamentaux sont les suivants:</span><span class="sxs-lookup"><span data-stu-id="c400a-119">The most fundamental elements are:</span></span>

* <span data-ttu-id="c400a-120">**TextBlock** -ajoute un bloc de texte avec des propriétés pour contrôler l’apparence du texte</span><span class="sxs-lookup"><span data-stu-id="c400a-120">**TextBlock** - adds a block of text with properties to control what the text looks like</span></span>
* <span data-ttu-id="c400a-121">**Image** -ajoute une image avec des propriétés pour contrôler l’apparence de l’image</span><span class="sxs-lookup"><span data-stu-id="c400a-121">**Image** - adds an image with properties to control what the image looks like</span></span>

## <a name="container-elements"></a><span data-ttu-id="c400a-122">Éléments de conteneur</span><span class="sxs-lookup"><span data-stu-id="c400a-122">Container elements</span></span>

<span data-ttu-id="c400a-123">Les cartes peuvent également avoir des conteneurs, qui réorganisent une collection d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="c400a-123">Cards can also have containers, which arrange a collection of child elements.</span></span>

* <span data-ttu-id="c400a-124">**Container** -définit une collection d’éléments</span><span class="sxs-lookup"><span data-stu-id="c400a-124">**Container** - Defines a a collection of elements</span></span>
* <span data-ttu-id="c400a-125">**ColumnSet/Column** -définit une collection de colonnes, chaque colonne étant un conteneur</span><span class="sxs-lookup"><span data-stu-id="c400a-125">**ColumnSet/Column** - Defines a collection of columns, each column is a container</span></span>
* <span data-ttu-id="c400a-126">**FactSet** -conteneur de faits</span><span class="sxs-lookup"><span data-stu-id="c400a-126">**FactSet** - Container of Facts</span></span>
* <span data-ttu-id="c400a-127">**ImageSet** : conteneur d’images pour que l’interface utilisateur puisse afficher l’expérience de la Galerie de photos appropriée pour une collection d’images.</span><span class="sxs-lookup"><span data-stu-id="c400a-127">**ImageSet** - Container of Images so that UI can show appropriate photo gallery experience for a collection of images.</span></span>

## <a name="input-elements"></a><span data-ttu-id="c400a-128">Éléments d’entrée</span><span class="sxs-lookup"><span data-stu-id="c400a-128">Input elements</span></span>

<span data-ttu-id="c400a-129">Les éléments d’entrée vous permettent de demander à l’interface utilisateur native de générer des formulaires simples:</span><span class="sxs-lookup"><span data-stu-id="c400a-129">Input elements allow you to ask for native UI to build simple forms:</span></span>

* <span data-ttu-id="c400a-130">**Input. Text** -obtient le contenu de texte de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c400a-130">**Input.Text** - get text content from the user</span></span>
* <span data-ttu-id="c400a-131">**Input. date** : obtenir une date à partir de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c400a-131">**Input.Date** - get a Date from the user</span></span>
* <span data-ttu-id="c400a-132">**Input. Time** : obtenir une heure de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c400a-132">**Input.Time** - get a Time from the user</span></span>
* <span data-ttu-id="c400a-133">**Input. Number** -obtenir un numéro de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c400a-133">**Input.Number** - get a Number from the user</span></span>
* <span data-ttu-id="c400a-134">**Input. ChoiceSet** : donnez à l’utilisateur un ensemble de choix et faites-le choisir</span><span class="sxs-lookup"><span data-stu-id="c400a-134">**Input.ChoiceSet** - Give the user a set of choices and have them pick</span></span>
* <span data-ttu-id="c400a-135">**Input. Toggle** : donne à l’utilisateur un choix unique entre deux éléments et les choisit</span><span class="sxs-lookup"><span data-stu-id="c400a-135">**Input.Toggle** - Give the user a single choice between two items and have them pick</span></span>

## <a name="actions"></a><span data-ttu-id="c400a-136">Actions</span><span class="sxs-lookup"><span data-stu-id="c400a-136">Actions</span></span>

<span data-ttu-id="c400a-137">Actions ajoutez des boutons à la carte.</span><span class="sxs-lookup"><span data-stu-id="c400a-137">Actions add buttons to the card.</span></span> <span data-ttu-id="c400a-138">Elles peuvent effectuer diverses actions, telles que l’ouverture d’une URL ou l’envoi de données.</span><span class="sxs-lookup"><span data-stu-id="c400a-138">These can perform a variety of actions, like opening a URL or submitting some data.</span></span>

* <span data-ttu-id="c400a-139">**Action. OpenURL** : le bouton ouvre une URL externe pour l’affichage</span><span class="sxs-lookup"><span data-stu-id="c400a-139">**Action.OpenUrl** - the button opens an external URL for viewing</span></span>
* <span data-ttu-id="c400a-140">**Action. ShowCard** : demande une sous-carte à afficher à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c400a-140">**Action.ShowCard** - Requests a sub-card to be shown to the user.</span></span>
* <span data-ttu-id="c400a-141">**Action. Submit** : demandez à tous les éléments d’entrée d’être regroupés dans un objet qui est ensuite envoyé via une méthode définie par l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="c400a-141">**Action.Submit** - Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

> <span data-ttu-id="c400a-142">**Exemple d’action. Submit**: Avec Skype, une action. Submit envoie une activité bot Framework bot au bot avec la propriété **value** contenant un objet avec toutes les données d’entrée qui lui sont associées.</span><span class="sxs-lookup"><span data-stu-id="c400a-142">**Example Action.Submit**: With Skype, an Action.Submit will send a Bot Framework bot activity back to the bot with the **Value** property containing an object with all of the input data on it.</span></span>

## <a name="learn-more"></a><span data-ttu-id="c400a-143">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="c400a-143">Learn More</span></span>

* <span data-ttu-id="c400a-144">[Parcourir les exemples de cartes](http://adaptivecards.io/samples/) pour l’inspiration</span><span class="sxs-lookup"><span data-stu-id="c400a-144">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="c400a-145">Utiliser l' [Explorateur de schémas](http://adaptivecards.io/explorer) pour parcourir les éléments disponibles</span><span class="sxs-lookup"><span data-stu-id="c400a-145">Use the [Schema Explorer](http://adaptivecards.io/explorer) to browse the available elements</span></span>
* <span data-ttu-id="c400a-146">Créer une carte à l’aide du [visualiseur interactif](http://adaptivecards.io/visualizer/)</span><span class="sxs-lookup"><span data-stu-id="c400a-146">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/)</span></span>
* <span data-ttu-id="c400a-147">[Soyez en contact](http://adaptivecards.io/connect) avec vos commentaires</span><span class="sxs-lookup"><span data-stu-id="c400a-147">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>

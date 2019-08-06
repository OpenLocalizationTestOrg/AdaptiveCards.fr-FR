---
title: Styles natifs-SDK HTML .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 5b829d9eefe933f133c8532030856849802c5eb5
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732836"
---
# <a name="native-styling---net-html"></a><span data-ttu-id="320d2-102">Styles natifs-HTML .NET</span><span class="sxs-lookup"><span data-stu-id="320d2-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="320d2-103">Bien que la configuration de l’hôte vous permette d’accéder à la plupart des cas sur chaque plateforme, il est probable que vous deviez effectuer des styles natifs sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="320d2-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="320d2-104">Le langage HTML facilite cette tâche en ajoutant des classes CSS à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="320d2-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="320d2-105">Élément</span><span class="sxs-lookup"><span data-stu-id="320d2-105">Element</span></span> | <span data-ttu-id="320d2-106">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="320d2-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="320d2-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="320d2-107">AdaptiveCard</span></span> | <span data-ttu-id="320d2-108">ac-adaptivecard</span><span class="sxs-lookup"><span data-stu-id="320d2-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="320d2-109">Toutes les actions</span><span class="sxs-lookup"><span data-stu-id="320d2-109">All Actions</span></span> | <span data-ttu-id="320d2-110">ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="320d2-110">ac-pushButton</span></span> | 
| <span data-ttu-id="320d2-111">Sélectionner des actions</span><span class="sxs-lookup"><span data-stu-id="320d2-111">Select Actions</span></span> | <span data-ttu-id="320d2-112">AC-sélectionnable</span><span class="sxs-lookup"><span data-stu-id="320d2-112">ac-selectable</span></span> |
| <span data-ttu-id="320d2-113">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="320d2-113">Action.OpenUrl</span></span>  | <span data-ttu-id="320d2-114">ac-action-openUrl</span><span class="sxs-lookup"><span data-stu-id="320d2-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="320d2-115">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="320d2-115">Action.ShowCard</span></span> | <span data-ttu-id="320d2-116">ac-action-showCard</span><span class="sxs-lookup"><span data-stu-id="320d2-116">ac-action-showCard</span></span> |
| <span data-ttu-id="320d2-117">Action. Submit</span><span class="sxs-lookup"><span data-stu-id="320d2-117">Action.Submit</span></span>  | <span data-ttu-id="320d2-118">ac-action-submit</span><span class="sxs-lookup"><span data-stu-id="320d2-118">ac-action-submit</span></span>  |
| <span data-ttu-id="320d2-119">ActionSet</span><span class="sxs-lookup"><span data-stu-id="320d2-119">ActionSet</span></span> | <span data-ttu-id="320d2-120">ac-actionset</span><span class="sxs-lookup"><span data-stu-id="320d2-120">ac-actionset</span></span> |
| <span data-ttu-id="320d2-121">Colonne</span><span class="sxs-lookup"><span data-stu-id="320d2-121">Column</span></span> | <span data-ttu-id="320d2-122">AC-Column</span><span class="sxs-lookup"><span data-stu-id="320d2-122">ac-column</span></span> |
| <span data-ttu-id="320d2-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="320d2-123">ColumnSet</span></span> | <span data-ttu-id="320d2-124">AC-columnset</span><span class="sxs-lookup"><span data-stu-id="320d2-124">ac-columnset</span></span> |
| <span data-ttu-id="320d2-125">Conteneur</span><span class="sxs-lookup"><span data-stu-id="320d2-125">Container</span></span> | <span data-ttu-id="320d2-126">AC-Container</span><span class="sxs-lookup"><span data-stu-id="320d2-126">ac-container</span></span> |
| <span data-ttu-id="320d2-127">Toutes les entrées</span><span class="sxs-lookup"><span data-stu-id="320d2-127">All Inputs</span></span> | <span data-ttu-id="320d2-128">entrée c.a.</span><span class="sxs-lookup"><span data-stu-id="320d2-128">ac-input</span></span> |
| <span data-ttu-id="320d2-129">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="320d2-129">Input.ChoiceSet</span></span> | <span data-ttu-id="320d2-130">ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="320d2-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="320d2-131">Input.Date</span><span class="sxs-lookup"><span data-stu-id="320d2-131">Input.Date</span></span> | <span data-ttu-id="320d2-132">ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="320d2-132">ac-dateInput</span></span> |
| <span data-ttu-id="320d2-133">Entrée. nombre</span><span class="sxs-lookup"><span data-stu-id="320d2-133">Input.Number</span></span> | <span data-ttu-id="320d2-134">ac-numberInput</span><span class="sxs-lookup"><span data-stu-id="320d2-134">ac-numberInput</span></span> |
| <span data-ttu-id="320d2-135">Input.Text</span><span class="sxs-lookup"><span data-stu-id="320d2-135">Input.Text</span></span> | <span data-ttu-id="320d2-136">ac-textInput</span><span class="sxs-lookup"><span data-stu-id="320d2-136">ac-textInput</span></span> |
| <span data-ttu-id="320d2-137">Input.Time</span><span class="sxs-lookup"><span data-stu-id="320d2-137">Input.Time</span></span> | <span data-ttu-id="320d2-138">ac-timeInput</span><span class="sxs-lookup"><span data-stu-id="320d2-138">ac-timeInput</span></span> |
| <span data-ttu-id="320d2-139">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="320d2-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="320d2-140">Image</span><span class="sxs-lookup"><span data-stu-id="320d2-140">Image</span></span>  | <span data-ttu-id="320d2-141">ac-image</span><span class="sxs-lookup"><span data-stu-id="320d2-141">ac-image</span></span> |
| <span data-ttu-id="320d2-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="320d2-142">ImageSet</span></span>  | <span data-ttu-id="320d2-143">ac-imageset</span><span class="sxs-lookup"><span data-stu-id="320d2-143">ac-imageset</span></span> |
| <span data-ttu-id="320d2-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="320d2-144">FactSet</span></span> | <span data-ttu-id="320d2-145">AC-FactSet</span><span class="sxs-lookup"><span data-stu-id="320d2-145">ac-factset</span></span> |
| <span data-ttu-id="320d2-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="320d2-146">TextBlock</span></span>  | <span data-ttu-id="320d2-147">ac-textblock</span><span class="sxs-lookup"><span data-stu-id="320d2-147">ac-textblock</span></span> |
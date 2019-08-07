---
title: Style natif-Kit de développement logiciel (SDK) UWP
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: 565c61535adc5b316cb8b1f3ad77e511012e7612
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732541"
---
# <a name="native-styling---uwp"></a><span data-ttu-id="80b27-102">Style natif-UWP</span><span class="sxs-lookup"><span data-stu-id="80b27-102">Native styling - UWP</span></span>

<span data-ttu-id="80b27-103">Bien que la configuration de l’hôte vous permette d’accéder à la plupart des cas sur chaque plateforme, il est probable que vous deviez effectuer des styles natifs sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="80b27-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="80b27-104">UWP facilite cette tâche en vous permettant de transmettre un ResourceDictionary pour un style, un comportement, des animations, etc. précis.</span><span class="sxs-lookup"><span data-stu-id="80b27-104">UWP makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="80b27-105">Élément</span><span class="sxs-lookup"><span data-stu-id="80b27-105">Element</span></span> | <span data-ttu-id="80b27-106">Noms de style</span><span class="sxs-lookup"><span data-stu-id="80b27-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="80b27-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="80b27-107">AdaptiveCard</span></span> | <span data-ttu-id="80b27-108">Adaptive.Card</span><span class="sxs-lookup"><span data-stu-id="80b27-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="80b27-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="80b27-109">Action.OpenUrl</span></span>  | <span data-ttu-id="80b27-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="80b27-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="80b27-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="80b27-111">Action.ShowCard</span></span> | <span data-ttu-id="80b27-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="80b27-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="80b27-113">Action. Submit</span><span class="sxs-lookup"><span data-stu-id="80b27-113">Action.Submit</span></span>  | <span data-ttu-id="80b27-114">Adaptive.Action.Submit</span><span class="sxs-lookup"><span data-stu-id="80b27-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="80b27-115">Colonne</span><span class="sxs-lookup"><span data-stu-id="80b27-115">Column</span></span> | <span data-ttu-id="80b27-116">Adaptive.Column, Adaptive.Action.Tap</span><span class="sxs-lookup"><span data-stu-id="80b27-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="80b27-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="80b27-117">ColumnSet</span></span> | <span data-ttu-id="80b27-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="80b27-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="80b27-119">Conteneur</span><span class="sxs-lookup"><span data-stu-id="80b27-119">Container</span></span> | <span data-ttu-id="80b27-120">Adaptive.Container</span><span class="sxs-lookup"><span data-stu-id="80b27-120">Adaptive.Container</span></span>|
| <span data-ttu-id="80b27-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="80b27-121">Input.ChoiceSet</span></span> | <span data-ttu-id="80b27-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="80b27-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="80b27-123">Input.Date</span><span class="sxs-lookup"><span data-stu-id="80b27-123">Input.Date</span></span> | <span data-ttu-id="80b27-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="80b27-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="80b27-125">Entrée. nombre</span><span class="sxs-lookup"><span data-stu-id="80b27-125">Input.Number</span></span> | <span data-ttu-id="80b27-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="80b27-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="80b27-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="80b27-127">Input.Text</span></span> | <span data-ttu-id="80b27-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="80b27-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="80b27-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="80b27-129">Input.Time</span></span> | <span data-ttu-id="80b27-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="80b27-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="80b27-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="80b27-131">Input.Toggle</span></span>| <span data-ttu-id="80b27-132">Adaptive.Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="80b27-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="80b27-133">Image</span><span class="sxs-lookup"><span data-stu-id="80b27-133">Image</span></span>  | <span data-ttu-id="80b27-134">Adaptive.Image</span><span class="sxs-lookup"><span data-stu-id="80b27-134">Adaptive.Image</span></span> |
| <span data-ttu-id="80b27-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="80b27-135">ImageSet</span></span>  | <span data-ttu-id="80b27-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="80b27-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="80b27-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="80b27-137">FactSet</span></span> | <span data-ttu-id="80b27-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="80b27-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="80b27-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="80b27-139">TextBlock</span></span>  | <span data-ttu-id="80b27-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="80b27-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="80b27-141">Cet exemple de dictionnaire de ressources XAML définit l’arrière-plan de tous les TextBlocks sur Aqua.</span><span class="sxs-lookup"><span data-stu-id="80b27-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="80b27-142">Vous souhaiterez probablement une plus grande avancée que celle-ci😁</span><span class="sxs-lookup"><span data-stu-id="80b27-142">You will probably want something more advanced than this 😁</span></span>

```xml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;
```

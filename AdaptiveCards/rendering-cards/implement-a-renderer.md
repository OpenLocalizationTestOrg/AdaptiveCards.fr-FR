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
# <a name="adaptive-card-renderer-specification"></a><span data-ttu-id="a4537-102">Spécification du convertisseur de carte adaptative</span><span class="sxs-lookup"><span data-stu-id="a4537-102">Adaptive Card Renderer Specification</span></span>

<span data-ttu-id="a4537-103">La spécification suivante décrit comment implémenter un convertisseur de carte adaptative sur une plate-forme d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a4537-103">The following specification describes how implement an Adaptive Card renderer on any UI platform.</span></span>

> [!IMPORTANT]
> 
> <span data-ttu-id="a4537-104">Ce contenu n’est pas encore terminé.</span><span class="sxs-lookup"><span data-stu-id="a4537-104">This content is not finished yet.</span></span> <span data-ttu-id="a4537-105">Revenez plus tard.</span><span class="sxs-lookup"><span data-stu-id="a4537-105">Check back shortly.</span></span>

## <a name="sdk-versioning"></a><span data-ttu-id="a4537-106">Contrôle de version du SDK</span><span class="sxs-lookup"><span data-stu-id="a4537-106">SDK Versioning</span></span>

1. <span data-ttu-id="a4537-107">La version principale et la version mineure du `schema` SDK doivent correspondre à la version.</span><span class="sxs-lookup"><span data-stu-id="a4537-107">The SDK major and minor version **SHOULD** match the `schema` version.</span></span> 
1. <span data-ttu-id="a4537-108">Le correctif/la build **doit** être utilisé pour les mises à jour du convertisseur qui n’ont pas de modifications de schéma.</span><span class="sxs-lookup"><span data-stu-id="a4537-108">Patch/build **SHOULD** be used for renderer updates that don't have schema changes.</span></span>

## <a name="parsing-json"></a><span data-ttu-id="a4537-109">Analyser JSON</span><span class="sxs-lookup"><span data-stu-id="a4537-109">Parsing JSON</span></span>

### <a name="error-conditions"></a><span data-ttu-id="a4537-110">Conditions d’erreur</span><span class="sxs-lookup"><span data-stu-id="a4537-110">Error conditions</span></span>
1. <span data-ttu-id="a4537-111">Un analyseur **doit** vérifier qu’il s’agit d’un contenu JSON valide</span><span class="sxs-lookup"><span data-stu-id="a4537-111">A parser **MUST** check that it's valid JSON content</span></span>
1. <span data-ttu-id="a4537-112">Un analyseur **doit** effectuer une validation par rapport au schéma (propriétés requises, etc.)</span><span class="sxs-lookup"><span data-stu-id="a4537-112">A parser **MUST** validate against the schema (required properties, etc)</span></span>
1. <span data-ttu-id="a4537-113">Les erreurs ci-dessus **doivent** être signalées à l’application hôte (exception ou équivalent)</span><span class="sxs-lookup"><span data-stu-id="a4537-113">The above errors **MUST** be reported to the host app (exception or equivalent)</span></span>

### <a name="unknown-types"></a><span data-ttu-id="a4537-114">Types inconnus</span><span class="sxs-lookup"><span data-stu-id="a4537-114">Unknown types</span></span>
1. <span data-ttu-id="a4537-115">Si des «types» inconnus sont détectés, ils **doivent être supprimés** du résultat</span><span class="sxs-lookup"><span data-stu-id="a4537-115">If unknown "types" are encountered they **MUST BE DROPPED** from the result</span></span>
1. <span data-ttu-id="a4537-116">Toute modification de la charge utile (comme ci-dessus) **doit** être signalée comme avertissement à l’application hôte</span><span class="sxs-lookup"><span data-stu-id="a4537-116">Any alterations of the payload (like above) **SHOULD** be reported as warnings to the host app</span></span>

### <a name="unknown-properties"></a><span data-ttu-id="a4537-117">Propriétés inconnues</span><span class="sxs-lookup"><span data-stu-id="a4537-117">Unknown properties</span></span>
1. <span data-ttu-id="a4537-118">Un analyseur **doit** inclure **des propriétés supplémentaires** sur les éléments</span><span class="sxs-lookup"><span data-stu-id="a4537-118">A parser **MUST** include **additional** properties on elements</span></span>

### <a name="additional-considerations"></a><span data-ttu-id="a4537-119">Considérations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a4537-119">Additional considerations</span></span>
1. <span data-ttu-id="a4537-120">La `speak` propriété peut contenir le balisage SSML et **doit** être retournée à l’application hôte telle qu’elle est spécifiée</span><span class="sxs-lookup"><span data-stu-id="a4537-120">The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified</span></span>

## <a name="parsing-host-config"></a><span data-ttu-id="a4537-121">Analyse de la configuration de l’hôte</span><span class="sxs-lookup"><span data-stu-id="a4537-121">Parsing Host Config</span></span>
1. <span data-ttu-id="a4537-122">TODO</span><span class="sxs-lookup"><span data-stu-id="a4537-122">TODO</span></span>

## <a name="versioning"></a><span data-ttu-id="a4537-123">Gestion de version</span><span class="sxs-lookup"><span data-stu-id="a4537-123">Versioning</span></span>

1. <span data-ttu-id="a4537-124">Un convertisseur **doit** implémenter une version particulière du schéma.</span><span class="sxs-lookup"><span data-stu-id="a4537-124">A renderer **MUST** implement a particular version of the schema.</span></span> 
1. <span data-ttu-id="a4537-125">Le `AdaptiveCard` constructeur **doit** attribuer à `version` la propriété une valeur par défaut en fonction de la version du schéma actuel</span><span class="sxs-lookup"><span data-stu-id="a4537-125">The `AdaptiveCard` constructor **MUST** give the `version` property a default value based on the current schema version</span></span> 
1. <span data-ttu-id="a4537-126">Si `version` un convertisseur rencontre une propriété dans le `AdaptiveCard` qui est supérieur à la version prise en charge, il **doit** retourner à la `fallbackText` place.</span><span class="sxs-lookup"><span data-stu-id="a4537-126">If a renderer encounters a `version` property in the `AdaptiveCard` that is higher than the supported version, it **MUST** return the `fallbackText` instead.</span></span>

## <a name="rendering"></a><span data-ttu-id="a4537-127">Rendu</span><span class="sxs-lookup"><span data-stu-id="a4537-127">Rendering</span></span>

<span data-ttu-id="a4537-128">Un `AdaptiveCard` est constitué d' `body` un `actions`et d’un.</span><span class="sxs-lookup"><span data-stu-id="a4537-128">An `AdaptiveCard` consists of a `body` and `actions`.</span></span> <span data-ttu-id="a4537-129">Est une collection de `CardElement`s qu’un convertisseur doit énumérer et afficher dans l’ordre. `body`</span><span class="sxs-lookup"><span data-stu-id="a4537-129">The `body` is a collection of `CardElement`s that a renderer will enumerate and render in order.</span></span> 

1. <span data-ttu-id="a4537-130">Chaque élément **doit** s’étendre à la largeur de son parent ( `display: block` en HTML).</span><span class="sxs-lookup"><span data-stu-id="a4537-130">Each Element **MUST** stretch to the width of its parent (think `display: block` in HTML).</span></span>
1. <span data-ttu-id="a4537-131">Un convertisseur **doit** ignorer les types d’éléments inconnus et continuer le rendu du reste de la charge utile.</span><span class="sxs-lookup"><span data-stu-id="a4537-131">A renderer **MUST** ignore unknown element types, and continue rendering the rest of the payload.</span></span>

### <a name="spacing-and-separators"></a><span data-ttu-id="a4537-132">Espacement et séparateurs</span><span class="sxs-lookup"><span data-stu-id="a4537-132">Spacing and Separators</span></span>

1. <span data-ttu-id="a4537-133">La `spacing` propriété sur chaque élément influence la quantité d’espace entre l’élément **actuel** et celui qui le précède.</span><span class="sxs-lookup"><span data-stu-id="a4537-133">The `spacing` property on every element influences the amount of space between the **CURRENT** element and the one **BEFORE** it.</span></span>
1. <span data-ttu-id="a4537-134">L’espacement ne doit s’appliquer **que** s’il est en réalité un élément qui le précède.</span><span class="sxs-lookup"><span data-stu-id="a4537-134">Spacing **MUST ONLY** apply when there actually is an element preceding it.</span></span> <span data-ttu-id="a4537-135">(Par exemple, ne s’applique pas au premier élément d’un tableau)</span><span class="sxs-lookup"><span data-stu-id="a4537-135">(E.g., won't apply to the first item in an array)</span></span>
1. <span data-ttu-id="a4537-136">Un convertisseur **doit** Rechercher la quantité d’espace à utiliser à partir de l' `hostConfig` espacement pour la valeur enum appliquée à l’élément actuel.</span><span class="sxs-lookup"><span data-stu-id="a4537-136">A renderer **MUST** look up the amount of space to use from the `hostConfig` spacing for the enum value applied to the current element.</span></span>
1. <span data-ttu-id="a4537-137">Si l’élément a `separator` la `true`valeur, une ligne visible **doit** être dessinée entre l’élément actuel et celui qui le précède.</span><span class="sxs-lookup"><span data-stu-id="a4537-137">If the element has a `separator` value of `true`, then a visible line **MUST** be drawn between the current element and the one before it.</span></span>
1. <span data-ttu-id="a4537-138">La ligne de séparation **doit** être dessinée `container.style.default.foregroundColor`à l’aide de.</span><span class="sxs-lookup"><span data-stu-id="a4537-138">The separator line **MUST** be drawn using the `container.style.default.foregroundColor`.</span></span>
1. <span data-ttu-id="a4537-139">Un séparateur **doit** être dessiné uniquement si l’élément **n’est pas** le premier dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="a4537-139">A separator **MUST ONLY** be drawn if the item **IS NOT** the first in the array.</span></span>

### <a name="columns"></a><span data-ttu-id="a4537-140">Colonnes</span><span class="sxs-lookup"><span data-stu-id="a4537-140">Columns</span></span>

1. <span data-ttu-id="a4537-141">`Column`Doit être interprété par «auto», «stretch» ou un rapport pondéré. `width`</span><span class="sxs-lookup"><span data-stu-id="a4537-141">`Column` `width` **MUST** be interpreted by "auto", "stretch" or a weighted ratio.</span></span>

### <a name="textblock"></a><span data-ttu-id="a4537-142">TextBlock</span><span class="sxs-lookup"><span data-stu-id="a4537-142">TextBlock</span></span>

1. <span data-ttu-id="a4537-143">Un TextBlock **doit** prendre une seule ligne, sauf si `wrap` la propriété `true`est.</span><span class="sxs-lookup"><span data-stu-id="a4537-143">A TextBlock **MUST** take up a single line unless the `wrap` property is `true`.</span></span> 
1. <span data-ttu-id="a4537-144">Le bloc de texte **doit** supprimer tout texte excédentaire avec des points de suspension (...)</span><span class="sxs-lookup"><span data-stu-id="a4537-144">The text block **SHOULD** trim any excess text with an ellipsis (...)</span></span>

#### <a name="markdown"></a><span data-ttu-id="a4537-145">Markdown</span><span class="sxs-lookup"><span data-stu-id="a4537-145">Markdown</span></span>

1. <span data-ttu-id="a4537-146">Les cartes adaptatives autorisent un sous-ensemble de démarque et `TextBlock`doivent être prises en charge dans.</span><span class="sxs-lookup"><span data-stu-id="a4537-146">Adaptive Cards allow for a subset of Markdown and **SHOULD** be supported in `TextBlock`.</span></span> 
1. <span data-ttu-id="a4537-147">Voir les [conditions requises](../authoring-cards/text-features.md) de la démarque complète</span><span class="sxs-lookup"><span data-stu-id="a4537-147">See full [markdown requirements](../authoring-cards/text-features.md)</span></span>

#### <a name="formatting-functions"></a><span data-ttu-id="a4537-148">Fonctions de mise en forme</span><span class="sxs-lookup"><span data-stu-id="a4537-148">Formatting functions</span></span>

1. <span data-ttu-id="a4537-149">`TextBlock`autorise les [fonctions de mise en forme de date et d’heure](../authoring-cards/text-features.md) qui **doivent** être prises en charge sur chaque convertisseur.</span><span class="sxs-lookup"><span data-stu-id="a4537-149">`TextBlock` allows [DATE/TIME formatting functions](../authoring-cards/text-features.md) that **MUST** be supported on every renderer.</span></span>
1. <span data-ttu-id="a4537-150">**Toutes les défaillances doivent** afficher la chaîne brute dans la carte.</span><span class="sxs-lookup"><span data-stu-id="a4537-150">**ALL FAILURES MUST** display the raw string in the card.</span></span> <span data-ttu-id="a4537-151">Aucun message convivial n’a été tenté.</span><span class="sxs-lookup"><span data-stu-id="a4537-151">No friendly message attempted.</span></span> <span data-ttu-id="a4537-152">(L’objectif est de permettre au développeur de savoir immédiatement qu’il y a un problème)</span><span class="sxs-lookup"><span data-stu-id="a4537-152">(The goal being to make the developer immediately aware there is a problem)</span></span>

1. <span data-ttu-id="a4537-153">TODO: Inclure Regex</span><span class="sxs-lookup"><span data-stu-id="a4537-153">TODO: Include regex</span></span>

### <a name="images"></a><span data-ttu-id="a4537-154">Images</span><span class="sxs-lookup"><span data-stu-id="a4537-154">Images</span></span>

1. <span data-ttu-id="a4537-155">Un convertisseur **doit** autoriser les applications hôtes à savoir quand toutes les images http ont été téléchargées et que la carte est «entièrement rendue»</span><span class="sxs-lookup"><span data-stu-id="a4537-155">A renderer **SHOULD** allow host apps to know when all HTTP images have been downloaded and the card is "fully rendered"</span></span>
1. <span data-ttu-id="a4537-156">Un convertisseur **doit** inspecter le paramètre de `maxImageSize` configuration de l’hôte lors du téléchargement des images http</span><span class="sxs-lookup"><span data-stu-id="a4537-156">A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images</span></span>
1. <span data-ttu-id="a4537-157">Un convertisseur **doit** prendre en `.png` charge et`.jpeg`</span><span class="sxs-lookup"><span data-stu-id="a4537-157">A renderer **MUST** support `.png` and `.jpeg`</span></span>
1. <span data-ttu-id="a4537-158">Un convertisseur **doit** prendre en `.gif` charge les images</span><span class="sxs-lookup"><span data-stu-id="a4537-158">A renderer **SHOULD** support `.gif` images</span></span>

### <a name="host-config"></a><span data-ttu-id="a4537-159">Configuration de l’hôte</span><span class="sxs-lookup"><span data-stu-id="a4537-159">Host Config</span></span>

* <span data-ttu-id="a4537-160">TODO: Que doivent être les valeurs par défaut?</span><span class="sxs-lookup"><span data-stu-id="a4537-160">TODO: What should the defaults be?</span></span> <span data-ttu-id="a4537-161">Doivent-ils tous les partager?</span><span class="sxs-lookup"><span data-stu-id="a4537-161">Should they all share it?</span></span> <span data-ttu-id="a4537-162">Devons-nous incorporer un fichier hostConfig. JSON commun dans les fichiers binaires?</span><span class="sxs-lookup"><span data-stu-id="a4537-162">Should we embed a common hostConfig.json file in the binaries?</span></span>
* <span data-ttu-id="a4537-163">TODO: Je pense que HostConfig a également besoin d’une version pour l’analyse?</span><span class="sxs-lookup"><span data-stu-id="a4537-163">TODO: I think HostConfig needs to be versioned as well for parsing?</span></span>

<span data-ttu-id="a4537-164">[`HostConfig`](host-config.md)est un objet de configuration partagé qui spécifie la façon dont un convertisseur de carte adaptative génère l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a4537-164">[`HostConfig`](host-config.md) is a shared configuration object that specifies how an Adaptive Card Renderer generates UI.</span></span>  

<span data-ttu-id="a4537-165">Cela permet aux propriétés qui ne sont pas indépendantes de la plateforme d’être partagées entre les convertisseurs sur différents périphériques et plateformes.</span><span class="sxs-lookup"><span data-stu-id="a4537-165">This allows properties which are platform agnostic to be shared among renderers on different platforms and devices.</span></span> <span data-ttu-id="a4537-166">Il permet également de créer des outils qui vous donnent une idée de l’apparence de la carte pour un environnement donné.</span><span class="sxs-lookup"><span data-stu-id="a4537-166">It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.</span></span>

1. <span data-ttu-id="a4537-167">Les convertisseurs **doivent** exposer un paramètre de **configuration d’hôte** pour héberger des applications</span><span class="sxs-lookup"><span data-stu-id="a4537-167">Renderers **MUST** expose a **Host Config** parameter to host apps</span></span>
1. <span data-ttu-id="a4537-168">Un style **doit** être appliqué à tous les éléments en fonction de leurs paramètres de configuration d’hôte respectifs</span><span class="sxs-lookup"><span data-stu-id="a4537-168">All elements **MUST** be styled according to their respective Host Config settings</span></span>

### <a name="native-platform-styling"></a><span data-ttu-id="a4537-169">Style de plateforme Native</span><span class="sxs-lookup"><span data-stu-id="a4537-169">Native platform styling</span></span>

1. <span data-ttu-id="a4537-170">Chaque type d’élément **doit** attacher un style de plateforme natif à l’élément d’interface utilisateur généré.</span><span class="sxs-lookup"><span data-stu-id="a4537-170">Each element type **SHOULD** attach a native platform style with the generated UI element.</span></span> <span data-ttu-id="a4537-171">Par exemple, dans le code HTML, nous avons ajouté une classe CSS aux types d’éléments et, en XAML, nous affectons un style spécifique.</span><span class="sxs-lookup"><span data-stu-id="a4537-171">E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.</span></span>

## <a name="extensibility"></a><span data-ttu-id="a4537-172">Extensibilité</span><span class="sxs-lookup"><span data-stu-id="a4537-172">Extensibility</span></span> 

1. <span data-ttu-id="a4537-173">Un convertisseur **doit** autoriser les applications hôtes à remplacer les convertisseurs d’éléments par défaut.</span><span class="sxs-lookup"><span data-stu-id="a4537-173">A renderer **MUST** allow host apps to override default element renderers.</span></span> <span data-ttu-id="a4537-174">Par exemple, remplacez `TextBlock` le rendu par sa propre logique.</span><span class="sxs-lookup"><span data-stu-id="a4537-174">E.g., replace `TextBlock` rendering with their own logic.</span></span>
1. <span data-ttu-id="a4537-175">Un convertisseur **doit** autoriser les applications hôtes à inscrire des types d’éléments personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a4537-175">A renderer **MUST** allow host apps to register custom element types.</span></span> <span data-ttu-id="a4537-176">Par exemple, ajout de la prise en `Rating` charge d’un élément personnalisé</span><span class="sxs-lookup"><span data-stu-id="a4537-176">E.g., add support for a custom `Rating` element</span></span>
1. <span data-ttu-id="a4537-177">Un convertisseur **doit** autoriser les applications hôtes à supprimer la prise en charge d’un élément par défaut.</span><span class="sxs-lookup"><span data-stu-id="a4537-177">A renderer **MUST** allow host apps to remove support for a default element.</span></span> <span data-ttu-id="a4537-178">Par exemple, supprimez `Action.Submit` -les s’ils ne souhaitent pas qu’ils soient pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a4537-178">E.g., remove `Action.Submit` if they don't want it supported.</span></span>

## <a name="actions"></a><span data-ttu-id="a4537-179">Actions</span><span class="sxs-lookup"><span data-stu-id="a4537-179">Actions</span></span>

1. <span data-ttu-id="a4537-180">Si HostConfig `supportsInteractivity` est `false`, un convertisseur **ne doit** afficher aucune action.</span><span class="sxs-lookup"><span data-stu-id="a4537-180">If HostConfig `supportsInteractivity` is `false`, a renderer **MUST NOT** render any actions.</span></span>
1. <span data-ttu-id="a4537-181">La `actions` propriété **doit** être rendue sous forme de boutons dans un type de barre d’action, généralement au bas de la carte.</span><span class="sxs-lookup"><span data-stu-id="a4537-181">The `actions` property **MUST** be rendered as buttons in some kind of action bar, usually at the bottom of the card.</span></span> 
1. <span data-ttu-id="a4537-182">Quand un bouton est frappé, il **doit** permettre à l’application hôte de gérer l’événement.</span><span class="sxs-lookup"><span data-stu-id="a4537-182">When a button is tapped it **MUST** allow the host app to handle the event.</span></span> 
1. <span data-ttu-id="a4537-183">L’événement **doit** transmettre toutes les propriétés associées avec l’action</span><span class="sxs-lookup"><span data-stu-id="a4537-183">The event **MUST** pass along all associated properties with the action</span></span>
1. <span data-ttu-id="a4537-184">L’événement **doit** passer le `AdaptiveCard` qui a été exécuté</span><span class="sxs-lookup"><span data-stu-id="a4537-184">The event **MUST** pass along the `AdaptiveCard` which was executed</span></span>

<span data-ttu-id="a4537-185">Action</span><span class="sxs-lookup"><span data-stu-id="a4537-185">Action</span></span> | <span data-ttu-id="a4537-186">Comportement</span><span class="sxs-lookup"><span data-stu-id="a4537-186">Behavior</span></span>
--- | ---
<span data-ttu-id="a4537-187">**Action.OpenUrl**</span><span class="sxs-lookup"><span data-stu-id="a4537-187">**Action.OpenUrl**</span></span> | <span data-ttu-id="a4537-188">Ouvrir une URL externe pour l’affichage</span><span class="sxs-lookup"><span data-stu-id="a4537-188">Open an external URL for viewing</span></span>
<span data-ttu-id="a4537-189">**Action.ShowCard**</span><span class="sxs-lookup"><span data-stu-id="a4537-189">**Action.ShowCard**</span></span> | <span data-ttu-id="a4537-190">Demande une sous-carte à afficher à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a4537-190">Requests a sub-card to be shown to the user.</span></span>
<span data-ttu-id="a4537-191">**Action.Submit**</span><span class="sxs-lookup"><span data-stu-id="a4537-191">**Action.Submit**</span></span> | <span data-ttu-id="a4537-192">Demandez à ce que tous les éléments d’entrée soient regroupés dans un objet qui est ensuite envoyé via une méthode définie par l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="a4537-192">Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

### <a name="actionopenurl"></a><span data-ttu-id="a4537-193">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="a4537-193">Action.OpenUrl</span></span>
1. <span data-ttu-id="a4537-194">`Action.OpenUrl`**Doit** ouvrir une URL à l’aide du mécanisme de plateforme natif</span><span class="sxs-lookup"><span data-stu-id="a4537-194">`Action.OpenUrl` **SHOULD** open a URL using the native platform mechanism</span></span>
1. <span data-ttu-id="a4537-195">Si ce n’est pas possible, il **doit** déclencher un événement à l’application hôte pour gérer l’ouverture de l’URL.</span><span class="sxs-lookup"><span data-stu-id="a4537-195">If this is not possible it **MUST** raise an event to the host app to handle opening the URL.</span></span> <span data-ttu-id="a4537-196">Cet événement **doit** permettre à l’application hôte de remplacer le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="a4537-196">This event **MUST** allow the host app to override the default behavior.</span></span> <span data-ttu-id="a4537-197">Par exemple, laissez-les ouvrir l’URL dans leur propre application.</span><span class="sxs-lookup"><span data-stu-id="a4537-197">E.g., let them open the URL within their own app.</span></span>

### <a name="actionshowcard"></a><span data-ttu-id="a4537-198">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="a4537-198">Action.ShowCard</span></span>

1. <span data-ttu-id="a4537-199">`Action.ShowCard`**Doit** être pris en charge d’une certaine manière, en fonction du paramètre hostConfig.</span><span class="sxs-lookup"><span data-stu-id="a4537-199">`Action.ShowCard` **MUST** be supported in some way, based on the hostConfig setting.</span></span> <span data-ttu-id="a4537-200">Il existe deux modes: inline et Popup.</span><span class="sxs-lookup"><span data-stu-id="a4537-200">There are two modes: inline, and popup.</span></span> <span data-ttu-id="a4537-201">Les cartes en ligne **doivent** basculer automatiquement la visibilité de la carte.</span><span class="sxs-lookup"><span data-stu-id="a4537-201">Inline cards **SHOULD** toggle the card visibility automatically.</span></span> <span data-ttu-id="a4537-202">En mode contextuel, un événement **doit** être déclenché sur l’application hôte pour afficher la carte d’une certaine façon.</span><span class="sxs-lookup"><span data-stu-id="a4537-202">In popup mode, an event **SHOULD** be fired to the host app to show the card in some way.</span></span>

### <a name="actionsubmit"></a><span data-ttu-id="a4537-203">Action. Submit</span><span class="sxs-lookup"><span data-stu-id="a4537-203">Action.Submit</span></span>

<span data-ttu-id="a4537-204">L’action Submit se comporte comme un envoi de formulaire HTML, sauf que lorsque le code HTML déclenche généralement une requête HTTP, les cartes adaptatives la laissent à chaque application hôte pour déterminer ce que signifie «envoi».</span><span class="sxs-lookup"><span data-stu-id="a4537-204">The Submit Action behaves like an HTML form submit, except that where HTML typically triggers an HTTP post, Adaptive Cards leaves it up to each host app to determine what "submit" means to them.</span></span> 

1. <span data-ttu-id="a4537-205">Lorsque ce **doit** déclencher un événement, l’utilisateur appuie sur l’action appelée.</span><span class="sxs-lookup"><span data-stu-id="a4537-205">When this **MUST** raise an event the user taps the action invoked.</span></span>  
1. <span data-ttu-id="a4537-206">La `data` propriété **doit** être incluse dans la charge utile de rappel.</span><span class="sxs-lookup"><span data-stu-id="a4537-206">The `data` property **MUST** be included in the callback payload.</span></span>
1. <span data-ttu-id="a4537-207">Pour `Action.Submit`, un convertisseur **doit** rassembler toutes les entrées sur la carte et récupérer leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="a4537-207">For `Action.Submit`, a renderer **MUST** gather all inputs on the card and retrieve their values.</span></span> 

### <a name="selectaction"></a><span data-ttu-id="a4537-208">selectAction</span><span class="sxs-lookup"><span data-stu-id="a4537-208">selectAction</span></span>

1. <span data-ttu-id="a4537-209">Si la configuration `supportedInteractivity` de `false` l’hôte `selectAction` est, un **ne doit pas être** rendu en tant que cible tactile.</span><span class="sxs-lookup"><span data-stu-id="a4537-209">If Host Config `supportedInteractivity` is `false` then a `selectAction` **MUST NOT** render as a touch target.</span></span>
1. <span data-ttu-id="a4537-210">`Image`, `ColumnSet`et `Column` offrent une`selectAction` propriété, qui **doit** être exécutée lorsque l’utilisateur l’appelle, par exemple, en appuyant sur l’élément.</span><span class="sxs-lookup"><span data-stu-id="a4537-210">`Image`, `ColumnSet`, and `Column` offer a `selectAction` property, which **SHOULD** be executed when the user invokes it, e.g., by tapping the element.</span></span>

## <a name="inputs"></a><span data-ttu-id="a4537-211">Entrées</span><span class="sxs-lookup"><span data-stu-id="a4537-211">Inputs</span></span>

1. <span data-ttu-id="a4537-212">Si HostConfig `supportsInteractivity` est `false` un convertisseur **ne doit pas** afficher d’entrées.</span><span class="sxs-lookup"><span data-stu-id="a4537-212">If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.</span></span>
2. <span data-ttu-id="a4537-213">Les entrées **doivent être** rendues avec la fidélité la plus élevée possible.</span><span class="sxs-lookup"><span data-stu-id="a4537-213">Inputs **SHOULD** render with the highest fidelity possible.</span></span> <span data-ttu-id="a4537-214">Par exemple, un `Input.Date` peut idéalement offrir un sélecteur de dates à un utilisateur, mais si cela n’est pas possible sur la pile de l’interface utilisateur, le convertisseur **doit** revenir au rendu d’une zone de texte standard.</span><span class="sxs-lookup"><span data-stu-id="a4537-214">For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then the renderer **MUST** fall back to rendering a standard text box.</span></span>
3. <span data-ttu-id="a4537-215">Un convertisseur **doit** afficher le `placeholderText` si possible</span><span class="sxs-lookup"><span data-stu-id="a4537-215">A renderer **SHOULD** display the `placeholderText` if possible</span></span>
4. <span data-ttu-id="a4537-216">Un convertisseur **n’a pas** à implémenter la validation de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="a4537-216">A renderer **DOES NOT** have to implement validation of the input.</span></span> <span data-ttu-id="a4537-217">Les utilisateurs de cartes adaptatives doivent prévoir de valider toutes les données reçues à leur extrémité.</span><span class="sxs-lookup"><span data-stu-id="a4537-217">Users of Adaptive Cards must plan to validate any received data on their end.</span></span>
5. <span data-ttu-id="a4537-218">La liaison de la valeur d’entrée **doit** être correctement placée dans une séquence d’échappement</span><span class="sxs-lookup"><span data-stu-id="a4537-218">Input value binding **MUST** be properly escaped</span></span>

6. <span data-ttu-id="a4537-219">L’objet **doit** être retourné à l’application hôte comme suit:</span><span class="sxs-lookup"><span data-stu-id="a4537-219">The object **MUST** be returned to the host app as follows:</span></span>

   <span data-ttu-id="a4537-220">Nous n’offrons aucune promesse de validation d’entrée dans les cartes adaptatives, c’est pourquoi il s’agit de la partie réceptrice pour analyser correctement la réponse.</span><span class="sxs-lookup"><span data-stu-id="a4537-220">We do not make any promises of input validation in adaptive cards, so it's up to the receiving party to properly parse the response.</span></span> <span data-ttu-id="a4537-221">Par exemple, une entrée. Number pourrait renvoyer «Hello» et doit être préparé pour cela.</span><span class="sxs-lookup"><span data-stu-id="a4537-221">E.g., a Input.Number could return "hello" and they need to be prepared for that.</span></span>


## <a name="events"></a><span data-ttu-id="a4537-222">Events</span><span class="sxs-lookup"><span data-stu-id="a4537-222">Events</span></span>

1. <span data-ttu-id="a4537-223">Un convertisseur **doit** déclencher un événement lorsque la visibilité d’un élément a changé, ce qui permet à l’application hôte de faire défiler la carte vers la position.</span><span class="sxs-lookup"><span data-stu-id="a4537-223">A renderer **SHOULD** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.</span></span>

---
title: Fonctionnalités de texte
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: f7ea40b80df4d976c0a8a86b15254018fdf2fac6
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732671"
---
# <a name="text-features"></a><span data-ttu-id="b7043-102">Fonctionnalités de texte</span><span class="sxs-lookup"><span data-stu-id="b7043-102">Text features</span></span>

<span data-ttu-id="b7043-103">`TextBlock`offre des fonctionnalités avancées de mise en forme et de localisation du texte.</span><span class="sxs-lookup"><span data-stu-id="b7043-103">`TextBlock` offers some advanced features for formatting and localizing the text.</span></span>

## <a name="markdown"></a><span data-ttu-id="b7043-104">Markdown</span><span class="sxs-lookup"><span data-stu-id="b7043-104">Markdown</span></span>
<span data-ttu-id="b7043-105">Pour prendre en charge le balisage en ligne, les cartes adaptatives prennent en charge un **sous-ensemble** de la syntaxe de démarque.</span><span class="sxs-lookup"><span data-stu-id="b7043-105">To support inline markup, Adaptive Cards support a **subset** of Markdown syntax.</span></span>

<span data-ttu-id="b7043-106">_Prise en charge_</span><span class="sxs-lookup"><span data-stu-id="b7043-106">_Supported_</span></span>

| <span data-ttu-id="b7043-107">Style de texte</span><span class="sxs-lookup"><span data-stu-id="b7043-107">Text Style</span></span>      | <span data-ttu-id="b7043-108">Markdown</span><span class="sxs-lookup"><span data-stu-id="b7043-108">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="b7043-109">**Gras**</span><span class="sxs-lookup"><span data-stu-id="b7043-109">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="b7043-110">_Italique_</span><span class="sxs-lookup"><span data-stu-id="b7043-110">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="b7043-111">Liste à puces</span><span class="sxs-lookup"><span data-stu-id="b7043-111">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="b7043-112">Liste numérotée</span><span class="sxs-lookup"><span data-stu-id="b7043-112">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="b7043-113">Liens hypertexte</span><span class="sxs-lookup"><span data-stu-id="b7043-113">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="b7043-114">_Non pris en charge_</span><span class="sxs-lookup"><span data-stu-id="b7043-114">_Not supported_</span></span>

* <span data-ttu-id="b7043-115">En-têtes</span><span class="sxs-lookup"><span data-stu-id="b7043-115">Headers</span></span>
* <span data-ttu-id="b7043-116">Tables</span><span class="sxs-lookup"><span data-stu-id="b7043-116">Tables</span></span>
* <span data-ttu-id="b7043-117">Images</span><span class="sxs-lookup"><span data-stu-id="b7043-117">Images</span></span>
* <span data-ttu-id="b7043-118">Tout ce qui n’est pas dans le tableau ci-dessus</span><span class="sxs-lookup"><span data-stu-id="b7043-118">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="b7043-119">Exemple de démarque</span><span class="sxs-lookup"><span data-stu-id="b7043-119">Markdown Example</span></span>

<span data-ttu-id="b7043-120">La charge utile ci-dessous affiche un résultat semblable à ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="b7043-120">The below payload would render something like this:</span></span>

![capture d’écran démarque](media/text-features/markdown.png)

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="b7043-122">Mise en forme et localisation de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="b7043-122">Date/Time formatting and localization</span></span>

<span data-ttu-id="b7043-123">Parfois, vous ne connaissez pas le fuseau horaire de l’utilisateur recevant la carte, de `DATE()` sorte `TIME()` que les cartes adaptatives offrent des fonctions de mise en forme qui permettent de localiser automatiquement l’heure sur l’appareil cible.</span><span class="sxs-lookup"><span data-stu-id="b7043-123">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="b7043-124">Exemple de date/heure</span><span class="sxs-lookup"><span data-stu-id="b7043-124">Date/Time Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Your package will arrive on {{DATE(2017-02-14T06:00:00Z, SHORT)}} at {{TIME(2017-02-14T06:00:00Z)}}",
            "wrap": true
        }
    ]
}
```

<span data-ttu-id="b7043-125">La carte ci-dessus s’affiche:</span><span class="sxs-lookup"><span data-stu-id="b7043-125">The above card will display:</span></span> 

> <span data-ttu-id="b7043-126">**Votre package arrive le mardi 14 février 2017 à 6:00 AM**</span><span class="sxs-lookup"><span data-stu-id="b7043-126">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="b7043-127">Règles de fonction de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="b7043-127">Date/Time function rules</span></span>

<span data-ttu-id="b7043-128">Certaines règles permettent d’interpréter correctement les fonctions de date/heure sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="b7043-128">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="b7043-129">Si les règles ne sont pas respectées, la chaîne brute sera affichée à l’utilisateur, et personne ne l’attend.</span><span class="sxs-lookup"><span data-stu-id="b7043-129">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="b7043-130">respecter la **casse** (doit être tout en majuscules)</span><span class="sxs-lookup"><span data-stu-id="b7043-130">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="b7043-131">**Aucun espace** entre les `{{`parenthèses, `}}`ou</span><span class="sxs-lookup"><span data-stu-id="b7043-131">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="b7043-132">**Mise en forme [RFC 3389](https://tools.ietf.org/html/rfc3339) stricte** (Voir les exemples ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="b7043-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="b7043-133">**Doit être** une date et une heure valides</span><span class="sxs-lookup"><span data-stu-id="b7043-133">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="b7043-134">Formats valides</span><span class="sxs-lookup"><span data-stu-id="b7043-134">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="b7043-135">Paramètre de format de date</span><span class="sxs-lookup"><span data-stu-id="b7043-135">Date formatting param</span></span>

<span data-ttu-id="b7043-136">Pour les dates, un paramètre facultatif peut être spécifié pour mettre en forme la sortie.</span><span class="sxs-lookup"><span data-stu-id="b7043-136">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="b7043-137">Format</span><span class="sxs-lookup"><span data-stu-id="b7043-137">Format</span></span>        |            <span data-ttu-id="b7043-138">Exemples</span><span class="sxs-lookup"><span data-stu-id="b7043-138">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="b7043-139">`COMPACT`Valeurs</span><span class="sxs-lookup"><span data-stu-id="b7043-139">`COMPACT` (Default)</span></span> |          <span data-ttu-id="b7043-140">"2/13/2017"</span><span class="sxs-lookup"><span data-stu-id="b7043-140">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="b7043-141">«Mois du 13 février, 2017»</span><span class="sxs-lookup"><span data-stu-id="b7043-141">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="b7043-142">«Lundi 13 février 2017»</span><span class="sxs-lookup"><span data-stu-id="b7043-142">"Monday, February 13th, 2017"</span></span> |


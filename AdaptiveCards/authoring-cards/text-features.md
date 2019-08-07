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
# <a name="text-features"></a>Fonctionnalités de texte

`TextBlock`offre des fonctionnalités avancées de mise en forme et de localisation du texte.

## <a name="markdown"></a>Markdown
Pour prendre en charge le balisage en ligne, les cartes adaptatives prennent en charge un **sous-ensemble** de la syntaxe de démarque.

_Prise en charge_

| Style de texte      | Markdown |
|-----------------|-----|
| **Gras**        | ```**Bold**``` |
| _Italique_        | ```_Italic_``` |
| Liste à puces     | ```- Item 1\r- Item 2\r- Item 3``` | 
| Liste numérotée   | ```1. Green\r2. Orange\r3. Blue``` |
| Liens hypertexte      | ```[Title](url)``` |

_Non pris en charge_

* En-têtes
* Tables
* Images
* Tout ce qui n’est pas dans le tableau ci-dessus

### <a name="markdown-example"></a>Exemple de démarque

La charge utile ci-dessous affiche un résultat semblable à ce qui suit:

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

## <a name="datetime-formatting-and-localization"></a>Mise en forme et localisation de date et d’heure

Parfois, vous ne connaissez pas le fuseau horaire de l’utilisateur recevant la carte, de `DATE()` sorte `TIME()` que les cartes adaptatives offrent des fonctions de mise en forme qui permettent de localiser automatiquement l’heure sur l’appareil cible.

### <a name="datetime-example"></a>Exemple de date/heure

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

La carte ci-dessus s’affiche: 

> **Votre package arrive le mardi 14 février 2017 à 6:00 AM**

### <a name="datetime-function-rules"></a>Règles de fonction de date et d’heure

Certaines règles permettent d’interpréter correctement les fonctions de date/heure sur chaque plateforme. Si les règles ne sont pas respectées, la chaîne brute sera affichée à l’utilisateur, et personne ne l’attend.

1. respecter la **casse** (doit être tout en majuscules)
1. **Aucun espace** entre les `{{`parenthèses, `}}`ou
1. **Mise en forme [RFC 3389](https://tools.ietf.org/html/rfc3339) stricte** (Voir les exemples ci-dessous)
1. **Doit être** une date et une heure valides

### <a name="valid-formats"></a>Formats valides

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a>Paramètre de format de date

Pour les dates, un paramètre facultatif peut être spécifié pour mettre en forme la sortie.


|       Format        |            Exemples            |
|---------------------|-------------------------------|
| `COMPACT`Valeurs |          "2/13/2017"          |
|       `SHORT`       |     «Mois du 13 février, 2017»     |
|       `LONG`        | «Lundi 13 février 2017» |


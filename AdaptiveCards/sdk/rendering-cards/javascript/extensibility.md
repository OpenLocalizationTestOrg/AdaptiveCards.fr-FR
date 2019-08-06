---
title: Extensibilité-SDK JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 4c43637d81bcf43251638133c66d1c77b92ace56
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732911"
---
# <a name="extensibility---javascript"></a><span data-ttu-id="d3461-102">Extensibilité-JavaScript</span><span class="sxs-lookup"><span data-stu-id="d3461-102">Extensibility - JavaScript</span></span>

## <a name="implement-and-register-a-custom-element"></a><span data-ttu-id="d3461-103">Implémenter et inscrire un élément personnalisé</span><span class="sxs-lookup"><span data-stu-id="d3461-103">Implement and register a custom element</span></span>

<span data-ttu-id="d3461-104">Les étapes de création d’un type d’élément de carte adaptative personnalisé sont les suivantes:</span><span class="sxs-lookup"><span data-stu-id="d3461-104">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="d3461-105">Créer une classe à partir de`CardElement`</span><span class="sxs-lookup"><span data-stu-id="d3461-105">Create a new class driving from `CardElement`</span></span>
- <span data-ttu-id="d3461-106">Implémenter `getJsonTypeName`ses `parse`méthodes `toJSON`,, et`internalRender` `renderSpeech`</span><span class="sxs-lookup"><span data-stu-id="d3461-106">Implement its `getJsonTypeName`, `parse`, `toJSON`, `internalRender` and `renderSpeech` methods</span></span>
- <span data-ttu-id="d3461-107">Inscrivez-le en l’ajoutant au registre des éléments du convertisseur</span><span class="sxs-lookup"><span data-stu-id="d3461-107">Register it by adding it to the renderer's element registry</span></span>

<span data-ttu-id="d3461-108">Prenons un exemple et implémentons un élément de barre de progression simple:</span><span class="sxs-lookup"><span data-stu-id="d3461-108">Let's take an example and implement a simple Progress Bar element:</span></span>

```typescript
import * as Adaptive from "adaptivecards";

export class ProgressBar extends Adaptive.CardElement {
    private _title: string;
    private _value: number = 0;
    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new Adaptive.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return "ProgressBar";
    }

    toJSON(): any {
        let result = super.toJSON();

        Adaptive.setProperty(result, "title", this.title);
        Adaptive.setProperty(result, "value", this.value);

        return result;
    }

    parse(json: any, errors?: Array<Adaptive.IValidationError>) {
        super.parse(json, errors);

        this.title = Adaptive.getStringValueOrDefault(json["title"], undefined);
        this.value = Adaptive.getValueOrDefault(json["value"], this._value);
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (Adaptive.isNullOrEmpty(this.title)) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }

    renderSpeech(): string {
        return (Adaptive.isNullOrEmpty(this.title) ? "Progress" : this.title) + " " + Math.ceil(this.value) + "%";
    }

    get title(): string {
        return this._title;
    }

    set title(value: string) {
        if (this._title !== value) {
            this._title = value;

            this.updateLayout();
        }
    }

    get value(): number {
        return this._value;
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this._value !== adjustedValue) {
            this._value = adjustedValue;

            this.updateLayout();
        }
    }
}
```

<span data-ttu-id="d3461-109">C'est tout !</span><span class="sxs-lookup"><span data-stu-id="d3461-109">That's it.</span></span> <span data-ttu-id="d3461-110">À présent, il vous suffit d’inscrire la classe de barre de progression auprès du convertisseur:</span><span class="sxs-lookup"><span data-stu-id="d3461-110">Now just register the Progress Bar class with the renderer:</span></span>

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## <a name="implement-and-register-a-custom-action"></a><span data-ttu-id="d3461-111">Implémenter et inscrire une action personnalisée</span><span class="sxs-lookup"><span data-stu-id="d3461-111">Implement and register a custom action</span></span>

<span data-ttu-id="d3461-112">Les étapes de création d’une action de carte adaptative personnalisée sont essentiellement les mêmes que celles des éléments personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d3461-112">The steps for creating a custom Adaptive Card action are essentially the same as those for custom elements.</span></span> <span data-ttu-id="d3461-113">Voici un exemple simple d’action d’alerte qui affiche simplement une boîte de message avec du texte configurable:</span><span class="sxs-lookup"><span data-stu-id="d3461-113">Here is a simple example of an Alert Action that simply displays a message box with configurable text:</span></span>

```typescript
import * as Adaptive from "adaptivecards";

export class AlertAction extends Adaptive.Action {
    text: string;

    getJsonTypeName(): string {
        return "Action.ALert";
    }

    execute() {
        alert(this.text);
    }

    parse(json: any) {
        super.parse(json);

        this.text = Adaptive.getStringValueOrDefault(json["text"], "Alert!");
    }

    toJSON() {
        let result = super.toJSON();

        Adaptive.setProperty(result, "text", this.text);

        return result;
    }
}
```

<span data-ttu-id="d3461-114">Inscrivez maintenant la nouvelle action:</span><span class="sxs-lookup"><span data-stu-id="d3461-114">Now register the new action:</span></span>

```
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## <a name="example"></a><span data-ttu-id="d3461-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3461-115">Example</span></span>

<span data-ttu-id="d3461-116">Voici un exemple de carte qui utilise à la fois l’élément ProgressBar et l’action AlertAction:</span><span class="sxs-lookup"><span data-stu-id="d3461-116">Here is a sample card that uses both the ProgressBar element and AlertAction action:</span></span>
```
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "size": "Medium",
            "weight": "Bolder",
            "text": "Custom ProgressBar element"
        },
        {
            "type": "ProgressBar",
            "title": "Please wait...",
            "value": 10
        }
    ],
    "actions": [
        {
            "type": "Action.Alert",
            "title": "Click me",
            "text": "Hello world!"
        }
    ]
}
```

<span data-ttu-id="d3461-117">Et voici comment il est rendu: ![image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span><span class="sxs-lookup"><span data-stu-id="d3461-117">And here is how it renders: ![image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span></span>
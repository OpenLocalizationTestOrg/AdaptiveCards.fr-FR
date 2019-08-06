---
title: Outils cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: f0c5a61d3406e1defffefc575ee0a6ec78fba93d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733026"
---
# <a name="tools-and-samples"></a>Outils et exemples

## <a name="card-designer"></a>Concepteur de cartes 

Vous avez besoin d’un outil pour concevoir vos cartes? Ne cherchez pas plus loin que le concepteur de cartes adaptatives basé sur le navigateur à l’adresse[https://adaptivecards.io/designer](https://adaptivecards.io/designer)

[![capture d’écran du concepteur](media/tools/designer.jpg)](https://adaptivecards.io/designer)

### <a name="embed-the-designer-into-your-app"></a>Incorporer le concepteur dans votre application

Mais pourquoi y envoyer vos utilisateurs quand vous pouvez **incorporer le concepteur de cartes directement dans votre application Web** à l’aide de notre bibliothèque JavaScript. 

Consultez le package [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) pour commencer.

## <a name="schema-validation"></a>Validation de schéma

La validation de schéma est un moyen puissant de faciliter la création d’outils et de les activer.

Nous avons fourni un [fichier de schéma JSON](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) complet pour la modification et la validation des cartes adaptatives dans JSON. Notez que la version de l’URL de schéma est une version plus récente de cartes adaptatives ayant une URL correspondante.

Dans Visual Studio et Visual Studio code vous pouvez obtenir une fonctionnalité IntelliSense automatique en `$schema` incluant une référence.

![bad](media/tools/invalidjson1.png)

![saisie semi-automatique](media/tools/autocomplete.png)

## <a name="example"></a>Exemple

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a>Extension de Visual Studio Code

Nous avons créé une extension Visual Studio code qui vous permet de visualiser la carte que vous modifiez en temps réel dans l’éditeur lui-même. 

![extension](media/tools/vscode-extension.png)

Pour installer, ouvrez le Marketplace des extensions et recherchez la visionneuse de **cartes adaptatives**.

![marketplace](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a>Usage

Lorsque vous modifiez un fichier. JSON avec une propriété de carte `$schema` adaptative, vous pouvez l’afficher à l’aide `Ctrl+Shift+V A`de.
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a>Options

Le paramètre de Visual Studio Code suivant est disponible pour la visionneuse AdaptiveCards. Cela peut être défini dans les paramètres utilisateur ou les paramètres de l’espace de travail.

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a>Exemple de visualiseur WPF

L' [exemple de projet de visualiseur WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) vous permet de visualiser des cartes à l’aide de WPF/XAML sur un ordinateur Windows.  Un `hostconfig` éditeur est intégré pour la modification et l’affichage des paramètres de configuration de l’ordinateur hôte. Enregistrez ces paramètres en tant que JSON pour les utiliser dans le rendu de votre application.

![visualiseur WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a>Exemple de ImageRender WPF

L' [exemple de projet ImageRender](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) transforme toute carte en un format png à partir de la ligne de commande à l’aide de WPF. 

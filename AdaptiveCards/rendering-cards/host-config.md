---
title: HostConfig pour cartes adaptatives
author: paulcam206
ms.author: paulcam
ms.date: 09/18/2018
ms.topic: reference
ms.openlocfilehash: 848ce3dd2ccca1f975dfd330c1c88292c753641d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733096"
---
# <a name="what-is-hostconfig"></a>Qu’est-ce que HostConfig?
`HostConfig`est un **objet de configuration multiplateforme** qui spécifie la façon dont un convertisseur de carte adaptative génère l’interface utilisateur.

Cela permet aux propriétés qui ne sont pas indépendantes de la plateforme d’être partagées entre les convertisseurs sur différents périphériques et plateformes. Il permet également de créer des outils qui vous donnent une idée de l’apparence de la carte pour un environnement donné.

Consultez un exemple de [HostConfig. JSON](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) pour obtenir un sentiment de son contenu.

---

   * [`AdaptiveCardConfig`](#schema-adaptivecardconfig)-Options de niveau supérieur pour`AdaptiveCards`
   * [`ActionsConfig`](#schema-actionsconfig)-Options pour `Action`s
   * [`ContainerStylesConfig`](#schema-containerstylesconfig)-Contrôle le style des conteneurs par défaut et d’accentuation
   * [`FactSetConfig`](#schema-factsetconfig)-Contrôle l’affichage des `FactSet`s
   * [`FontSizesConfig`](#schema-fontsizesconfig)-Contrôle la taille de police des métriques pour différents styles de texte
   * [`FontWeightsConfig`](#schema-fontweightsconfig)-Contrôle la mesure de la pondération de police
   * [`ForegroundColorsConfig`](#schema-foregroundcolorsconfig)-Contrôle diverses couleurs de police
   * [`ImageSetConfig`](#schema-imagesetconfig)-Contrôle l' `ImageSet`affichage des s
   * [`ImageSizesConfig`](#schema-imagesizesconfig)-Contrôle `Image` les tailles
   * [`MediaConfig`](#schema-mediaconfig)-Contrôle l’affichage et le comportement `Media` des éléments
   * [`SeparatorConfig`](#schema-separatorconfig)-Contrôle l’affichage des séparateurs
   * [`ShowCardConfig`](#schema-showcardconfig)-Contrôle le comportement et le style de`Action.ShowCard`
   * [`SpacingsConfig`](#schema-spacingsconfig)-Contrôle la disposition des éléments
   * [`TextBlockConfig`](#schema-textblockconfig)-Paramètres contrôlant l’affichage du texte

# <a name="card-configuration"></a>Configuration de la carte

<a name="schema-adaptivecardconfig"></a>
## <a name="adaptivecardconfig"></a>AdaptiveCardConfig

Options de niveau supérieur pour`AdaptiveCards`

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**allowCustomStyle**|`boolean`| Non, valeur par défaut:`true`|Contrôle si le style personnalisé est autorisé|1.0
|**supportsInteractivity**|`boolean`| Non, valeur par défaut:`true`|Contrôler si les `Action`s interactifs sont autorisés à être appelés|1.0
|**imageBaseUrl**|`string`| Non |URL de base à utiliser lors du chargement des ressources|1.0
|**fontFamily**|`string`| Non, valeur par défaut:`"Calibri"`|Type de police à utiliser lors du rendu du texte|1.0
|**actions**|`object`| Non |Options pour `Action`s|1.0
|**adaptiveCard**|`object`| Non |Options de niveau supérieur pour`AdaptiveCards`|1.0
|**containerStyles**|`object`| Non |Contrôle le style des conteneurs par défaut et d’accentuation|1.0
|**imageSizes**|`object`| Non |Contrôle `Image` les tailles|1.0
|**imageSet**|`object`| Non |Contrôle l' `ImageSet`affichage des s|1.0
|**factSet**|`object`| Non |Contrôle l’affichage de `FactSet`s|1.0
|**fontSizes**|`object`| Non |Contrôle la taille de police des métriques pour différents styles de texte|1.0
|**fontWeights**|`object`| Non |Contrôle les métriques de l’épaisseur de police|1.0
|**spacing**|`object`| Non |Contrôle la disposition des éléments|1.0
|**separator**|`object`| Non |Contrôle l’affichage des séparateurs|1.0
|**Media**|`object`| Non |Contrôle l’affichage et le comportement `Media` des éléments|1.1


<a name="schema-actionsconfig"></a>
## <a name="actionsconfig"></a>ActionsConfig

Options pour `Action`s

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**actionsOrientation**|`string`| Non, valeur par défaut:`"horizontal"`|Contrôle la disposition des boutons|1.0
|**actionAlignment**|`string`| Non, valeur par défaut:`"stretch"`|Contrôler la disposition des boutons|1.0
|**buttonSpacing**|`integer`| Non, valeur par défaut:`10`|Contrôle la quantité d’espacement à utiliser entre les boutons|1.0
|**maxActions**|`integer`| Non, valeur par défaut:`5`|Contrôle le nombre d’actions autorisées au total|1.0
|**spacing**|`string`| Non, valeur par défaut:`"default"`|Contrôle l’espacement global de l’élément action|1.0
|**showCard**|`object`| Non |Contrôle le comportement et le style de`Action.ShowCard`|1.0
|**iconPlacement**|`string`| Non, valeur par défaut:`"aboveTitle"`|Contrôle où placer l’icône d’action|1.0
|**iconSize**|`integer`| Non, valeur par défaut:`30`|Icône de contrôle de la taille de l’action|1.0


<a name="schema-containerstylesconfig"></a>
## <a name="containerstylesconfig"></a>ContainerStylesConfig

Contrôle le style des conteneurs par défaut et d’accentuation

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**default**|`object`| Non |Style de conteneur par défaut|1.0
|**emphasis**|`object`| Non |Style de conteneur à utiliser pour l’accentuation|1.0


<a name="schema-factsetconfig"></a>
## <a name="factsetconfig"></a>FactSetConfig

Contrôle l’affichage de `FactSet`s

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**title**|`object`| Non, valeur par défaut:`{"weight":"bolder","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":150}`|Paramètres contrôlant l’affichage du texte|1.0
|**value**|`object`| Non, valeur par défaut:`{"weight":"default","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":0}`|Paramètres contrôlant l’affichage du texte|1.0
|**spacing**|`integer`| Non, valeur par défaut:`10`|&nbsp;|1.0


<a name="schema-fontsizesconfig"></a>
## <a name="fontsizesconfig"></a>FontSizesConfig

Contrôle la taille de police des métriques pour différents styles de texte

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Non, valeur par défaut:`10`|Petite taille de police|1.0
|**default**|`integer`| Non, valeur par défaut:`12`|Taille de police par défaut|1.0
|**medium**|`integer`| Non, valeur par défaut:`14`|Taille de police moyenne|1.0
|**large**|`integer`| Non, valeur par défaut:`17`|Grande taille de police|1.0
|**extraLarge**|`integer`| Non, valeur par défaut:`20`|Très grande taille de police|1.0


<a name="schema-fontweightsconfig"></a>
## <a name="fontweightsconfig"></a>FontWeightsConfig

Contrôle les métriques de l’épaisseur de police

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**lighter**|`integer`| Non, valeur par défaut:`200`|&nbsp;|1.0
|**default**|`integer`| Non, valeur par défaut:`400`|&nbsp;|1.0
|**bolder**|`integer`| Non, valeur par défaut:`800`|&nbsp;|1.0


<a name="schema-foregroundcolorsconfig"></a>
## <a name="foregroundcolorsconfig"></a>ForegroundColorsConfig

Contrôle différentes couleurs de police

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**default**|`object`| Non, valeur par défaut:`{"default":"#FF000000","subtle":"#B2000000"}`|&nbsp;|1.0
|**accent**|`object`| Non, valeur par défaut:`{"default":"#FF0000FF","subtle":"#B20000FF"}`|&nbsp;|1.0
|**dark**|`object`| Non, valeur par défaut:`{"default":"#FF101010","subtle":"#B2101010"}`|&nbsp;|1.0
|**light**|`object`| Non, valeur par défaut:`{"default":"#FFFFFFFF","subtle":"#B2FFFFFF"}`|&nbsp;|1.0
|**good**|`object`| Non, valeur par défaut:`{"default":"#FF008000","subtle":"#B2008000"}`|&nbsp;|1.0
|**warning**|`object`| Non, valeur par défaut:`{"default":"#FFFFD700","subtle":"#B2FFD700"}`|&nbsp;|1.0
|**attention**|`object`| Non, valeur par défaut:`{"default":"#FF8B0000","subtle":"#B28B0000"}`|&nbsp;|1.0


<a name="schema-imagesetconfig"></a>
## <a name="imagesetconfig"></a>ImageSetConfig

Contrôle l' `ImageSet`affichage des s

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**imageSize**|`string`| Non, valeur par défaut:`"auto"`|Contrôle le dimensionnement d’une image individuelle|1.0
|**maxImageHeight**|`integer`| Non, valeur par défaut:`100`|Contraindre la hauteur de l’image à cette valeur|1.0


<a name="schema-imagesizesconfig"></a>
## <a name="imagesizesconfig"></a>ImageSizesConfig

Contrôle `Image` les tailles

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Non, valeur par défaut:`80`|Petite valeur de taille d’image|1.0
|**medium**|`integer`| Non, valeur par défaut:`120`|Valeur de la taille de l’image moyenne|1.0
|**large**|`integer`| Non, valeur par défaut:`180`|Valeur de la taille de l’image volumineuse|1.0


<a name="schema-mediaconfig"></a>
## <a name="mediaconfig"></a>MediaConfig

Contrôle l’affichage et le comportement `Media` des éléments

#### <a name="introduced-in-version-11"></a>Introduction dans la version 1,1

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**defaultPoster**|`string`| Non |URI de l’image à afficher lorsque le bouton de lecture n’a pas été appelé|1.1
|**playButton**|`string`| Non |Image à afficher en tant que bouton de lecture|1.1
|**allowInlinePlayback**|`boolean`| Non, valeur par défaut:`true`|Indique s’il faut afficher le média en ligne ou appeler en externe|1.1


<a name="schema-separatorconfig"></a>
## <a name="separatorconfig"></a>SeparatorConfig

Contrôle l’affichage des séparateurs

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**lineThickness**|`integer`| Non, valeur par défaut:`1`|Épaisseur de la ligne de séparation|1.0
|**lineColor**|`string,null`| Non, valeur par défaut:`#B2000000`|Couleur à utiliser lors du dessin de la ligne de séparation|1.0


<a name="schema-showcardconfig"></a>
## <a name="showcardconfig"></a>ShowCardConfig

Contrôle le comportement et le style de`Action.ShowCard`

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**actionMode**|`string`| Non, valeur par défaut:`"inline"`|Contrôle l’affichage de la carte|1.0
|**style**|`object`| Non, valeur par défaut:`emphasis`|Contrôle le style d’un conteneur|1.0
|**inlineTopMargin**|`integer`| Non, valeur par défaut:`16`|Quantité de marge à utiliser lors de l’affichage de la carte|1.0


<a name="schema-spacingsconfig"></a>
## <a name="spacingsconfig"></a>SpacingsConfig

Contrôle la disposition des éléments

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Non, valeur par défaut:`3`|Petite valeur d’espacement|1.0
|**default**|`integer`| Non, valeur par défaut:`8`|Valeur d’espacement par défaut|1.0
|**medium**|`integer`| Non, valeur par défaut:`20`|Valeur de l’espacement moyen|1.0
|**large**|`integer`| Non, valeur par défaut:`30`|Valeur d’espacement élevé|1.0
|**extraLarge**|`integer`| Non, valeur par défaut:`40`|Valeur d’espacement très grand|1.0
|**padding**|`integer`| Non, valeur par défaut:`20`|Valeur de remplissage|1.0


<a name="schema-textblockconfig"></a>
## <a name="textblockconfig"></a>TextBlockConfig

Paramètres contrôlant l’affichage du texte

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**size**|`string`| Non, valeur par défaut:`"default"`|Taille de police à utiliser lorsqu’une carte ne spécifie pas|1.0
|**weight**|`string`| Non, valeur par défaut:`"normal"`|Épaisseur de la police à utiliser lorsqu’une carte ne spécifie pas|1.0
|**color**|`string`| Non, valeur par défaut:`"default"`|Couleur de police à utiliser lorsqu’une carte ne spécifie pas|1.0
|**isSubtle**|`boolean`| Non, valeur par défaut:`false`|Le texte doit-il être discret si une carte ne spécifie pas|1.0
|**wrap**|`boolean`| Non, valeur par défaut:`true`|Le texte doit être renvoyé à la ligne si une carte ne le spécifie pas|1.0
|**maxWidth**|`integer`| Non, valeur par défaut:`0`|Largeur maximale à utiliser si une carte ne spécifie pas|1.0

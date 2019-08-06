---
title: Extensibilité-Kit de développement logiciel (SDK) iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 13245ced3f4f657e13793bfdf1d212e44d2b6a41
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732946"
---
# <a name="extensibility---ios"></a><span data-ttu-id="31a15-102">Extensibilité-iOS</span><span class="sxs-lookup"><span data-stu-id="31a15-102">Extensibility - iOS</span></span>

## <a name="changing-per-element-rendering"></a><span data-ttu-id="31a15-103">Modification par élément rendu</span><span class="sxs-lookup"><span data-stu-id="31a15-103">Changing per element rendering</span></span>

<span data-ttu-id="31a15-104">Les développeurs peuvent personnaliser l’apparence des éléments renderred AdaptiveCards tels que TextBlock.</span><span class="sxs-lookup"><span data-stu-id="31a15-104">Developers can customize the look of renderred AdaptiveCards elements such as TextBlock.</span></span>
<span data-ttu-id="31a15-105">L’exemple suivant montre comment modifier la couleur d’arrière-plan de NumberInput.</span><span class="sxs-lookup"><span data-stu-id="31a15-105">Following example shows how one can change background color of NumberInput.</span></span>

```objective-c
ACRRegistration *registration = [ACRRegistration getInstance];
// register custom renderer with registration
// custom renderer must implement ACRIBaseCardElementRenderer protocol
// for more information, please refer to CustomInputNumberRenderer.mm
 [registration setBaseCardElementRenderer:[CustomInputNumberRenderer getInstance] cardElementType:ACRNumberInput];
 ...
/// CustiomInputNumberRenderer.mm
- (UIView *)render:(UIView<ACRIContentHoldingView> *)viewGroup
              rootViewController:(UIViewController *)vc
              inputs:(NSArray *)inputs
     baseCardElement:(ACOBaseCardElement *)acoElem
          hostConfig:(ACOHostConfig *)acoConfig
  {
      ACRInputNumberRenderer *defaultRenderer = [ACRInputNumberRenderer getInstance];
 
      UIView *input = [defaultRenderer render:viewGroup
                           rootViewController:vc
                                       inputs:inputs
                              baseCardElement:acoElem
                                   hostConfig:acoConfig];
      if(input)
      {   
          // customize background color of input
          [input setBackgroundColor: [UIColor colorWithRed:1.0
                                                     green:59.0/255.0
                                                      blue:48.0/255.0
                                                     alpha:1.0]];
      }
      return input;
  }
  ```

 ## <a name="additional-property"></a><span data-ttu-id="31a15-106">Propriété supplémentaire</span><span class="sxs-lookup"><span data-stu-id="31a15-106">Additional Property</span></span>

 <span data-ttu-id="31a15-107">Les développeurs peuvent également envoyer des propriétés supplémentaires dans le cadre de la charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="31a15-107">Developers can also send in additional properties as part of json payload.</span></span>
<span data-ttu-id="31a15-108">Par exemple, en plus de «l’espacement» et de l’ID de charge utile JSON pour BaseCardElement, vous pouvez ajouter RADIUS pour les angles de TextBlock à sa charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="31a15-108">For example, in addition to "spacing" and "id" of json payload for BaseCardElement, one can add radius for corners of TextBlock to its json payload.</span></span>

 ```objective-c
 "type":"TextBlock",
 ...
 "radius":20,
 ...
 ```

 ```objective-c
         NSData *additionalProperty = [acoElem additionalProperty];
          if(additionalProperty) {
              NSDictionary *dictionary = [NSJSONSerialization JSONObjectWithData:additionalProperty options:NSJSONReadingMutableLeaves error:nil];
              radiusForMyTextBlock = dictionary[@"radius"];
          ...
```
 ## <a name="custom-parsing"></a><span data-ttu-id="31a15-109">Analyse personnalisée</span><span class="sxs-lookup"><span data-stu-id="31a15-109">Custom Parsing</span></span>

<span data-ttu-id="31a15-110">Les développeurs peuvent également avoir une analyse personnalisée et ajouter un nouvel élément d’interface utilisateur à la carte Adpative, comme la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="31a15-110">Developers can also have custom parsing and have new UI element added to adpative card such as progress bar.</span></span> <span data-ttu-id="31a15-111">Pour plus d’informations, consultez CustomProgressBarRenderer.mm.</span><span class="sxs-lookup"><span data-stu-id="31a15-111">Please check CustomProgressBarRenderer.mm for detail.</span></span>
<span data-ttu-id="31a15-112">L’analyseur personnalisé doit implémenter le protocole ACOIBaseCardElementParser.</span><span class="sxs-lookup"><span data-stu-id="31a15-112">Custom parser must implement ACOIBaseCardElementParser protocol.</span></span> <span data-ttu-id="31a15-113">la méthode deserializeToCustomElement doit analyser la charge utile JSON donnée en tant que NSData et retourner un pointeur vers l’objet UIView qui sera ajouté à AdaptiveCard objet rendu.</span><span class="sxs-lookup"><span data-stu-id="31a15-113">deserializeToCustomElement method should parses given json payload given as NSData and return a pointer to UIView object that will be added to AdaptiveCard rendered object.</span></span>

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c
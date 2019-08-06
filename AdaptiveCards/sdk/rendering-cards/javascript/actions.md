---
title: Actions-SDK JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: bd88a0d5a98dd892887da897ad2a3ae214222e2b
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732916"
---
# <a name="actions---javascript"></a><span data-ttu-id="6872b-102">Actions - JavaScript</span><span class="sxs-lookup"><span data-stu-id="6872b-102">Actions - JavaScript</span></span>

```js
// Set the adaptive card's event handlers. onExecuteAction is invoked
// whenever an action is clicked in the card
adaptiveCard.onExecuteAction = function(action) { alert("Ow!"); }
```
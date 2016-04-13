---
# required metadata

title: How to create selectors
description:
keywords:
author: 
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: bc085933-c33a-470b-b018-509afdc3e576

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

Don't think we need the H1, so I've removed it here, strictly for testing purposes.

Here is a one-way selector:

> [AZURE.SELECTOR]
-[Selector option 1](lp-selector1.md)
-[Selector option 2](lp-selector2.md)

That was using the Azure way.

Here's the "Minky" way:
<ul class="document-ui">
  <li>
    <div class="dropdown-container">
      <label for="dropdown">Pick an option</label>
      <div class="dropdown">
        <select>
          <option value="option-a">Option A</option>
          <option value="option-b">Option B</option>
        </select>
      </div>
</li>
</ul>

But the Minky way doesn't say how to change the contents based on those choices.
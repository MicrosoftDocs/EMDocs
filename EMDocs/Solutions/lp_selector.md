---
title: How to create selectors
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article

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
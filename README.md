# Lemonade Change Solution

This is a Python solution for the [860. Lemonade Change](https://leetcode.com/problems/lemonade-change/) problem on LeetCode.

---

## Problem Statement

At a lemonade stand, each lemonade costs $5. Customers queue to buy one at a time, paying with $5, $10, or $20 bills. The goal is to provide the correct change to each customer while ensuring that the net transaction is $5 for each lemonade.

---

## Solution

The solution is written in Python, as shown below:

```html
<div style="background: #f9f9f9; padding: 15px; border-radius: 8px; border: 1px solid #e1e1e1; overflow-x: auto;">
<pre>
<code class="language-python">
class Solution:
    def lemonadeChange(self, bills):
        """
        Determines if change can be provided to each customer in line.

        Args:
            bills (List[int]): A list of bills where each bill is either 5, 10, or 20.

        Returns:
            bool: True if change can be provided to every customer, False otherwise.
        """
        five, ten = 0, 0  # Counters for $5 and $10 bills

        for bill in bills:
            if bill == 5:
                five += 1
            elif bill == 10:
                if five > 0:
                    five -= 1
                    ten += 1
                else:
                    return False
            elif bill == 20:
                if ten > 0 and five > 0:
                    ten -= 1
                    five -= 1
                elif five >= 3:
                    five -= 3
                else:
                    return False
        return True
</code>
</pre>
</div>

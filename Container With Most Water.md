### **Problem Description: Container With Most Water**

#### **Problem Statement:**

You are given an integer array `height` of length `n`. The array represents \( n \) vertical lines, such that the \( i^{th} \) line has two endpoints at \((i, 0)\) and \((i, \text{height}[i])\).

Find two lines such that, together with the x-axis, they form a container that can store the maximum amount of water.

Return the **maximum amount of water** a container can store.  
**Note:** You cannot tilt the container (the lines must remain vertical).

---

#### **Example 1:**
**Input:**
```python
height = [1, 8, 6, 2, 5, 4, 8, 3, 7]
```

**Output:**
```
49
```

**Explanation:**
The lines at indices 1 and 8 form the container with the maximum area:
- Width = \( 8 - 1 = 7 \)
- Height = \( \min(\text{height}[1], \text{height}[8]) = \min(8, 7) = 7 \)
- Area = \( 7 \times 7 = 49 \)

---

#### **Example 2:**
**Input:**
```python
height = [1, 1]
```

**Output:**
```
1
```

**Explanation:**
The only container possible is between the two lines:
- Width = \( 1 - 0 = 1 \)
- Height = \( \min(\text{height}[0], \text{height}[1]) = 1 \)
- Area = \( 1 \times 1 = 1 \)

---

#### **Constraints:**
- \( n \geq 2 \): There are at least two lines.
- \( 0 \leq \text{height}[i] \leq 10^4 \): Height values are non-negative integers.

---

#### **Approach:**

##### **Two Pointers Technique (Efficient Approach)**:
1. Start with two pointers:
   - \( i \): At the beginning of the array.
   - \( j \): At the end of the array.
2. Calculate the area for the current pair of lines:  
   \[
   \text{area} = (j - i) \times \min(\text{height}[i], \text{height}[j])
   \]
3. Update the maximum area if the current area is greater.
4. Move the pointer pointing to the shorter line:
   - If \( \text{height}[i] < \text{height}[j] \), increment \( i \).
   - Otherwise, decrement \( j \).
5. Repeat until \( i \) and \( j \) meet.

**Complexity:**
- Time Complexity: \( O(n) \), as we traverse the array once.
- Space Complexity: \( O(1) \), no extra space used.

---

#### **Python Solution:**
```python
def maxArea(height):
    # Initialize two pointers
    i, j = 0, len(height) - 1

    # Variable to store the maximum area
    max_area = 0

    # Iterate until the pointers meet
    while i < j:
        # Calculate the current area
        current_area = (j - i) * min(height[i], height[j])
        
        # Update the maximum area if the current area is larger
        max_area = max(max_area, current_area)
        
        # Move the pointer pointing to the shorter line
        if height[i] < height[j]:
            i += 1
        else:
            j -= 1

    return max_area
```

---

#### **How It Works:**
1. The two pointers optimize the process by systematically narrowing down possible containers based on height and width.
2. It avoids unnecessary calculations for pairs that can't produce a larger area than the maximum already found.

---

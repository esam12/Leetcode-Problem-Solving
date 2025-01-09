## **Reverse Integer Problem**

### **Problem Description**  
Given a signed 32-bit integer `x`, return `x` with its digits reversed.  
If reversing `x` causes the value to go outside the signed 32-bit integer range `[-2³¹, 2³¹ - 1]`, then return `0`.  

**Constraints:**  
- The environment does not allow you to store 64-bit integers.  

---

### **Example Input and Output**
| Input         | Output |
|---------------|--------|
| `123`         | `321`  |
| `-123`        | `-321` |
| `120`         | `21`   |
| `1534236469`  | `0`    | (Exceeds 32-bit range)  

---

### **Solution**

Here's a Python implementation that solves the problem, considering the constraints:

```python
def reverse(x: int) -> int:
    # Define the 32-bit integer range
    INT_MIN, INT_MAX = -2**31, 2**31 - 1

    # Handle sign and work with the absolute value
    sign = -1 if x < 0 else 1
    x = abs(x)

    # Reverse digits
    reversed_num = 0
    while x != 0:
        digit = x % 10
        x //= 10

        # Check for overflow/underflow before updating reversed_num
        if reversed_num > (INT_MAX - digit) // 10:
            return 0

        reversed_num = reversed_num * 10 + digit

    return sign * reversed_num
```

---

### **Explanation of the Solution**

1. **Handling the Sign:**  
   - Extract the sign of the integer (`-1` for negatives, `1` for positives) using a simple conditional statement.  
   - Work with the absolute value of `x` for easier manipulation.

2. **Reversing Digits:**  
   - Use a loop to extract each digit from the number using modulus (`%`) and then append it to the reversed number by multiplying the existing reversed number by 10 and adding the new digit.

3. **Overflow Protection:**  
   - Before updating the reversed number, check whether it exceeds the 32-bit range using the condition:  
     ```python
     if reversed_num > (INT_MAX - digit) // 10:
         return 0
     ```

4. **Final Result:**  
   - Multiply the reversed number by the sign to restore its original sign.

---

### **Usage Examples**
Run the function with different inputs to test its behavior:

```python
print(reverse(123))         # Output: 321
print(reverse(-123))        # Output: -321
print(reverse(120))         # Output: 21
print(reverse(1534236469))  # Output: 0
```

---

### **Note**
This implementation ensures:
- Proper handling of signed integers.
- Adherence to 32-bit signed integer constraints.
- Efficient and safe digit reversal without using 64-bit storage.

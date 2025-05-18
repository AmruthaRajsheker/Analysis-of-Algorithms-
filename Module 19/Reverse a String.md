## **EXPERIMENT NO: 1A**

### **AIM:**

To implement a recursive function in a programming language to reverse a given input string.



### **ALGORITHM:**

1. **Start**
2. Define a recursive function `reverseString(str)`:

   * **Base Case:** If the string is empty or has only one character, return the string.
   * **Recursive Case:** Call `reverseString(str[1:])` and append `str[0]` at the end.
3. Accept a string input from the user.
4. Call the recursive function with the input string.
5. Display the reversed string.
6. **Stop**



### **PROGRAM:**

```python

def reverse_string(s):
    if len(s) <= 1:
        return s
    else:
        return reverse_string(s[1:]) + s[0]

# Input from user
input_string = input("Enter a string: ")
reversed_string = reverse_string(input_string)
print("Reversed string:", reversed_string)
```



### **OUTPUT:**


![image](https://github.com/user-attachments/assets/ec162576-7204-462f-9191-655751ff9489)





### **RESULT:**

The program successfully reverses the input string using recursion. The output accurately reflects the reversed sequence of characters in the input string, demonstrating correct recursive logic and functional implementation.



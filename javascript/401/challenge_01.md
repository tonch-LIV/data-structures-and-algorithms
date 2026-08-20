# Challenge Title

***reverseArray***  
Write a function called `reverseArray` that takes an array as an argument and returns a new array with the elements in reversed order without using a built-in reversing method.

## Whiteboard Process

![Whiteboard Process](/401/img/401_challenge01.png)

## Approach & Efficiency

### **Approach Explanation**

The approach creates a *new* empty array called `result` and begins at the last index of the original array.  
The function moves backward through the original array one index at a time; each value is copied into the next available index of the `result` array.  
This continues until index `0` has been copied. The completed `result` array is then returned with the elements in reversed order.  
This approach avoids using a built-in method such as `.reverse()` and demonstrates the process of reversing an array using indexes.  

### **The Big-O**

**Time Complexity:** `O(n)`  
The function visits each element in the original array once, so the amount of work increases linearly as the size of the array increases.  

**Space Complexity:** `O(n)`  
A new array is created to store all of the elements from the original array, so the amount of additional memory used grows with the size of the input array.  

## Solution

The function takes an array as an argument and returns a new array containing the same elements in reversed order.

```js
function reverseArray(array) {
  const result = [];

  let i = array.length - 1;

  while (i >= 0) {
    result[result.length] = array[i];
    i = i - 1;
  }

  return result;
}
```

<!-- CHECKLIST: Whiteboard Process -->

- [ ] Top-level README “Table of Contents” is updated
- [ ] README for this challenge is complete
  - [ ] Summary, Description, Approach & Efficiency, Solution
  - [ ] Picture of whiteboard
  - [ ] [Link to code](#solution)
- [ ] Feature tasks for this challenge are completed
- [ ] Unit tests written and passing
  - [ ] “Happy Path” - Expected outcome
  - [ ] Expected failure
  - [ ] Edge Case (if applicable/obvious)

<!----------------------------------------------------------------------------->

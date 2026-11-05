# ***tree-max***

Extend the `BinaryTree` class with a `findMaximumValue()` method that returns the largest numeric value stored in the tree.

The method accepts no arguments. A populated tree returns its maximum value; an empty tree returns `null`. Values are assumed to be numeric.

## Whiteboard Process

![Whiteboard Process ](img/401_challenge16.png)  

### [figma](https://www.figma.com/board/MO4FelnL1k8J3wF3HD40b2/challenge_16_maxValue?node-id=6844-199&t=jZhGY6kDHGcgB2bQ-1)

## Approach & Efficiency

### **Approach Explanation**

The solution uses recursive, depth-first preorder traversal: current node -> entire left subtree -> then entire right subtree.

The root's value becomes the initial `maximum`. A helper visits each node and updates `maximum` whenever it encounters a larger value. Starting with an actual tree value also handles trees containing only negative numbers.

After every node has been visited, the method returns `maximum`; `findMaximumValue()`.

### **The Big-O**

**Time Complexity: O(n)**  
(n is the number of nodes)  
Every node is visited once.  
Each visit performs a fixed amount of work:  

- a missing-node check,  
- a comparison, and possibly an assignment.  

Finding the maximum early does not remove the need to inspect the remaining nodes.

**Space Complexity: O(n), worst case**  
`maximum` stores just one number, which takes O(1) space.  
However, each recursive call also needs a stack frame so execution can resume after its child calls finish.  
Recursive calls accumulate along a tree that forms a chain.

## Solution

Add `findMaximumValue()` inside the `BinaryTree` class from [Challenge 15](challenge_15.md#solution), after its constructor and before `preOrder()`.

```js
findMaximumValue() {
  if (this.root === null) { // checks whether root is missing and..
    return null;
  }

  let maximum = this.root.value; // remembers root as (current) largest value

  const visit = (node) => { // process of traversing
    if (node === null) {
      return;
    }

    if (node.value > maximum) {
      maximum = node.value; // replaces/updates maximum
    }

    visit(node.left);  // traverses children
    visit(node.right);
  };

  visit(this.root); // starts traversal

  return maximum;
}
```

### Test / examples

These examples use `Node` and `BinaryTree` from Challenge 15, with `findMaximumValue()` added. Comments show the expected outputs.

```js
// Happy path: the assignment's example tree
const tree = new BinaryTree();

tree.root = new Node(2);
tree.root.left = new Node(7);
tree.root.right = new Node(5);

tree.root.left.left = new Node(2);
tree.root.left.right = new Node(6);
tree.root.left.right.left = new Node(5);
tree.root.left.right.right = new Node(11);

tree.root.right.right = new Node(9);
tree.root.right.right.left = new Node(4);

console.log(tree.findMaximumValue()); // 11

////

// Empty tree
const emptyTree = new BinaryTree();

console.log(emptyTree.findMaximumValue()); // null

// Single node
const singleTree = new BinaryTree();
singleTree.root = new Node(2);

console.log(singleTree.findMaximumValue()); // 2

// All negative values
const negativeTree = new BinaryTree();
negativeTree.root = new Node(-10);
negativeTree.root.left = new Node(-30);
negativeTree.root.right = new Node(-5);

console.log(negativeTree.findMaximumValue()); // -5
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

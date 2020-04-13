---
title: Tree and Tree Traversal
date: 2020-04-11 11:21:53
tags:
---

> We extend the concept of linked data structures to structure containing nodes with more than one self-referenced field. ... ... A traversal is a process that visits all the nodes in the tree. Since a tree is a nonlinear data structure, there is no unique traversal. [^2]

<!-- more -->

## Types of Trees

### Binary Tree

A *binary tree* is a tree data structure in which each node has at most two children.[^1]

### Binary Search Tree

A *binary search tree* is a binary tree where each node is greater than all node in its left subtree and smaller than all node in its right subtree. [^1]

{% mermaid graph TD %}
1((8)) --> 2((4))
1 --> 3((10))
2 --> 4((2))
2 --> 5((6))
3 --> 6((9))
3 --> 7((20))
{% endmermaid %}




### Complete Binary Tree

A *complete binary tree* is a binary tree in which every level, except possibly the last, is completely filled, and all nodes are as far left as possible.[^1]

{% mermaid graph TD %}
1(( )) --> 2(( ))
1(( )) --> 3(( ))
2(( )) --> 4(( ))
2(( )) --> 5(( ))
3(( )) --> 6(( ))
3(( )) --> 7(( ))
4(( )) --> 8(( ))
4(( )) --> 9(( ))
5(( )) --> 10(( ))
5(( )) --> 11(( ))
6(( )) --L--> 12(( ))
{% endmermaid %}

> Diagram: A complete binary tree with height h = 3



### Full Binary Tree

A *full binary tree* is a binary tree in which every node has either zero or two children. That is, no nodes have only one child.[^1]

{% mermaid graph TD %}
1(( )) --> 2(( ))
1(( )) --> 3(( ))
3(( )) --> 6(( ))
3(( )) --> 7(( ))
6(( )) --> 12(( ))
6(( )) --> 13(( ))
{% endmermaid %}

> Diagram: A full binary tree of height h = 3



### Perfect Binary Tree

A *perfect binary tree* is a binary tree where all leaves are on the same level , and every parent has two children. A perfect binary tree of height $h$ has $2^{h+1} - 1$ nodes and $2^h$ leaf nodes. [^1]

NOTE: height for root is 0. 

{% mermaid graph TD %}
1(( )) --> 2(( ))
1(( )) --> 3(( ))
2(( )) --> 4(( ))
2(( )) --> 5(( ))
3(( )) --> 6(( ))
3(( )) --> 7(( ))
4(( )) --> 8(( ))
4(( )) --> 9(( ))
5(( )) --> 10(( ))
5(( )) --> 11(( ))
6(( )) --> 12(( ))
6(( )) --> 13(( ))
7(( )) --> 14(( ))
7(( )) --> 15(( ))
{% endmermaid %}

> Diagram: A perfect binary tree of height h = 3



### Others

Following are also types of tree but not included in this section:

- Balanced Trees
	- Red-Black Trees
	- AVL Trees
- Binary Heaps
- Tires(Prefix Trees)







## Binary Tree Traversal

Unlike linear data structures which have only one logical way two traverse them, trees can be traversed in three different ways, pre-order traversal, in-order traversal, post-order traversal. The main difference among these three ways of traversal is the timing of processing current node.

| Tree Traversal | Timing of processing current node                            |
| -------------- | ------------------------------------------------------------ |
| Pre-order      | Process current node before processing its left & right subtree |
| In-order       | Process current node after processing its left subtree but before its right subtree |
| Post-order     | Process current node after processing its left & right subtree |

{% mermaid graph TD %}
1((1)) --> 2((2))
1 --> 3((3))
2 --> 4((4))
2 --> 5((5))
3 --> 6((6))
3 --> 7((7))
4 --> 8((8))
4 --> 9((9))
5 --> 10((10))
5 --> 11((11))
{% endmermaid %}


### Pre-order Traversal: Mid -> Left -> Right

Traversal result: `[1,2,4,8,9,5,10,11,3,6,7]`

### In-order Traversal: Left -> Mid -> Right

Traversal result: `[8,4,9,2,10,5,11,1,6,3,7]`

### Post-order Traversal: Left -> Right -> Mid

Traversal result: `[8,9,4,10,11,5,2,6,7,3,1]`



## Application

### Pre-order Traversal

| Tree Type | Application                                                  |
| --------- | ------------------------------------------------------------ |
| Any       | Normal traverse. Process current node before processing its subtrees. |

```java
void preOrderTraversal(Treenode node) {
    if(node == null) return;
    visit(node);
    preOrderTraversal(node.left);
    preOrderTraversal(node.right);
}
```

<a name="pre-order-excercise"></a>

#### Exercises

| #                                                            | Title                                                        | Level      | Solution                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ---------- | ---------------------------------------------- |
| [144](https://leetcode.com/problems/binary-tree-preorder-traversal/description/) | Binary Tree Pre-order Traversal (recursive + iterative solution) | Medium     | <a href="#144">Solution</a>                    |
| [100](https://leetcode.com/problems/same-tree/description/)  | Same Tree                                                    | Easy       | <a href="#100">Solution</a>                    |
| **[101](https://leetcode.com/problems/symmetric-tree/description/)** | **Symmetric Tree**                                           | **Easy**   | <a href="#101">Solution</a>                    |
| **[226](https://leetcode.com/problems/invert-binary-tree/description/)** | **Invert Binary Tree**                                       | **Easy**   | <a href="#226">Solution</a>                    |
| **[257](https://leetcode.com/problems/binary-tree-paths/)**  | **Binary Tree Paths**                                        | **Easy**   | <a href="#257">Solution</a>                    |
| **[112](https://leetcode.com/problems/path-sum/)**           | **Path Sum**                                                 | **Easy**   | <a href="#112">Solution</a>                    |
| **[113](https://leetcode.com/problems/path-sum-ii/)**        | **Path Sum II**                                              | **Medium** | <a href="#113">Solution</a>                    |
| **[298](https://www.lintcode.com/problem/binary-tree-longest-consecutive-sequence/description)** | **Binary Tree Longest Consecutive Sequence**                 | **Easy**   | <a href="#298">Solution</a>                    |
| **[111](https://leetcode.com/problems/minimum-depth-of-binary-tree/)** | **Minimum Depth of Binary Tree**                             | **Easy**   | <a href="#111">Solution</a>                    |
| **[104](https://leetcode.com/problems/maximum-depth-of-binary-tree)** | **Maximum Depth of Binary Tree**                             | **Easy**   | <a href="#104">Solution</a>                    |
| **[270](https://www.lintcode.com/problem/closest-binary-search-tree-value/description)** | **Closest Binary Search Tree Value**                         | **Easy**   | <a href="#270">Solution</a>                    |
| **[235](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)** | **Lowest Common Ancestor of a Binary Search Tree**           | **Easy**   | <a href="#235">Solution</a>                    |
| **[108](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)** | **Convert Sorted Array to Binary Search Tree**               | **Easy**   | <a href="#108">Solution</a>                    |
| [129](https://leetcode.com/problems/sum-root-to-leaf-numbers/) | Sum Root to Leaf Numbers                                     | Medium     | <a href="#129">Solution</a>                    |
| [366](https://www.lintcode.com/problem/find-leaves-of-binary-tree/description) | Find Leaves of Binary Tree                                   | Medium     | <a href="#366">Solution</a>                    |
| **[337](https://leetcode.com/problems/house-robber-iii/)**   | **House Robber II**                                          | **Medium** | <a href="#337">Solution</a> （没有复杂度分析） |
| [199]()                                                      | Binary Tree Right Side View                                  | Medium     | <a href="#199">Solution</a>                    |
| **[98](https://leetcode.com/problems/validate-binary-search-tree/)** | **Validate Binary Search Tree**                              | **Medium** | <a href="#98">Solution</a>                     |
| [109](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/) | Convert Sorted List to Binary Search Tree                    | Medium     | <a href="#109">Solution</a>                    |
| [114](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/) | Flatten Binary Tree to Linked List                           | Medium     | <a href="#114">Solution</a>                    |
| [222](https://leetcode.com/problems/count-complete-tree-nodes/) | Count Complete Tree Nodes                                    | Medium     | <a href="#222">Solution</a>                    |
| [105](https://leetcode.com/problems/count-complete-tree-nodes/) | Construct Binary Tree from Preorder and Inorder Traversal    | Medium     | <a href="#105">Solution</a>                    |
| **[116](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)** | **Populating Next Right Pointers in Each Node**              | **Medium** | <a href="#116">Solution</a>                    |
| **[117](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/)** | **Populating Next Right Pointers in Each Node II**           | **Medium** | <a href="#117">Solution</a>                    |



### In-order Traversal

| Tree Type          | Application                                                  |
| ------------------ | ------------------------------------------------------------ |
| Any                | Normal traverse. Process current node after processing its left subtree and before its right subtree. |
| Binary Search Tree | When traversing a *binary search tree*, in-order traversal gives us a non-decreasing traversing result. To get nodes of BST in non-increasing order, reverse the order of processing left and right subtree in in-order traverse. |

```java
void inOrderTraversal(Treenode node) {
    if(node == null) return;
    inOrderTraversal(node.left);
    visit(node);
    inOrderTraversal(node.right);
}
```

<a name="in-order-excercise"></a>

#### Exercises

| #                                                            | Title                                                        | Level      | Solution                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ---------- | --------------------------- |
| [94](https://leetcode.com/problems/binary-tree-inorder-traversal/) | Binary Tree In-order Traversal (recursive + iterative solution) | Medium     | <a href="#94">Solution</a>  |
| **[230](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)** | **Kth Smallest Element in a BST**                            | **Medium** | <a href="#230">Solution</a> |
| **[285](https://www.lintcode.com/problem/inorder-successor-in-bst/description)** | **In-order successor in BST**                                | **Medium** | <a href="#285">Solution</a> |
| **[173](https://leetcode.com/problems/binary-search-tree-iterator/)** | **Binary Search Tree Iterator**                              | **Medium** | <a href="#173">Solution</a> |
| [156](https://www.lintcode.com/problem/binary-tree-upside-down/description) | Binary Tree Upside Down                                      | Medium     | <a href="#156">Solution</a> |
| [99](https://leetcode.com/problems/recover-binary-search-tree/) | ==Inorder Recover Binary Search Tree==                       | Hard       | <a href="#99">Solution</a>  |
| [272](https://www.lintcode.com/problem/closest-binary-search-tree-value-ii/description) | ==Closest Binary Search Tree Value II==                      | Hard       | <a href="#272">Solution</a> |



### Post-order Traversal

| Tree Type | Application                                                  |
| --------- | ------------------------------------------------------------ |
| Any       | Normal traverse. Process current node after processing its subtrees. |

```java
void postOrderTraversal(Treenode node) {
    if(node == null) return;
    postOrderTraversal(node.left);
    postOrderTraversal(node.right);
    visit(node);
}
```

<a name="post-order-excercise"></a>

#### Exercises

| #                                                            | Title                                                        | Level      | Solution                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ---------- | --------------------------- |
| [145](https://leetcode.com/problems/binary-tree-postorder-traversal/) | Binary Tree Post-order Traversal (recursive + iterative solution) | Hard       | <a href="#145">Solution</a> |
| 106                                                          | Construct Binary Tree from Inorder and Postorder Traversal   | Medium     | <a href="#106">Solution</a> |
| **[110](https://leetcode.com/problems/balanced-binary-tree)** | **Balanced Binary Tree**                                     | **Easy**   | <a href="#110">Solution</a> |
| [250](https://www.lintcode.com/problem/count-univalue-subtrees/description) | Count Univalue Subtrees                                      | Medium     | <a href="#250">Solution</a> |
| **[236](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)** | **Lowest Common Ancestor of a Binary Tree**                  | **Medium** | <a href="#236">Solution</a> |
| **[124](https://leetcode.com/problems/binary-tree-maximum-path-sum)** | **Binary Tree Maximum Path Sum**                             | **Hard**   | <a href="#124">Solution</a> |
| [333](https://www.cnblogs.com/grandyang/p/5188938.html)      | ==Largest BST Subtree==                                      | Medium     | <a href="#333">Solution</a> |



### Level-order Traversal

| Tree Type | Application                                                  |
| --------- | ------------------------------------------------------------ |
| Any       | Normal traverse. Use pre-order to traverse but with level identification. Iteration version of level order traverse is BFS. |

```
void levelOrderTraversal(Treenode node, int level) {
    if(node == null) return;
    visit(node);
    levelOrderTraversal(node.left, level + 1);
    levelOrderTraversal(node.right, level + 1);
}
```

<a name="level-order-excercise"></a>

#### Exercises

| #                                                            | Title                                         | Level      | Solution                    |
| ------------------------------------------------------------ | --------------------------------------------- | ---------- | --------------------------- |
| [102](https://leetcode.com/problems/binary-tree-level-order-traversal/) | Binary Tree Level Order Traversal             | Easy       | <a href="#102">Solution</a> |
| [107](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/) | Binary Tree Level Order Traversal II          | Easy       | <a href="#107">Solution</a> |
| [103](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/) | Binary Tree Zigzag Level Order Traversal      | Medium     | <a href="#103">Solution</a> |
| **[314](https://www.lintcode.com/problem/binary-tree-vertical-order-traversal/description)** | ==**Binary Tree Vertical Order Traversal**==  | **Medium** | <a href="#314">Solution</a> |
| **[297](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/description/)** | ==**Serialize and Deserialize Binary Tree**== | **Hard**   | <a href="#297">Solution</a> |



<a name="others"></a>

### Others

| #                                                            | Title                                          | Tag                 | Level      | Solution                    |
| ------------------------------------------------------------ | ---------------------------------------------- | ------------------- | ---------- | --------------------------- |
| **[96](https://leetcode.com/problems/unique-binary-search-trees/)** | **Unique Binary Search Trees**                 | Dynamic Programming | **Medium** | <a href="#96">Solution</a>  |
| [95](https://leetcode.com/problems/unique-binary-search-trees-ii/) | Unique Binary Search Trees II                  |                     | Medium     | <a href="#95">Solution</a>  |
| [331](https://leetcode.com/problems/verify-preorder-serialization-of-a-binary-tree/) | Verify Preorder Serialization of a Binary Tree | Stack, Graph        | Medium     | <a href="#331">Solution</a> |
| [255](https://www.lintcode.com/problem/verify-preorder-sequence-in-binary-search-tree/description) | Verify Preorder Sequence in Binary Search Tree | Monotonic Stack     | Medium     | <a href="#255">Solution</a> |



## Solution

<a name="94"></a>

### 94. Binary Tree In-order Traversal

#### Recursion

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    List<Integer> result = new ArrayList<Integer>();
    public List<Integer> inorderTraversal(TreeNode root) {
        traverse(root);
        return result;
    }
    
    private void traverse(TreeNode root) {
        if(root == null) return;
        traverse(root.left);
        result.add(root.val);
        traverse(root.right);
    }
}
```

#### Iteration

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    List<Integer> result = new ArrayList<Integer>();
    public List<Integer> inorderTraversal(TreeNode root) {
        Stack<TreeNode> stack = new Stack<TreeNode>();
        TreeNode node = root;
        while(node != null || !stack.isEmpty()) {
            if(node == null) {
                node = stack.pop();
                result.add(node.val);
                node = node.right;
            } else {
                stack.push(node);
                node = node.left;
            }
        }
        return result;
    }
}
```





<a name="95"></a>

### 95. Unique Binary Search Trees II

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public List<TreeNode> generateTrees(int n) {
        if(n == 0) return new ArrayList<TreeNode>();
        return helper(n, 0);
    }
    
    private List<TreeNode> helper(int n, int offset) {
        List<TreeNode> results = new ArrayList<TreeNode>();
        if(n == 0) {
            results.add(null);
            return results;
        }
        if(n == 1) {
            results.add(new TreeNode(n + offset));
            return results;
        }
        for(int i = 1; i<=n; ++i) {
            List<TreeNode> leftTrees = helper(i - 1, offset);
            List<TreeNode> rightTrees = helper(n - i, i + offset);
            for(int k = 0; k < leftTrees.size(); ++k) {
                for(int l = 0; l < rightTrees.size(); ++l) {
                    TreeNode root = new TreeNode(i + offset);
                    root.left = leftTrees.get(k);
                    root.right = rightTrees.get(l);
                    results.add(root);
                }
            }
        }
        return results;
    }
}
```

<a href="#others">Back to excercises</a>





<a name="96"></a>

### 96. Unique Binary Search Trees

```java
class Solution {
    public int numTrees(int n) {
        int[] results = new int[n + 1];
        results[0] = 1;
        if(n >= 1) results[1] = 1;
        if(n >= 2) results[2] = 2;
        for(int i = 3; i <= n; ++i) {
            for(int j = 1; j<=i; ++j) {
                int left = j - 1, right = i - j;
                results[i] += results[left] * results[right];
            }
        }
        return results[n];
    }
}
```

##### Complexity

- Runtime Complexity：$O(N)$ 
- 空间复杂度：$O(N)$ 

<a href="#others">Back to excercises</a>



<a name="98"></a>

### 98. Validate Binary Search Tree

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public boolean isValidBST(TreeNode root) {
        return isInRange(root, null, null);
    }
    
    private boolean isInRange(TreeNode root, Integer lo, Integer hi) {
        if(root == null) return true;
        if(lo != null && lo >= root.val) return false;
        if(hi != null && root.val >= hi) return false;
        return isInRange(root.left, lo, root.val) 
            && isInRange(root.right, root.val, hi);
    }
```

##### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ if the tree is balance, worst case is $O(N)$.

<a href="#pre-order-excercise">Back to excercises</a>





<a name="100"></a>

### 100. Same Tree 

#### Recursion

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(p == null && q == null) return true;
        if(p == null || q == null) return false;
        return p.val == q.val && isSameTree(p.left, q.left) && isSameTree(p.right, q.right); 
    }
}
```

##### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ if the tree is balance, worst case is $O(N)$.

<a href="#pre-order-excercise">Back to excercises</a>





<a name="101"></a>

### 101. Symmetric Tree

```java
public boolean isSymmetric(TreeNode root) {
    return isMirror(root, root);
}

public boolean isMirror(TreeNode t1, TreeNode t2) {
    if (t1 == null && t2 == null) return true;
    if (t1 == null || t2 == null) return false;
    return (t1.val == t2.val)
        && isMirror(t1.right, t2.left)
        && isMirror(t1.left, t2.right);
}
```

<a href="#pre-order-excercise">Back to excercises</a>





<a name="102"></a>

### 102. Binary Tree Level Order Traversal

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    List<List<Integer>> results = new ArrayList<List<Integer>>();
    public List<List<Integer>> levelOrder(TreeNode root) {
        traverse(root, 0);
        return results;
    }
    
    private void traverse(TreeNode root, int i) {
        if(root == null) return;
        if(results.size() <= i) {
            results.add(new ArrayList());
        }
        results.get(i).add(root.val);
        traverse(root.left, i + 1);
        traverse(root.right, i + 1);
    }
}
```

#### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$

<a href="#level-order-excercise">Back to excercises</a>





<a name="103"></a>

### 103. Binary Tree Zigzag Level Order Traversal

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    List<List<Integer>> results = new LinkedList<List<Integer>>();
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        traverse(root, 0);
        return results;
    }
    private void traverse(TreeNode root, int level) {
        if(root == null) return;
        if(results.size() <= level) {
            results.add(new LinkedList<Integer>());
        }
        if(level % 2 == 0) {
            results.get(level).add(root.val);
        } else {
            results.get(level).add(0, root.val);
        }
        traverse(root.left, level + 1);
        traverse(root.right, level + 1);
    }
}
```

##### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ if the tree is balance, worst case is $O(N)$.

<a href="#level-order-excercise">Back to excercises</a>





<a name="104"></a>

### 104. Maximum Depth of Binary Tree

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    int result = 0;
    public int maxDepth(TreeNode root) {
        traverse(root, 1);
        return result;
    }
    
    private void traverse(TreeNode root, int level) {
        if(root == null) return;
        if(level > result) result = level;
        traverse(root.left, level + 1);
        traverse(root.right, level + 1);
    }
}
```

##### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ if the tree is balance, worst case is $O(N)$.

<a href="#pre-order-excercise">Back to excercises</a>





<a name="105"></a>

### 105. Construct Binary Tree From Preorder and Inorder Traversal

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        if(preorder.length == 0) return null;
        return helper(preorder, inorder, 0, 0, preorder.length, preorder.length);
    }
    
    private TreeNode helper(int[] preorder, int[] inorder, int i, int j, int endi, int endj) {
        if(i == endi && j == endj) return null;
        TreeNode root = new TreeNode(preorder[i]);
        int k = 0;
        while(root.val != inorder[j+k]) k++;
        if(k == 0) {
            root.left = null;
        } else {
            root.left = helper(preorder, inorder, i + 1, j, i + k + 1 ,j + k);
        }
        root.right = helper(preorder, inorder, i + k + 1, j + k + 1, endi ,endj);
        return root;
    }
}
```

##### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ if the tree is balance, worst case is $O(N)$.

<a href="#pre-order-excercise">Back to excercises</a>





<a name="107"></a>

###  107. Binary Tree Level Order Traversal II

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    List<List<Integer>> results = new LinkedList<List<Integer>>();
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        traverse(root, 0);
        return results;
    }
    private void traverse(TreeNode root, int level) {
        if(root == null) return;
        if(results.size() <= level) {
            results.add(0, new LinkedList<Integer>());
        }
        int index = results.size() - level - 1;
        results.get(index).add(root.val);
        traverse(root.left, level + 1);
        traverse(root.right, level + 1);
    }
}
```

#### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ 

<a href="#level-order-excercise">Back to excercises</a>





<a name="108"></a>

### 108. Convert Sorted Array to Binary Search Tree

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        return helper(nums, 0, nums.length - 1);
    }
    
    private TreeNode helper(int[] nums, int start, int end) {
        if(start > end) return null;
        int mid = start + (end - start) / 2;
        TreeNode root = new TreeNode(nums[mid]);
        root.left = helper(nums, start, mid - 1);
        root.right = helper(nums, mid + 1, end);
        return root;
    }
}
```

##### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ 

<a href="#pre-order-excercise">Back to excercises</a>





<a name="109"></a>

### 109. Convert Sorted List to Binary Search Tree

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */

/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode sortedListToBST(ListNode head) {
        return helper(head, null);
    }
    
    private TreeNode helper(ListNode start, ListNode end) {
        if(start == end) return null;
        ListNode mid = findMid(start, end);
        TreeNode root = new TreeNode(mid.val);
        root.left = helper(start, mid);
        root.right = helper(mid.next, end);
        return root;
    }
    
    private ListNode findMid(ListNode start, ListNode end) {
        ListNode fast = start, slow = start;
        while(fast != end && fast.next != end) {
            fast = fast.next.next;
            slow = slow.next;
        }
        return slow;
    }
}
```

##### Complexity

- Runtime Complexity: $O(N \log N)$. For details of how runtime is calculated, please check out [here](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/solution/).

- Space Complexity: $O(\log N)$ if the tree is balance, worst case is $O(N)$.

<a href="#post-order-excercise">Back to excercises</a>





<a name="110"></a>

### 110. Balanced Binary Tree

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    boolean result = true;
    public boolean isBalanced(TreeNode root) {
        traverseforHeight(root);
        return result;
    }
    
    private int traverseforHeight(TreeNode root) {
        if(root == null) return 0;
        if(root.left == null && root.right == null) return 1;
        int heightL = traverseforHeight(root.left);
        int heightR = traverseforHeight(root.right);
        int diff = Math.abs(heightL - heightR);
        if(diff > 1) result = false;
        return 1 + Math.max(heightL, heightR);
    }
}
```

##### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ if the tree is balance, worst case is $O(N)$.

<a href="#post-order-excercise">Back to excercises</a>





<a name="111"></a>

### 111. Minimum Depth of Binary Tree

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    int result = Integer.MAX_VALUE;
    public int minDepth(TreeNode root) {
        if(root == null) return 0;
        traverse(root, 1);    
        return result;
    }
    
    private void traverse(TreeNode root, int level) {
        if(root == null) return;
        if(root.left == null && root.right == null && level < result) {
            result = level;
        } 
        traverse(root.left, level + 1);
        traverse(root.right, level + 1);
    }
}
```

##### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ if the tree is balance, worst case is $O(N)$.

<a href="#pre-order-excercise">Back to excercises</a>





<a name="112"></a>

### 112. Path Sum

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    boolean result = false;
    public boolean hasPathSum(TreeNode root, int sum) {
        traverse(root, 0, sum);
        return result;
    }
    
    private void traverse(TreeNode root, int sum, int target) {
        if(root == null) return;
        sum += root.val;
        if(sum == target && root.left == null && root.right == null) {
            result = true;
        }
        traverse(root.left, sum, target);
        traverse(root.right, sum, target);
    }
} 
```

#### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$, worst case is unbalance tree $O(N)$.

<a href="#pre-order-excercise">Back to excercises</a>





<a name="113"></a>

### 113. Path Sum II

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    List<List<Integer>> result = new ArrayList<List<Integer>>();
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        if(root == null) return result;
        traverse(root, 0, sum, new ArrayList<Integer>());
        return result;
    }
    
    private void traverse(TreeNode root, int sum, int target, List<Integer> path) {
        if(root == null) return;
        sum += root.val;
        path.add(root.val);
        if(root.left == null && root.right == null && sum == target) {
            result.add(new ArrayList<Integer>(path));
        }
        traverse(root.left, sum, target, path);
        traverse(root.right, sum, target, path);
        path.remove(path.size() - 1);
    }   
}
```

#### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$, worst case is unbalance tree $O(N)$.

<a href="#pre-order-excercise">Back to excercises</a>





<a name="114"></a>

### 114. Flatten Binary Tree to Linked List

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public void flatten(TreeNode root) {
        if(root == null) return;
        if(root.left != null) {
            TreeNode tmp = root.right;
            root.right = root.left;
            root.left = null;
            TreeNode curNode = root.right;
            while(curNode.right != null) {
                curNode = curNode.right;
            }
            curNode.right = tmp;
        }
        flatten(root.right);
    }
}
```

#### Complexity

- Runtime complexity: $O(N)$
- Space Complexity: $O(N)$  

<a href="#pre-order-excercise">Back to excercises</a>





<a name="116"></a>

### 116. Populating Next Right Pointers in Each Node

```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node next;

    public Node() {}
    
    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, Node _left, Node _right, Node _next) {
        val = _val;
        left = _left;
        right = _right;
        next = _next;
    }
};
*/

class Solution {
    public Node connect(Node root) {
        traverse(root);
        return root;
    }
    
    private void traverse(Node root) {
        if(root == null) return;
        Node next = root.next;
        if(root.left != null) {
            root.left.next = root.right;
            if(next != null) {
                root.right.next = next.left;
            }
        }
        traverse(root.left);
        traverse(root.right);
    }
}
```

#### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ 

<a href="#pre-order-excercise">Back to excercises</a>





<a name="117"></a>

### 117. Populating Next Right Pointers in Each Node II

```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node next;

    public Node() {}
    
    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, Node _left, Node _right, Node _next) {
        val = _val;
        left = _left;
        right = _right;
        next = _next;
    }
};
*/

class Solution {
    public Node connect(Node root) {
        traverse(root);
        return root;
    }
    
    private void traverse(Node root) {
        if(root == null) return;
        Node next = null, curNode = root.next;
        while(curNode != null && next == null) {
            if(curNode.left != null) {
                next = curNode.left;
            } else {
                next = curNode.right;
            }
            curNode = curNode.next;
        }
        if(root.right != null) {
            root.right.next = next;
        }
        if(root.left != null) {
            root.left.next = root.right == null ? next : root.right;
        }
        traverse(root.right);
        traverse(root.left);
    }
}
```

#### Complexity:

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ 

<a href="#pre-order-excercise">Back to excercises</a>





<a name="124"></a>

### 124. Binary Tree Maximum Path Sum

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    int maxSum = Integer.MIN_VALUE;
    public int maxPathSum(TreeNode root) {
        if(root == null) return 0;
        traverse(root);
        return maxSum;
    }
    
    private int traverse(TreeNode root) {
        if(root == null) return 0;
        if(root.left ==  null && root.right == null) {
            maxSum = Math.max(root.val, maxSum);
            return root.val;
        }
        int sumL = traverse(root.left);
        int sumR = traverse(root.right);
        int max = Math.max(sumL + sumR + root.val, Math.max(Math.max(sumL, sumR) + root.val, root.val));
        maxSum = Math.max(max, maxSum);
        return Math.max(Math.max(sumL, sumR) + root.val, root.val); 
    }
}
```

#### Complexity

- Runtime Complexity: $O(N)$
- Space Complexity: $O(\log N)$

<a href="#post-order-excercise">Back to excercises</a>





<a name="129"></a>

### 129. Sum Root to Leaf Numbers

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    int total = 0;
    public int sumNumbers(TreeNode root) {
        traverse(root, 0);
        return total;
    }
    
    private void traverse(TreeNode root, int num) {
        if(root == null) return;
        num = num * 10 + root.val;
        if(root.left == null && root.right == null) {
            total += num;
        }
        traverse(root.left, num);
        traverse(root.right, num);
    }
}
```

#### Complexity

- Runtime complexity: $O(N)$
- Space Complexity: $O(\log N)$ 

<a href="#pre-order-excercise">Back to excercises</a>





<a name="144"></a>

### 144. Binary Tree Preorder Traversal

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> result = new LinkedList<Integer>();
        Stack<TreeNode> stack = new Stack<TreeNode>();
        TreeNode node = root;
        while(node != null || !stack.isEmpty()) {
            if(node == null) {
                node = stack.pop();
            } else {
                result.add(node.val);
                if(node.right != null) stack.add(node.right);
                node = node.left;
            }
        }
        return result;
    }
}
```

#### Complexity

- Runtime Complexity: $O(N)$
- Space Complexity: $O(\log N)$ 

<a href="#pre-order-excercise">Back to excercises</a>





<a name="156"></a>

### 156. Binary Tree Upside Down

In the flip operation, left most node becomes the root of flipped tree and its parent become its right child and the right sibling become its left child and same operation needs to be apply to all left most nodes.

```java
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */

public class Solution {
    /**
     * @param root: the root of binary tree
     * @return: new root
     */
    public TreeNode upsideDownBinaryTree(TreeNode root) {
        return traverse(root, null);
    }
    
    private TreeNode traverse(TreeNode root, TreeNode parent) {
        if(root == null) return null;
        TreeNode tmp = root;
        if(root.left != null) {
            root = traverse(root.left, root);
        }
        tmp.left = parent != null ? parent.right : null;
        tmp.right = parent;
        return root;
    }
}
```

#### Complexity

- Runtime complexity: $O(\log N)$ 
- Space Complexity: $O(\log N)$ 

<a href="#in-order-excercise">Back to excercises</a>





<a name="173"></a>

### 173. Binary Search Tree Iterator

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class BSTIterator {
    Stack<TreeNode> stack = new Stack<TreeNode>();

    public BSTIterator(TreeNode root) {
        while(root!= null) {
            stack.push(root);
            root = root.left;
        }
    }
    
    /** @return the next smallest number */
    public int next() {
        TreeNode result = stack.pop();
        TreeNode root = result.right;
        while(root!= null) {
            stack.push(root);
            root = root.left;
        }
        return result.val;
    }
    
    /** @return whether we have a next smallest number */
    public boolean hasNext() {
        return !stack.isEmpty();
    }
}

/**
 * Your BSTIterator object will be instantiated and called as such:
 * BSTIterator obj = new BSTIterator(root);
 * int param_1 = obj.next();
 * boolean param_2 = obj.hasNext();
 */
```

#### Complexity

- Runtime Complexity: $O(1)$ on average for `next` and `hasNext`, worst case is O(N) for `next`. Please click [here](https://leetcode.com/problems/binary-search-tree-iterator/solution/) to check out for solution.
- Space Complexity: $O(\log N)$

<a href="#in-order-excercise">Back to excercises</a>





<a name="199"></a>

### 199. Binary Tree Right Side View

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    List<Integer> result = new LinkedList<Integer>();
    public List<Integer> rightSideView(TreeNode root) {
        traverse(root, 0);
        return result;
    }
    private void traverse(TreeNode root, int level) {
        if(root == null) return;
        if(result.size() <= level) {
            result.add(root.val);
        }
        traverse(root.right, level + 1);
        traverse(root.left, level + 1);
    }
}
```

#### Complexity

- Runtime complexity: $O(N)$
- Space Complexity: $O(\log N)$ 

<a href="#pre-order-excercise">Back to excercises</a>





<a name="222"></a>

### 222. Count Complete Tree Nodes

#### Brute Force

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public int countNodes(TreeNode root) {
        if(root == null) return 0;
        return 1 + countNodes(root.left) + countNodes(root.right);
    }
}
```

##### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$ 

#### Optimized

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public int countNodes(TreeNode root) {
        if(root == null) return 0;
        int heightL = 0, heightR = 0;
        TreeNode curNode = root;
        while(curNode != null) {
            heightL++;
            curNode = curNode.left;
        }
        curNode = root;
        while(curNode != null) {
            heightR++;
            curNode = curNode.right;
        }
        if(heightL == heightR) return (int)Math.pow(2, heightR) - 1;
        return 1 + countNodes(root.left) + countNodes(root.right);
    }
}
```

##### Complexity

- Runtime Complexity: $O(\log N \times \log N)$. For detail of how runtime is calculated, please checkout [here](https://labuladong.gitbook.io/algo/shu-ju-jie-gou-xi-lie/wan-quan-er-cha-shu-jie-dian-shu).
- Space Complexity: $O(\log N)$

<a href="#pre-order-excercise">Back to excercises</a>





<a name="226"></a>

### 226. Invert Binary Tree

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if(root == null) return root;
        TreeNode tmp = root.left;
        root.left = invertTree(root.right);
        root.right = invertTree(tmp);
        return root;
    }
}
```

#### Complexity

- Runtime complexity: $O(N)$
- Space Complexity: $O(\log N)$ 

<a href="#pre-order-excercise">Back to excercises</a>





<a name="235"></a>

### 235. Lowest Common Ancestor of a Binary Search Tree

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root == null) return null;
        if(root.val < p.val && root.val < q.val) {
            return lowestCommonAncestor(root.right, p, q);
        }
        if(root.val > p.val && root.val > q.val) {
            return lowestCommonAncestor(root.left, p, q);
        }
        return root;
    }
}
```

#### Complexity

- Runtime complexity: $O(\log N)$ 
- Space Complexity: $O(\log N)$ 

<a href="#pre-order-excercise">Back to excercises</a>





<a name="230"></a>

###  230. Kth Smallest Element in a BST

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    int result = 0, cnt = 0;
    public int kthSmallest(TreeNode root, int k) {
        traverse(root, k);
        return result;
    }
    private void traverse(TreeNode root, int k) {
        if(root == null) return;
        traverse(root.left, k);
        cnt++;
        if(cnt == k) {
            result = root.val;
        }
        traverse(root.right, k);
    }
}
```

#### Complexity

- Runtime Complexity: $O(N)$ 
- Space Complexity: $O(\log N)$

<a href="#in-order-excercise">Back to excercises</a>







<a name="236"></a>

### 236. Lowest Common Ancestor of a Binary Tree

{% mermaid graph TD %}
3((3)) --> 5((5))
5 --> 6((6))
5 --> 2((2))
2 --> 7((7))
2 --> 4((4))
3 --> 1((1))
1 --> 0((0))
1 --> 8((8))
{% endmermaid %}

Ex 1: Search for 7 and 4, expect to return 2

{% mermaid graph TD %}
    3((3)) --> 5((5))
    5 --> 6((6))
    5 --> 2((2))
    2 --> 7((7))
    2 --> 4((4))
    3 --> 1((1))
    1 --> 0((0))
    1 --> 8((8))
    7 -- 7 --> 2
    4 -- 4 --> 2
    2 -- 2 --> 5
    6 -- null --> 5
    5 -- 2 --> 3
    1 -- null --> 3
    0 -- null --> 1
    8 -- null --> 1
{% endmermaid %}



Ex 2: Search for 2 and 6, expect to return 5

{% mermaid graph TD %}
    3((3)) --> 5((5))
    5 --> 6((6))
    5 --> 2((2))
    2 --> 7((7))
    2 --> 4((4))
    3 --> 1((1))
    1 --> 0((0))
    1 --> 8((8))
    7 -- null --> 2
    4 -- null --> 2
    2 -- 2 --> 5
    6 -- 6 --> 5
    5 -- 5 --> 3
    1 -- null --> 3
    0 -- null --> 1
    8 -- null --> 1
{% endmermaid %}

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root == null) return null;
        TreeNode commonL = lowestCommonAncestor(root.left, p, q);
        TreeNode commonR = lowestCommonAncestor(root.right, p, q);
        if(root.val == p.val || root.val == q.val) return root;
        if(commonL != null && commonR != null) return root;
        
        return commonL == null ? commonR : commonL;
    }
}
```

#### Complexity

- Runtime Complexity: $O(N)$
- Space Complexity: $O(\log N)$

<a href="#post-order-excercise">Back to excercises</a>







<a name="250"></a>

### 250. Count Univalue Subtrees

```java
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */

public class Solution {
    int cnt = 0;
    /**
     * @param root: the given tree
     * @return: the number of uni-value subtrees.
     */
    public int countUnivalSubtrees(TreeNode root) {
        isUnivalTree(root);
        return cnt;
    }
    
    private boolean isUnivalTree(TreeNode root) {
        if(root == null) return true;
        boolean lIsUni = isUnivalTree(root.left);
        boolean rIsUni = isUnivalTree(root.right);
        if(lIsUni && rIsUni) {
            if(root.left == null && root.right == null) {
                cnt += 1;
                return true;
            } else if(root.left == null) {
                if(root.right.val == root.val) {
                    cnt += 1;
                    return true;
                } else {
                    return false;
                }
            } else if(root.right == null) {
                if(root.left.val == root.val) {
                    cnt += 1;
                    return true;
                } else {
                    return false;
                }
            } else {
                if(root.left.val == root.right.val && root.left.val == root.val) {
                    cnt += 1;
                    return true;
                } else {
                    return false;
                }
            }
        }
        return false;
    }
}
```

#### Complexity

- Runtime Complexity: $O(n)$
- Space Complexity:  $O(\log n)$, worst case unbalanced tree $O(n)$

<a href="#post-order-excercise">Back to excercises</a>





<a name="255"></a>

### 255. Verify Preorder Sequence in Binary Search

#### Recursive Solution

```java
public class Solution {
    int index = 0;
    /**
     * @param preorder: List[int]
     * @return: return a boolean
     */
    public boolean verifyPreorder(int[] preorder) {
        return traverse(preorder, null, null);
    }
    
    private boolean traverse(int[] preorder, Integer lo, Integer hi){
        if(preorder.length <= index) return true;
        
        if(lo != null && preorder[index] <= lo) return false;
        if(hi != null && preorder[index] >= hi) return false;
        
        index++;
        int parent = index - 1;
        boolean resultL = traverse(preorder, lo, preorder[parent]);
        boolean resultR = traverse(preorder, preorder[parent], hi);
        
        return resultL || resultR;
    }
}
```

##### Complexity

- Runtime Complexity: $O(N)$
- Space Complexity: $O(\log N)$, worst case $O(N)$ (stack overflow)

#### Iterative Solution

```java
public class Solution {
    /**
     * @param preorder: List[int]
     * @return: return a boolean
     */
    public boolean verifyPreorder(int[] preorder) {
        Integer lo = null;
        int N = preorder.length;
        Stack<Integer> stack = new Stack<Integer>(); //root ---> left path 
        for(int i = 0; i < N; ++i) {
            int node = preorder[i];
            if(lo != null && node <= lo) return false;
            while(!stack.isEmpty() && stack.peek() < node) {
                lo = stack.pop();
            }
            stack.push(node);
        }
        return true;
    }
}
```

##### Complexity

- Runtime Complexity: $O(N)$
- Space Complexity: $O(N)$

<a href="#others">Back to excercises</a>





<a name="257"></a>

### 257. Binary Tree Paths

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    List<String> results = new ArrayList<String>();
    public List<String> binaryTreePaths(TreeNode root) {
        if(root == null) return results;
        traverse(root, new LinkedList<Integer>());
        return results;
    }
    
    private void traverse(TreeNode root, LinkedList<Integer> path) {
        if(root == null) return;
        path.add(root.val);
        if(root.left == null && root.right == null) {
            StringBuilder sb = new StringBuilder();
            for(int i = 0; i<path.size(); ++i) {
                if(i != 0) sb.append("->");
                sb.append(path.get(i));
            }
            results.add(sb.toString());
        }
        traverse(root.left, path);
        traverse(root.right, path);
        path.pollLast();
    }
}
```

#### Complexity

- Runtime Complexity: $O(n)$
- Space Complexity:  $O(\log n)$, worst case unbalanced tree $O(n)$

<a href="#pre-order-excercise">Back to excercises</a>





<a name="270"></a>

### 270. Closest Binary Search Tree Value

```java
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */

public class Solution {
    double diff = Integer.MAX_VALUE;
    int result = 0;
    /**
     * @param root: the given BST
     * @param target: the given target
     * @return: the value in the BST that is closest to the target
     */
    public int closestValue(TreeNode root, double target) {
        if(root == null) return 0;
        traverse(root, target);
        return result;
        // write your code here
    }
    private void traverse(TreeNode root, double target) {
        if(root == null) return;
        if(Math.abs(root.val - target) < diff) {
            diff = Math.abs(root.val - target);
            result = root.val;
        }
        if(target < root.val) traverse(root.left, target);
        else traverse(root.right, target);
    }
}
```

#### Complexity

- Runtime Complexity: $O(\log n)$ , worst case unbalanced tree $O(n)$ 
- Space Complexity:  $O(\log n)$, worst case unbalanced tree $O(n)$

<a href="#pre-order-excercise">Back to excercises</a>





<a name="285"></a>

### 285. Inorder Successor in BST

- If current node is less or equal to target node, go directly to right subtree.
- If current node is larger than target node, save the result from left subtree. If the result from left subtree is null, then return the current node.

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */


public class Solution {
    /*
     * @param root: The root of the BST.
     * @param p: You need find the successor node of p.
     * @return: Successor of p.
     */
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        if(root == null) return null;
        if(root.val <= p.val) {
            return inorderSuccessor(root.right, p);
        } else {
            TreeNode node = inorderSuccessor(root.left, p);
            return node == null ? root : node;
        }
    }
}
```

#### Complexity

- Runtime Complexity: $O(\log N)$
- Space Complexity: $O(\log N)$

<a href="#in-order-excercise">Back to excercises</a>





<a name="298"></a>

### 298. Binary Tree Longest Consecutive Sequence

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    int maxCnt = 0;
    public int longestConsecutive(TreeNode root) {
        if(root == null) return maxCnt;
        traverse(root, root.val - 1, 0);
        return maxCnt;
    }
    
    private void traverse(TreeNode root, int pre, int cnt) {
        if(root == null) {
            maxCnt = Math.max(cnt, maxCnt);
            return;
        }
        if(root.val == pre + 1) {
            traverse(root.left, root.val, cnt + 1);
            traverse(root.right, root.val, cnt + 1);
        } else {
            maxCnt = Math.max(cnt, maxCnt);
            traverse(root.left, root.val, 1);
            traverse(root.right, root.val, 1);
        }
    }
}
```

#### Complexity

- Runtime Complexity: $O(n)$
- Space Complexity:  $O(\log n)$, worst case unbalanced tree $O(n)$

<a href="#pre-order-excercise">Back to excercises</a>





<a name="331"></a>

### 331. Verify Preorder Serialization of a Binary Tree

#### Stack

```java
class Solution {
    public boolean isValidSerialization(String preorder) {
        String[] serialization = preorder.split(",");
        if(serialization.length == 1 && serialization[0].equals("#")) {
            return true;
        }
        Stack<Integer> stack = new Stack<Integer>();
        for(int i = 0; i<serialization.length; ++i) {
            String val = serialization[i];
            if(val.equals("#")) {
                if(stack.isEmpty()) return false;
                int preCnt = stack.pop();
                stack.add(preCnt + 1);
                while (!stack.isEmpty() && stack.peek() == 2) {
                    stack.pop();
                    if(!stack.isEmpty()) {
                        preCnt = stack.pop();
                        stack.add(preCnt + 1);
                    }
                }
            } else {
                if(i != 0 && stack.isEmpty()) return false;
                stack.push(0);
            }
        }
        return stack.isEmpty();
    }
}          
```

##### Complexity:

- Runtime Complexity: $O(N)$
- Space Complexity: $O(N)$ 

#### Difference of in&out degree

For any graph, total of the in degree equals the total of the out degree. For each node from a binary tree, they have 2 out degree and 1 in degree. Exception exists for root and leaf node. Root node only have 2 out degree while leaf only have 1 in degree.

```java
class Solution {
    public boolean isValidSerialization(String preorder) {
        String[] serialization = preorder.split(",");
        int diff = 1; // set to 1 so that in+out degree for root is 2
        for(String s: serialization) {
            diff -= 1;
            if(diff < 0) return false;
            if(!s.equals("#")) diff += 2;
        }
        return diff == 0;
    }
}      
```

##### Complexity:

- Runtime Complexity: $O(N)$
- Space Complexity: $O(1)$ 

<a href="#others">Back to excercises</a>





<a name="337"></a>

### 337. House Robber II

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public int rob(TreeNode root) {
        if(root == null) return 0;
        int robL = rob(root.left), robR = rob(root.right), nRobL = 0, nRobR = 0;
        if(root.left != null) {
            TreeNode node = root.left;
            nRobL = rob(node.left) + rob(node.right);
        } 
        if(root.right != null) {
            TreeNode node = root.right;
            nRobR = rob(node.left) + rob(node.right);
        }
        return Math.max(robL + robR, root.val + nRobL + nRobR);
    }
}
```

#### Complexity

- Runtime Complexity: $O(?)$ 
- Space Complexity: $O(?)$

<a href="#pre-order-excercise">Back to excercises</a>





<a name="366"></a>

### 366. Find Leaves of Binary Tree

```java
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */


public class Solution {
    List<List<Integer>> results = new LinkedList<List<Integer>>();
    /*
     * @param root: the root of binary tree
     * @return: collect and remove all leaves
     */
    public List<List<Integer>> findLeaves(TreeNode root) {
        traverseForHeight(root);
        return results;
    }
    
    private int traverseForHeight(TreeNode root) {
        if(root == null) return 0;
        int leftHeight = traverseForHeight(root.left);
        int rightHeight = traverseForHeight(root.right);
        int height = Math.max(leftHeight, rightHeight);
        if(results.size() <= height) {
            results.add(new LinkedList<Integer>());
        }
        results.get(height).add(root.val);
        return height + 1;
    }
}
```

#### Complexity

- Runtime Complexity: $O(n)$ 
- Space Complexity:  $O(\log n)$, worst case unbalanced tree $O(n)$

<a href="#pre-order-excercise">Back to excercises</a>







## References

[^1]: https://en.wikipedia.org/wiki/Binary_tree
[^2]: https://www.cs.cmu.edu/~adamchik/15-121/lectures/Trees/trees.html


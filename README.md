# Leetcode_Day97
# Day 97 — Minimum Depth of Binary Tree

**LeetCode 111 | Easy | Java**

## Problem

Given the root of a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node to the nearest leaf node.

A leaf node is a node that has no children.

---

## Approach: Recursion (DFS)

I used a recursive Depth First Search (DFS) approach.

The idea is to calculate the minimum depth of the left and right subtrees and use the smaller depth.

### Steps

1. If the root is `null`, return `0`.
2. Recursively calculate the minimum depth of the left subtree.
3. Recursively calculate the minimum depth of the right subtree.
4. If either subtree has depth `0`, return the depth of the other subtree plus `1`.
5. Otherwise, return the smaller depth between the left and right subtrees, plus `1`.

### Important Observation

We cannot always simply use `Math.min(left, right)`.

If one child is missing, that path is not a valid path to a leaf. We must follow the existing subtree instead.

### Java Code

```java
class Solution {
    public int minDepth(TreeNode root) {
        if(root == null) {
            return 0;
        }

        int left = minDepth(root.left);
        int right = minDepth(root.right);

        if(left == 0 || right == 0) {
            return left + right + 1;
        }

        return Math.min(left, right) + 1;
    }
}
```

---

## Complexity Analysis

**Time Complexity: O(n)**

Every node is visited once to calculate its minimum depth.

**Space Complexity: O(h)**

The recursive call stack depends on the height of the tree.

- Balanced tree: O(log n)
- Skewed tree: O(n)

---

## What I Learned

- How recursion helps solve binary tree problems.
- How to calculate the depth of left and right subtrees.
- Why handling missing children separately is important.
- How DFS explores the tree to find the nearest leaf.

## Key Takeaway

Finding the shortest path isn't always about choosing the smaller number immediately. First, we need to make sure that the path is actually valid.

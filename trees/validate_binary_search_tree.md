# Validate Binary Search Tree

[Problem Link](https://leetcode.com/problems/validate-binary-search-tree/)

## Goal
I was asked to check if a binary tree is a valid BST. It’s a classic challenge that tests my ability to enforce ordering constraints on every subtree, not just the parent-child pair.

## Approach
I decided to use a recursive helper that carries the allowed min and max values down the tree. The key insight was that each node must be strictly between its ancestors’ bounds, not just its immediate parent. This eliminates the need for an in-order traversal or a stack, keeping the logic clean and the recursion tail‑recursive. The moment a node violates the bounds, I can return false immediately, which made the solution elegant and easy to reason about.

## Code
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isValidBST(TreeNode root) {
        return validate(root, null, null);
    }

    public boolean validate(TreeNode node, Integer min, Integer max) {
        if (node == null) {
            return true;
        }

        if ((min != null && node.val <= min) || (max != null && node.val >= max)) {
            return false;
        }

        return validate(node.left, min, node.val) && validate(node.right, node.val, max);
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(H)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1791979406/ejsol3rwhwip1r9csjyy.png)

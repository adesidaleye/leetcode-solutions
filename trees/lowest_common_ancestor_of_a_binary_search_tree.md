# Lowest Common Ancestor of a Binary Search Tree

[Problem Link](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

## Goal
I was asked to find the lowest common ancestor in a BST, which is a classic problem that tests my ability to leverage BST properties for efficient traversal.

## Approach
I realized we can walk from the root down, comparing p and q values. If both are less than current, go left; if both greater, go right; otherwise current is the LCA. The insight was that the BST ordering guarantees the split point is the answer, so no extra storage or recursion is needed.

## Code
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
        TreeNode current = root;

        while (current != null) {
            if (p.val < current.val && q.val < current.val) {
                current = current.left;
            } else if (p.val > current.val && q.val > current.val) {
                current = current.right;
            } else {
                return current;
            }
        }

        return null;
    }
}
```

## Complexities
- Time complexity: O(h) where h is the height of the tree (worst‑case O(N))
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1791854864/z5vvzujsxrayyukj1cwg.png)

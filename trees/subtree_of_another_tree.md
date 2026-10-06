# Subtree of Another Tree

[Problem Link](https://leetcode.com/problems/subtree-of-another-tree)

## Goal
Today I tackled LeetCode 572, Subtree of Another Tree. The task is to decide if one binary tree is a subtree of another—basically, does there exist a node in the main tree whose subtree matches the entire second tree? It feels like a classic tree‑matching puzzle and a good test of recursive thinking.

## Approach
I started by thinking of a brute force: walk every node in the main tree and at each one, check if the two trees are identical. That led me to two helper functions: one to walk the main tree, and one to compare two trees for equality. The key insight was realizing that the comparison can be a simple recursive check—if both nodes are null, they match; if one is null or the values differ, they don't; otherwise, recurse on left and right children. This keeps the code clean and lets the recursion naturally handle all cases. The only trick was remembering to stop early when a match is found, which saves time.


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
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if (root == null) {
            return false;
        }

        if (isSameTree(root, subRoot)) {
            return true;
        }

        return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
    }

    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null) {
            return true;
        }

        if (p == null || q == null) {
            return false;
        }

        if (p.val != q.val) {
            return false;
        }

        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }
}
```

## Complexities
- Time complexity: O(N*M)
- Space complexity: O(H1+H2)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1791256687/muzvovqifn0h16hcpkif.png)

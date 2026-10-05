# Same Tree

[Problem Link](https://leetcode.com/problems/same-tree)

## Goal
I was tasked with checking if two binary trees are identical. It’s a classic recursion exercise that tests my understanding of tree traversal and base case handling.

## Approach
I started by thinking about the base cases: if both nodes are null, they match; if one is null, they don't. Then I realized that the comparison is symmetric, so I just need to recursively compare left and right subtrees. A simple depth‑first recursion does the job, no extra data structures needed.

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
- Time complexity: O(N)
- Space complexity: O(H)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1791211703/aphpxfz44u48wdmzq9wi.png)

# Maximum Depth of Binary Tree

[Problem Link](https://leetcode.com/problems/maximum-depth-of-binary-tree)

## Goal
I was asked to find the maximum depth of a binary tree, basically count the longest path from root to leaf. It’s a classic recursion test, but I love how it forces me to think about tree traversal and base cases.

## Approach
I immediately thought about recursion because each node's depth depends on its children. The key insight was realizing that the depth of a node is 1 plus the max depth of its subtrees. I wrote a simple recursive helper, base case root null returns 0, then compute left/right depths, take max, add 1. Its clean and elegant.

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
    public int maxDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int left = maxDepth(root.left);
        int right = maxDepth(root.right);

        return 1 + Math.max(left, right);
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(H) (worst‑case O(N))

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1791208518/ms4wifgpwqpvuhqd8qpw.png)

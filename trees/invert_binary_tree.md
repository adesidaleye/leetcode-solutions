# Invert Binary Tree

[Problem Link](https://leetcode.com/problems/invert-binary-tree)

## Goal
Invert Binary Tree asks me to take a binary tree and swap every node's left and right child. It’s a classic recursion test and a great way to see how tree structure flips.

## Approach
I realized the problem is just a mirror operation, so I used recursion: if root is null return null; otherwise invert left and right subtrees, then swap them at the current node. The insight was that each node can be handled independently, making the code concise and natural.

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
    public TreeNode invertTree(TreeNode root) {
        if (root == null) {
            return null;
        }

        TreeNode left = invertTree(root.left);
        TreeNode right = invertTree(root.right);

        root.left = right;
        root.right = left;

        return root;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(H)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1791154727/dojaospe7wyxpcpfib5z.png)

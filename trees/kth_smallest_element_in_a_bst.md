# Kth Smallest Element in a BST

[Problem Link](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

## Goal
I was tasked with finding the kth smallest element in a BST. It’s a classic interview question that tests understanding of BST properties and traversal techniques.

## Approach
I remembered that an inorder traversal of a BST yields the nodes in sorted order. Instead of recursing, I used a stack to simulate the recursion and stopped as soon as I hit the kth node. That early exit was the key insight that kept the solution lean and efficient.

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
    public int kthSmallest(TreeNode root, int k) {
        Deque<TreeNode> stack = new ArrayDeque<>();
        TreeNode curr = root;

        while (curr != null || !stack.isEmpty()) {
            while (curr != null) {
                stack.push(curr);
                curr = curr.left;
            }

            curr = stack.pop();
            k--;

            if (k == 0) {
                return curr.val;
            }

            curr = curr.right;
        }

        return -1;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(H)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1792052786/k7ixovtgun4ir1jcdruh.png)

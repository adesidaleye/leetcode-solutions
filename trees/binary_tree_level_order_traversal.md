# Binary Tree Level Order Traversal

[Problem Link](https://leetcode.com/problems/binary-tree-level-order-traversal/)

## Goal
Today I tackled Binary Tree Level Order Traversal: given a binary tree, I need to return its nodes level by level. It’s a classic BFS exercise that’s surprisingly useful for visualizing tree structures and debugging tree‑based algorithms.

## Approach
I started by realizing that a queue is perfect for breadth‑first search. I pushed the root, then looped until the queue was empty. For each level I recorded the queue’s current size, popped that many nodes, added their values to a sublist, and enqueued their children. The moment that clicked was treating each loop iteration as a distinct level, so I could build the nested lists cleanly. No recursion, just iterative BFS—clean, efficient, and easy to trace.

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
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> list = new ArrayList<>();

        if (root == null) {
            return list;
        }

        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while (!queue.isEmpty()) {
            int len = queue.size();
            List<Integer> subList = new ArrayList<>(len);

            for (int i = 0; i < len; i++) {
                TreeNode node = queue.poll();
                subList.add(node.val);

                if (node.left != null) {
                    queue.offer(node.left);
                }

                if (node.right != null) {
                    queue.offer(node.right);
                }
            }

            list.add(subList);
        }

        return list;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(N)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1791939598/m7mocafydrystljy22vt.png)

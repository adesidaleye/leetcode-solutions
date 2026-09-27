# Linked List Cycle

[Problem Link](https://leetcode.com/problems/linked-list-cycle)

## Goal
Linked List Cycle asks me to determine if a singly linked list contains a loop. It’s a classic interview puzzle because it forces you to think about space‑efficient traversal and the beauty of two pointers dancing through the nodes.

## Approach
I first thought of hashing visited nodes, but that would use O(N) space. Then I remembered Floyd’s Tortoise and Hare. The trick is to move one pointer one step and the other two steps; if there’s a cycle they’ll inevitably collide. When they meet I return true, otherwise I walk until the fast pointer hits null. The moment the insight hit—two speeds guarantee detection with constant memory—everything fell into place.

## Code
```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) {
            return false;
        }

        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;

            if (slow == fast) {
                return true;
            }
        }

        return false;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790538952/swywkzpuh2zicifcguzj.png)

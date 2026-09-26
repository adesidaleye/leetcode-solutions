# Reverse Linked List

[Problem Link](https://leetcode.com/problems/reverse-linked-list)

## Goal
Reverse a singly linked list and return the new head. It’s a classic pointer‑manipulation puzzle that feels great when you get it right.

## Approach
I started by sketching the recursive idea, but the call stack felt wasteful. Then I remembered the in‑place trick: keep a prev, current, and next pointer. The key insight was to stash nextNode before reassigning current.next, so I never lose the rest of the list. Looping until current hits null flips every link in one pass—simple, O(N) time, O(1) space.

## Code
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */

class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode current = head;

        while (current != null) {
            ListNode nextNode = current.next;
            current.next = prev;
            prev = current;
            current = nextNode;
        }

        return prev;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790392356/fqfrq46ngv74erg4otyc.png)

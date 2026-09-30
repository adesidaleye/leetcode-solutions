# Reorder List

[Problem Link](https://leetcode.com/problems/reorder-list)

## Goal
I was challenged to reorder a singly linked list so that the nodes alternate from the start and end, like L0→Ln→L1→Ln-1… It feels like a puzzle because you have to do it in place without extra memory.

## Approach
I first remembered that you can split the list into two halves by using the fast‑slow pointer trick. Once split, reverse the second half. Then weave the two lists together node by node. The key insight was realizing that reversing the second half lets me pull nodes from the end in O(1) time, and the weaving loop handles the alternation. It felt like a neat dance of pointers.

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
    public void reorderList(ListNode head) {
        if (head == null || head.next == null) {
            return;
        }

        ListNode slow = head;
        ListNode fast = head.next;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        ListNode half2 = slow.next;
        slow.next = null;

        ListNode head2 = null;
        ListNode current = half2;

        while (current != null) {
            ListNode savedNode = current.next;
            current.next = head2;
            head2 = current;
            current = savedNode;
        }

        ListNode first = head;
        ListNode second = head2;

        while (second != null) {
            ListNode nextFirst = first.next;
            ListNode nextSecond = second.next;

            first.next = second;
            second.next = nextFirst;

            first = nextFirst;
            second = nextSecond;
        }

    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790753568/bujcbaeg72ydjxej9snp.png)

# Merge Two Sorted Lists

[Problem Link](https://leetcode.com/problems/merge-two-sorted-lists)

## Goal
I had to merge two sorted linked lists into one sorted list, preserving order. It’s a classic interview staple that tests my pointer juggling skills and edge‑case handling.

## Approach
I remembered the merge step from merge sort and decided to use a dummy head with a tail pointer. I repeatedly compared the current nodes of both lists, attached the smaller one to the tail, and advanced that list. Once one list ran out, I simply linked the remaining nodes of the other list. The key insight was realizing I could rewire the existing next pointers instead of creating new nodes, keeping space usage minimal.

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
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                tail.next = list1;
                list1 = list1.next;
            } else {
                tail.next = list2;
                list2 = list2.next;
            }

            tail = tail.next;
        }

        tail.next = (list1 == null) ? list2 : list1;

        return dummy.next;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790448973/bgobw0zdxjkvegirxnma.png)

# Remove Nth Node From End of List

[Problem Link](https://leetcode.com/problems/remove-nth-node-from-end-of-list)

## Goal
Remove Nth Node From End of List: I need to delete the nth node from the tail of a singly linked list in one pass.

## Approach
I started by thinking of the classic two‑pointer trick. If I keep a fast pointer n steps ahead of a slow pointer, when the fast hits the end the slow will be right before the node to remove. The dummy head solves the edge case of deleting the first node. The moment that clicked was realizing that moving both pointers together until the fast is null gives me the exact predecessor of the target node. I then simply bypass the target by adjusting the next reference. It’s a clean, O(N) one‑pass solution.

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0, head);

        ListNode left = dummy;
        ListNode right = head;

        int nth = 0;
        while (nth < n) {
            right = right.next;
            nth++;
        }

        while (right != null) {
            left = left.next;
            right = right.next;
        }

        left.next = left.next.next;

        return dummy.next;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790761731/ht49ag71scqxxp5p23ri.png)

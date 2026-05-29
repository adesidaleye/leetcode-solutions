# Binary Search

[Problem Link](https://leetcode.com/problems/binary-search/)

## Goal
I just tackled the Binary Search problem on LeetCode, and I'm excited to dive into how I solved it - the problem asks to find the index of a target number in a sorted array, which is a classic algorithmic challenge that's both interesting and practical.

## Approach
My approach was to use a standard binary search strategy, dividing the search space in half at each step. What really clicked for me was realizing that by maintaining a start and end pointer, I could efficiently narrow down the search space until I found the target or determined it wasn't present. The key insight was understanding how to adjust these pointers based on whether the middle element was greater than, less than, or equal to the target.

## Code
```java
class Solution {
    public int search(int[] nums, int target) {
        int start = 0;
        int end = nums.length - 1;

        while(start <= end) {
            int mid = (start + end) / 2;

            if(nums[mid] == target) {
                return mid;
            } else if (nums[mid] > target) {
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }
        return -1;
    }
}
```

## Complexities
- Time complexity: O(log N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1780083078/pvhvhsejq8vppfbf6pfo.png)

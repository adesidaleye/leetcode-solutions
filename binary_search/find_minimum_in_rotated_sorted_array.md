# Find Minimum in Rotated Sorted Array

[Problem Link](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array)

## Goal
Find the minimum element in a rotated sorted array. It’s a classic binary search twist that turns a simple linear scan into a log-time brain-teaser.

## Approach
I started by remembering that the rotation breaks the sorted order at a pivot. If nums[mid] is greater than nums[right], the smallest value must be to the right; otherwise it’s on the left or at mid. By repeatedly shrinking the search window with this comparison, I zero in on the pivot in log time. The key insight was realizing that comparing mid to the right bound tells me which side contains the unsorted segment.

## Code
```java
class Solution {
    public int findMin(int[] nums) {
        int left = 0;
        int right = nums.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] > nums[right]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        return nums[right];
    }
}
```

## Complexities
- Time complexity: O(log N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790791794/gfrzifqoofs7vvu45lfo.png)

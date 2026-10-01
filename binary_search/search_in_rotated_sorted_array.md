# Search in Rotated Sorted Array

[Problem Link](https://leetcode.com/problems/search-in-rotated-sorted-array)

## Goal
Today I tackled LeetCode’s "Search in Rotated Sorted Array". It’s a classic twist on binary search where the array’s pivot breaks the usual monotonic order, and I had to figure out how to still cut the search space in half.

## Approach
I started by remembering that even though the whole array isn’t sorted, at least one half is. I checked if the left side is sorted by comparing nums[left] to nums[mid]. If it is, I know the target must be either in that sorted half or the other. That was the key insight: use the sorted half to decide which direction to keep searching. Then I mirrored the logic for when the right side is sorted. The rest is just standard binary search updates. It felt satisfying to turn a seemingly messy array into a clean, logarithmic search again.

## Code
```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) {
                return mid;
            }

            if (nums[left] <= nums[mid]) {
                if (nums[left] <= target && target < nums[mid]) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            } else {
                if (nums[mid] < target && target <= nums[right]) {
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }

        return -1;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790815600/yxzzavfthytkmu3kz4oc.png)

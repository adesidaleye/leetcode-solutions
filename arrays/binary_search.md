# Binary Search

[Problem Link](https://leetcode.com/problems/binary-search/)

## Goal
I just tackled the Binary Search problem on LeetCode, where I had to find an element in a sorted array. What's interesting is that this problem asks for an efficient solution, and I love how it pushes me to think about optimization.

## Approach
My approach was to divide the search space in half at each step, which led me to use a while loop and update the start and end pointers based on whether the target is greater than or less than the middle element. The key insight was realizing that I could eliminate half of the search space with each comparison, making the solution much faster than a linear search.

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
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1780081532/u6yyqmf2igrpxzfdxxcf.png)

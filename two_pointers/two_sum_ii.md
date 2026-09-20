# Two Sum II

[Problem Link](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

## Goal
I was asked to find two indices in a sorted array that sum to a target, returning 1‑based indices. It’s a classic two‑pointer problem that shows how sorting can make a search linear.

## Approach
I remembered the two‑pointer pattern: start left at 0 and right at the end. Compute the sum; if it equals the target, return the indices (+1 for 1‑based). If the sum is too small, move left up; if too large, move right down. Because the array is sorted, this guarantees we’ll find the pair in a single pass. The key insight was realizing that the sorted order lets us decide which pointer to move without any extra look‑ups.

## Code
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int left = 0;
        int right = numbers.length - 1;

        while (left < right) {
            int sum = numbers[left] + numbers[right];

            if (sum == target) {
                return new int[] {left + 1, right + 1};
            } else if (sum < target) {
                left++;
            } else {
                right--;
            }
        }

        return new int[] {-1, -1};
    }
}
```

## Complexities
- Time complexity: O(n)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1789872095/vrcsvmsef3rubggfd1xy.png)

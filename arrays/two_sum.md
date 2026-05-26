# Two Sum

[Problem Link](https://leetcode.com/problems/two-sum/)

## Goal
I'm trying to solve the Two Sum problem, where I need to find two numbers in an array that add up to a given target. This problem is interesting because it requires me to think about how to efficiently search for pairs of numbers in an array.

## Approach
My initial approach was to use a brute force strategy with nested loops to check every possible pair of numbers in the array. However, I realized that this approach would be inefficient for large arrays. The key insight was that I could use a hash-based approach to store the numbers I've seen so far and their indices, but my initial solution actually used a simpler nested loop approach which still solves the problem but is less efficient than using a hash map.

## Code
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] indices = new int[2];

        for(int i = 0; i < nums.length; i++) {
            for(int j = i + 1; j < nums.length; j++) {
                if(nums[i] + nums[j] == target) {
                    indices[0] = i;
                    indices[1] = j;
                }
            }
        }

        return indices;
    }
}
```

## Complexities
- Time complexity: O(N^2)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1779753641/fgnu5lo0rnrzyatwqusd.png)

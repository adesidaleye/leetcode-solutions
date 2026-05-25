# Two Sum

[Problem Link](https://leetcode.com/problems/two-sum/)

## Goal
I'm trying to solve the Two Sum problem, which asks me to find two numbers in an array that add up to a given target - it's interesting because it requires a combination of algorithmic thinking and data structure knowledge, and I'm excited to see how I can optimize my solution.

## Approach
My initial thought was to use a brute force approach with nested loops to check every possible pair of numbers, but as I started coding, I realized that this strategy would be inefficient for large arrays - the key insight was recognizing that I could improve this by using a more efficient data structure, such as a hashmap, to store the numbers I've seen so far and their indices, allowing me to find the complement of the current number in constant time.

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
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1779751914/s9mn2lhgca7vptt2jaib.png)

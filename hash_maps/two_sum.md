# Two Sum

[Problem Link](https://leetcode.com/problems/two-sum/)

## Goal
I'm tackling the Two Sum problem, which asks me to find two numbers in an array that add up to a given target. I love this problem because it's simple yet powerful, and it's a great example of how a clever data structure can make all the difference.

## Approach
My approach was to use a hash map to store the numbers I've seen so far and their indices. The key insight was to calculate the remainder of the target minus the current number, and then check if that remainder is already in the map. If it is, I've found my two numbers! If not, I add the current number to the map and move on. This strategy clicked when I realized that the hash map would allow me to look up numbers in constant time, making the whole algorithm much faster.

## Code
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();

        for(int i = 0; i < nums.length; i++) {
            int remainder = target - nums[i];

            if(!map.containsKey(remainder)) {
                map.put(nums[i], i);
            } else {
                return new int[] {map.get(remainder), i};
            }
        }
        return new int[] {};
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(N)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1783099739/o5qgxezb0qbt41pyihxq.png)

# Contains Duplicate

[Problem Link](https://leetcode.com/problems/contains-duplicate)

## Goal
I'm tackling the Contains Duplicate problem on LeetCode, which asks me to determine if there are any duplicate elements in an array of integers. I find this interesting because it requires me to think about efficient ways to keep track of the elements I've seen so far, and it has practical applications in data processing and analysis.

## Approach
My approach to solving this problem was to use a hash map to store the elements I've seen. The key insight here was realizing that hash maps have an average time complexity of O(1) for insert and search operations, making them ideal for this type of problem. I chose to use a HashSet in Java, which automatically eliminates duplicates and provides a convenient way to check if an element is already present. As I iterated through the array, I added each element to the set and checked if it was already present - if it was, I immediately returned true, indicating that a duplicate had been found.

## Code
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> seen = new HashSet<>();
        for(int num : nums) {
            if(!seen.add(num)) {
                return true;
            }
        }
        return false;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(N)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1783007501/qwrclrstipfkrtmuvftu.png)

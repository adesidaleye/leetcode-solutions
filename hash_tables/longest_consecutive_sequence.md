# Longest Consecutive Sequence

[Problem Link](https://leetcode.com/problems/longest-consecutive-sequence/description/)

## Goal
I was challenged to find the length of the longest run of consecutive numbers in an unsorted array. It feels like a hidden puzzle: you can't just sort because that would waste time; you need to spot a pattern.

## Approach
I remembered the trick from the Longest Consecutive Sequence solution: put numbers into a hash set for O(1) lookups, then for each number start a chain only if it has no predecessor. That way each element is processed once. The insight was realizing that checking for a missing predecessor lets me skip redundant work and keep the algorithm linear.

## Code
```java
class Solution {
    public int longestConsecutive(int[] nums) {
        Set<Integer> set = new HashSet<>();
        int longest = 0;

        for(int num : nums) {
            set.add(num);
        }

        for(int num : set) {
            if(!set.contains(num - 1)) {
                int currentNum = num;
                int length = 1;

                while(set.contains(currentNum + 1)) {
                    currentNum++;
                    length++;
                }

                longest = Math.max(longest, length);
            }
        }

        return longest;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(N)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1789581669/e1nprvzcvycndahxuyiy.png)

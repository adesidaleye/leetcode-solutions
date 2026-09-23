# Longest Substring Without Repeating Characters

[Problem Link](https://leetcode.com/problems/longest-substring-without-repeating-characters)

## Goal
I was challenged to find the longest substring in a string that has no repeating characters. It's a classic sliding window puzzle that forces you to think about how to keep track of the window efficiently.

## Approach
I started by picturing a two‑pointer window that expands until a duplicate appears, then shrinks from the left until the duplicate disappears. The aha moment was realizing that a HashSet can keep track of characters in the current window, letting me check for duplicates in O(1) time. This keeps the loop linear overall.

## Code
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int longest = 0;
        int left = 0;
        Set<Character> set = new HashSet<>();

        for (int right = 0; right < s.length(); right++) {
            char currentChar = s.charAt(right);

            while (set.contains(currentChar)) {
                set.remove(s.charAt(left));
                left++;
            }

            set.add(currentChar);

            longest = Math.max(longest, right - left + 1);
        }

        return longest;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(N)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790144716/miaqoismnyiqgclbxjq0.png)

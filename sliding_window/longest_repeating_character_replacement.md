# Longest Repeating Character Replacement

[Problem Link](https://leetcode.com/problems/longest-repeating-character-replacement)

## Goal
I was challenged to find the longest substring that can be turned into all one character by changing at most k letters. It felt like a classic sliding window puzzle but with a twist: we need to keep track of the most frequent letter inside the window. The problem is intriguing because it blends greedy window expansion with a clever frequency check.

## Approach
At first I thought about brute force, but that would be O(N^2). Then I remembered the sliding window trick from the 'Longest Substring with At Most K Distinct' problem. The key insight was realizing that the window can stay valid as long as the number of letters that need changing (window length minus the count of the most frequent letter) is <= k. So I keep a frequency array of 26 letters, update the max frequency on each step, and shrink from the left when the condition fails. This gives O(N) time.

## Code
```java
class Solution {
    public int characterReplacement(String s, int k) {
        int[] frequencyMap = new int[26];
        int maxLength = 0;

        int maxFreq = 0;
        int left = 0;

        for (int right = 0; right < s.length(); right++) {
            frequencyMap[s.charAt(right) - 'A']++;

            maxFreq = Math.max(maxFreq, frequencyMap[s.charAt(right) - 'A']);

            while ((right - left + 1) - maxFreq > k) {
                frequencyMap[s.charAt(left) - 'A']--;
                left++;
            }

            maxLength = Math.max(maxLength, right - left + 1);
        }

        return maxLength;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790258580/xzikamhkdn5xanxajpgy.png)

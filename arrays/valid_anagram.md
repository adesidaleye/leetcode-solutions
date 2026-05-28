# Valid Anagram

[Problem Link](https://leetcode.com/problems/valid-anagram)

## Goal
I wanted to tackle the Valid Anagram problem on LeetCode, which asks to determine if two given strings are anagrams of each other. This problem fascinates me because it requires an efficient algorithm to compare the characters in both strings, and I was excited to dive into it.

## Approach
My approach to solving this problem was to first compare the lengths of the two strings. If they are not equal, I immediately return false because anagrams must have the same number of characters. Next, I converted the strings into character arrays, sorted them, and then compared the sorted arrays. The key insight here was realizing that if the sorted arrays are equal, then the original strings are anagrams of each other. This strategy works well because sorting the arrays allows us to easily compare the characters in the strings, even if they are in a different order.

## Code
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length()) {
            return false;
        }
        
        char[] sArr = s.toCharArray();
        char[] tArr = t.toCharArray();

        Arrays.sort(sArr);
        Arrays.sort(tArr);

        if(Arrays.equals(sArr, tArr)) {
            return true;
        }

        return false;
    }
}
```

## Complexities
- Time complexity: O(N log N)
- Space complexity: O(N)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1779926568/ams7clzkdpyprg72mvkh.png)

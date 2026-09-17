# Valid Palindrome

[Problem Link](https://leetcode.com/problems/valid-palindrome)

## Goal
I was asked to determine if a given string is a palindrome, ignoring non‑alphanumeric characters and case. It feels like a classic two‑pointer problem but the extra cleanup keeps it interesting.

## Approach
I started with the two‑pointer pattern: left at 0, right at end. I kept bumping each pointer past any punctuation or space using while loops. Once I landed on real characters, I lowered both and compared. That simple skip‑compare loop made the solution clean and O(N). The key insight was realizing I could ignore everything that isn’t a letter or digit on the fly instead of building a filtered string.

## Code
```java
class Solution {
    public boolean isPalindrome(String s) {
        int left = 0;
        int right = s.length() - 1;

        while(left < right) {
            while(left < right && !Character.isLetterOrDigit(s.charAt(left))) {
                left++;
            }

            while(left < right && !Character.isLetterOrDigit(s.charAt(right))) {
                right--;
            }

            char lChar = Character.toLowerCase(s.charAt(left));
            char rChar = Character.toLowerCase(s.charAt(right));

            if(lChar != rChar) {
                return false;
            }

            left++;
            right--;
        }

        return true;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1789669955/coytj5y4dk4kbvi04t5e.png)

# Valid Parentheses

[Problem Link](https://leetcode.com/problems/valid-parentheses)

## Goal
I'm tackling the Valid Parentheses problem on LeetCode, where I need to determine if a given string of parentheses is valid. This problem is interesting because it requires me to think about how to efficiently validate the nesting of parentheses, which is a fundamental concept in programming.

## Approach
My approach to solving this problem involved using a stack data structure to keep track of the opening parentheses and a map to store the corresponding closing parentheses. The key insight was realizing that I could use the map to look up the expected opening parenthesis when I encounter a closing parenthesis, and then check if the top of the stack matches. This strategy allows me to iterate through the string only once, making it efficient.

## Code
```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> bracs = new Stack<>();
        Map<Character, Character> map = Map.of(
            ')', '(',
            '}', '{',
            ']', '['
        );

        for (Character ch : s.toCharArray()) {
            if (map.containsKey(ch)) {
                if (bracs.isEmpty() || bracs.peek() != map.get(ch)) {
                    return false;
                }
                
                bracs.pop();
            } else {
                bracs.push(ch);
            }
        }

        return bracs.isEmpty();
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(N)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1780169372/chni3r6ijozwd4fqzbgr.png)

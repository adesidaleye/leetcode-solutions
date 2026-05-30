# Valid Parentheses

[Problem Link](https://leetcode.com/problems/valid-parentheses)

## Goal
I'm tackling the Valid Parentheses problem on LeetCode, which asks me to determine whether a given string of parentheses is valid. This problem is interesting because it requires me to think about how to efficiently validate the nesting of parentheses in a string, a common task in many programming applications.

## Approach
My approach to solving this problem involved using a stack data structure to keep track of the opening parentheses encountered so far. The key insight that clicked for me was realizing that I could use a map to store the corresponding closing parentheses for each opening parenthesis, allowing me to easily check if a closing parenthesis matches the top of the stack. This strategy made it easy to iterate through the string and validate the parentheses in a single pass.

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
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1780148381/jliakwhrtzm81nm2pdzw.png)

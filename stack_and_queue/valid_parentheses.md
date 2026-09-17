# Valid Parentheses

[Problem Link](https://leetcode.com/problems/valid-parentheses/)

## Goal
I was challenged to check if a string of parentheses is properly nested. It's a quick sanity test for syntax parsing and I love the stack vibe.

## Approach
I thought stack first, because each opening needs a closing. I looped, pushing opens, popping on closes, checking matches. The big aha was returning false immediately when the stack is empty or mismatched - no wasted loops. Finally, I make sure the stack is empty at the end. Simple, but effective.

## Code
```java
class Solution {
    public boolean isValid(String s) {
        char[] characters = s.toCharArray();
        Stack<Character> stack = new Stack<>();

        for(char c : characters) {
            if(c == '(' || c == '{' || c == '[') {
                stack.push(c);
            } else {
                if(stack.empty()) {
                    return false;
                }

                char top = stack.pop();

                if(!(top == '(' && c == ')' 
                || top == '{' && c == '}'
                || top == '[' && c == ']')) {
                    return false;
                }
            }
        }

        return stack.empty();
    }
}
```

## Complexities
- Time complexity: O(n)
- Space complexity: O(n)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1789661199/w8kajdga6jhgw8kp1hiv.png)

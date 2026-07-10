# Decode and Encode Strings

[Problem Link](https://leetcode.com/problems/encode-and-decode-strings)

## Goal
I just tackled the Encode and Decode Strings problem on LeetCode, and it's fascinating because it challenges me to design a robust encoding and decoding scheme for a list of strings. The goal is to create a single string that represents all the input strings and then decode it back to the original list, which requires careful consideration of how to separate and identify each string.

## Approach
My approach was to use a delimiter-based strategy. I realized that if I could somehow embed the length of each string into the encoded string, I could accurately decode it later. The key insight was using the '@' character as a delimiter and prepending the length of each string to itself. This way, during decoding, I can parse the length, read that many characters, and add the string to my decoded list. It clicked when I understood that by including the length, I could avoid ambiguity and ensure accurate decoding.

## Code
```java
class Solution {

    public String encode(List<String> strs) {
        StringBuilder encoded = new StringBuilder();

        for(String str : strs) {
            encoded.append(str.length()).append('@').append(str);
        }

        return encoded.toString();
    }

    public List<String> decode(String str) {
        List<String> decoded = new ArrayList<>();
        if(str.length() == 0) {
            return decoded;
        }

        int start = 0;
        while(start < str.length()) {
            int end = str.indexOf('@', start);

            String wordLen = str.substring(start, end);
            int length = Integer.parseInt(wordLen);

            start = end + 1;
            String word = str.substring(start, start + length);
            decoded.add(word);

            start += length;
        }

        return decoded;
    }
}

```

## Complexities
- Time complexity: O(N)
- Space complexity: O(N)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1783724741/kthkgzyvkn4tobjjpzvb.png)

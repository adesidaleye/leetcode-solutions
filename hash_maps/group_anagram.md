# Group Anagram

[Problem Link](https://leetcode.com/problems/group-anagrams)

## Goal
I'm tackling the Group Anagrams problem, which asks me to group a list of strings into anagrams. This problem is interesting because it requires me to think creatively about how to efficiently categorize strings based on their character composition, rather than their literal sequence.

## Approach
My thought process started with realizing that anagrams are essentially strings with the same characters, just in a different order. This led me to consider sorting the characters in each string as a way to create a 'key' that could be used to group anagrams together. The key insight was that by sorting the characters in each string, I could use these sorted strings as keys in a hashmap to efficiently group the anagrams.

## Code
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String, List<String>> map = new HashMap<>();

        for(String str : strs) {
            char[] strArray = str.toCharArray();
            Arrays.sort(strArray);
            String sortedStr = new String(strArray);

            if(!map.containsKey(sortedStr)) {
                map.put(sortedStr, new ArrayList<>(Arrays.asList(str)));
            } else {
                map.get(sortedStr).add(str);
            }
        }

        return new ArrayList<>(map.values());
    }
}
```

## Complexities
- Time complexity: O(NM log M)
- Space complexity: O(NM)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1783193693/jycxuor2iuthduf5novk.png)

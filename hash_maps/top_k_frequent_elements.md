# Top K Frequent Elements

[Problem Link](https://leetcode.com/problems/top-k-frequent-elements)

## Goal
I'm tackling the Top K Frequent Elements problem on LeetCode, which asks me to find the k most frequent elements in an array. This problem is interesting because it requires me to think about how to efficiently count and rank elements in an array, and how to handle cases where there are multiple elements with the same frequency.

## Approach
My approach to this problem started with using a hash map to count the frequency of each element in the array. Then, I realized that I needed a way to efficiently get the top k elements, so I used a bucket sort approach, where I created an array of lists, and each index in the array corresponds to a frequency. I then iterated over the hash map and added each element to the corresponding list in the array. The key insight here was to iterate over the array in reverse order, so that I can get the most frequent elements first. This way, I can stop as soon as I have found k elements, without having to iterate over the entire array.

## Code
```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer,Integer> map = new HashMap<>();

        for(int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        List<Integer>[] buckets = new ArrayList[nums.length + 1];

        for(int i = 0; i < buckets.length; i++) {
            buckets[i] = new ArrayList<>();
        }
        for(int key : map.keySet()) {
            int frequency = map.get(key);
            buckets[frequency].add(key);
        }

        int[] kNums = new int[k];
        int kIndex = 0;

        for(int i = buckets.length - 1; i >= 0; i--) {
            for(int num : buckets[i]) {
                kNums[kIndex] = num;
                kIndex++;

                if(kIndex == k) {
                    return kNums;
                }
            }
        }
        return kNums;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(N)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1783322379/weedbvzbddxkte4tyqqg.png)

# 3Sum

[Problem Link](https://leetcode.com/problems/3sum/)

## Goal
3Sum asks for all unique triplets in an array that sum to zero – a classic puzzle that blends sorting with two‑pointer logic, and a great test of handling duplicates.

## Approach
I started by sorting the array; that instantly lets me use a two‑pointer sweep for each fixed element. The key insight was realizing that once the current number is positive, the rest can’t sum to zero, so I break early. Skipping equal values at the start of each loop and after finding a triplet removes duplicates in linear time. This keeps the solution clean and efficient.

## Code
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> list = new ArrayList<>();

        Arrays.sort(nums);

        for (int i = 0; i < nums.length - 2; i++) {
            if (nums[i] > 0) {
                break;
            }

            if (i > 0 && nums[i] == nums[i - 1]) {
                continue;
            }

            int left = i + 1;
            int right = nums.length - 1;

            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];

                if (sum == 0) {
                    list.add(Arrays.asList(nums[i], nums[left], nums[right]));

                    while (left < right && nums[left] == nums[left + 1]) {
                        left++;
                    }

                    while (left < right && nums[right] == nums[right - 1]) {
                        right--;
                    }

                    left++;
                    right--;
                } else if (sum < 0) {
                    left++;
                } else {
                    right--;
                }
            }
        }

        return list;
    }
}
```

## Complexities
- Time complexity: O(n^2)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790017151/jcmzmpou028fafuyexqg.png)

# Container With Most Water

[Problem Link](https://leetcode.com/problems/container-with-most-water)

## Goal
I was challenged to find the maximum area between two lines in an array, like a bucket holding water. It's a classic two-pointer problem that tests greedy intuition.

## Approach
I started with brute force, then remembered the two-pointer trick: start at both ends, compute area, move the shorter line inward because height limits the area. That insight reduced to O(N). I coded it and it passed.

## Code
```java
class Solution {
    public int maxArea(int[] height) {
        int area = 0;
        int left = 0;
        int right = height.length - 1;

        while (left < right) {
            int width = right - left;
            int breadth = Math.min(height[left], height[right]);

            int currentArea = breadth * width;

            area = Math.max(area, currentArea);

            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

        return area;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790029781/gisetnqwvpu3frk9xa4s.png)

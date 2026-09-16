# Valid Sudoku

[Problem Link](https://leetcode.com/problems/valid-sudoku/)

## Goal
I had to write a validator for a Sudoku board, checking rows, columns, and 3x3 boxes for duplicates. It’s a neat exercise in array indexing and careful boundary handling.

## Approach
I mapped each cell’s character to a 0‑based index (num - '1'), used three 9×9 boolean tables for rows, columns, and boxes, and computed the box index as (r/3)*3 + c/3. As I scan, I check if the number already appeared in its row, column, or box; if so, the board is invalid. This brute‑force but constant‑time method keeps the code simple and fast.

## Code
```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        boolean[][] rows = new boolean[9][9];
        boolean[][] cols = new boolean[9][9];
        boolean[][] boxes = new boolean[9][9];

        for(int r = 0; r < 9; r++) {
            for(int c = 0; c < 9; c++) {
                int num = board[r][c];

                if(num == '.') {
                    continue;
                }

                // convert 1-9 value to 0-8 for array using ASCII values
                int val = num - '1';
                // convert 2D coordinate to 1D value (e.g. (0, 1) -> 2)
                int boxIndex = (r/3)*3 + c/3;

                // check arrays if val index has been changed to true using the value itself
                if(rows[r][val] || cols[c][val] || boxes[boxIndex][val]) {
                    return false;
                }
                
                // If no, change value across all arrays to true, so next time, if same value val is checked, it will be true and if statement will return false
                rows[r][val] = true;
                cols[c][val] = true;
                boxes[boxIndex][val] = true;
            }
        }
        
        return true;
    }
}
```

## Complexities
- Time complexity: O(1)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1789581261/aqti0mfhcj5v46vviq9v.png)

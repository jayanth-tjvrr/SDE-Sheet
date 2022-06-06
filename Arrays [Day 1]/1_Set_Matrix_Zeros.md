## Set Matrix Zeroes
- [LeetCode](https://leetcode.com/problems/set-matrix-zeroes/)
- [Youtube](https://www.youtube.com/watch?v=M65xBewcqcI&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=9)

# Problem Statement

```

Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.
You must do it in place.

```

# Problem Solutions

- Brute Force Approach

```
    1. Traverse the matrix
    2. When you find a zero, traverse the particular row and column and set all the values to -1 except 0's
    3. Traverse again and change all -1's to 0's
    
    Complexity : O(N * M) + O(N + M)

        - Traversing : O(N * M)
        - Traverse row and column : O(N + M)

    Space Complexity : O(1)
```
```cpp
    void SetZeroes(vector<vector<int>>& nums) {
         int row = nums.size(), col = nums[0].size()-1;
        
        for(int i = 0; i < row; i++)
        {
            for(int j = 0; j < col; j++)
            {
                if(nums[i][j] == 0)
                {
                    for(int l = 0;l < col; l++)
                        if(nums[i][l] != 0) nums[i][l] = -1
                    for(int m = 0;m < row; m++)
                        if(nums[m][j] != 0) nums[m][j] = -1
                }
            }
        }
        for(int i = 0;i < row;i++)
        {
            for(int j = 0;j < col;j++)
            {
                if(nums[i][j] == -1)
                    nums[i][j] = 0;
            }
        }

    }
```

- Better Approach

```
    1. Initialize row and column vectors.
    2. Traverse the matrix.
    3. While traversing the matrix, if we find 0, update the row and column matrix with 0 at the position.
    4. Traverse the matrix again and make the elements zero based on the row and column matrix.



    Time Complexity : O(N * M)
    Space Complexity : O(M + N)

```
```cpp
    void setZeroes(vector<vector<int>>& matrix) {
        int row = matrix.size(), col = matrix[0].size();
        vector<int> rows(row, 1);
        vector<int> cols(col, 1);
        for(int i = 0;i < row;i++)
        {
            for(int j = 0; j< col;j++)
            {
                if(matrix[i][j] == 0)
                {
                    rows[i] = 0;
                    cols[j] = 0;
                }
            }
        }
        for(int i = row-1; i >= 0; i--)
        {
            for(int j = col-1; j>=0; j--)
            {
                if(rows[i] == 0 || cols[j] == 0)
                    matrix[i][j] = 0;
            }
        }
    }
            
```

- Best approach to reduce the space complexity.

```
    1. Same approach as above but use the first row and column instead of declaring two new vectors.



    Time Complexity : O(N * M)
    Space Complexity : O(1)
    
```
```cpp
    void setZeroes(vector<vector<int>>& matrix) {
        int col0 = 1, row = matrix.size(), col = matrix[0].size();
        for(int i = 0;i < row;i++)
        {
            if(matrix[i][0] == 0)
                col0 = 0;
            for(int j = 1; j< col;j++)
            {
                if(matrix[i][j] == 0)
                {
                    matrix[i][0] = matrix[0][j] = 0;
                }
            }
        }
        for(int i = row-1; i >= 0; i--)
        {
            for(int j = col-1; j>=1; j--)
            {
                if(matrix[i][0] == 0 || matrix[0][j] == 0)
                    matrix[i][j] = 0;
            }
            if(col0 == 0)
                matrix[i][0] = 0;
        }
            
    }
```

## Pascals Triangle

- [Leetcode](https://leetcode.com/problems/pascals-triangle/)
- [Youtube](https://youtu.be/6FLvhQjZqvM)

## Different Ways of Asking Questions

1. Given a Row Number. Ask to print pascal triangle upto n rows
2. Given a row number. and Ask to print that particular row
3. Given a row, column value and ask to print that number
    ```
    5,3    5th row -> 14641    3rd number -> 6
    
    For this the formula is Row-1 C column-1 => 4C2 => 4*3/2*1 => 6 
    ```

## O(N*N) Approach

```cpp
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> row(numRows);
        for(int i=0;i<numRows;i++){
            row[i].resize(i+1);
            row[i][0] = row[i][i] = 1;
            
            for(int j=1;j<i;j++){
                row[i][j] = row[i-1][j-1]+row[i-1][j];
            } 
        }
    return row;
    }
```
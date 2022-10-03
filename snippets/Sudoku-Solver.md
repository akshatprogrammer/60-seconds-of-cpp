---
title: Sudoku Solver
tags: Array Backtracking Matrix
expertise: intermediate
---

-Given: Write a program to solve a Sudoku puzzle by filling the empty cells.

  A sudoku solution must satisfy all of the following rules:

1. Each of the digits 1-9 must occur exactly once in each row.
2. Each of the digits 1-9 must occur exactly once in each column.
3. Each of the digits 1-9 must occur exactly once in each of the 9 3x3 sub-boxes of the grid. <br>
The '.' character indicates empty cells.
-Input: root = [1,null,2,3]
-Output: [1,3,2]

```cpp
class Solution {
public:
    bool isValid(int row,int col,char c,vector<vector<char>>& board){
        for(int i=0;i<9;i++){
            if(board[row][i]==c) return false;
            if(board[i][col]==c) return false;
            if(board[3*(row/3)+i/3][3*(col/3)+i%3]==c) return false;
            
        }
        return true;
    }
    bool solve(vector<vector<char>>& board){
        for(int i=0;i<board.size();i++){
            for(int j=0;j<board[0].size();j++){
                if(board[i][j]=='.'){
                    for(char c='1';c<='9';c++){
                        if(isValid(i,j,c,board)){
                            board[i][j]=c;
                        if(solve(board)) 
                            return true;
                        else
                            board[i][j]='.';          
                    }
                }
                return false;
            }
        }
        }
        return true;
    }
    void solveSudoku(vector<vector<char>>& board) {
        solve(board);
    }
};
```

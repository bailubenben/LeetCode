```java

public class Solution {
    public void solveSudoku(char[][] board) {
        if(board == null || board.length < 1)
            return;
        solve(board);
    }
    public boolean solve(char[][] board) {
        for(int i = 0; i < board.length; i++) {
            for(int j = 0; j < board[0].length; j++) {
                if(board[i][j] == '.') {
                    for(char v = '1'; v <= '9'; v ++) {
                        if(isValid(board, i, j, v)) {
                            board[i][j] = v;
                        
                            if(solve(board))
                                return true;
                            else
                                board[i][j] = '.';
                        }
                    }
                    return false;
                }
                
            }
        }
        return true;
    }
    public boolean isValid(char[][] board, int i, int j, char v) {
        for(int k = 0; k < 9; k++) {
            if(k != j && board[i][k] == v)
                return false;
            if(k != i && board[k][j] == v)
                return false;
            if (3 * (i / 3) + k / 3 != i && 3 * (j / 3) + k % 3 != j && board[ 3 * (i / 3) + k / 3][3 * (j / 3) + k % 3] == v)
                return false;
        }
        return true;
    }
}
```

class Solution {
    public int countSquares(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        int[][] dp = new int[m][n];
        int count = 0;

        // Fill dp array
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                // If it's the first row or first column, just copy the value
                if (i == 0 || j == 0) {
                    dp[i][j] = matrix[i][j];
                } 
                // For other cells, if the value in matrix is 1, check for minimum of the previous cells
                else if (matrix[i][j] == 1) {
                    dp[i][j] = Math.min(dp[i - 1][j], Math.min(dp[i][j - 1], dp[i - 1][j - 1])) + 1;
                }
                count += dp[i][j];
            }
        }

        return count;
    }
}

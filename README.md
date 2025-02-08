# Leetcode---1143
Longest Common Subsequence
//code in java
public class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();
        
        // Create a 2D array to store the lengths of longest common subsequence.
        int[][] dp = new int[m + 1][n + 1];
        
        // Fill the dp array.
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        
        return dp[m][n];
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        String text1 = "abcde";
        String text2 = "ace";
        int result = solution.longestCommonSubsequence(text1, text2);
        System.out.println("The length of the longest common subsequence is: " + result);
    }
}

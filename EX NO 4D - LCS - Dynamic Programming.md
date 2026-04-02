
# EX 4D Longest Common SubSequence - Dynamic Programming.
## AIM:
To write a Java program to for given constraints.
Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.
A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".
A common subsequence of two strings is a subsequence that is common to both strings.

Input: text1 = "abcde", text2 = "ace" 
Output: 3  
Explanation: The longest common subsequence is "ace" and its length is 3.
Constraints:

1 <= text1.length, text2.length <= 1000
text1 and text2 consist of only lowercase English characters.

## Algorithm
1. Input:
Read two strings, text1 and text2, from the user.

2. Initialization:
Let m = length of text1 and n = length of text2.
Create a 2D array dp[m+1][n+1], where dp[i][j] stores the length of the longest common subsequence (LCS) between text1[0..i-1] and text2[0..j-1].

3. Filling the DP Table:
   > For each i from 1 to m:
   
   > For each j from 1 to n:
   
   > If characters match (text1.charAt(i-1) == text2.charAt(j-1)): → dp[i][j] = 1 + dp[i-1][j-1]
   
   > Else: → dp[i][j] = max(dp[i-1][j], dp[i][j-1])

4. Result:
The value dp[m][n] gives the length of the longest common subsequence.

## Program:
```
import java.util.Scanner;

public class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();

        int[][] dp = new int[m + 1][n + 1];

        // Fill the dp table
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1] + 1; // characters match
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]); // skip one character
                }
            }
        }

        return dp[m][n]; // Length of LCS
    }

    // Main method for input and output
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        String text1 = sc.nextLine().replaceAll("\"", "");
        String text2 = sc.nextLine().replaceAll("\"", "");

        int lcsLength = sol.longestCommonSubsequence(text1, text2);
        System.out.println("Length of Longest Common Subsequence: " + lcsLength);

        sc.close();
    }
}

```

## Output:

<img width="919" height="233" alt="image" src="https://github.com/user-attachments/assets/92cedc89-5e1b-45df-87d8-ba1d328a4c27" />

## Result:
The program successfully implemented and the expected output is verified.

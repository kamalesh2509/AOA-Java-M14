
# EX 4B Frog Jump - Dynamic Programming.
## AIM:
To write a Java program to for given constraints.
A Frog Jump 1 or 2 steps at a time.
Problem Statement:

A frog is at the bottom of the stairs with n steps. It can jump either 1 or 2 steps at a time. Write a program to find the number of distinct ways the frog can reach the top (n-th step).

Input Format:

A single integer n (1 ≤ n ≤ 45) – number of steps.
 Output Format:

A single integer – number of distinct ways to reach step n.

## Algorithm
1. Start the program and read the integer n (number of steps) from the user.
2. If n equals 1, return 1; if n equals 2, return 2.
3. Initialize two variables: first = 1 and second = 2 to represent ways to reach steps 1 and 2.
4. Use a loop from 3 to n, updating current = first + second, then shift values (first = second, second = current).
5. After the loop ends, print the value of current as the total number of ways the frog can reach step n.

## Program:
```
/*
Program to implement Reverse a String
Developed by:KAMALESH E
Register Number: 212222100019
*/

import java.util.Scanner;

public class FrogJump {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
       
        int n = scanner.nextInt();
        scanner.close();

        System.out.println(countWays(n));
    }

   
    public static int countWays(int n) {
        if (n == 1) return 1;
        if (n == 2) return 2;

        int[] dp = new int[n + 1];
        dp[1] = 1;
        dp[2] = 2;

        for (int i = 3; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }

        return dp[n];
    }
}

```

## Output:

<img width="311" height="199" alt="image" src="https://github.com/user-attachments/assets/87b9ef06-8111-42fc-aebf-de071968f9e0" />

## Result:
The program successfully implemented and the expected output is verified.

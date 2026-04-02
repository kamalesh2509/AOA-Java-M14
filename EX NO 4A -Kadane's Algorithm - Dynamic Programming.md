
# EX 4A Kadane's Algorithm - Dynamic Programming. 
## AIM:
To Write a Java program to solve the below problem using Kadane's Algorithm.
A solar company installs solar panels around a circular grid of n buildings. Each building either generates or consumes net energy, represented by integers (+ve for generated, -ve for consumed).

The company wants to find a contiguous sequence of buildings (possibly wrapping around from the end to the beginning) that maximizes the total net energy.

Write a program to compute the maximum net energy that can be collected from any contiguous block of buildings on the circular grid.

Input Format:
First line: Integer n (number of buildings)

Second line: n space-separated integers: net energy for each building

Output Format:
A single integer: Maximum net energy collectable from a contiguous block (wrapping allowed)

Constraints:
1 <= n <= 10^6
## Algorithm
1. Start the program and read the number of solar panels n and their energy values into an array.
2. Use Kadane’s algorithm (kadane()) to find the maximum subarray sum without wrapping around.
3. Calculate the total energy sum and use another Kadane’s algorithm (kadaneMin()) to find the minimum subarray sum.
4. Compute the maximum circular sum as totalSum - minSubarraySum and compare it with the non-circular maximum.
5. Print the greater value as the maximum solar energy that can be obtained.

## Program:
```
/*
Program to implement Reverse a String
Developed by:  KAMALESH E
Register Number: 212222100019
*/

import java.util.*;

public class SolarEnergyMaximizer {

    public static int maxCircularEnergy(int[] energy) {
        int totalSum = 0;
        int maxKadane = kadaneMax(energy); 
        int minKadane = kadaneMin(energy); 

        for (int val : energy) {
            totalSum += val;
        }

        int wraparoundMax = totalSum - minKadane;

        if (wraparoundMax == 0) 
            return maxKadane;

        return Math.max(maxKadane, wraparoundMax);
    }

    private static int kadaneMax(int[] arr) {
        int maxSoFar = arr[0], current = arr[0];
        for (int i = 1; i < arr.length; i++) {
            current = Math.max(arr[i], current + arr[i]);
            maxSoFar = Math.max(maxSoFar, current);
        }
        return maxSoFar;
    }

    private static int kadaneMin(int[] arr) {
        int minSoFar = arr[0], current = arr[0];
        for (int i = 1; i < arr.length; i++) {
            current = Math.min(arr[i], current + arr[i]);
            minSoFar = Math.min(minSoFar, current);
        }
        return minSoFar;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] energy = new int[n];
        for (int i = 0; i < n; i++) {
            energy[i] = sc.nextInt();
        }
        System.out.println(maxCircularEnergy(energy));
    }
}

```

## Output:

<img width="411" height="236" alt="image" src="https://github.com/user-attachments/assets/5ee68cc9-746e-42b0-876e-728f6621fa5a" />

## Result:
The program successfully Implemented and the output is verified. 

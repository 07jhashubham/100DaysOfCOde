<h3>You are given an array of all empty zeroes; You are given Q queries. For each query; you need to add "1" from [L,R] array; print the final array after all queries are performed.</h3>


**Given:**
- Input - Array size = 5 
- Q = 3
- arr = [[1, 4], [2, 4], [1, 3]]

**Output:**

[2, 3, 3, 2, 0]

**Diference**  **trick** 
 1. Put left side -1 = 1
 2. Put right side = -1
 3. Do the prefix sum of the array

```java
import java.util.Scanner;

class look {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter the number of pairs (n): ");
        int n = sc.nextInt();
        int[][] val = new int[n][2];
        int q = sc.nextInt();
        System.out.println("Enter the pairs (two values for each pair) it should less then n:");
        for(int i = 0; i<q; i++) {
            for(int j = 0; j<2; j++) {
                val[i][j] = sc.nextInt();
            }
        }
        System.out.println("Pairs:");
        for (int i = 0; i < n; i++) {
            System.out.println("(" + val[i][0] + ", " + val[i][1] + ")");
        }
        // Solution begain
        int[] ans = new int[n];
        for(int i = 0; i<q; i++) {
            int left = val[i][0];
            int right = val[i][1];
            ans[left-1] += 1;
            ans[right] = ans[right] -1;
        }
        for (int i = 1; i < n; i++) {
           ans[i] += ans[i-1];
        }
        System.out.println(
            "Answer of the question is: "
           );
        for (int i = 0; i < n; i++) {
           System.out.print(
            ans[i] + " "
           );
        }
    }
}

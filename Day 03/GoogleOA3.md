## Given

You are given the following:

- An array `a` consisting of `n` elements.
- Integer `k`.

For each `1 ≤ i ≤ 5k`, perform the following operation exactly one time:

- Replace `a` by `a + x`, where `x` ∈ [-k, k], which denotes `x` should lie in the range of -k and k, both inclusive.

## Task

Determine the maximum length of the subsequence of array `a` such that all numbers in that subsequence are equal after applying the given operation.

## Test Case
Applying one operation with `x = 0` on index `1` and `2` to get array a as `[1. 5,
6]`.
Applying one operation on Index 3, with `× = -1` to get array a as `[1, 5, 5]`, Therefore, the maximum length of the subsequence with equal numbers is `2`.

## Approach -> 
- Using the Difference array trick to map the values.
- Subract `k` from every `a[i]` and also add `k` to every `a[i]`.
- Map those `a[i] -k ` values as left and make it 1 in array.
- Map those `a[i] +k ` values as right+1 and make it -1 in array.
- Do the prefix sum and return the max value from the array.

  ## Solution
  ```java
  import java.util.Scanner;
  class myclass {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        long n = sc.nextLong();
        long k = sc.nextLong();
        long[] arr = new long[(int) (n+1)];
        long i = 1;
        while(i<=n) {
            arr[(int)i] = sc.nextLong();
            i++;
        }
        i = 1;
        long ans[] = new long[200005];
        while(i<=n) {
            int left = (int)(arr[(int)i] - k);
            int right = (int)(arr[(int)i] + k);

            ans[left] += 1;
            ans[right+1] -= 1;
            i++;
        }
        long answer = 1;
        i =1;
        while(i<=20000) {
            ans[(int)i] += ans[(int)(i-1)] ;
            answer = Math.max(ans[(int)i], answer);
            i++;
        }
        System.out.println(answer);
    }
  }

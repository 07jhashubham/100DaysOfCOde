<h3>You are given an array A of N integers. You have to find the number of special pairs in
array A. A pair of two indexes i and j are called special if the following 2 conditions are satisfied.</h3>
- i≤j <br>
- A[A[A[i]]] = A[A[A[j]]] <br>
<br>

  <b>Find out the number of special pairs present in array A.</b>

  <b>Note: 1-based indexing is used.</b><br><br>
  Input format for custom testing Note: Use this input format if you are testing against custom input or writing code in a
language where we don't provide boilerplate code.
• The first line contains T, which represents the number of test cases.
• For each test case:
• The first line consists of a single integer N denoting the size of the array A. • The second line consists of N space-separated integers denoting the elements of Array A.

<br> <br> 
**Given**
A-12121

**Ex Solution**
- Pair (1, 2) is special.
- Pair (1, 3) is special.
- Pair (1, 4) is special.
- Pair (2, 3) is special.
- Pair (2, 4) is special.
- Pair (3, 4) is special.

Therefore, the answer is 6.

<br>
<b>Approach -> </b> <br>
- Make a hashmap and store the a[a[a[i]]] value.<br>
- Check if that is present in the hashmap if present then add to count.<br>
- Increase the a[a[a[i]]] value in hashmap every time.

<br><br>

```java
import java.util.Scanner;
import java.util.Map;
import java.util.HashMap;
class myclass{
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n+1];

        for(int i =1; i<=n; i++) {
            arr[i] = sc.nextInt();
        }
        //Solution begain form here...
        //creating a hashmap to store all the value with it's frequency
        Map<Integer,Integer> mp = new HashMap<>();
        int count = 0;
        for(int i = 1; i<=n; i++) {
            //getting the value of 
            int RHS = arr[arr[arr[i]]];
            //checking that value
            int val = mp.getOrDefault(RHS, 0);
            //updating if that present previously
            count += val;
            //updating map
            mp.put(RHS, mp.getOrDefault(RHS, 0) +1);
        }
        System.out.println(count);
    }
}

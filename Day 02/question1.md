Question1: Given an array A consisting of N integers, returns the maximum sum of two numbers whose digits add up to an equal sum.
if there are not two numbers whose digits have an equal sum, the function should return -1.
Constraints: N is integer within the range [1, 200000]
each element of array A is an integer within the range [1, 1000000000]

 

Example1:<br>
Input:<br>
A = [51, 71, 17, 42]<br>
Output: 93<br>
Explanation: There are two pairs of numbers whose digits add up to an equal sum: (51, 42) and (17, 71), The first pair sums up to 93<br>

 

Example2:<br>
Input:<br>
A = [42, 33, 60]<br>
Output: 102<br>
Explanation: The digits of all numbers in A add up the same sum, and choosing to add 42 and 60 gives the result 102<br>


- ✅ Approach ->
1. Make a hashmap and store the digitSum and its value.
2. If the digitSum is occur then make sum and max it.

```java
class Solution {
    public int digitCount(int n) {
        int ans = 0;
        while(n!=0){
            ans = ans+n%10;
            n = n/10;
        }
        return ans;
    }
    public int maximumSum(int[] nums) {
        int answer =-1;
        Map<Integer,Integer> map = new HashMap<>();
        for(int i =0; i<nums.length; i++) {
            int n = nums[i];
            if(map.containsKey(digitCount(n))) {
                int sum = nums[i] + map.get(digitCount(n));
                answer = Math.max(answer, sum);
                int k = Math.max(nums[i], map.get(digitCount(n)));
                map.put(digitCount(n), k);
            }
            else{
                map.put(digitCount(n), n);
            }
        }
        return answer;
    }
}

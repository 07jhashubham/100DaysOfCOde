Amazon Engineering maintains a large number of logs of operations across all products. A software engineer is debugging an issue in a product. An efficient way to analyze logs is to write automated scripts to check for patterns. The engineer wants to find the maximum number of times a target word can be obtained by rearranging a subset of characters in a log entry.

Given a log entry s and target word t, the target word can be obtained by selecting some subset of characters from s that can be rearranged to form string t and removing them from s. Determine the maximum number of times the target word can be removed from the given log entry.
Note: Both strings s and t consist only of lowercase English letters.


Example <br>
S = "mononom" <br>
t="mon" <br>
Output = 2 <br>

- ✅ Approach -> <br> 
  1. Make two Hashmaps and map both s and t with its frequency
  2. Run a loop for t and store the ratio of s freq of that number by t freq of that number
  3. Take a minimum from that stored value in ans and return the ans.

```java
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s = scanner.next();
        String t = scanner.next();
 
        Map<Character, Integer> freq_s = new HashMap<>();
        Map<Character, Integer> freq_t = new HashMap<>();
 
        for (char letter : s.toCharArray()) {
            freq_s.put(letter, freq_s.getOrDefault(letter, 0) + 1);
        }
        for (char letter : t.toCharArray()) {
            freq_t.put(letter, freq_t.getOrDefault(letter, 0) + 1);
        }
 
        int ans = Integer.MAX_VALUE;
 
        for (char letter : t.toCharArray()) {
            ans = Math.min(freq_s.getOrDefault(letter, 0) / freq_t.getOrDefault(letter, 0), ans);
        }
 
        System.out.println(ans);
    }
}

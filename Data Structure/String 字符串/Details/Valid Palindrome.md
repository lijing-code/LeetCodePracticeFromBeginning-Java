# Given a string, determine if it is a palindrome, only letters and numbers are considered and case is ignored

<p></p>

<p></p>

### Example 1

```
Input: "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama"
```
### Example 2
```
Input: "race a car"
Output: false
Explanation: "raceacar"
```
### Example 3
```
输入: "1b , 1"
输出: true
解释: "1b1"
```
### Method 1 : Two Pointers
<p>---</p>

```
public class Solution {
    public boolean isPalindrome(String s) {
        if (s == null || s.length() == 0) {
            return false;
        }
        s = s.toLowerCase().replace(" ", "");
        System.out.println(s);
        int n = s.length();
        int i = 0;
        int j = s.length() - 1;
        while (i < j){
            if (!Character.isLetterOrDigit(s.charAt(i))){
                i++;
                continue;
            }
            if (!Character.isLetterOrDigit(s.charAt(j))){
                j--;
                continue;
            }
            if (s.charAt(i) != s.charAt(j)){
                return false;
            }
            i++;
            j--;
        }
        return true;
    }
}

```
#### Time O(n); 
#### Space O(n); 

<br>


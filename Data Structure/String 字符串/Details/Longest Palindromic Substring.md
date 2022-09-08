# Given a string s, return the longest palindromic substring in s.

### Example 1

```
Input: s = "babad"
Output: "bab"
Explanation: "aba" is also a valid answer.
```
### Example 2
```
Input: s = "cbbd"
Output: "bb"
```
### Constraints
```
1 <= s.length <= 1000
s consist of only digits and English letters.
```
### Method 1 : Brute Force 
<p>Leetcode超时了</p>

```
class Solution {
    public String longestPalindrome(String s) {
//     edge case
        if (s == null || s.length() == 0) {
            return "";
        }
        if (s.length() == 1){
            return s;
        }
        StringBuilder ans = new StringBuilder();
        for (int i = 0; i < s.length(); i++) {
            int j = s.length() - 1;
            while (i < j) {
                if (s.charAt(i) == s.charAt(j) && isPalindrome(s.substring(i, j+1))){
                    if (s.substring(i, j+1).length() > ans.length()) {
                        ans.setLength(0);
                        ans.append(s.substring(i, j+1));
                    }
                }
                j--;
            }
        }
        if (ans.length() != 0){
            return ans.toString();
        }
        return Character.toString(s.charAt(0));
    }
    private boolean isPalindrome(String str) {
        if (str.length() == 1) {
            return true;
        }
        int l = 0;
        int r = str.length() - 1;
        while (l < r) {
            if (str.charAt(l) != str.charAt(r)){
                return false;
            }
            l++;
            r--;
        }
        return true;
    }
}

```
#### Time O(n²); 
#### Space O(n); 

<br>

## Follow-up: 

### Method 2 : 
<p>-</p>

```
-

```
#### Time O(n); 
#### Space O(n); 

### Method 3 : 
<p>-</p>

```
-
```

#### Time O(n); 
#### Space O(n); 

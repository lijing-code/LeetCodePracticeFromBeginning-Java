# You are given a string s. You can convert s to a palindrome by adding characters in front of it.


<p>Return the shortest palindrome you can find by performing this transformation.</p>

<p></p>

### Example 1

```
Input: s = "aacecaaa"
Output: "aaacecaaa"
```
### Example 2
```
Input: s = "abcd"
Output: "dcbabcd"
```
### Constraints
```
0 <= s.length <= 5 * 104;
s consists of lowercase English letters only.
```
### Method 1 : Brute Force 
<p>思路： 从后往前判断，如果当前位置之前的substring不是palindrome，则往前走</p>
<p>如果当前位置之前的substring是palindrom，则把当前位置走过的substring整个翻转加到原string左侧则可组成最小palindrom</p>
<p>下面思路是对的，但是在Leetcode上超时了，最差情况每一个字母都走了一次 isPalindrome func操作</p>

```
class Solution {
    public String shortestPalindrome(String s) {
        if (s == null || s.length() == 0) {
            return "";
        }
        
        if (isPalindrome(s)) return s;
        
        int i = s.length() - 1;
        while (i > 0) {
            if (isPalindrome(s.substring(0, i))){
                String sb = new StringBuilder(s.substring(i)).reverse().toString();
                String ans = sb + s;
                return ans;
            }
            i--;
        }
        return "";
    }
    
    private boolean isPalindrome(String str) {
        if (str.length() == 1) {
            return true;
        }
        int l = 0;
        int r = str.length() - 1;
        while (l < r) {
            if(str.charAt(l) != str.charAt(r)){
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

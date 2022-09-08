# Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.

<p>Letters are case sensitive, for example, "Aa" is not considered a palindrome here.</p>

<p></p>

### Example 1

```
Input: s = "abccccdd"
Output: 7
Explanation: One longest palindrome that can be built is "dccaccd", whose length is 7.
```
### Example 2
```
Input: s = "a"
Output: 1
Explanation: The longest palindrome that can be built is "a", whose length is 1.

```

### Method 1 : HashMap
<p>edge case String里要有内容</p>
<p>用每个char作为key，出现次数作为value</p>
<p>遍历这个str</p>
<p>如果table里没有当前key，或者这个key对应的value为0，则加入key，并且value为1</p>
<p>如果table里有个这个key，则调出其value（一定为1）</p>
<p>把ans里加2，因为有一对可以组成palindrom，并且把value重新设为0</p>
<p>最后，找出str里的char的对数*2为ans，再判断ans如果小于str的长度则 ans + 1，因为这样才是最长的palindrome，并且包括如果str只有一个char的情况</p>

```
class Solution {
    public int longestPalindrome(String s) {
        int ans = 0;
        if (s == null || s.length() == 0) {
            return 0;
        }
        
        HashMap<Character, Integer> map = new HashMap<>();
        
        for (int i = 0; i < s.length(); i++) {
            
            if (!map.containsKey(s.charAt(i))|| map.get(s.charAt(i)) == 0){
                map.put(s.charAt(i), 1);
            } else if (map.get(s.charAt(i)) == 1) {
                ans = ans + 2;
                map.put(s.charAt(i), 0);
            } 
        }
        if (ans < s.length()){
            ans = ans + 1;
        }
        return ans ;
    }
}

```
#### Time O(n); 便利了一次str，并且hashmap是O(1),整体是O(n) 
#### Space O(n); 整个str的长度

<br>

## Follow-up: Space 可能为 O(1)???

### Method 2 : 贪心算法
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

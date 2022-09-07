# For a given source string and a target string, you should output the first index(from 0) of target string in the source string.If the target does not exist in source, just return -1.

<p></p>

<p></p>

### Example 1

```
Input:
source = "source"
target = "target"
Output:
-1
If the source does not contain the target's content, return - 1.
```
### Example 2
```
Input:
source = "abcdabcdefg"
target = "bcd"
Output:
1
If the source contains the target's content, return the location where the target first appeared in the source.
```

### Method 1 : Brute Force
<p>计算两个string的长度，如果target比source长则一定返回-1</p>
<p>如果两个str都是null，则返回0</p>
<p>loop两个string，但是source只要走到n-m+1即可，因为后面剩的长度小于target了，一定没有答案了</p>
<p>用一个k来储存当前source走到的source的位置，用k和target的index去比，这样可以保留i</p>
<p>出口就是target的最后一个char和source还能对得上，就证明source里面含target</p>

```
class Solution {     
    public int strStr(String source, String target) {
        // edge case
        int n = source.length();
        int m = target.length();
        if (m > n) return -1;
        if((source == null || n == 0) && (target == null || m == 0)) return 0;
        if (target == null || m == 0) return 0;

        for (int i = 0; i < n - m + 1; i++) {
            int k = i;
            if (source.charAt(k) == target.charAt(0)){
                for (int j = 0; j < m; j++) {
                    if (source.charAt(k) == target.charAt(j)){
                        k++;
                    } else {
                        break;
                    }  
                    <!-- 注意这里k的位置 -->
                    if (k-1-i == m-1 && source.charAt(k-1) == target.charAt(m-1)) {
                        return i;
                    }
                } 
            }
        }
        return -1;  
    }
}

```
#### Time O(m*n);最差的情况就是把m和n都走遍了也没有答案 
#### Space O(n); 空间上用了O(m+n);

<br>

## Follow-up: 

### Method 2 : KMP Knuth-Morris-Pratt算法
<p> https://www.zhihu.com/question/21923021/answer/281346746</p>

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

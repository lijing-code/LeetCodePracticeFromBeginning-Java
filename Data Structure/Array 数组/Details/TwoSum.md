# Given an array of integers ```nums``` and an integer ```target```, return indices of the two numbers such that they add up to target.

<p>You may assume that each input would have exactly one solution, and you may not use the same element twice.</p>

<p>You can return the answer in any order.</p>

### Example 1

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```
### Example 2
```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```
### Example 3
```
Input: nums = [3,3], target = 6
Output: [0,1]
```
### Method 1 : brute force
<p>建立两个for循环，把每个组合都试一下，找出最终答案</p>

```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] ans = new int[2];
        for (int i = 0; i < nums.length; i++) {
            int secondElementValue = target - nums[i];
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[j] == secondElementValue) {
                    ans[0] = i;
                    ans[1] = j;
                }
            }
        }
        return ans;
        
    }
}

```
#### Time O(n²); 两个for loop
#### Space O(1); 

<br>

## Follow-up: Can you come up with an algorithm that is less than O(n²) time complexity?

### Method 2 : HashMap (:+1:Recommend)
<p>Build an empty hashmap, iterate nums.</p>
<p>key is nums[i], value is the index.</p>
<p>If the current number couldn't find a couple to add equal to the target, put the current number in hashmap.</p>
<p>If hasmap contains a key can satisfy the condition with the current number, then the value is the first element in answer, the current number's index in nums is the second element in ans. </p>

```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] ans = new int[2];
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(target - nums[i])) {
                ans[0] = map.get(target - nums[i]);
                ans[1] = i;
                return ans;
            }
            map.put(nums[i], i);
        }
        return ans;
        
    }
}

```
#### Time O(n); 只loop了一次, n为数组的大小
#### Space O(n); 创建了一个空的map，加上原来的nums空间，约等于O(n)，n为数组的大小

### Method 3 : Two Pointers
<p>Create a hashmap to save the index and the value in nums.</p>
<p>Sort nums in ascending order. from small to big.</p>
<p>Two pointer, one from beginning (left pointer), one from the last(right pointer).</p>
<p>If sorted nums[left] + sorted nums[right] > target, move right pointer.</p>
<p>If sorted nums[left] + sorted nums[right] < target, move left pointer.</p>
<p>End: left value + right value = target</p>

```
public class Solution {
    <!-- declare a data structor called Pair which consist of value and index -->
    class Pair {
         Integer value;
         Integer index;
         
         <!-- Constructor -->
         Pair(Integer value, Integer index) {
            this.value = value;
            this.index = index;
         }
    }

    <!-- declare a new class which implements the Comparator, in this class, I override the compare function.  -->
    <!-- Comparator 是 java的一个内置interface，要创建自己的class实现这个interface，并调用（override)其中的compare方法在自己造的class里使用 -->
     class ValueComparator implements Comparator<Pair> {    
    
        @Override    
        public int compare(Pair o1, Pair o2) {    
            return o1.value().compareTo(o2.value());      
        }
     }
    public int[] twoSum(int[] numbers, int target) {
        // write your code here
        //用一个pair数组记录每个numbers[i]的值和它的位置i，防止排序后不知道该元素的位置
        Pair[] pairs = new Pair[numbers.length];
        for(int i=0;i<numbers.length;i++) {
            pairs[i] = new Pair(numbers[i], i);
        }
        //排序,把pairs按valueComparator方法实现value从小到大排序
        Arrays.sort(pairs, new ValueComparator());
        int L= 0, R =  numbers.length-1;
        while(L<R) {
            if( number[L].value() + number[R].value() == target) {
                int t1 = number[L].index;
                int t2 = number[R].index;
                int[] result = {Math.min(t1,t2), Math.max(t1,t2)};
                return result;
            }
            if( number[L].value() + number[R].value() < target) {
                L++;
            } else {
                R--;
            }
        }
        int[] res = {};
        return res;
    }
}
```

#### Time O(nlogn); 两个指针只走了一次，n为数组大小. nlogn是quick sort的理想时间复杂度
#### Space O(n); 创建了一个空的map，加上原来的nums空间，约等于O(n)，n为数组的大小
#### notes：quick sort是把给出的无序序列以一个pivot为基准的快速排成有序序列，本质是tree，把给出的序列按pivot一分为二，并以分开的两部分继续向下分解，直到最后找出答案。所以logN是average子节点数，N是Tree的层数，因此快速排序正常遍历一遍的情况下时间复杂度是N*logN， worst case是n²

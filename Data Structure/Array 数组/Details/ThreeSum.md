# Given an integer array nums, return all the triplets ```[nums[i], nums[j], nums[k]]``` such that i != j, i != k, and j != k, and ```nums[i] + nums[j] + nums[k] == 0```.


<p>Notice that the solution set must not contain duplicate triplets.
</p>

<p></p>

### Example 1

```
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
```
### Example 2
```
Input: nums = [0,1,1]
Output: []
Explanation: The only possible triplet does not sum up to 0.
```
### Example 3
```
Input: nums = [0,0,0]
Output: [[0,0,0]]
Explanation: The only possible triplet sums up to 0.
```

### Method 1 : HashTable (:+1:Recommend)
<p>-</p>

```
-
```

#### Time O(n); 
#### Space O(n);


### Method 2 : Two Pointers (:+1:Recommend)
<p>---</p>

```
public List<List<Integer>> threeSum(int[] numbers) {
             <!-- edge cases   -->
        if (nums == null || nums.length < 3){
            return ans;
        }
        Arrays.sort(numbers);
        
        
        List<List<Integer>> results = new ArrayList();
        <!-- 因为nums是递增排序，如果两个相邻位置的值一样，则走过第一个得出答案就不需要走第二个了，因为答案会是一样的，这一步可以去重 -->
        for (int i = 0; i < numbers.length; i++) {
            if (i != 0 && numbers[i] == numbers[i - 1]) {
               continue;
            }
            findTwoSum(numbers, i, results);
        }
        
        return results;
    }
    
    private void findTwoSum(int[] nums, int index, List<List<Integer>> results) {
        int left = index + 1, right = nums.length - 1;
        int target = -nums[index];
        
        while (left < right) {
            int twoSum = nums[left] + nums[right];
            if (twoSum < target) {
                left++;
            } else if (twoSum > target) {
                right--;
            } else {
                 <!-- 找到了答案 -->
                List<Integer> triple = new ArrayList();
                triple.add(nums[index]);
                triple.add(nums[left]);
                triple.add(nums[right]);
                results.add(triple);
                left++;
                right--;
                <!-- 得到结果后，从后面去重，因为如果r和r-1上的数字值相同就没有必要再走一遍 -->
                while (left < right && nums[left] == nums[left - 1]) {
                    left++;
                }
            }
        }
    }
}

```
#### Time O(n²); TwoSum is O(n), and we call it n times; Sort Array is O(nlogn); O(n²) + O(nlogn) = O(n²)
#### Space O(n); from \mathcal{O}(\log{n})O(logn) to \mathcal{O}(n)O(n), depending on the implementation of the sorting algorithm. For the purpose of complexity analysis, we ignore the memory required for the output.？？？？啥意思



<br>

### Method 3 : Brute Force 容易超时
<p>三重循环，先sort Array，然后让 int i < int j < int k 找出所有可能性</p>
<p>然后把答案找出，再排序，再存入Hashset去重</p>

#### Time n^(3); 
#### Space O(n²); 前两个loop走完第三个数字就是确定的了，再去重，就只需要n*n的空间就够了

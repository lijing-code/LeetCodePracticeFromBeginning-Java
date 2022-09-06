<p>Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.</p>

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
#### Space O(n); 空间没有增加，还是原nums空间

<br>

### Follow-up: Can you come up with an algorithm that is less than O(n²) time complexity?

### Method 2 : HashMap (** Recommend **)
<p>HashMap </p>

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
#### Time O(n); 
#### Space O(n);


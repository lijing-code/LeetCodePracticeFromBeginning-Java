# Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

<p>The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.You must write an algorithm that runs in O(n) time and without using the division operation.
</p>

### Constraints
```
2 <= nums.length <= 105
-30 <= nums[i] <= 30
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.
```

## Follow-up: Can you solve the problem in O(1) extra space complexity? (The output array does not count as extra space for space complexity analysis.)

### Example 1

```
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```
### Example 2
```
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```

### Method 1 : 
<p>用目标数字左面的乘积*目标数字右面的乘积即为res。一直更新左面和右面的乘积值则可求出res上的数值。左右两边初始值都为1，先更新左边的乘积和res array，再更新右边乘积和res array。注意右边的边界是大于等于0</p>

```
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int[] res = new int[nums.length];
        int preProduct = 1 , postProduct = 1;
        for (int i = 0; i < res.length; i++) {
            if (i == 0) {
                res[i] = preProduct;
            } else {
                res[i] = nums[i-1] * preProduct;
                preProduct = res[i];
            }
        }
        for (int j = res.length - 1; j >= 0; j--) {
            if (j == res.length - 1) {
                res[j] *= postProduct;
            } else {
                res[j] *= nums[j + 1] * postProduct;
                postProduct = nums[j + 1] * postProduct;
            }
        }
        return res;
    }
}

```
#### Time O(n); Loop了两遍，2*n，简化为O(n)
#### Space O(1); 只开了一个空间for preProduct, 和 postProduct

```java
public class Solution {
    public void nextPermutation(int[] nums) {
        if(nums == null || nums.length <= 1)
            return;
        
        int i = nums.length - 1;
        while(i > 0 && nums[i - 1] >= nums[i])
            i--;
        if(i == 0) {
            reverse(nums, 0, nums.length - 1);
            return;
        }
        
        int j = nums.length - 1;
        while(j >= i && nums[j] <= nums[i - 1])
            j--;
        
        
        int temp = nums[j];
        nums[j] = nums[i - 1];
        nums[i - 1] = temp;
        
        reverse(nums, i, nums.length - 1);
    }
    
    private void reverse(int[] nums, int begin, int end) {
        int lo = begin, hi = end;
        while(lo < hi) {
            int temp = nums[lo];
            nums[lo] = nums[hi];
            nums[hi] = temp;
            lo ++;
            hi --;
        }
    }
}
```

```java
public class Solution {
    public int search(int[] nums, int target) {
        if(nums == null || nums.length < 1)
            return -1;
        int pivot = 0;
        while(pivot < nums.length - 1 && nums[pivot] < nums[pivot + 1])
            pivot ++;
        if(pivot == nums.length - 1)
            return bisearch(nums, 0, pivot, target);
        
        if(nums[nums.length - 1] < target)
            return bisearch(nums, 0, pivot, target);
        else if(nums[0] > target)
            return bisearch(nums, pivot + 1, nums.length - 1, target);
        else
            return -1;
        
    }
    private int bisearch(int[] nums, int begin, int end, int target) {
        int lo = begin, hi = end;
        if(begin == end) {
            if(nums[begin] == target)
                return begin;
            else
                return -1;
        }
        
        while(lo <= hi) {
            int mid = (lo + hi) / 2;
            if(nums[mid] == target)
                return mid;
            else if(nums[mid] > target)
                hi = mid - 1;
            else
                lo = mid + 1;
        }
        return -1;
    }
}
```

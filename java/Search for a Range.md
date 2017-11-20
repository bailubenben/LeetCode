```java
public class Solution {
    public int[] searchRange(int[] nums, int target) {
        if(nums == null || nums.length < 1)
            return new int[] {-1,-1};
        int lo = 0, hi = nums.length;
        int[] range = new int[2];
       
        range[0] = nums.length;
        range[1] = -1;
        
        int index = bisearch(nums, 0, nums.length - 1, target);
        if(index == -1)
            return new int[] {-1, -1};
        else {
            if(range[0] > index)
                range[0] = index;
            if(range[1] < index) 
                range[1] = index;
        }
        while(range[0] > 0) {
            index = bisearch(nums, 0, range[0] - 1, target);
            if(index != -1)
                range[0] = index;
            else
                break;
        }
        while(range[1] < nums.length - 1) {
            index = bisearch(nums, range[1] + 1, nums.length - 1, target);
            if(index != -1)
                range[1] = index;
            else
                break;
        }
        return range;
    }
    
    private int bisearch(int[] nums, int begin, int end, int target) {
        if(begin == end) {
            if(nums[begin] == target)
                return begin;
            else
                return -1;
        }
        int lo = begin, hi = end;
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

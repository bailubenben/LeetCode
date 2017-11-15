```java
public class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        if(nums == null || nums.length < 3)
            return new LinkedList<>();

        Arrays.sort(nums);       
        List<List<Integer>> res = new LinkedList<>();
        
        if(nums[0] > 0 || nums[nums.length - 1] < 0)
            return res;
        
        for(int i = 0; i < nums.length - 2; i ++) {
            if(i == 0 || (i > 0 && nums[i] != nums[i - 1])) {
                int lo = i + 1, hi = nums.length - 1, sum = -nums[i];
                while(lo < hi) {
                    if(nums[lo] + nums[hi] == sum) {
                        res.add(Arrays.asList(nums[i], nums[lo], nums[hi]));
                        lo ++;
                        hi --;
                        while(lo < hi && nums[lo] == nums[lo - 1])
                            lo ++;
                        while(lo < hi && nums[hi] == nums[hi + 1])
                            hi --;
                    }
                    else if ( nums[lo] + nums[hi] > sum) {
                        //while(lo < hi && nums[hi] == nums[hi + 1])
                            hi --;
                    }
                    else {
                        //while(lo < hi && nums[lo] == nums[lo - 1])
                            lo ++;
                    }
                }
            }
        }
        return res;
    }
}
```

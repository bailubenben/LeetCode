```java
public class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        List<List<Integer>> res = new LinkedList<List<Integer>>();
        if(nums == null || nums.length < 4)
            return res;
        Arrays.sort(nums);
        if(4 * nums[0] > target || 4 * nums[nums.length - 1] < target)
            return res;
        for(int i = 0; i < nums.length - 3; i++) {
            if(i == 0 || i > 0 && nums[i] != nums[i - 1]) {
                for(int j = i + 1; j < nums.length -2; j++) {
                    int lo = j + 1, hi = nums.length - 1;
                    int sum = target - nums[i] - nums[j];
                    if(j == i + 1 || (j > 1 && nums[j] != nums[j - 1])) {
                        while(lo < hi) {
                            if(nums[lo] + nums[hi] == sum) {
                                res.add(Arrays.asList(nums[i], nums[j], nums[lo], nums[hi]));
                                lo ++;
                                hi --;
                                while(lo < hi && nums[lo] == nums[lo - 1])
                                    lo++;
                                while(lo < hi && nums[hi] == nums[hi + 1])
                                    hi--;
                            }
                        else if(nums[lo] + nums[hi] < sum)
                            lo ++;
                        else
                            hi--;
                        
                        }
                    }
                
                }
            }
        }
        return res;
    }
}
```

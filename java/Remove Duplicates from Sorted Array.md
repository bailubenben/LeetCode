```java
public class Solution {
    public int removeDuplicates(int[] nums) {
        if(nums == null || nums.length == 0)
            return 0;
        int newlen = 0;
        for(int i = 0; i < nums.length; i++) {
            if(i > 0 && nums[i] == nums[i - 1])
                continue;
            nums[newlen] = nums[i];
            newlen ++;
        
        }
        return newlen;
    }
}
```

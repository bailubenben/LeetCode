```java
public class Solution {
	public int maxArea(int[] height) {
       int len = height.length;
       if(len < 2)
           return 0;
       int temphigh = 0;
       int tempmax = 0;
       int left = 0;
       int right = len - 1;
       while (left < right) {
           temphigh = height[left] > height[right] ? height[right] : height[left];
           tempmax = tempmax > temphigh * (right - left) ? tempmax : temphigh * (right - left);
           if(height[left] < height[right]) 
               left++;
           else
               right--;
       }
        
      
       return tempmax;
   }
}
```

## solution1
```python 
class Solution:
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        if not nums or len(nums) < 1:
            return -1
        size = len(nums)
        pivot = -1
        for i in range(size - 1):
            if nums[i] > nums[i + 1]:
                pivot = i
                break

        left = self.biSearch(nums, 0, pivot, target)
        if left != -1:
            return left
        return self.biSearch(nums, pivot + 1, size - 1, target)
        
    def biSearch(self, nums, start, end, target):
        lo, hi = start, end
        while lo <= hi:
            mid = (lo + hi) // 2
            if nums[mid] == target:
                return mid
            elif nums[mid] > target:
                hi = mid - 1
            else:
                lo = mid + 1
        return -1
```

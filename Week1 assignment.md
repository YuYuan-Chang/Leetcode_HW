### Week 1: Problem Assignments

1. [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) 

```
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        d = {}
        for i in nums:
            if i not in d:
                d[i] = 1
            else:
                d[i] = d[i] + 1
        print(d)
        for i in d.keys():
            if d[i] >= 2:
                return True
            elif d[i] != 1:
                return False
```

2. [Long Pressed Name](https://leetcode.com/problems/container-with-most-water/description/)

```
class Solution:
    def maxArea(self, height: List[int]) -> int:
        max_result = 0
        left, right = 0, len(height) - 1
        while left < right:
            area = min(height[left], height[right]) * (right - left)
            if area > max_result:
                max_result = area
            if height[left] < height[right]:
                left = left + 1
            else:
                right = right - 1
        return max_result
```

3. [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/description/) (Easy)

```
from sortedcontainers import SortedList

class Solution:
	def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:

		window = SortedList(nums[:k])

		result = [0] * (len(nums) - k +1)
		result[0] = window[-1]

		for index in range(k,len(nums)):

			window.remove(nums[index - k])
			window.add(nums[index])
			result[index - k + 1] = window[-1]

		return result
```


### question number 56. merge intervals.

Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

example:
```bash
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].
```

initial thought process:

1. we can check the last indices of the one element with the first indices of the second element. 
2. if i[0][1] >  i[1][0], we can merge them to a common group. 
3. this is a brute force approach and complexity of O(n^2) i guess?

solution notes:

apparently answer becomes clear once you check out the video solution from youtube. jokes apart, the idea is still the same, but before comparison we just have to sort the list with the start of each interval so that we only have to interate through only once ! the time complexity is sweet O(nlogn).

code:

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        
        intervals.sort(key = lambda i : i[0])
        output = [intervals[0]]

        for start, end in intervals[1:]:
            lastEnd = output[-1][1]

            if start <= lastEnd:
                output[-1][1] = max(lastEnd, end)
            else:
                output.append([start, end])
        
        return output 
```
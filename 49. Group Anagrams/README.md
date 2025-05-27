### question number 49. group anagrams.

given an array of strings strs, group the _anagrams_ together. you can return the answer in any order.

example:
```bash
Input: strs = ["eat","tea","tan","ate","nat","bat"]

Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```
initial thought process:

1. we can use a dictionary/hashmap. 
2. make three unquie dictionary somehow and then check each element.
3. then group it. 
4. but can lead to high time complexity, probable O(n^2)

solution notes:

looking at the solution, i was partially correct. however, the solution is to make the key value pair where keys are the elements in the strings, and values are the strings which have that element in them. the total time complexity here becomes O (m * n * 26) or O (m * n). 

also, lists cannot be keys in python. use defaultdict for the edge case where count doesn't initially exist.  

repeating again what i understood, we are creating an array of 26 0s, and add +1 to the index. techncially "tan" and "nat" will have same count value but different value from "ate". this way we can group those similar strings into common list. 

code:

```python
from collections import defaultdict
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        res = defaultdict(list)
        for s in strs:
            count = [0] * 26
            for c in s:
                count[ord(c)-ord('a')] +=1
            
            res[tuple(count)].append(s)
        return list(res.values())
```


 





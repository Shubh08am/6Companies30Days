# Perfect Rectangle

->[Problem Link](https://leetcode.com/problems/perfect-rectangle/)

 Given an array rectangles where rectangles[i] = [xi, yi, ai, bi] represents an axis-aligned rectangle.
 
 The bottom-left point of the rectangle is (xi, yi) and the top-right point of it is (ai, bi).

Return true if all the rectangles together form an exact cover of a rectangular region.
### Sample Input
```
rectangles = [[1,1,3,3],[3,1,4,2],[3,2,4,4],[1,3,2,4],[2,3,3,4]]
rectangles = [[1,1,2,3],[1,3,2,4],[3,1,4,2],[3,2,4,4]]
```
### Sample Output
```
true
false
```

### Solution
```cpp
class Solution {
public:
//how to observe like this :(
    bool isRectangleCover(vector<vector<int>>& rectangles) {
        map<pair<int, int>, int> m;
        int ans=0;
        for(auto it:rectangles){
            m[{it[0], it[1]}]++;
            m[{it[0], it[3]}]--;
            m[{it[2], it[1]}]--;
            m[{it[2], it[3]}]++;
        }

   for(auto it : m){ 
            if(it.second!=0){
                if(abs(it.second)!=1) return false;
                ans++;
            }
   }

        return ans==4;
    }
};
```

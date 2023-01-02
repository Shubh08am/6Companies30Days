# Airplane Seat Assignment Probability

->[Problem Link](https://leetcode.com/problems/airplane-seat-assignment-probability/)

 n passengers board an airplane with exactly n seats. The first passenger has lost the ticket and picks a seat randomly. But after that, the rest of the passengers will:

•Take their own seat if it is still available, and

•Pick other seats randomly when they find their seat occupied

Return the probability that the nth person gets his own seat.

### Sample Input
```
n = 1
n = 2
```
### Sample Output
```
1.00000
0.50000
```

### Solution
```cpp
class Solution {
public:
    double nthPersonGetsNthSeat(int n) {
        if(n==1) return 1;
        //nth person will be having 2 ways only - to get his seat or to take some one others seat
        return 1/2.0;
    }
};
```

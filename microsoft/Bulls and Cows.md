# Bulls and Cows

->[Problem Link](https://leetcode.com/problems/bulls-and-cows/)

You are playing the Bulls and Cows game with your friend.

You write down a secret number and ask your friend to guess what the number is. When your friend makes a guess, you provide a hint with the following info:

•The number of "bulls", which are digits in the guess that are in the correct position.

•The number of "cows", which are digits in the guess that are in your secret number but are located in the wrong position. Specifically, the non-bull digits in the guess that could be rearranged such that they become bulls.

•Given the secret number secret and your friend's guess guess, return the hint for your friend's guess.

The hint should be formatted as "xAyB", where x is the number of bulls and y is the number of cows. Note that both secret and guess may contain duplicate digits.


### Sample Input
```
secret = "1807", guess = "7810"
```
### Sample Output
```
"1A3B"
```

### Solution
```cpp
class Solution {
public:
    string getHint(string secret, string guess) {
        //bulls = correct pos of digits in secret and guess 
        //cows = no. of digits in wrong pos of guess in secret
        /*
        1123 -- 0111
        1A23 -- 0A11   bull=1
        AA23 -- 0AA1   cow=1
 
        1807-- 7810
        1A07 -- 7A10   bull=1
        AA07 -- 7AA0   cow=1
        AAA7 -- 7AAA   cow=2
        AAAA -- AAAA   cow=3
        
        */
        int n = secret.size();
        string ans = "";
        int cow=0,bull=0;
        for(int i=0;i<n;i++) {
            if(secret[i]==guess[i]) {bull++; guess[i]='A';secret[i]='A';}
        }
        ans+=(to_string(bull));
        ans+='A';
       
       for(int i=0;i<n;i++){
           for(int j=0;j<n;j++){
               if(secret[i]==guess[j] and i!=j and guess[j]!='A' ){
                  cow++;guess[j]='A';secret[i]='A';
               }
           }
       }
        ans+=(to_string(cow));
        ans+='B';

        return ans;
    }
};
```

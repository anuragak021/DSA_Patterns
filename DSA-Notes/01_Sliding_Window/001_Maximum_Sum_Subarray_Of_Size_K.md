# Maximum Sum Subarray Of Size K

### ### Problem [Link](https://www.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1)

## Problem Statement
Given an array of integers arr[]  and a number k. Return the maximum sum of a subarray of size k.

Note: A subarray is a contiguous part of any given array.

Constraints:
1 ≤ arr.size() ≤ 10^6 <br>
1 ≤ arr[i] ≤ 10^6 <br>
1 ≤ k ≤ arr.size()

### example test cases

Input: arr[] = [100, 200, 300, 400], k = 2 <br>
Output: 700 <br>
Explanation: arr2 + arr3 = 700, which is maximum. <br>
Input: arr[] = [1, 4, 2, 10, 23, 3, 1, 0, 20], k = 4 <br>
Output: 39 <br>
Explanation: arr1 + arr2 + arr3 + arr4 = 39, which is maximum. <br>
Input: arr[] = [100, 200, 300, 400], k = 1
Output: 400<br>
Explanation: arr3 = 400, which is maximum. 

---
## 💡 Approaches
Sliding window approach
### 📌 Best Approach 

The Best approach is to take a sliding window , have two variables i and j , initialize both of them to 0. Then take sum = 0 and maxi = INT_MIN , add the sum of arr[j] to sum and compare the maximum when the window size reaches k , then when it reaches k , subtract the arr[i] from sum , then return maxi.

#### Code (C++)
```cpp
class Solution {
  public:
    int maxSubarraySum(vector<int>& arr, int k) {
        // code here
        int i = 0 , j =  0 ;
        int sum = 0 ;
        int maxi = INT_MIN;
        while(j < arr.size()){
            sum += arr[j];
            if(j - i + 1 < k){
                j++;
            }
            else if(j - i + 1 == k){
                maxi = max(sum , maxi);
                sum -= arr[i];
                j++;
                i++;
            }
        }
        return maxi;
    }
};
```
#### TC and SC
- **Time Complexity:** O(N)
- **Space Complexity:** O(1)

---

## 📝 Notes

This is a sliding window approach.

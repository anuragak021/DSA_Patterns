# Maximum Sum of Distinct Subarrays with length k

### ### Problem [Link](https://leetcode.com/problems/maximum-sum-of-distinct-subarrays-with-length-k/description/)

## Problem Statement

You are given an integer array nums and an integer k. Find the maximum subarray sum of all the subarrays of nums that meet the following conditions:

The length of the subarray is k, and
All the elements of the subarray are distinct.
Return the maximum subarray sum of all the subarrays that meet the conditions. If no subarray meets the conditions, return 0.

A subarray is a contiguous non-empty sequence of elements within an array.

### example test cases
Example 1:

Input: nums = [1,5,4,2,9,9,9], k = 3
Output: 15
Explanation: The subarrays of nums with length 3 are:
- [1,5,4] which meets the requirements and has a sum of 10.
- [5,4,2] which meets the requirements and has a sum of 11.
- [4,2,9] which meets the requirements and has a sum of 15.
- [2,9,9] which does not meet the requirements because the element 9 is repeated.
- [9,9,9] which does not meet the requirements because the element 9 is repeated.
We return 15 because it is the maximum subarray sum of all the subarrays that meet the conditions
Example 2:

Input: nums = [4,4,4], k = 3
Output: 0
Explanation: The subarrays of nums with length 3 are:
- [4,4,4] which does not meet the requirements because the element 4 is repeated.
We return 0 because no subarrays meet the conditions.
 

Constraints:

1 <= k <= nums.length <= 105
1 <= nums[i] <= 105

---
## 💡 Approaches

### 📌 Best Approach 
The approach is to take a set , put elements in the set and check whether it is repeating or not , then after that check whether j - i + 1 == k or not if that is equal then output give the maximum
#### Code (C++)
```cpp

class Solution {
public:
    long long maximumSubarraySum(vector<int>& nums, int k) {
        int n = nums.size();
        long long result = 0 ;
        long long currWindowSum = 0 ;
        unordered_set<int> st;
        int i = 0 ;
        int j = 0 ;
        while(j < n){
            // check if nums[j] is already present in current window
            while(st.count(nums[j])){
                currWindowSum -= nums[i];
                st.erase(nums[i]);
                i++; 
            }
            currWindowSum += nums[j];
            st.insert(nums[j]);
            if(j - i + 1 == k){
                result = max(result , currWindowSum);
                currWindowSum -= nums[i];
                st.erase(nums[i]);
                i++;
            }
            j++;
        }
        return result;
    }
};

```
#### TC and SC
- **Time Complexity:** O(N)
- **Space Complexity:** O(N)

---
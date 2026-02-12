## Concatenation of Array

#### You are given an integer array nums of length n. Create an array ans of length 2n where ans[i] == nums[i] and ans[i + n] == nums[i] for 0 <= i < n (0-indexed). 
### Specifically, ans is the concatenation of two nums arrays. Return the array ans.

```cpp
class Solution {
public:
    vector<int> getConcatenation(vector<int>& nums) {

        int n =nums.size();
        vector<int> ans(2*n);
        for(int i=0;i<n;i++) {
            ans[i]=ans[i+n]=nums[i];
        }
        return ans;       
    }
};
```

## Contains Duplicate

#### Given an integer array nums, return true if any value appears more than once in the array, otherwise return false.

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_map<int,int> m;
        for(int i=0;i<nums.size();i++){
            if(m.find(nums[i]) != m.end()) return true;
            else{
                m[nums[i]]=i;
            }
        }
        return false;  
    }
};
```
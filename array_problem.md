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
## Valid Anagram
#### Given two strings s and t, return true if the two strings are anagrams of each other, otherwise return false.

#### An anagram is a string that contains the exact same characters as another string, but the order of the characters can be different.
```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.length()!=t.length()) return false;
        else{
            unordered_map <char,int> m1,m2;
            for(int i=0;i<s.length();i++){
                m1[s[i]]++;
                m2[t[i]]++;
            }
            if(m1!=m2) return false;
        }
        return true;
    }
};
```
## Two Sum
#### Given an array of integers nums and an integer target, return the indices i and j such that nums[i] + nums[j] == target and i != j.

#### You may assume that every input has exactly one pair of indices i and j that satisfy the condition.

#### Return the answer with the smaller index first.
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int> m;
        for(int i=0;i<nums.size();i++){
            if(m.find(target-nums[i])!=m.end()){
                return {m[target-nums[i]],i};
            }
            else{
                m[nums[i]]=i;
            }
        }
        return {};
    }
};
```
## Longest Common Prefix
#### You are given an array of strings strs. Return the longest common prefix of all the strings.

#### If there is no longest common prefix, return an empty string "".

```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        char val;
        string ans="";
        for(int j=0;j<strs[0].length();j++){
            val =strs[0][j];
            for(int i=1;i<strs.size();i++){
                if(val!=strs[i][j]) return ans;
            }
            ans+=val;
        }
        
        return ans;
    }
};
```

## Remove Element
#### You are given an integer array nums and an integer val. Your task is to remove all occurrences of val from nums in-place.

#### After removing all occurrences of val, return the number of remaining elements, say k, such that the first k elements of nums do not contain val.
```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int k=0;
        for(int i=0;i<nums.size();i++){
            if(nums[i]!=val){
                nums[k++]=nums[i];
            }
        }
        return k;
    }
};
```
## Majority Element
#### Given an array nums of size n, return the majority element.

#### The majority element is the element that appears more than ⌊n / 2⌋ times in the array. You may assume that the majority element always exists in the array.
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        unordered_map<int,int> m;
        int maxcount=0,ans;
        for(int i=0;i<nums.size();i++){
            m[nums[i]]++;
            if(maxcount<m[nums[i]]){
                maxcount=m[nums[i]];
                ans=nums[i];
            }
        }
        return ans;
    }
};
```
## Design HashSet
#### Design a HashSet without using any built-in hash table libraries.

Implement MyHashSet class:

void add(key) Inserts the value key into the HashSet.
bool contains(key) Returns whether the value key exists in the HashSet or not.
void remove(key) Removes the value key in the HashSet. If key does not exist in the HashSet, do nothing.

```cpp
class MyHashSet {
private:
    vector<bool> new_MyHashSet;
public:
    MyHashSet() {
        new_MyHashSet.resize(1000001,false);
    }
    
    void add(int key) {
        new_MyHashSet[key]=true;
    
    }
    
    void remove(int key) {
        new_MyHashSet[key]=false;
    }
    
    bool contains(int key) {
        return new_MyHashSet[key];
    }
};

/**
 * Your MyHashSet object will be instantiated and called as such:
 * MyHashSet* obj = new MyHashSet();
 * obj->add(key);
 * obj->remove(key);
 * bool param_3 = obj->contains(key);
 */
 ```

 ## 
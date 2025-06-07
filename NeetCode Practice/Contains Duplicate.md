
```
class Solution {
public:
	bool hasDuplicate(const std::vector <int> vector<int>& nums){
	std::unordered_set<int> hashset;
	
	 for(int n : nums){
		 if (hashset.find(n) != hashset.end()){
		 return true;
		 }
		 hashset.insert(n);
		 }
		 return false;
		  }
	};
```

Given an integer array, nums, return true if any value appears more than once in the array, otherwise return false.

i.e. if you are given the array {1,2,3,3} you should return true. whereas if you were given {1,2,3,4} you should return false. 


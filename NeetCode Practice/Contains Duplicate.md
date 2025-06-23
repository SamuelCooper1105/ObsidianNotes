
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

so the way this solution works is by taking in the array as an input for the solution. we then set up an unordered set which only needs one input as opposed to an unordered map. using a for loop interating over all the values in nums, the loop checks using an nested if loop to check if the value already exists within the set. 
if the value does not have two instances within the hash set(yet), the loop will add the value into the hashset, and continue checking values.
by adding in the values to the hash set, we can check if values exist more then once, if not the for loop simple returns a false value.

Some limitations of this approach include the fact we do not check for multiple values. In the Leetcode and Neetcode however the array lists, are capped at like 


``` mermaid.md
flowchart TD
	A[Start] -->B{Do something}
```

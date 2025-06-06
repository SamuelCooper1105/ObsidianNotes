We can implement indexes using Direct Addressing, ordered/unordered arrays, and ordered/unordered linked lists
- ### **Direct Addressing**:
	Before we begin lets make some assumptions about our bounds, keys are drawn from a universe $U={0,1,...m-1}$ where m is the number of slots in the dictionary. 
	Direct Addressing is essentially saying we have Key, which is a pair in realtion to some value which is data we want to store, we then have some address for that key, so we can search for our value.

	- Imagine we have some 64 bit number, which represents 18446744073709551616 different keys, obviously this is huge and beyond what we can accurately or realistically represent. 
	- this is also inefficient when $|U|>>|K|$ so we can use what we call a hash function (see [[#Hash Tables]]), which is a function that translates keys to indices of an array. 
	- This is much more space efficient then a direct address table. 
	- Ideally the keys would be spread out over the array, this reduces [[#Collisions]]
- ### Ordered/Unordered Arrays:
	
- ### Ordered/Unordered Linked Lists:
	
### Hash Tables :
A hash table is a data structure that stores data as key value pairs. This is accomplished by taking the key part of the key value pair and putting it through a hash function. We describe the relation of the elements in the hash table in relation to the size of the table itself, the Load Factor. The higher the load factor, the longer search times will be, and the more collisions(See [[#Collisions]]) will occur. An ideal load factor, can be achieved by a good hash function and proper table resizing. 

### Collisions
So what is a collision? A collision is where a key is hashed to a slot that already has a key inserted in it, if $|K| \leq m$, where m is the amount of slots and K is the amount of keys, the risk of a collision 
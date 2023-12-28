***Static Arrays***

- - - 

***Arrays***

***→ collection of ordered, contiguous group of elements***

- - - 

***Static Arrays***

***→ arrays with an allocated size when initialised - size of the array cannot be changed after initialisation***

- → *in strictly typed languages (C++, Java) - arrays are defined as static arrays*
- → *in loosely typed languages (Python) → have dynamic arrays rather than static arrays*

- - - 

***Operations***

- → ***reading*
- → ***traversal*
- → ***deletion*
- → ***insertion***

- - - 

***Reading***

- *elements are accessed through indices - which start at 0*
- *reading from an array → **accessing the index***

```c++
myArray = {1,3,5};
myArray[i];
```

- *as long as the index of the element is known → access is instant*
- *each index of myArray is mapped to an address in RAM*
- *regardless of size of input array (3 here) → time taken to access element (given a known index) is constant*

- ***time complexity → $O(1)$*

- - -

***Traversal***

- *→ **iterating through all values in an array***
- *can traverse to any part of the array*

```c
for (int i = 0; i < length; i++){
	cout << myArray[i];
}
```

- *length-1 is the last accessible index of the array (n-1 if n is the size of the array)*

- ***time complexity → $O(n)$*

- - - 

***Deletion (from end of array)***

- *in strictly typed languages → all array indices are filled with 0s/some default value upon initialisation - denoting an empty array*
- ***to remove an element from the last index of the array → set its value to 0/null/-1***
- *not being deleted per se → but overwriting denotes an empty index*
- ***reduces the length of the array by 1** as one less element after deletion*

```c++
void removeEnd(int arr[], int length) {
	if(length > 0) {
		arr[length-1] = 0;
	}
}
```

![deletion-at-end|500](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/e081b055-98b3-4edd-55f6-8fa6cc59d500/sharpen=1)

- *6 is deleted/overwritten by either 0 or -1 → length decremented by 1*
- ***time complexity → $O(1)$*

- - - 

***Deletion (from ith index)***

- *deleting from a random index i*
- *to maintain contiguous order → given the target index i - **need to iterate from i+1 until the end of the array and shift each element 1 position to the left** - to overwrite value at index i*
- *in the worst case → need to shift all the elements to the left*

```c++
void removeMiddle(int arr[], int i, int length){
	for(int index = i+1; index < length; index++){
		arr[index - 1] = arr[index];
	}
}
```

![removal-0th-index](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/2888f751-1ae4-4534-68ba-1b42689a0b00/sharpen=1)

- ***time complexity → $O(n)$*

- - - 

***Insertion (from end of array)***

- *can always access the last index of the array
- *assuming the last index of the array is empty*

```c++
void insertEnd(int arr[], int n, int length, int capcity){
	if(length < capacity){
		arr[length] = n;	
	}
}
```

- *length is the number of elements inside the array, capacity refers to the maximum number of elements the array can hold*

- ***time complexity → $O(1)$*

- - - 

***Insertion (at ith index)***

- *inserting at an arbitrary index i*
- *if i is not already empty → cannot overwrite index i → as would lose value that is already there*
- ***to insert → need to shift all values from index i to length-1 one position to the right***

```c++
void insertMiddle(int arr[], int i, int n, int length){
	for(int index = length - 1, index >= i; index--){
		arr[index+1] = arr[index];
	}
	arr[i] = n;
}
```

![insertion-at-i](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/34345b51-7e7d-478f-5ba1-68672e931200/sharpen=1)

- *shifting occurs prior to insertion to ensure values are not overwritten*
- ***time complexity → $O(n)$*

- - - 

***Complexity***

***Time:***

|Operation|Big-O Time|Notes|
|---|---|---|
|Access|O(1)||
|Insertion|O(1)∗|O(n) if insertion in the middle since shifting will be required|
|Deletion|O(1)∗|O(n) if deletion in the middle since shifting will be required|
***Space:***
- → $O(n)$
- → *n elements in array* 

- - - 

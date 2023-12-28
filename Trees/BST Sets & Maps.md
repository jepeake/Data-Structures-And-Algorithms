***BST Sets and Maps***

- - - 

- ***sets & maps**, similar to stacks & queues, are interfaces that can be implemented using trees*
- ***implementing them allows for $O(logn)$ time for operations***

- - - 

***Sets***

- *given a set of values*
- *storing them in a set (vs dynamic array) ensures that we have **unique values in our data structure***
- *implementing it using a tree ensures that out **values are stored alphabetically***

- - - 

***Maps***

- *map → operates on **key-value pairs***
- *keys map to a value → can find all the information associated with that key*
- *value could be an object*

- *operations performed on a TreeMap run in $O(logn)$ time*
- *mapping for the phonebook would look like:*

```c++
{'Alice' : 123, 'Brad' : 345, 'Collin' : 678}
```

- - - 

***C++ TreeMap:***

```c++
map<string, string> treeMap;
```

- - - 

- *trees are one way to implement sets & maps → hashing is another way*

- - - 

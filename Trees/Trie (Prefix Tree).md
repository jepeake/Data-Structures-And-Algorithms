***Trie (Prefix Tree)***

- - - 

***→ allows us to organise words based on the first few letters (prefix)***

- *letters are represented as the edges that connect the nodes*

- *each node will have at most 26 children (number of letters in alphabet)*

- -  -

***Operations***

- *Insert Word:* $O(1)$
- *Search Word:* $O(1)$
- *Search Prefix:* $O(1)$

<br>

- *a hashmap can also insert & search for words in constant time*
- *but it only supports an exact match for a string*
- *so searching for a prefix will be* $O(n)$ *in a hashmap*
- *this is the advantage of a prefix tree/trie*
- *e.g. search engine autocomplete*

- - - 

***Implementation***

***TrieNode***

```cpp
class TrieNode {
public:
    unordered_map<char, TrieNode*> children_;
    bool word_ = false;
};
```

- *each node keeps track of its children using a HashMap*
- *the key is the character (edge) - and the value is the TriNode (child) that is being pointed to*

- *we are inserting words into a Trie - and need to determine whether a word exists or not when we search*
- *therefore - we have a boolean value which determine if that TriNode is the end of the word*

- - -

***Trie Class***

```cpp
class Trie {
public:
    TrieNode root_;
};
```

- *whenever a Trie Class is instantiated - we have a new TrieNode root in the constructor*

- - - 

***Insertion***

```cpp
void insert(string word) {
    TrieNode *curr = &root_;
    for (char c: word) {
        if (curr->children_.count(c) == 0) {
            curr->children_[c] = new TrieNode();
        }
        curr = curr->children_[c];
    }
    curr->word_ = true;
}
```

- *to insert into the Trie → iterate through each character of the word*
- *if the character does not already exist in the Trie → insert into our HashMap - along with its children*
- *if it does already exist - we can keep traversing down the tree*
- *once we have reached the last character - mark that TrieNode as a word - to indicate the end of the word*

- *as we are using a HashMap to store the children → we can retrieve the children in* $O(1)$ *time (HashMap search is constant time)*

****

***Search***

```cpp
bool search(string word) {
    TrieNode *curr = &root_;

    for (char c: word) {
        if (curr->children_.count(c) == 0) {
            return false;
        }
        curr = curr->children_[c];
    }
    return curr->word_;
}
```

- *search for if a word exists & return a boolean*
- *iterate through each character & as soon as a character does not exist in the tree → return false*
- *if we get to the last character - return True/False - depending on if that character is marked as the end of a word*
- *e.g. if we added apple to the Trie, and then searched for app, the p would not be marked as the end of a word, so app would not be in the Trie*

- - - 

***Prefix Search***

```cpp
bool startsWith(string prefix) {
    TrieNode *curr = &root_;
    for (char c: prefix) {
        if (curr->children_.count(c) == 0) {
            return false;
        }
        curr = curr->children_[c];
    }
    return true;
}
```

- *same as search, but instead of returning mark for end of word, return true if all characters in the prefix exist in our Trie*

- - - 

***Complexity (Search)***

***Brute Force Method:***
- *brute force method: if we did not have a prefix tree - would have to iterate over all words and check which ones match*
- ***Time Complexity:*** $O(n \times m)$ → *n words of m average length*
- ***Space Complexity:*** $O(n \times m)$ *→ (storing each character of each word)*

***Tries:***
- ***Time Complexity:*** $O(m)$
- *iterate a single time for each character in the target word*
- ***Space Complexity:*** $O(n \times m \times c)$ 
- → *n: no. words / m: length of longest word / c: size of character set*
- → *in the worst case - no overlap in prefixes & every word of maximum length*

- - - 

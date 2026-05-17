---
title: Hash Table
publish: true
date created: 2026-05-17
---

### What is a hash table?
A Hash table is defined as a data structure used to insert, look up, and remove key-value pairs quickly. It operates on the hashing concept, where each key is translated by a hash function into a distinct index in an array. The index functions as a storage location for the matching value. In simple words, it maps the keys with the value.

### Load factor
A hash table's load factor is determined by how many elements are kept there in relation to how big the table is. The table may be cluttered and have longer search times and collisions if the load factor is high. An ideal load factor can be maintained with the use of a good hash function and proper table resizing.

### Time complexity
For lookup, insertion, and deletion operations, hash tables have an average-case time complexity of O(1). Yet, these operations may, in the worst case, require O(n) time, where n is the number of elements in the table.

![](/images/HashTable.png)


[[Data-Structure]]
# [Source](https://www.geeksforgeeks.org/dsa/hash-table-data-structure/)
Two Sum
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Two Sum II (Sorted Array)
Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.

Two Sum III (Design)
Design and implement a TwoSum class. It should support the following operations: add and find.

add - Add the number to an internal data structure.
find - Find if there exists any pair of numbers which sum is equal to the value.

I believe it depends a lot on what method we are using for find...
If we use binary search to get O(lgN) find, then we have to sort the array... which means we might need to use a binary search tree for O(lgN) insertion
If we use hash map as a solution, We have to maintain two data structure?

Two Sum IV(BST)
Given a Binary Search Tree and a target number, return true if there exist two elements in the BST such that their sum is equal to the given target.

It is quite a disaster to implement.. there are multiple solutions depending on which one you prefer...
Hashset, every node use binary search, 
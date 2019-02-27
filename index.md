# Array Problems
[977 Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)
Given an array of integers A sorted in non-decreasing order, return an array of the squares of each number, also in sorted non-decreasing order.
```
Input: [3,1,2,4]
Output: [2,4,3,1]
The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.
```
- Edge case
  - Consider negative numbers
- Solution 1
  - Square then sort
- Solution 2
  - Have two indices on left and right
  - Depending which one is greater use it
---
[905 Sort Array by Parity](https://leetcode.com/problems/sort-array-by-parity/)
Given an array A of non-negative integers, return an array consisting of all the even elements of A, followed by all the odd elements of A.
```
Input: [3,1,2,4]
Output: [2,4,3,1]
The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.
```
You may return any answer array that satisfies this condition.
- Edge case
  - None
- Solution 1
  - Sort with custom comparator
  - key = lambda x: x % 2
  - Time: O(nlgn) Space: O(n)
- Solution 2
  - Quicksort
  - Maintain 2 pointers i, j = 0, n
  - Time: O(n) Space: O(1)
  - Loop invariant is below i and above j is sorted
- Solution 3
  - Naive put even first, odd later
  - Time: O(n) Space: O(N)
---
[832. Flipping an Image](https://leetcode.com/problems/flipping-an-image/)
Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.

To flip an image horizontally means that each row of the image is reversed.  For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].

To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].
```
Input: [[1,1,0],[1,0,1],[0,0,0]]
Output: [[1,0,0],[0,1,0],[1,1,1]]
Explanation: First reverse each row: [[0,1,1],[1,0,1],[0,0,0]].
Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]]
```
- Insights
  - Either make use of library to reverse
  - List comprehension
```
def flipAndInvertImage(self, A):
  # row[::-1] reverse the row
  return [[1-i for i in row[::-1]] for row in A]
```
---
[561. Array Partition I](https://leetcode.com/problems/array-partition-i/)
Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

```
Input: [1,4,3,2]

Output: 4
Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).
```
Note:
n is a positive integer, which is in the range of [1, 10000].
All the integers in the array will be in the range of [-10000, 10000].

- Insights
  - Brute force is to consider every pair which is O(Nchoose2) = O(N^2)
  - The largest number is array is excluded... but we can include the next largest number by pairing it with the largest
- Solution
  - sort then pick every even index element
  - Time: O(NlgN) Space: Depending on sort
---
[985. Sum of Even Numbers After Queries](https://leetcode.com/problems/sum-of-even-numbers-after-queries/)
We have an array A of integers, and an array queries of queries.

For the i-th query val = queries[i][0], index = queries[i][1], we add val to A[index].  Then, the answer to the i-th query is the sum of the even values of A.

(Here, the given index = queries[i][1] is a 0-based index, and each query permanently modifies the array A.)

Return the answer to all queries.  Your answer array should have answer[i] as the answer to the i-th query.
```
Input: A = [1,2,3,4], queries = [[1,0],[-3,1],[-4,0],[2,3]]
Output: [8,6,2,4]
Explanation: 
At the beginning, the array is [1,2,3,4].
After adding 1 to A[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to A[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to A[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to A[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
```
- Insights
  - Brute force approach will work however it might time out as you keep iterating to calculate the sum
  - Keep track of the sum and modify it if query affects even numbers
  - Minus even number -> add val -> Add back if even for cleaner code
---
[922. Sort Array By Parity II](https://leetcode.com/problems/sort-array-by-parity-ii/)
Given an array A of non-negative integers, half of the integers in A are odd, and half of the integers are even.

Sort the array so that whenever A[i] is odd, i is odd; and whenever A[i] is even, i is even.

You may return any answer array that satisfies this condition.

```
Input: [4,2,5,7]
Output: [4,5,2,7]
Explanation: [4,7,2,5], [2,5,4,7], [2,7,4,5] would also have been accepted.
```
- Insights
  - Naive approach is initialise another array and iterate through original array and maintain 2 pointers to even and odd indices => space complexity O(n)
- Solution
  - Sort in place for space complexity O(1), Time Complexity is still O(n)
  - Maintain 2 pointers: 0 for even, 1 for odd
  - For every even index elements, if the element is even it is done else find nearest even element with odd index and swap it

```
j = 1
for i in xrange(0, len(A), 2):
  if A[i] % 2:
    while A[j] % 2:
      j += 2
    A[i], A[j] = A[j], A[i]
return A
```
---
[509. Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)
The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,

F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), for N > 1.
Given N, calculate F(N).

- Insights
  - Trivial... consider recursive versus iterative approach and not time out
---
[867. Transpose Matrix](https://leetcode.com/problems/transpose-matrix/)
Given a matrix A, return the transpose of A.

The transpose of a matrix is the matrix flipped over it's main diagonal, switching the row and column indices of the matrix.

- Python tricks with one liner
  - Understanding what zip does and what * does to unpack the values 
```
return list(zip(*A))
```
- Else just do the manually iterate 
---
[766. Toeplitz Matrix](https://leetcode.com/problems/toeplitz-matrix/)
A matrix is Toeplitz if every diagonal from top-left to bottom-right has the same element.

Now given an M x N matrix, return True if and only if the matrix is Toeplitz.
 
- Insights
  - Trivial coding
  - Take note same diagonal if r1-c1 == r2-c2
  - Store the value seen in that diagonal
- Extension
  - When cannot load the entire matrix
  - Need to store the value seen in each diagonal

---
[566. Reshape the Matrix](https://leetcode.com/problems/reshape-the-matrix/)
In MATLAB, there is a very useful function called 'reshape', which can reshape a matrix into a new one with different size but keep its original data.

You're given a matrix represented by a two-dimensional array, and two positive integers r and c representing the row number and column number of the wanted reshaped matrix, respectively.

The reshaped matrix need to be filled with all the elements of the original matrix in the same row-traversing order as they were.

If the 'reshape' operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.
```
 flat = sum(nums, [])   # convert two-dimension array to one-dimension array
 if r * c != len(flat): return nums
 return [[flat.pop(0) for j in range(c)] for i in range(r)]
```
---
[243. Shortest Word Distance](https://www.leetfree.com/problems/shortest-word-distance.html)
Given a list of words and two words word1 and word2, return the shortest distance between these two words in the list.

For example,
Assume that words = ["practice", "makes", "perfect", "coding", "makes"].

Given word1 = “coding”, word2 = “practice”, return 3.
Given word1 = "makes", word2 = "coding", return 1.

Note:
You may assume that word1 does not equal to word2, and word1 and word2 are both in the list.



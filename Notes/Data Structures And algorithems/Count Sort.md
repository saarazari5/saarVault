---
dateCreated: "2022-06-08 16:19"
tags: [sorting, data structures, algorithms]
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%
Related Notes: 

# [[Count Sort]]
[Counting sort](http://en.wikipedia.org/wiki/Counting_sort) is a sorting technique based on keys between a specific range. It works by counting the number of objects having distinct key values (kind of hashing). Then do some arithmetic to calculate the position of each object in the output sequence.

### Characteristics of counting sort:
- Counting sort makes assumptions about the data, for example, it assumes that values are going to be in the range of 0 to 10 or 10 – 99 etc, Some other assumptions counting sort makes are input data will be all real numbers.
- Like other algorithms this sorting algorithm is not a comparison-based algorithm, it hashes the value in a temporary count array and uses them for sorting.
- It uses a temporary array making it a non [[In Place algorithm]].

**Points to be noted:** 
- Counting sort is efficient if the range of input data is not significantly greater than the number of objects to be sorted. Consider the situation where the input sequence is between range 1 to 10K and the data is 10, 5, 10K, 5K. 

- It is not a comparison-based sorting. Its running time complexity is O(n) with space proportional to the range of data. 

- Counting sort is able to achieve this because we are making assumptions about the data we are sorting.

- It is often used as a sub-routine to another sorting algorithm like radix sort. 
- Counting sort uses partial hashing to count the occurrence of the data object in O(1).
- Counting sort can be extended to work for negative inputs also.
- Counting sort is not a [stable algorithm](https://www.geeksforgeeks.org/stability-in-sorting-algorithms/). But it can be made stable with some code changes.
---
dateCreated: "2022-05-06 00:44"
tags: []
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%
Related Notes: 

# [[Linear Data Structures]]
Data structure where data elements are arranged sequentially or linearly where each and every element is attached to its previous and next adjacent is called a **linear data structure**. In linear data structure, single level is involved. Therefore, we can traverse all the elements in single run only. Linear data structures are easy to implement because computer memory is arranged in a linear way. Its examples are [[array]], [[stack]], [[queue]], [[Linked list]], etc.


### 2-SUM 
assume we have a group of numbers $S={\{x_1,x_2,...,x_n\}}$ 
lets build a new linear data structure that support the following actions :
1) building of the data.
2) a method that check if there is a pair of elements $x_i,x_j\in{S}$  that their sum will be equal to the input $y$ . $x_i+x_j=y$ 


for part 1 we just need to save an array.
for part 2, we will save the elements in a sorted array
we know that for $x_i$ if there is a pair than $y-x_i\in{S}$ 
so for each element we perform binary search for $y-x_i$. 
time complexity : $O(n\log{n})$ .

we can even improve the algorithm by having a pointer $l$ to the start of the array and a pointer $n$ to the end of the array. 
each iteration we sum : $A[l]+A[n]$ 
if :
* $A[l]+A[n]=y$  we done
* $<y$ than : $l$++
* $>y$ than : $n--$ 
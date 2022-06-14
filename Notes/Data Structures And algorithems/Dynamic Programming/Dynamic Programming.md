---
dateCreated: "2022-06-14 10:08"
tags: [algorithem,data structures]
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%
Related Notes: 

# [[Dynamic Programming]]
Dynamic Programming is mainly an optimization over plain [recursion](https://www.geeksforgeeks.org/recursion/). Wherever we see a recursive solution that has repeated calls for same inputs, we can optimize it using Dynamic Programming. The idea is to simply store the results of subproblems, so that we do not have to re-compute them when needed later. This simple optimization reduces time complexities from exponential to polynomial. For example, if we write simple recursive solution for [Fibonacci Numbers](https://www.geeksforgeeks.org/program-for-nth-fibonacci-number/), we get exponential time complexity and if we optimize it by storing solutions of subproblems, time complexity reduces to linear.


![[Pasted image 20220614100839.png]]

### How to solve a Dynamic Programming Problem ?

```
Steps to solve a DP

1) Identify if it is a DP problem
2) Decide a state expression with 
   least parameters (can be a data structure of some sort)
3) Formulate state relationship    
4) Do tabulation (or add memoization)
```

##### how to identify a DP ? * write a naive solution. 
* write a recursive solution.
* check if there are multiple values that are being checked or calculated.

##### Deciding the state   
DP problems are all about state and their transition. This is the most basic step which must be done very carefully because the state transition depends on the choice of state definition you make. So, let’s see what do we mean by the term “state”.

**State** A state can be defined as the set of parameters that can uniquely identify a certain position or standing in the given problem. This set of parameters should be as small as possible to reduce state space. 

So, our first step will be deciding a state for the problem after identifying that the problem is a DP problem.  
As we know DP is all about using calculated results to formulate the final result.   
So, our next step will be to find a relation between previous states to reach the current state.

##### Adding memoization or tabulation for the state
This is the easiest part of a dynamic programming solution. We just need to store the state answer so that next time that state is required, we can directly use it from our memory


### Dynamic Programming problems
* [[Knapsack Problem]]
* [[Fibonacci Numbers]]
* [[Longest Increasing Subsequence]]
* 
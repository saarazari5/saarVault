---
dateCreated: "2022-05-04 17:51"
tags: [algorithem,data structures,c,c++]
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%
Related Notes: 

# [[Divide and conquer]]
**Divide And Conquer**   
This paradigm can be divided into the following three parts:

1.  **Divide:** This involves dividing the problem into smaller sub-problems.
2.  **Conquer:** Solve sub-problems by calling recursively until solved.
3.  **Combine:** Combine the sub-problems to get the final solution of the whole problem.

The following are some standard algorithms that follow Divide and Conquer algorithm : 
[[Quicksort]] [[merge sort]] [[binary search]] [Closest Pair of Points](https://www.geeksforgeeks.org/closest-pair-of-points-using-divide-and-conquer-algorithm/)

## use cases 
1) solving hard problems by dividing it to sub problems.
2) efficiency.
3) concurrency - can solve the problems in a concurrence matter. 

## the algorithm
``` psudo 
DAC(a, i, j)
{
    if(small(a, i, j))
      return(Solution(a, i, j))
    else 
      m = divide(a, i, j)               // f1(n)
      b = DAC(a, i, mid)                 // T(n/2)
      c = DAC(a, mid+1, j)            // T(n/2)
      d = combine(b, c)                 // f2(n)
   return(d)
}
```

## usage 
### increase-decrease array
assume we have an array $A[1\text{...n}]$ and we now that $\exists_{1\leq k\leq n}:\forall_{1\leq i\leq k}:{A[i]<A[i+1]} \ \ and \ \ \forall_{k\leq i\leq n}:A[i]>A[i+1]$

let build an algorithm that find the wanted $k$ :

``` psudo 
int IncreaseDecreaseIndex(A[n], int begin,int end){
  if A length lower than 3
	  solve in o(1)
	m = (begin+end)/2
	if A[m-1]<A[m]>A[m+1]
		return m
	if A[m-1]<A[m]
		return IncreaseDecreaseIndex(A,m,end)
	return IncreaseDecreaseIndex(A,begin,m)		  
}
```
[[Asymptotic Analysis]]: $T(n)=T(\frac{n}{2})+O(1)\in O(n\log{n})$ 

### the puddle on the roof
assume we have a model that represent a building height and its index in a row
and we have a row of this model being represented as $A[n]$ 
on a rainy day a paddle will be on the roof of a building where the right next building and the left building are taller than him. 
build an algorithm that return one of the roofs where a puddle will be created 
``` psudo 
int puddleOnTheRoof(A[n], int begin, int end){
	if A length lower than 3
	  solve in o(1)
	m = (begin+end)/2
	if A[m-1]>A[m]<A[m+1]
		return m
	if A[m-1]<A[m]
		return puddleOnTheRoof(A,begin,m)
	return puddleOnTheRoof(A,m,end)
}
```
[[Asymptotic Analysis]]: $T(n)=T(\frac{n}{2})+O(1)\in O(n\log{n})$


### largest sum of subArray
input : $A[n]$ 
output : $A[i...j]$ with the largest possible sum (can be more the one solution)

__intuition:__ 
there are 3 possible options: 
* both $i$ and $j$ are in the first half
* both $i$ and $j$ are in the second half
* $i$ is in the first half but $j$ is in the second half

 __solution__:
 * find the largest sum sub array in the left side 
 * find the largest sum sun array in the right side 
 * merge them

for example for $[10,7,-5,6,-1,-3,10,0]$  the calculation will be as following 

* divide the array : $[10,7,-5,6]$ and $[-1,-3,10,0]$ 
* sum each subarray and divide them again ($16$ and $7$)
* now we have the arrays $[10,7]$ $[-5,6]$ $[-1,-3]$ $[10,0]$ 
* sum each of them again until you reach one element array and return it as the sum. 
* compare each sum with his father sum and take the largest for example $10+7=17 > 10$  so we pick $17$ 
* if 2 bigger large array sums are next to each other in indexes , merge them , if not , pick the biggest sum of the two.
   in our case $17$ is not next to the biggest sum of the right part $10$ 
   and therefore not merge is needed...
* continue until returning to parent.

[[Asymptotic Analysis]] : $2T(\frac{n}{2})+O(1)\in{\Theta{(n)}}$


### power of a number
input : $a\in\mathbb{R}$ $n\in\mathbb{N}$ 
output : $a^{n}$ 

in $O(n)$ in pretty simple.... how ever we want to improve the Time complexity of this very used method.

##### improvement
$$ a^n =
  \begin{cases}
    1  & n=0\\
    a^\frac{n}{2}\cdot{ a^\frac{n}{2}} & 2|n \\
    a^{\frac{n-1}{2}}\cdot a^{\frac{n-1}{2}}\cdot a & 2\nmid n
  \end{cases}
$$
we might think that the runtime of this will be $T(n)=T(\frac{n}{2})+O(1)\in{O{(logn)}}$ 
how ever because the computer need the $log(m)$ bytes in order to represent $m$ number. this means that the processor needs another $log(n)$ work in order to save the solution n in memory. 
so what we did was an improvement because we did less multiply actions. how ever the performance will be higher than $O(logn)$ 


### Fibonacci algorithm 
we know the ordinary way of calculation with the formula : 
$f_{n}=f_{n-1}+f_{n-2}$ 
however the runtime of this algorithm is $O(2^n)$ 

if we calculating from the first elements to top it will be $\Theta(n)$ but with space complexity of $O(n)$ because we need to create $n$ variables for calculation ,but we can do even better.

$$f_n=\frac{(\frac{1+\sqrt{5}}{2})^{n}-(\frac{1-\sqrt{5}}{2})^{n}}{\sqrt{5}}$$

this formula is one way of calculation the $n$-th element in fib series, the time complexity of raising a number to a power of $n$ is $O(logn)$ how ever when working with a irrational numbers there can be a miscalculations, even more when $n$ is a very large number.

to fix this we can use the following method-

we can improve the miscalculation by looking at $f_{n+1}$ and $f_{n}$ 
as a vector and we will assume the following math equation (we can prove it with induction): 
$$ \bigl(\begin{smallmatrix}
f_{n+1} \\ f_{n} 
\end{smallmatrix} \bigr) = \bigl(\begin{smallmatrix}
1&1 \\ 1&0
\end{smallmatrix} \bigr)\bigl(\begin{smallmatrix}
f_{n} \\ f_{n-1}
\end{smallmatrix} \bigr) $$

we can open this formula and we will get 
$$ \bigl(\begin{smallmatrix}
f_{n+1} \\ f_{n} 
\end{smallmatrix} \bigr) = \bigl(\begin{smallmatrix}
1&1 \\ 1&0
\end{smallmatrix} \bigr)^i\cdot\bigl(\begin{smallmatrix}
f_{n+1-i} \\ f_{n-i}
\end{smallmatrix} \bigr) = \bigl(\begin{smallmatrix}
1&1 \\ 1&0
\end{smallmatrix} \bigr)^n\cdot\bigl(\begin{smallmatrix}
1 \\ 0
\end{smallmatrix} \bigr) $$
because matrix multiplication is $\Theta(1)$ the entire calculation is just $\Theta(logn)$ because raising to the power of numbers mentioned as above is $\Theta(logn)$.

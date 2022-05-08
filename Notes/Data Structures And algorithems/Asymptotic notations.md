---
dateCreated: "2022-04-27 12:39"
tags: [algorithem,data structures,c,c++]
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%
Related Notes: 

# [[Asymptotic notations]]
The main idea of asymptotic analysis is to have a measure of the efficiency of algorithms that don’t depend on machine-specific constants and don’t require algorithms to be implemented and time taken by programs to be compared. Asymptotic notations are mathematical tools to represent the time complexity of algorithms for asymptotic analysis. The following 5 asymptotic notations are mostly used to represent the time complexity of algorithms.

## big O notation 
he Big O notation defines an upper bound of an algorithm, it bounds a function only from above. (this is the worst case scenario).
$$f(n)\in O(g(n))\leftrightarrow \exists_{c>0,n_0\geq0}:\forall_{n\geq n_0}:f(n)\leq c\ \cdot g(n) $$
to simplify: $O(g(n))$  = { $f(n)$: there exist positive constants $C$ and $n_0$ such that $0\leq f(n)\leq c\cdot g(n) \text{ for all } n\geq n_0$ }

![[Pasted image 20220427141323.png]]

### examples:
#### $f(n)=7n+15$ 
$\displaylines{g(n)=n \\ for \ \ c=22 \ \ and \ \ n_0=1 \\ \downarrow \\ f(n)\leq 22g(n) \\ \downarrow \\ f(n)\in O(g(n))=O(n)}$ 

##  $\Omega$ notation 
Just as Big O notation provides an asymptotic upper bound on a function, Ω notation provides an asymptotic lower bound.   
Ω Notation can be useful when we have a lower bound on the time complexity of an algorithm. 
basically this the the best case scenario

$$f(n) \in \Omega(g(n)) \leftrightarrow \exists_{c>0, \ n_0\geq 0}:\ \forall_{n\geq n_0}: \ f(n)\geq c\cdot g(n) $$
![[Pasted image 20220427143416.png]]


## $\Theta$ notation 
The theta notation bounds a function from above and below, so it defines exact asymptotic behavior.   
A simple way to get the Theta notation of an expression is to drop low-order terms and ignore leading constants.

$$f(n)\in \Theta(g(n))\leftrightarrow f(n)\in O(g(n))\wedge f(n)\in \Omega(g(n))$$

we can define it also like the following : 
$$f(n)\in \Theta(g(n))\leftrightarrow \exists_{c_2\geq c_1>0 ,n_0\geq0} :\forall_{n\geq n_0}:c_1\cdot g(n) \leq f(n)\leq c_{2}\cdot g(n) $$
![[Pasted image 20220427143954.png]]


## Little $ο$ asymptotic notation 
Big-Ο is used as a tight upper-bound on the growth of an algorithm’s effort (this effort is described by the function f(n)), even though, as written, it can also be a loose upper-bound. “Little-ο” (ο()) notation is used to describe an upper-bound that cannot be tight.
in a math syntax that just means that

$$f(n)\in o(g(n))\leftrightarrow \forall_{c>0}\exists_{n_0\geq0}:\forall_{n\geq n_0}:f(n)\leq c\ \cdot g(n) $$

## Little $\omega$  asymptotic notation
The relationship between Big Omega (Ω) and Little Omega (ω) is similar to that of Big-Ο and Little o except that now we are looking at the lower bounds. Little Omega (ω) is a rough estimate of the order of the growth whereas Big Omega (Ω) may represent exact order of growth. We use ω notation to denote a lower bound that is not asymptotically tight.  
And, f(n) ∈ ω(g(n)) if and only if g(n) ∈ ο((f(n)).

$$f(n) \in \omega(g(n)) \leftrightarrow \forall_{c>0}\exists_{n_0\geq 0}:\ \forall_{n\geq n_0}: \ f(n)\geq c\cdot g(n) $$


## Using boundaries to define asymptotic notations
if $\lim_{n\to\infty}\frac{f(n)}{g(n)}$ exists than:

$$\displaylines{\lim_{n\to\infty}\frac{f(n)}{g(n)} = 0 \leftrightarrow f(n)\in o(g(n)) \\ \\ \lim_{n\to\infty}\frac{f(n)}{g(n)} = x\in\mathbb{R^{+}}\leftrightarrow f(n)\in{\Theta(g(n))} \\ \\ \lim_{n\to\infty}\frac{f(n)}{g(n)} = \infty \leftrightarrow f(n)\in{\omega(g(n))}}$$

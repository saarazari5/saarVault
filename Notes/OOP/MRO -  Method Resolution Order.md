---
dateCreated: "2022-06-13 15:40"
tags: [oop, java, python]
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%
Related Notes: 

# [[MRO -  Method Resolution Order]]
**MRO** is a concept used in inheritance. It is the order in which a method is searched for in a classes hierarchy and is especially useful in Python because [[Python]] supports [[multiple inheritance]]

in this summary, we will focus on python because of the method mentioned above... 

### MRO in python :
In Python, the MRO is from bottom to top and left to right. This means that, first, the method is searched in the class of the object. If it’s not found, it is searched in the immediate super class. In the case of multiple super classes, it is searched left to right, in the order by which was declared by the developer. For example:

``` python 
def class C(B, A)
```

in this case the search will be $C\rightarrow B\rightarrow A$ for a method implementation. Since B was mentioned first in the class declaration, it will be searched for first while resolving a method.

#### example 1 
![[Pasted image 20220613155236.png]]

``` Python 
class A:
	def method(self):
	  print("A.method() called")

  

class B(A):
	def method(self):
	  print("B.method() called")

  
b = B()
b.method()

```

This is a simple case with single inheritance. In this case, when `b.method()` is called, it first searches for the method in class B. In this case, class B had defined the method; hence, it is the one that was executed. In the case where it is not present in B, then the method from its immediate super class (A) would be called. So, the MRO for this case is: B -> A.


#### example 2
![[Pasted image 20220613155708.png]]
``` Python 
class A:

 def method(self):
  print("A.method() called")

class B:
 pass

class C(B, A):
 pass
 
c = C()
c.method()
```

The MRO for this case is:  
C -> B -> A  
The method only existed in A, where it was searched for last.
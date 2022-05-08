---
dateCreated: "2022-04-17 17:42"
tags: [java]
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%
Related Notes: 

# [[Static and Dynamic Binding]]

## Static binding
In Java static binding refers to the execution of a program where type of object is determined/known at compile time i.e when compiler executes the code it know the type of object or class to which object belongs.
-   private, final and static members (methods and variables) use static binding while for [[virtual methods]] (In Java methods are virtual by default) binding is done during run time based upon the run time object.

__The binding which can be resolved at compile time by the compiler is known as static or early binding. The binding of all the static, private, and final methods is done at compile-time.__
```Java
// Java Program to Illustrate Static Binding

// Main class
class NewClass {

	// Static nested inner class
	// Class 1
	public static class superclass {

		// Method of inner class
		static void print()
		{

			// Print statement
			System.out.println(
				"print() in superclass is called");
		}
	}

	// Static nested inner class
	// Class 2
	public static class subclass extends superclass {

		// Method of inner class
		static void print()
		{

			// print statement
			System.out.println(
				"print() in subclass is called");
		}
	}

	// Method of main class
	// Main driver method
	public static void main(String[] args)
	{

		// Creating objects of static inner classes
		// inside main() method
		superclass A = new superclass();
		superclass B = new subclass();

		// Calling method over above objects
		A.print();
		B.print();
	}
}

```

__Output__
```
print in superclass is called
print in superclass is called
```

**Output Explanation:** As you can see, in both cases the print method of the superclass is called. Let us discuss how this happens :
-   We have created one object of subclass and one object of the superclass with the reference of the superclass.
-   Since the print method of the superclass is static, the compiler knows that it will not be overridden in subclasses and hence compiler knows during compile time which print method to call and hence no ambiguity.

## Dynamic binding 
In Dynamic binding compiler doesn’t decide the method to be called. Overriding is a perfect example of dynamic binding. In overriding both parent and child classes have the same method.
```java
// Java Program to Illustrate Dynamic Binding

// Main class
public class GFG {

	// Static nested inner class
	// Class 1
	public static class superclass {

		// Method of inner class 1
		void print()
		{

			// Print statement
			System.out.println(
				"print in superclass is called");
		}
	}

	// Static nested inner class
	// Class 2
	public static class subclass extends superclass {

		// Method of inner class 2
		@Override void print()
		{

			// Print statement
			System.out.println(
				"print in subclass is called");
		}
	}

	// Method inside main class
	public static void main(String[] args)
	{

		// Creating object of inner class 1
		// with reference to constructor of super class
		superclass A = new superclass();

		// Creating object of inner class 1
		// with reference to constructor of sub class
		superclass B = new subclass();

		// Calling print() method over above objects
		A.print();
		B.print();
	}
}
```

**Output**
```
print in superclass is called
print in subclass is called
```

**Output Explanation:** the output differs. But why? Let’s break down the code and understand it thoroughly. 
-   Methods are not static in this code.
-   During compilation, the compiler has no idea as to which print has to be called since the compiler goes only by referencing variable not by the type of object, and therefore the binding would be delayed to runtime and therefore the corresponding version of the print will be called based on type on an object.


__Static binding is better performance-wise (no extra overhead is required). The compiler knows that all such methods ==cannot be overridden== and will always be accessed by objects of the local class. Hence compiler doesn’t have any difficulty determining the object of the class (local class for sure). That’s the reason binding for such methods is static.__

[[#Static binding]] | [[#Dynamic binding]]
------------ | ------------
It takes place at compile time for which is referred to as early binding | It takes place at runtime so do it is referred to as late binding.
It uses overloading more precisely operator overloading method | It uses overriding methods.
It takes place using normal functions | It takes place using virtual functions
Real objects never use static binding | Real objects use dynamic binding.



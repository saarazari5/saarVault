---
dateCreated: "2022-04-17 19:49"
tags: [java, c, c++ ]
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%
Related Notes: 

# [[Virtual Methods]]
In [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming"), in languages such as [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"), and [Object Pascal](https://en.wikipedia.org/wiki/Object_Pascal "Object Pascal"), a **virtual function** or **virtual method** is an inheritable and overridable function or method for which [dynamic dispatch](https://en.wikipedia.org/wiki/Dynamic_dispatch "Dynamic dispatch") is facilitated. This concept is an important part of the (runtime) [polymorphism](https://en.wikipedia.org/wiki/Polymorphism_(computer_science) "Polymorphism (computer science)") portion of [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming") (OOP). In short, a virtual function defines a target function to be executed, but the target might not be known at compile time.

### The concept of the virtual function solves the following problem:

In [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming"), when a derived class inherits from a base class, an object of the derived class may be referred to via a [pointer](https://en.wikipedia.org/wiki/Pointer_(computer_programming) "Pointer (computer programming)") or [reference](https://en.wikipedia.org/wiki/Reference_(computer_science) "Reference (computer science)") of the base class type instead of the derived class type. If there are base class methods overridden by the derived class, the method actually called by such a reference or pointer can be bound (linked) either 'early' (by the compiler), according to the declared type of the pointer or reference, or 'late' (i.e., by the runtime system of the language), according to the actual type of the object is referred to.

Virtual functions are resolved 'late'. If the function in question is 'virtual' in the base class, the most-derived class's implementation of the function is called according to the actual type of the object referred to, regardless of the declared type of the pointer or reference. If it is not 'virtual', the method is resolved 'early' and selected according to the declared type of the pointer or reference.

Virtual functions allow a program to call methods that don't necessarily even exist at the moment the code is compiled

In C++, _virtual methods_ are declared by prepending the `virtual` keyword to the function's declaration in the base class. This modifier is inherited by all implementations of that method in derived classes, meaning that they can continue to over-ride each other and be late-bound. And even if methods owned by the base class call the virtual method, they will instead be calling the derived method. _Overloading_ occurs when two or more methods in one class have the same method name but different parameters. _Overriding_ means having two methods with the same method name and parameters. Overloading is also referred to as function matching, and overriding as dynamic function mapping.

```c++
class Animal {
 public:
  // Intentionally not virtual:
  void Move() {
    std::cout << "This animal moves in some way" << std::endl;
  }
  virtual void Eat() = 0;
};

// The class "Animal" may possess a definition for Eat if desired.
class Llama : public Animal {
 public:
  // The non virtual function Move is inherited but not overridden.
  void Eat() override {
    std::cout << "Llamas eat grass!" << std::endl;
  }
};

```
For example, a base class `Animal` could have a virtual function `Eat`. Subclass `Llama` would implement `Eat` differently than subclass `Wolf`, but one can invoke `Eat` on any class instance referred to as Animal, and get the `Eat` behavior of the specific subclass.
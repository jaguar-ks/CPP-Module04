# *CPP-Module-04*
---
## **Navigation table:**
1. [Polymorphism in C++.](#polymorphism-in-c)
1. [Types of Polymorphism in C++.](#types-of-polymorphism-in-c)
    1. [Compile Time Polymorphism.](#compile-time-polymorphism)
    1. [Runtime Polymorphism.](#runtime-polymorphism)
1. [Virtual Functions.](#virtual-functions)
1. [VTABLE & VPTR.](#vtable--vptr)
1. [Compile-Time Polymorphism Vs. Run-Time Polymorphism](#compile-time-polymorphism-vs-run-time-polymorphism)
1. [Abstract classes](#abstract-classes)
1. [Interfaces in C++.](#interfaces-in-c)
    1. [Importance of Interfaces.](#importance-of-interfaces)
    1. [Rules While Using Interfaces](#rules-while-using-interfaces)
1. [FinalMark & Author.](#finalmark--author)

---
## **Polymorphism in C++:**
Polymorphism word is the combination of "poly," which means many + "morphs," which means forms, which together means many forms. Polymorphism in C++ is when the behavior of the same object or function is different in different contexts. Let's take a real-world example of the word right can mean different things in a different context.

+ I was right. In the above sentence, the word right means "correct".
+ Please take a right turn. The word right refers to the "right direction" in the above sentence.

---
## **Types of Polymorphism in C++:**
There is two types of Polymorphism:

### ***Compile Time Polymorphism:***
Compile-time polymorphism is done by overloading an operator or function. It is also known as "static" or "early binding".

For example:
```cpp
    #include <iostream>
    using namespace std;

    int Sum( int a, int b ){
        return a + b;
    }
    int Sum( int a, int b, int c ){
        return a + b + c; 
    }

    int main ( void ){
        cout << "The sum of 1 + 2 is: " << Sum(1, 2) << endl;
        cout << "The sum of 1 + 2 + 3 is: " << Sum(1, 2, 3) << endl;
    }
```
the provided code will output:
> The sum of 1 + 2 is: 3
>
> The sum of 1 + 2 + 3 is: 6 

It called compile-time polymorphism because overloaded functions are called by comparing the data types and number of parameters. This type of information is available to the compiler at the compile time.

### ***Runtime Polymorphism:***
Runtime polymorphism occurs when functions are resolved at runtime rather than compile time when a call to an overridden method is resolved dynamically at runtime rather than compile time. It's also known as late binding or dynamic binding.

> Runtime polymorphism is achieved using a combination of function overriding and virtual functions.

---

## **Virtual Functions:**
A virtual function is a member function which is declared within a base class and is overridden by a derived class. Now, when you refer to a derived class object using a pointer to the base class, you can call a virtual function for that object and execute the derived class’s version of that particular function.

The syntax of virtual functions is as follows:

```cpp
    virtual <FuncReturnType> <FuncName> (<Parametes>);
```
>Virtual functions in C++ must be members of some class, also they cannot be static members of the class. Hence, virtual functions belong to the objects of the class, not the class itself, and once they are defined as virtual in the base class no need to be marked as virtual in derived classes, in addition to that functions prototype of a designated as a virtual function must be similar in the base class and all the derived classes.

> Note : Deleting a derived class object using a pointer of base class type that has a non-virtual destructor results in undefined behavior. To correct this situation, the base class should be defined with a virtual destructor. Making base class destructor virtual guarantees that the object of derived class is destructed properly.

---
## **VTABLE & VPTR:**
To accomplish late binding, the compiler creates a single table (called the VTABLE) for each class that contains virtual functions. The compiler places the addresses of the virtual functions for that particular class in the VTABLE. In each class with virtual functions, it secretly places a pointer, called the vpointer (abbreviated as VPTR), which points to the VTABLE for that object. When you make a virtual function call through a base-class pointer (that is, when you make a polymorphic call), the compiler quietly inserts code to fetch the VPTR and look up the function address in the VTABLE, thus calling the right function and causing late binding to take place, this happen in two actions:

+ Every new object created of a class with at least one virtual function defined in it consists of a virtual pointer (VPTR). This virtual pointer is inserted into the newly created object by the C++ compiler, as one of the object’s data members. This virtual pointer points to VTABLE.

+ At the class level, there exists a static data member, namely VTABLE., it belongs to the class, & not its objects is modeled as a static array consisting of function pointers, each array bucket (cell) of VTABLE consisting of a function pointer, points to some virtual function in the class.

![vtables and vptrs](https://www.equestionanswers.com/cpp/images/vptr-vtable-vfunctions.gif)

---

## **Compile-Time Polymorphism Vs. Run-Time Polymorphism:**

| Compile Time | Run Time |
|--------------|----------|
| At Compile time, which functions to be called is decided. | At Runtime, which function to be called is decided. |
| Also known as early or static binding | Also known as late or dynamic binding |
| It executes faster because the function is resolved at compilation time only. | It executes slower because the function is resolved at Run-time. |
| It is achieved through function and operator overloading | t is achieved through function overriding and virtual functions |

---

## **Abstract classes:**
An abstract class is a class that is designed to be specifically used as a base class. An abstract class contains at least one pure virtual function. You declare a pure virtual function by using a pure specifier (= 0) in the declaration of a virtual member function in the class declaration. The classes inheriting the abstract class must provide a definition for the pure virtual function; otherwise, the subclass would become an abstract class itself.

```cpp
    virtual <FuncReturnType> <FuncName> (<Parametes>) = 0; 
```

> Note: The return type of the virtual function must be consistent throughout all of its implementing classes.

---

## **Interfaces in C++:**
Interfaces are nothing but a way to describe the behavior of a class without committing to the implementation of the class. In C++ programming there is no built-in concept of interfaces. In order to create an interface, we need to create an abstract class which is having only pure virtual methods. In C++, Interfaces are also called pure abstract classes.

### ***Importance of Interfaces:***
+ Any class derived from the pure abstract class (Interface) must implement all of the methods of the base class i.e. Interface.
+ Interface pointers can be passed to functions and classes thereby we can call the functions of the derived class from there itself.

## **FinalMark & Author:**

![final-mark](./finalmark.png)

**Author:**[jaguar-ks](https://github.com/jaguar-ks)

lab0 - C++ and Erlang
======================

Task 0
-------

Chose two languages, at least one of these to be Object Oriented (OO). Research and demonstrate in examples (code) how we can use (or simulate if there is no such possibility) core OOP concepts - inheritance, polymorphism, incapsulation. 

#### Encapsulation ####
Generally speaking, encapsulation is the inclusion of one thing within another thing so that the included thing is not apparent.

In **Erlang** is data type named Funs - functions which takes Funs as arguments, or which return Funs are called higher order functions.

Funs encourages us to encapsulate common patterns of design into functional forms called higher order functions. These functions not only shortens programs, but also produce clearer programs because the intended meaning of the program is explicitly rather than implicitly stated. For example:

```erlang
double(L)  -> map(fun(X) -> 2*X end, L).
add_one(L) -> map(fun(X) -> 1 + X end, L).
```

map(F, List) is a function which takes a function F and a list L as arguments and returns the new list which is obtained by applying F to each of the elements in L.

**C++** supports the properties of encapsulation and data hiding through the creation of user-defined types, called classes. By default, all items defined in a class are private. For example:

```cpp
class Box
{
   public:
      double getVolume(void)
      {
         return length * breadth * height;
      }
   private:
      double length;      // Length of a box
      double breadth;     // Breadth of a box
      double height;      // Height of a box
};
```

The variables length, breadth, and height are private. This means that they can be accessed only by other members of the Box class, and not by any other part of your program. This is one way encapsulation is achieved.

#### Inheritance ####

In OOP inheritance is the ability to derive new classes from existing classes. A derived class (or "subclass") inherits the instance variables and methods of the " base class " (or "superclass"), and may add new instance variables and methods. 

A simple example of inheritance in **Erlang**:

```erlang
-module(new_module).
-extends(old_module).
-export([g/1]).
g(X) -> ...
```

'extends' declaration enables inheritance.
All function calls to new_module:f(...) will be redirected to old_module:f(...) if f is not exported from new_module.

A good example of inheritance in **C++** is relationship between employee and manager, where manager can inherit from employee. We can then add any new data and methods needed for a manager and redefine any methods that differ for a manager.

Here, we show a new implementation of Manager that inherits from Employee:

```cpp
#include "employee.h"

class Manager : public Employee {
	public:
	  Manager(string theName,
	          float thePayRate,
	          bool isSalaried);

	  bool getSalaried() const;

	  float pay(float hoursWorked) const;

	protected:
	  bool salaried;
};
```

The line:

```cpp
class Manager : public Employee {
```

causes Manager to inherit all the data and methods of Employee.


#### Polymorphism ####

Polymorphism is ability to present the same interface for different instances (types).

**Erlang** is dynamically typed language, as a result module and even function name could be taken from variable during function call. For example, interfaces of dict and orddict from OTP are unified, and following code shows polymorphism implementation.

```erlang
Module =
       case Ordering of
           unordered ->
               dict;
           ordered ->
               ordict
       end,
Container = Module:from_list(Values),
Module:find(Key, Container).
```

**C++** polymorphism means that a call to a member function will cause a different function to be executed depending on the type of object that invokes the function.

Consider the following example where a base class has been derived by other two classes:

```cpp
class Shape {
   protected:
      int width, height;
   public:
      Shape( int a=0, int b=0)
      {
         width = a;
         height = b;
      }
      virtual int area()
      {
         cout << "Parent class area :" <<endl;
         return 0;
      }
};

class Rectangle: public Shape{
	public:
	  Rectangle( int a=0, int b=0):Shape(a, b) { }
	  int area ()
	  { 
	     cout << "Rectangle class area :" <<endl;
	     return (width * height); 
	  }
};
class Triangle: public Shape{
	public:
	  Triangle( int a=0, int b=0):Shape(a, b) { }
	  int area ()
	  { 
	     cout << "Triangle class area :" <<endl;
	     return (width * height / 2); 
	  }
};
```

The compiler looks at the contents of the pointer. Hence, since addresses of objects of tri and rec classes are stored in *shape the respective area() function is called.

As you can see, each of the child classes has a separate implementation for the function area(). This is how polymorphism is generally used. You have different classes with a function of the same name, and even the same parameters, but with different implementations.

Task 1
-------

Make a free form comparison/analysis of these concepts in your two languages. For example you can use a grid with pros and cons. Max one A4 page. Push your report to public repo and submit link to it.

|Erlang|C++|Criteria of comparisson|
|:---:|:---:|---|
|Yes|No|The semantics of this language are much different than other languages|
|No|Yes|This is a low level language|
|No|Yes|I would use this language for writing programs for embedded hardware platform|
|Yes|No|This language is minimal|
|Yes|Yes|Learning this language improved my ability as a programmer|
|No|Yes|I know many other people who uses this language|
|Yes|Yes|This language is good for begginers|
|No|Yes|This is a mainstream language|
|Yes|Yes|If my code in this language successfully compiles, there is a good chance my code is correct|
|No|Yes|I would use this language for a desktop GUI project|
|Yes|No|This is a high level language|
|No|Yes|There is a wide variety of open source code written in this language|
|No|Yes|I use many applications written in this language|

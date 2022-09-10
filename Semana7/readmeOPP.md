
Object Oriented Programming using Typescript

![1_n64atUMpf_v28pT7DwaVPg](https://user-images.githubusercontent.com/108378310/189500985-df9f2c8d-7023-4908-8a0c-bf723f87dc1c.jpg)

Coding with objects and classes makes the life of a developer easier. Object oriented programming is a methodology to simplify the development of softwares, applications, packages etc. The main pillars of OOPs are:

Class
Object
Inheritance
Polymorphism
Abstraction
Encapsulation
Here we will learn each of these concepts one by one.

Classes and Objects
Let’s consider an analogy of John who wished to build a house. John first approached to an architecture and the architecture gave John a blueprint of the house before beginning the construction or the occurrence of the house.


![1_cRVD88ogFfm05tBgrb0nxg](https://user-images.githubusercontent.com/108378310/189501007-6024c233-d443-4ca9-93af-bf0d611df84d.gif)


Here we can relate the blueprint to a class and after the construction the house will be the object.

Notice the blueprint doesn’t have any space on the earth’s surface whereas the house will have some space on the earth’s surface. Similarly classes don’t consume any space in the memory but objects consume some space in the memory.

Let’s take an example using typescript:


In the above example we have defined a class called Employee which have two members one is “name” of type string another is “age” of type number. On line number 10 we have instantiated an object called emp of type Employee. Since emp is the object of type Employee it must have the name and age property. On line 11 and 12 we are accessing those properties using dot(.) operator.

Note-

Constructor is a special type of method which initialises the object. In above example on line number 10 the two arguments viz. “John” and 24 are passed to the constructor of the class Employee.
“This” is a reference variable that refers to the current object.
Inheritance
It is not efficient to write block of codes over and over again. Developers love code reusability. Inheritance provides code reusability to the developers. It is the mechanism through which a class inherits or acquires properties of another class.

The class from which properties are inherited is called the base/super/parent class and the class which acquires the property is called the derived/child/sub class.

Let’s take an example of an organisation which have managers and area managers. Manager is the base class with four properties viz. ‘firstName’, ‘lastName’, ‘salary’ and ‘email’. AreaManager will also have these four properties along with a new property called ‘area’.

It is clear that if we make a set of the properties of each class then AreaManager will be a superset of Manager. In other words Properties of Manager can be inherited to the AreaManager.


So to reuse the codes/properties of Manager we can inherit it within AreaManager and it can be done using the keyword extends.

note: ‘super’ is a keyword used to call the parent constructor and its value.


output:


Types of Inheritance
Single inheritance
Multilevel Inheritance
Multiple Inheritance
Hierarchical inheritance
Hybrid inheritance
Single Inheritance
When a single class inherits another single class . Above example is a single inheritance.

Multilevel Inheritance

When there is a single chain of inheritance then it is called as multilevel inheritance. In the above example if a new class AreaSupervisor extends class AreaManager then it will be an example of multilevel inheritance.

Multiple Inheritance

When a sub class inherits from more than one base class. Typescript does not support multiple inheritance.

Hierarchical Inheritance

When more than one sub classes are inherited from a single base class.

Hybrid Inheritance

Combination of more than one type of inheritance is called hybrid inheritance. To reduce complexity typescript does not support hybrid inheritance.

Polymorphism
Poly signifies many and meaning of morph is shape, so polymorphism is basically executing a function in many ways. Polymorphism is another way after inheritance to achieve code reusability.

Polymorphism can be achieved by:

Method Overloading
Method Overriding
Method Overloading
In typescript we can have multiple function with the same name using different parameter types and return types. Unlike java, in typescript the number of parameters must be same. Let’s understand this with two examples:


output:


Here, Example is a class containing method add. On line 7 we are trying to overload the function add by changing the parameter type and return type to number. Since we may provide parameter of type string as well as number so in the function definition we provide the parameter type and return type as any. In the output the function add is overloaded and returning us two different outputs.

Now let’s try providing different number of parameters:


output:


Hence it is not allowed in typescript.

Method Overriding
To implement method overriding we must use inheritance and in the child class we provide different definition of functions that have been previously declared in the base class. Let’s take an example:


Output:


In the above example subclass Macbook and subclass DellLaptop both extends base class Laptop. Laptop has a method getOS(). We are overriding this method in both the subclasses by simply defining it uniquely in each time.

Here we clearly see polymorphism where getOS() method is called three times but each time with a different output.

Abstraction
Abstraction is simply hiding internal details and showing functionalities. It lets us focus on what an object does instead of how it does.

Abstraction can be achieved by two ways:

Using abstract class
Using interface
Abstract class
We define an abstract class in typescript using an abstract keyword before the class keyword.
Instance of an abstract class cannot be created. But other classes can be derived from it.
The class which extends an abstract class must define all the abstract methods or properties.
The class which extends abstract class must call super in the constructor.
Let’s take an example:


Output:


Interface
It is a syntax for a class.
It contains only the declaration of methods and properties. Classes implementing an interface must implement all its members and methods.
It cannot be instantiated.
It is used to type-check an object, whether it is followed by a specific structure or not .
Interfaces can be inherited from other interfaces by using extends key word.
Classes use implements keyword to implement an interface.
Let’s take an example:


In the above example interface IEmployee extends interface IUser, shows interfaces can be inherited from other interfaces. Again class Employee implements interface IEmployee.

Now let’s see how interface is helping us to check the type.


Output:


From the above example it is clear that when a class implements an interface it must implement all its member variables and methods and hence the type is checked.

Access Modifiers
To understand encapsulation we must first understand the access modifiers. There are three types of access modifiers in typescript:

Public
Private
Protected
Public
By default all the members of a class are public in typescript that means we can access and modify them outside of the class. Let’s take an example:


Output:


Private
Private members are allowed to access or modify inside the class but not allowed outside of the class. Let’s take an example:


Output:


Here age is a private member which is accessed by the display method which is within the class Employee.

Now let’s see another scenario:


Output:


Here we are trying to access age outside of the class which is not allowed.

Protected
Protected members can be accessed or modified within the class as well as within its child classes. For example:


Output:


Here age is protected but it is accessed and modified through the child class member function display() and modify() respectively.

Encapsulation
Wrapping codes and data into a single unit is called encapsulation. We can achieve it by using the access modifiers. For example we can create a fully encapsulated class by making all its members private.


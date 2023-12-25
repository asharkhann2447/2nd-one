# 2nd-one
Explain the concept of pure virtual functions, abstract base classes and interfaces. Discuss the  role of abstract classes in designing class hierarchies.
Purely virtual features:
A pure virtual function is a function in the base class that has no implementation.
It is declared using the "= 0" syntax in C++.
Classes containing purely virtual functions are called abstract classes.

Abstract Base Classes (ABC):
An abstract base class is a class that cannot be instantiated by itself.
It often contains one or more pure virtual functions that define an interface that derived classes must implement.
Abstract base classes are intended to be subclasses and provide a common interface to a group of related classes.

Interface:
An interface defines a contract for a set of methods that a class must implement.
In languages like Java or C#, interfaces are a way to achieve abstraction and multiple inheritance.
They provide a mechanism to achieve polymorphism by allowing objects of different classes to be treated as objects of a common type.

The role of abstract classes in designing class hierarchies:
Abstract classes serve as blueprints for other classes, define a common interface, and provide some common functionality.
They help achieve abstraction by hiding implementation details from the user.
Abstract classes facilitate code reusability because common methods can be defined in an abstract class and its subclasses can be reused.
They contribute to polymorphism by allowing objects of derived classes to be treated like objects of an abstract base class.

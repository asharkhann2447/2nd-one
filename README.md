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


Question 2:
#include <iostream>
#include <string>

using namespace std;

class Product {
private:
    int productId;
    string productName;
    int price;

public:
    Product() : productId(0), productName(""), price(0) {}

    Product(int id, const string& name, int p) : productId(id), productName(name), price(p) {}

    void displayInfo() const {
        cout << "ID: " << productId << "\nName: " << productName << "\nPrice: $" << price << "\n\n";
    }

    double getPrice() const {
        return price;
    }
};

class ShoppingCart {
private:
    static const int MAX_PRODUCTS = 10;
    int itemCount = 0;
    Product items[MAX_PRODUCTS];

public:
    void addToCart(const Product& product) {
        if (itemCount < MAX_PRODUCTS) {
            items[itemCount++] = product;
        }
    }

    void showAllItems() const {
        for (int i = 0; i < itemCount; ++i) {
            items[i].displayInfo();
        }
    }

    double calculateTotal() const {
        double total = 0.0;
        for (int i = 0; i < itemCount; ++i) {
            total += items[i].getPrice();
        }
        return total;
    }
};

class User {
private:
    int userId;
    ShoppingCart* shoppingCart;

public:
    User(int id) : userId(id), shoppingCart(nullptr) {}

    void displayProfile() const {
        cout << "\tUser ID: " << userId << "\n";
    }

    void assignShoppingCart(ShoppingCart* cart) {
        this->shoppingCart = cart;
    }

    ShoppingCart* getShoppingCart() const {
        return shoppingCart;
    }
};

int main() {
    User customer(1);

    Product item1(10001, "Widget A", 50);
    Product item2(10002, "Gadget B", 120);
    Product item3(10003, "Doodad C", 75);

    ShoppingCart cart;
    cart.addToCart(item1);
    cart.addToCart(item2);
    cart.addToCart(item3);

    customer.assignShoppingCart(&cart);

    customer.displayProfile();
    ShoppingCart* userCart = customer.getShoppingCart();

    userCart->showAllItems();
    cout << "Total Purchase Amount: $" << userCart->calculateTotal() << '\n';

    return 0;
}

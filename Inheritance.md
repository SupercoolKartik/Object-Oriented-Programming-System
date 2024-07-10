**The capability of a** [class] **to derive properties and characteristics from another class is called Inheritance.

Inheritance is a feature or a process in which, new classes are created from the existing classes. The new class created is called “derived class” or “child class” and the existing class is known as the “base class” or “parent class”. The derived class now is said to be inherited from the base class.

When we say derived class inherits the base class, it means, the **derived class inherits all the properties of the base class, without changing the properties of base class and may add new features to its own.** These new features in the derived class will not affect the base class. The derived class is the specialized class for the base class.
- **Sub Class:** The class that inherits properties from another class is called Subclass or Derived Class. 
- **Super Class:** The class whose properties are inherited by a subclass is called Base Class or Superclass.
- **Access Specifiers**: Control the access level of inherited members


#### Syntax of Inheritance
```
class derived_class_name : access-specifier base_class_name
{
       // body ....
};
```
where,
- ***access-specifier****: Specifies the access mode which can be either of private, public or protected. If neither is specified, private is taken as default.

### Example of Inheritance
```
#include <iostream>
#include <string>

using namespace std;

// Base class
class Car {
private:
    string make;
    string model;
    int year;

public:
    // Constructor
    Car(string carMake, string carModel, int carYear)
        : make(carMake), model(carModel), year(carYear) {}

    // Getter for make
    string getMake() const {
        return make;
    }

    // Setter for make
    void setMake(string carMake) {
        make = carMake;
    }

    // Getter for model
    string getModel() const {
        return model;
    }

    // Setter for model
    void setModel(string carModel) {
        model = carModel;
    }

    // Getter for year
    int getYear() const {
        return year;
    }

    // Setter for year
    void setYear(int carYear) {
        if(carYear > 1885 && carYear <= 2024) { // Validation check
            year = carYear;
        } else {
            cout << "Invalid year" << endl;
        }
    }

    // Method to display car details
    void displayInfo() const {
        cout << "Make: " << make << endl;
        cout << "Model: " << model << endl;
        cout << "Year: " << year << endl;
    }
};

// Derived class
class ElectricCar : public Car {
private:
    int batteryCapacity; // Battery capacity in kWh

public:
    // Constructor
    ElectricCar(string carMake, string carModel, int carYear, int batteryCapacity)
        : Car(carMake, carModel, carYear), batteryCapacity(batteryCapacity) {}

    // Getter for battery capacity
    int getBatteryCapacity() const {
        return batteryCapacity;
    }

    // Setter for battery capacity
    void setBatteryCapacity(int capacity) {
        batteryCapacity = capacity;
    }

    // Method to display electric car details
    void displayInfo() const {
        Car::displayInfo(); // Call base class method
        cout << "Battery Capacity: " << batteryCapacity << " kWh" << endl;
    }
};

int main() {
    ElectricCar eCar("Tesla", "Model S", 2023, 100);

    eCar.displayInfo();

    return 0;
}

```


### Benefits of Inheritance
- **Code Reuse**: Allows existing classes to be reused, avoiding redundancy.
- **Extensibility**: Existing classes can be extended with new functionalities.
- **Hierarchy Representation**: Represents hierarchical relationships naturally.
	(Hierarchical representation in inheritance refers to the natural way of representing relationships between classes where multiple derived classes inherit from a single base class. This structure mimics real-world hierarchies, making it easier to model and understand complex relationships between different entities in a system.)


## Modes of Inheritance
Mode of inheritance controls the access level of the inherited members of the base class in the derived class. In C++, there are 3 modes of inheritance:

- **Public Mode**
- **Protected Mode**
- **Private Mode**

***Let this example of Base Class***
```
#include <iostream>
using namespace std;

class Base {
public:
    int publicVar;
protected:
    int protectedVar;
private:
    int privateVar;
};

```

##### 1. Public Inheritance
- **Public members of the base class** become **public members of the derived class**.
- **Protected members of the base class** become **protected members of the derived class**.
- **Private members of the base class** are not directly accessible by the derived class but can be accessed through public or protected member functions of the base class.

```
class DerivedPublic : public Base {
public:
    void display() {
        cout << "PublicVar: " << publicVar << endl;        // Accessible
        cout << "ProtectedVar: " << protectedVar << endl;  // Accessible
        // cout << "PrivateVar: " << privateVar << endl;  // Not accessible
    }
};

int main() {
    DerivedPublic obj;
    obj.publicVar = 10;  // Accessible
    // obj.protectedVar = 20;  // Not accessible
    obj.display();
    return 0;
}
```

##### 2. Protected Inheritance
- **Public members of the base class** become **protected members of the derived class**.
- **Protected members of the base class** remain **protected members of the derived class**.
- **Private members of the base class** are not directly accessible by the derived class but can be accessed through public or protected member functions of the base class.

```
class DerivedProtected : protected Base {
public:
    void display() {
        cout << "PublicVar: " << publicVar << endl;        // Accessible
        cout << "ProtectedVar: " << protectedVar << endl;  // Accessible
        // cout << "PrivateVar: " << privateVar << endl;  // Not accessible
    }
};

int main() {
    DerivedProtected obj;
    // obj.publicVar = 10;  // Not accessible
    // obj.protectedVar = 20;  // Not accessible
    obj.display();
    return 0;
}

```

#### 3. Private Inheritance

- **Public members of the base class** become **private members of the derived class**.
- **Protected members of the base class** become **private members of the derived class**.
- **Private members of the base class** are not directly accessible by the derived class but can be accessed through public or protected member functions of the base class.

```
class DerivedPublic : public Base {
public:
    void display() {
        cout << "PublicVar: " << publicVar << endl;        // Accessible
        cout << "ProtectedVar: " << protectedVar << endl;  // Accessible
        // cout << "PrivateVar: " << privateVar << endl;  // Not accessible
    }
};

int main() {
    DerivedPublic obj;
    obj.publicVar = 10;  // Accessible
    // obj.protectedVar = 20;  // Not accessible
    obj.display();
    return 0;
}
```


**Note:** The main difference between protected inheritance and private inheritance in C++ is the accessibility of the inherited members to further derived classes. Both modes make the public and protected members of the base class inaccessible to non-member functions and non-friend classes of the derived class, but they differ in how they allow further inheritance.



**Here’s a summary of how members are inherited under different modes:**

| **Base Class Member** | **Public Inheritance** | **Protected Inheritance** | **Private Inheritance** |     |
| --------------------- | ---------------------- | ------------------------- | ----------------------- | --- |
| **Public**            | Public                 | Protected                 | Private                 |     |
| **Protected**         | Protected              | Protected                 | Private                 |     |
| **Private**           | N/A                    | N/A                       | N/A                     |     |

**Note:** Private mode is the default mode that is applied when we don’t specify any mode.
**Note:** In practice, public inheritance is the most commonly used mode, as it clearly expresses an "is-a" relationship between the base and derived classes.


## Types of Inheritance
The inheritance can be classified on the basis of the relationship between the derived class and the base class. In C++, we have 5 types of inheritances:

1. **Single inheritance***
2. **Multilevel inheritance***
3. **Multiple inheritance***
4. **Hierarchical inheritance***
5. **Hybrid inheritance***

#### 1. Single Inheritance
In single inheritance, a class is allowed to inherit from only one class. i.e. one base class is inherited by one derived class only.
  or
A derived class inherits from only one base class.

```
  +------+
  | Base |
  +------+
	 |
	 v
+-----------+
|  Derived  |
+-----------+

```

**Example**
```
#include <iostream>
using namespace std;

class Base {
public:
    void display() {
        cout << "Base class" << endl;
    }
};

class Derived : public Base {
};

int main() {
    Derived obj;
    obj.display();  // Outputs: Base class
    return 0;
}

```

#### 2. Multiple Inheritance
Multiple Inheritance is a feature of C++ where a class can inherit from more than one class.
  or
A derived class inherits from more than one base class.

```
+-------+    +-------+
| Base1 |    | Base2 |
+-------+    +-------+
     \          /
      \        /
       v      v
     +---------+
     | Derived |
     +---------+

```

**Syntax**
```
class Derived : public Base1, public Base2 { };
```

**Example**
```
#include <iostream>
using namespace std;

class Base1 {
public:
    void display1() {
        cout << "Base1 class" << endl;
    }
};

class Base2 {
public:
    void display2() {
        cout << "Base2 class" << endl;
    }
};

class Derived : public Base1, public Base2 {
};

int main() {
    Derived obj;
    obj.display1();  // Outputs: Base1 class
    obj.display2();  // Outputs: Base2 class
    return 0;
}

```

#### 3. Multilevel Inheritance
In this type of inheritance, a derived class is created from another derived class and that derived class can be derived from a base class or any other derived class. There can be any number of levels, forming a chain of inheritance.

```
  +------+
  | Base |
  +------+
     |
     v
+----------+
| Derived1 |
+----------+
     |
     v
+----------+
| Derived2 |
+----------+

```

**Example**
```
#include <iostream>
using namespace std;

class Base {
public:
    void display() {
        cout << "Base class" << endl;
    }
};

class Derived1 : public Base {
};

class Derived2 : public Derived1 {
};

int main() {
    Derived2 obj;
    obj.display();  // Outputs: Base class
    return 0;
}

```


#### 4. Hierarchical Inheritance
In this type of inheritance, more than one subclass is inherited from a single base class. i.e. more than one derived class is created from a single base class.

```
        +------+
        | Base |
        +------+
         /    \
        v      v
+----------+  +----------+
| Derived1 |  | Derived2 |
+----------+  +----------+

```

**Example**
```
#include <iostream>
using namespace std;

class Base {
public:
    void display() {
        cout << "Base class" << endl;
    }
};

class Derived1 : public Base {
};

class Derived2 : public Base {
};

int main() {
    Derived1 obj1;
    Derived2 obj2;
    obj1.display();  // Outputs: Base class
    obj2.display();  // Outputs: Base class
    return 0;
}

```


#### 5. Hybrid Inheritance
Hybrid Inheritance is implemented by combining more than one type of inheritance. 
For example: Combining Hierarchical inheritance and Multiple Inheritance will create hybrid inheritance in C++

There is no particular syntax of hybrid inheritance. We can just combine two of the above inheritance types.

```
       +--------+       +--------+
       | Base 1 |       | Base 2 |
       +--------+       +--------+
      /         \        / 
     v           v      v
+----------+    +----------+
| Derived1 |    | Derived2 |
+----------+    +----------+
     \          /
      v        v
     +----------+
     | Derived3 |
     +----------+
```

**Example**
```
#include <iostream>
using namespace std;

class Base {
public:
    void display() {
        cout << "Base class" << endl;
    }
};

class Derived1 : virtual public Base {
};

class Derived2 : virtual public Base {
};

class Derived3 : public Derived1, public Derived2 {
};

int main() {
    Derived3 obj;
    obj.display();  // Outputs: Base class
    return 0;
}

```


## Inheritance ambiguity

**Inheritance ambiguity** in object-oriented programming occurs when a derived class inherits from multiple base classes that have members with the same name. This creates confusion for the compiler, as it is unable to determine which member to use in the derived class. In C++, this typically happens in scenarios involving multiple inheritance.

To resolve the ambiguity, we can use the scope resolution operator to specify which `show()` function we want to call.

```
#include <iostream>
using namespace std;

class Base1 {
public:
    void show() {
        cout << "Base1 show" << endl;
    }
};

class Base2 {
public:
    void show() {
        cout << "Base2 show" << endl;
    }
};

class Derived : public Base1, public Base2 {
public:
    void show() {
        Base1::show();  // Explicitly call Base1's show()
        Base2::show();  // Explicitly call Base2's show()
    }
};

int main() {
    Derived d;
    d.show();  // No ambiguity now
    return 0;
}

```



> Next topic -> [[Polymorphism]]
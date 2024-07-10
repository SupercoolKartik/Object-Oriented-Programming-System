Shallow copy and deep copy are two concepts related to copying objects, often encountered in object-oriented programming (OOP). They refer to different ways of copying the contents of an object, especially when the object contains dynamically allocated memory.



### *Shallow Copy*
- Shallow copy is a simple copying mechanism where **only the top-level structure of the object is duplicated**, not the contents.
- If the object contains pointers to dynamically allocated memory, **only the memory addresses (pointers) are copied**, **not the actual data pointed to by those pointers**
- As a result, multiple objects end up sharing the same dynamically allocated memory, which can lead to issues if one object modifies the shared data. Modification **modifications to one object can affect the others**
- Default copy constructor always performs shallow copy


```

#include <iostream>
#include <string>

using namespace std;

class Car {
private:
    string* make; // Pointer to dynamically allocated memory
    string model;
    int year;

public:
    // Constructor
    Car(string carMake, string carModel, int carYear) {
        make = new string(carMake); // Allocate memory for make and copy the string
        model = carModel;
        year = carYear;
    }

    // Copy constructor (shallow copy)
    Car(const Car& other) {
        make = other.make; // Shallow copy of pointer
        model = other.model;
        year = other.year;
    }

    // Destructor
    ~Car() {
        delete make; // Release dynamically allocated memory
    }

    // Method to display information about the car
    void displayInfo() {
        cout << "Make: " << *make << endl;
        cout << "Model: " << model << endl;
        cout << "Year: " << year << endl;
    }
    // Method to update the car's make
    void updateMake(string newMake) {
        *make = newMake;
    }
};

int main() {
    // Create a Car object
    Car originalCar("Toyota", "Camry", 2022);

    // Create a shallow copy of the original car
    Car copiedCar = originalCar;

    // Modify the original car's make
    originalCar.updateMake("Honda");

    // Display information about the original car
    cout << "Original Car:" << endl;
    originalCar.displayInfo();                  //-------> Returns Honda

    // Display information about the copied car
    cout << "\nCopied Car:" << endl;
    copiedCar.displayInfo();                   //-------> Also returns Honda

    return 0;
}

```


### *Deep Copy*
- Deep copy, on the other hand, is a more **complex copying mechanism** where **both the top-level structure and the contents of the object are duplicated.**
- If the object contains pointers to dynamically allocated memory, **a new memory block is allocated for each pointer, and the data is copied from the original memory to the new memory**.
- As a result, **each object has its own independent copy of the data**, and **modifications to one object do not affect the others**.

```

#include <iostream>
#include <string>

using namespace std;

class Car {
private:
    string* make; // Pointer to dynamically allocated memory
    string model;
    int year;

public:
    // Constructor
    Car(string carMake, string carModel, int carYear) {
        make = new string(carMake); // Allocate memory for make and copy the string
        model = carModel;
        year = carYear;
    }

    // Copy constructor (deep copy)
    Car(const Car& other) {
        make = new string(*(other.make)); // Deep copy of string
        model = other.model;
        year = other.year;
    }

    // Destructor
    ~Car() {
        delete make; // Release dynamically allocated memory
    }

    // Method to display information about the car
    void displayInfo() {
        cout << "Make: " << *make << endl;
        cout << "Model: " << model << endl;
        cout << "Year: " << year << endl;
    }
    
    // Method to update the car's make
    void updateMake(string newMake) {
        *make = newMake;
    }
};

int main() {
    // Create a Car object
    Car originalCar("Toyota", "Camry", 2022);

    // Create a deep copy of the original car
    Car copiedCar = originalCar;

    // Modify the original car's make
    originalCar.updateMake("Honda");

    // Display information about the original car
    cout << "Original Car:" << endl;
    originalCar.displayInfo();                     //------> Returns Honda

    // Display information about the copied car
    cout << "\nCopied Car:" << endl;
    copiedCar.displayInfo();                      //------> Still returns Toyota

    return 0;
}

```



> Next topic -> [[Copy Assignment Operator]]
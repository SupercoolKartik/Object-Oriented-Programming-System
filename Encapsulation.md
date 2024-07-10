
Encapsulation is a fundamental concept in object-oriented programming (OOP) which is **defined as the wrapping up of data (variables/states) and methods (functions/behaviors) that operate on that data into a single unit or class**. It also involves restricting direct access to some of an object's components, which is a means of preventing unintended interference and misuse of the data. Encapsulation is often achieved through the use of [[access specifiers]]: private, protected, and public.

Encapsulation uses [[access specifiers]] to control visibility. Public methods are provided to access and modify private data members, often called **getter** and **setter** methods.

Consider **a real-life example of encapsulation**, in a company, there are different sections like the accounts section, finance section, sales section, etc. Now,
- The finance section handles all the financial transactions and keeps records of all the data related to finance.
- Similarly, the sales section handles all the sales-related activities and keeps records of all the sales.
Now there may arise a situation when for some reason an official from the finance section needs all the data about sales in a particular month.
In this case, he is not allowed to directly access the data of the sales section. He will first have to contact some other officer in the sales section and then request him to give the particular data.
This is what **Encapsulation** is. Here the data of the sales section and the employees that can manipulate them are wrapped under a single name “sales section”.

**==Q. What is Fully Encapsulated Class?==**
A fully encapsulated class in object-oriented programming is one **where all the data members (variables) are private, and access to these members is only possible through public methods (getter and setter functions)**. This ensures that the internal state of the object can only be modified in a controlled manner.


### Two Important  property of Encapsulation

1. **Data Protection:** Encapsulation protects the [[internal state of an object]] by keeping its data members private. Access to and modification of these data members is restricted to the class’s public methods, **ensuring controlled and secure data manipulation**.
2. **Information Hiding:** Encapsulation hides the internal implementation details of a class from external code. Only the public interface of the class is accessible, providing abstraction and simplifying the usage of the class while allowing the internal implementation to be modified without impacting external code.



### Features of Encapsulation

Below are the features of encapsulation:

1. By encapsulation, we can make the class read-only (by making only getters and not setters for the data members). 
2. The **function which we are making inside the class must use only member variables**, only then it is called encapsulation.
3. **If we don’t make a function inside the class which is using the member variable of the class then we don’t call it encapsulation**.
4. Encapsulation **improves readability, maintainability, and security** by grouping data and methods together. The code is also an advantage of encapsulation.
5. It helps to control the modification of our data members (Allows controlled modification).
6. We can not access any function from the class directly. We need an object to access that function that is using the member variables of that class. 
7. Encapsulated code is better for unit testing.



```

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
        year = carYear;
    }

    // Method to display car details
    void displayInfo() const {
        cout << "Make: " << make << endl;
        cout << "Model: " << model << endl;
        cout << "Year: " << year << endl;
    }
};
//The class above is a fully encapsulated class

int main() {
    Car car1("Toyota", "Camry", 2022);
    
	cout<<car1.getYear()<<endl;
	
    car1.displayInfo();

    // Modifying the car details using setters
    car1.setMake("Honda");
    car1.setModel("Accord");
    car1.setYear(2023);

    car1.displayInfo();

    return 0;
}

```



> Next topic -> [[Inheritance]]


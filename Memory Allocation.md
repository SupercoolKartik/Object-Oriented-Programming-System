
### Static Allocation

Static allocation usually refers to objects that are created at compile time and have a fixed lifetime throughout the program's execution. i.e. these objects are allocated memory when the program starts and deallocated when the program terminates.
The size and lifetime of objects with static allocation are fixed and determined at compile time. 

The programmer does not have direct control over the memory allocation and deallocation process during program execution.

Static allocation is suitable for objects whose size and lifetime are known at compile time and do not need to be dynamically managed("Dynamically managed" refers to the ability to allocate and deallocate memory for objects dynamically at runtime based on program logic and requirements).

In static allocation, objects are created as regular variables

```
// Static allocation of Car objects 
Car car1("Toyota", "Camry", "Blue", 2022); 
Car car2("Honda", "Accord", "Red", 2023);
```



### Dynamic Allocation

- Dynamic allocation in OOP involves creating objects at runtime and allocating memory from the [[heap]].
-  Objects with dynamic allocation are created using pointers and are allocated memory using `new` (in C++) or `malloc()` (in C).
-  These objects have a variable lifetime and are deallocated explicitly using `delete` (in C++) or `free()` (in C) when they are no longer needed.

In dynamic allocation, memory for objects is allocated and deallocated explicitly at runtime using functions like `new` (in C++) or `malloc()` (in C). This means that the programmer has control over when memory is allocated and deallocated for objects. Objects with dynamic allocation have a variable lifetime, and their memory usage can be controlled dynamically during program execution.



```
// Dynamic allocation of Car objects
Car *car1 = new Car("Toyota", "Camry", "Blue", 2022); //Set values while declaring
Car *car2 = new Car(); //Or just declare and set the values later

(*car1).displayInfo();
	or
car1->displayInfo();

//Get/Set/Change

car1->year = 1998;
car2->year = 2000;

// Deallocate memory 
delete car1;
delete car2;
```


> Next topic -> [[Constructor]]
Flexibility in code means that you can write generic code that can handle new requirements or changes with minimal modifications.

#### Example:
Imagine you have a drawing application that needs to support different shapes. You can create a base class `Shape` and derive different shape classes from it.

```
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void draw() {
        cout << "Drawing Shape" << endl;
    }
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing Circle" << endl;
    }
};

class Square : public Shape {
public:
    void draw() override {
        cout << "Drawing Square" << endl;
    }
};

void renderShape(Shape* shape) {
    shape->draw();
}

int main() {
    Circle circle;
    Square square;

    renderShape(&circle); // Calls Circle::draw()
    renderShape(&square); // Calls Square::draw()

    return 0;
}
```


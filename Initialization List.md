Initializer List is used in initializing the data members of a class. The list of members to be initialized is indicated with constructor as a comma-separated list followed by a colon. Following is an example that uses the initializer list to initialize x and y of Point class.

```
#include <iostream>
using namespace std;

class Point {
private:
	int x;
	int y;

public:
	Point(int i = 0, int j = 0) : x(i), y(j) {}
	
	/* The above use of Initializer list is optional as 
		the constructor can also be written as:
		Point(int i = 0, int j = 0) {
			x = i;
			y = j;
		}
	*/

	int getX() const { return x; }
	int getY() const { return y; }
};

int main()
{
	Point t1(10, 15);
	
	cout << "x = " << t1.getX() << ", ";
	cout << "y = " << t1.getY();
	
	return 0;
}

```



> Next topic -> [[Constant Keyword]]
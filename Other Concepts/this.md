this is a pointer which stores the address of the current object
h1 in this case

```
class Hero {
private:
    char level;
    int health;
    

public:
	char name;

	//Getter functions for health and level
    int getHealth() {
        return health;
    }

    char getLevel() {
        return level;
    }

	//Setter functions for health and level
    void setHealth(int val) {
        this->health = val;
    }

    void setLevel(char val) {
        this->level = val;
    }
    
};
int main(){
	Hero h1;
	h1.sethealth(35);
}


```
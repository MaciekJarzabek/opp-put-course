#include <iostream>
using namespace std;

class Fruit {
public:
	Fruit() {};
	virtual string Name() const = 0;
	virtual int Calories() const = 0;
};

class Apple : public Fruit {
private:
	const string name;
	const int calories;

public:
	Apple(string name, int calories) : name(name), calories(calories) {}

	string Name() const override {
		return name;
	}

	int Calories() const override {
		return calories;
	}
};

int main() {
	Apple apple("Red", 997);
	cout <<  apple.Name() << " apple with " << apple.Calories() << " calories." << endl;
	return 0;
}


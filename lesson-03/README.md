# This directory contains solution to the lesson-03
#include <iostream>
#include <string>
#include <functional>

using namespace std;

class Glass {
private:
	string level;

public:
	Glass Fill(string newLevel) {
		this->level = move(newLevel);
		return *this;
	}
	string CurrentLevel() {
		return this->level;
	};
};

class Human{
private:
	string name;
	Glass* glasses[10];
	int count;

public:
	void HumanName(string HumanNewName) {
		this->name = move(HumanNewName);
	}
	void DrinkFromGlass(const Glass& glass) {
		this->humanGlasses->push_back(glass);
	}
	Glass PutAwayGlass() {
		Glass putAsideByHuman = this->humanGlasses->back();
		this-> HumanGlasses->pop_back();
		return putAsideByHuman;
	}

};

int main()
{
	Human Sam;
	Sam.HumanName("Smith");
	Glass glass;
	Glass newGlass = Glass.Fill("Full");
	Sam.DrinkFromGlass(newGlass);
	Glass emptyGlass = Sam.PutAwayGlass();
	cout << emptyGlass.CurrentLevel();

	return 0;

}

#include <iostream>
#include <stdio.h>

using namespace std;

class Nature {
public:
	int trees;

};

class People {
public:
	int Americans;

};

class Animal {
public:
	int Dogs;

};

int main()
{
	Nature* Pine = new Nature;
	People* Simon = new People;
	Animal* Husky = new Animal;
	Pine->trees = 21;
	Simon->Americans = 32;
	Husky->Dogs = 11;
	cout << "The world presents you with many trees" << endl;
	cout << "The world offers many new acquaintances" << endl;
	cout << "The dog is man's best friend" << endl;

	return 0;
}

#include <iostream>
using namespace std;

class Person {
private:
	string name;
	int age;
	string address;
public:
	Person() : Person("Julian", 2137, "ul. Ulanow 69") {}

	Person(string n, int a) : Person(n, a, "") {}

	Person(string n, int a, string addr) : name(n), age(a), address(addr) {}

	void printInfo() {
		cout << "Name: " << name << endl;
		cout << "Age: " << age << endl;
		cout << "Address: " << address << endl;
	}
};

int main() {
	
	Person person1;
	Person person2("Szymon", 5, "ul. Wyszynskiego 2/2" );
	Person person3("Zuzanna", 30);

	
	person1.printInfo();
	cout << endl;
	person2.printInfo();
	cout << endl;
	person3.printInfo();

	return 0;
}

# This directory contains solution to the lesson-07
#include <iostream>
#include <cmath>
#include <stdexcept>
using namespace std;

class Logarithm {
public:
	Logarithm(double base, double number) {
		base_ = base;
		number_ = number;
	}

	double Calculate() const {
		try {
			return log(number_) / log(base_);
		}
		catch (const exception & e) {
			cerr << "Error calculating logarithm: " << e.what() << endl;

		}
	}

private:
	double base_;
	double number_;
};

class InvalidBaseException : public invalid_argument {
public:
	InvalidBaseException() : invalid_argument("Invalid base: logarithm base must be greater than 0 and not equal to 1") {}
};

class InvalidNumberException : public invalid_argument {
public:
	InvalidNumberException() : invalid_argument("Invalid number: logarithm number must be greater than 0") {}
};

int main() {
	double base, number;
	cout << "Enter the base: ";
	cin >> base;
	cout << "Enter the number: ";
	cin >> number;

	try {
		Logarithm log(base, number);
		double result = log.Calculate();
		cout << "log_" << base << "(" << number << ") = " << result << endl;
	}
	catch (const InvalidBaseException & e) {
		cerr << "Invalid base: " << e.what() << endl;
	}
	catch (const InvalidNumberException & e) {
		cerr << "Invalid number: " << e.what() << endl;
	}
	catch (const exception & e) {
		cerr << "Error: " << e.what() << endl;
	}

	return 0;
}

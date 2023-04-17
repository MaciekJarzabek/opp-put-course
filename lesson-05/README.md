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


//zad2*
#include <iostream>
using namespace std;
#include <map>

class Cantor {
public:
	Cantor() = default;
	virtual ~Cantor() = default;

	virtual double Rate(const std::string& abbreviation) const = 0;
};

class Currency {
public:
	Currency() = default;
	virtual ~Currency() = default;

	virtual double ConvertedToDollars(const Cantor& cantor) const = 0;
	virtual std::string Abbreviation() const = 0;
	virtual double Amount() const = 0;
};

class FakeUsdCantor : public Cantor {
public:
	FakeUsdCantor() {
		// rates_ map with values for ten most popular currencies relative to USD
		rates_ = {
		  {"EUR", 0.85},
		  {"JPY", 110.66},
		  {"GBP", 0.73},
		  {"CHF", 0.91},
		  {"CAD", 1.25},
		  {"AUD", 1.34},
		  {"CNY", 6.47},
		  {"HKD", 7.78},
		  {"NZD", 1.44},
		  {"KRW", 1153.89}
		};
	}

	double Rate(const std::string& abbreviation) const override {
		auto it = rates_.find(abbreviation);
		if (it != rates_.end()) {
			return it->second;
		}
		// Handle error case when currency abbreviation is not found
		return 0.0;
	}

private:
	std::map<std::string, double> rates_;
};

class Euro {

public:
	Euro(string currency_abbreviation, double amount) {
		this-> currency_abbreviation = currency_abbreviation;
		this-> amount = amount;
	}

	string Abbreviation (){
		return "EUR";
	}

	double ConvertedToDollars(const Cantor& cantor) {
		double exchangeRate = cantor.Rate(Abbreviation());
		return amount / exchangeRate;
	}

	double Amount() {
		return 100;
	}

private:
	string currency_abbreviation;
	double amount;

};

int main() {
	return 0;
}


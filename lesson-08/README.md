#include <iostream>
#include <vector>
#include <string>

using namespace std;

class Product {
private:
	string name;
	int id;

public:
	Product(string name, int id) : name(name), id(id) {}

	string Name() const {
		return name;
	}

	int Id() const {
		return id;
	}
};

class Customer {
private:
	string name;
	string email;
	int customerId;
	vector<Product> products;

public:
	Customer(string name,string email, int customerId) : name(name),email(email), customerId(customerId) {}

	string Name() const {
		return name;
	}

	string Email() const {
		return email;
	}

	int CustomerId() const {
		return customerId;
	}

	void addProduct(Product product) {
		products.push_back(product);
	}

	vector<Product> Products() const {
		return products;
	}
};

class Order {
private:
	int orderId;
	vector<Product> products;

public:
	Order(int orderId) : orderId(orderId) {}

	int OrderId() const {
		return orderId;
	}

	void addProduct(Product product) {
		products.push_back(product);
	}

	vector<Product> Products() const {
		return products;
	}

	float TotalCost() const {
		float totalCost = 0.0;
		for (auto product : products) {
			totalCost += 4.0; 
		}
		return totalCost;
	}
};

int main() {
	// tworzenie klientów i ich id
	Customer alice("Alice","alice@gmail.com", 1);
	Customer mark("Mark","mark@gmail.com", 2);

	//tworzenie produktów
	Product book("Book", 123);
	Product laptop("Laptop", 456);

	// dodawanie produktów do listy konkretnego klienta
	alice.addProduct(book);
	mark.addProduct(laptop);

	// tworzenie zamówienia 1-ego klienta
	Order aliceOrder(1);
	for (auto product : alice.Products()) {
		aliceOrder.addProduct(product);
		aliceOrder.addProduct(product);
	}

	//tworzenie zamówienia 2-ego klienta
	Order markOrder(2);
	for (auto product : mark.Products()) {
		markOrder.addProduct(product);
	}

	
	cout << "Alice's order total cost: $" << aliceOrder.TotalCost() << endl;
	cout << "Marks's order total cost: $" << markOrder.TotalCost() << endl;

	return 0;
}

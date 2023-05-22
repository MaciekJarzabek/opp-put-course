# This directory contains solution to the lesson-09

#include <fstream>
#include <iostream>
#include <memory>
#include <vector>
#include <algorithm>
#include <cctype>
#include <string>
using namespace std;

class IntegerSequence {
public:
	virtual vector<int> Numbers() = 0;
};

class VectorSequence : public IntegerSequence {
private:
	vector<int> sequence;
public:
	VectorSequence(vector<int> numbers) : sequence(numbers) {}

	vector<int> Numbers() override {
		return sequence;
	}
};



class PositiveSequence : public IntegerSequence {
private:
	shared_ptr<IntegerSequence> sequence;
public:
	PositiveSequence(shared_ptr<IntegerSequence> seq) : sequence(seq) {}

	vector<int> Numbers() override {
		auto numbers = sequence->Numbers();
		numbers.erase(remove_if(numbers.begin(), numbers.end(), [](int num) { return num < 0; }), numbers.end());
		return numbers;
	}
};

class SortedSequence : public IntegerSequence {
private:
	shared_ptr<IntegerSequence> sequence;
public:
	SortedSequence(shared_ptr<IntegerSequence> seq) : sequence(seq) {}

	vector<int> Numbers() override {
		auto numbers = sequence->Numbers();
		sort(numbers.begin(), numbers.end());
		return numbers;
	}

};

class EvenSequence : public IntegerSequence {
private:
	shared_ptr<IntegerSequence> sequence;
public:
	EvenSequence(shared_ptr<IntegerSequence> seq) : sequence(seq) {}
	
	vector<int> Numbers() override {
		auto numbers = sequence->Numbers();

		return numbers;
	}
};

int main() {
		vector<int> input_Sequence = { 3,4,61,-3,0,1,14 };
		
		for (int i : numbers) {
			cout << i << " ";
		}
		return 0;
	
}

# This directory contains solution to the lesson-06
#include <iostream>
#include <sstream>
#include <memory>
#include <string>
#include <cassert>
using namespace std;

class Sequence {
public:
	virtual int Length() = 0;
};

class FakeSequence : public Sequence {
public:
	int Length() override { return 100; }
};

class Gene {
private:
	string name_;
	shared_ptr<Sequence> sequence_;

public:
	Gene(shared_ptr<Sequence> sequence, string name)
		: sequence_(sequence), name_(name) {}

	void JSON() {
		cout << "{ \"name\": \"" << name_ << "\", \"length\": " << sequence_->Length() << " }" << endl;
	}
};

int main() {
	shared_ptr<Sequence> fake_seq = make_shared<FakeSequence>();
	Gene gene("BALF5",fake_seq);
	cout << gene.JSON() << endl;

	return 0;
}

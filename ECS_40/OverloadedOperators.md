## Overloaded Operators ##

Quite a few of the questions that I get from ECS 40 students are about overloaded operators. So I thought I'd try to talk about them in my own words. Even I had some difficulty trying to understand these things when I first had to learn about them.

### Why use overloaded operators? ###

Yes, you don't really need to use overloaded operators and could do all the operations you want without them. However, they can make your code much easier to read and your classes much easier for someone else to use.

Say, for example, you have a class that represents a bank account (don't mind the bad programming style, I just like to have correct code):

	class BankAccount
	{
		public:
			double getAmount() { return amount; }
			void setAmount(double newAmount) { amount = newAmount; }
		private:
			double amount;
	};

And then in your program, you combine the amounts of money in two accounts into one. Wouldn't it be nice if you could write your code in the following way?

	BankAccount b1, b2, b3;
	b1.setAmount(1000);
	b2.setAmount(1337);
	b3 = b1 + b2; // in which b3.amount == 2337

Never mind that I just created money out of thin air.

### So how do I implement an overloaded operator? ###

Overloaded operators are just functions with special names. Like normal functions you are probably used to writing, you have to specify a return value, parameters, and code to be executed when they are called. You just need to use the keyword `operator` and the symbol of the operator you want to overload as the function name.

To make the code that I wrote above work, here's one way I could overload the plus operator:

	BankAccount::BankAccount operator+(const BankAccount& rhs)
	{
		BankAccount temp;
		temp.amount = this->amount + rhs.amount;
		return temp;
	}

The function would be a class method of the `BankAccount` class. This is why we can directly use `amount`, since the class itself definitely should have access to its own private data members. No need for those getter and setter methods that we are forced to write to preserve abstraction, and that you would have to use to perform the operation outside of the class if you didn't do operator overloading. 

The other thing that might seem a little confusing is the use of the `this` pointer. Notice how we have the operand on the right hand side of the expression as a parameter, but not the left? The left operand is actually the object that "calls" the overloaded operator, so we can access its data by using the `this` pointer. 

The reason why the return value is a `BankAccount` is because of our assignment statement. The variable `b3` is a `BankAccount`, so the operand on the right hand side of the assignment operator should also be a `BankAccount`. 

### Another Way ###

What happens if you want to define the overloaded operator as a non-member function, or if the left hand side of the expression is not an instantiation of the class? No problem, here's another way to implement it:

	BankAccount operator+(const BankAccount& lhs, const BankAccount& rhs)
	{
		BankAccount temp;
		temp.amount = lhs.amount + rhs.amount;
		return temp;
	}

Looks almost the same, except there is another parameter: the left operand of the expression. Since this is not a class method, it is not declared as such. However, to have access to the private data members of the `BankAccount` class, this function must be declared as a friend function within the class definition:

	class BankAccount
	{
		public:
			double getAmount() { return amount; }
			void setAmount(double newAmount) { amount = newAmount; }
			friend BankAccount operator+(const BankAccount& lhs, const BankAccount& rhs);
		private:
			double amount;
	};

### Further ###

So I will not go into details about how to overload all of the operators; there are just way too many to count and there is a thing called the Internet that has many resources in which you can consult. There are also subtleties that come with implementing some of the other operators (e.g., overloading the assignment operator and dealing with self assignment). But hopefully this helps, and you won't be as intimidated to implement your own overloaded operators. :D
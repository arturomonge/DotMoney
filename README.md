# Money Value Type W.I.P. #

## Introduction

A Money value type designed for C#, noted that since it is designed to be immutable-alike, you may need to cocnern about performance when doing long calculation on Money objects.

### Features

- Provides a `Money` class encapsulates all information and allow for dynamic formatting based its own internal Currency setup.
- By design, most fields are ready-only, means each Money object is fixed when instantiated, as in the real world, Money can not change its form or currency type after it is created, computation and conversion are allowed but they will always produce a new Money object.
- Provides a `Currency` class served as both the decorating class for Money displaying operation and a standalone class.
- Currency types definition is defined in a separate respository, which means developer can add more types as needed.
- Support digital currencies (ex.Bitcoin, Litecoin) and currency sub-type display and definition.
- (Will be more later...)

### Resources

- Structure based on: https://github.com/dewe/Money
- Currency repository based on: http://www.lindelauf.com/?p=17http://www.codeproject.com/Articles/28244/A-Money-type-for-the-CLR?msg=3679755
- Good reference: http://github.com/RubyMoney/money


## Usage

```

# 10.00 USD
Money myMoney = new Money(10, "USD");
Money myMoney2 = new Money((decimal)20.05, "USD");

# Comparisons
myMoney == new Money(10, "USD")			#=> true
myMoney == new Money(10.00001, "USD")	#=> false
myMoney == new Money(100, "EUR")		#=> false
myMoney != new Money(100, "EUR")		#=> true

myMoney > myMoney2		#=> false
myMoney <= myMoney2		#=> true

# Arithmetic
myMoney * new Money(10, "BTC")		#=> throw new ArgumentException("Money Currency Not Equal")
myMoney + myMoney2 == new Money((decimal)30.5, "USD")
myMoney - myMoney2 == new Money((decimal)-10.5, "USD")
myMoney * myMoney2 == new Money((decimal)205.0, "USD")
myMoney / 10      == new Money(1, "USD")
(myMoney - (decimal)0.5) * 5 == new Money((decimal)100, "USD")

```

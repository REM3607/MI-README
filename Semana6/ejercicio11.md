# Rational
## Description

A rational number is a number that can be represented as the ratio of two integers. 
For example, 2/3 is a rational number, and you can think of 7 as a rational number with an implicit 1 in the denominator (7/1). 
For this assignment, you are going to write a class definition for rational numbers.

## Create a new class named Rational. 

A Rational object should have two number instance variables to store the numerator and denominator.
Write a constructor for your class that takes two arguments and that uses them to initalize the instance variables.
Write a method called printRational that prints the object in some reasonable format.
Write a method called invert that inverts the number by swapping the numerator and denominator. 
This method should modify the instance variables.
Write a method called toFloat that converts the rational number to a floating-point number and returns the result. 
This method is a pure function it does not modify the object.
Write method named reduce that reduces a rational number to its lowest terms by finding the greatest common divisor (GCD) of the numerator and denominator and dividing through. 
This method should modify the instance variables. To calculate the GCD you can search for Euclidian Algorithm: GCD.

# Solution 

```JavaScript

export default class Rational {
  numerator: number;
  denominator: number;

  constructor(numerator: number, denominator: number) {
    this.numerator = numerator;
    this.denominator = denominator;
  }

  printRational() {
    console.log(`${this.numerator} / ${this.denominator}`);
  }

  invert() {
    [this.numerator, this.denominator] = [this.denominator, this.numerator];
  }

  toFloat(): number {
    return this.numerator / this.denominator;
  }

  gcd(n: number, d: number): number {
    if (d == 0) return n;
    return this.gcd(d, n % d);
  }

  reduce() {
    const gcd = this.gcd(this.numerator, this.denominator);
    this.numerator = this.numerator / gcd;
    this.denominator = this.denominator / gcd;
  }
}
```

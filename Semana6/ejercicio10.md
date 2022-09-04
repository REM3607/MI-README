# Time

## Description
You have been hired by a brand of digital watches to be able to create the functionality of keeping track of time, for this you have been asked to do the following:

Write a definition for the class name Time this class would be use to build a digital clock. This class should have 3 attributes of type number. hour, minute and second.
Write a constructor that takes parameters named hour, minute and second and initializes the instance variables.
Write a method called getInSeconds that returns a number representing the actual time in the instance represented in seconds.
Write a method named printTime that prints the instance variables in a reader-friendly format (not the { ... } format way).

```JavaScript

export default class Time {
  hour: number;
  minute: number;
  second: number;

  constructor(hour: number, minute: number, second: number) {
    this.hour = hour;
    this.minute = minute;
    this.second = second;
  }

  printTime() {
    console.log(`
        ===========================
          Hours: ${this.hour}
          Minutes: ${this.minute}
          Seconds: ${this.second}
        ===========================
    `);
  }

  getInSeconds(): number {
    const minutes = this.hour * 60 + this.minute;
    return minutes * 60 + this.second;
  }
}

```

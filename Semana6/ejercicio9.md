
# Tile
## Description
In the board game Scrabble2, each tile contains a letter, which is used to spell words, and a score, which is used to determine the value of words.

Write a definition for a class named Tile that represents Scrabble tiles. The instance variables should be a string named letter and an number named value.
Write a constructor that takes parameters named letter and value and initializes the instance variables.
Write a method named printTile that prints the instance variables in a reader-friendly format (not the { ... } format way).
Don't worry you don't have to check if the letter is no more than one String length.
You can use this Main class to test your code.

```JavaScript

export default class Tile {
  letter: string;
  value: number;

  constructor(letter: string, value: number) {
    this.letter = letter;
    this.value = value;
  }

  printTile() {
    console.log(`
        ===========================
          Letter: ${this.letter}
          Value: ${this.value}
        ===========================
    `);
  }
}

```

# Instructions

## Past Solutions
The goal of this exercise is to convert a string to a new string where each character in the new string is "(" if that character appears only once in the original string, or ")" if that character appears more than once in the original string. Ignore capitalization when determining if a character is a duplicate.

## Examples
"din"      =>  "((("
"recede"   =>  "()()()"
"Success"  =>  ")())())"
"(( @"     =>  "))((" 

## Notes
Assertion messages may be unclear about what they display in some languages. If you read "...It Should encode XXX", the "XXX" is the expected result, not the input!

## Solution

```JavaScript
export function duplicateEncode(word: string){ // Success
  // lower case
  word = word.toLowerCase(); // 'success'
  // (string) | (string[]) ***
  const characters: string[] = word.split(''); // ['s','u','c','c','e','s','s']
  // iterar 
  const encoded: string[] = characters.map((character) => {
    character = character.replace(/\(/g, '\\(');
    character = character.replace(/\)/g, '\\)');
    const regex = new RegExp(character, 'g');
    const found = word.match(regex) || [];
    if(found.length === 1) {
      return '(';
    } 
    return ')';  
  }); // [')','(',')',')','(',')',')']
  return encoded.join('');  
}
```



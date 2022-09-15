# Make the Deadfish Swim

## Instructions

Write a simple parser that will parse and run Deadfish.

Deadfish has 4 commands, each 1 character long:

i increments the value (initially 0)
d decrements the value
s squares the value
o outputs the value into the return array
Invalid characters should be ignored.

parse("iiisdoso") => [8, 64]

## Solution

```JavaScript

/** return the output array and ignore all non-op characters */
export function parse(data: string): number[] {
    var result: number[] = []
    var current = 0

    data.split('').map((c) => {
      switch (c) {
        case 'i': current++; break
        case 'd': current--; break
        case 's': current = current ** 2; break
        case 'o': result.push(current); break
      }
    })

    return result
}
```

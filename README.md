# JavaScript_Learning
"Welcome to the JavaScript Learning repository! Learn and master JavaScript, a popular, versatile programming language. Perfect for beginners and experienced developers. Your coding journey begins here!"

# Problem Statement 

**Q1.) Write a program that swaps alternate digits of a given integer 'n'.​**

- If the total number of digits in the integer ‘n’ is even, swap the first and second digit, the third and fourth digit, the fifth and sixth digit, and so on. ​​

- For example, in the integer 564783, there are a total number of 6 digits. Here, the number 6 is an even number. The new integer after swapping this integer will be 657438.

- If the total number of digits in the integer ‘n’ is odd, then the first digit remains unchanged, and swapping begins from the second digit onwards.​​
    
- For example, in the integer 512364783, there are a total number of 9 digits. Here, the number 9 is an odd number. The new integer after swapping this integer will be 521637438.  In this case, the first digit remains unchanged, and the swap begins from the second digit. ​
```Javascript
const swapDigits = (number) => {
    if (typeof number !== 'number') {
        throw new Error('Input must be a number');
    }

    if (number < 0) {
        return 0; // Return 0 for negative numbers
    }

    let numberStr = number.toString(); // Convert the input number to a string
    let numberArray = numberStr.split(''); // Split the string into an array of digits

    // Determine if the total number of digits is even or odd
    const isEven = numberArray.length % 2 === 0;

    // Swap the digits based on whether the total number of digits is even or odd
    for (let i = isEven ? 0 : 1; i < numberArray.length - 1; i += 2) {
        let temp = numberArray[i];
        numberArray[i] = numberArray[i + 1];
        numberArray[i + 1] = temp;
    }

    // Join the array back into a string and parse it as an integer
    let swappedNumber = parseInt(numberArray.join(''), 10);
    return swappedNumber;

}

module.exports = swapDigits
```
**Test Case - Chai**
```Javascript
const chai = require('chai')
const expect = chai.expect

const swapDigits = require('../src/swapdigits')

describe('Swap Digits 1',()=>{
    it('swap the given even digits',()=>{
        expect(swapDigits(123455)).to.equal(214355)
    })
    it('swap the given odd digits',()=>{
        expect(swapDigits(123)).to.equal(132)
    })
    it('swap the given one digit',()=>{
        expect(swapDigits(0)).to.equal(0)
    })
    it('swap the given negative number', () => {
        expect(swapDigits(-512364783)).to.equal(0);
      });
})
```
- explain the code for the `swapDigits` function step by step:

```javascript
const swapDigits = (number) => {
  if (typeof number !== 'number') {
    throw new Error('Input must be a number');
  }
```

The code begins by defining a function called `swapDigits`, which takes a single argument `number`. It checks if the input `number` is of type 'number' using the `typeof` operator. If the input is not a number, it throws an error.

```javascript
  if (number < 0) {
    return 0; // Return 0 for negative numbers
  }
```

Next, the code checks if the input `number` is negative. If it is, the function returns `0`. This is done to handle the case mentioned in your test case where a negative number should be transformed into `0`.

```javascript
  let numberStr = number.toString(); // Convert the input number to a string
  let numberArray = numberStr.split(''); // Split the string into an array of digits
```

The input `number` is converted to a string using `toString()`, and the resulting string is then split into an array of individual digits using `split('')`.

```javascript
  const isEven = numberArray.length % 2 === 0;
```

The code determines whether the total number of digits in the input number is even or odd by checking if the length of the `numberArray` is divisible by 2.

```javascript
  for (let i = isEven ? 0 : 1; i < numberArray.length - 1; i += 2) {
    let temp = numberArray[i];
    numberArray[i] = numberArray[i + 1];
    numberArray[i + 1] = temp;
  }
```

Here, a loop is used to swap adjacent digits in the `numberArray` based on whether the total number of digits is even or odd. If it's even, the loop starts from the first digit (index 0) and swaps every pair of adjacent digits (0 with 1, 2 with 3, and so on). If it's odd, the loop starts from the second digit (index 1) and swaps the rest in the same manner.

```javascript
  let swappedNumber = parseInt(numberArray.join(''), 10);
```

After swapping the digits, the code joins the modified `numberArray` back into a string and then parses it as an integer using `parseInt`. This converts the swapped string back into an integer.

```javascript
  return swappedNumber;
}
```

Finally, the function returns the `swappedNumber`, which is the result of swapping the digits of the input number according to the rules you specified.

This code handles both positive and negative numbers, returning `0` for negative numbers as specified in your test case, and correctly swaps digits for positive numbers.

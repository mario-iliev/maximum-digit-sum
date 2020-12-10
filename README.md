# "Maximum digit sum" challange
This is a task that can be given on some interviews. The solutions I found online are using a bit of brute force in order to reach the answer so I decided to give this a try with a more mathematical aproach.

---

## The task:
You will be given an integer n and your task will be to return the largest integer that is <= n and has the highest digit sum.
The input conditions: n === integer, n > 0
The output condition: integer

Example: 78 => 78

_Digit Sum for 78 = 7 + 8 = 15. Note that 69 is also an option, but 78 is larger._

```javascript
function maxDigitSum(n) {
  if (n < 10) {
    return n;
  } else {
    const digitCount = String(n).length;
    const denary = Math.pow(10, digitCount - 1);
    const denaryRemainder = Math.round(n / denary) * denary - n;

    if (denaryRemainder === 1 || denaryRemainder === denary / 10 + 1) {
      return n;
    } else if ((n + denary / 10) % denary === 0) {
      return n - 1;
    } else {
      return n - (n % denary) - 1;
    }
  }
}

/* Below is the test function */
function testMaxDigitSum() {
  const inputOutputPairs = [
    [5, 5],
    [9, 9],
    [10, 9],
    [20, 19],
    [49, 49],
    [64, 59],
    [67, 59],
    [69, 69],
    [71, 69],
    [78, 78],
    [89, 89],
    [99, 99],
    [100, 99],
    [125, 99],
    [149, 99],
    [178, 99],
    [169, 99],
    [189, 189],
    [199, 199],
    [200, 199],
    [270, 199],
    [576, 499],
    [990, 989],
    [999, 999],
    [1000, 999],
    [1678, 999],
    [1789, 999],
    [1889, 999],
    [1899, 1899],
    [1999, 1999],
    [2899, 2899],
    [3000, 2999],
    [4111, 3999],
    [5900, 5899],
    [18999, 18999],
    [37690],
  ];

  inputOutputPairs.forEach(([input, output]) => {
    output && console.log(`For ${input} expected ${output} received ${maxDigitSum(input)}`);
    !output && console.log(`For ${input} result is ${maxDigitSum(input)}`);
  });
}

testMaxDigitSum();
```

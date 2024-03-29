# JavaScript Pow(x, n)
<br/>

## Challenge
Implement `pow(x, n)`, which calculates `x` raised to the power `n` (ex. `xⁿ`).
<br/>
<br/>

### 1<sup>st</sup> Example

```JavaScript
Input: x = 2.00000, n = 10
Output: 1024.00000
```

### 2<sup>nd</sup> Example

```JavaScript
Input: x = 2.10000, n = 3
Output: 9.26100
```

### 3<sup>rd</sup> Example

```JavaScript
Input: x = 2.00000, n = -2
Output: 0.25000
Explanation: 2⁻² = 1/2² = 1/4 = 0.25
```

<br/>

### Constraints

- `-100.0 < x < 100.0`
- `-2³¹ <= n <= 2³¹-1`
- `-10⁴ <= xⁿ <= 10⁴`
- `n` is an integer.

<br/>

## Solution

```JavaScript
const myPow = (x, n) => {
    if (n == 0) {
        return 1;
    }

    if (n % 2 == 0) {
        return myPow(x * x, n / 2);
    }

    if (n == 1) {
        return x;
    }

    if (n < 0) {
        return 1 / myPow(x, Math.abs(n));
    }

    return x * myPow(x, n - 1);
};
```

<br/>

## Explanation

I've defined a function called `myPow` that calculates the power of a given number. It takes two parameters, `x` and `n`, where `x` is the base number and `n` is the exponent.
<br/>

The function starts by checking if `n` is equal to `0`. If it is, the function returns `1`, as any number raised to the power of `0` is always `1`.
<br/>

If `n` is not `0`, the function checks if `n` is an even number by checking if `n` modulo `2` is equal to `0`. If it is, the function recursively calls itself with the base number `x` squared and the exponent `n` divided by `2`. This is possible because `xⁿ = (x²)⁽ⁿᐟ²⁾` when `n` is even.
<br/>

If `n` is not `0` and not even, the function checks if `n` is equal to `1`. If it is, the function returns the base number `x` itself, as any number raised to the power of `1` is itself.
<br/>

If `n` is not `0`, not even, and not `1`, the function checks if `n` is less than `0`. If it is, the function recursively calls itself with the base number `x` and the absolute value of `n`. This is possible because `x⁽⁻ⁿ⁾ = 1/(xⁿ)`.
<br/>

If none of the above conditions are met, the function returns the base number `x` multiplied by the function recursively called with the base number `x` and the exponent `n` decremented by `1`. This is possible because `xⁿ = x * x⁽ⁿ⁻¹⁾`.
<br/>

In summary, the `myPow` function calculates the power of a given number by using recursion and applying different mathematical properties depending on the value of the exponent.
<br/>
<br/>
<br/>
<br/>

### :next_track_button: [Next (Best Time To Buy & Sell Stock)][Next]
<br/>

### :previous_track_button: [Previous (Number of Atoms)][Previous]
<br/>

### :play_or_pause_button: [More Recursion & Memoization Challenges][More]
<br/>

### :eject_button: [Return to Course Outline][Return]
<br/>

[Next]: https://github.com/Superklok/JavaScriptRecursionAndMemoization/blob/main/JavaScriptBestTimeToBuyAndSellStock.md
[Previous]: https://github.com/Superklok/JavaScriptHashMapsAndSets/blob/main/Multiset/JavaScriptNumberOfAtoms.md
[More]: https://github.com/Superklok/JavaScriptRecursionAndMemoization
[Return]: https://github.com/Superklok/LearnJavaScript
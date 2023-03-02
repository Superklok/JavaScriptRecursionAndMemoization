# JavaScript Pow(x, n)

## Challenge:

Implement `pow(x, n)`, which calculates `x` raised to the power `n` (i.e., `xⁿ`).

### 1<sup>st</sup> Example:

`Input: x = 2.00000, n = 10`
<br/>
`Output: 1024.00000`

### 2<sup>nd</sup> Example:

`Input: x = 2.10000, n = 3`
<br/>
`Output: 9.26100`

### 3<sup>rd</sup> Example:

`Input: x = 2.00000, n = -2`
<br/>
`Output: 0.25000`
<br/>
`Explanation: 2⁻² = 1/2² = 1/4 = 0.25`

### Constraints:

`-100.0 < x < 100.0`
<br/>
`-2³¹ <= n <= 2³¹-1`
<br/>
`n` is an integer.
<br/>
`-10⁴ <= xⁿ <= 10⁴`

## Solution:

`const myPow = (x, n) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(n == 0) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return 1;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(n % 2 == 0) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return myPow(x * x, n / 2);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(n == 1) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return x;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(n < 0) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return 1 / myPow(x, Math.abs(n));`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return x * myPow(x, n - 1);`
<br/>
`};`
<br/>
<br/>
# JavaScript Edit Distance

## Challenge:

Given two strings `word1` and `word2`, return the minimum number of operations required to convert `word1` to `word2`.

You have the following three operations permitted on a word:
<br/>
Insert a character
<br/>
Delete a character
<br/>
Replace a character

### 1<sup>st</sup> Example:

`Input: word1 = "horse", word2 = "ros"`
<br/>
`Output: 3`
<br/>
`Explanation: horse -> rorse (replace 'h' with 'r')`
<br/>
`rorse -> rose (remove 'r')`
<br/>
`rose -> ros (remove 'e')`

### 2<sup>nd</sup> Example:

`Input: word1 = "intention", word2 = "execution"`
<br/>
`Output: 5`
<br/>
`Explanation: intention -> inention (remove 't')`
<br/>
`inention -> enention (replace 'i' with 'e')`
<br/>
`enention -> exention (replace 'n' with 'x')`
<br/>
`exention -> exection (replace 'n' with 'c')`
<br/>
`exection -> execution (insert 'u')`

### Constraints:

`0 <= word1.length, word2.length <= 500`
<br/>
`word1` and `word2` consist of lowercase English letters.

## Solution:

`const minDistance = (word1, word2) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const memo = new Map();`
<br/>
<br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const run = (w1, w2) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let insert  = Infinity,`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`del     = Infinity,`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`replace = Infinity;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if(memo.has(\`${w1} - ${w2}\`)) {
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return memo.get(\`${w1} - ${w2}\`);
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(w1 >= word1.length && w2 >= word2.length) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return 0;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(word1[w1] === word2[w2]) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return run(w1 + 1, w2 + 1);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(w2 < word2.length) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`insert = run(w1, w2 + 1);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(w1 < word1.length) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`del = run(w1 + 1, w2);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(w1 < word1.length && w2 < word2.length) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`replace = run(w1 + 1, w2 + 1);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const res = Math.min(insert, del, replace) + 1;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;memo.set(\`${w1} - ${w2}\`, res);
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return res;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`};`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return run(0, 0);`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've coded a function called `minDistance` that calculates the minimum number of operations required to transform one word into another. It takes two input parameters: `word1` and `word2`.
<br/>

Inside the function, a `Map` called `memo` is created to store previously computed results.
<br/>

The function `run` is defined within `minDistance`, which represents the recursive calculation. It takes two parameters: `w1` and `w2`.
<br/>

Three variables, `insert`, `del`, and `replace`, are initialized with `Infinity`. These variables will store the minimum number of operations required for each operation type.
<br/>

The function checks if the result for the current combination of `w1` and `w2` is already present in the `memo` `Map`. If it is, the previously computed result is returned.
<br/>

If both `w1` and `w2` have reached the end of their respective words (`word1` and `word2`), the function returns `0`, as no further operations are needed.
<br/>

If the characters at `w1` and `w2` are the same, the function recursively calls `run` with incremented `w1` and `w2` to proceed to the next characters.
<br/>

If `w2` is less than the length of `word2`, the function recursively calls `run` with the same `w1` and incremented `w2` to simulate an insert operation.
<br/>

If `w1` is less than the length of `word1`, the function recursively calls `run` with incremented `w1` and the same `w2` to simulate a delete operation.
<br/>

If both `w1` and `w2` are less than the lengths of `word1` and `word2` respectively, the function recursively calls `run` with incremented `w1` and `w2` to simulate a replace operation.
<br/>

The minimum number of operations required among the three types (insert, delete, and replace) is calculated by taking the minimum among `insert`, `del`, and `replace` and adding `1` to it.
<br/>

The result is stored in the `memo` `Map` using the combination of `w1` and `w2` as the key.
<br/>

Finally, the result is returned as the output of the `minDistance` function.
<br/>

In summary, the `minDistance` function uses recursion and memoization to calculate the minimum number of operations required to transform one word into another. It considers insertions, deletions, and replacements of characters. The function stores previously computed results to optimize performance.
<br/>
<br/>
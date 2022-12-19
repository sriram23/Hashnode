# Reverse an integer - JS

Hello World!

Today I'd like to share you how I solved ***reversing integer*** using JavaScript. Let me dive into the problem.
#### Input Format:
The input would be an integer *'x'*

#### Constraints:
 - Should return the reverse of 'x'.
 - The reversed integer should be in the range `[-2^31, 2^31 - 1]`. Else, zero should be returned.

### Solution:
The strategy I used to reverse the number is ***split and join***. Which means, I will split each digit of a number and will store it in an array. Then I will reverse the array. After that I will join those array which would be the reversal of the number.

That is if the number is 123, then
`123 -> ['1', '2', '3'] -> ['3', '2', '1'] -> 321`

Okay, let me write the code for this

```
var reverse = function(x) {
    const reversedNumber = x.toString().split('').reverse().join('');
    return reversedNumber;
}
```
What I did in the code is I convert 'x' to a string, then split each digit and store in array using the `split()` function, then I reverse the Array using `reverse()` function, then I merge those reversed array  using the `join()` function.

Now when we pass a number, we will get exact reverse of the number. 

But the problem with the above code is for negative integers, it won't return reversed number. For example, if 'x' is -123, the above code will work like
`-123 -> ['-', '1', '2', '3'] -> ['3', '2', '1', '-'] -> 321-`

In our case, it should be -321. How can we achieve that? For this, I've used a flag variable. Before reversing the number, I've added a check to find whether the number is positive or negative. If the number is negative the negativeFlag would be set `true`. Then I will reverse the absolute value of x (which means without considering the + or - signs) and finally if the negative flag is set to true, then we will negate the number. For changing the number to negative value, I have used the `bitwise not operator (~)`.
~x will give one number less than the negative value of x. Which means if x is 5, then ~x would be -6. So I've added 1 to ~x. Below is the code implementation.

```
var reverse = function(x) {
    const negativeFlag = x<0;
    const reversedNumber = Math.abs(x).toString().split('').reverse().join('');
    return negativeFlag?~reversedNumber+1:reversedNumber;
};
```

Now we are done with reversal. Now if we look at the constraints, it is said that the reversed number should be in the range `[-2^31, 2^31 - 1]`. Let's implement this. For this I've used limitFlag variable, which would be set true if the reversed number is not in specified range. So, here is the final version of code.

```
var reverse = function(x) {
    const negativeFlag = x<0;
    const reversedNumber = Math.abs(x).toString().split('').reverse().join('');
    const limitFlag = reversedNumber<=Math.pow(-2, 31) || reversedNumber>Math.pow(2, 31);
    return limitFlag?0:negativeFlag?~reversedNumber+1:reversedNumber;
};
```
This problem is taken from [Leet code](https://leetcode.com/problems/reverse-integer/). If you want to give a try with the problem, you can visit the above link.

Thank you! 
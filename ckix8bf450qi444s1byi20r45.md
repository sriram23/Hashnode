# Harshad Number

Hello World!

Happy to write here. In this post, let us see what is **Harshad Number** and how we can find whether the number is Harshad Number or not.

# What is Harshad Number?
A number which is divisible by sum of its digits is called as **Harshad Number**.

For example, **18** is a Harshad Number. The division of 18 by its sum of digits will give a whole number

> 18 => 18/(1+8) => 18/9 => 2

Since, we got 2, which is a whole number 18 is a Harshad Number.

Let's take another example, **19**.


> 19 => 19/(1+9) => 19/10 => 1.9

We've got 1.9, which is not a whole number. So, 19 is not a Harshad Number.

# Let's code

Let us construct a simple program in python to find the given is Harshad Number or not.

So far, we've solved the problem in human perspective. Let's now solve in programming perspective.

First we have to get a number from user. We have to store the number provided by user in a variable called *number*.


``` 
number = input()
```

This would get a number from user and will store it in *number* variable.

Next, we have to find the sum of digit. For that we have to split the number to list of numbers, so that the list would contain each digit of the number provided by user.

We'd have to make 18 -> [1,8]


```
lst = [int(i) for i in str(number)]
``` 

The above code will split the numbers and will create a list of digits and will store them in variable called *lst*

Now, we need to find sum of those digits in the list. We can make use of the for loops here to get the sum of digits.

```
for i in lst:
  sumOfDigits += i
```
So now, the `sumOfDigits` would hold the value of sum of digits.
We now going to find the division of number by sumOfDigits.
```
result = int(number)/sumOfDigits
```

The `result` variable will hold the divison of number by sum of digits.
Now, if the result is a whole number, then the provided number is Harshad, else it is not a Harshad Number.
```
print('Harshad Number' if result==math.floor(result) else 'Not a Harshad Number')
```
Here we have used the python conditional operator, which would print 'Harshad Number' when the result is same as the round off to the lower bound of result. Otherwise, it would be 'Not a Harshad Number'

Here is the final code:
```
import math

number = input()
sumOfDigits = 0
lst = [int(i) for i in str(number)]
for i in lst:
  sumOfDigits += i
result = int(number)/sumOfDigits
print('Harshad Number' if result==math.floor(result) else 'Not a Harshad Number')
```

Here are the outputs:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608474511882/HZxU0vSMb.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608474538038/5VFnayzUz.png)

You can find the code here: https://repl.it/join/ojwfyxyc-sriramb

Thank you!
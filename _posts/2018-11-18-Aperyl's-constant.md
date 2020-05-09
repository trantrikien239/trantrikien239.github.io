So, yesterday I came across this video about the amazing Apery's Constant.

[![Apéry's constant - Numberphile](https://res.cloudinary.com/marcomontalbano/image/upload/v1588356230/video_to_markdown/images/youtube--ur-iLy4z3QE-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=ur-iLy4z3QE "Apéry's constant - Numberphile")

## The Problem

In short, Apery’s Constant (C) is this infinity sum:

![infinity sum](https://github.com/trantrikien239/trantrikien239.github.io/blob/master/media/Aperys-Number.png?raw=true)

And apparently 1/C is the probability that 3 random integers are co-prime.

The Mathematician in video ask his friends on Twitter to write 3 random number in the comments to approximately calculate Apery’s Constant. But since I don’t have Twitter (or many friends that are interested in this kind of thing =]]]). So I think why not test it myself using a simple python script.

## Let’s code

First, I import numpy because it’s the simplest and most efficient way to generate random arrays of 3 integers.

```python
import numpy as np
```

Then, let’s prepare a function to find out if 3 integers are co-prime or not:

- First, we need to define a function that get greatest common divisor (GCD) of 2 numbers. GCD of 3 numbers are easily calculated by get GCD of 2 numbers first, then get GCD of that and the last number.
- Then define a function that return True if 3 numbers are co-prime.

```python
def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

def coprime_3_int(a,b,c):
    return gcd(gcd(a, b), c) == 1
```

Now, it’s time for trials and errors (like hundred of thousands time).

```python
sample = 1e5
num_co_prime = 0

for in range(sample):
    l = np.random.randint(1, sample + 1, 3)
    if coprime_3_int(*l):
        num_co_prime += 1
```

Finally, calculate the Apery’s Constant according to the formula P = 1/C. Need to convert “sample” to float for the division return with decimal point.

```python
Aperyls_constant = float(sample) / num_co_prime
print(Aperyls_constant)
# 1.2012733497507357
```

Pretty close to the actual Apery’s constant right?

![infinity sum](https://github.com/trantrikien239/trantrikien239.github.io/blob/master/media/Aperys-Number.png?raw=true)


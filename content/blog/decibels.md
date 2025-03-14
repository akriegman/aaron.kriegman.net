---
title: "Decibels"
date: 2023-09-22T13:40:08-04:00
draft: false
katex: true
description:
---

In our number system, it is not very easy to quickly judge the magnitude of a
number. The first thing you look for to get a feel for the size of a number is
how many digits it has, and the second thing you look for is the first digit.
Now as it turns out, for this purpose, different digits give you different
amounts of information. If the first digit is a $1$, then your number could be
as large as, say, $1999$, nearly twice the smallest it can be, $1000$. So you
really need to look at the second digit to get a feel for the size of your
number. On the other hand, if the first digit is a $9$, then the largest
possible value is only $11\\%$ larger than the smallest, so you already have a
decent idea of the magnitude. This idea is often formalized as
[Benford's law](https://en.wikipedia.org/wiki/Benford%27s_law), which states
that in typical data sets the first digits of the numbers are not evenly
distributed, with $1$ appearing about $30\\%$ of the time, $2$ appearing the
second most, etc.

Quickly judging multiplication is not easy either, and is also dependent on the
first digit. If I asked you what's $3950$ times $5050$, you could estimate that
as $4000$ times $5000$, and tell me about $20$ million pretty easily. If I asked
you what's $1250$ times $1580$, it's not so straightforward. Maybe you could
estimate it as $1200 \cdot 1600$, but now you're doing multiplication with two
significant figures, which is already much harder. If you just wanted to quickly
estimate the answer, you might not bother in this case. In both these cases, the
proportions of our two numbers are the same. That is to say, in a world where
$3.16$ centimeters made an inch, you'd be doing the first problem if you worked
in centimeters and the second if you worked in inches. So these two
multiplication problems are really the same problem with a different skin, yet
one is harder for no good reason.

Enter decibels[^0]. The decibel scale was originally meant for measuring the
volume of sound, but it can be combined with other units[^1], or just used to
represent plain numbers. The definition of the scale is that every $10$ decibels
is a factor of $10$. So $20$ dB $= 100$, $-10$ dB $= 0.1$, $0$ dB $= 1$, etc.
This means that $5$ dB is the square root of ten, $1$ dB is the tenth root of
ten, etc. One incredibly useful coincidence is that $3$ dB is very close to $2$.
This corresponds to the fact that $2^{10} = 1024 \approx 1000 = 10^3$.

[^0]: This solution didn't fall out of the sky of course. I got the inspiration
from the idle game Antimatter Dimensions, which has an option to display all
numbers in the game using exponential notation, which is like scientific
notation but instead of $4$e$3$ for example you would write e$3.6$. I liked this
a lot and started thinking about how great it would be if everyone started using
this all the time. I also started coming up with some useful approximations for
converting to and from exponential notation. I started to notice that it's
really useful to work in tenths of an order of magnitude, and hey, maybe we
should have a name for those. I later found out that a name already exists,
they're called decibels.

    Another scale that came about in a similar way is the twelve note musical
    scale. This scale divides each factor of two into twelve equal pieces called
    semitones, so each semitone is about a quarter of a decibel. Four semitones
    is very close to $5/4$ (relative error below $-21$ dB) and seven semitones
    is extremely close to $3/2$ (relative error below $-29$ dB). These strong
    approximations of simple rational numbers are the essential reason why the
    twelve note musical scale is good. If you wanted to, you could make music
    using quarters of decibels instead of semitones.

[^1]: Decibel milliwatts (dBmW) are often used to measure wifi signal strength.

Now let's revisit our previous examples but with decibels, and see if they're
easier. $1000$ and $1999$ written in decibels are $30$ dB and $33$ dB. Before we
needed to look at three pieces of information to get a feel for the magnitudes
of these numbers: the number of digits, the first digit, and the second digit.
But after expressing the numbers in decibels, we can get a good feel for their
sizes with only two pieces of information: the tens place[^2] tells us the order
of magnitude of the number, and the ones place tells us pretty well where the
number falls within that order of magnitude. The numbers starting with $1$ get
the $0$ to $3$ range of the ones place when written in decibels, so a
proportional amount of our scale is dedicated to these numbers. Meanwhile
$80,000$ is $49$ dB and $90,000$ is $49.5$ dB, so these numbers get squeezed
into a smaller part of our scale, as they should since they are proportionally
closer.

[^2]: For numbers larger than $99$ dB or smaller than $-99$ dB, you also need to
look at the higher places to get the order of magnitude. But at that point
counting the digits isn't very useful anyways.

One of the key properties of decibels is that $x$ dB $\cdot\ y$ dB $= (x + y)$
dB. That is, decibels turn multiplication into addition (and division into
subtraction). So our previous problem, $3950 \cdot 5050$, becomes $36$ dB
$\cdot\ 37$ dB, which is just $73$ dB $= 20$ million. About as easy as before.
On the other hand, $1250 \cdot 1580$ becomes $31$ dB $\cdot\ 32$ dB $= 63$ dB $=
2$ million, which is _much_ easier than before. Importantly, it's the same
difficulty as the first problem, as it should be.

## Decibel arithmetic tips

One time in a meeting in my first internship, we were discussing poker hand
probabilities, when someone asked how many possible five card hands there are.
Nobody knew the answer off the top of their head, so we just moved on. Sitting
in that meeting, using decibels, I was able to calculate in my head that it was
about $2$ million. I then refined my estimate to $2.5$ million, impressing all
my coworkers when we looked it up and it was about $2.6$ million. Once you learn
the tips in this section, you'll be able to do these kinds of calculations in
your head too.

### Converting to and from decibels

As I mentioned before, the approximation $3$ dB $= 2$ is going to be our best
friend. This tells us that $6$ dB $= 4$ and $9$ dB $= 8$. Working backwards from
$10$ dB $= 10$, we get that $7$ dB $= 5,$ $4$ dB $= 2.5$, and $1$ dB $= 1.25$.

For $5$ dB, we can use the approximation $\sqrt{10} = \pi$ to get $5$ dB $=
3.14,$ $8$ dB $= 6.28$, and $2$ dB $= 1.57$. This approximation is not the most
accurate or the easiest to use, but it is easy to remember. Slightly more
accurate is $5$ dB = $3 \frac16$ (That's an improper fraction! This is the first
time I've used those since elementary school.) which gives $2$ dB $= 1
\frac7{12}$ and $8$ dB $= 6 \frac13$. A helpful way to remember the $2$ dB
approximation is that $0$ dB, $1$ dB, $2$ dB, and $3$ dB break the interval from
$1$ to $2$ into pieces of proportion $3$ to $4$ to $5$. The relative errors[^rel]
of all these estimates are all smaller than $-21$ dB, or $0.8\\%$.

[^rel]: The relative error of an approximation $x + E$ to a value $x$ is defined
as the absolute error $E$ scaled relative to the value, ie $\frac Ex$. This is
approximately equal to $\frac E{x+E}$ when the relative error is small, so it
doesn't matter whether you scale by the value or the approximation. The relative
error has the advantage of being scale invariant, and in many situations is the
most natural way to express error.

    <!-- Another method that comes to mind for expressing the error of an approximation while 
    remaining scale invariant would be to just give the ratio. 
    Consider for example the approximation $3$ dB to the value $2$. The ratio is 
    about $1.0024$. We don't want to write out tons of placeholder zeros, so we can try 
    expressing the ratio in decibels, in this case $0.0103$ dB. It turns out though that in general this 
    doesn't actually make things any better, it only saves us at most one placeholder zero. 
    So, it would be useful to use decibels again to express what fraction of a 
    decibel the ratio is. In this case the ratio is $-19.9$ dB dB. 
    As it turns out, for approximations with small errors, the ratio in decibel 
    decibels is equal to the relative error in decibels plus a constant. That 
    constant is about $6.38$. Sure enough, for our example the relative error 
    is $-26.2$ dB. -->

    The other method that comes to mind as a potentially more natural way to express the error
    is to just give the ratio of the approximation to the value.
    As discussed above, ratios like this are best expressed using a scale like
    decibels, and as it turns out, for close approximations, the ratio in decibels
    is proportional to the relative error. So we may as well just use the relative error.

Then we can get an estimate for any whole number of decibels by just sliding
over the decimal point. For example, $14$ dB $= 25$, and $-6$ dB $= 0.25$.

For values in between a whole number of decibels, the best way to convert is by
interpolating linearly. For example, to convert $3$ into decibels, we recall
that $4$ dB $= 2 \frac12$ and $5$ dB $= 3 \frac16$. $3$ is $3/4$ of the way from
$2 \frac12$ to $3 \frac16$, so $3 = 4 \frac34$ dB.

Now as an example of how to convert the other way, say we want to find $2 \cdot
3$ using decibels. That's $(3 + 4 \frac34)$ dB $= 7 \frac34$ dB. $7$ dB $= 5$
and $8$ dB $= 6 \frac13$, so the answer is three quarters of the way from $5$ to
$6 \frac13$ which is approximately $6$. This is a silly example, but it's cool
that it gives us the right answer.

The relative error of this linear interpolation is also smaller than $-21$ dB,
so as long as we're using the reference points mentioned above there's no reason
to use a better interpolation method[^3].

[^3]: The relative error of each exponential approximation is proportional to
the absolute error of the inverse logarithmic approximation.

### An example

Now I'll show you how to use this to estimate the number of poker hands. There
is a well known formula for the number of ways to choose $5$ cards out of a $52$
card deck:

$$\frac{52 \cdot 51 \cdot 50 \cdot 49 \cdot 48}{5 \cdot 4 \cdot 3 \cdot 2 \cdot
1}$$

This number is called "$52$ choose $5$". We can approximate the numerator as
$50^5$, especially since the factors are spread symmetrically around $50$, so
the errors in this approximation will partially cancel[^4].

[^4]: The relative error away from $50$ for each factor is one or two parts in
$50$. The first order error of $51$ will cancel with $49$, and $52$ with $48$,
leaving us with only the second order error. Therefore $50^5$ approximates the
numerator with relative error on the order of $(2/50)^2$, or about $(2 \cdot
(3 - 17))$ dB $ = -28$ dB.

Now $50 = 17$ dB, so $50^5$ is $(17 \cdot 5)$ dB $= 85$ dB. The denominator
comes out to $120$, which is close to $125 = 21$ dB. So our final answer is
$(85 - 21)$ dB $= 64$ dB $= 2.5$ million. Pretty close to the actual answer of
$2,598,960$! I originally estimated the denominator as $20$ dB, which is how I
got my first estimate of $2$ million.

But we can do better. Instead of rounding $120$ to $125$, we can interpolate.
$120$ is $4/5$ of the way from $100$ to $125$, so it's closer to $20.8$ dB. So
our final answer is $64.2$ dB, which is $1/5$ of the way from $2.5$ million to
$3 \frac16$ million, so about $2.63$ million. This is slightly closer to the
answer and has a relative error of just over $-20$ dB. If you round this
estimate to $2.6$ million you'll get lucky and get a lot closer.

## Conclusion

The first takeaway from all this is that when you encounter numbers in the wild
and you need to multiply, divide, or compare their proportions, you may find it
useful to convert them to decibels first. I find that it's often not worth it
for one off multiplication or division, but for exponents, comparisons, and
products of many numbers, this conversion can be very helpful.

But the bigger point I want to make is that I think we should start presenting
many numbers as decibels in the first place. As discussed, our number system is
biased towards certain digits, and makes common operations more difficult than
they have to be. If we started using decibels in news articles, on nutrition
labels, etc., it would be easier to intuitively judge numbers. Unfortunately,
this would require getting our entire society to become literate in decibels,
which would not be worth it for this marginal improvement. So it seems that this
system of approximations that I've come up with will be relegated to the realm
of party tricks and occasionally useful tools for the foreseeable future. Maybe
one day this could be incorporated into a school curriculum, but that would
probably be a bad choice because there're more important things for kids to
learn in math class.

I would like to point out that not all numbers are better in decibel form. Some
numbers are meant to be multiplied, divided, and compared using ratios, and for
those numbers we should use decibels. Other numbers are meant to be added,
subtracted, or compared using differences, and for these numbers it would not be
helpful to use decibels.

Lastly, I'll mention that decibels are what is known as a logarithmic scale.
I've avoided using this word because I don't want to scare people away. I think
that the content in this post is actually pretty accessible, but if I'm not
careful then people will get intimidated and their eyes will glaze over.

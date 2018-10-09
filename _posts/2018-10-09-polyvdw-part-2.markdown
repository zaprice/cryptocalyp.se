---
layout: post
title: "Elementary Upper Bounds for \\(PW(4, \\{ax^2+bx\\})\\)"
---

We'll generalize the algorithm from the last post to $$PW(4, \{x^2+x\})$$ and try to go further to all quadratics $$ax^2+bx$$.

Instead of squares, we now have $$f(x)=x^2+x=x(x+1)$$, which are sometimes called the _rectangular numbers_.

To use the same algorithm, we need a parameterization of integer solutions to $$x(x+1) + y(y+1) = z(z+1)$$,
similar to Euclid's formula for Pythagorean triples.
First, we use the quadratic formula to express $$z$$ in terms of $$x$$ and $$y$$.

$$z = f(x,y) = \frac{-1+\sqrt{4x(x+1)+4y(y+1)+1}}{2}$$

This equality holds in general, but we only want values with $$z\in\N$$.

$$z$$ is an integer _iff_ $$\ 4x(x+1)+4y(y+1)=(2z+1)^2$$ is an odd square.
This can be factored into $$(2x+1)^2+(2y+1)^2=(2z+1)^2+1$$, or $$m^2+n^2=k^2+1$$ with $$m,n,k$$ odd --
like an "almost" Pythagorean triple.

A parameterization of $$m^2+n^2=k^2+1$$ would imply one for $$(x,y,z)$$, and luckily this equation is easier.
Using the [_Bramagupta-Fibonacci identity_](https://en.wikipedia.org/wiki/Brahmagupta%E2%80%93Fibonacci_identity) with $$bc-ad=1$$, we get:

$$(ac-bd)^2 + (ad+bc)^2 = (ac+bd)^2 + 1$$

So, with parameters $$a,b,c,d$$ and constraints $$bc-ad=1$$, $$ac-bd> 1$$, $$2\vert ac-bd-1, ad+bc-1$$, we have:

$$x = \frac{ac-bd-1}{2},\ y = \frac{ad+bc-1}{2},\ z = \frac{ac+bd-1}{2}$$

Like last time, we generate quadruples $$(a,b,c,d)$$ and discard ones that don't fit the constraints.
We use them to find triples that overlap in a $$K_3$$, and finally see if some $$K_3$$ admits a $$w$$ that solves the system.
The smallest solution I've found looks like this:

![]({{"assets/4-color_x^2+x.png" | absolute_url}})

Can we generalize even further to $$Ax^2+Bx$$? Sure!
Skipping a few steps, we get $$(2Ax+B)^2 + (2Ay+B)^2 = (2Az+B)^2 + B^2$$.
We can parameterize it like before as,

$$x = \frac{ac-bd-B}{2A},\ y = \frac{ad+bc-B}{2A},\ z = \frac{ac+bd-B}{2A}$$

with a similar set of constraints:

$$bc-ad=B,\ ac-bd> B,\ 2A\vert ac-bd-B, ad+bc-B$$

We can make improvements to the parameter search, too.
Rather than searching all $$(a,b,c,d)$$, we could eliminate parts of the parameter space that we know do not contain solutions.
With fixed $$a$$ and $$d$$, the first constraint implies that $$bc$$ is some factorization of $$ad + B$$.
We can pre-compute a table of factorizations and use that to cut the search space down to basically $$n^2$$.
You can see the code for this [on GitHub](https://github.com/zaprice/polyvdw/blob/e17902c9151e16447a385ca290d9dbb0b2659bfd/src/java/polyvdw/PolyRunner.java)!

We can find bounds for nearly any $$PW(4,x^2+Bx)$$ with this method,
but I've only found a few bounds for the more general $$Ax^2+Bx$$ case;
if such configurations exist, it seems the numbers involved are much larger.
Here's one example:

![]({{"assets/4-color_3x^2+x.png" | absolute_url}})

You can check out the full table [here]({{"assets/bounds.pdf" | absolute_url}})!

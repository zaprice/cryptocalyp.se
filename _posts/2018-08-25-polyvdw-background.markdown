---
layout: post
title: "Simple Cases of the Polynomial van der Waerden Theorem"
---


First, we state the standard and polynomial versions of van der Waerden's theorem.

<span class="theorem">For any positive integers $$c,k$$ there is some number $$N=W(c,k)$$ such that if the integers $$\{1,\ldots,N\}$$ are $$c$$-colored, then there must be $$k$$ integers in arithmetic progression that are the same color.</span>

This is a classic Ramsey-type theorem: if you color $$\{1,\ldots,N\}$$, there is no way to avoid creating some monochromatic structure (for large enough $$N$$), in this case an arithmetic progression of length $$k$$.

Starting with a progression like $$\{a_0, a_0+r, a_0+2r,\ldots, a_0+kr\}$$ where the difference between each term is the constant $$r$$, we can generalize by replacing that constant with a set of $$k$$ functions.
We take some fixed $$d$$ and consider polynomials $$\{p_1,\ldots,p_k\}$$ with all $$p_i(0)=0$$; our new "progression" is $$\{a_0, a_0+p_1(d), a_0+p_2(d),\ldots, a_0+p_k(d)\}$$.
This leads to the statement of the polynomial van der Waerden theorem:

<span class="theorem">For any positive integers $$c,k$$ and a set $$\{p_1,\ldots,p_k\}\subseteq\Z[x]$$ of polynomials with $$p_i(0)=0$$, there exists some number $$N=PW(c,\{p_1,\ldots,p_k\})$$ such that any $$c$$-coloring of $$\{1,\ldots,N\}$$ has a monochromatic subset $$\{a_0, a_0+p_1(d), a_0+p_2(d),\ldots, a_0+p_k(d)\}$$ for some $$d$$.</span>

This generalizes the standard theorem as the previous arithmetic progression has polynomials $$p_i(x) = ix$$ and $$d=r$$.

The bounds you get on $$W(c,k)$$ and $$PW(c,\{p_1,\ldots,p_k\})$$ from proving these theorems are very large, and computing exact values is intractable and computationally expensive to even verify.
As such, it's an interesting exercise to see if we can significantly improve the bounds on $$PW$$ by some method which is checkable in an elementary way.

We begin with the simplest case; bounding the value of $$PW(2,\{x^2\})$$ is equivalent to asking for the smallest $$N$$ where any $$2$$-coloring of $$\{1,\ldots,N\}$$ must have two numbers the same color that are a square apart.
This case is easy to solve by inspection.
Without loss of generality we say $$1$$ is $$\RR$$.
$$2$$ must be $$\BB$$ as $$2-1$$ is a square, and so $$3$$ is $$\RR$$ and so on.
\\[\begin{matrix}1&2&3&4&5&\ldots\\\\\RR&\BB&\RR&\BB&\RR&\ldots\end{matrix}\\]
However, $$5-1=2^2$$ but both are $$\RR$$.
Thus, $$PW(2,\{x^2\})\leq 5$$ and this bound is tight as there is only one possible $$2$$-coloring (up to symmetry).

For $$c=3$$ it is more complicated.
Taking $$1$$ as $$\RR$$, any $$n^2+1$$ must be $$\BB$$ or $$\GG$$.
A configuration of $$a,b$$ where $$(a^2+1)-(b^2+1)=c^2$$ would result in $$1, a^2+1, b^2+1$$ all different colors.
This is just a Pythagorean triple; taking the smallest $$(3,4,5)$$ gives us:

![]({{"assets/3-color_x^2.png" | absolute_url}})

By symmetry, we know that 42 must also be $$\RR$$.
And we can iterate this construction! $$42+4^2$$ and $$42+5^2$$ must be either $$\BB$$ or $$\GG$$, and $$42+4^2+5^2=1+2\cdot41$$ must be $$\RR$$.

All $$1+i\cdot41$$ are $$\RR$$, so $$1+41^2$$ is the same color as $$1$$ providing a bound of $$PW(3, \{x^2\})\leq 1+41^2$$.
In the next few posts, we will discuss how to adapt this technique for more colors and other polynomials.

---
layout: post
title: "An Elementary Upper Bound for \\(PW(4, \\{x^2\\})\\)"
---

In this post, we discuss the process for generating an "elementary" configuration which bounds the polynomial van der Waerden number $$PW(4, \{x^2\})$$.
We write our $$\N$$-colorings starting at $$0$$ for simplicity.

For the 3-color case, we built a $$K_3$$ with different colored vertices using a Pythagorean triple;
then we found an integer a square away from the $$\BB$$ and $$\GG$$ vertices, which must be $$\RR$$.
Essentially, we solved this system of Diophantine equations:

$$
\begin{matrix}
x^2 + a^2 = y^2 \\
x^2 + b^2 = w \\
y^2 + c^2 = w
\end{matrix}$$

We iterated this construction to obtain the square $$w^2$$ which must be $$\RR$$, completing the proof.
To generalize this method to four colors, we need a $$K_4$$ colored $$\RR\BB\GG\YY$$ and another $$w$$ which must be $$\RR$$, as in:

![]({{"assets/4-color_x^2_blank.png" | absolute_url}})

Or as a system:

$$
\begin{matrix}
x^2 + a^2 = y^2 \\
x^2 + b^2 = z^2 \\
y^2 + c^2 = z^2 \\
\\
x^2 + d^2 = w \\
y^2 + e^2 = w \\
z^2 + f^2 = w
\end{matrix}
$$

I've taken to calling $$(x,y,z)$$ a _Pythagorean $$K_3$$_ as a generalization of the Pythagorean triple --
rather than two squares with a square difference, we have three squares with square pairwise differences.
Note that $$(a,b,c)$$ is a Pythagorean $$K_3$$ as well.

It [was shown](https://en.wikipedia.org/wiki/Hilbert%27s_tenth_problem) in 1970 that there is no decision procedure for the solvability of arbitrary Diophantine equations, so solving this system is going to be more difficult than making a library call.
However, we can make some simplifications so our search is not strictly brute-force.

Each equation in the first block is a Pythagorean triple, for which we have a [known formula](https://en.wikipedia.org/wiki/Pythagorean_triple#Generating_a_triple) with parameters $$k,m,n$$ where $$m > n$$, and $$m,n$$ are coprime but not both odd.
From here, we can use the [Farey sequence](https://en.wikipedia.org/wiki/Farey_sequence) as an efficient algorithm to generate coprime pairs $$m,n$$.
Then, we check if our triples overlap to form a $$K_3$$, and from there check if that $$K_3$$ has some $$w$$ satisfying the constraints.

You can see my implementation of this algorithm [on Github](https://github.com/zaprice/polyvdw/blob/31bb22c1431b038b7d185f843bec3a22a86033a3/src/java/polyvdw/Cfour.java);
one important observation is that a triple $$(x,y,z)$$ is part of a $$K_3$$ precisely when the smallest difference $$a^2 = y^2 - x^2$$ is part of another
triple $$(a,b,c)$$.

In the process of bounding $$PW(4, \{x^2\})$$, I generated many Pythagorean $$K_3$$'s, which you can see [here]({{"assets/kthrees.csv" | absolute_url}}).
They could potentially have interesting number-theoretic properties, outside of their use in this proof.
It seems likely that there exist greater Pythagorean $$K_n$$ as well, but generating them with this method is infeasible.

Finally, the graph which shows that $$PW(4, \{x^2\}) < 1+290085289^2$$.
We say such a configuration is _elementary_ because it is easily verified despite the fact that generating it may have involved arbitrarily complex computation.


![]({{"assets/4-color_x^2.png" | absolute_url}})

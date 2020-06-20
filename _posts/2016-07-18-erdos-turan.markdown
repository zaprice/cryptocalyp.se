---
layout: post
title: "The Erdős-Turán Conjecture"
date:   2016-07-18 22:05:00
series: "Arithmetic Combinatorics"
tag: math
---

The **[Erdős-Turán conjecture](https://en.wikipedia.org/wiki/Erd%C5%91s_conjecture_on_arithmetic_progressions)**[^1] on arithmetic progressions states:

<span class='conjecture'>For a set $$A$$ of positive integers, if</span>

$$\sum_{a\in A}\frac{1}{a}\to\infty$$

then $$A$$ contains arbitrarily long arithmetic progressions.

In the literature, sets with a divergent sum of reciprocals are sometimes referred to as **large** or **substantial sets**.
Only a sequence with a sufficiently dense tail could have divergent reciprocal sum;
the conjecture states that you cannot construct such a sequence without necessarily including an arithmetic progression of every length.
The contrapositive provides an upper bound for the density of sequences that do not contain arbitrary arithmetic progressions as they must be less dense than large sets.

As a combinatorial statement about arithmetic progressions, the conjecture is closely related to theorems of [van der Waerden](https://en.wikipedia.org/wiki/Van_der_Waerden's_theorem) and [Szemerédi](https://en.wikipedia.org/wiki/Szemer%C3%A9di's_theorem).
We will show that it is a strictly stronger version of Szemerédi's theorem.

First, we sketch the prototype that inspires this proof.
When you think of large sets, the first and most obvious example that comes to mind is the harmonic series:

$$\sum_{n=1}^{\infty}\frac{1}{n}\to\infty$$

The classic [proof](https://en.wikipedia.org/wiki/Harmonic_series_(mathematics)#Divergence) of this statement is due to Nicole Oresme, from 14th century France.

<div class='proof'>
$$\sum_{n=1}^{\infty}\frac{1}{n} = 1 + \frac{1}{2} + \frac{1}{3} + \frac{1}{4} + \frac{1}{5} + \frac{1}{6} + \frac{1}{7} + \ldots$$
$$> \frac{1}{2} + (\frac{1}{4} + \frac{1}{4}) + (\frac{1}{8} + \frac{1}{8} + \frac{1}{8} + \frac{1}{8}) + \ldots$$
$$ = \sum_{n=1}^{\infty} 2^{n-1}\frac{1}{2^{n}} = \sum_{n=1}^{\infty}\frac{1}{2}\to\infty$$
</div>

The trick has two parts:
first _grouping_ the elements into groups of size $$2^{n-1}$$,
and then _bounding_ each element in that group from below by $$\frac{1}{2^n}$$.
The sum then reduces to one which obviously diverges.
We can generalize this proof to other series by being clever about how we choose those components.

So far we have seen two measures of the density of a sequence of positive integers:
whether its sum of reciprocals diverges, and whether it contains arithmetic progressions of arbitrary length.
Here is a more intuitive notion of density used by Szeméredi.

<span class='definition'>If $$A\subset\N$$, then the **upper density** of $$A$$ is

$$\bar{\delta}(A)=\limsup_{n\to\infty}\frac{|A\cap\{1,\ldots,n\}|}{n}$$

It is the asymptote of the sequence of upper bounds on the density of $$A$$ in $$\{1,\ldots,n\}$$, as $$n$$ goes to infinity.
Szeméredi's theorem states that sets with positive $$\bar{\delta}$$ must contain arbitrarily long arithmetic progressions.

<span class='proposition'>All sets with positive upper density are large.</span>

<div class='proof'>
Let \(A\) be a set with \(\bar{\delta}(A)=\delta>0\).
Say \(N_1=1\) and choose a sequence \(\{N_k\}_{k\in\N}\) of positive integers such that
$$N_k\geq\frac{4}{\delta}N_{k-1} \text{ and }
|A\cap[1,N_k)|\geq\frac{\delta}{2}N_k$$
What does this mean?
This is the grouping condition.
\(N_k\) is at least \(\frac{4}{\delta}\) times the previous term \(N_{k-1}\);
each group is the set of elements between \(N_{k-1}\) and \(N_k\).
How big is that group?
$$|A\cap[N_{k-1},N_k)|=|A\cap[1,N_k)|-|A\cap[1,N_{k-1})|\geq\frac{\delta}{2}N_k-N_{k-1}$$
as there can be at most \(N_{k-1}\) elements in \(A\) smaller than \(N_{k-1}\).
All elements \(n\) in each group \(A\cap[N_{k-1},N_k)\) are strictly smaller than \(N_k\), so \(\frac{1}{n}\geq\frac{1}{N_k}\).
<br>
Now we can state and bound our reciprocal sum as follows:
$$\sum_{n\in A}\frac{1}{n}=\sum_{k=1}^\infty\sum_{n\in A\cap[N_{k-1},N_k)}\frac{1}{n}
\geq\sum_{k=1}^\infty|A\cap[N_{k-1},N_k)|\frac{1}{N_k}$$
$$=\sum_{k=1}^\infty(\frac{\delta}{2}N_k - N_{k-1})\frac{1}{N_k}
\geq\sum_{k=1}^\infty(\frac{\delta}{2}N_k - \frac{\delta}{4}N_k)\frac{1}{N_k}
=\sum_{k=1}^\infty\frac{\delta}{4}\to\infty$$
</div>

This proof gives us a few examples of large sets,
including that any arithmetic progression is large;
$$\{a_0+bn : n\in\N\}$$ has upper density $$^1\!/_b$$ .

Moreover, large sets with upper density $$0$$ do exist;
[Euler showed](https://en.wikipedia.org/wiki/Divergence_of_the_sum_of_the_reciprocals_of_the_primes) that the set of primes is large,
but the [prime number theorem](https://en.wikipedia.org/wiki/Prime_number_theorem) shows that $$\bar{\delta}(\textbf{P})=0$$.
As such, the conjecture extends Szeméredi's theorem to a larger class of sets.

There are also sets containing arbitrary arithmetic progressions which neither are large nor have positive upper density;
you can see the construction of such a set in this [exposition](http://alexricemath.com/wp-content/uploads/2013/06/DensityAndSubstance.pdf) by Alex Rice which also includes related examples.

So, if the conjecture is true we have three nested classes, each of which has some elements not included in the others:
**sets with arbitrary arithmetic progressions** $$\supset$$ **large sets** $$\supset$$ **sets with positive upper density**.

[^1]: Not to be confused with the [Erdős-Turán conjecture](https://en.wikipedia.org/wiki/Erd%C5%91s%E2%80%93Tur%C3%A1n_conjecture_on_additive_bases) on additive bases, another tangentially related problem in arithmetic combinatorics

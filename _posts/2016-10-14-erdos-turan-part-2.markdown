---
layout: post
title: "The Erdős-Turán Conjecture: Part II"
date:   2016-10-14 09:10:00
series: "Arithmetic Combinatorics"
tag: math
---

For a positive integer sequence $$A$$ to have divergent reciprocal sum, it must be sufficiently "dense."
Today we will formalize a notion of density and investigate the boundary between sets with convergent and divergent reciprocal sums.

<span class='definition'>Given a set $$A$$, define the _counting function_ $$\delta_A$$ as</span>

$$\delta_A(n) = |A\cap\{1,\ldots,n\}|$$

that is, $$\delta_A(n)$$ is the number of elements of $$A$$ less than $$n$$.

<span class='definition'>Two functions $$f$$ and $$g$$ are _asymptotically equivalent_, denoted $$f\sim g$$, if</span>

$$\lim_{x\to\infty} \frac{f(x)}{g(x)} = 1$$

<span class='definition'>For a set $$A$$, we say that $$f$$ is an _asymptotic formula_ for $$\delta_A$$ if
$$\delta_A(n)\sim f$$.</span>

The most well-known asymptotic formula is for the primes;
the [prime number theorem](https://en.wikipedia.org/wiki/Prime_number_theorem)
states that $$\pi(n)\sim\frac{n}{\log n}$$.

We use this formula to show that the reciprocal sum of the primes diverges, and then generalize this result to arbitrary sequences.

<div class='lemma'>$$\sum_{p\ prime}\frac{1}{p}=\int_{1}^{\infty}\frac{\pi(x)}{x^2}dx$$</div>

<div class='proof'>

Let the set of primes be \(P=\{p_i\}\), and the prime counting function \(\pi(x)\).
Then,

$$\int_{1}^{\infty}\frac{\pi(x)}{x^2}dx = \sum_{i=1}^{\infty}\int_{p_i}^{p_{i+1}}\frac{i}{x^2}dx
=\sum_{i=1}^{\infty}i\big(\frac{1}{p_i}-\frac{1}{p_{i+1}}\big)$$

$$= 1\big(\frac{1}{2}-\frac{1}{3}\big)+2\big(\frac{1}{3}-\frac{1}{5}\big)
+3\big(\frac{1}{5}-\frac{1}{7}\big)\ldots
=\frac{1}{2}+\frac{1}{3}+\frac{1}{5}+\ldots=\sum_{p\ prime}\frac{1}{p}$$

</div>

Note that this uses no specific information about the primes and thus holds more generally for any set and its counting function.

We need this lemma to pass from the counting function to its asymptotic formula, but I have omitted the proof as it is mostly unrelated.

<span class='lemma'>If $$f, g$$ functions with $$f\sim g$$, then there exists some $$c$$ such that $$f(x)\leq cg(x)$$ and $$g(x)\leq cf(x)$$ for sufficiently large $$x$$.</span>

<span class='theorem'>$$\sum_{p\ prime}\frac{1}{p}\to\infty$$</span>

<div class='proof'>
$$\sum_{p\ prime}\frac{1}{p}=\int_{1}^{\infty}\frac{\pi(x)}{x^2}dx\geq c\int_{1}^{\infty}\frac{\frac{x}{\log x}}{x^2}dx$$ by the lemma.
We solve this as
$$c\int_{1}^{\infty}\frac{1}{x\log x}dx=c\big(\log\log x\ \Big|_1^\infty\big)
=c\big(\lim_{y\to\infty}\log\log y - 0\big)\to\infty$$
</div>

We have seen how the divergent sum of prime reciprocals is a direct result of the asymptotic density of the sequence of primes.
We have also noted that any arbitrary set $$A$$ can be treated by evaluating $$\int_{1}^{\infty}\frac{\delta_A(x)}{x^2}dx$$ in the same fashion.

The next question arises naturally:
can we find a function $$f$$ that divides sets, based on their asymptotic formulae, into those with and without divergent reciprocal sums?
That is, a function $$f$$ where $$\delta_A > f$$ implies $$\sum_{a\in A}\frac{1}{a}\to\infty$$, and $$\delta_A \leq f$$ implies $$\sum_{a\in A}\frac{1}{a}\to c<\infty$$?

I claim that any set $$A$$ with a counting function that is of the form $$\frac{x}{\log^{1+\epsilon}x}$$ (or smaller) has a convergent sum of reciprocals.
This is interesting as our set of primes is very close to the boundary.
A slightly sparser set, e.g. one with density $$\mathcal{O}\big(\frac{x}{\log x\log\log x}\big)$$, will still have divergent reciprocal sum, but you cannot go much sparser until the sum begins to converge.

<span class='theorem'>If $$A$$ is a sequence such that $$\delta_A(x)\sim \frac{x}{\log^{1+\epsilon} x}$$, or $$\delta_A(x)\sim f(x) <\frac{x}{\log^{1+\epsilon} x}$$, then $$\sum_{a\in A}\frac{1}{a}$$ converges.</span>

<div class='proof'>
It is sufficient to prove the case where \(\delta_A(x)\sim \frac{x}{\log^{1+\epsilon} x}\).
Similar to before, we start with the integral:
$$\sum_{a\in A}\frac{1}{a}=\int_{1}^{\infty}\frac{\delta_A(x)}{x^2}dx$$
The antiderivative of this function with the asymptotic formula plugged in comes out to \(-\frac{1}{\epsilon\log^\epsilon x}\) which has an asymptote at \(x=1\).
We will have to be clever to avoid this when evaluating the integral.
We start by splitting it in two:
$$\int_{1}^{\infty}\frac{\delta_A(x)}{x^2}dx=
\int_{1}^{2}\frac{\delta_A(x)}{x^2}dx+
\int_{2}^{\infty}\frac{\delta_A(x)}{x^2}dx$$
The counting function for our sequence \(A\) must necessarily be smaller than that of \(\N\) since \(A\subseteq\N\).
\(\delta_\N\sim x\), so we can bound each integral with a different asymptotic formula.
$$\int_{1}^{2}\frac{\delta_A(x)}{x^2}dx+
\int_{2}^{\infty}\frac{\delta_A(x)}{x^2}dx\leq
\int_{1}^{2}\frac{\delta_\N(x)}{x^2}dx+
\int_{2}^{\infty}\frac{\delta_A(x)}{x^2}dx$$
$$\leq c_1\int_{1}^{2}\frac{x}{x^2}dx+
c_2\int_{2}^{\infty}\frac{\frac{x}{log^{1+\epsilon} x}}{x^2}dx$$
$$=c_1\log 2 + c_2\big(-\frac{1}{\epsilon\log^\epsilon x}\Big|_2^\infty\big)
=c_1\log 2 + c_2\big(0+\frac{1}{\epsilon\log^\epsilon 2}\big)<\infty$$
</div>

We can relate this back to the Erdős conjecture via the contrapositive:

<span class='conjecture'>If $$A$$ is a set of positive integers with no arithmetic progressions longer than $$k$$, then</span>

$$\sum_{a\in A}\frac{1}{a} = c < \infty$$

 Therefore, by the conjecture we would know that a set without arbitrary arithmetic progressions must have a counting function with asymptotic formula $$\frac{x}{\log^{1+\epsilon} x}$$ or smaller.

There is an outstanding question of whether or not this is an appropriate bound.
The upper bound on the density of sets without arithmetic progressions could potentially be much lower than $$\frac{x}{\log^{1+\epsilon} x}$$;
[Gowers](https://mathoverflow.net/questions/13230/erdos-conjecture-on-arithmetic-progressions/25404#25404) in particular is of this view.

It may be interesting and fruitful to look at this more general reformulation of the problem: what is the necessary level of asymptotic density to ensure that a set contains arbitrary arithmetic progressions?
Likewise, how dense can you possibly make a set that contains only limited arithmetic progressions?
It may turn out that the tightest bound is unrelated to the sum of reciprocals conjecture and the bound that it implies.

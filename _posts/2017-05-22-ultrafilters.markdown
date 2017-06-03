---
layout: post
title: "Ultrafilters"
date: 2017-05-22 22:00:00
tag: math
---

<span class='definition'>Given a lattice $$(L,\wedge,\vee,\leq)$$, a _filter_ on $$L$$ is a nonempty set $$F\subseteq L$$ where</span>
1. $$\forall x\in F, \forall y\in L,\ x\leq y\Rightarrow y\in F$$$$$$
2. $$\forall x,y\in F\Rightarrow x\wedge y\in F$$$$$$

A set satisfying the first condition is called an _upper set_, while a set satisfying the second is _downward-directed_.
Upper sets are sometimes called filters in the literature, as in Stanley's [Enumerative Combinatorics](http://www-math.mit.edu/~rstan/ec/ec1.pdf) (p. 282), but upper sets and filters are distinct and have different applications.
For instance, [Birkhoff's theorem](https://en.wikipedia.org/wiki/Birkhoff%27s_representation_theorem) is a statement about upper sets which is _not_ true if you require them to be filters.

The given definition is motivated by algebra:
the filter has a dual known as an _ideal_, given by switching $$\leq,\wedge$$ to $$\geq,\vee$$. The second property buys you some symmetry with the concept of an ideal in ring theory.

A filter is called _proper_ if it is not the entire set.
For the most part we will be dealing with filters on the lattice of subsets of a set $$X$$, written as $$(\P(X),\cap,\cup,\subseteq)$$.

<span class='proposition'>If $$C$$ is a chain of proper filters on $$\P(X)$$, then $$\displaystyle\bigcup_{c\in C}c$$ is a proper filter.</span>
<div class='proof'>
If $Y,Z\in\bigcup c$, then there are filters $Y\in F_Y, Z\in F_Z$ in $C$.
$C$ is totally ordered, so we can say without loss of generality that $F_Y\subseteq F_Z$.
$Y,Z\in F_Z$ and $Y\cap Z\in F_Z$, so $Y\cap Z\in\bigcup c$.
<br><br>
If $Y\in\bigcup c$, $Z\in\P(X)$, and $Y\subseteq Z$, then $F_Y$ contains both $Y$ and $Z$.
Therefore $Z\in\bigcup c$.<br>
If $\bigcup c$ is not proper, then $\emptyset\in\bigcup c$ and $\emptyset\in c$ for some $c\in C$. This cannot be the case as all $c$ are proper.
Thus, $\bigcup c$ is a proper filter.
</div>

<span class='definition'>An _ultrafilter_ $$\ \mathcal{U}\subseteq L$$ is a maximal proper filter on $$L$$. That is, if $$F$$ is a filter and $$\mathcal{U}\subseteq F$$, then either $$\mathcal{U}=F$$ or $$F=L$$.</span>

Not every lattice will have an ultrafilter;
$$(\Z,\min,\max,\leq)$$ has many filters but no ultrafilters.

<span class='lemma'>Every proper filter in $$\P(X)$$ is contained in an ultrafilter.</span>
<div class='proof'>
Let $F$ be such a filter and $\Omega$ the set of proper filters on $\P(X)$.
Consider $\mathcal{F}=\{Y\in\Omega: F\subseteq Y\}$, the set of filters which extend $F$, as the partial order $(\mathcal{F}, \subseteq)$.
If $C\subseteq\mathcal{F}$ is a chain of filters, we know $\cup_{c\in C}c$ is a filter, and it is an upper bound for the chain.
Since all chains are bounded, $\mathcal{F}$ must have a maximal element.
Thus, there is some maximal filter $\mathcal{U}\supseteq F$.
</div>

This statement is usually called the _ultrafilter lemma_.
We proved it with Zorn's lemma, but it is actually equivalent to the weaker [boolean prime ideal theorem](https://en.wikipedia.org/wiki/Boolean_prime_ideal_theorem).
That means there are models of set theory where the ultrafilter lemma is true but Zorn's lemma is false.

Now we'll prove an important property of ultrafilters.
Let us use $$B^c$$ to denote the set complement $$X\setminus B$$.

<span class='theorem'>If $$\ \mathcal{U}\subset\P(X)$$ is an ultrafilter, then $$\forall B\in\P(X)$$ either $$B\in \mathcal{U}$$ or $$B^c\in \mathcal{U}$$.</span>
<div class='proof'>
Suppose that $B,B^c\in \mathcal{U}$.
Then, $B\cap B^c=\emptyset\in \mathcal{U}$, which cannot be the case as $\mathcal{U}$ is a proper filter.
<br><br>
Now, assume $B\notin \mathcal{U}$ and define $\mathcal{U}^+=\mathcal{U}\cup\{Y\subseteq X: \exists u\in \mathcal{U},\ Y\supseteq u\cap B^c\}$.
If $Y\in \mathcal{U}^+$, we know $Y\in \mathcal{U}$ or $Y\supseteq u\cap B^c$ for some $u\in \mathcal{U}$.
<br><br>
Let $\hat{Y}\in\P(X)$ with $Y\subseteq\hat{Y}$; if $Y\in \mathcal{U}$ then $\hat{Y}\in \mathcal{U}$ as $\mathcal{U}$ is a filter.
Otherwise, $u\cap B^c\subseteq Y\subseteq\hat{Y}$, so $\hat{Y}\in \mathcal{U}^+$ as a superset of some $u\cap B^c$.
<br><br>
Let $Y,Z\in \mathcal{U}^+$; if both are in $\mathcal{U}$, then $Y\cap Z\in \mathcal{U}$.
If both are not, then we have $u\cap B^c\subseteq Y,\ v\cap B^c\subseteq Z$ for some $u,v\in \mathcal{U}$.
Then $(u\cap v)\cap B^c$ is a lower bound for $Y,Z$ and so $(u\cap v)\cap B^c\subseteq Y\cap Z$.
$u\cap v\in \mathcal{U}$ by downward-directedness, so $Y\cap Z\in \mathcal{U}^+$.
If $Y\in \mathcal{U},\ Z\supseteq v\cap B^c$, then $(Y\cap v)\cap B^c\subseteq Y\cap Z\in \mathcal{U}^+$.
Thus, $\mathcal{U}^+$ is a filter.
<br><br>
Moreover, if $\emptyset\in \mathcal{U}^+$ then $u\cap B^c\subseteq\emptyset$ for some $u\in \mathcal{U}$.
This means that $u\subseteq B$ and thus $B\in \mathcal{U}$, contradicting our initial assumption.
So $\mathcal{U}^+$ is a proper filter which extends $\mathcal{U}$, and it must be the case that $\mathcal{U}=\mathcal{U}^+$.
Since $(u\cap B^c)\subseteq B^c$, we know $B^c\in \mathcal{U}$.
</div>

An ultrafilter is called _principal_ if it is of the form $$\mathcal{U}_\alpha=\{x\in L: \alpha\leq x\}$$ for some $$\alpha\in L$$.

<span class='proposition'>If $$\mathcal{U}_\alpha \subset\P(X)$$ is a principal ultrafilter, then $$\alpha=\{a\}$$ for some $$a\in X$$.</span>
<div class='proof'>
Let $a\in\alpha$; either $\{a\}$ or $X\setminus\{a\}$ are in $\mathcal{U}$ by the previous theorem.
$\alpha\nsubseteq X\setminus\{a\}$ by construction, so $\{a\}\in\mathcal{U}$.
Thus, $\alpha=\{a\}$ as $\alpha$ cannot be the empty set.
</div>

In a finite lattice, all ultrafilters are principal.
In an infinite lattice we may find ultrafilters that are not based on a single element.
These ultrafilters are called _non-principal_.

<span class='theorem'>If $$|X|$$ is infinite, then there exists a non-principal ultrafilter on $$\P(X)$$.</span>
<div class='proof'>
Let $B=\{A\subset X: A^c\ \text{finite}\}$.
If $Y\in B$, $Y\subseteq\hat{Y}$, then $\hat{Y}^c\subseteq Y^c$, so $\hat{Y}^c$ is finite and $\hat{Y}\in B$.
Any $Y,Z\in B$ have $Y\cap Z=(X\setminus Y^c)\cap(X\setminus Z^c)=X\setminus(Y^c\cup Z^c)$ by De Morgan's law, so $Y\cap Z$ has finite complement $Y^c\cup Z^c$ and $Y\cap Z\in B$.
<br><br>
Thus, $B$ is a filter and is contained in some ultrafilter $A$.
Any finite set $Z$ has $Z^c\in A$, so $Z\notin A$.
Therefore $A$ cannot be principal, as it does not contain $\{a\}$ for any $a\in X$.
</div>

By this construction, we can see what non-principal ultrafilters look like intuitively.
They are filters of co-finite sets and have no minimal element.

Ultrafilters have some interesting applications; in topology, the [compactification](https://en.wikipedia.org/wiki/Stone%E2%80%93%C4%8Cech_compactification) of the naturals $$\beta\N$$ is a topology generated by ultrafilters on $$\N$$.
The elements of $$\N$$ are mapped to the principal ultrafilters, and the non-principal ultrafilters are the sets added to make the space compact.
Ultrafilters have interesting properties in logic, including the aforementioned relationship to the axiom of choice, and are also studied for their own sake as lattice objects.

Another interesting fact is that you can prove the infinite Ramsey's theorem using ultrafilters.

<span class='theorem'>Let $$\chi:\N^2\rightarrow [r]$$ be an infinite $$r$$-coloring of pairs of natural numbers. Then, there is an infinite $$A\subseteq\N$$ where $$|\chi(A^2)|=1$$.</span>

You can see how this theorem is analogous to the finite Ramsey if you think of $$\N^2$$ as representing the edges of a complete graph on countably many vertices.

<div class='proof'>
Fix a non-principal ultrafilter $\mu\subset\P(\N^2)$, and define the mapping $\chi':\N\rightarrow [r]$ as $\chi'(x)=i$ where $\{y:X(x,y)=i\}\in\mu$.
That is, the image of $x$ under $\chi'$ is the color $i$ where the set of all $y\in\N$ connected to $x$ by an $i$-colored edge is in the ultrafilter $\mu$.
<br><br>
We must show $\chi'$ is well-defined. $x$ is connected to every element of $\N\setminus\{x\}$ by a colored edge, so the set is partitioned into $r$ parts based on those colors.
If two of those partitions $A,B$ are in $\mu$, then $A\cap B\in\mu$.
However, we know $A\cap B=\emptyset$ because they are parts of a partition, and $\emptyset\in\mu$ contradicts the fact that $\mu$ must be a proper filter.
Thus, there can be only one such set and $\chi'(x)=i$ is unique.
<br><br>
$\chi'$ partitions $\N$ into $r$ parts by its image.
There must be a unique $i$ such that $B=\{x\in\N: \chi'(x)=i\}$ and $B\in\mu$;
if not, we can derive a contradiction as before.
Moreover, $B$ is a set where each $x\in B$ has a set of neighbors on $i$-colored edges included in the ultrafilter.
$\mu$ is non-principal, so $B$ must be infinite.

We will use induction to prove that there exists a set $A=\{a_i: i\in\N\}$ where $\chi(a_n,a_k)=i$ for all $n,k$.
Select some $a_1\in B$ and assume that the property holds for $\{a_1,\ldots a_n\}$.
<br><br>
Define

$$S_n=B\cap(\bigcap_{j=1}^n\{y\in\N: \chi(a_j,y)=i\})$$
We want to pick $a_{n+1}$ from $S_n$, so we must show it is nonempty and contains elements other than $\{a_1,\ldots, a_n\}$.
We know by the selection of $i$ that $\{y\in\N: \chi(a_j,y)=i\}\in\mu$, because $a_j\in B$ and thus $\chi'(a_j)=i$.
$S_n$ is a finite intersection of sets in $\mu$, so $S_n\in\mu$.
By non-principality of $\mu$, we then know that $S_n$ is infinite.
So, $S_n\neq\emptyset$ and ${a_1,\ldots, a_n}\subsetneq S_n$.
<br><br>
Therefore, we can choose $a_{n+1}\notin\{a_1,\ldots, a_n\}$ from $S_n$, and $\{a_1,\ldots, a_{n+1}\}$ is monochromatic.
By induction, we can construct an infinite monochromatic set $A\subseteq\N$.
</div>

---
layout: post
title: "Infinite Ordinals"
date:   2015-04-03 19:30:00
series: "Goodstein's Theorem"
tag: math
---

In the last post, we generalized one property of the positive integers, that they can be used to measure the *multiplicity* of a collection, to infinite collections and the _infinite cardinals_.
What about *order*, the other interesting property?

The natural numbers are _totally ordered_, meaning that given any two $$n$$ and $$k$$, we can tell which one "more" or "fewer".
Either $$n < k$$, or $$k < n$$, or $$k = n$$.
In a sense, what we are doing is describing _where_ each number belongs when put in order,
in the same way that alphabetical ordering (mathematicians prefer to call it _lexicographic ordering_) tells us _where_ to put words in relation to each other in a dictionary.
Given any list of numbers with no duplicates; say $$4, 1, 7, 8, 14, 193$$; we can put them in ascending order:
$$1 < 4 < 7 < 8 < 14 < 193$$.

In fact, the structure of the natural numbers is even richer than this.
Not only can we put them in order, every natural number $$n$$ has a _direct successor_: a smallest natural number $$k$$ such that $$n < k$$.
In positive integers, our successors are easy to see. The successor to $$1$$ is $$2$$, the successor to $$2$$ is $$3$$, and so on.
Given any $$n$$, its successor is $$n+1$$.

Moreover, the natural numbers are _well-ordered_, meaning any subset of them contains a smallest element.
In the example from above, $$1$$ is smallest element of the set $$\{1,4,7,8,14,193\}$$.

As before, we will consider what happens if we attempt to extend these properties past finite numbers.
What if we imagine some number which is "bigger" every positive integer?
In notation, it is easy to state: let $$\omega$$ be a number such that, for any natural number $$n$$, $$n < \omega$$.
It is clear that $$\omega$$ must be infinite. It couldn't be finite and yet still be "more" than any finite number.

We can formalize this notion of ordinal numbers with a clever recursive definition:

<span class="definition">An **_ordinal number_** $$n$$ is the well-ordered set of ordinal numbers less than $$n$$. Notationally, $$n=\{x : x < n\}$$.</span>

What is less clear is the relationship between $$\omega$$ and $$\aleph_0$$. Are they the same? Are they related?

By the above definition, we can see that $$\omega=\{x : x < \omega\}=\N$$.
Then, the _cardinality_ of $$\omega$$ as a set must be $$\aleph_0$$.

In the same way that $$2$$ is the direct successor of $$1$$, we can consider the successor of $$\omega$$; let's call it $$\omega+1$$.
From here, we can think about $$\omega+2$$, $$\omega+3$$, and so on.
We might again ask: is there is some ordinal which is bigger than $$\omega+n$$, for any natural number $$n$$?
It would make sense to call this number $$\omega+\omega=2\omega$$.

You can see where this is going. This process continues ad infinitum.
So far we've considered two distinct types of ordinals:
_successor ordinals_, which can be expressed as $$x+1$$ for some other ordinal x;
and _limit ordinals_, which cannot.
Limit ordinals are the result of considering the ordinal larger than any $$x+n$$ for some ordinals $$n$$.
As such, while successor ordinals have _direct predecessors_, as $$2$$ is to $$3$$, limit ordinals have no element that directly precedes them in the ordering.

The cardinalities of the infinite ordinals are a little strange, however.
We know that $$\omega$$ has cardinality $$\aleph_0$$, but what about $$\omega+1$$?
Well, $$\omega+1=\{x : x < \omega+1\}=\{\omega,1,2,3\dots\}$$.
This set might look larger than $$\N$$, but we can build a mapping between them:
take $$\omega$$ to $$1$$, $$1$$ to $$2$$, $$2$$ to $$3$$, and so on.
Since this is a bijection between $$\omega+1$$ and $$\N$$, they must have the same cardinality!
You can see how this would generalize to $$\omega+2,\omega+3,\dots,2\omega,\dots$$

Now you can see how **order** and **size** break down and separate when generalized towards infinity.
You can have an infinite ordinal that comes after another in the ordering, like $$\omega<\omega + 1$$, where they both have the same cardinality.
This is a common occurrence in mathematics: as you stretch ideas out to cover more objects, they must often be reinterpreted.

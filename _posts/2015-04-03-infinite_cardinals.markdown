---
layout: post
title: "Infinite Cardinals"
date:   2015-04-03 19:20:00
series: "Goodstein's Theorem"
tag: math
---

In mathematics, one of our main tools for inquiry is _generalization_.
Given an object we are familiar with, we choose a property of that object and ask the questions:

* "To what other objects might this property apply?"
* "How are these new objects related to the familiar one?"

In this example, we will talk about the positive integers, and how we can generalize their properties to address different _kinds_ of infinities.  
The positive integers, often called the _natural numbers_ and denoted $$\mathbb{N}$$ have two properties that currently interest us: **quantity** and **order**.

If you are given a collection of things, you can say _how many_ you have by assigning a natural number to it.
A pair of jeans has four pockets; four describes _how many_ pockets are in the collection.
In mathematics, we call this property of a collection _cardinality_; namely, the number of things in it.
We can compare the sizes of collections, too.
A set of four pockets and a set of four coins have the same cardinality.
We can pair them up without any left over; every pocket has exactly one coin in it, and every coin resides in exactly one pocket.
We call this a _one-to-one correspondence_, or _bijection_.

What happens when you have a large collection? We can assess the cardinality of familiar collections and assign them each a positive integer.
If the universe is of finite size, it can only contain a finite number of stars.
Thus, there is some positive integer large enough to describe it.  
Similarly, we can ask: what is the cardinality of the set of positive integers?  
If we pick any positive integer $$k$$ and say the cardinality of $$\mathbb{N}$$ is $$k$$, we would be wrong;
$$\mathbb{N}$$ contains the number $$k+1$$, so there is no way it could have only $$k$$ elements.
But, this goes for _any_ positive integer $$k$$.
So, the set of positive integers has a cardinality that cannot be named by any positive integer.

It certainly _has_ a cardinality, though. There are objects in the collection, so its size isn't zero.
And there are other collections of the same size, too; consider the collection of regular polygons, or the collection of perfect squares.
Any regular polygon has a positive integer number of sides, so we can pair each positive integer $$n$$ with the regular $$n$$-sided polygon.
Similarly, any perfect square is some $$2^k$$, where $$k$$ is a positive integer; we can pair them up in the same way.

Since there are many collections of this same cardinality, it makes sense to it a name.
We call it _aleph null_, commonly notated as $$\aleph_0$$.
A number we can assign to the size of a set is known as a _cardinal_.
Positive integers are cardinals, as we well know. But $$\aleph_0$$ is also a cardinal; it just happens to be an _infinite_ cardinal.
We've discovered that there is at least one infinite "number" with the same *multiplicity*-measuring properties as the friendly and finite positive integers.
In fact, there are infinitely many such infinite cardinals, and $$\aleph_0$$ is the smallest; moreover, the rest of the infinite cardinals are qualitatively different from aleph null. We will demonstrate their existence in
<a class="page-link" href="{{ site.baseurl }}">Rigour Warning: Infinite Cardinals</a>. (Coming Soon)

So far, we have generalized one property of the familiar natural numbers, that they can be used to measure the size of collections, to a less-familiar object:
an infinite cardinal.
Our original notion of quantity was tied to the positive integers, but upon further inspection it seems to be a more general concept.

When we think of positive integers, we tend to think of quantity and order as being the same property:  
3 is _bigger_ than 2, which also means 3 _comes after_ 2 in an ordering.
In the next post, we will look at generalizing this second property, **order**, to get an even-less-familiar object: an infinite ordinal.
Moreover, we will see how quantity and order become distinct, different notions when generalized to infinite objects.

### <a class="page-link" href="{{ site.baseurl }}">Rigour Warning: Infinite Cardinals</a> (Coming Soon)

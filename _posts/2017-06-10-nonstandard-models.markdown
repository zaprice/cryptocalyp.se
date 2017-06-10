---
layout: post
title: "Non-Standard Models of Peano Arithmetic"
date:   2017-06-10 12:00:00
tag: math
---

Informally, a _model_ $$\mathfrak{U}$$ of an axiom system $$T$$ is an assignment of the symbols in $$T$$ to objects in $$\mathfrak{U}$$ such that every formula provable in $$T$$ is true in $$\mathfrak{U}$$.
In other words, a model is a structure that fits the axioms of $$T$$.
A familiar example is group theory, or **GT**, which has many models.
Structures like the symmetries of an $$n$$-gon $$D_n$$, or the integers under addition $$(\Z,+)$$ are models of group theory.

In Peano arithmetic, the _standard model_ is the structure we intended to study with **PA**: the natural numbers $$\N$$, with the successor function, addition, and multiplication defined in the usual ways.
Interestingly, **PA** admits multiple models in the same way **GT** does.

Today we're going to take a mostly-informal look at a non-standard model of **PA**.
To start, we posit that there is an additional element $$z$$ distinct from all the elements we already know about.
We introduce a new constant symbol $$z$$ to the language of $$T$$ and add countably many axioms stating that $$z\neq 0$$, $$z\neq s(0)$$, $$z\neq s(s(0))$$, etc.
We know that the theory $$T$$ with the addition of our new axioms must have a model by the [compactness theorem](https://en.wikipedia.org/wiki/Compactness_theorem).

$$z$$ is an element of **PA** and has a successor $$s(z)$$, along with $$s(s(z))$$, $$s(s(s(z)))$$, and so on.
You might think that this means our structure looks something like the ordinals, with $$\{0, 1,2,\ldots\}\cup\{\omega,\omega+1,\omega+2,\ldots\}\cup\ldots$$, but we can show that $$z$$ must have an infinite chain of predecessors as well.

We prove that in **PA**, every element is either 0 or has a predecessor.
I will be using the inference rules and axiom abbreviations for first-order logic and **PA** from [Halbeisen's Combinatorial Set Theory](https://people.math.ethz.ch/~halorenz/publications/pdf/cst.pdf) (pp. 27 - 32).

<div class="theorem">
$$\forall x((x=0)\lor(\exists y(s(y) = x)))$$
</div>
<div class="proof">
<div style="display: flex;">
<div>
$$\ $$
$$(P\!A_7)$$
$$(L_{16})$$
$$(L_6)$$
$$(\text{Inference})$$
$$(L_{13})$$
$$(L_{16})$$
$$(L_{18})$$
$$(\text{Inference})$$
$$(L_6)$$
$$(\text{Inference})$$
$$(L_1)$$
$$(\text{Inference})$$
$$(\text{Generalization})$$
$$(L_5)$$
$$(\text{Inference})$$
$$(\text{Inference})$$
$$(\text{Inference})$$
</div>
<div>
$$\varphi(x) := (x=0)\lor(\exists y(s(y) = x))$$
$$\varphi_1 := (\varphi(0)\land\forall x(\varphi(x)\rightarrow\varphi(s(x))))\rightarrow\forall x\varphi(x)$$
$$\varphi_2 := 0=0$$
$$\varphi_3 := \varphi_2\rightarrow(\varphi_2\lor\exists y(s(y)=0))$$
$$\varphi_4 := (0=0)\lor\exists y(s(y)=0)$$
$$\varphi_5 := (s(x)=s(x))\rightarrow\exists y(s(y)=s(x))$$
$$\varphi_6 := x=x$$
$$\varphi_7 := s(x)=s(x)$$
$$\varphi_8 := \exists y(s(y)=s(x))$$
$$\varphi_9 := \varphi_8\rightarrow((s(x)=0)\lor\varphi_8)$$
$$\varphi_{10} := (s(x)=0)\lor\exists y(s(y)=s(x))$$
$$\varphi_{11} := \varphi(s(x))\rightarrow(\varphi(x)\rightarrow\varphi(s(x)))$$
$$\varphi_{12} := \varphi(x)\rightarrow\varphi(s(x))$$
$$\varphi_{13} :=\forall x(\varphi(x)\rightarrow\varphi(s(x)))$$
$$\varphi_{14} := \varphi_4\rightarrow(\varphi_{13}\rightarrow(\varphi_4\land\varphi_{13}))$$
$$\varphi_{15} := \varphi_{13}\rightarrow(\varphi_4\land\varphi_{13})$$
$$\varphi_{16} := \varphi_4\land\varphi_{13}$$
$$\varphi_{17} := \forall x(\varphi(x))$$
</div>
</div>
</div>

So $$z$$ must have an infinite sequence of predecessors in addition to having as many successors.
This means our model has at least one copy of something like $$\Z$$, all the elements of which are unreachable from the initial segment $$\N$$ through finite addition.

Now we consider multiplication.
There will be additional copies of the $$z$$ segment, centered on $$2\times z$$, $$3\times z$$, and so on.
Each of these segments is disconnected from every other;
as an example, $$2\times z=z+z\neq z+k$$ for any finite k, and thus no number of iterated successor operations will get you from $$z$$ to $$2\times z$$.

At this point, our model looks something like $$\N+\Z\times\Z$$;
a one-sided initial segment along with countably many two-sided segments which are ordered.
However, there are even more copies of $$\Z$$ in this model.

We state without proof that every element in **PA** is even or odd.
Then, either $$z/2$$ or $$(z+1)/2$$ must be an integer.
More generally every $$n\!\!\mod k\in\{0,1,\ldots,k-1\}$$, so $$(z+j)/k$$ is an integer for some $$0\leq j < k$$.
As before, any such element is unreachable by finite addition from any other segment.
We end up with an unbounded, countable, dense, linearly-ordered set of $$z$$ segments.
Any such set is isomorphic to $$\Q$$, so our model looks like $$\N+\Z\times\Q$$.

And finally, the application of [incompleteness](https://en.wikipedia.org/wiki/G%C3%B6del%27s_incompleteness_theorems#First_incompleteness_theorem) that we've all been waiting for.
A statement $$s$$ in a consistent theory $$T$$ is called *independent* if:
* $$T$$ cannot prove $$s$$ or its negation
* $$T\cup s$$ and $$T\cup\neg s$$ are both consistent

By incompleteness, any sufficiently strong theory contains independent statements.
A theory is consistent *<u>if and only if</u>* it has a model, so there are some models of $$T$$ where $$s$$ is true and some where it is false.[^1]

We all know some independence results; the axiom of choice is independent from **ZF**, the continuum hypothesis is undecidable in **ZFC**, etc.
But are are there any such statements that are "natural," that can be understood intuitively?
Or are they all Gödel sentences and [large cardinal](https://en.wikipedia.org/wiki/List_of_large_cardinal_properties) axioms: statements whose truthiness evokes indifference?

One example is [Goodstein's theorem](https://en.wikipedia.org/wiki/Goodstein%27s_theorem), an elementary statement about arithmetic that is undecidable in **PA**.
The theorem is provable in some extensions of **PA**, but it is false for the model we saw today.
There are other examples of combinatorial or number-theoretic statements independent of **PA**, like the [Paris-Harrington theorem](https://en.wikipedia.org/wiki/Paris%E2%80%93Harrington_theorem) or the termination of one-player hydra games.

Another way to think about independence is via the second incompleteness theorem.
These statements require a certain [countable ordinal](https://en.wikipedia.org/wiki/Epsilon_numbers_(mathematics)) to prove, the existence of which is enough to prove the [consistency of **PA**](https://en.wikipedia.org/wiki/Gentzen%27s_consistency_proof) itself.
Thus they must be independent, as no system can prove its own consistency.

[^1]: Combinatorial Set Theory, p. 42

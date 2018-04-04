---
layout: post
title: "Compactness, Three Ways"
---

We all know the definition of compactness from topology: every open cover admits a finite subcover.
Then there's the compactness theorem from first-order logic that I mentioned in a [previous post]({{site.baseurl}}{% post_url 2017-06-10-nonstandard-models %}): a set of first-order sentences has a model if and only if every finite subset has a model.
And in Ramsey theory there's the compactness principle:

<span class="theorem">Suppose $$H=(V,E)$$ is a hypergraph with no infinite edges. If for all finite $$W\subset V$$ the induced subgraph $$H[W]$$ is $$r$$-colorable, then $$H$$ is $$r$$-colorable.</span>

We have these three ideas called "compactness," and they all have something in common: they allow you to conclude that some particular property of an infinite object has been inherited from a finite sub-object.

* If $$O$$ is a set of open sets which covers $$T$$, then there is some finite subset $$U\subseteq O$$ which covers $$T$$
* If $$\Sigma$$ is an inconsistent set of first-order sentences, then there is some finite subset $$\sigma\subseteq\Sigma$$ which is inconsistent
* If $$H$$ is a hypergraph which is not $$r$$-colorable, then there is some finite induced subgraph $$H[W]$$ which is not $$r$$-colorable

In particular, there is nothing special about the infinite-ness of the set which gives it that property.
Unlike how, say, the line segment $$(0,1)$$ has positive measure as a consequence of its infinite-ness, not because it contains a finite set of positive measure.

These statements are not just conceptually similar but mathematically related. As we will show, the compactness theorem and compactness principle can both be proved with [Tychonoff's theorem](https://en.wikipedia.org/wiki/Tychonoff%27s_theorem).
Specifically we need only the fact that Tychonoff's theorem holds for Hausdorff spaces, which is equivalent to the ultrafilter lemma and the [BPI theorem](https://en.wikipedia.org/wiki/Boolean_prime_ideal_theorem).
We can also prove the ultrafilter lemma from the compactness theorem, and the proof sketch at the end gives an idea of how it's equivalent to the compactness principle.

First, the proof of the compactness principle.
<div class='proof'>
We will use the notation \([r]=\{1,2,\ldots,r\}\).
Let \(T\) be the set of all possible colorings of the vertices of \(H\) with \(r\) colors. \(T=\{f:V\rightarrow [r]\}\), or considered another way, \(T=V\times [r]\).
<br>
<br>
Let \([r]\) have the discrete topology: every subset is open (and also closed), and it has a basis \(\{1\},\ldots,\{r\}\).
This gives \(T\) the product topology.
Since \([r]\) is compact as a finite topological space, we can apply Tychonoff's theorem and conclude \(T\) is also compact.
<br>
<br>
Given an index set \(I\) for \(V\), the basis for the product topology on \(T=V\times[r]\) is the set of products \(\prod_{i\in I}\epsilon_i\) where finitely many \(\epsilon_i\in[r]\) and the rest are \(\epsilon_j=[r]\).
Moreover, each basis element is also closed as its complement is a union of other basis elements.
Given a finite set of indices \(J=\{j_1,\ldots,j_n\}\subset I\), we can notate a basis element as \(S(j_1,\ldots,j_n,\epsilon_1,\ldots,\epsilon_n)\) where \(W=\{v_{j_k}\in V : j_k\in J\}\) are vertices with fixed colors \(f(v_{j_k})=\epsilon_k\) for any \(f\in S(j_1,\ldots,j_n,\epsilon_1,\ldots,\epsilon_n)\).
<br>
<br>
If \(W\subset V\) is a finite set of vertices, let \(F_W=\{f\in T :\forall\{v_1,\ldots,v_n\}\subset W,\{v_1,\ldots,v_n\}\in E,\ \exists i,j,\ f(v_i)\neq f(v_j)\}\), the set of functions which are not monochromatic on any edge in \(H[W]\), or otherwise the set of \(r\)-colorings of \(H\) which are proper when restricted to \(H[W]\).
<br>
<br>
Each \(W=\{v_{j_k}\in V : j_k\in J\}\) is a finite set of vertices and there are a finite number of colors, so \(F_W\) is necessarily finite.
Thus, it is open in \(T\) as a union of basis elements  \(S(j_1,\ldots,j_n,\epsilon_1,\ldots,\epsilon_n)\) where \(\epsilon_1,\ldots\epsilon_n\) are proper \(r\)-colorings of \(W\),
and closed as a finite union of closed sets.
Additionally, each \(F_W\) is nonempty as we assumed all finite induced subgraphs are \(r\)-colorable.
<br>
<br>
If \(W\subset W'\), then \(F_{W'}\subseteq F_W\) as any proper coloring of the larger set must also be proper on the smaller set.
Thus, for any \(W_1,\ldots,W_m\) finite subsets of \(V\), we know \(F_{W_1\cup\ldots\cup W_m}\subseteq F_{W_1}\cap\ldots\cap F_{W_m}\) or that any coloring which is proper on all \(W_i\) together must be proper on each subgraph individually.
<br>
<br>
\(W_1\cup\ldots\cup W_m\) is finite, so \(F_{W_1\cup\ldots\cup W_m}\neq\emptyset\). Thus \(F_{W_1}\cap\ldots\cap F_{W_m}\) is nonempty, and so \(\mathcal{F}=\{F_W : W\subset V,\ W\ finite\}\) is a family of closed sets satisfying the finite intersection property.
As \(T\) is compact, we can conclude that \(\bigcap_{F\in\mathcal{F}}F\neq\emptyset\);
that is, there exists some \(f\in T\) which is proper on \(H[W]\) for any finite set of vertices \(W\).
Every edge \(X\in E\) is finite, so \(X\) is a finite subset of \(V\) and \(f\in F_X\).
Thus, \(f\) is proper on every edge of \(H\) and is the desired \(r\)-coloring.
</div>

The proof of the compactness theorem of first-order logic is similar.
We would like to show that the set $$\Sigma$$ of well-formed formulae is consistent if every finite subset is consistent.
The vertex set $$V$$ is replaced by the set of statements $$S$$ used to generate $$\Sigma$$.
Rather than a set $$[r]$$ of colors, we have $$\{0,1\}$$ representing whether a statement is true or false.
An edge $$e\in E$$ of the hypergraph is now a formula $$e\in\Sigma$$ which connects statements rather than vertices, and formulae are finite by definition.
We are looking for some truth value mapping $$f:S\rightarrow\{0,1\}$$ for the statements in $$S$$ such that every formula in $$\Sigma$$ is satisfied, i.e. there are no contradictions.

The proof works the same as before.
We give $$\{0,1\}$$ the discrete topology and $$T=S\times\{0,1\}$$ the corresponding product topology.
As we assume every finite subset of formulae $$W\subset\Sigma$$ is satisfiable, there are corresponding sets $$F_W$$ of consistent truth assignments.
$$T$$ is compact by Tychonoff's theorem, so again we have a family $$\mathcal{F}=\{F_W : W\subset \Sigma,\ W\ finite\}$$ of closed sets a with nonempty intersection.
Thus, there is some truth assignment which renders $$\Sigma$$ consistent.

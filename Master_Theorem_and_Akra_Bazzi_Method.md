
# Table of Contents

1.  [Master's Theorem](#orgeec0dce)
    1.  [Case 1](#org2b769a7)
    2.  [Case 2](#org2cda39c)
    3.  [Case 3](#orgf2d9bf3)
2.  [Akra-Bazzi Method](#orgda2283d)



<a id="orgeec0dce"></a>

# Master's Theorem

`Master Theorem`, also known as Master Method, provides asymptotic analysis (*i.e.* the time complexity) for many of the recursion algorithms that follow the pattern of divide-and-conquer.
Master Theorem is an advanced technique to estimate the time complexity of certain recursive algorithms. It does not apply to all recursion algorithms.

One can apply the master theorem to calculate the time complexity of the following type.

<div class="org-center">
<p>
<i>T(n) = a.T(/n/b) + f(n)</i>
</p>
</div>

where *f(n)* is the time complexity that it takes to divide the problems into subproblems and also to combine the results from the subproblems.
We can further represent *f(n)* as O(n<sup>d</sup>) and d≥0.

Then, Master Theorem provides us three formulas to calculate the time complexity of the recursion algorithm, according to the relationship among a, b, d.
They are stated as follows:

1.  if a > b<sup>d</sup> i.e d < log<sub>b</sub> a, then *T(n)* = O(n<sup>log</sup><sub>b</sub><sup>a</sup>)
2.  if a = b<sup>d</sup> i.e d = log<sub>b</sub> a, then *T(n)* = O(n<sup>d</sup> *logn*)
3.  if a < b<sup>d</sup> i.e d > log<sub>b</sub> a, then *T(n)* = O(n<sup>d</sup>)


<a id="org2b769a7"></a>

## Case 1

<div class="org-center">
<p>
<i>T(n)</i> =O(n<sup>log</sup><sub>b</sub><sup>a</sup>)
</p>
</div>

Binary tree traversal related algorithms where one needs to traverse a binary tree in order to solve the problem.

When using DFS, b = 2, a = 2, d = 0. The reason behind *f(n)* = *O(1)* is twofold:

1.  The effort to split the problems in DFS is constant, since the input is already organized as a collection of subproblems, i.e. children subtree
2.  The effort to combine the results from the recursion calls is also constant

As a result, by applying the Master Theorem, we can obtian the time complexity of DFS recursion algorithm, as follows:

Since a = 2, b = 2, so d < log<sub>b</sub> a, i.e. 0 < log<sub>2</sub> 2 = 1, therefore *T(n)* = *O(n)*


<a id="org2cda39c"></a>

## Case 2

<div class="org-center">
<p>
<i>T(n)</i> = O(n<sup>d</sup> <i>logn</i>)
</p>
</div>

Binary search

a = 1, b = 2, d = 0, so d = log<sub>b</sub> a i.e. 0 = log<sub>2</sub> 1, therefore *T(n) = O(logn)*


<a id="orgf2d9bf3"></a>

## Case 3


<a id="orgda2283d"></a>

# Akra-Bazzi Method

This is a generalization of the Master's theorem in order to deal with cases where subproblems are of different size.
It is used to analyse the asymptotic behaviour of the mathematical recurrences that appear in the analysis of divide and conquer algorithms where the sub-problems have substantially different sizes.
It is named after mathematicians Mohamad Akra and Louay Bazzi.


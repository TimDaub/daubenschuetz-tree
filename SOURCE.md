# daubenschütz tree - a content-aware merkle tree

Author: Tim Daubenschütz

Date: March 5, 2021

## Abstract

We introduce daubenschütz tree, a content-aware merkle tree. A daubenschütz tree
is content-aware making it possible to prove the inclusion of and identity of a
specific data point in a data block.

## Specification

A daubenschütz tree $t$ is a tree of hashes in which each leave is an list $l$
with an arbitrary number of elements $e_i$ where $i$ for $i \in \N_0$
represents the index of $e$ within $l$, e.g. $l(1337) = e_{1337}$. For $i = 0$,
we call $e_0$ the _value_ $v$ of $l$ and all following $e_i$, where $i > 0$ the
_keys_ $k_i$. Hence, we can write $l$ as $l(v, k_0, k_1, ...)$.

A hash function $h(x)$, where $x$ represents an arbitrarily-sized bytearray.
Its digest $d$ for $d = h(x)$ can be represented as a bytearray too. For any
$x$ as input in $h(x)$, the length (or bit **c**ount) $c_h$ of $d$ is fixed. In
the case of the popular hash function $SHA-256$ or $h_{SHA-256}(x)$, any
arbitrarily-sized input $x$ has a bit count $c_h = 512$ bits.

To insert a new leave in an empty tree $t$, we insert its first leave $l_0("a",
"hello", "world")$ as follows:

1. We take $l_0(v, k_0, k_1)(0) = v$ and supply it to $h(v) = d_v$.
2. For each $k_i$ of $l_0$, we also supply them in sequence to $h(k_i) =
   d_{k_i}$.
3. Finally, we compute the root hash $r_{l_0}$ of $l_0$ with $r_{l_0} = h(d_v +
   d_{k_i} + d_{k_i+1} + d_{k_i+2}...)$.

## References


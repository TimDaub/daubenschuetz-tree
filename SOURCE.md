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
_keys_ $k_j$ ($j \in \N). Hence, we can write $l$ as $l(v, k_1, k_2, ...)$.

A hash function $h(x)$, where $x$ represents an arbitrarily-sized bytearray.
Its digest $d$ for $d = h(x)$, where $l_d$ represents the byte length of $d$ is
a property of $h$. E.g. in the case of $h_{SHA-256}(x)$, any arbitrarily-sized
input $x$ has a fixed-length digest $d$ of length $l_d = 512$ bits. $d$ can be
represented as a bytearray too.



For an empty tree $t$, we just insert $t$ and build the tree by hashing


Building the daubenschütz tree from the leaves through layered hashing using
a function $h(x) = y$, where 

## References


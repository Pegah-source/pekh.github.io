---
layout: post
title: "Fenwick Tree"
date: 2024-09-15
categories: competitive-programming
---



## Fenwick Tree (Binary Indexed Tree)

A **Fenwick Tree** (also **Binary Indexed Tree (BIT)**) is a useful data structure to  **calculate sum of a consecutive subset** (also known as Range Sum Query (RSQ)) in an ordered set.


The advantage is that we can use it to update elements efficiently, in **O(log n)**.


Another cool thing: we can use bit manipulation techniques for more efficiency.


Each node is responsible for the sum of elements in a coonsecutive subset; which one? the node $i$ keeps the sum for the subset $\[(i - LSOne(i)+1), ..., i\]$. ($LSOne(i)$ for a binary number gives the least significant bit that is one. For example, for $6$ it would be $2$.)

Why is it structured like this? becuase then we can easily and efficiently:
1- compute $rsq(i,j)$
2- update the value of an item at index $i$ (and the tree accordingly)

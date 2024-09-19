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
1. compute $rsq(i,j)$
2. update the value of an item at index $i$ (and the tree accordingly)

First, if we want to compute $rsq(i,j)$, we can just calculate $rsq(1,j)$ and $rsq(1, i-1)$ and the substract them from eachother; so it boils down to computing $rsq(1,i)$.

if $i^{\prime} = i - LSOne(i)$ (what is does is simply removing the least significant one-bit and keeping the rest) did you what happened there? :D we had the node $i$ responsible for the subset $\[(i - LSOne(i)+1), ..., i\]$, and then the node $i^{\prime}$ is responsible for $\[(i^{\prime} - LSOne(i^{\prime})+1), ..., (i - LSOne(i))\]$, and ... ; so, if we continue like that, till reaching zero, we get the sum of all elements from $1$ to $i$.
$$rsq(1,i) = n_{i} + n_{i^{\prime}} + n_{i^{\prime \prime}} ...$$

The complexity? $O(log n)$.


Secondly, we want to update the element at the index $i$, Let's say we want to add $v$ to it : what nodes would this update affect? all the nodes such as $j$ where $ i \in \[(j - LSOne(j)+1), ..., j\]$; what are those? those that when you drop their least significant one-bit are less than $i$ but are larger than $i$: this part is slightly more tricky to digest, but the logic behind it is that we shouold start from $i$ and add something to it to push the least significant one-bit further. It is beacuse as long as this one-bit goes further, the remaining number would be larger than $i$ after removing it. To push this one-bit further, we can add the value of the least significant one-bit to it: $\[(i + LSOne(i)), (i + LSOne(i) + LSOne(i + LSOne(i))), ...\]$

The complexity? again $O(log n)$.


### Simple Implementation
The implementation is taken from the book Competitive Programmingn book 1, by Steven and Felix Halim and Suhendry Effendy.

\\\
```cpp

#define LSOne(S)   ((S) & (-S))
typedef vector<int> vi;

class FenwickTree {
private:
    vi ft;

public:
    FenwickTree(int n) {
        ft.assign(n + 1, 0);  // Fenwick Tree is 1-based index, so size n+1
    }

    // Function to update the Fenwick Tree with a new value at index idx
    void update(int i, int value) {
        while (idx <= n) {
            BIT[idx] += value;
            i += i & -i;  // Move to the next responsible node
        }
    }

    // Function to compute the prefix sum from index 1 to idx
    int query(int i) {
        int sum = 0;
        while (i > 0) {
            sum += BIT[i];
            i -= i & -i;  // Move to the parent node
        }
        return sum;
    }

    // Function to get the sum in the range [l, r]
    int rsqe(int i, int j) {
        return query(i) - query(i - 1);
    }
};
\\\



Things to still add: Other operations that can be done on Fenwick Tree, their complexity, and the complete implementation.

---
layout: post
title: "Articulation Points"
date: 2024-09-15
categories: competitive-programming
---



## Articulation Points & Bridges in an Undirected Graph

[Disclaimer: All (or almost all) that is explained here is from the Steven and Felix Halim and Suhendry Effendy book.]

Articulation point in a graph: if you take out this node, your graph will split up in two parts .....
Bridge: the same thing would happen if you take such an edge out .....



The goal is to find such nodes or edges in an undirected graph.
I have never really used this algorithm in any problem I have solved, as far as I remember :U ... but it's a fun one, like it has those moments where you go : Aaaaaaaaaaaa, that's why :U (this thing: :U is such a mood)(I should just quit writing otherwise I will just continue jabbering and babbering about nonesense, so, let's stop it here)


What would be the stupid way to find such vertices or edges? Just take out each node or edge one by one and check if the graph remains connected. The complexity would be O(Vx(V+E)), one is for taking out each node/edge, and the other for an algorithm to run through the graph, BFS or DFS, and check if we can access all nodes starting from one.


But let's be wiser, and make some changes to DFS to make it serve our goal better; define two numbers to store for each node when applying DFS:
1. `dfs_num` : The iteration at which we visit a node
2. `dfs_low` : If `R` is the set of nodes in the DFS spanning subtree rooted at `u`, then `dfs_low` is the lowest `dfs_num` that can be found in `R` **OR** among the ones not in `R` but reachable by a back edge from `R`.


**ADD A VISUALIZATION OF THE DFS AND ASSIGNING THE DFS_NUM AND DFS_LOW**



Let's say we have done DFS over the graph and now we have all the numbers we wanted to store.
consider a vertex `u` connnected to `v`, and add the condition `dfs_low(v)` $\geq$ `dfs_num(u)`
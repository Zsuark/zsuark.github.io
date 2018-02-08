---
layout:   post
title:    "Database and Graph Theory review"
date:     2018-02-08 06:30:00 +0100
category: architecture
tags:     ["software development", "software architecture", "databases", "nosql", "Graph Theory"]
---


# Database Review

This last week, I have been doing a lot of research/review and experimentation with authentication, security and databases. So, this week's blog posts are more of a "brain dump" than proper articles.

Just to remind you we are currently building a social media application using Clojure and Ring.


# Databases / Persistence Stores

The concept of "database" is often associated with relational database. However relational databases are best suited for well, relational data - data that is represented well in tabular form. Databases persist data, so they are also called persistence stores. OK, I may be over-simplifying things here, but our purpose is to persist state.

There is a miriad of options available these days, and a lot of difficult choices to make. It is overwhelming.

Document and Graph databases offer flexibility and ways of modeling data that may be better for our social application, so I have been researching NoSQL databases.

Be aware that the most readily available material on the internet regarding databases / persistence stores is usually quite biased by opinion and vendors. (This blog post is **not** exempt!)


# Sample database readings

- [Choosing the right NoSQL database for the job: a quality attribute evaluation](https://journalofbigdata.springeropen.com/articles/10.1186/s40537-015-0025-0)
- [Graph Database (Wikipedia)](https://en.wikipedia.org/wiki/Graph_database)
- [ArangoDB](https://en.wikipedia.org/wiki/ArangoDB) - could be a good choice
- [Neo4j](https://en.wikipedia.org/wiki/Neo4j) - another good choice
- [Research on architecture and query performance based on distributed graph database Neo4j](http://ieeexplore.ieee.org/document/6703387/?reload=true)


# Graph Theory

Graph databases are based on Graph theory. Below are my notes from reviewing the [Mathigon](https://mathigon.org/course/graphs-and-networks) and other site (below).

These notes are far from complete, and don't even start to cover off on graph database theory &mdash; but it is a start on graph theory, which form the basis of graph databases theory.

- Point are called **vertices** (1 vertix, 2+ vertices) may also be known as nodes.
- Connecting lines are called **edges**
- If the edges only go one way, the graph is called a **directed** graph
- If there are discontinuous segments in the graph, it is a **disconnected** graph
- Graphs may contain multiple edges which connect to themselves &mdash; **loops**
- We can create new graphs from an existing graph by removing vertices and edges - these are called **subgraphs**.
- The **order** of a graph is the number of vertices.
- The **degree** of a vertix is the number of edges connected to the vertix.
- Graphs which have a single ring of vertices are called **cycles**. All cycles have the same number of edges and vertices.
- If all vertices are connected to every other vertix, then there are (n * (n - 1))/2 edges, where n is the number of vertices. **Kn = (n * (n -1))/2**
- **Bipartite** graphs are graphs which are split into two groups (or sets). Each vertix in a set is connected to all vertices in the other set, but none in it's own. If x is the number of vertices in the first set, and y is the number of vertices in the second set - then there are x * y edges. Kxy = x * y
- Graphs that can be drawn without overlapping edges are called **planar** graphs.
- In a planar graph, the areas bounded by edges and vertices are called **faces**.
- _Faces + Vertices = Edges + 1_ or _F + V = E + 1_


# Sample Graph Theory readings

- [Graph Theory on brilliant.org](https://brilliant.org/wiki/graph-theory)
- [Graph Theory by Keijo Ruohonen](http://math.tut.fi/~ruohonen/GT_English.pdf)
- [Graph Theory on Mathigon](https://mathigon.org/course/graphs-and-networks)
- [A Gentle Introduction To Graph Theory](https://medium.com/basecs/a-gentle-introduction-to-graph-theory-77969829ead8)


# That is all...

..for the moment &mdash; except also check out the [quick review of authentication and security](/architecture/2018/02/08/authentication-review/) that I have been doing this week.

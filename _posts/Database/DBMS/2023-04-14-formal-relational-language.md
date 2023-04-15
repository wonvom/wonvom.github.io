---
title: Formal Relational Language
author: wonvom
date: 2022-04-14 18:42:00 -0800
categories: [Database, DBMS]
tags: [database, sql, relational, model, algebra, calculus, datalog]
math: true
pin: false
---

# Relational Model & Datalog

## Introduction to Datalog

In this blog, we will explore the basics of Datalog, a powerful query language used in various domains, such as data querying, machine learning on relational data, artificial intelligence & knowledge representation, and distributed systems. We will focus on a subset of Datalog called nonrecursive Datalog.

### Key Takeaways:

* Datalog is widely used in data querying, AI, machine learning, and distributed systems.
Nonrecursive Datalog is a simplified version of Datalog that is easier to understand and work with.
* Datalog uses rules to query data, which can be combined and extended using operators like union, negation, and comparisons.
* Understanding Datalog examples and rules will help you see how the language can be used in practical scenarios.

### Datalog Basics

Datalog consists of facts, queries, and rules. Facts are tuples that represent data, while queries and rules are used to extract information from that data. Let's consider the following facts:

```
Movie(mid, title, year, total-gross)
Actor(aid, name, b-year)
Plays(mid, aid)
```

```
Q :- Movie (2, 'Godfather I', 1972, 400)
Q :- Movie (8, 'Godfather II', 1974, 390)
Q :- Actor (9, 'Robert De Niro', 1943)
```

The above facts describe movies, actors, and the roles that actors play in movies. Now let's see some examples of Datalog rules and how they can be used to query this data.

### Example Queries

1. Movies that were produced in 1998 and made $20:
```
Q1(y) :- Movie (x, y, 1998, 20)
```

2. Actors who played in a movie whose total gross is $20:
```
Q2(y) :- Actor (x, y, z), Plays (t, x), Movie (t, v, w, 20)
```

3. Actors who played in a movie whose total gross is $20 and a movie made in 1998:
```
Q3(y) :- Actor (x, y, z), Plays (t, x), Movie (t, v, w, 20), Plays (9, x), Movie (9, 1, 1998, h)
```

### Using Union and Comparisons
Datalog allows us to use the union of rules and comparison operators like "=", "<", and ">" in rules. Let's see an example that demonstrates this:

4. Actors who played in a movie with a gross of $20 or a movie made in 1990:
```
Q4(y) :- Actor (x, y, z), Plays (t, x), Movie (t, v, w, 20)
Q4(y) :- Actor (x, y, z), Plays (t, x), Movie (t, v, w, 1990)
```

5. Actors who played in a movie with a gross of more than $20 or a movie made after 1990:
```
Q5(y) :- Actor (x, y, z), Plays (t, x), Movie (t, v, w, f), f > 20
Q5(y) :- Actor (x, y, z), Plays (t, x), Movie (t, v, w, f), w > 1990
```

### Using Negation
Datalog also supports negation in rules. For example:

6. All actors who did not play in a movie with Robert De Niro:
```
U(x, y, z) :- Actor (x, y, z), Plays (t, x), Plays (t, f), Actor (f, 'Robert De Niro', g)
Q6(y) :- Actor (x, y, z), not U(x, y, z)
```

### Unsafe Rules
In Datalog, some rules can return infinitely many results, making them unsafe. A rule is considered safe if every variable appears in at least one positive predicate. Here are two examples of unsafe rules:

```
V(x, y, z) :- Actor (x, y, 1998), z > 200
W(x, y, z) :- Actor (x, y, z), not Plays (t, x)
```

### Wrapping Up

In this blog post, we introduced Datalog, a powerful query language used in various domains. We focused on nonrecursive Datalog and provided examples to help you understand how rules and queries are used to extract information from facts. By understanding Datalog's basics and how to work with rules, you'll be better equipped to harness its power in your data analysis and manipulation tasks.
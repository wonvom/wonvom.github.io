---
title: Relational Algebra
author: wonvom
date: 2022-04-14 20:20:00 -0800
categories: [Database, DBMS]
tags: [database, sql, relational, model, algebra, calculus, datalog]
math: true
pin: false
---

# Relational Algebra

## Introduction to Relational Algebra

In this blog, we will explore relational algebra (RA), an algebraic representation of queries for relational databases. RA defines a set of basic operations on relations, and each operation returns a relation. These operations can be composed to create complex queries.

### Key Takeaways:

* elational algebra provides an algebraic view on representing queries.
* Basic operations in relational algebra include selection, projection, cross-product, set-difference, and union.
* Additional operations like intersection and join can be useful.
* Relational algebra, safe nonrecursive Datalog, and domain-independent RC express the same set of queries.

## RA Operations

### Basic Operations

1. **Selection (σ)** - Selects a subset of rows from a relation. The schema of the result is identical to the schema of the input.

|aid|aname|b-year|
|---|-------|----|
|1|Robert DeNiro|1954|
|2|Al Pacino|1958|
|3|Jon Bing|1992|

```
σ_{b-year>1990} Actor
```


|aid | aname| b-year|
|---|----|----|
|3 | Jon Bing | 1992|

2. **Projection (π)** - Deletes attributes that are not in the projection list. The schema of the result contains exactly the fields in the projection list, with the same names that they had in the input relation.

|aid | aname | b-year|
|---|----|----|
|1 | Robert DeNiro | 1954|
|2 | Al Pacino | 1958|

|aname|
|-|
| Robert DeNiro|
|Al Pacino|
|Jon Bing|


3. **Cross-Product (X)** - Each tuple of R is paired with every tuple of S. The result schema has one attribute per each attribute of R and S.

|aid | aname | b-year|
|---|----|----|
|1 | Robert DeNiro | 1954|
|2 | Al Pacino | 1958|

|mid | aid|
|--|--|
|20 | 1|
|30 | 2|

|aid | aname | b-year | mid | aid|
|-|-|-|-|
|1    | Robert DeNiro | 1954 | 20 | 1|
|2   | Robert DeNiro | 1954 | 30 | 2|
|3 | Al Pacino | 1958 | 20 | 1|
|4 | Al Pacino | 1958 | 30 | 2|

4. **Join (⨝)** - Result schema is the same as that of cross-product. More meaningful than cross-product. If condition is equality, join is called equi-join. Natural join is an equi-join on all common fields.

```
R ⨝_{c} S = σ_{c} (R X S)
```

|aid | aname | b-year|
|-|-|-|
|1| Robert DeNiro | 1954|
|2 | Al Pacino | 1958|

|mid | aid|
|-|-|
|20 | 1|
|30 | 2|

```
Actor ⨝_{Actor.aid=Plays.aid} Plays
```

|aid | aname | b-year | mid | aid|
|-|-|-|-|-|
|1 | Robert DeNiro | 1954 | 20 | 1 |
|2 | Al Pacino | 1958 | 30 | 2|


### Union, Intersection, Set-Difference

5. **Union (U)** - Returns tuples in relation 1 and in relation 2.

6. **Intersection** - Not essential but useful.

7. **Set-Difference (-)** - Returns tuples in relation 1, but not in relation 2.

These operations act like their counterparts in set theory. They take two input relations that are union-compatible, meaning they have the same number of attributes and corresponding attributes with the same domain (type). The output has the same schema as the input.

### Expressiveness and Usage of RA, RC, and Datalog

1. **Expressiveness** - The Equivalency Theorem states that relational algebra (RA), safe nonrecursive Datalog, and domain-independent RC express the same set of queries. We don't cover the proof in this course, but you can read Chapter 3 of the Alice Book if interested.
2. **Usage** - Relational database systems usually translate SQL to RA due to its simplicity. RC is used to express knowledge and constraints over data, such as integrity and quality constraints (e.g., each person has only one SSN). Datalog is used in systems that need recursion (e.g., query languages in some graph data systems extend Datalog) and in machine learning over relational data. It is easy to use recursion in Datalog.

### Wrap-up

In this blog post, we introduced relational algebra, an algebraic view on representing queries for relational databases. We discussed the basic operations in relational algebra, including selection, projection, cross-product, set-difference, and union, as well as additional operations like intersection and join. We also touched on the expressiveness and usage of relational algebra, safe nonrecursive Datalog, and domain-independent RC.

By understanding the various operations in relational algebra and how they can be combined, you can create powerful queries for relational databases and gain a deeper understanding of how SQL and other query languages work under the hood. This knowledge can help you work more effectively with relational databases and better comprehend the underlying processes at work.
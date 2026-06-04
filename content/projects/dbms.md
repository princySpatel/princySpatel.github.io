---
title: "DBMS Normalization Engine"
description: "An interactive, algorithmic engine built with Python and Streamlit that automatically decomposes any database schema into 1NF, 2NF, 3NF, and BCNF."
timestamp: 2026-03-20
tags: ["DBMS", "Python", "Streamlit", "Algorithms"]
githubUrl: "https://github.com/princySpatel/DB-normalization-system"
---

## Overview
Database normalization is often taught as an abstract, manual process. I built this normalization engine to mathematically automate and visualize that process. While the app boots up with a default "Airport Database" theme to provide immediate context, the underlying engine is entirely dynamic—it can parse and normalize **any** custom relational schema and set of functional dependencies you feed it.

## The Algorithmic Engine
Instead of just hardcoding rules, the engine performs genuine relational algebra calculations under the hood:
* **Attribute Closures:** Dynamically computes the closure of any attribute set to determine reachability.
* **Candidate Key Discovery:** Uses set combinations to mathematically prove and extract all valid primary and candidate keys from raw dependencies.
* **Minimal Cover Synthesis:** Strips out extraneous attributes and redundant dependencies to find the cleanest version of the functional dependencies.

## Step-by-Step Decomposition
The UI breaks down the normalization process exactly how a database engineer would approach it:
1. **1NF Validation:** Checks for atomic attributes and repeating groups.
2. **2NF Processing:** Detects partial dependencies and splits tables to eliminate them.
3. **3NF Synthesis:** Removes transitive dependencies so non-key attributes depend only on candidate keys.
4. **Recursive BCNF:** Applies a recursive decomposition algorithm to ensure every determinant is a superkey, outputting the final, perfectly normalized schema.

## The Interface
Built with **Streamlit**, the application features a custom-styled, clean UI. It abstracts the heavy mathematical lifting behind the scenes and presents the user with readable schema grids, clearly defining Primary Keys (PK) and inferred Foreign Keys (FK) for the final database design.

*some of the image*
![image simulation](https://princyspatel.github.io/images/dbms1.png)
![image simulation](https://princyspatel.github.io/images/dbms2.png)
![image simulation](https://princyspatel.github.io/images/dbms3.png)

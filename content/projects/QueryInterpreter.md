---
ShowToc: false  
title: SQL-like Natural Language Query Interpreter  
date: 2024-12-04  
draft: false  
summary: Built a Prolog-based interpreter that parses and executes SQL-style natural language queries with logical reasoning.  
math: true  
---

## Description

This project focused on building an interpreter in Prolog that reads natural language commands similar to SQL, parses them using Definite Clause Grammar (DCG), and executes them through logical and constraint-based reasoning. The system supports commands like filtering, joining, and matching values across tables. It processes inputs from a text file, extracts structured queries, and evaluates them against a Prolog-based knowledge base. The results are formatted and displayed in tables.

## Tech Stack  
- SWI-Prolog  
- Definite Clause Grammar (DCG)

## Contributions  
- Implemented a parser using **DCG** to convert natural language commands into structured Prolog queries.  
- Built logic to evaluate commands by filtering data based on comparison operators and logical conditions (e.g., AND, OR).  
- Handled complex operations like table joins and nested queries by linking related data through shared attributes.  
- Used helper utilities to format and print the result tables based on filtered queries.  
- Ensured proper handling of edge cases like invalid date comparisons and empty result sets.

---
ShowToc: false  
title: Lambda Calculus Interpreter  
date: 2024-09-26  
draft: false  
summary: Developed a functional interpreter for lambda calculus expressions with support for beta and eta reductions in applicative order.  
math: true  
---

## Description

This project is a Haskell-based interpreter for lambda calculus expressions. It reads expressions from an input file, performs reductions using beta and eta rules following applicative order (call-by-value), and writes the final results to an output file. The interpreter handles invalid input gracefully and follows proper rules for variable renaming to avoid conflicts during substitution. 

## Tech Stack  
- Haskell

## Contributions  
- Implemented a reducer function that applies beta and eta reductions to lambda expressions represented by a custom `Lexp` datatype.
- Utilized provided parsing utilities to handle input/output operations, focusing on the core reduction logic.
- Ensured correct handling of variable scoping and alpha-renaming to prevent variable capture during substitutions.
- Validated the interpreter against a suite of test cases, confirming accurate reduction results and robust error handling.

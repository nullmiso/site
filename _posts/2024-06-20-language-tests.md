---
layout: post
title: "Building a compiler"
category: example2
---

This spring I took a course titled "Translation of Programming Languages" at UC Santa Barbara. This was the standard compiler class for undergraduates at our school. I believe I spent the most time on this class out of every class I've taken at UCSB, and in lieu of hosting a public repository (which another student confirmed would not be possible after the course), I would like to document my experience with building a compiler from the top down in C++ with my team of roommates (henceforth called A and B) for a toy language called "c flat."

### Lexer
Roommate A drew up a few NFA graphs to emulate the behavior of the lexer, while I built a map from syntax to operator names and wired the nodes together on the .cpp file and Roommate B wrote a function to find and print whether the lexer had reached an accepting state. After a few test runs with our apartment's 65-inch TV, we submitted our code to the autograder for the first time. I noted that most of the issues that came up after our initial submission were because the algorithm did not account for the End Of File situation, which helped us determine how to rework the logic in the lexer file. We finished this assignment, the first part of the compiler, in a single night.

### LL1 Parser + Validator
Usually this section would have been broken up across two assignments (as was the case the previous time this course was offered). However, we had only one and a half weeks to complete both. We had been making progress on the assignment since it was announced, but about three days before the assignment was due, Roommate A wisely suggested we set aside all of our other schoolwork to focus exclusively on it.

This parser was to be LL(1); that is, it would parse a language without left-recursion and would have a deterministic (no epsilon transitions) lookahead of 1 character to determine which state to enter. After painstakingly designing functions to print every token generated from the previous assignment, we 
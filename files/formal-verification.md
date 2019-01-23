# Formal Verification

# Introduction {#intro}

Formal verification is the process of using formal definitions to verify that a program conforms to certain specifications. In other words, it uses mathematics to answer the question, "Have we made what we were trying to make?"

In contrast, programmers currently write unit tests to ensure that a program conforms to certain specifications. They test the program with as many inputs as possible, verifying each time that the output fits what is mentioned in the specification. For example, to test that a program correctly sorts a list of numbers into ascending value, it will be tested with an input of `[2, 3, 1]`. The test's output should yield `[1, 2, 3]`, or else the program is invalid.

However, the unit test approach may not be able to cover all possible inputs (or edge cases), and these may lead a program to failure. The solution to this is formal verification. Formal verification involves writing mathematical definitions of the program. To drawing on the same example given above, one may write a definition, "For every item j in a list, ensure that the element j ≤ j+1". This is a huge step-up from unit tests, as the correctness of the program is shown to be mathematically universal.

# Michelson with GADT {#gadt}

GADT stands for Generalized Algebraic Data Types. GADTs allow OCaml developers to describe rich relations between data constructors and the types they inhabit. Currently, the Michelson language uses GADT (Generalized Algebraic Data Types) for formal verification of types.

# Michelson with Coq {#coq}

As of January 2019, the formal verification implementation of Michelson with Coq is not yet complete. However, using the Coq interactive theorem prover, the following parts of the language
are formalized:

- the type system
- the syntax
- the semantics

Coq implements a program specification and higher-level mathematical language called *Gallina*  This language is in turn based on an expressive formal language called the *Calculus of Inductive Constructions*, which combines both a higher-order logic and a richly-typed functional programming language. Through a *vernacular* language of commands, Coq allows one to:

- define functions or predicates that can be evaluated efficiently;
- state mathematical theorems and software specifications;
- interactively develop formal proofs of these theorems;
- machine-check these proofs by a relatively small certification "kernel";
- extract certified programs to languages like Objective Caml, Haskell or Scheme.

As a proof development system, Coq provides interactive proof methods, decision and semi-decision algorithms, and a *tactic* language that lets the user define its own proof methods. Connections with external computer algebra systems and theorem provers are also available.

As a platform for the formalization of mathematics and for the development of programs, Coq provides support for high-level notation, implicit content and other useful macros.

# Why is this important for financial contracts?

Smart contracts are programs that hold a given amount of money. As such, it is crucial that they be error-free and correct. Unit testing is not sufficient to cover all edge cases and all errors that may occur in the wild. 

Complex financial contracts involve steps and processes that involve the trust of the involved parties, as well as of other parties that have stake in the trustworthiness of the system on which the contract is built. An incorrectly constructed contract can breach trust in the system. In worst cases, unintended program effects can lead to a loss of money, as was seen in multiple instances with Ethereum.

With formal verification, computer scientists and developers can prove indisputably that certain programs are error-free. They can do this to the same degree of certainty that is required of a mathematician who wishes to prove a theorem. These advances are being used to secure everything from unmanned drones to the internet.
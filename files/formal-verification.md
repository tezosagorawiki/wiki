# Formal Verification

# Introduction {#intro}

Formal verification is the process of verifying that a program conforms to a specification by using formal definitions. It tries to answer the question "have we made what we were trying to make?" mathematically.

To contrast, programmers currently write unit tests to ensure that a program conforms to the specifications. They will test the program with as many inputs as possible, and verify that the output fits what is mentioned in the specification. For example, to test that a program correctly sorts a list, it will be tested with an input of `[2, 3, 1]`. The test's output should yield `[1, 2, 3]`, or the program is invalid.

However, the unit test approach may not be able to cover all possible inputs (or edge cases) that may lead a program to failure. The solution to this is formal verification. Formal verification involves writing mathematical definitions of the program. From the example above of sorting a list, one may write a definition, "For every item j in a list, ensure that the element j ≤ j+1". This is a huge step-up from existing methods of verifying programs i.e. unit tests, by mathematically proving their correctness.

# Michelson with GADT {#gadt}

GADT stands for Generalized Algebraic Data Types. GADTs allow OCaml developers to describe richer relations between the data constructors and the type they inhabit. Currently, the Michelson language uses GADT (Generalized Algebraic Data Types) for formal verification of types.

# Michelson with Coq {#coq}

Currently, the formal verification implementation of Michelson with Coq is not complete yet. Using the Coq interactive theorem prover, the following parts of the language
are formalized:

- the type system
- the syntax
- the semantics

Coq implements a program specification and mathematical higher-level language called *Gallina* that is based on an expressive formal language called the *Calculus of Inductive Constructions* that itself combines both a higher-order logic and a richly-typed functional programming language. Through a *vernacular* language of commands, Coq allows:

- to define functions or predicates, that can be evaluated efficiently;
- to state mathematical theorems and software specifications;
- to interactively develop formal proofs of these theorems;
- to machine-check these proofs by a relatively small certification "kernel";
- to extract certified programs to languages like Objective Caml, Haskell or Scheme.

As a proof development system, Coq provides interactive proof methods, decision and semi-decision algorithms, and a *tactic* language for letting the user define its own proof methods. Connection with external computer algebra system or theorem provers is available.

As a platform for the formalization of mathematics or the development of programs, Coq provides support for high-level notations, implicit contents and various other useful kinds of macros.

Following our previous example of a sorted list, using Coq, a definition could be written as:

    Require Import Coq.Lists.List.
    Import ListNotations.
    
    Inductive SortedList : list nat -> Prop :=
    | sort0 : SortedList []
    | sort1 : forall a, SortedList [a]
    | sort2 : forall z1 z2 l, z1 <= z2 -> SortedList (z2 :: l) -> SortedList (z1 :: z2 :: l).

Finally, we create a proof to show that the definition is working.

    Theorem SortedList_sep:
      forall l1 l2,
      SortedList (l1 ++ l2) -> SortedList l1 /\ SortedList l2.
    Proof.
      induction l1; firstorder; try destruct l1; inversion H;
        rewrite <- ?app_comm_cons in *; try constructor; firstorder.
    Qed.

# Why is this important for financial contracts?

Smart contracts are programs that hold arbitrary amount of money, which makes it crucial for them to be designed error-free and correctly. By creating these rich financial contracts, testing is just not sufficient to cover all the edge cases and errors that can happen in the wild. Next, complex financial contracts involve steps and processes that involve the trust of two parties. An incorrectly-constructed contract would breach the trust of the system and the involved parties. On top of that, unintended program effects can lead to loss of money, as seen in multiple instances with Ethereum.

With formal verification, computer scientists and developers can prove certain programs to be error-free with the same certainty that mathematicians prove theorems. These advances are being used to secure everything from unmanned drones to the internet.
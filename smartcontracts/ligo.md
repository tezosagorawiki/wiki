# LIGO

**LIGO**

[LIGO](https://ligolang.org) is a programming language for Tezos with support for different syntaxes:

* CameLIGO, an OCaml inspired syntax
* ReasonLIGO, a functional JavaScript-like syntax inspired by ReasonML
* PascaLIGO, a Pascal inspired syntax

These syntaxes are transformed into an intermediate representation, which is type checked and efficiently translated into Michelson.

**LIGO Resources**

* [LIGO homepage](https://ligolang.org/)
* [LIGO documentation](https://ligolang.org/docs/intro/introduction)
* [LIGO IDE](https://ide.ligolang.org/)

### **OCaml, the language of the Tezos protocol**

The Tezos protocol is written in OCaml, a general purpose industrial-strength programming language with an emphasis on expressiveness and safety. It is the technology of choice in companies where speed is crucial and a single mistake can cost millions. It has a large standard library, which makes it useful for many of the same applications as Python or Perl, and it has robust modular and object-oriented programming constructs that make it applicable for large-scale software engineering. Many top companies use OCaml, including Facebook, Bloomberg, Docker, and Jane Street.

#### OCaml Resources

* [What is OCaml?](https://ocaml.org/learn/description.html)
* [Jane Street OCaml Tutorial](https://github.com/janestreet/learn-ocaml-workshop)
* [Real World OCaml](https://realworldocaml.org/)

### **What is functional programming? How is it different from other paradigms?**

[Functional programming](https://en.wikipedia.org/wiki/Functional_programming) is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

It is a declarative programming paradigm, which means programming is done with expressions or declarations instead of statements. In functional code, the output value of a function depends only on the arguments that are passed to the function, so that calling a function f twice with the same value for an argument x produces the same result f\(x\) each time. This is in contrast to procedures that depend on a local or global state, which may produce different results at different times when called with the same arguments but a different program state. Eliminating side effects, i.e. changes in state that do not depend on the function inputs, can make it much easier to understand and predict the behavior of a program, which is one of the key motivations for the development of functional programming.

Here is a diagram that shows the high-level differences between the EVM \(Ethereum Virtual Machine\), WASM \(Web Assembly\) and Michelson:

![](../.gitbook/assets/languages.png)

## Michelson Language <a id="michelson"></a>

## Introduction

Michelson is the low-level, stack-based programming language used to write smart contracts on the Tezos blockchain. Michelson was designed to facilitate formal verification, allowing users to prove the properties of their contracts.

It uses a stack rewriting paradigm, whereby each function rewrites an input stack into an output stack. \(The meaning of this will be fully explained below.\) This runs in a purely functional way and does not modify the inputs at all. Thus, all data structures are **immutable**.

## What is a Stack?

A stack is an abstract data type that serves as a collection of elements, with two principal operations: push \(adds an element to the collection\) and pop \(removes the most recently added element that has not yet been removed\). The order in which elements come off a stack gives rise to its alternative name, LIFO \(last in, first out\). Additionally, a peek operation may give access to the top without modifying the stack.

![](https://upload.wikimedia.org/wikipedia/commons/9/9f/Stack_data_structure.gif)

Source: Wikipedia.

## Rewriting Stacks

To see what mean it means to rewrite stacks, we will run through a transaction in Michelson. First, before a transaction runs, the blockchain state at a certain hash is deserialized and put onto the stack as the variable `storage`. We have a `from` function that receives the transaction data `amount` , the amount of attached ꜩ, and the `parameter` , the function's parameters.

```text
from [ (Pair (Pair amount parameter) storage) ]
```

After running the function, without any updates to the stack, the program will call a `to` function that has the parameters `result`, which is the result of the function, and the output `storage` that is serialized and stored on the blockchain.

```text
to [ (Pair result storage) ]
```

In the example, Michelson only manipulates the stack functionally and a new stack is passed from function to function.

## Language Resources <a id="resources"></a>

## Michelson:

* [Michelson Language Intro](https://tezos.gitlab.io/007/michelson.html)
* [Michelson talk](https://www.youtube.com/watch?v=4oG4Ead74xA)
* [Michelson Tutorial Part 1 by CamlCase](https://gitlab.com/camlcase-dev/michelson-tutorial/tree/master/01)
* [Michelson Tutorial Part 2 by CamlCase](https://gitlab.com/camlcase-dev/michelson-tutorial/tree/master/02)
* [Michelson Tutorial Part 3 by CamlCase](https://gitlab.com/camlcase-dev/michelson-tutorial/tree/master/03)
* [Michelson Tutorial Part 4 by CamlCase](https://gitlab.com/camlcase-dev/michelson-tutorial/tree/master/04)


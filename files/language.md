# Language FAQ {#faq}

## **What is Michelson?**

Michelson is the domain-specific language used to write smart contracts on the Tezos blockchain. Michelson is a stack-based language, it doesn't have any variables. Stack-oriented languages operate on one or more stacks, each of which may serve a different purpose. See here for [Michelson documentation](http://tezos.gitlab.io/mainnet/whitedoc/michelson.html) and here for [Michelson tutorials](https://gitlab.com/camlcase-dev/michelson-tutorial/tree/master).

## **What is Liquidity?**

Liquidity is a high-level language to program Smart Contracts for Tezos. It is a fully typed functional language, it uses the syntax of OCaml, and strictly complies with Michelson security restrictions. Liquidity already covers 100% of the Michelson features, and contracts generated with Liquidity can be submitted on the main network. A formal-method framework for Liquidity is under development, to prove the correctness of smart-contracts written in Liquidity.

## **What is the difference between Liquidity and Michelson?**

Liquidity is compiled back to Michelson. It is easier to approach as it has local variables and high-level types instead of stack manipulations.

## **What is OCAML?**

OCaml is a general purpose industrial-strength programming language with an emphasis on expressiveness and safety. It is the technology of choice in companies where a single mistake can cost millions and speed matters. It has a large standard library, making it useful for many of the same applications as Python or Perl, and has robust modular and object-oriented programming constructs that make it applicable for large-scale software engineering. Many top companies use OCaml including Facebook, Bloomberg, Docker, and Jane Street.

## **What is functional programming? How is it different from other paradigms?**

Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

It is a declarative programming paradigm, which means programming is done with expressions or declarations instead of statements. In functional code, the output value of a function depends only on the arguments that are passed to the function, so calling a function f twice with the same value for an argument x produces the same result f(x) each time; this is in contrast to procedures depending on a local or global state, which may produce different results at different times when called with the same arguments but a different program state. Eliminating side effects, i.e. changes in state that do not depend on the function inputs, can make it much easier to understand and predict the behavior of a program, which is one of the key motivations for the development of functional programming.

Here is a diagram that shows the differences between EVM (Ethereum Virtual Machine), WASM (Web Assembly) and Michelson:

![](../img/languages.png)

# Michelson Language {#michelson}

# Introduction

Michelson is the low level, stack-based programming language used to write smart contracts on the Tezos blockchain. Michelson was designed to facilitate formal verification, allowing users to prove the properties of their contracts.

It uses a stack rewriting paradigm, whereby each function will rewrite an input stack into an output stack (will explain what this means in a while). This runs in a purely functional way and does not modify the inputs at all. Thus, all data structures are **immutable**.

# What is a Stack?

A stack is an abstract data type that serves as a collection of elements, with two principal operations: push (adds an element to the collection) and pop (removes the most recently added element that was not yet removed). The order in which elements come off a stack gives rise to its alternative name, LIFO (last in, first out). Additionally, a peek operation may give access to the top without modifying the stack.

![](https://upload.wikimedia.org/wikipedia/commons/9/9f/Stack_data_structure.gif)

Source: Wikipedia.

# Rewriting Stacks

To see what rewriting stacks mean, we have to run through a transaction in Michelson. First, before a transaction runs, the blockchain state at a certain hash is deserialized and put onto the stack as the variable `storage`. We have a `from` function that receives the transaction data `amount` , the amount of attached ꜩ, and the `parameter` , the function's parameters.

    from [ (Pair (Pair amount parameter) storage) ]

After running the function, without any updates to the stack, the program will call a `to` function that has the parameters `result`, which is the result of the function, and the output `storage` that is serialized and stored on the blockchain.

    to [ (Pair result storage) ]

In the example, Michelson only manipulates the stack functionally and a new stack is passed from function to function. 

# Why Michelson?

At first sight, Michelson is a strange language. It doesn’t include many features like polymorphism, closures, or named functions. Compared to a language like Haskell or OCaml, it seems underpowered; its stack is not always easy to deal with; there is no standard library. However, these restrictions are largely motivated by the language’s design goals.

There are two large motivations for Michelson:

1. To provide readable bytecode
2. To be introspectable

Tezos takes a slightly different view from Ethereum regarding the role of smart contracts. We think of our platform more as a way to implement pieces of business logic than as a generic “world computer”. Looking at Ethereum, most contracts implement things like multisig wallets, vesting and distribution rules, etc. Michelson is targeted to these applications, not the case of arbitrary programs.

Michelson is designed as a readable compilation target, though it can be hand written. The goal is that even the output of a compiler can be understood. We intend the language to be simple enough that developers can build their own analysis tools and compilers should they prefer to do so. This is a departure from the EVM’s bytecode which more closely resembles assembly. With a lower-level bytecode, you usually need confidence in both your program and the compiler toolchain. With Michelson you can more easily check over and verify properties of the program that is actually executed.

Using a higher-level bytecode also simplifies the process of proving properties about the compiled output. Programs written in Michelson can be reasonably analyzed by SMT solvers and formalized in Coq without the need for more complicated techniques like separation logic. Similarly, the restrictions imposed by the forced indentation and capitalization ensure that the source cannot be obfuscated with indentation and alignment tricks.

Our current implementation of Michelson is based around an OCaml GADT, which we have used to verify the type-soundness of the language. Additionally, the implementation of a stack based language maps directly to the semantics. The same is not true for any efficient implementation of the lambda-calculus. There have also been two formally verified implementations of Michelson, one in Coq and one in F*. One day, we hope to replace our current implementation with a verified one.

Finally, one of the main advantages of Tezos is that the system is amendable. We want to start with a small core language in which we are confident and add features as good use cases are created for them. We don't want to throw everything into the language in at the onset and then break backwards compatibility.

So, why Michelson? To provide a straightforward platform for business logic, to provide a readable bytecode, and to be introspectable. When I was working with Olin Shivers, he was very fond of saying that one should always use a "tool small enough for the job". Michelson has been carefully designed to be that tool.

# Liquidity {#liquidity}

Liquidity is a high-level language to program Smart Contracts for Tezos. It is a fully typed functional language, it uses the syntax of OCaml, and strictly complies with Michelson security restrictions.

A formal-method framework for Liquidity is under development, to prove the correctness of smart-contracts written in Liquidity.

The Liquidity language provides the following features:

- Full coverage of the Michelson language: Anything that can be written in Michelson can be written in Liquidity,
- Local variables instead of stack manipulations: values can be stored in local variables.
- High-level types: types like sum-types and record-types can be defined and used in Liquidity programs.

Liquidity already covers 100% of the Michelson features, and contracts generated with Liquidity can be submitted on the current mainnet and zeronet.


# Language Resources {#resources}

# Michelson:

- [Michelson language homepage](https://www.michelson-lang.com/)
- [Contract a day](https://www.michelson-lang.com/contract-a-day.html)
- [Michelson talk](https://www.youtube.com/watch?v=4oG4Ead74xA)
- [Michelson Tutorial Part 1 by CamlCase](https://gitlab.com/camlcase-dev/michelson-tutorial/tree/master/01)
- [Michelson Tutorial Part 2 by CamlCase](https://gitlab.com/camlcase-dev/michelson-tutorial/tree/master/02)
- [Michelson Tutorial Part 3 by CamlCase](https://gitlab.com/camlcase-dev/michelson-tutorial/tree/master/03)
- [Michelson Tutorial Part 4 by CamlCase](https://gitlab.com/camlcase-dev/michelson-tutorial/tree/master/04)

# Liquidity:

- [Liquidity homepage](http://www.liquidity-lang.org/)
- [Liquidity documentation](http://www.liquidity-lang.org/doc/)

# OCaml:

- [What is OCaml?](https://ocaml.org/learn/description.html)
- [Jane Street OCaml Tutorial](https://github.com/janestreet/learn-ocaml-workshop)
- [Real World OCaml](https://realworldocaml.org/)
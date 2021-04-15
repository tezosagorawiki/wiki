# Morley Framework

The Morley framework is a collection of projects that build upon and complement each other. Most notably:

1. [Morley](./#morley)
2. [Lorentz](./#lorentz)
3. [Indigo](./#indigo)
4. [Cleveland](./#cleveland)

## Morley

[Morley](https://gitlab.com/morley-framework/morley/-/blob/master/code/morley/README.md) is a Haskell-based framework for meta-programming Michelson smart contracts.

It consists of:

* The Morley language: a superset of the Michelson language, with a simpler syntax and some simple features.

  Contracts are written in `.mtz` files.

* A library with the core Tezos and Michelson data types, as well as tools for typechecking,

  interpreting, parsing and printing Michelson and Morley contracts.

* An executable with commands for compiling and working with Morley and Michelson contracts,

  along with a REPL for interactively running instructions.

It's the founding library of [Lorentz](./#lorentz), [Indigo](./#indigo), [Cleveland](./#cleveland) as well as related tools and utilities.

### Morley Resources

* [Morley project page](https://gitlab.com/morley-framework/morley/-/blob/master/code/morley/README.md/)
* [Morley API docs](https://hackage.haskell.org/package/morley)

## Lorentz

[Lorentz](https://gitlab.com/morley-framework/morley/-/blob/master/code/lorentz/README.md) is a stack-based embedded Domain Specific Language \(eDSL\) in Haskell that compiles to Michelson.

Some of its noteworthy features are:

* An expressive type system, including product/sum types and parametric polymorphism.
* Powerful type inference.
* Type-safe mechanisms for writing smart contracts with an upgradeable storage and contract migrations.
* The ability to easily share and reuse components of a contract as Haskell packages.
* The ability to automatically generate documentation for your smart contract in Markdown format,

  and to keep it up-to-date with the contract's code as it evolves.

### Lorentz Resources

* [Lorentz introductory blog post](https://serokell.io/blog/lorentz-implementing-smart-contract-edsl-in-haskell)
* [Lorentz project page](https://gitlab.com/morley-framework/morley/-/blob/master/code/lorentz/README.md/)
* [Lorentz API docs](https://hackage.haskell.org/package/lorentz)

## Indigo

Indigo eDSL is a high-level language for developing Michelson contracts.

Like [Lorentz](./#lorentz), it makes full use of Haskell's type system to ensure safety, expressiveness and reusability.

It is meant first and foremost to free you from the burden of manual stack management required by languages like Michelson and Lorentz, and supports common features of imperative languages, such as mutable variables and _while_ loops.

### Indigo Resources

* [Indigo project page](https://gitlab.com/morley-framework/indigo)
* [Indigo documentation and tutorial](https://indigo-lang.gitlab.io/)
* [Indigo API docs](https://hackage.haskell.org/package/indigo)

## Cleveland

[Cleveland](https://gitlab.com/morley-framework/morley/-/tree/master/code/cleveland) is a Haskell library for testing Michelson contracts.

Cleveland makes it trivial to load a contract from disk, originate it, transfer XTZ, check its storage/balance, call its entrypoints, check whether it failed with a given error, etc.

Cleveland tests can be run:

* on an actual blockchain;
* or via Morley's in-memory interpreter for a faster feedback loop.

It supports example-based testing \(via the [tasty](https://hackage.haskell.org/package/tasty) testing framework\) and property-based testing \(via [hedgehog](https://hackage.haskell.org/package/hedgehog)\).

### Cleveland Resources

* [Cleveland project page](https://gitlab.com/morley-framework/morley/-/tree/master/code/cleveland)
* [Cleveland documentation and tutorial](https://gitlab.com/morley-framework/morley/-/blob/master/code/cleveland/testingEDSL.md/)


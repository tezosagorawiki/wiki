### **High-level Languages of Tezos**

Tezos has several popular high-level languages which offer more approachable syntaxes and familiar developer experience (e.g. local variables) compared to writing Michelson directly. SmartPy and LIGO are the most popular and widely-supported languages for writing Tezos smart contracts.

#### SmartPy {#smartpy}

[SmartPy](https://smartpy.io) is a complete system to develop smart-contracts for the Tezos blockchain. It is an embedded Domain Specific Language (DSL) in python that gives the users the ability to write and implement test scenarios to test their smart-contracts. It includes an online IDE, a beautiful origination page to deploy smart-contracts in various Tezos networks, an explorer that allows users to interact with their contracts, and a command-line interface.

Python is used to generate programs in an imperative, type inferred, and intermediate language called SmartML. SmartML is the name of the OCaml library that provides an interpreter, a compiler to Michelson, and a scenario “on-chain” interpreter. The platform uses a mix of OCaml translated to pure javascript through js_of_ocaml, Python, and Typescript to glue everything together. The command-line interface is also built using js_of_ocaml and runs on Node.js.

##### SmartPy Resources
- [SmartPy homepage](https://smartpy.io)
- [SmartPy documentation](https://smartpy.io/reference.html)
- [SmartPy IDE](https://smartpy.io/ide)
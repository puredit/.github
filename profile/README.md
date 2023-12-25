# Project Overview
This org contains the accompanying source code and examples of the following paper:

[Niklas Korz](https://2023.splashcon.org/profile/niklaskorz), [Artur Andrzejak](https://aip.ifi.uni-heidelberg.de/team/aa)

It is based on the repository [https://github.com/niklaskorz/puredit](https://github.com/niklaskorz/puredit).

**Virtual Domain Specific Languages via Embedded Projectional Editing**

Published at 22nd International Conference on Generative Programming: Concepts & Experiences ([GPCE 2023](https://2023.splashcon.org/program/program-splash-2023/)), in conjunction with ACM SPLASH 2023, 22-27 October 2023, Cascais, Portugal.

## Summary
We propose here an approach that represents a subset of a General-Purpose Programming Language (GPL) as GUI widgets in a hybrid editor. It relies on matching parametrized patterns against the GPL program, and displaying the matched parts as dynamically rendered widgets. Such widgets can be interpreted as components of an external DSL. Since the source code is serialized as GPL text without annotations, there is no DSL outside the editor - hence the term ‘virtual’ DSL.

The underlying GPL and the virtual DSL can be mixed in a compositional way, with zero cost of their integration. The project infrastructure does not need to be adapted. Furthermore, our approach works with mainstream GPLs like Python or JavaScript.

To lower the development effort of such virtual DSLs, we also propose an approach to generate patterns and the corresponding text-only GUI widgets from pairs of examples.

A live demo of the system can be accessed [here](https://puredit.korz.dev/).

## Why the name Puredit?
> Purism, referring to the arts, was a movement (...) where objects are represented as elementary forms devoid of detail. ([Wikipedia](https://en.wikipedia.org/wiki/Purism))

The **Pur**ist **edit**or is a projectional editor that uses textual code as its source of truth. Unlike other projectional editors, Puredit is based on the assumption that parsers are fast enough to continuously react to changes to a document and update the projections accordingly. Projections are derived from patterns on the abstract syntax tree. To make the definition of patterns easy, they are parsed from actual code snippets in the target language.

## Repository structure
- `samples`: executable applications and demos
- `generator`: an application for generating code pattern templates and projection components from samples
- `parser`: a library for defining syntax tree patterns through code templates and finding nodes matching these patterns in a program's syntax tree
- `projections`: an extension for the [CodeMirror 6](https://codemirror.net/) editor for detecting syntax tree patterns in a document and replacing them with interactive projection widgets implemented as Svelte components
- `codemirror-typescript`: a client-side language server for the TypeScript programming language integrated into [CodeMirror 6](https://codemirror.net/), based on [prisma/text-editors](https://github.com/prisma/text-editors)
- `utils`: a library with helper functions used throughout the project.
- `vscode-extension`: an extension for [Microsoft Visual Studio Code](https://code.visualstudio.com/) to integrate projectional editors.

## Dependencies
This project requires [Node](https://nodejs.org/en/) 16 LTS and [npm](https://www.npmjs.com/) 8.
Node 18 may work but has not been tested.

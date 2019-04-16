# Rome Testnet Specification

## Table Of Content

- [Purpose](#purpose)
- [Decisions](#decisions)
- [Work In Progress](#work-in-progress)
- [Glossary](#glossary)
- [Notation](#notation)
- [Rome](#rome)
 - [Overview](#overview)
 - [Roles](#roles)
 - [Substrate Runtime](#substrate-runtime)

## Document Purpose

The life time and purpose of this docuemnt is separated into two distinct phases,

- Enable greater
- xxx
- audience
- use case
- scope
- frist ry, tierative arrive at standard, extract generalised template for joystrema and other Susbtrate teams.

## Specification Style

Given the descrbied purpose of this document, the style of specification admits to the following constraints

- S

Take Substrate for granted, and SRML momdules, dont explicitly described.

### Conventions

<explain how you wille xplain different parts, what each part of the explanation does>

#### Substrate

-  explain how to intereprt speciciation, so we understand `map`, build et.
- xxxx

#### Protocols




### Glossary

- **Substrate:** A blockchain SDK
- **Runtime:** Application specific consensus code written for the Substrate SDK. Includes state and transaction rules specific to the application, but excludes consensus algorithm and p2p networking.
- **Substrate Module:** A substrate rutnime is partitoned into state and corresponding transaction types .. <= bad explanation.
- **SRML:** Substrate standard runtime library (srml), is a set of highly reusable Substrate modules which come with the
- **GRANDPA:** Consensus algorthm used.

### Notation

- Code is written in Rust.
- When describing state variables, the standard storage encoding,decoding offered by Substrate `decl_storage` is used, in particular
 - xx
 - xx
 - xx
- In some cases transaction logic may be written in psuedocode, or just free form, over fully valid Rust.

## Specification

### Overview

something high level?

### Roles

xxxx


#### x
##### xx
###### xxx

### Substrate Runtime

#### Substrate Version

`0.x.x.x.x`

#### Types

These are all public types that are part of the runtime. They are public in the sense that they are parameters in transactions or events, or that they are part of some module state(s). Any other types that may appear in a particular implementation, for example generic types and traits/interfaces related to software engineering abstractions, are not included.
.....

#### Modules

- [Rome](rome-module.md)

#### Migrations

list of what other runtimes one will introduce a migration from....

"HOW TO DESCRIBE A MIGRATION"

### Protocols

xxxx

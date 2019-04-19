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


<explain how you wille xplain different parts, what each part of the explanation does>

### Substrate

-  explain how to intereprt speciciation, so we understand `map`, build et.
- xxxx

what bout built in stuff, like types `origin`, and functions, like `ensure_signed`.

what about block level callback?

- **pre-condition:** first order predicate in the runtime state and the transaction paramters which must hold _exactly_ for transaction to be accepted. e.g. that proper person has isgned?
- **post-condition**: first order predicate in the runtime state and the transaction parameters which must hold _exactly_ when the transaction is accepted. The value of state variable `X` _after_ a transaction is handled, is denoted by `X'`. Hence, as an example, the condition that an integer variable `foo` has been incremented after a transaction is captured by the following predicate: `foo' == foo + 1`. Notice that blockchain state, like event logs ands o on, are not part of this, hence they are not in post-condition. (perhaps change?). It is OK to use separately defined functions to define this predicate, but these cannot have side effects.

Notice that no _iomplementaiton_ is ever provided, only how transaction generate new state constraints. This allows us to avoid any implementation specific types, and also allows all modules to be defiend in terms of what actual types are instantioned in the parametric `T::` trait, rather than introduce lots of trait abstractions.

### Protocols




## Glossary

- **Substrate:** A blockchain SDK
- **Runtime:** Application specific consensus code written for the Substrate SDK. Includes state and transaction rules specific to the application, but excludes consensus algorithm and p2p networking.
- **Substrate Module:** A substrate rutnime is partitoned into state and corresponding transaction types .. <= bad explanation.
- **SRML:** Substrate standard runtime library (srml), is a set of highly reusable Substrate modules which come with the
- **GRANDPA:** Consensus algorthm used.

## Notation

- Code is written in Rust.
- When describing state variables, the standard storage encoding,decoding offered by Substrate `decl_storage` is used, in particular
 - xx
 - xx
 - xx
- In some cases transaction logic may be written in psuedocode, or just free form, over fully valid Rust.

## Specification

### Overview

something high level?

### Substrate Runtime

#### Substrate Version

`1.0.0`

#### [Types](#types)

#### Modules

- [**Proposals**](proposal-module.md)
- [**CouncilElection**](council-election-module.md)
- [**Council**](council-module.md)
- [**Memo**](memo-module.md)
- [**Members**](members-module.md)
- [**Migration**](migration-module.md)
- [**Actors**](actors-module.md)
- [**DataObjectTypeRegistry**](data-object-type-registry-module.md)
- [**DataDirectory**](data-directory-module.md)
- [**DataObjectStorageRegistry**](data-object-storage-registry-module.md)
- [**DownloadSessions**](download-sessions-module.md)

#### Migrations

list of what other runtimes one will introduce a migration from....

"HOW TO DESCRIBE A MIGRATION"

### Protocols

xxxx

#### Roles

- role 1
- role 2


## References

1. xxxx
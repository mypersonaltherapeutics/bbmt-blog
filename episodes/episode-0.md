# The Birds, the Bees, and the Merkle Trees Ep[0]: Blockchains From Scratch

*This is episode 0 of 'The Birds, the Bees, and the Merkle Trees',
a developer-focused educational series on blockchain technology.
The purpose of this series is to give a bottom-up view of how blockchains
work, by experimenting with and building core blockchain technologies.
This series is for educational purposes only and should not be construed
as advice or recommendations concerning best-practices for security,
cryptography, etc... This series is developed openly on github,
at `forrest-marshall/bbmt-blog`.*

---

## Introduction

Blockchain technology has been the subject of a lot of hype lately.
Some of it is justified, and some not so much.  My goal in writing
this series is to give a bottom-up view on what blockchains are,
how they work, and how they may be useful to you.

When I first came across blockchain technology, educational materials seemed
to fall into two distinct camps: those which treated blockchains as if they
worked by magic, and those which required advanced degrees to comprehend.
The situation has gotten better since then, but the learning curve can still
be quite steep.  For the purposes of this series, I will be approaching the
fundamental components of the blockchain technology as *tools*.  We won't be
exploring the mathematics or abstract theory much, but we will be exploring
what these tools can do, how these tools are useful, and how to reason about
these tools as we build on top of them.

I am the kind of person who needs to play with things to really understand them.
Whenever I approach a new system, the first thing I do is attempt to
build a 'toy' version of the system that I can play with.  In keeping with this
methodology, we will be building toy versions of the fundamental structures
that make blockchains useful and interesting, including building our own
pseudo-blockchain(s).  I am going to favor clarity and simplicity over efficiency
and robustness, but you should have a working understanding of blockchain
technology by the end of this series.

I will try not to assume any specific knowledge on the part of the reader, though
comfortability with basic programming concepts (functions, types, etc...) and
command-line usage is necessary for full comprehension.  If you have not done
any programming before you should still be able to follow along, but some
googling may be necessary.


## Why Blockchains?

Before we try to understand *how* blockchains work, it is worth looking at *why* blockchains
are worth understanding at all.  A brief glance at the repository of all human knowledge
yields this helpful definition:

> ...a continuously growing list of records, called *blocks*, which are linked
> and secured using cryptography... --Wikipedia

The properties of a blockchain vary by implementation, but it is reasonable to assume that any given
blockchain system was built to meet the following criteria:

- *permissioned*:  Blockchains typically integrate the concept of *permissioned roles*,
  wherein different actors within the system have different actions which they may or
  may not be allowed to take.  These roles are typically enforced via asymmetric
  cryptography, a concept we will be discussing in the next episode.
- *immutable*:  Blockchains are designed to secure historical state against modification.
  Each block contains a cryptographic fingerprint of the previous block such that the
  history of the blockchain is nearly impossible to fake or modify.
- *distributed*:  Distributed systems exist as a network across multiple individual nodes.
  Well-built distributed systems don't have *single points of failure*, meaning that any
  given node within the system may fail without causing the rest of the system to fail.
  Blockchains take this a step  further with a property known as *Byzantine fault tolerance*,
  which allows them to continue to function normally even if some portion of the nodes are
  malicious (willfully trying to work against the interest of the system).
- *transactional*:  Every new block in a blockchain is the product of a set of inputs to the system,
  each of which specifies some set of state-transitions.  Each input either succeeds or fails
  based upon whether the state-transition it describes is allowable by the rules of the system.


## The State of the Art

Early blockchains were purpose-built to achieve specific tasks, not unlike the early
information-processing machines which preceded the modern computer.  When the computers
that we know and love arrived on the scene, they changed everything.  Modern computers are
*general-purpose machines*, and general-purpose is a very big deal.  The state of the art
is no longer blockchains as applications, but rather blockchains as computers.  This is
all thanks to simulated computer processors, known as
[virtual machines](https://en.wikipedia.org/wiki/Virtual_machine).

With the advent of blockchain-based virtual machines, most notably the
[Ethereum Virtual Machine](https://en.wikipedia.org/wiki/Ethereum#Ethereum_Virtual_Machine),
developers are now able to write decentralized applications (DAPPs) which can inherit
the unique properties of the blockchains on which they run.  

One of my primary goals in writing this series is to help developers understand the
unique strengths, and weaknesses, of blockchain-based applications.


## What You Will Need

We are going to be using the [Rust](https://www.rust-lang.org) programming
language for our experiments and projects.  If you are going to follow
along (recommended), you will need to install Rust on your machine.
If you are not familiar with Rust, don't worry; I won't
be assuming any preexisting knowledge of Rust or its ecosystem.  Rust is a relatively new
language which has a very strong focus on reliability, security, and speed.  I chose
Rust for this series because it strikes a nice balance between the convenience of a
high-level language like JavaScript or Python, and the control of a low-level language
like C or C++.

You can install the latest version of the Rust compiler, as well as its associated
package-manager, `cargo`, like so:

```
curl https://sh.rustup.rs -sSf | sh
```

Follow the on-screen instructions to get your local copy of Rust set up.  If you want
to learn more about the Rust language, the [rust book](https://doc.rust-lang.org/book/second-edition/)
is an excellent open-source book which has been developed in parallel with the language,
and covers all of the core features of the language in a friendly and accessible way.


## Up Next

In the next episode, [hashing things out](./episode-1.md), we will be discussing cryptography
in general, the key cryptographic goals of blockchain technologies, and experimenting
with the properties and applications of cryptographic hashing functions.

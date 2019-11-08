---
title: "Just Enough Software Architecture Chapter 2"
date: 2019-11-07T12:40:13-05:00
draft: true
---

> *This series loosely summarizes George Fairbanks's* Just Enough Software Architecture: A Risk-Driven Approach *as I read through it.*

Chapter 2 focuses on defining architecture, its importance, and its use cases.

# Approaches to Architecture

Fairbanks identifies three approaches to architecture.

1. **Architecture-indifferent design:** You code willy-nilly without thinking
   about architecture. This doesn't mean your project *doesn't have* an
   architecture, because architecture (in Fairbanks's view) is an artifact, a
   description of your product. It just means you weren't intentional about
   choosing it. This isn't necessarily *wrong or bad*, by the way. Remember the
   example of installing a mailbox in Chapter 1?
1. **Architecture-focused design:** You intentionally choose an architecture
  that's compatible with your goals.
1. **Architecture hoisting:** You make your architecture *guarantee* your goals
  as much as possible.
    * Example: Your system needs to process messages within 50 milliseconds. In
      architecture-focused design, maybe you choose client-server architecture,
      since that's compatible with that speed. In architecture hoisting, you
      make it part of the architecture itself by, say, indicating that you'll
      need a variable number of servers to support that processing speed.

# Why Is Architecture Important?

* It's the **skeleton** of your project. Think how animal skeletons influence what
  animals can do.
* It influences your project's **quality attributes**. For example, it affects
  scalability and performance.
* It's unrelated to functionality, but **it can make it hard to achieve certain
  functionality**. Would you put a ship factory in the desert or by the ocean?
  (Unlike me, Fairbanks stresses the first part: that architecture is unrelated
  to functionality. I stress the second part because I'm not sure how the first
  argues for the importance of architecture; it seems to do the opposite.)
* It constrains systems. Constraints can be good. One constraint of a bank
  system is that it shouldn't leak your data.

# When Is Architecture Important?

* The solution space is small
* There's a high risk of failure
* The quality attribute requirements are difficult (it has to be fast *and* secure *and* extensible)
* It's a new domain (you're a master of robotics, but this is your first web app)
* You're building a product that already has a well-defined architecture (a CRUD mobile app)

# Presumptive Architecture

Presumptive architecture is the architecture that it's implicitly assumed
something will be built in. For a web app, that might be three-layer
architecture.

Reference architecture is a subset of this. A reference architecture is a
written spec describing a recommended architecture, often by a vendor. For
example, Microsoft's architectural recommendations for ASP.NET web apps.

# Types of Architects

Fairbanks identifies 
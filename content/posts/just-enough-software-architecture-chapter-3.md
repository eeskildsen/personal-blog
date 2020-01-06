---
title: "Just Enough Software Architecture: Chapter 3"
date: 2020-01-06T14:38:00-05:00
draft: false
---

> *This series loosely summarizes George Fairbanks's* Just Enough Software Architecture: A Risk-Driven Approach *as I read through it.*

Chapter 3 of *Just Enough Software Architecture* details the *how* of the risk-driven model. How should it be applied? What techniques should be used?

## Are You Risk-Driven?

Some teams think they're already risk-driven when they're not. How can you know for sure?

Look at your processes. Do you have rigid rules? They can be well-intentioned, but they might be stopping you from being truly risk-driven.

For example, consider this rule:

> Developers have to write a documentation package for each project.

It may sound reasonable, but for many projects, the risks don't merit it.

## Risks

What *is* a risk? One definition is `probability of failure × perceived impact`.

Risks differ by role. Engineering risks are things like, "Will it scale?" Project management risks are things like, "Will the customer like it?"

Risks can be prioritized by:

* Priority to stakeholders
* How hard they'll be to achieve for the development team

The second point above is a way to *identify* risks as well: Find difficult requirements.

## Techniques

Techniques are ways of reducing risks&mdash;strategies you can apply.

### How Many Techniques Should You Use?

Possibilities include:

1. None
    * Let the chips fall where they may.
1. Yardstick
    * Spend a predetermined amount of time designing, like 33%.
1. Documentation package
    * Thoroughly document your software package. This is often unnecessary unless you're "$BIGCOMPANY," as Fairbanks puts it. If you're a team of 5 co-located developers, it's overkill.
1. Ad hoc
    * Decide how much design to do as you go along.

Fairbanks recommends using a *risk-driven model* to choose your answer.

1. Find your risks
1. Prioritize them
1. Choose *techniques* for dealing with them
1. Apply the techniques
1. Evaluate how effectively the risks were reduced

### Spectrum

Techniques lie on a spectrum. *Analysis* is one end, *solution* the other.

* Analysis: You develop and test your own designs.
* Solution: You use a known-good technique, like *facade* from the Gang of Four.

The risk-driven model focuses on the analysis end of the spectrum, the Wild West.

Look for an "optimal basket" of techniques to use. Why *an optimal basket* and not *everything and the kitchen sink*? Because you have finite time and resources. You can never fully eliminate *all* risks.

### Choosing Techniques

When choosing which techniques to apply, it helps to determine what kind of problem you're solving.

There are problems to *find* and problems to *prove*. Problems to find have straightforward answers, like 2 + 2. Problems to prove are more complex, involving more ambiguity and uncertainty.

There are problems that are best addressed by *analogic models* and problems that are best addressed by *analytical models*. Analogic models have representations of objects, like the blips on radar screens representing planes. Analytical models are more abstract, like mathematical equations.

There are problems that can only be efficiently analyzed using certain types of models, called *viewtypes*, on which more in Chapter 9.

There are problems that have *affinities*, which are techniques that go well with them, like hammers with nails.

## Evolutionary Design vs. Planned Design

Evolutionary design is designing as you go, while planned design is up-front design.

Evolutionary design has been "re-invigorated" by TDD and other agile practices. Planned design is still useful, especially in projects where refactoring is impractical. Imagine using evolutionary design to build a bridge, for example.

*Minimal planned design* is a compromise between evolutionary design and planned design. You do some initial design to make sure the biggest risks are accounted for, then use evolutionary design.

## Software Development Processes

The risk-driven model works with all types of software development processes, from waterfall to agile.

How can you use it with agile, though, since agile is feature-focused? Well, you can treat risks like features. Educate the project owner as to what priority risks should have, and put them in the backlog.

Other techniques include:

* Having a Sprint 0 just for design (not features)
* Handling small risks within sprints, as they come up

## Architecture Refactoring

As you implement a system, you may realize the original design stunk. Failure risk tells you whether you should rewrite or whether it's good enough as is.
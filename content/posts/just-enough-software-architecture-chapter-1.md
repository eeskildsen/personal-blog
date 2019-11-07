---
title: "Just Enough Software Architecture: Chapter 1"
date: 2019-11-06T11:25:14-05:00
draft: false
---

> *This series loosely summarizes George Fairbanks's* Just Enough Software Architecture: A Risk-Driven Approach *as I read through it.*

# Intro

Software is getting harder. It may be the most complicated thing humans have ever built. Consequently, we need tools to approach it with.

# 3 Tools To Approach Software With

* **Partitioning:** Separate parts of a project. This lets you forget about the details. "I have a thousand classes in this project. Let me break it up into 10 libraries."
* **Knowledge:** "I've solved this problem before." "This is close to a pattern I know. Let me use it to help clean up my code."
* **Abstraction:** When driving from point A to point B, think about the roads, not the fields and parking lots.


# What's Architecture?

Architecture is:

* A tool that helps you use the tools above
* "Macroscopic design of a software system"

## Architecture Isn't Functionality

Architecture is separate from functionality. Systems with different architectures can do the same job.

Start simple. Change the architecture when you need to. Rackspace did this with an email logging system. As they grew, they changed the architecture.

1. **Version 1:** Log files lived locally on the email servers. There was a tool that `ssh`ed into the servers to grab the log files and do stuff with them.
1. **Version 2:** The email servers logged to a central database.
1. **Version 3:** The email servers logged to Hadoop Distributed File System.

## Quality Attributes Compete

There are tradeoffs. If your system is super performant, development may be difficult. If it's super scalable, it may not be flexible.

## Conceptual Models Help

A software architect could look at Rackspace's 3 versions and see patterns. This would help them reason about which one is best in a given situation.

# Abstractions and Constraints Are Useful

It's easier to think about small problems than big ones. An abstraction like "job" helps you understand what something does right away (it runs, it may have a schedule, etc.).

# What's Risk-Driven Architecture?

Approaching architecture from the perspective of risk helps you reason about how much is enough and how much is too much.

Example: The author's father has 2 mechanical engineering degrees. But when he put in a mailbox, he didn't "calculate moments, stresses, and strains." He just stuck it in the ground. Why? Low risk.

In contrast, consider Friendster. They should've expected high traffic and architected for it. Instead their site got slow, and competitors like MySpace and Facebook beat them.

*Risk-driven architecture* is about choosing just enough architecture for the task at hand. If the only risk can be handled by refactoring, do *no* architecture.
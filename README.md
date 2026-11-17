# Computer Science — Learn It From First Principles

This is my long-term engineering knowledge base. The goal is not to collect definitions or copy tutorials; it is to build a durable mental model of how software and computers actually work.

## Why this repository exists

Building applications without understanding the systems underneath eventually creates gaps: debugging becomes guesswork, architecture becomes cargo-culting, and unfamiliar technologies feel harder than they should. I want to understand the principles well enough to make engineering decisions, implement small versions of important ideas, debug failures, and explain concepts independently.

## How to learn each topic

Treat every topic as an investigation, not a chapter to finish. Work through these questions:

1. **What problem does it solve?** What becomes difficult without this concept?
2. **Why was it created?** Understand the historical context, earlier approaches, and their limitations.
3. **How does it work internally?** Trace components, data structures, protocols, state transitions, and execution flow.
4. **What are the trade-offs?** Identify costs, constraints, failure modes, and alternatives.
5. **Can I build or observe it?** Implement a small version, run an experiment, inspect a real system, or reproduce a failure.
6. **Can I explain it without notes?** Write it in your own words and identify what remains unclear.

Do not move on just because a page has been read. Move on when you can reason about the concept and use it.

## Topic note template

Use this structure for every substantial topic:

- **Problem:** What problem exists?
- **Motivation and history:** Why did this idea appear? What did it replace or improve?
- **Mental model:** What is the simplest accurate way to think about it?
- **How it works internally:** Components and step-by-step execution.
- **Example:** A concrete example or trace.
- **Implementation lab:** A small program, experiment, or practical investigation.
- **Failure modes:** What can go wrong, and how would I diagnose it?
- **Trade-offs:** Benefits, costs, limitations, and alternatives.
- **Connections:** Which other concepts does this depend on or influence?
- **Explain it back:** A short explanation from memory.
- **Open questions:** What remains unclear?

## Learning principles

- Prefer fundamentals over memorizing framework APIs.
- Draw diagrams for flows, boundaries, and state changes.
- Use code to test mental models, not to avoid forming them.
- Read documentation and primary sources where possible.
- Keep notes in your own words; link sources rather than copying them.
- Record incorrect assumptions and what changed your mind.
- Revisit older topics. Understanding deepens through retrieval and use.
- Connect each concept to something built in a real project.

## Suggested learning order

1. Programming fundamentals and data structures
2. Computer architecture and operating systems
3. Networking, beginning with HTTP
4. Databases and transactions
5. Concurrency and distributed systems
6. System design and reliability
7. AI/ML foundations: math, data, models, training, inference, and evaluation

## Repository map

| Area | Focus |
|---|---|
| [Computer Science](./computer-science/) | How computers execute programs and represent information |
| [Data Structures & Algorithms](./data-structures-algorithms/) | Organizing data and reasoning about computational cost |
| [Networking](./networking/) | How machines communicate across boundaries |
| [Databases](./databases/) | How data is stored, queried, indexed, and kept correct |
| [Distributed Systems](./distributed-systems/) | How machines coordinate despite latency and failure |
| [AI/ML](./ai-ml/) | How systems learn patterns from data |
| [System Design](./system-design/) | Designing systems under real constraints |

## What success looks like

I should be able to explain not only *what* a technology does, but **why it exists, what happens internally, what can fail, and why one design might be chosen over another**. The aim is better engineering judgment—not a large number of markdown files.

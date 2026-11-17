# Computer Science Learning Roadmap

A connected, first-principles roadmap for understanding how computers and software work — from executing a single program to building distributed systems and modern AI applications.

The goal is not to collect technologies or finish a checklist. The goal is to build accurate mental models, understand trade-offs, run experiments, and explain systems without relying on tutorials.

## The learning philosophy

Learn in dependency order. Each subject should answer questions raised by the previous one:

1. **Programming and execution:** What happens when I run a program?
2. **Computer architecture and operating systems:** How does the machine execute instructions and manage resources?
3. **Data structures and algorithms:** How can information and computation be organized efficiently?
4. **Networking:** How do programs on different machines communicate?
5. **Databases and storage:** How is information stored, queried, and kept correct?
6. **Concurrency:** How do programs coordinate multiple tasks safely?
7. **Distributed systems and system design:** How do multiple machines work together and recover from failures?
8. **AI and machine learning:** How can we build systems that learn patterns from data?

This is a recommended sequence, not a rule that every topic must be completely mastered before moving forward. Revisit topics as projects expose new questions.

## Roadmap at a glance

| Stage | Subject | Central question |
|---|---|---|
| 0 | Programming foundations and execution | What happens when code runs? |
| 1 | Computer architecture and operating systems | How does a computer execute and manage work? |
| 2 | Data structures and algorithms | How do we represent data and solve problems efficiently? |
| 3 | Computer networking | How do computers communicate? |
| 4 | Databases and storage systems | How do we store, retrieve, and protect data? |
| 5 | Concurrency and parallelism | How can multiple tasks run safely and efficiently? |
| 6 | Distributed systems and system design | How do many machines behave like one system? |
| Parallel track | Mathematics and AI/ML | How do machines learn from data? |

---

## Stage 0 — Programming foundations and execution

**Indicative time:** 1–2 weeks

### Why learn this?

Knowing a language's syntax is different from understanding what happens when a program executes. Start by connecting your code to the runtime, operating system, and processor.

### Learn

- Source code, compilation, interpretation, and runtimes.
- Variables, types, values, references, and memory.
- Functions, call stack, recursion, and scope.
- Errors, exceptions, and debugging.
- Files, directories, command-line basics, and environment variables.
- Processes at a basic level.
- Git and the development workflow.

### Investigate

What happens when you execute a Node.js program?

Trace the path from source code, through the JavaScript runtime and engine, to machine instructions and operating-system services. Understand which parts are handled by Node.js, the JavaScript engine, and the operating system.

### Build and experiment

- Write small programs that demonstrate function calls and recursion.
- Experiment with objects, references, and mutation.
- Read and write files.
- Trigger errors and inspect stack traces.
- Run a Node.js program and inspect its process using operating-system tools.

### Move on when

You can explain the difference between source code, a runtime, a process, and machine execution — and can trace a simple program's execution without guessing.

---

## Stage 1 — Computer architecture and operating systems

**Indicative time:** 3–4 weeks

### Why learn this?

Programs do not run in an abstract environment. They use physical hardware and resources managed by an operating system.

### Learn in this order

1. Bits, bytes, binary, hexadecimal, and number representation.
2. CPU, instructions, registers, and the instruction execution cycle.
3. RAM, memory addresses, cache, and the memory hierarchy.
4. Persistent storage: SSDs and filesystems.
5. Operating-system responsibilities and kernel/user space.
6. Processes, process states, and context switching.
7. Threads and basic scheduling.
8. Stack, heap, virtual memory, and address spaces.
9. System calls and permissions.

### Build and experiment

- Use Linux or WSL to inspect processes and resource usage.
- Compare the memory use of small programs.
- Explore process IDs, parent/child processes, and signals.
- Inspect files and permissions.
- Experiment with multiple processes.

### Move on when

You can explain how the CPU, memory, storage, and operating system work together to run an application.

---

## Stage 2 — Data structures and algorithms

**Indicative time:** 6–8 weeks initially; continue practicing afterward.

### Why learn this?

The way data is represented changes the time and memory required to solve a problem. Data structures and algorithms give you tools to reason about those costs.

### Learn in this order

1. Complexity analysis: time, space, and Big O.
2. Arrays and strings.
3. Hash maps and sets.
4. Stacks and queues.
5. Linked lists.
6. Recursion and backtracking.
7. Trees, binary search trees, and heaps.
8. Graphs: BFS and DFS.
9. Sorting and searching.
10. Greedy algorithms and dynamic programming.

### Build and experiment

- Implement common data structures yourself.
- Compare array search with hash-map lookup.
- Implement a queue and use it to process jobs.
- Represent prerequisite relationships as a graph.
- Solve problems and explain the complexity of your solution.

### Connect it to real software

- Hash maps appear in caches and lookup-heavy applications.
- Trees appear in indexes and hierarchical data.
- Queues appear in job processing.
- Graphs represent dependencies, routes, and relationships.

### Move on when

You can choose a data structure for a particular problem, explain why it fits, and estimate the time and space costs.

---

## Stage 3 — Computer networking

**Indicative time:** 3–4 weeks

### Why learn this?

A backend application is often a program communicating with other programs across a network. Networking explains what happens between a client and a server.

### Learn in this order

1. Networks, IP addresses, ports, and packets.
2. DNS and domain-name resolution.
3. TCP and UDP.
4. Client-server communication.
5. HTTP request/response model.
6. HTTP methods, status codes, headers, and body.
7. HTTPS, TLS, certificates, and the handshake.
8. Cookies, sessions, and authentication at the protocol level.
9. REST APIs and WebSockets.
10. Proxies, load balancers, and CDNs.

### Investigate

What happens after you enter an HTTPS URL in a browser?

Trace DNS resolution, connection establishment, TLS negotiation, the HTTP request, server processing, the response, and browser rendering. Keep track of which layer is responsible for each step.

### Build and experiment

- Build a minimal HTTP server.
- Send requests using curl.
- Inspect requests in browser DevTools.
- Compare HTTP and HTTPS.
- Build a simple WebSocket client and server.
- Observe what changes when a server is unreachable.

### Move on when

You can explain how a browser reaches a server, how an HTTP request travels, and what TCP and TLS contribute.

---

## Stage 4 — Databases and storage systems

**Indicative time:** 4 weeks

### Why learn this?

Applications need to store information reliably, retrieve it efficiently, and handle multiple users changing data at the same time.

### Learn in this order

1. Relational data models, tables, rows, and relationships.
2. SQL: filtering, joins, grouping, and constraints.
3. Schema design and normalization.
4. Indexes and B-trees.
5. Query planning and execution.
6. Transactions and ACID properties.
7. Isolation levels and concurrency anomalies.
8. Locks and MVCC.
9. Replication and partitioning.
10. NoSQL data models and trade-offs.

### Build and experiment

- Build a small application using PostgreSQL.
- Design its schema and constraints.
- Add indexes and compare query plans.
- Run transactions from multiple sessions.
- Reproduce a concurrency problem and investigate how isolation affects it.
- Compare a relational data model with a document-oriented model.

### Connect it to previous stages

- Indexes depend on data structures.
- Database processes use operating-system resources.
- Storage engines interact with memory and disks.
- Applications communicate with databases over networks.
- Transactions coordinate concurrent operations.

### Move on when

You can explain how a database stores and retrieves records, why indexes help, and how transactions protect data.

---

## Stage 5 — Concurrency and parallelism

**Indicative time:** 3–4 weeks

### Why learn this?

Real applications handle overlapping requests and tasks. Concurrency introduces coordination problems that do not appear in simple sequential programs.

### Learn

- Concurrency versus parallelism.
- Processes versus threads.
- Asynchronous I/O and event loops.
- CPU-bound versus I/O-bound work.
- Race conditions.
- Critical sections, mutexes, and semaphores.
- Deadlocks and starvation.
- Shared state and synchronization.
- Garbage collection and resource cleanup.

### Build and experiment

- Process multiple jobs concurrently.
- Create a race condition intentionally and then fix it.
- Compare sequential and concurrent I/O.
- Experiment with CPU-bound and I/O-bound workloads.
- Investigate how Node.js handles asynchronous operations.

### Move on when

You can explain why concurrency is useful, what can go wrong when tasks overlap, and how coordination mechanisms help.

---

## Stage 6 — Distributed systems and system design

**Indicative time:** 4–6 weeks initially; deepen through projects.

### Why learn this?

A system running on one machine has limits. Production systems often use many services and machines, where networks fail, data gets out of sync, and processes crash independently.

### Learn in this order

1. Monoliths, services, and distributed-system basics.
2. Stateless versus stateful services.
3. Caching and cache invalidation.
4. Message queues and background workers.
5. Retries, timeouts, and idempotency.
6. Replication and consistency.
7. Partitioning and sharding.
8. Failure detection and fault tolerance.
9. Rate limiting and backpressure.
10. Observability: logs, metrics, and traces.
11. Capacity estimation and system-design trade-offs.

### Build and experiment

Build a small service with:

- An API server.
- PostgreSQL for persistent data.
- Redis for caching or coordination.
- A background worker and a queue.

Then experiment:

- What happens when the worker crashes?
- What happens when a job is delivered twice?
- What happens when Redis is unavailable?
- What happens when the database responds slowly?
- How do retries affect the system?
- How can you observe and debug failures?

### Move on when

You can reason about partial failures, retries, consistency, and the trade-offs involved in scaling an application across multiple machines.

---

# Parallel track — Mathematics and AI/ML

You do not need to complete every systems topic before beginning AI/ML. Start building the mathematical and Python foundations alongside the early CS stages. Then follow this sequence.

## AI/ML Stage A — Mathematics

- Linear algebra: scalars, vectors, matrices, matrix multiplication.
- Probability and statistics.
- Functions and logarithms.
- Derivatives and gradients.
- Basic optimization.

**Goal:** Understand the mathematical operations used in machine learning instead of treating them as library magic.

## AI/ML Stage B — Python and scientific computing

- Python fundamentals.
- NumPy.
- Pandas.
- Matplotlib.
- Jupyter notebooks.
- Working with datasets.

**Goal:** Become comfortable manipulating data and experimenting with mathematical operations in code.

## AI/ML Stage C — Classical machine learning

- Supervised and unsupervised learning.
- Regression and classification.
- Decision trees and ensemble methods.
- Clustering.
- Loss functions.
- Gradient descent.
- Overfitting, underfitting, and regularization.
- Train/validation/test splits and evaluation metrics.

**Goal:** Understand how a model learns from examples and how to evaluate whether it generalizes.

## AI/ML Stage D — Deep learning

- Neurons and layers.
- Activation functions.
- Forward propagation.
- Backpropagation.
- Optimizers.
- Training loops.
- Regularization.
- Frameworks such as PyTorch.

**Goal:** Understand how neural networks represent patterns and update their parameters during training.

## AI/ML Stage E — NLP and Transformers

- Text preprocessing and tokenization.
- Embeddings.
- Sequence models and attention.
- Self-attention and multi-head attention.
- Positional information.
- Transformer architecture.
- Pretraining and fine-tuning.

**Goal:** Understand the architecture behind modern language models, not just how to call an API.

## AI/ML Stage F — LLMs and AI engineering

- Tokenizers and context windows.
- Inference and sampling.
- Prompting and structured outputs.
- Retrieval-augmented generation (RAG).
- Embedding models and vector search.
- Evaluation and observability.
- Tool calling and agent architectures.
- Reliability, security, and cost trade-offs.

**Goal:** Connect model internals to reliable real-world AI applications.

---

# How to study every topic

Use this six-step learning cycle for every important concept.

### 1. Find the problem

Ask what problem existed before this concept and why the concept was introduced.

### 2. Build a mental model

Draw the components and their relationships. Explain the idea in simple language.

### 3. Understand the internals

Trace what happens step by step. Identify which component is responsible for each action.

### 4. Build a tiny implementation

Create a simplified version yourself. It does not need to be production-ready.

### 5. Experiment with the real system

Run commands, inspect logs, measure behavior, and deliberately create failures.

### 6. Connect and explain

Connect the idea to another concept or one of your projects. Explain it from memory without looking at your notes.

## Questions every topic README should answer

For each concept, write down:

1. What problem does it solve?
2. Why was it created?
3. How does it work internally?
4. What happens step by step?
5. What are its trade-offs and limitations?
6. Where is it used in real software?
7. Can I implement a simplified version?
8. Can I explain it without a tutorial?

Do not write notes just to summarize articles. Write notes that capture your own mental model, experiments, observations, and unresolved questions.

---

# A sustainable weekly routine

Use this as a starting point and adjust it to your actual schedule.

| Activity | Weekly target |
|---|---|
| Main CS subject | 4 focused sessions |
| DSA practice | 3–4 short sessions |
| AI/ML mathematics | 2 short sessions |
| Practical experiment | 1 focused session |
| Revision and explanation | 1 session |

Avoid studying six unrelated subjects every day. Focus on one primary subject at a time, while keeping DSA and mathematics as lighter parallel practices.

## A good study session

- **Understand:** Read or study one small concept.
- **Draw:** Make a diagram or trace the execution flow.
- **Experiment:** Run a command, inspect a program, or write a small implementation.
- **Explain:** Write what you understood in your own words.
- **Connect:** Note where this concept appears in another subject or project.

Consistency and understanding are more important than finishing the roadmap quickly.

---

# Your first assignment

Start with this question:

## What happens when I execute a program?

Investigate these six concepts in order:

1. Binary, bits, and bytes — how is information represented?
2. CPU and instructions — how does the processor execute work?
3. RAM and memory — where does running program data live?
4. Programs and processes — what happens when I start an application?
5. Stack and heap — how is memory organized while a program runs?
6. Operating system — how are programs and resources managed?

### Practical assignment

Use your terminal and WSL:

- Write a small Node.js program.
- Run it and find its process.
- Inspect its process ID and memory usage.
- Change the program and observe what changes.
- Draw the path from your source code to the running process.
- Explain the roles of Node.js, the JavaScript engine, the OS, CPU, and RAM.

**Do not move on just because you finished reading. Move on when you can explain the execution journey in your own words.**

---

## Final principle

Do not make the goal "finish computer science."

Make the goal to become an engineer who understands why software works, how it works internally, why it fails, and how to design it better.

Build things, investigate what happens underneath them, and keep connecting new knowledge to what you already understand.

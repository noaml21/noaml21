# Noam Levi

Computer Science student at Bar-Ilan University, focused on systems programming, Linux security and machine learning.

I like building things down to the operating-system level and proving that they work: every project below
has an automated test suite, runs in CI, and documents its own limitations alongside what it achieves.

## Featured Projects

### 🛡️ [AgentGuard](https://github.com/noaml21/agentguard): a kernel-enforced sandbox for AI coding agents
`C` · `Linux` · `Landlock` · `seccomp-BPF` · `cgroups v2` · `Bash` · `Python`

A C launcher that runs an AI coding agent, and every process it spawns, inside a sandbox enforced by the Linux kernel.
Landlock restricts filesystem access by inode, so symlinks, hard links and renames cannot escape it. seccomp-BPF blocks
ptrace, namespaces, mounts, bpf and io_uring. Network access is denied by default, and startup fails closed if any
required layer cannot be applied.
- An effect-based red-team corpus of 36 attacks: V2 blocks all 14 bypasses of the V1 hook layer that target files outside the workspace
- 226/226 sandbox tests, also clean under ASan + UBSan, plus a threat model that lists the residual risks

### ⚙️ [Linux Concurrency & IPC Lab](https://github.com/noaml21/linux-concurrency-ipc): a C11 benchmark engine for synchronization and IPC
`C11` · `pthreads` · `System V IPC` · `shared memory` · `Python` · `Textual`

Benchmarks mutexes, System V semaphores, pipes, FIFOs and a semaphore-based bounded MPSC ring buffer in shared memory.
Every transferred record is validated, so missing, duplicate or corrupted records are counted and failed runs are
excluded from the statistics.
- Fault injection (stalls, fork failures, signals) that checks every process and IPC object is cleaned up
- A batched ring variant with 1.83–3.08× median throughput at capacity 64, measured in a reproducible 80-run study
- An interactive terminal lab for seeded experiments, run history and comparisons; CI runs GCC and Clang with sanitizers

### 🤖 [MLForge](https://github.com/noaml21/ml-from-scratch): an end-to-end, local-first ML workbench
`Python` · `scikit-learn` · `NumPy` · `Textual`

A terminal application that takes a tabular dataset from a raw file to an evaluated model, then exports that model
as an installable Python package. It is leakage-safe by construction: data is split before any preprocessing is fitted.
Training runs in supervised child processes with cancellation, and the model you inspect is exactly the one that is exported.
- 707 automated tests; exported models are verified in isolated environments against the in-app predictions
- Grew out of from-scratch NumPy implementations of K-Means, Logistic Regression and PCA, compared against scikit-learn

### 🍔 [Better Wolt](https://github.com/noaml21/better-wolt): a full-stack food-delivery platform (team project, 97/100)
`React` · `React Native / Expo` · `Node.js` · `Express` · `MongoDB` · `Docker`

A React web app and an Expo mobile app on one REST API, designed in Hebrew, right to left. It started as a team
course project; after the course I took it through three further iterations on the architecture, design and security.
- Server-side pricing, a tested authorization matrix, Zod validation at the API boundary, bcrypt with rate-limited sign-in
- A multi-stage, non-root Docker image and CI that runs the API, web and mobile builds

## Tech Stack

- **Languages:** C · Python · JavaScript · Bash
- **Systems & Security:** Linux internals · POSIX IPC · pthreads · Landlock · seccomp · sanitizers (ASan/UBSan)
- **ML & Data:** NumPy · scikit-learn
- **Web & Tools:** React · React Native · Node.js · MongoDB · Docker · Git · GitHub Actions

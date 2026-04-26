<div align="center">

<img src="./static/image/murmur-logo.png" alt="Murmur logo" width="65%"/>

**Murmur, local-first intelligence for your own machine**

[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg?style=flat-square)](./LICENSE)
[![Go Version](https://img.shields.io/badge/Go-1.23+-00ADD8.svg?style=flat-square&logo=go)](https://go.dev/)
[![Desktop](https://img.shields.io/badge/Desktop-Wails-6C47FF?style=flat-square)](https://wails.io/)
[![Monitoring](https://img.shields.io/badge/Monitoring-Netdata-00AB44?style=flat-square)](https://www.netdata.cloud/)
[![Status](https://img.shields.io/badge/Status-v0.1.0%20roadmap-orange?style=flat-square)](#roadmap)

Private multi-agent reasoning, structured memory, and Obsidian-native knowledge workflows — running locally as a lightweight desktop intelligence appliance.

</div>

> [!NOTE]
> **Murmur** is a local-first evolution of the Mirofish-style workflow, redesigned around a Go-first runtime, durable local memory, native desktop packaging, and operator-owned data. The goal is simple: keep the intelligence loop on your machine, keep the evidence human-readable, and keep the stack small enough to run comfortably on normal hardware.

## Why Murmur

Most AI tools are cloud-first, opaque, and heavy. Murmur takes the opposite approach:

- **Local-first** — your notes, simulations, and memory stay on your device.
- **Go-first** — the runtime, orchestration, and core services are designed for a small, efficient native stack.
- **Obsidian-native** — Murmur turns internal agent state into readable markdown and linked evidence in your vault.
- **Desktop-first** — the release target is a native app, not a browser tab full of infrastructure.
- **Operator-friendly** — system health and node metrics can be monitored with Netdata when you need them.

## What Murmur does

Murmur is designed as an intelligence appliance for private research and structured reasoning. A typical flow looks like this:

1. **Ingest context** — documents, notes, or seed materials are loaded into the local workspace.
2. **Build memory** — facts, entities, and relationships are stored in Murmur’s local memory layers.
3. **Run agents** — the swarm reasons over the context using a controlled local runtime.
4. **Generate evidence** — reports, summaries, and linked facts are written back as structured outputs.
5. **Sync to Obsidian** — the final knowledge is exported as markdown you can read, keep, and extend.

## Core architecture

Murmur is intentionally split into a few clear layers:

| Layer | Purpose | Planned stack |
| --- | --- | --- |
| Engine | Orchestration, runtime, agent loop | Go core, binary message flow, queue-based task execution |
| Memory | Fast active state + durable persistence | BuntDB, BadgerDB, typed graph relations |
| Knowledge | Human-readable long-term evidence | Obsidian markdown export |
| Security | Sandboxed tools and policy checks | gVisor experiments, path restrictions, Casbin |
| Desktop | Native user experience | Wails |
| Monitoring | System health and node observability | Netdata |

## Design goals

Murmur is being built around a few non-negotiable goals:

- **Fast local runtime**
- **Low moving parts**
- **Private-by-default operation**
- **Human-readable outputs**
- **Native desktop distribution**
- **Reasonable performance on mid-range hardware**
- **Raspberry Pi support as a preview target, not a fake promise**

## Realistic user experience

For end users, Murmur should feel like an app — not a dev environment.

### Release experience

- Download the installer.
- Open Murmur.
- Choose a workspace or vault.
- Add source material.
- Run a reasoning workflow.
- Read the exported markdown and reports locally.

End users should **not** need to manually install Go, Docker, databases, or internal runtime dependencies.

### Developer experience

The development path is intentionally separate from the end-user path:

- Backend/runtime in Go
- Desktop shell via Wails
- Local-first storage and export
- Optional monitoring with Netdata during development or node operation

## Quick start

### End users

When Murmur reaches packaged releases, the intended path is:

1. Download the app for your platform.
2. Install and launch Murmur.
3. Select or create a local workspace.
4. Connect an Obsidian vault folder if you want markdown sync.
5. Start a run.

### Developers

> [!IMPORTANT]
> This section describes the development workflow, not the normal user install path.

Expected local developer flow:

- Go services run locally
- Desktop shell runs through Wails
- Local storage remains embedded
- Monitoring is optional unless you are profiling or running a long-lived node

## Architecture principles

### 1. Local-first memory

Murmur separates hot memory from durable memory:

- **Hot state** is for active agent thoughts and runtime state.
- **Warm/durable state** is for preserved memory and structured artifacts.
- **Vault export** is for human-readable long-term evidence.

This keeps the runtime fast without turning the Obsidian vault into the execution database.

### 2. Obsidian-native knowledge

Obsidian is not treated as a gimmick integration. Murmur is designed to export readable markdown notes, fact links, and report artifacts that stay useful even outside the app.

### 3. Safe tool execution

Tool use is planned to run behind explicit policy boundaries:

- restricted file access
- allowlisted actions
- bounded execution
- auditability
- sandbox-first experiments where supported

### 4. Small native footprint

Murmur is being built as a native desktop app instead of an Electron-style bundle. The aim is a lightweight release that starts quickly, stays responsive, and runs locally without dragging in unnecessary moving parts.

## Monitoring

Murmur uses **Netdata** as the overall monitoring layer for node health and runtime observability.

Use Netdata when you want to monitor:

- CPU
- memory
- disk
- temperature
- process health
- long-running local node behavior

For most normal desktop users, monitoring is optional. For advanced users running Murmur continuously or on a Raspberry Pi, it becomes much more useful.

## Hardware expectations

Murmur is being designed for normal machines first.

| Device | Expected support |
| --- | --- |
| Windows desktop / laptop | Primary release target |
| Linux desktop / laptop | Supported developer and advanced-user target |
| macOS | Planned desktop target |
| Raspberry Pi 5 | Preview / appliance target |
| Raspberry Pi 4 | Experimental / constrained target |

> [!WARNING]
> Large graphs, long-running agent loops, and heavy models can still exceed lightweight systems. Murmur is local-first, not magic.

## Use cases

Murmur is a good fit for:

- private research workflows
- local evidence synthesis
- multi-agent scenario exploration
- personal or team knowledge work
- Obsidian-linked analysis
- low-infrastructure intelligence appliances
- Raspberry Pi experimentation for always-on local nodes

## Roadmap

### v0.1.0 target

The current target is a realistic “industrial-grade” local release with:

- Go-first runtime
- embedded local memory
- Obsidian markdown export
- native desktop shell
- monitoring support
- safer tool execution
- Windows-first stable packaging
- Raspberry Pi preview support

## Status

Murmur is currently in active architecture and implementation planning. The project direction is clear, but the release is intentionally scoped to stay realistic for a solo developer building a stable local-first system.

## Contributing

Issues, discussions, and thoughtful PRs are welcome.

If you want to contribute:

1. Open an issue first for major changes.
2. Keep changes aligned with the local-first design goals.
3. Avoid introducing unnecessary infrastructure or cloud-only assumptions.
4. Prefer simple, testable Go-first implementations.

## License

[AGPL-3.0](./LICENSE)

## Acknowledgments

Murmur is forked from [go-mirofish](https://github.com/go-mirofish/go-mirofish), which itself builds on the broader [MiroFish](https://github.com/666ghj/MiroFish) direction. Murmur is developed as a standalone project with its own roadmap, release cycle, and product focus.

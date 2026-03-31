# Codebase Comprehension

A Claude Code skill for systematic code exploration and understanding.

## Overview

`codebase-comprehension` provides a systematic approach to understanding any codebase regardless of scale. It guides AI agents through L1→L2→L3→L4 progressive depth to build a complete mental model efficiently.

## When to Use

- Onboarding to a new project
- Understanding large-scale architecture
- Finding specific functionality in big codebases
- Analyzing critical paths for modifications
- Any scenario requiring "how does this work?"

## Installation

```bash
# Clone to Claude Code skills directory
cd ~/.claude/skills
git clone https://github.com/YOUR_USERNAME/codebase-comprehension.git
```

Or use Claude Plugin:

```bash
claude plugin marketplace add https://github.com/YOUR_USERNAME/codebase-comprehension
claude plugin install codebase-comprehension@codebase-comprehension --scope user
```

## Quick Start

Tell Claude to analyze a codebase:

> "Help me understand this project" or "Explore the architecture of this codebase"

The skill will automatically apply L1→L2→L3→L4 progressive analysis.

## Methodology

### L1: Global Scan

Build overall understanding:
- Identify tech stack
- Locate entry files
- Analyze directory structure
- Estimate code scale

### L2: Module Partition

Understand system boundaries:
- Trace dependencies from entry points
- Identify core modules (most referenced)
- Analyze module responsibilities
- Generate Mermaid dependency graph

### L3: Data Flow Tracing

Understand how the system works:
- Trace request lifecycle
- Analyze data transformation
- Map state management
- Generate Mermaid sequence diagram

### L4: Deep Dive

Understand core logic:
- Identify critical paths
- Find boundary conditions (timeout, retry, concurrency)
- Assess risks for modifications
- Generate decision point tables

## Output

The skill generates a comprehensive Markdown report with:

- Tech stack analysis
- Module dependency diagrams (Mermaid)
- Data flow diagrams (Mermaid)
- Code statistics
- Risk assessment (for modification scenarios)

## Scale-Based Strategy

| Codebase Size | Strategy |
|--------------|----------|
| Small (<10K lines) | Full scan + focused reading |
| Medium (10K-100K) | Partitioned scan + correlation |
| Large (>100K) | Priority-driven + incremental |

## Mermaid Compatibility

This skill generates Mermaid diagrams with maximum compatibility:

- English labels only
- Double quotes for non-ASCII text
- No subgraph (not widely supported)
- `participant` syntax in sequence diagrams

Example:

```mermaid
graph TD
    A["root/"] --> B["src/"]
    B --> C["components/"]

sequenceDiagram
    participant User
    participant System
    User->>System: request
```

## Project Structure

```
codebase-comprehension/
├── SKILL.md              # Main skill definition
└── README.md             # This file
```

## License

MIT

## Inspired By

- [web-access](https://github.com/eze-is/web-access) - Claude Code联网能力skill
- Superpowers skills framework
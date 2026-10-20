# Repolex Knowledge Graph of asottile/gh-perf-review

RDF knowledge graph data for [asottile/gh-perf-review](https://github.com/asottile/gh-perf-review), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download asottile/gh-perf-review
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 57c067bddd257966945cb613d064675d9db94d32
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 57c067bddd257966945cb613d064675d9db94d32
│           └── chunk-001.nq.gz
├── blob
│   ├── 426f19735ceaf538d1bf14bc35882304bf284d29.nq.gz
│   ├── 4f82b90de14714164385f088f7a5417568619738.nq.gz
│   ├── 8fe0360c7062b64696f804cd090bac7c77b5ab6f.nq.gz
│   ├── a6cfb701f73d88ec037042a71c80c66eeeaad11c.nq.gz
│   ├── e03e944532a11962fd394d18a60221fb9943e5f7.nq.gz
│   └── f1543fad215851e7e301b045b4b8f95a1e446d9c.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 57c067bddd257966945cb613d064675d9db94d32.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 14 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[asottile/gh-perf-review](https://github.com/asottile/gh-perf-review)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*

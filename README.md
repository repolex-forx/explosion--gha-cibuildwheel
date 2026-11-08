# Repolex Knowledge Graph of explosion/gha-cibuildwheel

RDF knowledge graph data for [explosion/gha-cibuildwheel](https://github.com/explosion/gha-cibuildwheel), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/gha-cibuildwheel
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 2ade48ac7d4fed55e9f24f73eddd8f280722a2f8
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 2ade48ac7d4fed55e9f24f73eddd8f280722a2f8
│           └── chunk-001.nq.gz
├── blob
│   ├── 01f6b40ef73b57144670fd92a48933d6805fa507.nq.gz
│   ├── 13d70059f2aa4418243a0bfd30bced916a1a48e7.nq.gz
│   └── 14da42b00358564dc770eab35a8d2b7bca567f5a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 2ade48ac7d4fed55e9f24f73eddd8f280722a2f8.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 10 files
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

[explosion/gha-cibuildwheel](https://github.com/explosion/gha-cibuildwheel)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*

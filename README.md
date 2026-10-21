# Repolex Knowledge Graph of py-pdf/pdf-crawler

RDF knowledge graph data for [py-pdf/pdf-crawler](https://github.com/py-pdf/pdf-crawler), parsed by [repolex](https://repolex.ai).

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
rlex download py-pdf/pdf-crawler
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 8c9228a22faf313ea12f15847cb59eedfc5e5e44
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 8c9228a22faf313ea12f15847cb59eedfc5e5e44
│           └── chunk-001.nq.gz
├── blob
│   ├── 0d5b44e0b6d6eb9d5853631ebc45e5bb5340f529.nq.gz
│   ├── 0d78eaf13e4c6ab6eab096621ecaaa17bc5afc8a.nq.gz
│   ├── 281a9a0971d4ab8262259d90c4cbc7b575365908.nq.gz
│   ├── 4f3170899e01eb33cc0d57b219c6b93ccde46f10.nq.gz
│   ├── 7979dc00299ecabc3691eae8adbba32266ff8270.nq.gz
│   ├── 7a50801f4f3c1429a24eadfe8f74c4869022d0df.nq.gz
│   ├── b190e9ce50936202a6caeae2117e13055a48bb4b.nq.gz
│   ├── b7d7db05da73de834fe55842354c3d613a538af1.nq.gz
│   ├── df364248f42967e404dd7dbc8d065e36bfa8d8ef.nq.gz
│   ├── e29a132af7a6b9d921d5991ba1b21be3aef231ec.nq.gz
│   ├── e65d57734e0e5063d11704c77589d421004222f7.nq.gz
│   └── f2f2c19f14a4640572208abfb1126e452cf847f6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 8c9228a22faf313ea12f15847cb59eedfc5e5e44.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 18 files
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

[py-pdf/pdf-crawler](https://github.com/py-pdf/pdf-crawler)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*

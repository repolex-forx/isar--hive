# Repolex Knowledge Graph of isar/hive

RDF knowledge graph data for [isar/hive](https://github.com/isar/hive), parsed by [repolex](https://repolex.ai).

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
rlex download isar/hive
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1b4febe967370f790759823a5e154adc383e53d3
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1b4febe967370f790759823a5e154adc383e53d3
│           └── chunk-001.nq.gz
├── blob
│   ├── 084ba1f4890398bdf13d90020f6571cac5ca820c.nq.gz
│   ├── 10c1f647b2b123129413ac548b695bc01bad66c5.nq.gz
│   ├── 12050404378f1ed971fe544ddb342bf4202d3af1.nq.gz
│   ├── 1a07e3bf820f915dfe1b1eff8c9d156f0b6bcb6b.nq.gz
│   ├── 2a6d503c47e81426491cbfe107ae371b7f76741b.nq.gz
│   ├── 33651b52c93857eca5c5d48f2e0590dac3dd1a24.nq.gz
│   ├── 3f106f107b6218caf682bb970029f180d34ff600.nq.gz
│   ├── 4389651225dc16fe809a262dc3f7ea7869de9c83.nq.gz
│   ├── 478b2e2acca28cbe7c070eff38d6d3556f468288.nq.gz
│   ├── 62a2881fb483a8b4ffcc3a3d38d88575242f18ec.nq.gz
│   ├── 790179f506f2443953c67c055a7705c6cb17adb9.nq.gz
│   ├── 85ad35931fe123d2c454cf6aae5989b575d9e7be.nq.gz
│   ├── 8a679165eb139904c4f6222db166502169e42436.nq.gz
│   ├── afcd4d86e9bbd589367636399d947a4b26060bd5.nq.gz
│   ├── b046235d1f68c6d42d4a400e7f5c5ada98449689.nq.gz
│   ├── be434cb42b50a08f236347e218000f6bfd883164.nq.gz
│   ├── c568581b235db2160e40792cc5a33f26c7c974fb.nq.gz
│   ├── c8e0d7e8b75a4ac88092aaa73eb309fd95d31475.nq.gz
│   ├── df18e99ff6f13a47d95764b35e8191486b1b1ea0.nq.gz
│   ├── ed5d8f023606bf1168feb7d5d6972e742e37f588.nq.gz
│   ├── f49a4e16e68b128803cc2dcea614603632b04eac.nq.gz
│   └── f4cee3b6a749569d749382e4992ec18b623ca45e.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1b4febe967370f790759823a5e154adc383e53d3.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 30 files
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

[isar/hive](https://github.com/isar/hive)

---
*Parsed on 2026-11-09 by [repolex](https://repolex.ai)*

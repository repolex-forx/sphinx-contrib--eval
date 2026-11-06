# Repolex Knowledge Graph of sphinx-contrib/eval

RDF knowledge graph data for [sphinx-contrib/eval](https://github.com/sphinx-contrib/eval), parsed by [repolex](https://repolex.ai).

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
rlex download sphinx-contrib/eval
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── b19de8e74a72ad3e49cab547967b6811d0905ae3
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── b19de8e74a72ad3e49cab547967b6811d0905ae3
│           └── chunk-001.nq.gz
├── blob
│   ├── 0864efbbf938d28e6f48aa2ebdbeecce03f0cd98.nq.gz
│   ├── 18c63519e99e4498977a589fc2731913946f0b2c.nq.gz
│   ├── 1bd32282ef5ddce4f643c5b1e6d1d9db0188cb9e.nq.gz
│   ├── 209d62fd65c87c0afd187808464af4a346d40d2c.nq.gz
│   ├── 23128d81133422b8aac8014db5c5a434b8e39a2d.nq.gz
│   ├── 26172d29971594379ab40ce46722d098ff5a041d.nq.gz
│   ├── 29afad1b558f1bf70024d396d1c248c75239df15.nq.gz
│   ├── 2b2f105ec30e94afcbf483916ccfed393e106235.nq.gz
│   ├── 2cdf4481e741a35905b96109c6df1017e7b315ac.nq.gz
│   ├── 436ff16d4e59e426517c7ca77e9f7a9f3ad4f9c9.nq.gz
│   ├── 4b9aae5f4e58106f299cf9de106c3c1945eb3463.nq.gz
│   ├── 563c0b4a39d050dcad9ded85e1b03b908e934c65.nq.gz
│   ├── 57747ac2e666de87c1210de76014172b6f3dce01.nq.gz
│   ├── 6c837615295dd7dfb19724c0c46859eec4888a46.nq.gz
│   ├── 6e70a3b85a5d39c8746c329d85b6e4a7d66b0993.nq.gz
│   ├── 723d6d4950b82908fec53435427fae03b9b1f1ff.nq.gz
│   ├── 7956a7b06bf7260bdfd5dea6b2c2d1e86786be03.nq.gz
│   ├── 79727be7e4f7d005596a2aaed063822e4f3ef005.nq.gz
│   ├── 8136c679e75205f459ecf85c152915ef87594d4a.nq.gz
│   ├── 89a3f3213ac6c9438d70dec80ec4627ee5dbd078.nq.gz
│   ├── 8e524ecd21ad2ed97c2ceb38b68c42b36da133d0.nq.gz
│   ├── 8f2b4d8415f6d51ba33bfa28729bb0681445e340.nq.gz
│   ├── b4c47fa3ce13c2a17706d89d3a434b6ddd4a83fd.nq.gz
│   ├── b9df012f9294decb8f7d635f88afad20c70f5116.nq.gz
│   ├── be0ff9577cdd4d1844720b07a8292463962a12f6.nq.gz
│   ├── c1f9d2ed05a92e7fc43aad78d74cb8430b140610.nq.gz
│   ├── d934abd5ceca10e7ba51a0c07de36459a5c364e9.nq.gz
│   ├── dfcf15aaf4c897dc0d409b9e9fb99a1ee072dac7.nq.gz
│   ├── e4670b0ca40a98dbd0dcf0d988ec0ea3f9299cd1.nq.gz
│   ├── e525ed9a265af771c02411a7451623f872749003.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e893f7b00d49cd2d972ac8433d99fe3b2eab60a8.nq.gz
│   ├── f23df4aea8c40b5c55b6a041333ea11bcefa09b1.nq.gz
│   ├── f288702d2fa16d3cdf0035b15a9fcbc552cd88e7.nq.gz
│   ├── f5a6281cea667971af2af967d57bbf6638546392.nq.gz
│   ├── fc27acea14a45c2ee20a3296db686f81e64b5cff.nq.gz
│   └── ff1245960940e171e5db2f2cd7d5961dba514493.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── b19de8e74a72ad3e49cab547967b6811d0905ae3.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 44 files
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

[sphinx-contrib/eval](https://github.com/sphinx-contrib/eval)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*

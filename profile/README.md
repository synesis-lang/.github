# Synesis

> **The confluence of information into intelligence.**

A Domain-Specific Language and toolchain for transforming qualitative research annotations into structured, auditable knowledge.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)

---

## What is Synesis?

Qualitative research — literature reviews, grounded theory, case studies — generates enormous amounts of interpretive work that is typically lost in unstructured notes, spreadsheets, or proprietary software.

Synesis is a **compiler for analytical thinking**: you write your interpretations in plain-text files with a clean declarative syntax, and the toolchain validates, structures, and exports them as canonical knowledge artifacts. Discipline becomes a form of freedom — by delegating logical organization to a formal structure, the mind stays free for what truly matters: interpretation, nuance, and insight.

The result is true **σύνεσις** — the convergence of evidence fragments into an intelligible, auditable, and technically rigorous whole.

---

## The Ecosystem

```mermaid
graph TD
    Z["📚 Zotero\n(PDF annotations & tags)"]
    ZP["🔌 zotero-synesis-export\n(.xpi plugin)\nexports raw .syn\nno chains or ontology codes"]
    SC["🤖 synesis-coder\n(AI-assisted annotation)\ngenerates full .syn with chains\nand codes per project template"]
    SYN["📄 .syn / .synt / .syno / .synp\n(Synesis source files)"]
    C["⚙️ Synesis Compiler\n(LALR parser · AST validator · exporters)"]
    API["🐍 Python API\nsynesis.load() · to_dataframe()"]
    LSP["🧠 Synesis LSP\n(Language Server Protocol)"]
    EXT["🖥️ Synesis Explorer\n(VS Code extension)"]
    JP["📓 Jupyter Notebook\n(data science · visualization)"]
    OUT["📊 Structured Outputs\nJSON · CSV · Excel · REFI-QDA"]
    NEO["🕸️ Graph Database\nNeo4j / Memgraph"]
    MCP["🤖 AI Agents\nClaude Desktop via MCP"]

    Z -->|"export highlights & tags\n(plain .syn, no chains)"| ZP
    ZP -->|raw annotations| SYN
    SYN -->|"human codes .syn\nwith chains + ontology codes"| EXT
    EXT -->|"template-aware\nAI coding request"| SC
    SC -->|"fully coded .syn\n(chains · codes · fields)"| SYN
    SYN -->|parsed & validated| C
    C --> API
    C -->|AST + diagnostics| LSP
    LSP -->|JSON-RPC / stdio| EXT
    API -->|to_dataframe · to_json_dict| JP
    C -->|compile| OUT
    OUT -->|import| NEO
    NEO -->|graph queries| MCP
```

---

## Repositories

| Repository | Language | Role |
|---|---|---|
| [synesis](https://github.com/synesis-lang/synesis) | Python | Compiler, parser, validator, exporters, Python API |
| [synesis-lsp](https://github.com/synesis-lang/synesis-lsp) | Python | Language Server — diagnostics, hover, completion, semantic tokens |
| [synesis-explorer](https://github.com/synesis-lang/synesis-explorer) | JS/TS | VS Code extension — tree views, graph viewer, themes |
| [zotero-synesis-export](https://github.com/synesis-lang/zotero-synesis-export) | JavaScript | Zotero 7 plugin — exports PDF highlights and tags as plain `.syn` (no chains or ontology codes) |
| [synesis2neo4j](https://github.com/synesis-lang/synesis2neo4j) | Python | Import compiled knowledge into Neo4j / Memgraph |
| [synesis-coder](https://github.com/synesis-lang/synesis-coder) | Python | AI-assisted annotation — generates fully coded `.syn` files (chains, codes, fields) conforming to the project template |

---

## Potential Applications

| Domain | How Synesis helps |
|---|---|
| **Systematic literature reviews** | Annotate hundreds of papers with a shared template; export clean datasets for meta-analysis |
| **Grounded Theory / Thematic Analysis** | Build and validate code systems with ontological constraints; trace every code to its source |
| **Mixed-methods research** | Bridge qualitative interpretation with quantitative formats for R or Python workflows |
| **Knowledge graphs** | Compile research findings into Neo4j; model causal chains as graph edges |
| **AI-augmented analysis** | Feed structured annotations as context to LLMs via MCP; responses traceable to source evidence |
| **Biblical / exegetical studies** | Code canonical texts with relational chains; integrate classical and patristic corpora |
| **Longitudinal projects** | Template versioning and strict validation prevent concept drift across research phases |

---

## Quick Start

```bash
pip install synesis synesis-lsp
```

Install the [VS Code extension](https://github.com/synesis-lang/synesis-explorer/releases) and the [Zotero plugin](https://github.com/synesis-lang/zotero-synesis-export/releases). Full documentation at **[synesis-lang.github.io](https://synesis-lang.github.io)**.

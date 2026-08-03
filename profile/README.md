# Synesis

> **The confluence of information into intelligence.**

A Domain-Specific Language and toolchain for transforming qualitative research annotations into structured, auditable knowledge.

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3%20%2B%20exception-blue.svg)](https://github.com/synesis-lang/synesis/blob/main/LICENSE)
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
    SC["🤖 synesis-coder\n(LLM-assisted annotation)\ngenerates full .syn with chains\nand codes per project template"]
    SYN["📄 .syn / .synt / .syno / .synp\n(Synesis source files)"]
    C["⚙️ Synesis Compiler\n(LALR parser · AST validator · exporters)"]:::core
    API["🐍 Python API\nsynesis.load() · to_dataframe()"]
    LSP["🧠 Synesis LSP\n(Language Server Protocol)"]
    EXT["🖥️ Synesis for VS Code\n(editor extension)"]
    JP["📓 Jupyter Notebook\n(data science · visualization)"]
    OUT["📊 Structured Outputs\nJSON · CSV · Excel · REFI-QDA"]
    GRAPH["🕸️ synesis-graph\nNeo4j / GraphQLite"]
    MCP["🤖 AI Agents\nMCP-compatible clients"]

    classDef core fill:#7c3aed,stroke:#4c1d95,color:#fff,font-weight:bold

    Z -->|"export highlights & tags\n(plain .syn, no chains)"| ZP
    ZP -->|raw annotations| SYN
    SYN -->|"human codes .syn\nwith chains + ontology codes"| EXT
    EXT -->|"template-aware\nannotation request"| SC
    SC -->|"fully coded .syn\n(chains · codes · fields)"| SYN
    SYN -->|parsed & validated| C
    C --> API
    C -->|AST + diagnostics| LSP
    LSP -->|JSON-RPC / stdio| EXT
    API -->|to_dataframe · to_json_dict| JP
    C -->|compile| OUT
    OUT -->|import| GRAPH
    GRAPH -->|graph queries| MCP
```

---

## Repositories

| Repository | Language | Role |
|---|---|---|
| [synesis](https://github.com/synesis-lang/synesis) | Python | Compiler, parser, validator, exporters, Python API |
| [synesis-lsp](https://github.com/synesis-lang/synesis-lsp) | Python | Language Server — diagnostics, hover, completion, semantic tokens |
| [synesis-vscode](https://github.com/synesis-lang/synesis-vscode) | JS/TS | VS Code extension — tree views, graph viewer, themes |
| [synesis-graph](https://github.com/synesis-lang/synesis-graph) | Python | Import compiled knowledge into Neo4j or GraphQLite; standalone HTML graph visualization |
| [synesis-coder](https://github.com/synesis-lang/synesis-coder) | Python | LLM-assisted annotation — abstract/document/ontology coding, critique, normalization, dataset generation, and more, conforming to the project template |
| [zotero-synesis-export](https://github.com/synesis-lang/zotero-synesis-export) | JavaScript | Zotero 7 plugin — exports PDF highlights and tags as plain `.syn` (no chains or ontology codes) |

---

## Potential Applications

| Domain | How Synesis helps |
|---|---|
| **Systematic literature reviews** | Annotate hundreds of papers with a shared template; export clean datasets for meta-analysis |
| **Grounded Theory / Thematic Analysis** | Build and validate code systems with ontological constraints; trace every code to its source |
| **Mixed-methods research** | Bridge qualitative interpretation with quantitative formats for R or Python workflows |
| **Knowledge graphs** | Compile research findings into Neo4j or GraphQLite; model causal chains as graph edges |
| **AI-augmented analysis** | Feed structured annotations as context to LLMs via MCP; responses traceable to source evidence |
| **Biblical / exegetical studies** | Code canonical texts with relational chains; integrate classical and patristic corpora |
| **Longitudinal projects** | Template versioning and strict validation prevent concept drift across research phases |

---

## Quick Start

```bash
pip install synesis synesis-lsp
```

Then install [Synesis for VS Code](https://github.com/synesis-lang/synesis-vscode/releases). Optionally, add the [Zotero plugin](https://github.com/synesis-lang/zotero-synesis-export/releases) to export PDF annotations directly to `.syn`, and `pip install synesis-graph` / `synesis-coder` for graph export and LLM-assisted annotation. Full documentation at **[synesis-lang.github.io](https://synesis-lang.github.io)**.

---

## License

The `synesis`, `synesis-lsp`, `synesis-graph`, and `synesis-coder` packages are
distributed under the **GNU Affero General Public License, version 3 only
(AGPL-3.0-only), with the Synesis Data-Output Exception** — your research data
and compiled outputs are never covered by the AGPL. `synesis-vscode` and
`zotero-synesis-export` remain **MIT**. See each repository's `LICENSE` for
details.

Interested in contributing? See the [Contributor License Agreement](https://github.com/synesis-lang/synesis/blob/main/CLA.md).

# 🧩 OWE Widget Definition Format

Welcome to the **Open Widget Ecosystem (OWE)** — the foundational specification for defining all widgets used within the Divizend Companion app and beyond.

This repository serves as the **single source of truth** for how widgets are described: including their metadata, required data sources, UI layout, and configuration. All widget definitions are plain JSON files that conform to a shared schema and are fully declarative, portable, and real-time-ready.

> ✅ This repository also contains **all widget definition files** for the widgets available in the **Divizend Companion** — available on both the [App Store](https://apps.apple.com) and [Google Play](https://play.google.com).

---

## 📜 Purpose

This repository defines:

- The **JSON schema** for widget definition files
- A set of **official widget definition files** available in the live Companion app
- Tooling to **validate** any widget definition against the schema

---

## 📂 Widget Definition File Format

Each widget is defined in a single `.json` file with the following top-level structure:

- `meta`: General metadata (name, title, version, author, tags, repository URL, etc.)
- `config`: User-configurable fields and options
- `data`: A GraphQL query definition specifying what data this widget needs
- `ui`: Declarative frontend layout split into:
  - `compact`: the home screen display
  - `expanded` (optional): a modal or dialog view when the widget is tapped

All files **must** conform to a central schema, which guarantees structural correctness, security, and interoperability.

---

## 📍 Schema Location

The canonical JSON Schema against which all widget definition files are validated is located at:

```
./schema/widget.schema.json
```

This schema is the authoritative contract for what a widget definition file must contain.

---

## 🗂 Widget Definitions

A growing collection of official widget definition files used by the Companion app is available in:

```
./examples/
```

Each file in this folder is a valid, tested, and minimal-to-complex example demonstrating how to define different widget types (e.g. financial, AI-powered, generative, multimedia).

---

## 🔢 Versioning

This repository — and each individual widget definition — adheres to **Semantic Versioning (SemVer)**:

- **MAJOR**: Breaking changes (incompatible schema updates)
- **MINOR**: Backward-compatible additions (new features, fields, UI types, etc.)
- **PATCH**: Backward-compatible fixes (typos, structural clarifications, test tweaks)

Each widget definition includes a `version` field in its `meta` section, which must follow SemVer to help track changes to individual widgets over time.

---

## ✅ Validation Tests

Every widget definition file in this repository is automatically validated against the shared schema to ensure correctness.

### 🔧 How to Run Tests

To validate all widget files:

1. Install dependencies:

```bash
pnpm install
```

2. Run the validation test suite:

```bash
pnpm test
```

This will:

- Traverse all `.json` files in `./examples/`
- Validate each against `./schema/widget.schema.json`
- Print human-readable results for schema conformity

Validation is implemented using [ajv](https://ajv.js.org/), the fast JSON Schema validator.

---

## 🤝 Contributing

This is an open-source, community-first specification. To contribute:

- Make sure your widget files conform to the schema
- Use the same structure and naming conventions
- Include your widget file in the `examples/` folder
- Update version numbers accordingly
- Ensure all tests pass before opening a PR

---

## 🧪 Testing Philosophy

This repository encourages test-driven development (TDD). All future enhancements to the widget schema must be accompanied by:

- Updated tests
- At least one new valid example in `examples/`
- Zero validation errors

---

## 🚀 Roadmap

- Add a CLI tool: `create-divizend-widget`
- Real-time playground: validate + preview widget JSON in-browser
- Visual schema explorer
- Built-in PNG renderer for social sharing

---

## 🛡 License

MIT © Divizend

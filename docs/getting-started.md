# Getting Started

This guide helps you run marocAffiliate documentation locally.

## Prerequisites

- Python 3.10+
- `pip`

## Install

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Start development server

```bash
mkdocs serve
```

Then open `http://127.0.0.1:8000`.

## Project structure

```text
marocAffiliate-docs/
├── docs/
│   ├── index.md
│   ├── getting-started.md
│   ├── architecture.md
│   ├── development.md
│   └── deployment.md
├── mkdocs.yml
└── requirements.txt
```

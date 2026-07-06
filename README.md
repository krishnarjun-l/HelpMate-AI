# HelpMate AI — Generative Search over Insurance Policy Documents

A **retrieval-augmented generative search system** that answers natural-language questions from insurance policy documents. It ingests long policy PDFs, retrieves the most relevant passages, and generates accurate, grounded answers.

This was a Generative AI project in a PG Data Science program.

## Overview

Insurance policy documents are long, dense, and hard to search. HelpMate AI builds a three-layer generative search pipeline over them:

1. **Embedding layer** — parse the policy PDFs (PyMuPDF / `fitz`), chunk the text, and build a searchable document index (LlamaIndex).
2. **Search & re-ranking layer** — retrieve candidate passages for a query and re-rank them for relevance.
3. **Generation layer** — an OpenAI model composes a final answer grounded in the retrieved passages, with the supporting evidence shown alongside.

## Data & configuration

The insurance policy PDFs are **not included** in this repository. Supply your own policy document(s) and point the ingestion step in the notebook at them.

**API key:** the notebook expects an OpenAI API key. In the original notebook this was read from a local `OPENAI_API_Key.txt` file. **Do not commit your API key.** Provide it via an environment variable instead, e.g.:

```bash
export OPENAI_API_KEY="your-key-here"
```

and read `os.environ["OPENAI_API_KEY"]` in the notebook. The `.gitignore` already excludes `OPENAI_API_Key.txt` and `.env` files as a safeguard.

## Repository structure

```
.
├── notebooks/
│   └── helpmate_ai.ipynb     # PDF ingestion, indexing, retrieval, re-ranking, generation
├── docs/
│   └── Documentation.pdf     # Project documentation
├── requirements.txt
└── README.md
```

## Getting started

1. Clone the repository and set up a virtual environment:

   ```bash
   git clone https://github.com/<your-username>/HelpMate-AI-Insurance-Search.git
   cd HelpMate-AI-Insurance-Search
   python3 -m venv .venv && source .venv/bin/activate
   pip install -r requirements.txt
   ```

2. Set your OpenAI API key as an environment variable (see above) and place your policy PDF(s) where the notebook expects them.

3. Run the notebook:

   ```bash
   jupyter notebook notebooks/helpmate_ai.ipynb
   ```

## Requirements

- Python 3.10+
- openai
- llama-index
- PyMuPDF (`fitz`)
- transformers, nltk, pandas, tabulate

See `requirements.txt`.

## Author

Krishnarjun Lakshminarayanan — PG Data Science, Generative AI project.

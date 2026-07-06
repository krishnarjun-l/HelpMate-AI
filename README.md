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

and read `os.environ["OPENAI_API_KEY"]` in the notebook. 

## Repository structure

```
.
├── HelpMateAIProject.ipynb 
├── Documentation-HelpMateAIProject.pdf 
├── requirements.txt
└── README.md
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

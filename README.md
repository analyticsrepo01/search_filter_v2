# Vertex AI Search Examples

This repository demonstrates how to leverage Vertex AI Search capabilities for building search applications:

## Overview

Vertex AI Search leverages decades of Google's expertise in information retrieval, combining:
- Deep information retrieval
- State-of-the-art natural language processing 
- Latest large language model (LLM) processing

The examples show three key approaches:

1. Using Vertex AI Search out-of-the-box capabilities via the Python API
2. Using Vertex AI Search Datastore as a Grounding Source with Gemini Models
3. Using Vertex AI Search with LangChain as a Retriever

## Features

- Integration with Vertex AI Search API
- Custom prompts and search specifications 
- Grounding with Gemini models
- LangChain integration for retrieval-augmented generation
- Support for filters and metadata
- Extractive answers and summaries

## Prerequisites

- Google Cloud project with Vertex AI API enabled
- Python 3.10+
- Required packages:
  - google-cloud-discoveryengine
  - langchain_google_community 
  - langchain
  - langchain-google-vertexai
  - google-cloud-aiplatform

## Setup

```bash
pip install --upgrade google-cloud-aiplatform
pip install google-cloud-discoveryengine langchain_google_community langchain langchain-google-vertexai
```

## Usage

See the Jupyter notebooks for detailed examples:

- `search_filters_metadata.ipynb` - Using filters and metadata
- `vertexai_search_Pru.ipynb` - Core search capabilities and integration examples
- `vertexai_search_options.ipynb` - Additional search options and configurations

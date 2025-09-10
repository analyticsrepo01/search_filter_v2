# Vertex AI Search with Filters & Metadata

A comprehensive collection of examples demonstrating advanced Vertex AI Search capabilities including filtering, metadata handling, query-level boosting, and facets.

## Author
**Saurabh**

## License
MIT License

## Overview

This repository demonstrates how to leverage Vertex AI Search capabilities for building sophisticated search applications with advanced filtering and metadata support. Vertex AI Search combines decades of Google's expertise in information retrieval with state-of-the-art natural language processing and large language model capabilities.

## Key Features

- **Metadata Filtering**: Filter search results based on structured metadata fields
- **Query-level Boosting**: Enhance search relevance with custom boosting strategies
- **Faceted Search**: Implement faceted navigation for better user experience
- **Advanced Search Options**: Configure extractive answers, summaries, and snippets
- **LangChain Integration**: Use Vertex AI Search as a retriever in RAG applications
- **Grounding with Gemini**: Integrate search results with Gemini models for enhanced responses

## Repository Structure

### Core Notebooks

1. **`search_filters_metadata.ipynb`**
   - Demonstrates how to use filters and metadata in search requests
   - Shows filtering by document ID, category, year, and other metadata fields
   - Includes both REST API and Python SDK examples
   - Perfect for understanding basic filtering concepts

2. **`query_level_boosting_filtering_and_facets.ipynb`**
   - Advanced query-level boosting techniques
   - Comprehensive filtering strategies
   - Faceted search implementation
   - Performance optimization techniques

### Sample Data

- **`alpha-metadata.json`**: Sample metadata file containing 176 Alphabet Inc. financial documents
  - Document structure includes:
    - `id`: Unique document identifier
    - `structData`: Metadata fields (title, year, quarter, category, tenant, description)
    - `content`: Document content information (mimeType, URI)
  - Ready for ingestion into Vertex AI Search datastores
  - Contains financial documents spanning 2004-2023

### Additional Resources

- `vertexai_search_options.ipynb`: Additional search configuration options
- `RAG_Crew.ipynb` & `RAG_Crew_VertexSearch.ipynb`: RAG implementation examples

## Prerequisites

- Google Cloud project with Vertex AI API enabled
- Python 3.10+
- Vertex AI Search datastore configured

## Setup

1. **Install required packages:**
```bash
pip install --upgrade google-cloud-aiplatform
pip install -U google-cloud-discoveryengine
pip install langchain_google_community langchain langchain-google-vertexai
```

2. **Configure your environment:**
```python
PROJECT_ID = "your-project-id"
LOCATION = "global"  # or your preferred location
DATA_STORE_ID = "your-datastore-id"
```

3. **Authenticate with Google Cloud:**
```python
from google.auth import default
creds, _ = default()
```

## Using the Alpha Metadata

The `alpha-metadata.json` file contains sample financial documents from Alphabet Inc. as example that can be used for testing and development:

### Data Ingestion

You can use this file to populate your Vertex AI Search datastore:

```bash
# Upload the metadata file to your datastore
# Follow Google Cloud documentation for bulk import procedures
```

### Sample Document Structure

```json
{
  "id": "doc-0",
  "structData": {
    "title": "2019Q2_alphabet_earnings_release.pdf",
    "description": "Alphabet Inc. financial document - 2019 Q2",
    "year": "2019",
    "quarter": "Q2",
    "category": "financial",
    "tenant": "alphabet"
  },
  "content": {
    "mimeType": "application/pdf",
    "uri": "gs://cloud-samples-data/gen-app-builder/search/alphabet-investor-pdfs/2019Q2_alphabet_earnings_release.pdf"
  }
}
```

### Available Filters

With this metadata, you can filter by:
- `year`: Document year (2004-2023)
- `quarter`: Financial quarter (Q1, Q2, Q3, Q4, Unknown)
- `category`: Document category (financial)
- `tenant`: Organization (alphabet)
- `id`: Specific document IDs

## Quick Start Examples

### Basic Filtering

```python
# Filter by specific document ID
filter_str = 'id: ANY("doc-25")'

# Filter by year
filter_str = 'year: ANY("2019")'

# Multiple filters
filter_str = 'year: ANY("2019") AND quarter: ANY("Q2")'
```

### Using with LangChain

```python
from langchain_google_community import VertexAISearchRetriever

retriever = VertexAISearchRetriever(
    project_id=PROJECT_ID,
    location_id=LOCATION,
    data_store_id=DATA_STORE_ID,
    max_documents=10,
    get_extractive_answers=True
)
```

## Notebooks Overview

### 1. Search Filters & Metadata (`search_filters_metadata.ipynb`)

**Objective**: Learn how to use filters and metadata in Vertex AI Search

**Key Topics**:
- REST API filtering examples
- Python SDK implementation
- Single and multiple metadata filters
- LangChain integration

**Use Cases**:
- Filtering financial documents by year
- Restricting search to specific document categories
- Combining multiple filter criteria

### 2. Query-Level Boosting & Facets (`query_level_boosting_filtering_and_facets.ipynb`)

**Objective**: Advanced search techniques and performance optimization

**Key Topics**:
- Query-level boosting strategies
- Faceted search implementation
- Advanced filtering techniques
- Performance optimization

**Use Cases**:
- Enhancing search relevance
- Building faceted navigation
- Custom ranking and boosting

## Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

## Support

For questions about Vertex AI Search, refer to the [official documentation](https://cloud.google.com/generative-ai-app-builder/docs/introduction).

---

*This repository provides practical examples for implementing enterprise-grade search solutions using Google Cloud's Vertex AI Search capabilities.*
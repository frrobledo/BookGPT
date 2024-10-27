# Ask a Book Questions

This project implements a document question-answering system that allows users to ask questions about the content of PDF documents. The system uses LangChain, OpenAI embeddings, and Pinecone vector database to enable semantic search and intelligent responses.

## Features

- PDF document loading and processing
- Text chunking for efficient processing
- Semantic search capabilities
- Question-answering using GPT-3.5 Turbo
- Vector storage using Pinecone
- Support for both local and online PDF files

## Prerequisites

- Python 3.8+
- OpenAI API key
- Pinecone API key and environment
- Required Python packages (see Requirements section)

## Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd <repository-name>
```

2. Install the required packages:
```bash
pip install langchain openai pinecone-client unstructured pyyaml
```

3. Create a `config.yaml` file in the root directory with your API credentials:
```yaml
openai_key: "your-openai-api-key"
pinecone_key: "your-pinecone-api-key"
pinecone_env: "your-pinecone-environment"
index_name: "your-pinecone-index-name"
```

## Usage

1. Place your PDF document in the `data/` directory or use an online PDF URL

2. Run the Jupyter notebook:
```bash
jupyter notebook "Ask A Book Questions.ipynb"
```

3. Follow the notebook cells to:
   - Load and process your PDF document
   - Create text chunks
   - Generate embeddings
   - Store vectors in Pinecone
   - Ask questions about your document

## How It Works

1. **Document Loading**: The system uses UnstructuredPDFLoader to load PDF documents, supporting both local and online PDFs.

2. **Text Processing**: The document is split into smaller chunks using RecursiveCharacterTextSplitter for more efficient processing.

3. **Embedding Generation**: OpenAI's embedding model converts text chunks into vector representations.

4. **Vector Storage**: Embeddings are stored in a Pinecone vector database for efficient similarity search.

5. **Question Answering**: When a question is asked, the system:
   - Finds relevant text chunks using semantic search
   - Passes these chunks and the question to GPT-3.5 Turbo
   - Returns a coherent answer based on the document content

## Configuration

Key configuration parameters in the notebook:
- `chunk_size`: Size of text chunks (default: 1000 characters)
- `chunk_overlap`: Overlap between chunks (default: 0 characters)
- `temperature`: Controls randomness in GPT-3.5 responses (default: 0)
- `max_tokens`: Maximum length of generated responses (default: 2104)

## Example

```python
query = "Enumerate all that is said about monotonicity in this paper"
docs = docsearch.similarity_search(query, include_metadata=True)
chain.run(input_documents=docs, question=query)
```

## Dependencies

- langchain
- openai
- pinecone-client
- unstructured
- pyyaml
- jupyter

## Security Notes

- Keep your `config.yaml` file secure and never commit it to version control
- Add `config.yaml` to your `.gitignore` file
- Monitor your API usage to manage costs

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.


## Acknowledgments

- LangChain for the document processing framework
- OpenAI for embeddings and language model
- Pinecone for vector storage capabilities
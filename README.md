# UdaPlay - AI Game Research Agent

An intelligent AI-powered research agent for the video game industry that combines offline knowledge retrieval with real-time web search capabilities.

## Project Overview

UdaPlay demonstrates the development of a sophisticated agentic AI system for video game research. The project is split into two main components:

### Part 1: Offline RAG (Retrieval-Augmented Generation)
Build a Vector Database using ChromaDB to efficiently store and retrieve video game information from a curated dataset of 20 games.

**Key Components:**
- ChromaDB persistent vector database
- Embedding-based document retrieval
- Game metadata indexing (Name, Platform, Genre, Publisher, Description, Release Year)

### Part 2: AI Agent Development
Create an intelligent agent that leverages both local knowledge and web search to answer complex questions about video games.

**Agent Capabilities:**
- Query local game database with semantic search
- Perform web searches for current information
- Maintain conversation state and memory
- Return structured, contextual answers (JSON + natural language)
- Learn and store useful information for future queries via long-term memory
- Analyze public sentiment about games from web reviews
- Detect currently trending games by category

## Getting Started

### Prerequisites

- Python 3.11 or higher
- pip (Python package manager)
- An OpenAI API key
- A Tavily API key for web search

### Installation

1. **Clone or download the project**
2. **Install dependencies**
   ```bash
   pip install -r starter/requirement.txt
   ```

3. **Configure environment variables**
   
   Create a `config.env` file in the `starter/` directory with your API keys:
   ```dotenv
   OPENAI_API_KEY="your-key-here"
   OPENAI_BASE_URL="https://openai.vocareum.com/v1"
   CHROMA_OPENAI_API_KEY="your-key-here"
   TAVILY_API_KEY="your-key-here"
   ```

### Project Structure

```
project/
├── README.md                          # Project documentation
├── starter/
│   ├── README.md                      # Detailed project instructions
│   ├── config.env                     # Environment configuration template
│   ├── requirement.txt                # Python dependencies
│   ├── Udaplay_01_starter_project.ipynb          # Part 1: RAG setup
│   ├── Udaplay_02_starter_project.ipynb          # Part 2: Agent development
│   ├── Udaplay_02_solution_project.ipynb         # Reference solution
│   ├── chromadb/                      # Persistent vector database
│   │   └── chroma.sqlite3
│   └── games/                         # Game dataset (20 JSON files)
│       ├── 001.json - 020.json        # Game metadata files
└── lib/                               # Core library modules
    ├── __init__.py
    ├── agents.py                      # Agentic AI implementation
    ├── documents.py                   # Document processing utilities
    ├── evaluation.py                  # Evaluation and scoring functions
    ├── llm.py                         # Language model interactions
    ├── loaders.py                     # Data loading utilities
    ├── memory.py                      # Conversation memory management
    ├── messages.py                    # Message formatting and handling
    ├── parsers.py                     # Output parsing utilities
    ├── rag.py                         # RAG implementation
    ├── state_machine.py               # Agent state management
    ├── tooling.py                     # Tool definitions and helpers
    └── vector_db.py                   # Vector database operations
```

## Key Components

### Library Modules (`lib/`)

- **agents.py**: Core agent logic for decision-making and action planning
- **vector_db.py**: ChromaDB integration for semantic search
- **rag.py**: Retrieval-augmented generation pipeline
- **llm.py**: OpenAI API interactions and model management
- **memory.py**: Session memory and conversation context
- **tooling.py**: Tool definitions and helpers
- **7 Agent Tools**: `retrieve_game`, `evaluate_retrieval`, `game_web_search`, `analyze_game_sentiment`, `detect_trending_games`, `remember_fact`, `recall_memory`
- **documents.py**: Document processing and formatting
- **parsers.py**: Response parsing and structuring
- **evaluation.py**: Quality metrics and result evaluation
- **loaders.py**: Game data loading from JSON
- **messages.py**: Message formatting for agent communication
- **state_machine.py**: Agent state transitions and workflow

### Game Dataset

The `games/` directory contains 20 JSON files with comprehensive video game information including title, platform, genre, publisher, and description.

## Project Deliverables

### Part 1: Vector Database & RAG
- Set up ChromaDB client with persistent storage
- Create embeddings for game documents
- Implement semantic search functionality
- Build basic retrieval pipeline

### Part 2: Agentic AI System
- Implement 7 agent tools:
  - `retrieve_game`: Query vector database for game information
  - `evaluate_retrieval`: Assess quality of retrieved documents
  - `game_web_search`: Search the web when internal knowledge is insufficient
  - `analyze_game_sentiment`: Analyze public sentiment from game reviews and news
  - `detect_trending_games`: Detect trending games by category (RPG, indie, PS5, etc.)
  - `remember_fact`: Store key facts into long-term memory for future retrieval
  - `recall_memory`: Search long-term memory for previously learned facts
- Build agent decision logic using GPT models
- Implement long-term memory with ChromaDB-backed storage
- Create structured output formatting (Pydantic models with JSON output)

## Dependencies

```
chromadb>=1.0.4
matplotlib>=3.9.0
openai>=1.73.0
pdfplumber>=0.11.0
pydantic>=2.11.3
pydantic-settings>=2.13.0
python-dotenv>=1.1.0
tavily-python>=0.5.4
```

## Built With

* [OpenAI API](https://openai.com/) - Language model and embeddings
* [ChromaDB](https://www.trychroma.com/) - Vector database
* [Tavily API](https://tavily.com/) - Web search capability
* [Pydantic](https://docs.pydantic.dev/) - Data validation
* [python-dotenv](https://github.com/theskumar/python-dotenv) - Environment management

## License

[License](../LICENSE.md)

# Python Agents

A comprehensive collection of Python agent implementations using LangChain and Cloudflare Workers AI.

## 🚀 Overview

This repository demonstrates various AI agent patterns and implementations, including:
- Basic LLM interactions with Cloudflare Workers AI
- Prompt chaining and structured output
- Custom tool creation and binding
- ReAct agents for multi-step reasoning
- Document search and editing capabilities
- Integration with external APIs (DuckDuckGo search)

## 📁 Project Structure

```
python-agents/
├── docs/                           # Documentation files for agent testing
│   ├── climate.txt                 # Climate change documentation
│   ├── python.txt                  # Python programming documentation
│   ├── sample.txt                  # Sample document
│   ├── travel.txt                  # Travel documentation
│   ├── windows1.txt                # Windows OS documentation
│   └── windows2.txt                # Windows installation documentation
├── langchain_agent.ipynb          # Main Jupyter notebook with agent examples
├── requirements.txt                # Python dependencies
└── README.md                       # This file
```

## 🛠️ Setup

### Prerequisites
- Python 3.11+
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/KRNK97/Python-Agents.git
   cd Python-Agents
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv env
   source env/bin/activate  # On Windows: env\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   Create a `.env` file in the project root:
   ```env
   CF_AI_API_KEY=your_cloudflare_api_key_here
   CF_ACCOUNT_ID=your_cloudflare_account_id_here
   OPENAI_API_KEY=your_openai_api_key_here  # Optional
   ANTHROPIC_API_KEY=your_anthropic_api_key_here  # Optional
   ```

## 📚 Usage

### Running the Notebooks

1. **Start Jupyter Notebook**
   ```bash
   jupyter notebook
   ```

2. **Open the notebook**
   - `langchain_agent.ipynb` - Complete agent implementation with examples

### Key Features Demonstrated

#### 1. Basic LLM Usage
```python
from langchain_cloudflare import ChatCloudflareWorkersAI

llm = ChatCloudflareWorkersAI(
    api_token=cf_api_token,
    model="@cf/meta/llama-2-7b-chat-int8",
)
```

#### 2. Structured Output
```python
json_schema = {
    "title": "joke",
    "type": "object",
    "properties": {
        "setup": {"type": "string"},
        "punchline": {"type": "string"},
        "rating": {"type": "integer", "minimum": 1, "maximum": 10}
    }
}

structured_llm = llm.with_structured_output(json_schema)
```

#### 3. Custom Tools
```python
@tool
def search_text_file(query: str) -> str:
    """Search for a text file using semantic similarity."""
    # Implementation details in the notebook
```

#### 4. ReAct Agents
```python
from langgraph.prebuilt import create_react_agent

agent = create_react_agent(llm, [search_text_file, edit_text_file])
result = agent.invoke({"messages": [{"role": "user", "content": query}]})
```

## 🔧 Dependencies

### Dependencies (from requirements.txt)
- `python-dotenv` - Environment variable management
- `langchain` - Core LangChain framework
- `langchain-cloudflare` - Cloudflare Workers AI integration
- `sentence_transformers` - Text embeddings for semantic search
- `langgraph` - Agent workflow framework

## 🌟 Features

- **Multi-Model Support**: Works with various Cloudflare Workers AI models
- **Semantic Search**: Document search using embeddings
- **File Operations**: Read, search, and edit text files
- **Web Search**: Integration with DuckDuckGo for real-time information
- **Structured Output**: JSON schema-based response formatting
- **Agent Workflows**: Multi-step reasoning and action planning

## 📖 Documentation

The `docs/` folder contains 6 sample text documents that demonstrate the agent's document search and editing capabilities:

- **climate.txt** - Climate change and environmental topics
- **python.txt** - Python programming information
- **sample.txt** - General sample content
- **travel.txt** - Travel and tourism information
- **windows1.txt** - Windows operating system basics
- **windows2.txt** - Windows installation procedures

These files are used in the `langchain_agent.ipynb` notebook to demonstrate how agents can:
- Search for relevant documents using semantic similarity
- Extract and modify content from documents
- Combine multiple tools for complex tasks

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🔗 Links

- **Repository**: [https://github.com/KRNK97/Python-Agents](https://github.com/KRNK97/Python-Agents)
- **LangChain Documentation**: [https://python.langchain.com/](https://python.langchain.com/)
- **Cloudflare Workers AI**: [https://developers.cloudflare.com/workers-ai/](https://developers.cloudflare.com/workers-ai/)

## 📞 Support

If you have any questions or need help, please:
1. Check the [Issues](https://github.com/KRNK97/Python-Agents/issues) page
2. Create a new issue if your question isn't already answered
3. Fork and submit a pull request for any improvements

---

**Happy Coding! 🚀**

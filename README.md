# Dual-Personality Chatbot with LangGraph

A simple yet powerful demonstration of using **LangGraph** to build a stateful, multi-agent chatbot that automatically routes user messages to either:

- An **empathetic therapist agent** (for emotional support & feelings), or  
- A **logical & factual assistant** (for information, analysis & problem-solving)

The routing decision is made by a lightweight classifier agent that analyzes the user's last message.

Powered by **Llama 3.2** running locally via **Ollama**.

## Features

- Automatic classification of user input as **emotional** or **logical**
- Conditional routing using LangGraph
- Two distinct agent personalities with different system prompts
- Conversation history maintained via state
- Simple terminal-based chat interface
- Easy to run locally with Ollama

## Project Structure

```
.
├── requirements.txt       # Python dependencies
├── single_node.py         # Basic single-agent chatbot (starting point)
└── dual_node.py           # Main dual-personality router + agents implementation
```

## Requirements

- Python 3.10+
- [Ollama](https://ollama.com/) installed and running
- Model: `llama3.2:latest` (pulled via Ollama)

## Installation

1. Clone the repository

```bash
git clone https://github.com/Bilal11123/Dual-Personality-Chatbot-with-LangGraph.git
cd Dual-Personality-Chatbot-with-LangGraph
```

2. Install dependencies

```bash
pip install -r requirements.txt
```

(Or use uv / poetry / pipx if you prefer)

3. Make sure Ollama is running and the model is available

```bash
ollama pull llama3.2:latest
ollama run llama3.2:latest   # optional – just to verify
```

## Usage

Run the dual-personality chatbot:

```bash
python dual_node.py
```

### Example Interaction

```
----------------------------------------
Enter a message (enter q to exit): I'm feeling really lost and overwhelmed lately...

Assistant: I’m really sorry you’re going through this. It sounds incredibly heavy to feel so lost and overwhelmed. Would you like to share a bit more about what’s been weighing on you? I’m here to listen, without judgment.

----------------------------------------
Enter a message (enter q to exit): What's the capital of France?

Assistant: The capital of France is Paris.
```

## How It Works

1. **Classifier** → analyzes the last user message and decides: `"emotional"` or `"logical"`
2. **Router** → reads the classification and sets the next node
3. **Therapist agent** → uses an empathetic, validation-focused prompt
4. **Logical agent** → gives concise, fact-based answers only
5. Output → returned to the user in the terminal

All agents use the same underlying `llama3.2` model via LangChain + Ollama.

## Files Explained

- **`single_node.py`**  
  Basic LangGraph example with one chatbot node — good for learning the basics

- **`dual_node.py`**  
  Full implementation with classification + conditional routing + two personalities

## Customization Ideas

- Change the model (`llama3.1:8b`, `mistral`, `phi3.5`, etc.)
- Add more personalities (e.g. sarcastic, motivational, technical writer)
- Improve classification with few-shot examples
- Add tool calling / memory persistence
- Build a Streamlit / Gradio / FastAPI frontend

## Dependencies (requirements.txt)

```text
python-dotenv
langgraph
langchain[anthropic]          # actually only using langchain-core + ollama integration
ipykernel                     # optional – for notebooks
```

> Note: you can remove `langchain[anthropic]` if you're only using Ollama/local models.

## License

MIT

---

Feel free to experiment, break things, and turn this into your own multi-agent playground!  
Happy hacking! 🦙

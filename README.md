# LangGraph Learning Journey
[![Ask DeepWiki](https://devin.ai/assets/askdeepwiki.png)](https://deepwiki.com/kalp12/langraph-learning)

This repository is a practical guide to learning LangGraph, a library for building stateful, multi-actor applications with LLMs. Through a series of focused examples, you'll learn how to construct and run computation graphs for creating robust and complex AI agents. 

The examples cover fundamental concepts such as creating state graphs, adding conditional logic, integrating tools, managing memory, implementing observability with LangSmith, and building human-in-the-loop workflows.

## Key Concepts Covered

*   **Simple Graph Creation**: Building a basic `StateGraph` with nodes and edges.
*   **Conditional Edges**: Routing the graph's flow based on the current state.
*   **Chatbot Implementation**: Creating a basic conversational agent that maintains message history.
*   **Tool Calling**: Equipping an agent with external tools and enabling it to decide when to use them.
*   **Agentic Behavior**: Creating loops in the graph to allow the agent to use tools and then reason about the output.
*   **Persistent Memory**: Using `MemorySaver` to maintain conversation state across multiple turns and for different users.
*   **LangSmith Tracing**: Integrating with LangSmith for observability, debugging, and monitoring of graph executions.
*   **Human-in-the-Loop (HITL)**: Pausing a graph's execution to wait for human input before proceeding.

## Repository Contents

This repository contains a series of Jupyter notebooks and a Python script, each demonstrating a specific LangGraph feature:

*   `1_simple_graph.ipynb`: Introduces the fundamentals of creating a state graph with nodes and a defined state.
*   `2_graph_with_condition.ipynb`: Demonstrates how to use conditional edges to route the graph's logic based on the current state.
*   `3_chatbot.ipynb`: Implements a simple conversational chatbot, showing how to manage and append to a list of messages.
*   `4_tool_call.ipynb`: Illustrates how an LLM can call external tools like `get_stock_price`.
*   `5_tool_call_agent.ipynb`: Builds on the previous example to create a more robust agent that can loop back to a reasoning step after using a tool, enabling multi-step tool use.
*   `6_memory.ipynb`: Implements persistent, multi-threaded conversation memory using `MemorySaver` to handle separate, stateful conversations.
*   `7_langsmith_tracing.ipynb`: Shows how to trace graph execution with LangSmith for enhanced debugging and monitoring.
*   `8_hitl.py`: Provides an example of a Human-in-the-Loop workflow, where the graph pauses to ask for human approval before proceeding with an action like buying a stock.

## Getting Started

Follow these steps to set up your local environment and run the examples.

### 1. Clone the Repository
```bash
git clone https://github.com/kalp12/langraph-learning.git
cd langraph-learning
```

### 2. Set Up Environment Variables
Create a `.env` file by copying the `sample.env` file. This file is used to store your API keys securely.
```bash
cp sample.env .env
```
Open the `.env` file and add your API keys for Google GenAI and LangSmith.

```dotenv
GOOGLE_API_KEY=<your google api key>
OPENAI_API_KEY=<your open ai key>
LANGSMITH_API_KEY=<langsmith project key>
LANGSMITH_TRACING=true
LANGSMITH_ENDPOINT="https://api.smith.langchain.com"
LANGSMITH_PROJECT="langgraph-learning"
```

### 3. Install Dependencies
This project uses `uv` for fast dependency management. If you don't have `uv` installed, you can install it via pip:
```bash
pip install uv
```
Once `uv` is installed, create a virtual environment and sync the dependencies from the `uv.lock` file:
```bash
# Create a virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows, use `.venv\Scripts\activate`

# Sync dependencies
uv pip sync
```

## Usage

You can run the examples as either Jupyter Notebooks or as a standalone Python script.

### Running Jupyter Notebooks
To explore the `.ipynb` examples, start the Jupyter Notebook server:
```bash
jupyter notebook
```
This will open a new tab in your browser. From there, you can navigate to and run any of the notebooks (`1_simple_graph.ipynb`, `2_graph_with_condition.ipynb`, etc.) to see them in action.

### Running the Python Script
To run the Human-in-the-Loop (HITL) example, execute the `8_hitl.py` script directly from your terminal:
```bash
python 8_hitl.py
```
This script is interactive and will prompt you for input in the terminal to either approve or reject a transaction.

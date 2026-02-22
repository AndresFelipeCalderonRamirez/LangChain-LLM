# LangChain-LLM

## Project Architecture and Components

## Project Context

This project demonstrates how to build an AI Agent using LangChain, LangGraph, and Google Gemini. Unlike a simple prompt-response interaction, this system allows the model to use tools, maintain conversational memory, access structured runtime context, and produce structured outputs. The goal is to show how modern LLM agents can reason, call tools dynamically, maintain state across conversations, and generate controlled outputs in a scalable and modular way.

---

## Overview

This project implements an AI Agent system using:

- LangChain for agent creation and orchestration  
- LangGraph for memory and state management  
- Google Gemini as the Large Language Model  
- Custom tools for weather and user location  
- Structured output formatting  
- Runtime context injection  

The agent can:

- Call tools dynamically  
- Retrieve user-specific context  
- Maintain memory across interactions  
- Generate structured responses  

---

## Architecture

```
User Message
     ↓
Agent (Gemini Model)
     ↓
Reasoning + Tool Selection
     ↓
Tool Execution (Weather / Location)
     ↓
Structured Output
     ↓
Memory Checkpoint (LangGraph)
     ↓
Final Response
```
## Components Explained

### 1. Environment Configuration
Tool: python-dotenv  
Purpose: Load API keys securely from a `.env` file.  
Why: Keeps credentials out of source code and follows security best practices.

---

### 2. Language Model (LLM)
Model: gemini-2.5-flash-lite  
Purpose: Core reasoning engine of the agent.  
Why:
- Fast and efficient.
- Suitable for agent workflows.
- Adjustable temperature for response creativity.

---

### 3. Basic Tool (Initial Example)
Function: `get_weather(city: str)`  
Purpose: Simulates a weather API.  
Why: Demonstrates how agents can call external functions.

---

### 4. System Prompt
Purpose: Defines agent behavior and personality.  
Why:
- Controls reasoning style.
- Defines tool usage rules.
- Guides decision-making logic.

In this case, the agent:
- Speaks in puns.
- Uses tools intelligently.
- Determines whether to infer or retrieve user location.

---

### 5. Custom Tools

#### get_weather_for_location
Purpose: Returns weather information for a specific city.  
Why: Demonstrates structured tool usage.

#### get_user_location
Purpose: Retrieves the user's location using runtime context.  
Why:
- Shows contextual tool execution.
- Demonstrates dependency on runtime data.

---

### 6. Context Schema

Dataclass: `Context`  
Purpose: Defines structured runtime data (e.g., `user_id`).  
Why:
- Enables personalized tool execution.
- Keeps logic clean and type-safe.

---

### 7. Structured Response Format

Dataclass: `ResponseFormat`  

Fields:
- `punny_response`
- `weather_conditions`

Purpose: Enforces structured output.  
Why:
- Ensures predictable responses.
- Useful for APIs and production systems.
- Improves reliability over raw text output.

---

### 8. Memory (LangGraph)

Tool: `InMemorySaver`  

Purpose: Stores conversation state using thread IDs.  
Why:
- Maintains context across multiple messages.
- Enables multi-turn conversations.
- Demonstrates agent memory capabilities.

---

### 9. Agent Creation

Tool: `create_agent`  

Configured with:
- Model
- System prompt
- Tools
- Context schema
- Structured output strategy
- Memory checkpointer

Purpose: Combines all components into a working agent system.

---

### 10. Agent Execution

The agent is executed with:

- `messages`
- `config` (thread ID)
- `context` (user_id)

Why:
- `thread_id` enables memory persistence.
- `context` allows personalized tool calls.

---

### 11. Memory Test

A second invocation confirms that:

- The agent remembers the conversation.
- The thread state persists.
- Structured responses remain consistent.


---
# Installation and Execution Guide

## 1. Clone the Repository

```bash
git clone <your-repository-url>
cd <repository-folder>
```

---

## 2. Install Dependencies

```bash
pip install langchain \
            langgraph \
            langchain-google-genai \
            python-dotenv
```

---
## 4. Run the Notebook or Script
Then open the notebook and run all cells sequentially.
# Technologies Used

- LangChain – Agent creation and orchestration framework.  
- LangGraph – State management and memory handling for agents.  
- Google Gemini (via langchain-google-genai) – Provides the LLM used for reasoning and generation.  
- Python-dotenv – Secure environment variable management.  
- Python 3.x – Core programming language.  
- Jupyter Notebook (optional) – Interactive execution environment.  

---

# Structure

```
C:.
│   .env
│   .gitignore
│   LANG.ipynb
│   README.md
```
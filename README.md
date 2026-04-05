# Using Prompts and Agents in LangChain

This notebook demonstrates how to build LLM-powered pipelines using LangChain and Claude (Anthropic).

## Tasks Overview

**Task 1 — Basic LLM Call**
Simple prompt to get a structured explanation of a topic (Quantum Computing) with a response length limit.

**Task 2 — Parameterized Prompt Template**
Using `PromptTemplate` to dynamically pass topics to the model. Tested on Bayesian Methods, Transformers, and Explainable AI.

**Task 3 — ReAct Agent for Scientific Publications**
A ReAct-type agent with Tavily search that automatically finds 5 recent AI research papers, returning title, authors, and description for each.

**Task 4 — Business Analytics Agent**
An agent combining web search (Tavily) and Python execution (PythonREPLTool) to generate a sales forecast for a Brazilian orange exporter, incorporating real-time weather data, inflation rates, and global demand trends.

## Tools & Libraries
- `langchain`, `langchain-anthropic`, `langchain-tavily`
- `langchain-experimental` (PythonREPLTool)
- `Claude Sonnet` (Anthropic API)
- `scipy`, `numpy`, `pandas`, `matplotlib`

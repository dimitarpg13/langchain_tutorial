# Intro to LangChain, LangSmith, and LangGraph

## LangChain vs LangGraph

LangChain and LangGraph are both frameworks for building applications with Large Language Models (LLMs), but they differ in their approach to structuring and managing workflows. LangChain is designed for linear, sequential workflows, while LangGraph is geared towards complex, stateful, multi-agent workflows with loops and branching. 

**Key differences**:
LangChain uses a chain structure (DAG), suitable for linear processes like _retrieve-summarize-answer_. LangGraph uses a graph structure, allowing for loops, branching, and revisiting previous states, making it better for interactive systems and complex decision-making. 

**State Management**:
LangChain's state managmenet is less roboust than LangGraph's. While it can pass information through chains, it does not easily maintain persistent state across multiple runs. LangGraph has built-in state management, enabling nodes to access and modify shared state, making it suitable for applications needing context and memory. 



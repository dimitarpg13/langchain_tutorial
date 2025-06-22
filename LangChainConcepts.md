## LangChain Concepts

### Conceptual Gide

#### Architecture

LangChain as a framework consists of a number of package.

`langchain-core`
This package contains base abstractions of different components and ways to compose them together. The interfaces for core components like LLMs, vector stores, retrievers, and more are defined here. No third party integrations are defined here. The dependencies are kept purposefully very lightweight.

`langchain`

The main `lnagchain` package contains chains, agents, and retrieval strategies that make up an application's cognitive architecture. 

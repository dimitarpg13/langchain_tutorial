# LangChain Use Cases


## Summarization

**Use Case Description**
Suppose you have a set of documents (PDF's, `Notion` document pages, customer questions, etc.) and you want to summarize the content.

![Figure: summarization use case](images/summarization_use_case_1.png)


<ins>Question:</ins>

How to pass the documents to be summarized to the LLM's context window?
Two comon approaches:

1. The _Stuff All Together_ approach: put all documents in a single prompt. This is the simplest approach but it comes with shortcomings.

2. The _Map-Reduce_ approach: summarize each document separately in a "map"
 step and then "reduce" the summaries into a final summary.

![Figure: summarization example 1](images/summarization_use_case_2.png)

Before anything install packages and set environmental variables

```jupyter
%pip install --upgrade --quiet langchain-openai tiktoken chromadb langchain langchainhub

import dotenv
dotenv.load_dotenv()
```


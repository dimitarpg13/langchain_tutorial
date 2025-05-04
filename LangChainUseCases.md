# LangChain Use Cases

## Some Preliminaries

### LangChain Expression Language (LCEL)

LangChain Expression Language (LCEL) is a declarative way to easily compose chains together. LCEL was designed to support putting prototypes in production , with no code changes. LCEL can be used from the simplest "prompt + LLM" chain to the most complex chains having hundreds of steps. 

**Benefits of using LCEL**

* Streaming support : 

## Summarization

**Use Case Description**
Suppose you have a set of documents (PDF's, `Notion` document pages, customer questions, etc.) and you want to summarize the content.

![Figure: summarization use case](images/summarization_use_case_1.png)


<ins>Question:</ins>

How to pass the documents to be summarized to the LLM's context window?
Two comon approaches:

1. Put all documents in a single prompt. This is the simplest approach but it comes with shortcomings.

2. 

![Figure: summarization example 1](images/summarization_use_case_2.png)

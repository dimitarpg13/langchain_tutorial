# LangChain Use Cases

## Some Preliminaries

### LangChain Expression Language (LCEL)

LangChain Expression Language (LCEL) is a declarative way to easily compose chains together. LCEL was designed to support putting prototypes in production , with no code changes. LCEL can be used from the simplest "prompt + LLM" chain to the most complex chains having hundreds of steps. 

**Benefits of using LCEL**

* _Streaming support_ :  short time-to-first-token, that is time elapsed until the first chink of output comes out, is acichieved with LCEL chains.
  this means that the parser output from the streamed tokens from LLM to a streaming output parser is produced with the same rate as the LLM provider raw token output.

* _Async support_ : An LCEL chain can be called with both the synchronouus API (e.g. in Jupyter notebook while prototyping) as well as with asyncrhonous API (e.g. in a `LangServe` server); The same code can be used both for prototyping (syncrhonously) and in production (asynchronously) with server-level concurrency implemented in both cases. 

* _Optimized parallel execution_ : Whenever LCEL chains have steps that can be executed in parallel  e.g. if you fetch documents from multiple retrievers, parallel execution is implemented whenever it makes sense and it is optimized for minimal latency.

* _Retries and fallbacks_ : can be configured for any part of the LCEL chain.

* _Access intermediate result_ : for more complex chains it is often very useful to access the results from intermediate steps even before the final output is produced. This is useful for debugging or even presenting the end-users with more detailed step-level intermediate info.  

* _Input and output schemas_ : Input and output schemas give every LCEL chain Pydantic and JSONSChema schemas inferred from the structure of the chain.

* _LangSmith integration and tracing_ : with LCEL, all steps are automatically logged to `LangSmith` for maximum observability and ease of debugging

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

# LangChain Expression Language

*LangChain Expression Language* or *LCEL*, is a declarative way to chain LangChain components. LCEL was designed to support putting prototypes in production, with no code changes from the simplest "prompt + LLM" chain to the most complex chains. Complex chains can have hundreds of steps. Here are the reasons one would want to use LCEL:

* **First-class streaming support**:  when building chains with LCEL, we get the best possible time-to-first-token which is the time elapsed until the first chunk of output comes out. For some chains this means we stream tokens straight from an LLM to a streaming output parser, and we get back parsed, incremental chunks of output at the same rate as the LLM provider outputs the raw tokens.

* **async support**: any chain built with LCEL can be called both with the synchronous API (e.g. in Jupyter notebook while prototyping) as well as with the asynchronous API (e.g. in a LangServe server). The asynchronous API is obviously beneficial for achieving high throughputs by handling concurrent requests at scale on the server side.

* **optimized parallel execution**: whenever the LCEL chains have steps that can be executed in parallel (e.g. when documents are fetched from multiple retrievers) it is done automatically both in the sync and async interfaces for the smallest possible latency.

* **retries and fallbacks**: retries and fallbacks can be configured for any part of the LCEL chain. In this way chains are made more reliable at scale. Streaming support for retries and fallbacks is being added which will minimize the latency.

* **access intermediate results**: for more complex chains it is often very useful to access the results of intermediate steps even before the final output is produced. This can be used to let end-users know something is happening, or even just to debug your chain. Intermediate results are available for streaming on the server side in LangServe server instance.

* **input and output schemas**: input and output schemas give every LCEL chain Pydantic and JSONSchema schemas inferred from the structure of the chain. This can be used for validation of inputs and outputs, and is an integral part of LangServe.

* **integrated LangSmith tracing**: as the chains get more complex, it becomes important to understand what is happening at every step. With LCEL, all steps are automatically logged to LangSmith for observability and debuggability.

## Runnable interface

Creating custom chains is facilitated by implementing the [Runnable protocol](https://python.langchain.com/v0.2/api_reference/core/runnables/langchain_core.runnables.base.Runnable.html#langchain_core.runnables.base.Runnable). Many LangChain components implement the Runnable protocol, including the chat models, LLMs, output parsers, retrievers, prompt templates, etc. Some of the primitives for working with runnables are discussed later.

`Runnable` is a standard interface for defining and invoking custom chains:

* `stream`: stream back chunks of the response
* `invoke`: call the chain on an input
* `batch`: call the chain on a list of inputs

These also have corresponding async methods that should be used with [asyncio](https://docs.python.org/3/library/asyncio.html) `await` syntax for concurrency:

* `astream`: stream back chunks of the response async
* `ainvoke`: call the chain on an input async
* `abatch`: call the chain on a list of inputs async
* `astream_log`: stream back intermediate steps as they happen, in addition to the final response
* `astream_events`: (**beta**) stream events as they happen in the chain (introduced in `langchain-core` `0.1.14`)



# LangChain Expression Language

*LangChain Expression Language* or *LCEL*, is a declarative way to chain LangChain components. LCEL was designed to support putting prototypes in production, with no code changes from the simplest "prompt + LLM" chain to the most complex chains. Complex chains can have hundreds of steps. Here are the reasons one would want to use LCEL:

* **First-class streaming support**:  when building chains with LCEL, we get the best possible time-to-first-token which is the time elapsed until the first chunk of output comes out. For some chains this means we stream tokens straight from an LLM to a streaming output parser, and we get back parsed, incremental chunks of output at the same rate as the LLM provider outputs the raw tokens.

* **async support**: any chain built with LCEL can be called both with the synchronous API (e.g. in Jupyter notebook while prototyping) as well as with the asynchronous API (e.g. in a LangServe server). The asynchronous API is obviously beneficial for achieving high throughputs by handling concurrent requests at scale on the server side.

* 

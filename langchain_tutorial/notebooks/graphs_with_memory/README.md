# Resource on graphs utilizing memory

## First Step: Construct a Simple Graph

<!-- ![Figure: Simple Graph with LangChain](../../../images/simple_graph.png) -->

<img src="../../../images/simple_graph.png" alt="Figure: Simple Graph with LangChain" width="500"/>

In order to define simple graph with LangChain first we need to deal with [the State of the graph](https://langchain-ai.github.io/langgraph/concepts/low_level/#state).

### The State of the Graph

The `State` of the graph consists of the _Schema_ of the Graph as well as _Reducer Functions_. Both are defined in the next sections.

### The Schema of the Graph

The schema of the `State` will be input schema to all `Nodes` and `Edges` in the graph, and can be either a `TypedDict` or a `Pydantic` model.  All `Nodes` will emit updates to the `State` whic are then applied using the specified `reducer` function.

LangChain supports the [Pydantic BaseModel](https://docs.pydantic.dev/latest/api/base_model/) as a graph state to add _default values_ and additional data validation. 

By default , the graph will have the same input and output schemas. This default can be changed by specifying the input and output schemas explicitly. This is useful when the schema has a lot of keys and some need to be explicitly for input only while others need to be explicitly specified for output only. 

#### Multiple schemas

Typically, all graph nodes communicate with a single schema. This means that they will read and write to the same state channels. But, there are cases where more  control is needed:

* Internal nodes can pass information that is not required in the graph's input / output.

* different input / output schemas for the graph are needed. The output, for example, could only contain a single relevant output key.



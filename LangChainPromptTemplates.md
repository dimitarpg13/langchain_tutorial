## Prompt Templates

Prompt templates help to translate user input and parameters into instructions for a language model. This can be used to guide a model's response, helping it understand the context and generate relevant and coherent language-based output.

Prompt templates take as an input a dictionary, where each key represents a variable in the prompt template to fill in.
Prompt templates output a `PromptValue`. `PromptValue` is a serializable class with methods `to_messages()` which returns a list of strings representing the prompt value and `to_string()` which converts the prompt to a string.
The PromptValue can be passed to an LLM or a `ChatModel`. The reason the `PromptValue` container exist is to make it easy to swtich between strings and messages.

API reference for `PromptTemplate`: [here](https://python.langchain.com/api_reference/core/prompts/langchain_core.prompts.prompt.PromptTemplate.html)

Here are the available types of Prompt Templates:

### String PromptTemplates

These prompt templates are used to format a single string, and generally are used for simpler inputs. For example, a common way to construct and use a PromptTemplate is as follows:

```python
from langchain_core.prompts import PromptTemplate

prompt_template = PromptTemplate.from_template("Tell me a joke about {topic}")

prompt_template.invoke({"topic": "cats"})
```

### ChatPromptTemplate

These prompt templates are used to format a list of messages. These "templates" consist of a list of templates themselves. For example, a common way to construct and use a `ChatPromptTemplate` is as follows:

```python

```


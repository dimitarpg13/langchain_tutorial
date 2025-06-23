## Prompt Templates

Prompt templates help to translate user input and parameters into instructions for a language model. This can be used to guide a model's response, helping it understand the context and generate relevant and coherent language-based output.

Prompt templates take as an input a dictionary, where each key represents a variable in the prompt template to fill in.
Prompt templates output a `PromptValue`. `PromptValue` is a serializable class with methods `to_messages()` which returns a list of strings representing the prompt value and `to_string()` which converts the prompt to a string.
The PromptValue can be passed to an LLM or a `ChatModel`. The reason the `PromptValue` container exist is to make it easy to swtich between strings and messages.

Here are the available types of Prompt Templates:

### String PromptTemplates

API reference for `String PromptTemplate`: [here](https://python.langchain.com/api_reference/core/prompts/langchain_core.prompts.prompt.PromptTemplate.html)

These prompt templates are used to format a single string, and generally are used for simpler inputs. For example, a common way to construct and use a PromptTemplate is as follows:

```python
from langchain_core.prompts import PromptTemplate

prompt_template = PromptTemplate.from_template("Tell me a joke about {topic}")

prompt_template.invoke({"topic": "cats"})
```

### ChatPromptTemplate

API reference for `ChatPromptTemplate`: [here](https://python.langchain.com/api_reference/core/prompts/langchain_core.prompts.chat.ChatPromptTemplate.html)

These prompt templates are used to format a list of messages. These "templates" consist of a list of templates themselves. For example, a common way to construct and use a `ChatPromptTemplate` is as follows:

```python
from langchain_core.prompts import ChatPromptTemplate

prompt_template = ChatPromptTemplate([
   ("system", "You are a helpful assistant"),
   ("user", "Tell me a joke about {topic}")
])

prompt_template.invoke({"topic": "cats"})
```

In the above example, this `ChatPromptTemplate` will construct two messages when called. The first one is a `SystemMessage` that has no variables to format. The second is a `HumanMessage` and will be formatted by the `topic` variable the user passes in.

More on `HumanMessage` and `SystemMessage` [here](https://python.langchain.com/api_reference/core/messages/langchain_core.messages.human.HumanMessage.html) and [here](https://python.langchain.com/api_reference/core/messages/langchain_core.messages.system.SystemMessage.html).

### MessagesPlaceholder

API Reference for `MessagesPlaceholder`: [here](https://python.langchain.com/api_reference/core/prompts/langchain_core.prompts.chat.MessagesPlaceholder.html)

this prompt template is responsible for adding a list of messages in a particular place. In the above `ChatPromptTemplate` we saw how we could format two messages each one a string. But what if we wanted the user to pass in a list of messages that we would slot into a particular spot? This is how you use `MessagePlaceholder`:

```python
from langchain_core.prompts import ChatPromptTemplate, MessagesPlaceholder
from langchain_core.messages import HumanMessage

prompt_template = ChatPromptTemplate([
  ("system", "You are a helpful assistant"),
  MessagesPlaceholder("msgs")
])

prompt_template.invoke({"msgs": [HumanMessage(content="hi!")]})
```

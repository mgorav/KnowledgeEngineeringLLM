## Boosting LLMs with Open Source RAG

Retrieval augmented generation (RAG) strategically expands language models' knowledge through selective external data integration. Open source ecosystems offer modular building blocks simplifying exploration.

**Core RAG Capabilities:**

- Identify relevant contextual documents
- Fuse pertinent signals into model
- Generate responses incorporating insights

Additional functionality like dense retrievers and query parsers simplify workflow.

**Feature Comparison**


| Tool | Description | Key Features |
|-|-|-|
| HuggingFace | Modular RAG Pipeline | Customizable retrieval, evaluation metrics |
| RealM (NVIDIA)  | Multi-Document Summarization | Neural relevance ranking, fusion |
| Weaviate | VectorSemantic Graph Search | Knowledge graph and text data queries | 
| RAG (Anthropic) | Reusable RAG Modules | Encoder, retriever, decoder components|
| **Pythia** | **Open Domain Dialog** | **Reading comprehension, commonsense reasoning** |
| **BlenderBot** | **Engaging Conversations** | **Persona-based responses, knowledge retrieval** |

Together these accelerate applying retrieval augmentation to boost LLM abilities across use cases like conversational search and open-domain QA. Responsible development principles remain vital throughout model building, training and deployment.

### Examples

**HuggingFace PyTorch**

* Load a RAG model tokenizer, retriever, and generator model
* Retriever indexes documents for efficient passage lookup
* Tokenizer preprocesses text into model digestible tokens
* Model handles retrieval augmentation and text generation
Sample query generates a relevant response text incorporating external information

```python
from transformers import RagTokenizer, RagRetriever, RagTokenForGeneration

tokenizer = RagTokenizer.from_pretrained("facebook/rag-token-nq")
retriever = RagRetriever.from_pretrained("facebook/rag-token-nq", index_name="exact") 
model = RagTokenForGeneration.from_pretrained("facebook/rag-token-nq", retriever=retriever)

inputs = tokenizer("who is the pope?", return_tensors="pt") 
outputs = model.generate(**inputs)
```

**Weaviate Go**

* Client connects to the Weaviate semantic graph database
* Create object inserts data entities with properties into the knowledge graph
* Enables storing nodes and relationships for RAG augmentation

```go
import (
    "github.com/semi-technologies/weaviate/client"
)

client := client.NewClient("http://localhost:8080")
data := map[string]interface{}{
  "name": "John",
  "age":  42,
}

_, err := client.CreateObject(&data)
```

**RealM Python**

Interface wraps the RealM model capabilities
Query is the search request text
Documents show sample passages to augment response
Tau filters document relevance threshold
Model handles ranking passages, fusing context, and text generation

```python
from realmlib import Interface

interface = Interface(
    model_name="voidful/realm-ccnews-encoder",
    model_device="cuda"
)

response = interface(
    query="who is the pope?", 
    documents=["Pope Francis is the leader of the Catholic Church"],
    tau=0.7
)
```

**Pythia Python**

```python
from pythia.common.sample import SampleImage
from pythia.tasks.base_task import BaseTask

task = BaseTask(dataset_type="test")
sample = SampleImage(task=task)  

with torch.no_grad():
    scores = task.model(sample) 
``` 

- Pythia has an extensible modular architecture
- Tasks handle capabilities like visual QA and dialog
- Models process inputs to generate relevant responses

**BlenderBot**

```python 
from parlai.core.agents import create_agent

agent = create_agent(SingleTurnDialogAgent, 
                    opt={'model_file': BLENDERBOT_3B_PATH})

print(agent.act()) 
agent.act(PREV_RESP) 
```

- Provides conversational agent interface
- Opt contains model checkpoint for agent
- act() handles generating responses

### [Back](..%2Freadme.md)
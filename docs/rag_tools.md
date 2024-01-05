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
| HuggingFace | Modular RAG Pipeline | Customizable dense & sparse retrieval, evaluation metrics |   
| RealM (NVIDIA) | Multi-Document Summarization | Efficient passage scoring, neural relevance ranking |
| Weaviate | Graph-based Semantic Retrieval | Vector search on knowledge graph and text data |
| RAG (Anthropic) | Reusable RAG Modules | Encoder, retriever, decoder components for custom models |

Together these accelerate applying retrieval augmentation to boost LLM abilities across use cases like conversational search and open-domain QA. Responsible development principles remain vital throughout model building, training and deployment.

### Examples

**HuggingFace PyTorch**

```python
from transformers import RagTokenizer, RagRetriever, RagTokenForGeneration

tokenizer = RagTokenizer.from_pretrained("facebook/rag-token-nq")
retriever = RagRetriever.from_pretrained("facebook/rag-token-nq", index_name="exact") 
model = RagTokenForGeneration.from_pretrained("facebook/rag-token-nq", retriever=retriever)

inputs = tokenizer("who is the pope?", return_tensors="pt") 
outputs = model.generate(**inputs)
```

**Weaviate Go**

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
### [Back](..%2Freadme.md)
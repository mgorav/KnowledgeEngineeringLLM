## Hugging Face: The Home of Open-Source LLMs

[Hugging Face](https://huggingface.co/) has emerged as the leading platform for accessing, customizing and deploying open-source large language models like BERT, GPT-2, BLOOM and more.

Some key capabilities offered by Hugging Face:

**Easy Access:** Provides hundreds of pre-trained LLMs ready for use via simple model IDs. Enables leveraging state-of-the-art models without training from scratch.

**Performance Optimization:** Features highly optimized implementations of popular model architectures, ensuring speed, reduced memory footprint and lower costs.

**Customization:** Allows fine-tuning models for specific use cases by continuing pretraining on niche datasets. Generates customized high-performing variants.

**MLOps Integrations:** Offers integrations with ML workflows platforms like Amazon SageMaker, Kubernetes, MLflow and more to simplify LLM operations.

**Community:** Boasts of a vibrant community of machine learning researchers and practitioners collaborating on pushing SOTA models. Fosters rapid innovation.

**Commercial Support:** Provides enterprise offerings including confidential computing, dedicated GPU access, premium support and consulting services.

The simplicity of use combined with customization flexibility has catalyzed research and adoption of large language models across academia and industry via Hugging Face's platform. It has played a seminal role in unlocking and shaping the practical applied impact of LLMs.



### Integrating Leading Open-Source LLMs into Scalable Workflows

**State-of-the-Art Models**
Hugging Face provides optimized implementations of pioneering architectures like BERT, GPT-2, BLOOM and DistilBERT.


**MLOps on AWS SageMaker**
Fully managed workflow from notebooks to hosted endpoints:
- Explore models
- Customize via transfer learning
- Operationalize predictions


**Tight Integration**
- Import models directly into notebooks
- Push updated versions to the Hub


**Observability**
Monitor model behavior and performance with CloudWatch data and logs.


This bi-directional integration between Hugging Face and AWS harnesses both cutting edge ML innovation and scalable infrastructure for impactful LLM deployment.

![img_12.png](..%2Fimages%2Fimg_12.png)

Here is a table of Hugging Face large language models that are production-ready:

| Model | Description | Production Readiness |
|-|-|-|
| BERT | Bidirectional encoder for natural language understanding | High - Widely used in industry applications |
| DistilBERT | Lightweight version of BERT with smaller footprint | High - Nearly equivalent performance to BERT with lower compute requirements |
| GPT-2 | Autoregressive decoder model for text generation | Medium - Can be unstable for long form generation, but works well for short text |
| GPT-J | Larger version of GPT-2 with increased performance | Medium - More expensive to run than GPT-2 but generates higher quality text |  
| BLOOM | Blender Bot model designed specifically for conversational AI | High - Made keeping production viability in mind with constraints for safety and reliability |
| XLM-RoBERTa | Multilingual version of BERT supporting 100+ languages | Medium - Production-ready for most languages, but some less resourced languages can be unstable |
| T5 | Encoder-decoder model designed for multi-task learning | Low - Primarily used in research, requires very large compute resources limiting production viability currently |

**Key Criteria for Production Readiness:**

- Model Stability: Consistent behavior without sudden drifting or quality deterioration
- Infrastructure Requirements: Manageable resource needs allowing cost-effective deployment
- Constraint Integration: Controls for safety, accountability etc.
- Monitoring & Explainability: Observability into model internals

**DistilBERT (HuggingFace)**

```python
from transformers import DistilBertTokenizer, DistilBertForSequenceClassification

tokenizer = DistilBertTokenizer.from_pretrained('distilbert-base-uncased')
model = DistilBertForSequenceClassification.from_pretrained('distilbert-base-uncased')

text = "I really enjoyed that movie!"  
inputs = tokenizer(text, return_tensors='pt')
outputs = model(**inputs)  

scores = outputs[0].argmax()
print(scores)
```

Similar to BERT but with the smaller DistilBERT model for faster inference.

**GPT-J (EleutherAI)**

```python
import jax
from mesh_transformer import *

model = GPTJForCausalLM.from_pretrained()
tokenizer = Gpt2Tokenizer.from_pretrained("gpt2")

text = tokenizer.encode("Once upon a time", return_tensors='jax')
output = model.generate(text, do_sample=True, top_p=0.9, max_length=100)
print(tokenizer.decode(output[0]))
```

Leverages Mesh Transformer and JAX for efficient large scale generation.


**BLOOM (HuggingFace)**

```python 
from transformers import BlenderbotSmallTokenizer, BlenderbotSmallForConditionalGeneration

tokenizer = BlenderbotSmallTokenizer.from_pretrained("facebook/blenderbot_small-90M")
model = BlenderbotSmallForConditionalGeneration.from_pretrained("facebook/blenderbot_small-90M")

text = "How are you doing today?"
inputs = tokenizer([text], return_tensors="pt") 
reply = model.generate(**inputs)
print(tokenizer.decode(reply[0]))
```

Facebook's BLOOM encoder-decoder chatbot model.

And similarly for XLM-RoBERTa multilingual model and T5 text-to-text transfer learning model.

### [Back](..%2Freadme.md)
## Examples

**BERT (HuggingFace Transformers)**

```python
from transformers import BertTokenizer, BertForSequenceClassification

tokenizer = BertTokenizer.from_pretrained('bert-base-cased')
model = BertForSequenceClassification.from_pretrained('bert-base-cased')

text = "I really enjoyed that movie!"
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
scores = output[0].argmax().item()
print(scores)
```

- Loads pre-trained BERT model and tokenizer
- Tokenizer encodes raw text into digestible tokens
- Model makes sentiment classification prediction
- Output contains score distribution across classes
- Argmax selects the highest sentiment class

**GPT-2 (HuggingFace Transformers)**

```python
from transformers import GPT2Tokenizer, GPT2LMHeadModel

tokenizer = GPT2Tokenizer.from_pretrained('gpt2')
model = GPT2LMHeadModel.from_pretrained('gpt2')

prompt = "Once upon a time" 
input_ids = tokenizer(prompt, return_tensors='pt').input_ids  

gen_tokens = model.generate(input_ids, do_sample=True) 
gen_text = tokenizer.decode(gen_tokens[0], skip_special_tokens=True)

print(gen_text)
```

- Loads off-the-shelf GPT-2 model
- Encodes context prompt
- Triggers text generation adding to prompt
- Decodes tokens into readable text
- `do_sample` introduces randomness mimicking human

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

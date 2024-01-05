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

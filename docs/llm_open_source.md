## Unlocking Open-Source LLM Power: A Technical Deep Dive

Open-source large language models (LLMs) enable cutting-edge NLP capabilities without expensive licensing. Let's explore the mathematical and algorithmic core powering innovations like BERT, BLOOM, GPT-2 and LAMA.

### LLM Capability Buffet

Feast your eyes on this smorgasbord of powerful open-source models, each with unique strengths:

| Model | Description | Foundation |
|-|-|-|  
| **BERT** | Natural language understanding for sentiment, search etc | Transformer encoder |
| **GPT-2** | Text generation capabilities | Transformer decoder |
| **BLOOM** | Conversational abilities | Blender BOT |   
| **LAMA** | Factual question answering | T5 encoder-decoder |

### BERT: A Transformer Under the Hood

BERT relies on multi-headed self-attention between token vectors to deeply analyze relationships within sentences. This architecture builds interconnected contextual understanding to unlock language mastery.

Mathematically, self-attention layers calculate interaction scores between query, key and value projections of input vectors via:

```
Attention(Q,K,V) = softmax(QK^T/√d)V
```

The attention mechanism is a key component powering the capabilities of large language models like BERT and GPT-2. Let's explore the self-attention formula in more detail:

**Attention(Q,K,V) = softmax(QK^T/√d)V**

Here's what each variable denotes:

**Q:** Queries matrix. Each row represents the vector embedding for a token in the input text sequence that attention is applied on.

**K:** Keys matrix. Analogous to queries - each row holds the vector for an input token.

**V:** Values matrix. Again each row contains the embedding vector for an input token.

Intuitively, queries Q represent what we want to focus attention on, keys K indicate what to match against, and values V hold what content we want to extract.

The **softmax** normalizes weights assigning importance scores. Higher scores denote closer query-key matches.

**QK^T:** This performs a matrix multiplication between queries and keys. The result captures query-key compatibility for every pair of tokens.

**√d**: The d dimensionality scaling factor prevents dot products from growing too large with high-dimensional embeddings.

**Final Output:** The output is a matrix containing attention weighted embedding value vectors - essentially tokens with their representations enriched by relationships modeled via multi-headed self-attention.

In short, self-attention leverages this mathematical machinery to relate words in a sentence irrespective of relative positioning, enabling language understanding. The formulas power modern NLP!


Stacking such layers enables modeling linguistic hierarchy. Pretraining on massive text corpora provides the breadth of language grounding.

### GPT-2: Sculpting Probability Distributions

GPT-2 leverages the Transformer decoder to predict probability distributions for next token sequences. The chain rule decomposition allows language modeling as an autoregressive process:

```math
P(t1,....,tn) = Π P(ti | t1, ...., ti-1) 
```

Where:

- t1 to tn are tokens (typically words or subwords) in a sequence
- P is the probability distribution over sequences
- Π denotes the product over conditional probabilities

This utilizes the chain rule of probability to decompose the overall sequence probability into conditional terms.

Each term P(ti | t1, ...., ti-1) gives the probability of the next token ti given the previous context tokens leading up to it.

So the full formula essentially multiplies a series of conditional probabilities, one for each next token in the sequence.

This allows autoregressively generating text token-by-token, by sampling the next word based on the predictions of the previous ones.

The Transformer decoder architecture in GPT-2 is designed to model these conditional probabilities for text effectively using self-attention and neural layers.

Training on vast corpora slowly sculpts the conditional distributions to resonate with patterns in natural text.

In short, this decomposition into conditional text probabilities enables GPT-2 to generate remarkably high-quality and coherent text by capturing the essential continuity of language.


Training on vast corpora slowly sculpts these distributions to resonate with patterns in textual data - enabling remarkably eloquent text generation capabilities.

And so on for BLOOM's conversational architecture and LAMA's encoder-decoder structure.

Combining the mathematical foundations with workflow optimization unlocks immense applied potential for open-source LLMs.

**BLOOM**

BLOOM is a conversational agent that has been specifically optimized for stability and coherence during dialog interactions. Some of the key techniques used:

**Contextual Weight Assignments**

BLOOM uses elastic weight consolidation (EWC) to prevent catastrophic forgetting when adapting to new conversational contexts:

```
L = Loss(y, ŷ) + λ ∑ Fi Wi (θ - θA)2
```

Here λ adjusts the regularization strength, Fi are Fisher information matrices calculated for parameter θ, Wi denotes the importance and θA contains the historical optimal values.

This allows tuning model parameters to current context while retaining prior training.

**Consistency Regularization**

Consistency techniques like truncated backpropagation through time further enhance sequence level coherence:

```
L = CrossEntropy(y, ŷ) + β * ConsistencyLoss(hT, h1) 
```

Here h1 and hT are hidden states from the start and end of a generated sequence. Minimizing divergence through β ensures response stability.

**Cross Entropy Loss**

Cross entropy quantifies the difference between two probability distributions - specifically between the model's predicted distribution `ŷ` and the true distribution `y`.

It is commonly used as the loss function when training classification models. Mathematically, for a single example:

```
H(y,ŷ) = −∑ y⋅log(ŷ)
```

Here `y` is the one-hot encoded vector for the true class and `ŷ` contains the model predicted probabilities per class.

Minimizing cross-entropy guides the model to output probabilities that closely match the provided labels.

**Consistency Loss**

Consistency loss reduces divergence between model predictions across similar inputs. For language models, it relates outputs at different positions in a text sequence:

```
Lconsistency = ∑ D(hm, hn) 
```

Here `hm` and `hn` are hidden activations from the model at two different sequence positions. `D` measures divergence between the vectors - commonly using MSE or KL divergence.

Minimizing this loss encourages stability in hidden representations across sequence positions. This enhances coherence in model outputs when generating text or having a conversation.

The combination of cross-entropy and consistency losses help improve language quality and stability in models like BLOOM.


**LAMA**

LAMA employs a seq2seq Transformer architecture for tasks like summarization and question answering:


```
P(t1', ...., tm' | t1, ...., tn ) = Π P(tj'| t1, ..., tj-1', t1, ...., tn)
```

The encoder ingests the context sequence tn while decoder models the conditional probability of generating the target summary tk' token-by-token.


# Notes

## Chapter 1. Introduction to Building AI Applications with Foundation Models

### Important Concepts

- Foundation models emerged from large language models, which, in turn, originated as just language models.
- While language models have been around for a while, they’ve only been able to grow to the scale they are today with self-supervision.
- A language model encodes statistical information about one or more languages.
- Intuitively, this information tells us how likely a word is to appear in a given context.
- The statistical nature of languages was discovered centuries ago.
- The basic unit of a language model is token.
- For GPT-4, an average token is approximately ¾ the length of a word.
- The set of all tokens a model can work with is the model’s vocabulary
- Why do language models use token as their unit instead of word or character? 1) Compared to characters, tokens allow the model to break words into meaningful components 2)Because there are fewer unique tokens than unique words, this reduces the model’s vocabulary size, making the model more efficient 3) Tokens also help the model process unknown words. => Tokens balance having fewer units than words while retaining more meaning than individual
characters.
- There are two main types of language models: masked language models and autoregressive language models. They differ based on what information they can use to predict a token.
- Masked language model: A masked language model is trained to predict missing tokens anywhere in a sequence, using the context from both before and after the missing tokens. As of writing, masked language models are commonly used for nongenerative tasks such as sentiment analysis and text classification.
- Autoregressive language model: An autoregressive language model is trained to predict the next token in a sequence, using only the preceding tokens. Today, autoregressive language models are the models of choice for text generation, and for this reason, they are much more popular than masked language models.
- In this book, unless explicitly stated, language model will refer to an autoregressive model.
- language models can be trained using self-supervision, while many other models require supervision. Supervision refers to the process of training ML algorithms using labeled data, which can be
expensive and slow to obtain. Self-supervision helps overcome this data labeling bottleneck to create larger datasets for models to learn from, effectively allowing models to scale up.
- Self-supervision helps overcome the data labeling bottleneck. In self-supervision, instead of requiring explicit labels, the model can infer labels from the input data. Language modeling is self-supervised because each input sequence provides both the labels (tokens to be predicted) and the contexts the model can use to predict these labels.
- Self-supervision differs from unsupervision. In self-supervised learning, labels are inferred from the input data. In unsupervised learning, you don’t need labels at all.
- A model’s size is typically measured by its number of parameters. A parameter is a variable within an ML model that is updated through the training process. In general, though this is not always true, the more parameters a model has, the greater its capacity to learn desired behaviors.
- Why do larger models need more data? Larger models have more capacity to learn, and, therefore, would need more training data to maximize their performance.
- <BOS> and <EOS> mark the beginning and the end of a sequence.
- Incorporating more data modalities into language models makes them even more powerful.
- While many people still call Gemini and GPT-4V LLMs, they’re better characterized as foundation models. The word foundation signifies both 1) the importance of these models in AI applications and the fact that 2) they can be built upon for different needs.
- A model that can work with more than one data modality is also called a multimodal model. A generative multimodal model is also called a large multimodal model (LMM).
- If a language model generates the next token conditioned on text-only tokens, a multimodal model generates the next token conditioned on both text and image tokens, or whichever modalities that the model supports,
- Self-supervision works for multimodal models too. For example, OpenAI used a variant of self-supervision called natural language supervision to train their language-image model CLIP (OpenAI, 2021). Instead of manually generating labels for each image, they found (image, text) pairs that co- occurred on the internet
- This book uses the term foundation models to refer to both large language models and large multimodal models.
- CLIP is an embedding model, trained to produce joint embeddings of both texts and images.
- you can think of embeddings as vectors that aim to capture the meanings of the original data. Multimodal embedding models like CLIP are the backbones of generative multimodal models.
- Foundation models also mark the transition from task-specific models to general-purpose models.
- Foundation models, thanks to their scale and the way they are trained, are capable of a wide range of tasks.
- continue (p.49)




-

#### 🧠 Easy way to remember

**Open-ended = Open answer**  
→ **You explain.**  
→ *“What do you think?”*

**Closed-ended = Closed choices**  
→ **You choose/give a specific answer.**  
→ *“Yes or no?”*

#### 🔑 One-line memory trick

> **OPEN = “Tell me.”**  
> **CLOSED = “Choose/Give me.”**

So whenever you see **open-ended vs. closed-ended**, think:

**OPEN → freedom 🗣️**  
**CLOSED → limits ✅**


-------
language models can be trained using self-supervision


----

### 1.1 Section Title

#### Key Ideas

- 
- 
- 

#### Important Concepts

**Concept**

Definition or explanation.

**Concept**

Definition or explanation.

#### Examples

- 
- 

#### Memorable Statements

> 

#### Key Takeaways

- 
- 

#### My Understanding

...

#### Questions

- 
- 


### 1.2 Section Title

#### Key Ideas

- 
- 

#### Important Concepts

**Concept**

Definition.

#### Memorable Statements

> 

#### Key Takeaways

- 

#### My Understanding

...


## Chapter 2: Chapter Title

### 2.1 Section Title

#### Key Ideas

- 
- 

#### Important Concepts

**Concept**

Definition.

#### Memorable Statements

> 

#### Key Takeaways

- 

#### My Understanding

...


## Chapter 3: Chapter Title

### 3.1 Section Title

#### Key Ideas

- 
- 

#### Important Concepts

**Concept**

Definition.

#### Memorable Statements

> 

#### Key Takeaways

- 

#### My Understanding

...

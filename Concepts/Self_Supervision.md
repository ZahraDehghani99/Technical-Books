**Self-supervision** is a way of training a model where the **training signal (labels) is created automatically from the data itself**, rather than being manually provided by humans.

### Is next-token prediction supervised or self-supervised?

**Next-token prediction is self-supervised learning.** ✅

For example, suppose the training text is:

> `The cat is sleeping`

We can create training examples automatically:

| Input | Target |
|---|---|
| `The` | `cat` |
| `The cat` | `is` |
| `The cat is` | `sleeping` |

Nobody needs to manually label the data. The **text itself provides the target**.

So:

```text
Raw text
   ↓
"The cat is sleeping"
   ↓
Automatically create targets
   ↓
Input:  "The cat is"
Target: "sleeping"
   ↓
Train model
```

That's why it's called **self-supervised**: the data supervises itself.

### But why isn't it just supervised learning?

Technically, the training objective looks exactly like supervised learning:

```text
input → target → loss
```

For example:

```text
"The cat is" → "sleeping"
```

The important distinction is **where the labels came from**:

| Learning type | Where do targets/labels come from? | Example |
|---|---|---|
| **Supervised** | Humans / external annotation | Image → `cat` |
| **Self-supervised** | Automatically generated from the data | `"The cat is"` → `"sleeping"` |
| **Unsupervised** | No explicit target/label | Clustering documents |

So you can think of self-supervised learning as:

> **Supervised learning where the labels are generated automatically from the input data.**

### In LLMs specifically

For a GPT-style model:

**Next-token prediction = self-supervised pretraining objective.**

The model receives:

```text
The capital of France is
```

and the target is:

```text
Paris
```

The training corpus already contains the answer; we don't need someone to annotate every example as *“Paris is the correct answer.”*

This is one of the key reasons LLMs can be pretrained on **enormous amounts of raw text**.

**One important nuance:** after pretraining, models can be further trained with **human-labeled supervised data** (SFT) and/or preference-based methods such as RLHF. So an LLM's entire training process isn't necessarily self-supervised—**next-token prediction during pretraining is.**

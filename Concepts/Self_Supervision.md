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




Yes — **your intuition is correct**. The confusing part is that **“self-supervised” is still a form of supervised learning** in the sense that the model has a target and a loss function.

The distinction is **where the target comes from**.

### Think about it this way

Suppose we want the model to predict the next word:

> `The cat is ___`

The target is:

> `sleeping`

We calculate a loss:

```text
model prediction → "eating"
                    ↓
             compare with
                    ↓
target → "sleeping"
                    ↓
                 loss
```

So yes, we're absolutely **supervising the model with a target**.

The question is:

> **Who created the target?**

### 1. Traditional supervised learning

Humans provide the labels:

```text
Image → [human says] → "cat"
```

The dataset might look like:

```text
image_001.jpg → cat
image_002.jpg → dog
image_003.jpg → cat
```

Someone had to create those labels.

### 2. Self-supervised learning

The **data itself provides the labels**.

Given:

```text
The cat is sleeping
```

we automatically create:

```text
Input:  The
Target: cat

Input:  The cat
Target: is

Input:  The cat is
Target: sleeping
```

No human needed to say *“sleeping is the correct answer.”*

The original text already contained the answer.

---

### So you're right: it IS supervision

A useful mental model is:

> **Self-supervised learning is supervised learning where the supervision/labels are generated automatically from the data.**

That's why the terminology can initially feel weird.

You have:

```text
                 MACHINE LEARNING
                       │
          ┌────────────┴────────────┐
          │                         │
     Supervised                Unsupervised
          │
          │
    ┌─────┴──────┐
    │            │
Traditional   Self-supervised
supervision
    │            │
Human labels   Data generates
               its own labels
```

And **next-token prediction belongs to self-supervised learning**.

### Why call it "self" supervised?

Because the **input creates its own target**.

For example:

```text
Original text:
"The quick brown fox jumps over the lazy dog."

                    ↓

Input                         Target
──────────────────────────────────────
"The"                         "quick"
"The quick"                   "brown"
"The quick brown"             "fox"
"The quick brown fox"         "jumps"
...
```

Then the model predicts the target and we calculate cross-entropy loss.

So the training mechanism is:

**data → automatically construct `(input, target)` → prediction → loss → backpropagation**

The **loss isn't what makes it self-supervised**. Both supervised and self-supervised learning use losses.

The key distinction is **how the target was obtained**.

---

### One more important distinction

You said:

> "we use loss for predicting the word we want"

Exactly.

But consider two scenarios:

**Scenario A — supervised:**

> Human: "Here is a sentence. The correct next word is `Paris`."

**Scenario B — self-supervised:**

> Dataset: "The capital of France is Paris."

We take the existing `Paris` and hide it from the model.

The model tries to predict it, and we use the original text as the target.

That's essentially **creating a learning task from the data itself**.

This is the core idea behind why LLMs can learn from trillions of tokens without humans manually labeling every token.

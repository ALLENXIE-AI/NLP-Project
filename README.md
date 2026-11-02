# NLP Midterm Project: Bigram vs. LSTM vs. Transformer

## 1. Project Overview

This project compares three different language models on the same NLP task: predicting the next character based on previous text.

The three models are:

1. Bigram Language Model
2. LSTM Language Model
3. Small Transformer Language Model

The goal is to understand how different architectures process text, how their performance compares, and how self-attention improves language modeling.

All three models were implemented using Python and PyTorch.

## 2. Dataset

I used the Tiny Shakespeare dataset, which contains approximately 1.1 million characters from Shakespeare's plays.

Dataset source:
https://github.com/karpathy/char-rnn/tree/master/data/tinyshakespeare

The dataset is automatically downloaded when running the notebook.

### Data Preprocessing

- Character-level tokenization
- Vocabulary size: 65 characters
- Training split: 90%
- Validation split: 10%
- Batch size: 32
- Context length: 64 characters

Each character is converted into an integer ID. The models learn to predict the next character at each position in the input sequence.

The same dataset, vocabulary, and train/validation split were used for all three models.

## 3. Model Architectures

### Model 1: Bigram

The Bigram model predicts the next character using only the current character.

It uses an embedding table to learn the scores for possible next characters.

Because the model only considers one character at a time, it cannot understand longer context or sentence structure.

### Model 2: LSTM

The LSTM model uses an embedding layer, an LSTM layer, and a linear output layer.

Architecture:
- Embedding dimension: 64
- Hidden size: 128
- LSTM layers: 1
- Output layer: Linear

Unlike Bigram, LSTM uses hidden states to carry information from earlier characters.

This allows it to learn longer patterns, although it may still struggle with long-range dependencies.

### Model 3: Small Transformer

The Transformer model uses self-attention to process the input sequence.

Architecture:
- Token embeddings
- Positional embeddings
- Embedding dimension: 64
- Attention heads: 4
- Transformer blocks: 2
- Feedforward layers
- Layer normalization
- Linear output layer

The model uses causal masking to prevent attention from accessing future characters.

Self-attention allows the model to consider different positions in the context when predicting the next character.

## 4. Training Configuration

All three models were trained for 1,000 steps using AdamW and cross-entropy loss.

| Setting | Bigram | LSTM | Transformer |
|---|---|---|---|
| Training steps | 1000 | 1000 | 1000 |
| Batch size | 32 | 32 | 32 |
| Context length | 64 | 64 | 64 |
| Learning rate | 0.01 | 0.003 | 0.001 |
| Optimizer | AdamW | AdamW | AdamW |

Training and validation losses were estimated using 20 sampled batches per evaluation, with the same evaluation samples used across models.

Different learning rates were used for the different architectures.

## 5. Experimental Results

| Model | Train Loss | Validation Loss | Training Time |
|---|---:|---:|---:|
| Bigram | 2.4796 | 2.5047 | 2.71s |
| LSTM | 1.6476 | 1.7797 | 5.09s |
| Transformer | 2.0498 | 2.0961 | 8.12s |

### Which Model Performed Best?

The LSTM achieved the lowest validation loss of 1.7797.

Its validation loss was approximately 28.9% lower than Bigram's.

This suggests that LSTM was the most effective model for next-character prediction under the experimental settings.

### Which Model Trained Fastest?

Bigram had the shortest recorded training time at 2.71 seconds.

LSTM required 5.09 seconds, while Transformer required 8.12 seconds.

The simpler Bigram architecture required less computation.

The recorded times are approximate, and GPU synchronization was not handled identically in every initial experiment.

## 6. Generated Text Comparison

Each model generated 300 new characters using a newline as the starting prompt.

### Bigram Sample

~~~text
Henthimavachishelapinisers we s, oreanotsthelu.
GLI it inde Miced tlat mang yofowhas
brothangean t.
~~~

The Bigram generated mostly random-looking character combinations with limited word structure.

### LSTM Sample

~~~text
GLOUCESTERY:
So, lapvits by we have good
The luke I will, be ever fold
He call it thy
brothange.
~~~

The LSTM produced more recognizable English words and Shakespeare-style dialogue.

### Transformer Sample

~~~text
PUANCETRENIICENT,NG HABER:
Plakeman, your thy brothangsan try
Thas thaps me machan the.
~~~

The Transformer learned some dialogue formatting and word patterns but still generated many invented words.

### Qualitative Comparison

The LSTM generated the most readable text in this experiment.

Bigram struggled to form complete words, while Transformer produced some recognizable structures but less coherent text than LSTM.

The complete generated samples are available in `generated_samples.txt`.

## 7. Discussion

### What Did the Transformer Improve?

The Transformer achieved a lower validation loss than Bigram by using self-attention to incorporate information from multiple previous characters.

Unlike Bigram, which only considers the current character, self-attention allows the Transformer to directly consider earlier positions in the context.

However, the Transformer did not outperform LSTM in this experiment.

This may be related to the limited training steps, small model size, and differences in hyperparameters.

### Was the Added Complexity Worth It?

Under the current experimental settings, LSTM provided the best balance between prediction performance and training time.

The Transformer required more training time without achieving better validation loss than LSTM.

However, self-attention remains useful because it can model relationships between distant positions and supports parallel computation during training.

### Limitations

Although all models used the same dataset and training steps, they had different architectures, parameter counts, and learning rates.

Therefore, the experiment does not represent an identical computational budget.

Text quality was also evaluated qualitatively using a limited number of generated samples.

More training steps, hyperparameter tuning, and repeated experiments could provide a more reliable comparison.

## 8. Final Reflection

After comparing Bigram, LSTM, and Transformer models, I learned that using more context can significantly improve language modeling.

Bigram only considers the current character, while LSTM uses hidden states to remember previous information.

Transformers use self-attention to directly examine relationships between positions in a sequence.

I think self-attention is powerful because it allows the model to identify relevant information from different parts of the context without relying entirely on sequential hidden-state updates.

Although my Transformer did not achieve the best results, I learned that a more advanced architecture does not automatically guarantee better performance.

Model size, training configuration, and computational resources all influence the results.

## 9. How to Run

1. Open `NLP_Midterm_Project.ipynb` in Google Colab.
2. Select a GPU runtime if available.
3. Run all notebook cells in order.
4. The notebook will automatically download Tiny Shakespeare.
5. Train the three models and evaluate their performance.
6. Compare the generated text and loss values.

The project uses Python, PyTorch, NumPy, and pandas.

Actual results and training times may vary depending on the runtime and random sampling.

## 10. Repository Contents

- `NLP_Midterm_Project.ipynb` — Complete model implementations, training, evaluation, and analysis.
- `model_comparison.csv` — Training loss, validation loss, and training time.
- `generated_samples.txt` — Generated text from all three models.
- `README.md` — Project documentation.
- `ai_use_summary.md` — AI assistance and usage documentation (to be added).

## 11. AI Usage

ChatGPT was used to help explain model architectures, provide example implementations, guide the training workflow, and help organize the evaluation and documentation.

I ran the models, examined their outputs, compared the experimental results, and reviewed the explanations.

The full AI-use documentation will be provided in `ai_use_summary.md`.

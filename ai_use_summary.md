# AI Use Summary

## AI Tool Used

ChatGPT (OpenAI)

## How AI Assisted Me

I used ChatGPT as a learning and coding assistant during this project.

ChatGPT helped me understand the differences between Bigram, LSTM, and Transformer models, and provided initial PyTorch implementation examples.

It also helped explain character-level tokenization, training loops, model evaluation, and text generation.

After running the experiments, I provided the actual model results to ChatGPT for help interpreting the differences in validation loss, training time, and generated text quality.

ChatGPT also assisted with structuring the README, results analysis, final reflection, and AI-use documentation.

I was responsible for executing the experiments, checking the outputs, comparing the results, and reviewing the final project materials.

The model implementations were AI-assisted, and I have documented this rather than claiming that all code was written independently.

## My Contributions

I was responsible for running the experiments, checking the outputs, analyzing the results, and organizing the final project.

### 1. Environment Setup and Data Preparation

I set up the project in Google Colab and used PyTorch to run the language models.

I loaded the Tiny Shakespeare dataset and used a character-level tokenizer to convert text into numerical sequences.

I worked with the training and validation datasets and used the same data preparation pipeline for all three models to support a fair comparison.

### 2. Model Implementation and Training

I organized and executed the Bigram, LSTM, and Transformer implementations in my notebook using the code examples and explanations provided by ChatGPT.

I ran the training loops for all three models and checked their outputs to confirm that training completed successfully.

I also worked with the training configurations, including batch size, context length, learning rates, and training steps.

This process helped me understand how each model processes input sequences and predicts the next character.

### 3. Experiment Execution and Result Collection

I executed the experiments in Google Colab and collected the actual training loss, validation loss, and training time for each model.

I compared the results:

- Bigram: Validation Loss = 2.5047
- LSTM: Validation Loss = 1.7797
- Transformer: Validation Loss = 2.0961

I observed that LSTM achieved the lowest validation loss, even though the Transformer used a more complex architecture.

I also recorded the training times and organized the results into a comparison table.

### 4. Generated Text Evaluation

I generated text samples using each trained model and examined the differences in their outputs.

I observed that the Bigram model frequently produced random-looking character combinations, while LSTM generated more recognizable words and dialogue structures.

I also noticed that the Transformer learned some Shakespeare-style formatting but still produced many incomplete words.

These observations helped me compare the practical behavior of the models beyond their numerical loss values.

### 5. Results Analysis and Interpretation

I reviewed the experimental results and worked with ChatGPT to interpret the differences between the three models.

I examined why LSTM performed better in this experiment and considered how training steps, model complexity, and hyperparameters could affect the results.

I also considered the limitations of the comparison, including differences in learning rates and computational requirements.

The final analysis was based on actual experimental results rather than assumed model performance.

### 6. Project Organization and GitHub Submission

I organized the notebook into separate sections for data preparation, model implementation, training, evaluation, and reflection.

I saved the experiment results in CSV format and the generated text samples in a separate file.

I created my GitHub repository, uploaded the notebook and result files, and organized the project documentation.

I also used ChatGPT to help structure the README and AI-use documentation.

### 7. Personal Learning

Through running and reviewing the experiments, I developed a better understanding of how the three architectures approach language modeling.

I learned that Bigram relies only on the current character, LSTM uses recurrent hidden states to maintain context, and Transformer uses self-attention to connect information across positions.

One important takeaway from my experiments was that a more advanced architecture does not automatically produce better results under a limited training budget.

This project gave me practical experience executing language modeling experiments, interpreting evaluation metrics, and comparing neural network architectures.

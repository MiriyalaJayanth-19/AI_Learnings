# TinyGPT — Experiment Results

## 1. Overview

This experiment explores how trainable embeddings and Transformer components work together in a GPT-style language model.

The model was implemented using PyTorch and trained on a small next-token prediction task using token IDs produced by a custom tokenizer supporting Telugu and English token pieces.

The objective was to understand the mechanics of embedding learning, causal self-attention, Transformer blocks, and autoregressive prediction.

## 2. Model Configuration

| Parameter | Value |
|---|---|
| Vocabulary size | 1,200 tokens |
| Embedding dimension (`d_model`) | 32 |
| Context length | 16 tokens |
| Transformer blocks | 1 |
| Attention heads | 1 (single-head attention) |
| Feed-forward hidden dimension | 128 |
| Optimizer | AdamW |
| Learning rate | 0.001 |
| Training steps | 100 |
| Total parameters | 89,952 |

## 3. Architecture

The model follows this processing pipeline:

1. **Token Embedding:** Maps each token ID to a learnable 32-dimensional vector.
2. **Positional Embedding:** Adds information about token positions.
3. **Causal Self-Attention:** Allows each token to attend to previous tokens without accessing future tokens.
4. **Feed-Forward Network:** Processes the contextual representations.
5. **Layer Normalization and Residual Connections:** Support stable information flow through the Transformer block.
6. **Language Model Head:** Projects the final representations into scores for all 1,200 vocabulary tokens.
7. **Next-Token Prediction:** Uses cross-entropy loss to compare predicted token scores with the actual next tokens.

## 4. Training Results

The model was trained for 100 optimization steps on a single 16-token input sequence and its corresponding next-token targets.

| Training Step | Reported Training Loss |
|---:|---:|
| 20 | 5.4969 |
| 40 | 3.7281 |
| 60 | 2.1930 |
| 80 | 1.1195 |
| 100 | 0.5634 |

The training loss decreased from approximately 7.1 before training to 0.5634 at the final reported training step.

**Interpretation:** The model became increasingly effective at predicting the tokens in its small training sequence. However, this result does not establish that it can generalize to unseen text.

## 5. Prediction Experiment

After training, greedy decoding was used to generate token predictions for different prompts.

Example prompts included:

- `నేను`
- `Hello world`
- `Artificial intelligence`

The model generated mixtures of Telugu token pieces, English fragments, and byte-level tokens such as `<0x62>`.

Some prompts also produced repeated tokens, including `▁ప్ర`.

### Observations

- The model could produce next-token predictions and generate token sequences.
- Predictions for unfamiliar prompts were generally incoherent.
- Repeated tokens showed that greedy decoding could become stuck in repetitive patterns.
- The generated output was not reliably readable as Telugu or English text.

These results are expected for a model trained on such a small amount of data.

## 6. Key Learnings

- Token IDs are mapped to trainable vector representations through an embedding matrix.
- Positional embeddings provide information about the order of tokens.
- Causal attention prevents a token from accessing future tokens during training.
- Residual connections, layer normalization, and feed-forward networks form important parts of a Transformer block.
- Cross-entropy loss and backpropagation allow the model's parameters to learn next-token prediction.
- A decreasing training loss does not necessarily indicate language understanding or generalization.
- Training data, tokenizer consistency, and evaluation on unseen examples are essential when developing language models.

## 7. Limitations

This experiment is an educational implementation, not a production-ready language model.

Current limitations include:

- Training on only one tiny sequence rather than a representative text corpus.
- A single attention head and one Transformer block.
- No held-out validation or test dataset.
- No meaningful evaluation of language quality or generalization.
- Generated token pieces may not decode into readable text.
- Greedy decoding can produce repetitive outputs.

The training loss should therefore be interpreted only as evidence that the model learned the small training task.

## 8. Next Steps

Planned improvements:

1. Verify tokenizer encoding and decoding, including byte-level tokens.
2. Train on a larger Telugu–English text corpus.
3. Create training, validation, and test splits.
4. Generate multiple training examples using sliding context windows.
5. Implement multi-head causal self-attention.
6. Compare training and validation loss.
7. Evaluate predictions on prompts excluded from training.
8. Experiment with sampling strategies and repetition control.

## 9. Conclusion

This experiment provided a practical introduction to the core mechanics of a GPT-style language model, from token embeddings to Transformer-based next-token prediction.

The most important finding was that successfully implementing and training a model is only the first step. Learning useful language patterns requires suitable data, careful evaluation, and evidence of generalization beyond the training examples.
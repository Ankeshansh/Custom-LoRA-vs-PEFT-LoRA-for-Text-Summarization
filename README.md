# Custom LoRA vs PEFT LoRA for Text Summarization

## Project Overview
This project implements Low-Rank Adaptation (LoRA) for fine-tuning T5 for text summarization:
1. **PEFT LoRA** - Uses the `peft` library to apply LoRA efficiently.
2. **Custom LoRA** - Manually implements LoRA modifications in transformer layers.

The goal is to analyze the performance, efficiency, and implementation complexity of both methods.

## Installation
Ensure you have the required dependencies installed:
```bash
pip install torch transformers datasets rouge_score peft
```

## Dataset
The project uses the CNN/DailyMail dataset for text summarization. It is loaded using the Hugging Face `datasets` library:

## Model and Training
### PEFT LoRA Approach
- Uses `peft.LoraConfig` to inject LoRA adapters into T5 layers.
- Efficiently fine-tunes parameters while freezing the base model.
- Requires fewer resources compared to full fine-tuning.

### Custom LoRA Approach
- Manually modifies transformer layers to integrate LoRA.
- Implements custom parameter decomposition and adaptation.
- More flexibility but requires deeper understanding of model internals.

### Training
Both methods follow similar training steps:
1. Tokenization using `T5Tokenizer`.
2. Model initialization (`T5ForConditionalGeneration`).
3. Dataset preparation (padding, truncation, batching).
4. Training loop with loss computation and optimization.
5. Evaluation using ROUGE scores.

## Evaluation and Results
- Both methods are evaluated using the **ROUGE metric** to measure summarization quality.
- PEFT LoRA provides faster training and lower memory consumption and is easier to implement and integrate due to its library support.
- Custom LoRA allows more fine-grained control and slightly outperforms PEFT LoRA in all ROUGE metrics.


## ROUGE Score Comparison
The following table presents the ROUGE scores achieved by each method:

| Metric  | Custom LoRA | PEFT LoRA |
|---------|------------|-----------|
| **ROUGE-1** | 0.3293     | 0.3194    |
| **ROUGE-2** | 0.1306     | 0.1227    |
| **ROUGE-L** | 0.2537     | 0.2462    |





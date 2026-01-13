# Interviewer Tuning

This repository contains experiments for **fine-tuning and inference of large language models** to behave as an adaptive interviewer.

The core idea is to train a model to act as an interviewer who asks meaningful follow-up questions based on an ongoing conversation. The project focuses on:

- Parameter-efficient fine-tuning (LoRA)
- 4-bit quantized model loading for low memory usage
- Instruction-based conversational datasets
- Interactive inference loops
- Data extraction and refinement pipelines for tuning

---

## Models
- `tiiuae/falcon-7b`
- `microsoft/phi-2`

## Key Techniques
- Hugging Face Transformers
- BitsAndBytes 4-bit quantization
- PEFT / LoRA
- Instruction + conversation style prompting
- Custom dataset preprocessing and merging
  
## Fine-Tuning Strategy
The fine-tuning process is carried out in two stages using LoRA adapters:

### Domain Fine-Tuning
In the first stage, the model is fine-tuned on domain-specific data (e.g., Python, Azure, Cooking, etc.).
The objective is to build domain expertise by training the model to complete text sequences extracted from domain-specific textbooks or structured learning material.

### Conversational / Interview Fine-Tuning
In the second stage, the domain-adapted model is further fine-tuned on instruction-based conversational data.
This step teaches the model to conduct interviews by generating coherent, contextual follow-up questions based on an ongoing dialogue.

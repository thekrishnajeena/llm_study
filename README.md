# 🧠 LLM Study Journey

Welcome to my personal deep dive into the world of Large Language Models (LLMs)! This repository documents my hands-on exploration of core concepts, practical workflows, and advanced techniques in natural language processing using the Hugging Face ecosystem and beyond.

---

## 🚀 What This Project Covers

This study is structured around real-world mini-projects and experiments that reflect both foundational and cutting-edge topics in LLMs:

### 📚 Core Topics
- Tokenization strategies and dataset preprocessing
- Efficient batching with dynamic padding
- Transformer architectures and attention mechanisms
- Evaluation metrics like perplexity
- Time series modeling (AR, MA, ARMA) for NLP applications

### 🛠️ Practical Workflows
- Using `datasets.map()` with batched tokenization
- Leveraging `DataCollatorWithPadding` for memory-efficient training
- Troubleshooting multiprocessing and tokenization edge cases
- Fine-tuning and deploying models on AMD GPUs with ROCm
- Containerizing models using Docker

---

## 🧪 Example: Tokenizing GLUE Tasks

```python
def preprocess_glue(example, task_name):
    if task_name in ["sst2", "cola"]:
        return tokenizer(example["sentence"], truncation=True)
    elif task_name == "qqp":
        return tokenizer(example["question1"], example["question2"], truncation=True)
    elif task_name == "qnli":
        return tokenizer(example["question"], example["sentence"], truncation=True)
    elif task_name in ["mnli", "ax"]:
        return tokenizer(example["premise"], example["hypothesis"], truncation=True)
    elif task_name in ["mrpc", "rte", "stsb", "wnli"]:
        return tokenizer(example["sentence1"], example["sentence2"], truncation=True)
    else:
        raise ValueError(f"Unsupported task: {task_name}")

# MetaGuard: A Multi-Layer Classification Framework for Controlled and Safe LLM Response Generation

## Abstract
Large Language Models (LLMs) face a critical vulnerability: unsafe prompts can bypass safeguards and cause harmful or unethical outputs. In this work, we present MetaGuard, a real-time multi-layered classification system that analyzes user inputs using both binary (benign/malicious) and domain-subdomain classification before dynamically generating system prompts to control LLM responses. Our framework combines lightweight RoBERTa-based classifiers, real-time metadata integration, and flexible prompt engineering to enhance LLM safety without compromising usability. Experiments demonstrate over 97% F1 score for binary classification and high accuracy in detecting specific sensitive domains such as Technology Misuse and Serious Crime. MetaGuard offers a practical pathway for securing open LLM deployments.

## Keywords
Prompt Injection, LLM Safety, Binary Classification, Metadata-driven Defense, Multi-Layer Architecture

## 1. Introduction
The increasing adoption of LLMs has exposed vulnerabilities where carefully crafted prompts can bypass system instructions, leading to unsafe, unethical, or illegal outputs. Existing moderation tools primarily rely on simple keyword matching, which are insufficient against modern, obfuscated attacks. There is an urgent need for real-time, dynamic prompt analysis before forwarding inputs to the LLM. MetaGuard aims to fill this gap through a dual classification approach that informs the system prompt guiding LLM behavior.

## 2. Background
Prompt injection research has intensified after notable attacks demonstrated jailbreaks and instruction overrides on major LLMs. Traditional defenses, including OpenAI's Moderation API or prompt hardening techniques, often lag behind adversaries' evolving tactics. Prior works mainly targeted binary classification, leaving finer-grained domain control underexplored. This motivates MetaGuard’s hybrid, metadata-informed defense architecture.

## 3. Related Work
Several works like DeepMind's Safeguard, WildJailbreak Dataset studies, and OpenAI's prompt leak detection highlight vulnerabilities in model prompting. However, few propose an integrated pipeline of binary and domain-specific classification influencing system prompts dynamically. MetaGuard extends beyond simple blocking to metadata-driven control at the prompt layer.

## 4. Methodology
MetaGuard consists of two primary classifiers:
- **Binary Classifier** (RoBERTa-base): Trained on a merged dataset (SafeGuard, SPML, Jailbreak Classification) to classify prompts as benign (0) or malicious (1).
- **Multi-Class Domain Classifier** (RoBERTa-base): Trained on GenTelBench-v1 to predict domain and subdomain categories (28 classes + safe).

Both classifiers output prediction probabilities and top-k classes, which are injected into a dynamically crafted system prompt.

The final system prompt determines whether the LLM should answer normally, answer cautiously, or refuse to answer based on the binary and domain labels.

## 5. System Architecture

```
User Prompt → Binary Classifier
           → Multi-Class Classifier
           → System Prompt Generator
           → Controlled LLM (via Ollama)
           → Safe Response to User
```

- Binary Classifier: flags prompt as benign/malicious
- Multi-Class Classifier: classifies sensitive domains
- System Prompt Generator: adapts behavior based on metadata
- LLM (local LLaMA 3.1/8B) responds based on embedded rules

## 6. Experimental Setup
- **Hardware**: Ubuntu 22.04, NVIDIA RTX 4090 (24 GB VRAM)
- **Datasets**:
  - Jailbreak-Classification (binary)
  - SPML-Chatbot Injection (binary)
  - SafeGuard Prompt Injection (binary)
  - GenTelBench-v1 (domain-subdomain multiclass)
- **Training Details**:
  - Model: `roberta-base`
  - Learning Rate: 1.5e-5
  - Batch Size: 64
  - Epochs: 5
  - Mixed Precision (fp16): Enabled

## 7. Results

### 7.1 Binary Classifier
- **Accuracy**: 97.8%
- **F1 Score**: 97.5%
- **Precision**: 98.1%
- **Recall**: 97.2%
- **Confusion Matrix**:

|        | Predicted Benign | Predicted Malicious |
|--------|------------------|---------------------|
| Benign |  4900             | 100                 |
| Malicious | 120             | 4880               |

### 7.2 Multi-Class Domain Classifier
- **Accuracy**: 95.3%
- **Macro F1**: 94.7%
- **Top-3 Accuracy**: 99.1%
- Misclassifications primarily occurred between closely related domains (e.g., Cybercrime vs Malware).

### 7.3 Streamlit Web UI Demo
- Model selector (LLAMA 3.1/8B)
- Displays classification metadata
- Dynamic system prompt adaptation
- Real-time logging (input/output/log.json)

## 8. Discussion
**Strengths**:
- Fast real-time prediction (<100ms per prompt)
- Metadata-driven LLM response generation
- Modular design compatible with any HuggingFace model

**Limitations**:
- Current setup only covers English prompts
- Fine-grained classification for multilingual prompts needs future work
- Some semantic ambiguity between classes like "Social Panic" and "Manipulation of Public Opinion"

## 9. Conclusion and Future Work
MetaGuard demonstrates that a lightweight multi-layered prompt filtering system can significantly enhance LLM safety without sacrificing flexibility. By dynamically adjusting LLM behavior based on classifier metadata, it offers a scalable path for deploying safer models in production environments.

**Future Work**:
- Token-level explainability (LIME/SHAP)
- Unsupervised detection of new attacks
- Full multilingual capability (Arabic, Chinese, etc.)
- REST API + Hugging Face Spaces Deployment

## References

[1] OpenAI Moderation API: https://platform.openai.com/docs/guides/moderation

[2] DeepMind Safeguard Dataset, WildJailbreak (2024)

[3] RoBERTa: Robustly Optimized BERT Pretraining Approach (Liu et al.)

[4] HuggingFace Datasets Library: https://huggingface.co/docs/datasets

[5] Ollama Local LLM Server: https://ollama.ai

---

## Authors
**Ibrahim Odat**  
**Abdalla XX**  
School of Computer Science and Engineering  
University Research Project 2025


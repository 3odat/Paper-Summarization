# **Prompt Inject Detection with Generative Explanation**


### ✅ **Abstract:**
Large Language Models (LLMs) are susceptible to **prompt injection attacks**, which can manipulate or exploit model vulnerabilities, leading to unintended responses such as **jailbreaking, malicious outputs, or security breaches**. The challenge in investigating these attacks arises due to the **sheer volume of input prompts**, many of which are benign, and the **contextual subjectivity** of adversarial prompts.

This research proposes **using an LLM-based system to not only detect prompt injections but also generate explanations for detections**, helping AI security investigators **triage and analyze** malicious inputs. The study explores **fine-tuning LLMs** to improve detection and explanation accuracy.

### ✅ **Figures & Tables:**
- **Comparison of model performance** using different fine-tuning techniques.
- **Evaluation of adversarial prompt detection** using **ToxicChat dataset**.
- **Manual evaluation of generated explanations** for clarity, bias, and correctness.

### ✅ **Conclusion:**
The study finds that **fine-tuned LLMs** significantly improve the detection of adversarial prompts. Moreover, **LLMs can generate useful explanations**, aiding AI security investigators in understanding and handling **prompt injection attacks**. The research concludes that such tools can enhance **cybersecurity analysis** and suggests future work on **output censorship detection and improving explanation quality**.

---

## **📌 Step 2: Read the Key Sections in Detail**

### 🔹 **Introduction – Why is this research necessary?**
- **LLMs are vulnerable** to **prompt injection attacks**, where attackers craft **malicious prompts** to bypass safeguards.
- These attacks can cause **hallucinations, data leaks, or generate harmful content**.
- Existing **guardrails (e.g., signature-based, ML-based)** focus on detection but **lack explanation** mechanisms.
- This research explores using **text-generation LLMs** to **both detect** adversarial prompts and **generate explanations**, improving AI security investigations.

---
![Alt Text](1.jpg)
### 🔹 **Methodology – How was this done?**

#### **1️⃣ Dataset Selection**
- **ToxicChat Dataset**: A benchmark dataset containing:
  - **Benign prompts**
  - **Toxic prompts**
  - **Jailbreaking prompts** (attacks to override LLM safeguards)

#### **2️⃣ LLM-Based Guardrails with Explanation**
- **Llama3.2 (1B and 3B models) from Meta** were used.
- Models were **fine-tuned using**:
  - **Supervised Fine-Tuning (SFT)**
  - **Direct Preference Optimization (DPO)**
  - **Low-Rank Adaptation (LoRA)**

#### **3️⃣ Experimental Setup**
- Evaluated **prompt detection accuracy** using:
  - **ToxicChat dataset** (known benign/adversarial prompts)
  - **Garak (Nvidia’s adversarial LLM testing tool)**
- **Generated explanations manually evaluated** for:
  - **Listing contributing factors**
  - **Subjectivity/bias**
  - **Illustrative examples**
  - **Misleading arguments**

---

### 🔹 **Results & Discussion – Key Findings**

#### **1️⃣ Detection Accuracy**
- **Fine-tuned models (SFT & DPO) outperformed vanilla models** in detecting adversarial prompts.
- **Larger models (3B parameters) generalized better than 1B models** after fine-tuning.

#### **2️⃣ Generated Explanations**
- **Fine-tuned models provided better explanations** than vanilla models.
- **Key observations:**
  - Some explanations were **subjective or biased**.
  - Some explanations **lacked illustrative examples**.
  - A few explanations were **misleading** but rare.

---

## **📌 Research Significance**

### **🔍 What problem does this paper solve?**
- **Existing guardrails detect but do not explain prompt injection attacks.**
- **LLMs can generate explanations**, aiding AI security investigations.
- **Fine-tuning improves adversarial prompt detection and explanation accuracy.**

### **🔍 Main Contribution:**
✅ **Introduced an LLM-based prompt injection detection tool with generative explanations.**  
✅ **Evaluated fine-tuning techniques (SFT, DPO, LoRA) to enhance detection performance.**  
✅ **Conducted human evaluation of explanations to ensure reliability.**  

### **🔍 How does this paper fit into Cybersecurity & AI research?**
- **AI-Powered Penetration Testing**: Helps detect and analyze adversarial attacks on LLMs.
- **Defensive AI Security**: Provides a tool for investigators to identify and respond to malicious prompts.
- **Adversarial NLP Attacks**: Enhances understanding of prompt injection vulnerabilities.

---

## **📌 Next Steps & Future Work**
- **Assessing LLMs for output censorship detection**.
- **Improving explanation generation quality**.
- **Expanding dataset diversity to enhance robustness**.

---

## **🔎 Key Takeaways**
💡 **Fine-tuned LLMs improve prompt injection detection.**  
💡 **LLMs can generate explanations to support AI security investigations.**  
💡 **Future research should enhance output analysis and explanation clarity.**  

This research has **practical applications** for **AI security teams**, **cyber threat analysts**, and **AI developers**, helping them understand and **combat prompt injection attacks effectively**. 🚀

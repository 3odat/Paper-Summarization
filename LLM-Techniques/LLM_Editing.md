# Memory Sharing for Large Language Model based Agents


## Abstract
The adaptation of Large Language Model (LLM)-based agents to execute tasks via natural language prompts represents a significant advancement, notably eliminating the need for explicit retraining or fine-tuning. However, these agents are constrained by the comprehensiveness and diversity of provided examples, leading to outputs that often diverge from expected results, especially for open-ended questions. This paper introduces the **Memory Sharing (MS) framework**, which integrates real-time memory filtering, storage, and retrieval to enhance In-Context Learning (ICL). This framework allows for **memory sharing among multiple agents**, improving response quality and facilitating collective intelligence. The dynamically growing memory pool is leveraged not only to improve responses but also to train and enhance the retriever. We evaluate our framework across three distinct domains involving specialized agent tasks. Experimental results demonstrate that the MS framework significantly enhances agent performance in addressing open-ended questions.

## Introduction
Large Language Models (LLMs) have transformed machine learning and conversational AI. In-Context Learning (ICL) enables LLMs to perform tasks using **few-shot examples** without requiring parameter updates, significantly expanding the capabilities of LLM-based agents. However, challenges remain regarding the diversity of examples and reliance on external databases.

We propose the **Memory Sharing (MS) framework**, which allows multiple agents to share memories, facilitating **collective self-enhancement** through interactive learning. This enables agents to evolve from **individual intelligence to collective intelligence**. By integrating **Retrieval-Augmented Generation (RAG)**, the MS framework enhances example diversity and allows for **autonomous memory growth**.

### Contributions
1. **Shared Memory Pool**: Constructing Prompt-Answer (PA) pairs from multiple agents and storing them for collaborative improvements.
2. **Addressing Data Scarcity**: Introducing an interactive learning method for rapid memory expansion.
3. **Empirical Validation**: Conducting extensive experiments across different open-ended tasks, demonstrating the effectiveness of MS in improving agent responses.

## Related Work
### Memory Mechanisms in Agents
Equipping agents with memory mechanisms enhances performance, ensuring conversational consistency and experience accumulation. Existing models like **MemGPT**, **VOYAGER**, and **Reflexion** leverage memory for self-enhancement, but **MS focuses on shared memories for collective intelligence.**

### In-Context Learning
ICL improves LLM adaptability via **few-shot learning**, enhancing logical reasoning and generalization. However, **lack of example diversity** and reliance on **external knowledge bases** hinder performance. MS addresses these challenges by dynamically **generating and sharing high-quality examples.**

### Retrieval-Augmented Generation
RAG enhances LLM responses by retrieving relevant examples from external databases. However, existing retrievers are **static**. The **MS framework continuously trains the retriever**, ensuring it evolves alongside the expanding memory pool.

## The Memory Sharing Framework
### Memory Generation
Memories are stored as **Prompt-Answer (PA) pairs**. After each interaction, a PA pair is evaluated and, if deemed useful, added to the memory pool.

### Memory Retrieval and Training
Agents retrieve **relevant memories** from the shared pool via a **dense retriever**, which improves response quality. Additionally, new memories are **used to train the retriever**, enhancing its adaptability.

### Interactive Learning
To bootstrap memory sharing, **agents interactively generate and refine prompts and answers**, expanding the memory pool dynamically. This rapid learning method enables **self-enhancement in multi-agent systems.**

## Experiments
### Experiment Details
We evaluate the **MS framework** across three domains:
1. **Literary Creation** (Sonnets, Limericks, Classical Chinese Poetry)
2. **Unconventional Logic Problem-Solving** (Puzzles, Riddles, Puns)
3. **Plan Generation** (Study Plans, Travel Plans, Fitness Plans)

Three LLMs are tested: **GPT-3.5-turbo, GPT-4o, and Open-Mistral-7B**. Performance is measured using **BERTScore**.

### Experiment Analysis
**Findings:**
- **Shared memories improve performance significantly** compared to zero-shot learning.
- **Three-shot learning** yields the best results for most agents.
- **Homogeneous memory pools (domain-specific) outperform heterogeneous pools**, emphasizing the importance of domain relevance.
- Performance **improves as memory pool size increases**.

## Conclusion
We introduce the **MS framework**, enabling real-time **memory sharing** among multiple LLM-based agents. **Key results:**
- **Enhanced response accuracy for open-ended queries**.
- **Dynamically growing memory pool improves retriever effectiveness**.
- **Eliminates dependence on external databases** through interactive learning.

### Future Work
- **Integration with more LLMs** (e.g., GPT-4, LLaMA-3, Claude-2).
- **Exploring self-generated memories for fine-tuning LLMs**.
- **Handling complex, multi-turn interactions in memory sharing.**

# decodelabs_tasks
DecodeLabs Internship assignments
# DecodeLabs Industrial Training: Deterministic AI Engines

**Author:** Michael Odhiambo  
**Role:** Full Stack Developer (Kotlin/Python) & Prompt Engineer  
**Batch:** 2026 | Powered by DecodeLabs

## 🚀 Project Overview

This repository contains three production-grade Prompt Engineering modules designed to transform Large Language Models (LLMs) from probabilistic chatbots into **deterministic compilation engines**. 

Moving beyond simple conversational interfaces, these projects implement strict architectural patterns—including Few-Shot Learning, Chain-of-Thought (CoT) Scaffolding, and Context-Anchored RAG—to achieve zero-tolerance for hallucinations and 100% schema adherence.

## 🛠️ Technical Methodologies

### Task 1: Zero-Shot & Few-Shot Data Extraction
*   **Mission:** Transform chaotic, unstructured customer support emails into strictly typed JSON.
*   **Key Techniques:**
    *   **Delimiter Isolation:** Used `<raw_data>` tags to prevent Instruction-Data Conflation.
    *   **Few-Shot Patterning:** Implemented 3 structural examples to push format adherence from ~60% to >99%.
    *   **Null-Fallback Logic:** Enforced explicit `null` returns for missing fields (e.g., missing phone numbers) to protect downstream database integrity.
    *   **Temperature Control:** Hardcoded to `0.0` for deterministic token selection.

### Task 2: Chain-of-Thought (CoT) Logic Engine
*   **Mission:** Force System 2 (Deliberate) reasoning to solve complex multi-step logic traps.
*   **Key Techniques:**
    *   **XML Scaffolding:** Enforced a rigid 4-phase pipeline (`Extract`, `Formulate`, `Calculate`, `Inner Critic`) within `<reasoning>` tags.
    *   **Self-Correction:** Implemented an "Inner Critic" phase where the model audits its own math before finalizing the output.
    *   **Cognitive Reflection Tests (CRTs):** Validated against heuristic traps (e.g., the "5 machines/5 widgets" riddle) to prove the engine overrides System 1 intuition.

### Task 3: Context-Anchored Answering (RAG Basics)
*   **Mission:** Build a "Closed-Book" Gatekeeper that relies solely on verified context.
*   **Key Techniques:**
    *   **Context Locking:** Restricted the model to `[Para X]` tagged documents, bypassing pre-trained parametric memory.
    *   **Deflection Protocol:** Implemented a strict negative constraint: if information is missing, the engine outputs exactly `"Information Not Found"` without apology or filler.
    *   **Source Attribution:** Required precise paragraph-level citations (`[Para 1]`) for every factual claim to ensure auditable paper trails.

## 💻 Integration Strategy (Backend Perspective)

As a Backend Developer specializing in **Kotlin (Ktor)** and **Python (Django)**, I view these prompts as critical "Logic Modules" in a larger microservices architecture:

1.  **Validation Hierarchy:** In a production environment, the JSON output from **Task 1** would be immediately passed through a **Pydantic (Python)** or **Kotlinx Serialization** validator. If the schema fails, a "Repair Loop" prompt is triggered automatically.
2.  **RAG Pipeline:** **Task 3** represents the generation layer of a RAG system. In a real-world deployment, the `<context>` block would be dynamically populated by a vector database retrieval step, while the "Deflection Protocol" serves as a safety layer for enterprise HR or Legal queries.
3.  **Cost Optimization:** By placing static instructions and Few-Shot examples at the beginning of the prompt (Static Prefix), we maximize cache hits in modern LLM APIs, reducing latency and token costs by up to 90%.

## 📂 Repository Structure

```text
decodelabs_tasks/
├── README.md
├── Task_1_Data_Extraction/
│   ├── prompt_engine.md       # The "Code": Strict extraction prompt
│   ├── test_input.txt    # Input: Chaotic data with missing fields
│   └── output.json   # Output: Flawless JSON with null handling
├── Task_2_CoT_Logic/
│   ├── prompt_engine.md       # The "Code": CoT XML scaffolding
│   ├── test_input.txt         # Input: CRT Logic Traps
│   └── output.txt         # Output: Step-by-step reasoning proof
└── Task_3_RAG_Gatekeeper/
    ├── prompt_engine.md       # The "Code": Context-locking prompt
    ├── context_docs.txt       # Input: Verified [Para X] documents
    ├── test_input.txt       # Input: Valid + Distractor queries
    └── output.txt         # Output: Citations and Deflection proof
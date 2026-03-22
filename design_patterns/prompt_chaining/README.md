# 1. Prompt Chaining

## What
Prompt Chaining, also known as the **Pipeline pattern**, is a "divide-and-conquer" strategy for handling intricate tasks with Large Language Models (LLMs). Instead of using a single, monolithic prompt, the original problem is broken down into a sequence of smaller, manageable sub-problems. In this workflow, the output generated from one prompt is strategically fed as input into the subsequent prompt, establishing a dependency chain.

## Why
*   **Modularity and Clarity**: Decomposing tasks makes each individual step easier to understand, optimize, and debug.
*   **Enhanced Reliability**: By focusing the model on one specific operation at a time, it reduces the "cognitive load," which minimizes common issues like instruction neglect, contextual drift, and hallucinations.
*   **Role Specialization**: You can assign distinct roles (e.g., "Market Analyst" for step 1, "Expert Writer" for step 3) to the model at different stages to increase accuracy.
*   **External Integration**: It allows the system to interact with external APIs, databases, or calculators between LLM calls, enriching the agent's capabilities beyond its training data.

## When
Use this pattern when a task is too complex for a single prompt, involves multiple distinct processing stages, or requires state management. 

**Practical Examples:**
*   **Information Processing**: Extracting text from a URL, summarizing it, and then identifying key entities for a database search.
*   **Data Transformation**: Converting unstructured text (like an invoice) into a structured JSON format through iterative extraction and validation.
*   **Content Generation**: A procedural workflow moving from ideation to outlining, drafting sections, and final coherence review.
*   **Complex Reasoning**: Breaking a multi-part question into sub-questions that are researched individually before synthesizing a final answer.

## Caution
*   **Data Integrity**: The reliability of the chain depends on the integrity of data passed between steps; ambiguous or poorly formatted output in one stage can cause subsequent stages to fail. Using **structured outputs** (JSON/XML) is crucial.
*   **Error Propagation**: While chaining helps manage errors, early mistakes can still amplify if not caught by validation logic between steps.
*   **Latency**: Sequential processing is inherently slower than single-prompt or parallel execution since each step must wait for the previous one to complete.

## Implementation: *show me the code!*

- **[langchain_code.ipynb](./langchain_code.ipynb)** — Introductory notebook demonstrating a **2-step LangChain chain** (LCEL). The first step extracts technical specifications from a free-text description; the second transforms those specifications into a structured JSON object. Shows how to compose prompts and parsers using the `|` pipe operator.

- **[langchain_code_advanced.ipynb](./langchain_code_advanced.ipynb)** — Advanced notebook implementing a **4-step job-application analyser** with LangChain. Each step produces a validated **Pydantic** object (`JobRequirements`, `CandidateScore`, `InterviewPlan`) that feeds into the next, with the final step generating a free-form hiring recommendation report. Also demonstrates how to express the entire pipeline as a single LCEL chain using `RunnablePassthrough` and `RunnableLambda`.

- **[agent.py](./agent.py)** — Implements a 3-stage code pipeline using the **Google ADK** `SequentialAgent`. Three `LlmAgent` instances are chained in order: a Code Writer (generates Python code from a specification), a Code Reviewer (critiques the generated code), and a Code Refactorer (applies the review feedback to produce a final, improved version).

***

## Infographic

![](./infographic.png)

# 2. Routing

## What
Routing is a design pattern that introduces conditional logic into an agent’s operational framework, allowing it to move beyond fixed, linear execution. It acts as a dynamic decision-making mechanism that evaluates specific criteria—such as user intent, environment state, or previous outputs—to select the most appropriate subsequent action, specialized tool, or sub-agent.

## Why
*   **Adaptive Behavior**: It transforms an agent from a static executor into a flexible, context-aware system capable of making intelligent decisions under changing conditions.
*   **Efficiency and Specialization**: By acting as a high-level dispatcher, routing ensures that tasks are assigned to the most suitable specialized component, improving overall system performance.
*   **Scalability**: It allows developers to build sophisticated applications that can manage the complexity and variability of real-world requests by triaging inputs.

## When
Use the Routing pattern when an agent must decide between multiple distinct workflows, tools, or sub-agents based on the current state or user input. 

### Routing Mechanisms

Routing is the core component of the Routing pattern, acting as the decision-making engine that directs the flow of control. There are four primary ways to implement this mechanism:

*   **LLM-based Routing**: The language model itself is prompted to analyze the input and output a specific category or identifier (e.g., "Order Status" or "Technical Support"). 
*   **Embedding-based Routing**: Input queries are converted into vector embeddings and compared against embeddings representing different routes or system capabilities.
*   **Rule-based Routing**: This approach uses predefined logic, such as `if-else` statements, switch cases, or regular expressions, based on keywords and structured data.
*   **Machine Learning (ML) Model-Based Routing**: This involves using a specialized discriminative model, such as a classifier, that has been fine-tuned on labeled data for a specific routing task.

**Practical Examples:**
*   **Customer Support**: Classifying a query to direct it to "Sales," "Technical Support," or an "Account Management" tool.
*   **Data Pipelines**: Analyzing incoming files (e.g., emails or API payloads) to trigger specific transformation functions based on format or metadata.
*   **AI Coding Assistants**: Identifying a programming language and user intent (debug vs. explain) to route the request to the correct specialized tool.

## Caution
*   **Reliability vs. Flexibility**: LLM-based routing is flexible but can be less deterministic and slower than rule-based logic (e.g., if-else statements).
*   **Computational Cost**: Using a generative model for every routing decision can increase latency and API costs compared to embedding-based semantic similarity or specialized classifiers.
*   **Complexity**: In intricate scenarios, routing requires robust state management to ensure decisions remain consistent with the accumulated context of the system.

***

## Infographic

![](./infographic.png)
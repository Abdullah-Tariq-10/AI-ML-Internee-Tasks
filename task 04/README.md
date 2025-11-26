# AI/ML Internee Tasks (1-6)

# Task 4: General Health Query Chatbot (API-Based)

## 📌 Overview
This project builds a specialized conversational agent designed to answer general health questions safely and informatively. Instead of training a model from scratch, it leverages the power of the **Mistral-7B-Instruct** model via the **Hugging Face Inference API**. The core focus of this task is **Prompt Engineering**: crafting a robust system prompt that enforces a specific persona ("HealthBot"), tone, and strict safety guidelines.

## 🎯 Objectives
* **API Integration:** Connect to a Large Language Model (LLM) using the Hugging Face API.
* **Prompt Engineering:** Design a system prompt that defines the bot's behavior, including a friendly persona and mandatory disclaimers.
* **Safety Filters:** Implement rules to prevent the bot from diagnosing conditions, prescribing medications, or giving harmful advice.
* **Contextual Response:** Ensure the bot handles general health queries (e.g., "What causes a sore throat?") differently from emergency situations (e.g., "I have chest pain").

## 🛠️ Technologies Used
* **Python 3.x**
* **Hugging Face Hub (`huggingface_hub`):** The official client library for interacting with the Inference API.
* **Mistral-7B-Instruct-v0.2:** An open-source, instruction-tuned LLM known for high-quality dialogue generation.

## 🧩 Key Implementation Details

### 1. System Prompt Design
The heart of this chatbot is the `SYSTEM_PROMPT` variable. It instructs the model to:
* **Act as "HealthBot":** Friendly, calm, and knowledgeable.
* **Follow Safety Rules:**
    * **NO Diagnosis:** Never confirm a specific condition.
    * **NO Prescriptions:** Describe medications generally, but never recommend dosages.
    * **Emergency Protocol:** Immediately direct users to emergency services (1122/911) if symptoms like chest pain or fainting are detected.
* **Mandatory Disclaimer:** Append a specific medical disclaimer to *every* response.

### 2. API Integration
The script uses the `InferenceClient` to send messages to the Mistral model. This allows for a lightweight implementation that runs in any environment without needing a local GPU.

### 3. Robust Testing
The solution includes a comprehensive test suite covering:
* **Symptom Checks:** ("Why do I get headaches?")
* **Medicine Info:** ("What is ibuprofen used for?")
* **Lifestyle Advice:** ("How to boost immunity?")
* **Safety/Emergency Checks:** ("I can't breathe") - *Crucial for verifying safety filters.*

## 🚀 How to Run
1.  **Install Dependencies:**
    ```bash
    pip install huggingface_hub
    ```
2.  **Get an API Token:** You will need a free User Access Token from your [Hugging Face Settings](https://huggingface.co/settings/tokens).
3.  **Configure & Run:**
    * Open `healthQuery_chatbot_task_4.ipynb`.
    * Paste your token into the `API_TOKEN` variable.
    * Run the notebook cells to initialize the client and test the bot.
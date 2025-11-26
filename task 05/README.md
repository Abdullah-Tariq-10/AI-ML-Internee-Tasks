# AI/ML Internee Tasks (1-6)

#  Mental Health Support Chatbot (Fine-Tuned LLM)

## 📌 Task Objective
The goal of this project was to build and fine-tune a **supportive, empathetic AI chatbot** capable of providing emotional wellness support. Unlike standard chatbots that simply answer questions, this model was trained to prioritize **active listening, validation, and safety**.

**Key Goals:**
* Fine-tune a "Small Language Model" (SLM) on real human dialogues to learn empathy.
* Prevent "toxic positivity" and "negative bonding" (where the bot complains about itself).
* Implement robust **Safety Guardrails** to detect and handle crisis situations (e.g., self-harm) responsibly.

---

## 📂 Dataset Used
* **Source:** [EmpatheticDialogues (Facebook AI)](https://www.kaggle.com/datasets/atharvjairath/empathetic-dialogues-facebook-ai)
* **File:** `emotion-emotion_69k.csv`
* **Structure:** The dataset contains conversations grounded in specific emotional situations (e.g., anxiety, pride, sadness).
* **Preprocessing:**
    * **Cleaning:** Removed "Customer/Agent" formatting artifacts specific to the raw CSV file.
    * **Quality Filter:** Filtered out low-quality responses (e.g., extremely short replies < 15 characters like "Ok" or "What?") to prevent the model from learning lazy conversational habits.
    * **Formatting:** Converted data into the **ChatML** structure (`System` $\rightarrow$ `User` $\rightarrow$ `Assistant`) for instruction tuning.

---

## 🤖 Models & Techniques Applied

### 1. Base Model
* **Model:** `Qwen/Qwen2.5-1.5B-Instruct`
* **Reasoning:** Selected for its high reasoning capability relative to its small size (1.5B parameters). This allowed for efficient fine-tuning on free-tier GPUs (Google Colab T4) while maintaining better conversational coherence than older models like DistilGPT2.

### 2. Fine-Tuning Technique
* **Method:** **QLoRA** (Quantized Low-Rank Adaptation).
* **Configuration:**
    * **Precision:** 4-bit Quantization (via `bitsandbytes`) for memory efficiency.
    * **LoRA Rank (r):** 16
    * **LoRA Alpha:** 32
    * **Target Modules:** `q_proj`, `v_proj` (Attention layers).
    * **Frameworks:** Hugging Face `transformers`, `peft`, `trl`.

### 3. Safety Engineering
* **Python-Level Guardrails:** Implemented a pre-generation check that intercepts crisis keywords (e.g., "suicide", "hurt myself") and returns a hard-coded safety message with helpline resources.
* **System Prompt Engineering:** Designed a "Listener" persona to force the model to ask open-ended questions and validate feelings rather than giving unsolicited or generic advice.

---

## 📊 Key Results & Findings

### 1. Training Performance
* The model successfully converged over **200 steps** of training.
* The fine-tuning shifted the model's tone from a "Generic Assistant" to a "Supportive Friend."

### 2. Behavioral Improvements
| Feature | Before Fine-Tuning / Optimization | After Fine-Tuning + Guardrails |
| :--- | :--- | :--- |
| **Response Style** | Generic, robotic, or overly advice-heavy. | Validation-focused ("That must be hard"). Asks gentle follow-up questions. |
| **Hallucinations** | Would make up stories (e.g., "I'm on a diet to fit into my jeans"). | **Eliminated.** Stays focused on the user's context. |
| **Negative Bonding** | "I'm going to fail my exam too." (Unhelpful commiseration). | "Oh no! Why do you feel unprepared?" (Supportive inquiry). |
| **Safety** | Treated "suicide" as a normal sad topic. | **Immediate Intervention:** Blocks generation and provides helpline links. |

### 3. Challenges Overcome
* **Dataset Noise:** The raw dataset contained many casual/lazy responses. Filtering for length (>15 chars) significantly improved response quality.
* **Toxic Positivity:** The model initially gave empty platitudes ("You have lots of friends!"). A restrictive System Prompt ("Do not give advice") corrected this behavior.

---

## 🚀 How to Run
The project is delivered as a **Jupyter Notebook (`.ipynb`)**.

1.  Open the notebook in **Google Colab** (GPU Required).
2.  Upload the dataset file: `emotion-emotion_69k.csv`.
3.  Run all cells to:
    * Install dependencies (`peft`, `trl`, `bitsandbytes`).
    * Fine-tune the QLoRA adapter.
    * Launch the interactive chat loop with safety guardrails.

---

### 📜 License
This project utilizes the `Qwen 2.5` model and the `EmpatheticDialogues` dataset, both open for research and non-commercial use.
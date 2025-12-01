# Assignment 6 – Prompt Engineering for Performance Improvement  
**Student:** *Kyle Kitching*  
**Course:** AD311  
**Model Used:** Google Gemini 2.5 Flash (via google-genai Python SDK)  
**Repository:** AI-ML-Assignment-6-Prompt-Engineering  

---

## 🎯 Project Overview

The goal of this assignment is to demonstrate how **prompt engineering** improves a Large Language Model’s (LLM) performance.  
I selected the task of **structured data extraction** from a messy, unstructured text review.  

**Constant Input Used for All Tests:**

```
I went to Joe’s Pizza last Friday. The slice was $3.50 and honestly it tasted burnt.
My friend Sarah paid $4.25 for a soda. I might go back on March 5th, 2025.
```

The objective was to extract:

- Restaurant name  
- Items purchased  
- Item prices  
- Date mentioned  

All prompts were run using the **Gemini 2.5 Flash** model.

---

## 📊 Summary of Prompt Performance

Below is the comparison of all five prompts, based on qualitative evaluation:  
(Scored from **1–10**, where 10 = highest performance)

| Prompt Type | Technique Used | Score | Observations |
|------------|----------------|-------|--------------|
| **Baseline** | None | **2** | Output was messy and unstructured, no clear fields. |
| **Technique 1** | Role Prompting | **6** | AI extracted more relevant details but output was still natural language, not structured. |
| **Technique 2** | Output Formatting / JSON | **8** | Produced valid JSON, but occasionally missed one field or slightly misformatted a value. |
| **Technique 3** | Chain-of-Thought | **9** | Model reasoned through the steps and produced accurate, complete JSON. Minor over-explaining. |
| **Final Optimized Prompt** | Combined Techniques (Role + Formatting + Hidden CoT) | **10** | Clean and consistent JSON only, complete extraction, no reasoning text leaked. |

---

## 🧠 Key Lessons Learned

Three insights stood out from this experiment:

1. **Role prompting increases internal alignment.**  
   Giving the model a professional role (Senior Data Analyst) immediately improved relevance and accuracy.

2. **Explicit output formatting is the single strongest technique.**  
   When the model was instructed to follow a strict JSON schema, its structure and consistency improved dramatically.

3. **Chain-of-thought reasoning boosts accuracy, but should be hidden in final output.**  
   CoT helped the model break down the reasoning steps, but in production, you want the reasoning invisible.  
   Combining *silent reasoning + strict formatting* created the strongest prompt.

Together, these techniques transformed a vague, low-quality baseline into a high-accuracy structured extraction system.

---

---

#API KEY
https://aistudio.google.com/u/2/api-keys

--

## 📁 Repository Structure

```
AI-ML-Assignment-6-Prompt-Engineering/
│
├── prompt_engineering.ipynb     # Notebook with all tests + outputs
├── README.md                    # This document
└── input_text.txt (optional)    # The constant input in plain text
```

---

## ▶️ Video Demonstration

https://youtu.be/tY7YLPDyC9A
---

## ✔ Environment Setup

This project uses Gemini via the **google-genai** Python library:

```bash
pip install google-genai
```

In Python:

```python
from google import genai
client = genai.Client(api_key="YOUR_KEY")
```

---

## ✔ Model Used

**Gemini 2.5 Flash** – chosen because it is:

- Fast and free  
- High reasoning accuracy  
- Fully supports complex generation and JSON formatting  

---

## ✔ Attribution

All work in this assignment, including code, explanations, and prompt designs, was created as part of AD331 / AI/ML coursework.  

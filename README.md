RAG vs Fine-Tuning for E-commerce Customer Support

 Project Overview

This project demonstrates a real-world GenAI system for automating **e-commerce customer support** by comparing two powerful approaches:

* Fine-Tuned Large Language Model (LLM)
* Retrieval-Augmented Generation (RAG)

The goal is to evaluate which approach performs better in handling **real customer queries** across accuracy, reliability, and scalability.

 Problem Statement

E-commerce platforms handle thousands of customer queries daily, including:

* Order tracking
* Refund and return policies
* Payment failures
* Delivery issues

Traditional LLMs often:

* Provide **generic responses**
* **Hallucinate** when specific data is missing

This project addresses these issues by comparing:

* **Fine-tuning (learning from data)**
* **RAG (retrieving real-time knowledge)**

---

 System Architecture

   Fine-Tuning Pipeline

1. Collected custom e-commerce support conversations
2. Formatted data in chat-style (`<|user|>`, `<|assistant|>`)
3. Fine-tuned **TinyLlama (1.1B)** using **LoRA (PEFT)**
4. Optimized for:

   * Tone (polite, helpful)
   * Structure (support-style responses)

---

  RAG Pipeline

1. Created a knowledge base using e-commerce policy documents (PDFs)
2. Split documents into chunks
3. Generated embeddings using sentence-transformers
4. Stored vectors in **ChromaDB**
5. Retrieved relevant context based on user query
6. Passed context to LLM for grounded response generation

---
## Model Information
This project uses a locally stored model. No external API calls are required for inference, enabling fully offline usage.
------------------------------

  Tech Stack

*  Transformers (Hugging Face)
*  PEFT (LoRA fine-tuning)
*  LangChain (RAG pipeline)
*  ChromaDB (vector database)
*  Sentence Transformers (embeddings)
*  Python (Google Colab)

---

 How It Works

1. User enters a query
2. System processes query in two ways:

   * Fine-tuned LLM (direct generation)
   * RAG (retrieve + generate)
3. Outputs are compared for:

   * Accuracy
   * Context-awareness
   * Reliability

---

 Fine-Tuning vs RAG Comparison

| Metric        | Fine-Tuning     | RAG                   |
| ------------- | --------------- | ----------------------- |
| Accuracy      | Medium          | High (context-based)    |
| Responses     | Generic         | Specific & grounded     |
| Hallucination | Possible        | Reduced                 |
| Cost          | High (training) | Lower                   |
| Scalability   | Limited         | High (just update data) |

---

 Sample Observations

* Fine-tuned model performs well for **general queries**
* RAG provides **precise answers using actual policy data**
* RAG significantly reduces hallucination
* Performance depends heavily on **quality of knowledge base**

---


 Limitations

* Limited dataset used for fine-tuning
* Small model (TinyLlama 1.1B) restricts response quality
* RAG accuracy depends on completeness of documents
* Some edge cases may still produce incomplete responses

---

 Key Insights

* Fine-tuning improves **response style and tone**
* RAG improves **factual accuracy**
* Best real-world systems combine **Fine-Tuning + RAG**

---

 Project Structure

```
├── notebooks/
│   └── ecommerce_rag_finetune.ipynb
|   └── model_comparison.md
├── data/
├── README.md
├── requirements.txt
```

---

 How to Run

1. Clone the repository
2. Install dependencies:

   ```
   pip install -r requirements.txt
   ```
3. Open the notebook in Google Colab / VS Code
4. Run cells step-by-step

---

 Note

The trained Fine-Tuned model is available and saved locally on the machine, but due to size constraints, it is not pushed to this GitHub repository.
If you are pulling this repo elsewhere, the model can be recreated by running the provided notebook.

---

 Future Improvements

* Deploy as a web app (Streamlit)
* Use larger models (Mistral, LLaMA 3)
* Improve knowledge base coverage
* Add real-time API integration

---

  Conclusion

This project highlights a critical insight in modern GenAI systems:

> Fine-tuning teaches the model *how to speak*,
> RAG teaches the model *what to say*.

** These are the commparison for both Rag and Fine tuning **

<img width="922" height="470" alt="image" src="https://github.com/user-attachments/assets/05702c6b-7f46-4c5a-a1d2-1ca49e19c0dd" />




<img width="1027" height="439" alt="image" src="https://github.com/user-attachments/assets/3f13b744-f11a-4034-a2d6-ddabb1f0d300" />


---

 Contact

If you’d like to discuss this project or collaborate, feel free to connect!

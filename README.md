# IPO-Sentiment-Analyzer
A fine-tuned NLP model that classifies IPO-related text — headlines, news snippets, and retail investor reactions — as Bullish, Bearish, or Neutral.# IPO Sentiment Analyzer

A fine-tuned NLP model that classifies IPO-related text — headlines, news snippets, and retail investor reactions — as **Bullish**, **Bearish**, or **Neutral**.

Built as part of **Day 10 of 30 Days of AI Engineering**.

---

## 🚀 Live Demo

Try the model live on Hugging Face Spaces:
**[https://huggingface.co/spaces/GSMS-B/ipo-related-sentences-sentiment-analyzer](https://huggingface.co/spaces/GSMS-B/ipo-related-sentences-sentiment-analyzer)**

---

## 📌 What This Project Does

Given any sentence about an IPO — a news headline, a social media reaction, a financial commentary — the model predicts the sentiment expressed:

| Label | Meaning |
|-------|---------|
| **Bullish** | Positive sentiment — optimism, strong demand, good fundamentals |
| **Bearish** | Negative sentiment — concern, overvaluation, weak outlook |
| **Neutral** | Balanced or factual — no clear directional sentiment |

### Example Inputs

```
"Strong GMP, oversubscribed 200x, applying full amount."
→ Bullish (high confidence)

"Avoid this IPO completely — overpriced with no moat."
→ Bearish (high confidence)

"IPO opens tomorrow, price band set at ₹400–420."
→ Neutral
```

---

## 🧠 Model Architecture

- **Base model:** [ProsusAI/finbert](https://huggingface.co/ProsusAI/finbert) — a BERT model pre-trained on financial text
- **Fine-tuning method:** LoRA (Low-Rank Adaptation) via PEFT — only ~900K parameters trained out of 110M
- **Classification head:** 3-class sequence classification (Bullish / Bearish / Neutral)
- **Training hardware:** Google Colab free tier (T4 GPU)

---

## 📊 Dataset

No public dataset existed for this specific task, so both datasets were created from scratch using synthetic data generation.

### Dataset 1 — Base Training Set
- 900 sentences total
- 300 Bullish, 300 Bearish, 300 Neutral
- Written to resemble IPO headlines, financial news snippets, and retail investor reactions on social media
- Covers Indian market vocabulary: GMP, QIB quota, OFS component, oversubscription ratios, SEBI, promoter holding, etc.

### Dataset 2 — Continual Fine-Tuning Set
- 250 sentences focused on edge cases
- Sarcastic sentences, contrast-heavy language, and irony
- Examples like: sentences with negative wording but positive overall sentiment, and vice versa
- Used for a second round of fine-tuning on top of the base model to improve robustness

---

## 🗂️ Repository Structure

```
ipo-sentiment-analyzer/
│
├── ipo_sentiment_analyzer.ipynb   # Full training notebook (Colab-ready)
├── ipo_sentiment_data.csv               # 900-row base training dataset
├── ipo_continual_finetune.csv         # 250-row continual fine-tuning dataset
└── README.md
```

---

## ⚙️ How to Run

Open the notebook directly in Google Colab:

1. Upload `ipo_sentiment_data.csv` and `ipo_continual_finetune.csv` to your Colab session
2. Run all cells in order — installs, data prep, tokenization, training, evaluation, and push to Hub
3. Set your Hugging Face token in the notebook where indicated

All training runs on the free Colab T4 GPU. Full fine-tuning takes approximately 15–20 minutes.

---


## 🔍 Known Limitations

- The model handles straightforward sentiment well but can still struggle with highly sarcastic or deeply ironic sentences
- Trained on synthetic data — real-world performance may vary on very colloquial or regional language


---

## 🛠️ Tech Stack

- [Hugging Face Transformers](https://huggingface.co/docs/transformers)
- [Hugging Face Datasets](https://huggingface.co/docs/datasets)
- [PEFT (Parameter-Efficient Fine-Tuning)](https://huggingface.co/docs/peft)
- [Hugging Face Spaces + Gradio](https://huggingface.co/spaces)
- Google Colab (free tier)
- Python, PyTorch

---

## 📅 Series Context

This project is part of the **30 Days of AI Engineering** series — building and shipping one AI project every day for 30 days.

- Day 9: Explored the Hugging Face ecosystem and identified libraries for this project
- **Day 10: Built, trained, and deployed this IPO sentiment analyzer end-to-end**

---

## 📬 Connect

Built by [GSMS_B] — feel free to open issues, suggest improvements, or fork and retrain on your own dataset.

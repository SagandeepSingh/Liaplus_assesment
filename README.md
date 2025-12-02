Liaplus Assessment Chatbot 

Author: Sagandeep Singh
Date: 02/12/25

1. Project Overview

This project implements an AI-powered Restaurant Feedback Chatbot capable of:

Statement-level sentiment analysis

Conversation-level sentiment summarisation

Issue/topic classification (Food Quality, Service, Ambience, Pricing, Other)

Sentiment trend visualisation

Automatic Excel export of full conversation logs

The system is modular, scalable, and runnable on Google Colab or local Python/Jupyter Notebook.

2. How to Run
Jupyter Notebook Setup

Install required libraries:

pip install transformers torch sentencepiece nltk pandas openpyxl matplotlib


Download VADER lexicon (if using fallback):

import nltk
nltk.download('vader_lexicon')


Run the notebook and execute the main chatbot loop.

3. Chosen Technologies

Transformer Model: nlptown/bert-base-multilingual-uncased-sentiment

Zero-shot Classifier: facebook/bart-large-mnli

Fallback Sentiment Engine: NLTK VADER

Data Handling: pandas DataFrame + Excel export

Plotting: matplotlib

Architecture: Python OOP + dataclasses

4. Explanation of Sentiment Logic
4.1 Transformer-based Sentiment

The transformer outputs ratings from 1–5 stars.

Mapping:

4–5 stars → Positive

3 stars → Neutral

1–2 stars → Negative

4.2 VADER Fallback Logic

VADER uses compound polarity score:

≥ 0.05 → Positive

≤ -0.05 → Negative

Otherwise → Neutral

5. Topic / Issue Classification Logic
5.1 Zero-shot Classification

Predicted topics:

Food Quality

Service

Ambience

Pricing

Other

If classifier confidence is below 0.3, the system falls back to keyword rules.

5.2 Keyword Fallback

Uses simple keyword maps to guarantee classification consistency even for unusual messages.

6. Status of Tier 2 Implementation

✔️ Statement-level analysis implemented

Timestamp

Sentiment

Issue

Detailed transformer/VADER raw outputs

✔️ Trend Plotting using matplotlib

✔️ Excel Export implemented

7. Test Examples
Example Interaction

User: “Your service disappoints me.”
→ Sentiment: Negative, Issue: Service

User: “Last experience was better.”
→ Sentiment: Positive, Issue: Service

User: “Food was too cold today.”
→ Sentiment: Negative, Issue: Food Quality

User: “Loved the ambience.”
→ Sentiment: Positive, Issue: Ambience

Overall Output Example
Overall Sentiment: Neutral / Mixed
Positive: 2
Negative: 2
Neutral: 0

8. Innovations and Additional Features

Dual sentiment engine (Transformer + VADER)

Zero-shot classification with fallback for accuracy

Statement-level + Conversation-level dual analysis

Sentiment trend visualization using encoded values (-1, 0, +1)

Export conversation log to Excel

Highly modular OOP architecture:

SentimentEngine, IssueClassifier, ConversationBot, TrendAnalyzer

9. Output Files Generated

restaurant_feedback_realistic.xlsx — Conversation dataset

Matplotlib sentiment trend plot

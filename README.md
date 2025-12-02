\documentclass[12pt]{article}
\usepackage[a4paper, margin=1in]{geometry}
\usepackage{titlesec}
\usepackage{hyperref}
\usepackage{setspace}
\usepackage{enumitem}

\title{\textbf{ Liaplus Assesment  Chatbot}\\Project Documentation}
\author{Sagandeep Singh}
\date{02/12/25}

\begin{document}
\maketitle
\onehalfspacing

\section*{1. Project Overview}
This project implements an AI-powered Restaurant Feedback Chatbot capable of:
\begin{itemize}
    \item Statement-level sentiment analysis
    \item Conversation-level sentiment summarisation
    \item Issue/topic classification (Food Quality, Service, Ambience, Pricing, Other)
    \item Sentiment trend visualisation
    \item Automatic Excel export of conversation records
\end{itemize}

The system is modular, production-style, and runs in Google Colab or local Python.

\section*{2. How to Run}



\subsection*{Jupyter Notebook}
\begin{verbatim}
pip install transformers torch sentencepiece nltk pandas openpyxl matplotlib
\end{verbatim}
Run the notebook and execute the main chatbot loop.

\section*{3. Chosen Technologies}
\begin{itemize}
    \item \textbf{Transformer Model:} nlptown/bert-base-multilingual-uncased-sentiment
    \item \textbf{Zero-shot Classifier:} facebook/bart-large-mnli
    \item \textbf{Fallback Sentiment Engine:} NLTK VADER
    \item \textbf{Data Handling:} pandas DataFrame + Excel export
    \item \textbf{Plotting:} matplotlib
    \item \textbf{Architecture:} Python OOP + dataclasses
\end{itemize}

\section*{4. Explanation of Sentiment Logic}

\subsection*{4.1 Transformer-based Sentiment}
The model outputs a rating from 1 to 5 stars.  
The mapping is:
\begin{itemize}
    \item 4--5 stars = Positive
    \item 3 stars = Neutral
    \item 1--2 stars = Negative
\end{itemize}

\subsection*{4.2 VADER Fallback Logic}
Uses compound polarity score:
\begin{itemize}
    \item $\geq 0.05$ = Positive
    \item $\leq -0.05$ = Negative
    \item otherwise = Neutral
\end{itemize}

\section*{5. Topic / Issue Classification Logic}

\subsection*{5.1 Zero-shot Classification}
The model predicts one of:
\begin{itemize}
    \item Food Quality
    \item Service
    \item Ambience
    \item Pricing
    \item Other
\end{itemize}

If the confidence is $<0.3$, keyword fallback is triggered.

\subsection*{5.2 Keyword Fallback}
Simple keyword dictionaries ensure consistent classification when zero-shot scores are low.

\section*{6. Status of Tier 2 Implementation}

\begin{itemize}
    \item \textbf{ implemented with timestamps, sentiment, issue, and details.
    \item \textbf{Trend Plotting:} Implemented using matplotlib.
    \item \textbf{Excel Export:} Implemented.
\end{itemize}

\section*{7. Test Examples}

\subsection*{Example Interaction}
\begin{description}[leftmargin=2cm]
    \item[User:] ``Your service disappoints me.''  
    Sentiment: Negative, Issue: Service

    \item[User:] ``Last experience was better.''  
    Sentiment: Positive, Issue: Service

    \item[User:] ``Food was too cold today.''  
    Sentiment: Negative, Issue: Food Quality

    \item[User:] ``Loved the ambience.''  
    Sentiment: Positive, Issue: Ambience
\end{description}

\subsection*{Overall Output Example}
\begin{verbatim}
Overall Sentiment: Neutral / Mixed
Positive: 2
Negative: 2
Neutral: 0
\end{verbatim}

\section*{8. Innovations and Additional Features}

\begin{itemize}
    \item Dual sentiment engine (Transformer + VADER fallback).
    \item Zero-shot issue detection with keyword fallback for robustness.
    \item Statement-level + conversation-level dual analysis.
    \item Trend plotting using encoded sentiment values (-1, 0, +1).
    \item Automatic Excel export suitable for analytics or ML training.
    \item Modular OOP design: SentimentEngine, IssueClassifier, ConversationBot, TrendAnalyzer.
\end{itemize}

\section*{9. Output Files Generated}
\begin{itemize}
    \item \textbf{restaurant\_feedback\_realistic.xlsx} (Conversation log)
    \item Matplotlib trend plot (sentiment timeline)
\end{itemize}

\end{document}


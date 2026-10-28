# 📈 Meme Stock Sentiment Analyzer

**Meme Stock Sentiment Analyzer** is an AI-powered web application for sentiment analysis of **WallStreetBets** posts and meme stocks using **Large Language Models (LLMs)**.

The application classifies Reddit posts as **Positive**(bullish), **Negative**(bearish), or **Neutral**, identifies mentioned meme stocks, and displays real-time stock information through an interactive web interface.

---

## 🚀 Features

* 🤖 AI-powered sentiment analysis using GPT-5.4-mini
* 📊 Detects Bullish, Bearish, and Neutral market sentiment
* 💬 Understands WallStreetBets slang and financial terminology
* 🎯 Few-shot prompt engineering for improved classification
* 📈 Live stock prices powered by Yahoo Finance
* 📱 Modern and responsive web interface
* ⚡ Fast API backend with real-time predictions

---

## 🛠️ Tech Stack

### Backend

* Python
* FastAPI
* OpenAI API (GPT-5.4-mini)
* yfinance

### Frontend

* HTML
* CSS
* JavaScript

### AI Techniques

* Prompt Engineering
* Few-shot Prompting
* Rule-based Keyword Enhancement
* Financial Domain Adaptation

---

## 🧠 How It Works

1. A Reddit post is submitted through the web interface.
2. The application sends the post to an LLM with a carefully designed system prompt.
3. Few-shot examples help the model understand financial slang, sarcasm, and WallStreetBets terminology.
4. The response is combined with rule-based keyword analysis.
5. The application displays:

   * Sentiment (Bullish / Bearish / Neutral)
   * Mentioned stock ticker
   * Confidence score
   * Current market price

---

## 📊 Model Performance

The final system achieved an overall **92.4% classification accuracy** on the evaluation datasets.


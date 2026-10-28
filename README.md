# 📈 MemeStocksSurgen

**AI-powered sentiment classifier for WallStreetBets posts and meme stocks**

This project classifies Reddit r/WallStreetBets posts as **Positive** (bullish), **Negative** (bearish), or **Neutral** using a hybrid approach:

- GPT-5.4-mini with carefully crafted system prompt
- Few-shot examples tailored to WSB slang and sarcasm
- Rule-based keyword signals (bullish/bearish meme language)
- Flair-based overrides with special handling for short positions

It also extracts mentioned tickers and provides live stock data via Yahoo Finance.

---

## Features

- Single-post and batch (DataFrame) classification
- Automatic `$TICKER` extraction
- Understanding of WSB slang, memes, sarcasm and irony
- Correct treatment of profitable puts/shorts as **Negative**
- Live stock prices, company info and historical data (`yfinance`)
- Pre-labeled dataset included (`wsb_labeled.csv`)
- Helper functions for sentiment summaries and top tickers

---

## Installation

```bash
git clone https://github.com/n0rtx/MemeStocksSurgen.git
cd MemeStocksSurgen
pip install -r requirements.txt
```

Set your OpenAI API key:

```bash
export OPENAI_API_KEY="your-api-key"
```

---

## Usage

### Classify a single post

```python
from meme_stock_classifier import classify_post
from openai import OpenAI

client = OpenAI()

result = classify_post(
    "Bought GME calls last week, diamond hands 💎🙌 to the moon 🚀",
    client=client
)
print(result)
```

### Classify a DataFrame

```python
from meme_stock_classifier import classify_dataframe, load_labeled_data

df = load_labeled_data()
classified = classify_dataframe(df, client=client)
```

### Sentiment summary & top tickers

```python
from meme_stock_classifier import get_sentiment_summary, get_top_tickers

summary = get_sentiment_summary(classified)
top = get_top_tickers(classified, n=10)
```

### Stock data

```python
from stock_data import get_stock_info, get_price_history, get_multi_ticker_summary

info = get_stock_info("GME")
history = get_price_history("GME", period="3mo")
summary = get_multi_ticker_summary(["GME", "AMC", "NVDA"])
```

---

## Project Structure

```
MemeStocksSurgen/
├── meme_stock_classifier.py   # Core classification logic
├── stock_data.py              # Yahoo Finance utilities
├── model_setup.py             # Path & config helper
├── model_config.json          # Optional Hugging Face config
├── wsb_labeled.csv            # Pre-labeled WSB dataset
├── ticker_prices.csv          # Ticker price snapshot
├── requirements.txt
└── README.md
```

---

## How Classification Works

1. If the post has a clear flair (`Gain` / `Loss`) — use it (with override for short positions).
2. Detect strong bullish/bearish WSB keywords and pass them as context.
3. Build a few-shot prompt with carefully selected examples.
4. Send to GPT-5.4-mini (temperature=0).
5. Extract ticker with regex (`$TICKER`).

The system focuses strictly on **expected price direction**, not the poster’s emotion or profit.

---

## License

MIT License
```

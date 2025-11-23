# 📈 Stock Market News Sentiment Analysis & Price Correlation

**Week 1 – EDA & NLP Project**

This project analyzes **financial news headlines**, extracts **sentiment**, and explores how sentiment relates to **stock price movements**. It includes exploratory data analysis (EDA), text cleaning, sentiment scoring, technical indicators, and a sentiment-price correlation workflow.

---

## 🚀 **Project Objectives**

* Perform **EDA** on stock-related news data
* Clean and preprocess text for NLP tasks
* Compute **sentiment scores** using VADER
* Ingest historical stock price data via **yfinance**
* Generate at least one **technical indicator** (SMA, RSI, etc.)
* Merge news sentiment with stock price
* Compute and visualize **sentiment–price correlations**
* Structure project using a proper `src/` module
* Include modular functions with docstrings and version-controlled workflow

---

## 📂 **Project Structure**

```
project/
│
├── data/
│   ├── raw/               # Original CSV files
│   ├── processed/         # Cleaned datasets
│
├── notebooks/             # EDA, experimentation
│
├── src/
│   ├── __init__.py
│   ├── data_ingestion.py  # Load & download stock prices
│   ├── preprocessing.py   # Text cleaning, preprocessing
│   ├── sentiment.py       # Sentiment scoring functions
│   ├── technicals.py      # Technical indicators (SMA, RSI)
│   ├── correlation.py     # Merge + correlation workflow
│
├── main.py                # End-to-end pipeline
├── README.md
├── requirements.txt
```

---

**Installation & Setup**

### Clone repository


git clone <repo-url>
cd project


### Install dependencies


pip install -r requirements.txt


### Download NLTK resources

```python
import nltk
nltk.download("punkt")
nltk.download("stopwords")
nltk.download("wordnet")
nltk.download("vader_lexicon")
```

---

**Data Sources**

### **News Data**

Uploaded CSV of financial news headlines containing:

* headline
* url
* publisher
* date
* stock ticker

### **Stock Price Data**

Pulled programmatically using:

```python
import yfinance as yf
yf.download("AAPL", start="2020-01-01", end="2020-12-31")
```

---

**Text Preprocessing**

Located in `src/preprocessing.py`:

* lowercasing
* tokenization
* stopword removal
* lemmatization
* final cleaned text output

Each function includes full docstrings.

---

 **Sentiment Analysis**

Using **VADER SentimentIntensityAnalyzer**:

```python
df['sentiment'] = sia.polarity_scores(df['cleaned'])['compound']
```

---

## 📈 **Technical Indicators**

At least one indicator (SMA) is implemented:

```python
df['SMA_14'] = df['Close'].rolling(14).mean()
```

Additional indicators such as RSI or MACD can be added in `src/technicals.py`.

---

 **Merging Sentiment & Stock Prices**

News date is matched with stock’s trading date.

```python
merged = pd.merge(news, stock, left_on="date", right_on="Date")
```

---

 **Correlation Workflow**

Located in `src/correlation.py`:

* Merge sentiment with price
* Compute Pearson correlation
* Produce scatter plots & time-series visualizations

```python
corr = merged['sentiment'].corr(merged['Close'])
print("Correlation:", corr)
```

---

 **How to Run the Full Pipeline**


python main.py


This script:

1. Loads news data
2. Cleans text
3. Computes sentiment
4. Downloads stock price
5. Generates technical indicators
6. Merges datasets
7. Outputs correlation & visualizations

---

 **Example Outputs**

* Sentiment distribution plot
* Stock price over time
* SMA overlay plot
* Sentiment vs. Close price scatter
* Correlation score

---

 **Future Improvements**

* Add more NLP features (TF-IDF, embeddings)
* Expand to multiple tickers
* Improve model prediction pipeline
* Add backtesting for trading signals

---

 **License**

This project is for educational purposes.

---

If you want, I can also **generate main.py**, all **src files**, or **write your docstrings automatically**.

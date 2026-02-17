# News Trading Agent

A CLI tool that fetches recent financial headlines for a stock ticker, scores their sentiment using Claude, and outputs a **BUY / SELL / HOLD** recommendation.

## How It Works

1. **Fetch headlines** — Pulls up to 10 recent English-language headlines from [NewsAPI](https://newsapi.org)
2. **Score sentiment** — Sends each headline to Claude (Sonnet) to classify as bullish, bearish, or neutral
3. **Aggregate** — Computes an average sentiment score from -1.00 to +1.00
4. **Recommend** — Maps the score to a trading signal: BUY (>= 0.3), SELL (<= -0.3), or HOLD

## Setup

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Configure API keys

Create a `.env` file in the project root:

```
NEWSAPI_KEY=your_newsapi_key
ANTHROPIC_API_KEY=your_anthropic_key
```

- Get a NewsAPI key at [newsapi.org](https://newsapi.org)
- Get an Anthropic API key at [console.anthropic.com](https://console.anthropic.com)

## Usage

```bash
python main.py <TICKER>
```

Example:

```bash
python main.py AAPL
```

### Sample Output

```
Fetching headlines for AAPL...
Found 10 headline(s).

[1/10] Analysing: Apple (AAPL)'s A Free Rider, Says Jim Cramer
         [+] BULLISH — Jim Cramer's comment implies Apple benefits from favorable conditions.
...

============================================================
  Ticker:       AAPL
  Headlines:    10 analysed
  Bullish:      1
  Bearish:      0
  Neutral:      9
  Avg Score:    +0.10  (range -1.00 to +1.00)
  Signal:       HOLD
============================================================
```

## Disclaimer

This tool is for educational purposes only. It is not financial advice. Always do your own research before making investment decisions.

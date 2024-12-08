# InStock-EN: Stock Market Analysis System

InStock-EN is a comprehensive stock market analysis and trading system that captures daily stock and ETF data, calculates various technical indicators, identifies chart patterns, provides integrated stock screening, and includes multiple built-in trading strategies. The system supports backtesting, automated trading, and batch processing. It runs efficiently and is accessible on PC, tablet, and mobile devices.

## Key Features

### 1. Comprehensive Stock Screening
The system supports over 200 screening criteria across multiple categories:

- Market Scope: Markets, industries, regions, concepts, styles, index components, listing date
- Fundamentals: Valuation metrics, per-share indicators, profitability, growth potential, capital structure
- Technical Analysis: MACD crossovers, KDJ crossovers, volume breakouts, money flow indicators
- Market Sentiment: Announcements, institutional coverage, shareholding changes
- Trading Metrics: Price performance, trading volume, capital flows, market statistics

### 2. Daily Market Data
- Daily stock prices and metrics
- Capital flow analysis
- Dividend and distribution data
- Major trader activities
- Block trades
- Fundamental data
- Industry and concept fund flows
- Daily ETF data

### 3. Technical Indicators
The system calculates over 30 technical indicators including:
- MACD, KDJ, BOLL, TRIX
- RSI, VR, ROC, DMI
- CCI, ATR, OBV, SAR
- And many more...

### 4. Pattern Recognition
Identifies 61 different chart patterns with buy/sell signals.

### 5. Trading Strategies
Built-in strategies include:
- Volume breakout
- Platform breakout
- Moving average trends
- Turtle trading rules
- Low ATR growth
- Fundamental screening

### 6. Backtesting
Comprehensive backtesting system to verify indicator and strategy effectiveness.

### 7. Automated Trading
Supports automated trading with built-in IPO subscription strategy.

## Installation

### Prerequisites
- Python 3.11 or later
- MySQL/MariaDB
- TA-Lib
- Required Python packages (see requirements.txt)

### Standard Installation
1. Install Python 3.11+
2. Install MySQL/MariaDB
3. Install dependencies: `pip install -r requirements.txt`
4. Install TA-Lib
5. Configure database settings
6. Run the system

### Docker Installation
```bash
# Run database service
docker run -d --name InStockDbService \
    -v /data/mariadb/data:/var/lib/instockdb \
    -e MYSQL_ROOT_PASSWORD=root \
    library/mariadb:latest

# Run InStock service
docker run -dit --name InStock --link=InStockDbService \
    -p 9988:9988 \
    -e db_host=InStockDbService \
    mayanghua/instock-en:latest
```

## Usage

### 1. Data Processing
```bash
# Run data processing jobs
python execute_daily_job.py  # Current date
python execute_daily_job.py 2024-01-01  # Specific date
python execute_daily_job.py 2024-01-01,2024-01-02  # Multiple dates
python execute_daily_job.py 2024-01-01 2024-01-31  # Date range
```

### 2. Web Interface
Access the web interface at http://localhost:9988 after starting the web service.

### 3. Automated Trading
Configure trading settings in trade_client.json and start the trading service.

## Development

### Project Structure
```
instock-en/
├── src/
│   ├── data/        # Data collection and processing
│   ├── analysis/    # Technical analysis and strategies
│   ├── web/         # Web interface
│   ├── trading/     # Trading functionality
│   └── utils/       # Utility functions
├── scripts/         # Running scripts
└── docs/           # Documentation
```

### Contributing
1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## Disclaimer

This system is for educational and analysis purposes only. Stock market investment carries risk, and this system does not guarantee any returns. Users are responsible for their own investment decisions.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
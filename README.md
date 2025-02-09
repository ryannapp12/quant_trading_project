# Advanced Quantitative Trading Engine

A production-grade quantitative trading engine featuring sophisticated statistical arbitrage, advanced risk analytics, and real-time strategy visualization. Built with modern best practices, this engine demonstrates institutional-quality architecture and analysis capabilities.

## Key Features

### Advanced Trading Strategies
- **Statistical Arbitrage:** Implements pairs trading with dynamic hedge ratios and cointegration testing
- **Mean Reversion:** Adaptive thresholds with position sizing
- **Momentum:** Trend-following with optimized lookback periods
- **Portfolio Optimization:** Modern portfolio theory implementation with custom constraints

### Sophisticated Analytics
- **Advanced Risk Metrics:** 
  - Value at Risk (VaR) with multiple calculation methods
  - Conditional VaR (Expected Shortfall)
  - Extreme Value Theory (EVT) for tail risk
  - Dynamic drawdown analysis with recovery metrics
- **Factor Analysis:**
  - Multi-factor exposure calculation
  - Dynamic beta estimation
  - R-squared analytics
- **Statistical Tests:**
  - Cointegration testing with ADF
  - Half-life calculation for mean reversion
  - Rolling correlation analysis

### Enhanced Visualization
- **Interactive Performance Dashboards:**
  - Strategy return comparisons
  - Risk metric visualization
  - Drawdown analysis
- **Pair Trading Analytics:**
  - Spread visualization
  - Rolling correlation plots
  - Returns scatter analysis
  - Normalized price series comparison

### Technical Architecture
- **Robust Data Management:**
  - SQLite-based market data caching
  - Multiple data provider support (Yahoo Finance, CSV)
  - Efficient data preprocessing and alignment
- **Concurrent Processing:**
  - Parallel strategy backtesting
  - Thread-safe data handling
  - Optimized computation engine
- **Production-Ready Features:**
  - Comprehensive logging system
  - Performance profiling decorators
  - Error handling and recovery
  - Modular, extensible design

## Project Structure

```
quant_trading_project/
├── config/
│   └── settings.py              # Configuration parameters
├── data/
│   └── market_data.db          # SQLite database (auto-generated)
├── src/
│   ├── core/
│   │   ├── backtesting_engine.py    # Parallel backtesting engine
│   │   ├── data_provider.py         # Abstract data provider interface
│   │   ├── csv_data_provider.py     # CSV data handler
│   │   ├── portfolio_optimizer.py    # Portfolio optimization engine
│   │   ├── risk_engine.py           # Enhanced risk analytics
│   │   └── models.py                # Data models and types
│   ├── strategies/
│   │   ├── base_strategy.py         # Strategy interface
│   │   ├── momentum_strategy.py     # Momentum implementation
│   │   ├── mean_reversion_strategy.py # Mean reversion logic
│   │   └── statistical_arbitrage.py  # Stat arb implementation
│   └── utils/
│       ├── logger.py                # Logging configuration
│       └── decorators.py            # Performance monitoring
├── main.py                     # Application entry point
├── requirements.txt            # Dependencies
└── README.md
```

## Installation

### 1. Clone the Repository
```bash
git clone https://github.com/ryannapp12/quant_trading_project.git
cd quant_trading_project
```

### 2. Create Virtual Environment
```bash
python -m venv venv

# Windows:
venv\Scripts\activate

# macOS/Linux:
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

## Usage Examples

### Basic Backtesting
```python
from src.core.data_provider import YahooDataProvider
from src.strategies.momentum_strategy import MomentumStrategy

# Initialize data provider
provider = YahooDataProvider("AAPL", "2020-01-01", "2024-01-01")
data = provider.load_data()

# Create and run strategy
strategy = MomentumStrategy(window=20)
results = strategy.backtest(data)
```

### Statistical Arbitrage
```python
from src.strategies.statistical_arbitrage import StatisticalArbitrageStrategy

# Create pairs trading strategy
stat_arb = StatisticalArbitrageStrategy(
    lookback_period=20,
    entry_zscore=1.5,
    exit_zscore=0.5
)

# Add benchmark data
data['benchmark_close'] = benchmark_data['close']

# Run backtest
results = stat_arb.backtest(data)
```

## Performance Analysis

### Risk Metrics
```python
from src.core.risk_engine import RiskEngine

risk = RiskEngine(results)
tail_metrics = risk.calculate_tail_risk_metrics()
drawdown_metrics = risk.calculate_drawdown_metrics()
```

### Visualization
```python
# Plot performance comparison
plot_pair_analysis(data, "AAPL-QQQ")

# Display strategy results
plt.figure(figsize=(15, 7))
plt.plot(results.index, results['cumulative_strategy'])
plt.show()
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---
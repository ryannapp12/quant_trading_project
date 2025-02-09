# Quantitative Trading Engine

A state-of-the-art quantitative trading engine demonstrating a modular, scalable, and highly optimized architecture.

## Features

- **Data Caching:** Efficient market data retrieval using SQLite
- **Abstract Strategy Pattern:** Easily extendable to add new trading strategies
- **Concurrent Backtesting:** Runs multiple strategies in parallel using ThreadPoolExecutor
- **Advanced Risk Analysis:** Calculates Sharpe Ratio, Sortino Ratio, Maximum Drawdown, and Value at Risk (VaR)
- **Utility Decorators & Logging:** Built-in execution time measurement and comprehensive logging for observability

## Project Structure

```
quant_trading_project/
├── config/
│   └── settings.py
├── data/
│   └── market_data.db  # (Generated automatically)
├── src/
│   ├── core/
│   │   ├── backtesting_engine.py
│   │   ├── data_provider.py
│   │   ├── risk_engine.py
│   │   └── models.py
│   ├── strategies/
│   │   ├── base_strategy.py
│   │   └── momentum_strategy.py
│   └── utils/
│       ├── logger.py
│       └── decorators.py
├── main.py
├── requirements.txt
└── README.md
```

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/ryannapp12/quant_trading_project.git
cd quant_trading_project
```

### 2. Create and Activate a Virtual Environment

```bash
python -m venv venv

# On Windows:
venv\Scripts\activate

# On macOS/Linux:
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Open the Project in VSCode

- Open VSCode and select File > Open Folder… to open the quant_trading_project folder
- (Optional) Create a .vscode folder with settings.json and launch.json to configure the Python interpreter and debugging

```json
# .vscode/launch.json
{
    "version": "0.2.0",
    "configurations": [
      {
        "name": "Python: Run main.py",
        "type": "debugpy",
        "request": "launch",
        "program": "${workspaceFolder}/main.py",
        "console": "integratedTerminal"
      }
    ]
  }
```
```json
# .vscode/settings.json
{
    "python.pythonPath": "venv/bin/python", // Adjust path for Windows if necessary
    "python.linting.enabled": true,
    "python.linting.pylintEnabled": true,
    "python.formatting.provider": "autopep8",
    "editor.formatOnSave": true
  }
```
```json
# .vscode/tasks.json
{
    "version": "2.0.0",
    "tasks": [
      {
        "label": "Run main.py",
        "type": "shell",
        "command": "python main.py",
        "group": {
          "kind": "build",
          "isDefault": true
        },
        "problemMatcher": []
      }
    ]
  }
```

### 5. Run the Project

```bash
python main.py
```

## Extending the Project

### Add New Strategies
Create additional strategy modules in `src/strategies/` by inheriting from `BaseStrategy`.

### Enhance Risk Metrics
Extend `RiskEngine` in `src/core/risk_engine.py` with further analytical metrics.

### Improve Data Handling
Customize `YahooDataProvider` or add new providers by implementing the `DataProvider` interface.

## Additional Notes

### SQLite Database
The database file (`data/market_data.db`) is generated automatically when you run the project and cache the data. You do not need to create it manually.

### Extensibility
The modular design lets you add new strategies, extend risk metrics, or swap out data providers without modifying the core engine.

### Performance & Observability
Concurrency in the backtesting engine, custom decorators for timing, and a robust logging setup ensure that the project is high-performing and fully observable.
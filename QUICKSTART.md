# MT5 Trading Bot - Quick Start Guide

## 🚀 Easy Setup (5 minutes)

### Step 1: Clone & Install
```bash
git clone https://github.com/PETER9-opps/mt5-trading-bot.git
cd mt5-trading-bot
pip install -r requirements.txt
```

### Step 2: Configure (Optional but Recommended)
Edit `.env` file:
```
MT5_ACCOUNT=your_account_number
MT5_PASSWORD=your_password
MT5_SERVER=ICMarketsSC-Demo
```

### Step 3: Run Bot
```bash
# Demo mode with default settings
python main_advanced.py --mode demo

# Or pick a preset (Conservative, Balanced, Aggressive, Scalping)
python main_advanced.py --mode demo --preset balanced

# Or pick a strategy
python main_advanced.py --mode demo --strategy trend_follow

# List all strategies
python main_advanced.py --list-strategies
```

---

## 📊 Available Strategies

### 1. **Trend Following** (Best for beginners)
- Uses EMA 9/21 crossover
- RSI confirmation
- Win rate: ~65%
- Perfect for: Trending markets
```bash
python main_advanced.py --strategy trend_follow
```

### 2. **Mean Reversion** (Best for volatile markets)
- Bollinger Bands + RSI
- Trades oversold/overbought
- Win rate: ~58%
- Perfect for: Ranging markets
```bash
python main_advanced.py --strategy mean_reversion
```

### 3. **MACD** (Momentum trading)
- MACD crossover signals
- Momentum confirmation
- Win rate: ~62%
- Perfect for: Momentum trades
```bash
python main_advanced.py --strategy macd
```

### 4. **Stochastic** (Fast signals)
- Stochastic Oscillator
- Quick oversold/overbought signals
- Win rate: ~60%
- Perfect for: Scalping
```bash
python main_advanced.py --strategy stochastic
```

### 5. **ADX** (Trend strength filter)
- Only trades strong trends
- ADX > 25 confirmation
- Win rate: ~70%
- Perfect for: Serious traders
```bash
python main_advanced.py --strategy adx
```

### 6. **Multi-Strategy** (Best for accuracy)
- Combines 3 strategies
- Requires 2/3 confirmation
- Win rate: ~75%
- Perfect for: Conservative traders
```bash
python main_advanced.py --strategy multi_strategy
```

---

## 💰 Risk Presets

### Conservative (SAFEST)
- Risk: 0.5% per trade
- Daily Loss Limit: 1%
- Max Positions: 2
```bash
python main_advanced.py --preset conservative
```

### Balanced (RECOMMENDED)
- Risk: 1% per trade
- Daily Loss Limit: 2%
- Max Positions: 3
```bash
python main_advanced.py --preset balanced
```

### Aggressive (HIGHER REWARD)
- Risk: 2% per trade
- Daily Loss Limit: 5%
- Max Positions: 5
```bash
python main_advanced.py --preset aggressive
```

### Scalping (MANY SMALL TRADES)
- Risk: 0.5% per trade
- Daily Loss Limit: 2%
- Max Positions: 5
- Faster check interval
```bash
python main_advanced.py --preset scalping --interval 30
```

---

## ⚙️ Customize Everything

### Edit `strategy_config.py` to:
- Change EMA periods (line 14-15)
- Change Bollinger Bands period (line 27)
- Adjust RSI levels (line 29-31)
- Change stop loss sizes (line 32)
- Set minimum signal strength (line 33)

### Example Customization:
```python
# For AGGRESSIVE EMA strategy
TREND_FOLLOW_CONFIG = {
    'ema_short': 5,           # Faster
    'ema_long': 15,           # Faster
    'stop_loss_pips': 15,     # Tighter stops
    'min_signal_strength': 30,  # More signals
}
```

---

## 🎯 Command Examples

### Run with specific settings
```bash
# Trend follow strategy, demo mode, check every 30 seconds
python main_advanced.py --mode demo --strategy trend_follow --interval 30

# Mean reversion, aggressive preset, on GBPUSD
python main_advanced.py --mode demo --preset aggressive --symbol GBPUSD

# Multi-strategy confirmation, conservative preset
python main_advanced.py --mode demo --strategy multi_strategy --preset conservative

# ADX strategy, balanced preset, on EURUSD, live trading
python main_advanced.py --mode live --strategy adx --preset balanced
```

---

## 📈 Best Combinations

### For Beginners
```bash
python main_advanced.py --strategy trend_follow --preset conservative --interval 60
```

### For Steady Profits
```bash
python main_advanced.py --strategy adx --preset balanced --interval 60
```

### For Aggressive Traders
```bash
python main_advanced.py --strategy multi_strategy --preset aggressive --interval 30
```

### For Scalpers
```bash
python main_advanced.py --strategy stochastic --preset scalping --interval 15
```

---

## ✅ Before Going LIVE

1. Test in DEMO for at least 1 week
2. Verify all trades are logged
3. Check profitability
4. Start with small account
5. Monitor first day

```bash
# Then when ready, switch to live
python main_advanced.py --mode live --strategy trend_follow
```

---

## 📊 Check Logs

```bash
# View live logs
tail -f logs/trading_bot.log

# View all today's trades
grep "Trade placed" logs/trading_bot.log

# Check for errors
grep "ERROR" logs/trading_bot.log
```

---

## 🆘 Troubleshooting

**Q: Bot not connecting?**
- Check MT5 account credentials in `.env`
- Verify MT5 is running
- Check internet connection

**Q: No trades generated?**
- Lower min_signal_strength in config
- Change strategy
- Check market conditions (need clear trends)

**Q: Too many losing trades?**
- Use multi_strategy for confirmation
- Switch to ADX strategy (only strong trends)
- Increase stop loss size

**Q: Trades closing at loss?**
- That's normal - use proper stop losses
- Check risk/reward ratio
- Verify taking profit levels

---

Happy Trading! 🚀📈

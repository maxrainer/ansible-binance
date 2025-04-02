# Ansible Binance Automation Trading

## Overview
Automation for crypto currency trading. 
Trading platform currently supported: binance.com
Relias on AI model prediction. Technical indicator prediction only. 
AI model project and REST API interface implementation in another project. 

## Trading Concept
mandatory values:
- ba_coin: BNB 
- ba_interval: 5 Minute (prediction AI model interval)
- ba_usd: 10 (~ USD per sell and buy trade)

all limit variables are percentage values
1. Buy
   - buy as cheap as possible
   - avoid to raise the average value
   - new average is calculated at every buy
   - only under or close to average (clearance variable: high_buy_limit)
   - only under or close to lowest price buy (clearance variable: best_buy_price_max_diff)
   - buy accelerator
     - takes action when low_accelerate_buy_limit under average value is reached
     - multiply ba_usd value by variable buy_multiplicator 
   - max USD buy limit per coin 
     - variable max_buy_usd
     - unlimited if 0
2. Sell
   - sell with profit only
   - sell above average value plus clearance 'low_sell_limit'
   - don't recalculate average after sell (to avoid less profit)
   - sell all coins when reaching 'high_sell_limit'
   - clear average after 'sell all'
   - clear average if nothing to sell
   
![Sell/Buy](https://github.com/maxrainer/ansible-binance/blob/main/images/automation_image1.jpg)

## Variables
```
# COIN:
ba_coin: BNB
ba_interval: 5 Minute
ba_usd: 10

# SELL
high_sell_limit: 1.0
low_sell_limit: 0.5

# BUY
# 0.3% above average, 0,3% above lowest price
max_buy_usd: 1000  
best_buy_price_max_diff: 0.3
low_accelerate_buy_limit: 4
buy_multiplicator: 2
high_buy_limit: 0.3
```
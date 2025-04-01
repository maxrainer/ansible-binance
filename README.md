# Ansible Binance Automation Trading

## Overview

## Trading Concept
1. Buy
   - buy as cheap as possible
   - new average is calculated at every buy
   - only under or close to average (clearance variable: high_buy_limit)
   - only under or close to lowest price buy (clearance variable: best_buy_price_max_diff)
2. Sell
   - (always) sell with profit
   - sell above average value plus clearance 'low_sell_limit'
   - don't recalculate average after sell
   - sell all coins when reaching 'high_sell_limit'
   - clear average after 'sell all'
   - clear average if nothing to sell
   
![Sell/Buy](https://github.com/maxrainer/ansible-binance/blob/main/images/automation_image1.jpg)

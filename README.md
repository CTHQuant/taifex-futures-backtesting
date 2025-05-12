#  TAIEX Futures Backtesting Project 台指期策略回測專案

本專案展示一個以 **台指期 (TXF)** 為標的的量化策略回測流程，涵蓋了資料蒐集、參數優化與績效評估，使用 Python 與 Jupyter Notebook 撰寫，並搭配 [Shioaji API by 永豐金證券](https://sinotrade.github.io/) 取得即時與歷史資料。
Train period: 2024/01/01~2024/12/31 
Test period: 2025/01/01~2025/05/05

---

## 專案內容

| Notebook 名稱 | 功能說明 |
|---------------|----------|
| `Backtesting_Data_collection.ipynb` | 抓取台指期 KBARS / TICKS 資料，處理每日交易資訊與前十大權值股走勢分析 |
| `Backtesting_Gridsearch.ipynb` | 對停利 / 停損參數進行 Grid Search，找出 Sharpe 與 PnL 最佳化區間 |
| `Backtesting_Result.ipynb` | 整合回測結果，輸出每筆交易紀錄、總績效統計與勝率、報酬風險比等指標 |

---

## 策略邏輯

- **進場邏輯**
  - 依據權值股 + 台積電 K 棒是否紅K
  - 內外盤比作為多空方向判斷
- **停損 / 停利邏輯**
  - 動態依成交量比等級設定 TP / SL 點數偏移
  - 持倉最大至收盤前自動平倉

---

## 環境需求

- Python 3.9+
- 套件需求：
  ```bash
  pip install pandas polars numpy matplotlib shioaji

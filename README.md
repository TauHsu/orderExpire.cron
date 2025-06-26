# 過期訂單自動刪除 排程功能

### 說明
每分鐘自動檢查，是否有超過 30 分鐘的待付款訂單。
在建立訂單時，將該訂單存入 Redis ，並倒數計時 30 分鍾。

[orderExpire.cron.js](https://github.com/TauHsu/orderExpire.cron/blob/main/crons/orderExpire.cron.js)：
每分鐘檢查有無過期 Redis Key，若 Redis 暫時連線失敗時，直接尋找 資料庫-訂單資料表 有無過期訂單。

[redisRestore.js](https://github.com/TauHsu/orderExpire.cron/blob/main/utils/redisRestore.js)：
Redis 重新連線時，將未滿30分鐘的待付款訂單，重新建立Redis Key，並倒數剩餘時間。

---

## 專案技術
- **後端語言**：Node.js
- **後端框架**：Express
- **排程**：[node-crons](https://docs.google.com/document/d/1GWuqjKpdtDiHLYQv4Czzw9N53wSfx70m8nGPO9MtYVE/edit?tab=t.0)

---

## 環境變數說明
```bash
# Server
PORT=3000

# Logging
LOG_LEVEL=debug                  # 可選: error, warn, info, debug, verbose

# Redis Config
REDIS_URL=your_redisUrl          # 部署的 Redis URL

```

---

## 關於作者
```bash
姓名: Tau 
Email: jason850629@gmail.com
GitHub: https://github.com/TauHsu
```

如果您有任何問題或建議，歡迎與我聯繫。感謝閱讀！

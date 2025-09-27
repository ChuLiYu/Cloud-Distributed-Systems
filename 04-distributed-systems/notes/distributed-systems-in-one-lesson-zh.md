---
title: 雲與分散式系統筆記 (中文版)
tags: [cloud, distributed-systems, notes, 中文]
updated: 2025-09-27
---

# 雲與分散式系統筆記 (中文版)

## 1. 分散式系統是什麼？
- **定義**：由多個獨立電腦組成，對使用者來說卻像是一台單一電腦。  
- **核心議題**：
  - 儲存 (Storage)
  - 計算 (Computation)
  - 訊息傳遞 (Messaging)

---

## 2. 儲存 (Storage)

### 2.1 單一主節點 (Single-Master Storage)
- 一個節點負責寫入，其它節點用來讀取。
- 問題：若主節點失效 → 需要切換或容錯機制。

### 2.2 讀取複製 (Read Replication)
- 多個副本以提升讀取效能。
- 適合讀多於寫的應用。

### 2.3 分片 (Sharding)
- **定義**：將資料切分，分散到不同節點。
- 方法：
  - 索引分片 (Index-based)
  - Join 分片（可配合資料反正規化 Denormalization）

### 2.4 一致性雜湊 (Consistent Hashing)
- 資料分配到節點的演算法。
- 關鍵公式：`R + W > N`  
  - R = 讀取副本數  
  - W = 寫入副本數  
  - N = 總副本數  
- 確保資料一致性。

### 2.5 CAP 定理
- **Consistency**：一致性  
- **Availability**：可用性  
- **Partition Tolerance**：分區容忍度  
- 理論：在網路分區時，只能滿足其中兩個。

---

## 3. 計算 (Computation)

### 3.1 Hadoop
- 批次處理 (Batch Processing)
- 適合大規模資料的離線處理。

### 3.2 Spark
- 記憶體為主的分散式計算引擎。
- 支援即時處理與批次處理。

---

## 4. 訊息傳遞 (Messaging)

### 4.1 Message Queue
- 解耦合系統元件。
- 範例：RabbitMQ, ActiveMQ。

### 4.2 Streaming
- 資料流處理。
- 範例：Apache Kafka。

---

## 5. 小結
- 分散式系統的挑戰：
  - 一致性 (Consistency)
  - 可用性 (Availability)
  - 容錯性 (Fault Tolerance)
- 工具與框架：
  - Hadoop / Spark → 計算
  - Cassandra / DynamoDB → 儲存
  - Kafka → 訊息傳遞
- 核心設計理念：**彈性、容錯、可擴展性**。

---

## 📚 延伸閱讀
- [CAP Theorem](https://en.wikipedia.org/wiki/CAP_theorem)
- [Consistency Models](https://jepsen.io/)
- [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/)

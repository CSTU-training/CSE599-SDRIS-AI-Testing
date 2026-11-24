# CSE590 專案介紹（中文版）

> **範圍更新（2026-11-23）：** 官方作業標示課程為 **CSE590**，截止 **2026-12-20**。提議選擇 **(c) Testing GenAI Apps**，以 SDRIS AI 分析模組作為受測系統，仍需教授確認。重點是 **3D AI Test Model／Decision Table／Complexity**、合成及擴增資料、**教授提供的 Agentic AI Test Tool** 生成測試腳本、真實測試結果、Bug Report，以及含成本／預算與覆蓋率的品質報告。QoS 為選做（最高額外 10%）。Python/pytest/API/UI 測試是輔助方法，不能替代教授工具。下方 12/21 的展示日期為團隊暫定，並非附件作業列明。詳見 [課程範圍調整](course-realignment.md) 與 [3D 建模草案](test-modeling-design.md)。

## 專案名稱
SDRIS 伺服器故障診斷系統的 AI 測試與品質評估

**課程：** CSTU CSE590 — AI & Software Test Automation  
**團隊：** Team 3  
**預定繳交：** 2026-12-20  
**預定展示：** 2026-12-21

## 專案摘要
本專案以 SDRIS（Server Diagnostic & Reliability Intelligence System）作為受測系統（System Under Test, SUT）。SDRIS 是開發中的伺服器故障診斷平台，目標是協助工程師分析測試日誌、辨識異常、整理證據，並提供 AI 輔助的故障原因與排查建議。

課堂專案**不是重新開發 SDRIS**，而是設計測試模型、測試資料與自動化評估，驗證 SDRIS MVP 的功能正確性、AI 診斷品質、證據可靠性與穩健性。

## MVP 測試流程
1. 準備合成的伺服器測試日誌。
2. 透過 SDRIS 可用的介面輸入日誌（實際 API 契約仍待確認）。
3. 檢查日誌解析、異常偵測與診斷輸出。
4. 比對預期結果（ground truth）、證據引用及不確定性表達。
5. 產生測試紀錄、Bug Reports、品質指標與期末報告。

## 測試範圍
- Black-box / white-box 測試及 API 測試
- 3D AI Test Model 與 Decision Tables
- 合成測試資料、受控資料增強
- Python / pytest 自動化測試
- 診斷正確性、證據有效性、錯誤結論及不確定性評估
- 測試覆蓋率、複雜度、成本與品質報告

## 初期案例
以儲存裝置 NVMe/FIO 異常作為候選第一條端到端案例，再依 SDRIS 實際可用功能擴充 ECC、網路或開機問題。這是**規劃**，不是已完成的功能。

## 團隊協作
具備伺服器背景的成員負責技術情境與預期診斷審核；其他成員可以共同參與測試模型、案例、資料標註、執行紀錄、缺陷追蹤與品質報告。分工需經團隊討論確認。

## 目前狀態與限制
目前 GitHub README 主要是規劃文件；Python 測試框架、範例 API 和完整診斷流程不得視為已實作。3D 模型的維度、教師提供的 Agentic AI 測試工具，以及是否允許自建 SUT，仍需依老師要求確認。

**資料安全：** 公開 Repository 只能使用合成或明確授權公開的資料；不得上傳內部日誌、客戶資料、真實設備識別碼、IP、密碼或專有腳本。

## 相關文件
- [English Overview](project-overview.en.md)
- [Team Onboarding](team-onboarding.md)
- [Assignment Mapping](assignment-mapping.md)
- [原始完整 README](../README.md)

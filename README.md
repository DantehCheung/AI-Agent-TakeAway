# AI-Agent-TakeAway
Integrated the text information which is useful about AI-Agent system's mindset

給工程師的 Takeaway

如果你在用 LangChain、LangGraph 或自己的框架搭建一個 AI agent，這五個維度是一份不錯的檢查清單：

資源管理做了嗎？ 你的 context 滿了之後怎麼辦？有沒有熔斷機制防止無限循環消耗？

狀態持久化做了嗎？ 跨 session 的知識存在哪？怎麼讀回來？有沒有機制判斷哪些值得存？

信息流控制做了嗎？ 每一輪送給模型的 context 是精心選擇的，還是把所有東西都塞進去？

安全邊界做了嗎？ 模型能呼叫的工具有沒有約束？危險操作有沒有攔截和確認機制？

任務編排需要嗎？ 你的任務複雜到需要多個 agent 協作嗎？如果需要，通信和權限怎麼設計？

這五個問題，任何一個沒想清楚，都可能成為系統在 production 環境下的瓶頸。

Reference: Harness Engineering - AI 工程師的第三個維度




🧱 靜態字首架構的四大核心要素
1. System Prompt（系統提示詞）
	• 定義：設定 AI 的角色、語氣、行為準則與限制（例如：「你是一個資深的軟體架構師...」）。
	• 靜態特性：在同一個應用程式中，這段規則通常是固定不變的。
2. Tool Definition（工具定義）
	• 定義：提供給模型的外部 API 規格或函數宣告（Function Calling），讓 AI 知道有哪些工具可用、需要什麼參數。
	• 靜態特性：除非更新系統功能，否則工具的 JSON Schema 通常保持不變。
3. Context（上下文背景）
	• 定義：長篇的固定知識庫、法律條文、企業內部文件或產品規格。
	• 靜態特性：這些是提供給 RAG（檢索增強生成）或多輪對話的基礎背景，在一段時間內是固定的。
4. Engineering（工程優化）
	• 定義：如何精心設計與排列上述內容的順序。
	• 關鍵原則：必須將「完全不變的內容」排在最前面（即字首 Prefix），將「會變動的內容（如使用者最新的問題）」排在最後面。

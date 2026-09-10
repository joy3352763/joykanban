# mytaskboard
純地端、無資料庫，單純靠匯出/匯入json


純前端個人用 :: https://joy3352763.github.io/mykanban/
<img width="1900" height="594" alt="image" src="https://github.com/user-attachments/assets/613dca42-2ea7-4116-a868-2f25fba5456f" />





團隊追蹤介面 :: https://joy3352763.github.io/mykanban/tracker.html
<img width="1814" height="933" alt="image" src="https://github.com/user-attachments/assets/76515a05-40bb-4b0b-8d0c-f80bfb69fff2" />
可匯入多人的json一起看進度

🚀 零部署・純前端專案追蹤系統 (Backendless Kanban & Tracker)
這是一個完全不需要後端伺服器、無需安裝任何資料庫的純前端 Kanban 看板系統。透過瀏覽器的 LocalStorage 與 JSON 檔案的匯出/匯入機制，完美實現了個人高效任務管理、Obsidian 筆記無縫連動，以及輕量級的團隊協作與主管彙整。


✨ 系統優勢 (Why choose this?)
 * 真正的零部署 (Zero Setup)：只需要一個瀏覽器，點擊 HTML 檔案即可立刻開始使用，完全免除 Node.js、Docker 或資料庫的環境架設煩惱。
 * 資料絕對掌控 (Privacy First)：資料 100% 儲存在你的本地端與 JSON 備份檔中，無雲端外洩風險，適合高資安要求的專案環境。
 * 極致輕量與彈性：採用 Vue 3 + Tailwind CSS 打造，單一 HTML 檔案不到 1000 行，隨時可以打開記事本客製化自己的專屬功能。
 * 無痛的團隊協作：透過「主/備援機制」與「單張卡片傳遞」，完美避開了傳統檔案共用最可怕的「資料覆寫衝突 (Race Condition)」。


🛠️ 核心功能 (Core Features)
1. 豐富的任務卡片系統
 * 直覺拖曳：支援 Backlog、In Progress、Done 欄位間的平滑拖曳操作。
 * 多維度屬性：支援自訂標籤 (Tags)、預計完成日 (Due Date)、子任務進度條 (Subtasks)，以及視覺化的追蹤標記 (Watch)。
 * 自動循環重生 (Recurring Tasks)：支援每日、每週、每月循環任務，並可自訂結束條件（特定日期或執行次數），卡片進入 Done 後自動於 Backlog 產生新週期任務。
2. 完美的 Obsidian 工作流連動
 * 一鍵轉譯 Markdown：點擊「複製為 Obsidian」，看板資料將自動轉化為相容於 Dataview 與 Tasks 外掛的語法。
 * 雙括號連結：任務標題會自動轉換為 [[內部連結]]，貼入 Obsidian 後可無縫對接你的每日工作日誌 (Daily Note)。
3. 智慧團隊協作與彙整機制
 * 單張卡片派發：主責人可將設定好的單張卡片匯出給備援人員。系統具備智慧防呆，匯入時自動辨識並詢問是否「覆蓋更新」或「新建」，絕不搞亂現有看板。
 * 主管聚合儀表板 (tracker.html)：主管可一次匯入全團隊的 JSON 檔。系統自動透過「全局專案代碼 (Project Code)」整併任務，並嚴格以「主責人員」的資料作為唯一真理 (Single Source of Truth)，自動計算子任務完成率。


📂 檔案結構
系統分為兩個獨立的單頁應用程式 (SPA)：
 * kanban.html (個人操作端)：供所有團隊成員日常使用。負責建立任務、拖曳進度、匯出個人 JSON 備份，以及與 Obsidian 連動。
 * tracker.html (主管聚合端)：唯讀儀表板。負責一次讀取多份 JSON，解決衝突並視覺化呈現整個團隊的專案健康度。


📖 操作指南 (Getting Started)
第一步：初始化你的專屬看板
 * 雙擊打開 kanban.html。
 * 點擊右上角 「⚙️ 設定」。
 * 在「看板擁有者 (Board Owner)」輸入你的名字（請與團隊約定好的名稱完全一致）。
 * （選用）更新「團隊名單」字串，以確保卡片內的下拉選單擁有最新成員。
第二步：建立與編輯任務
 * 點擊欄位底部的 「+ Create new card」。
 * 點擊剛建立的卡片進入編輯模式。
 * 填寫標題、日期、標籤（可連續輸入半形逗號分隔），並隨意新增子任務。
 * 如果這是團隊協作專案，勾選 「🤝 團隊協作專案」，務必填入唯一的 「專案代碼」，並指定主責與備援人員。
第三步：資料備份與還原
 * 日常存檔：系統會自動將每次點擊與拖曳儲存於瀏覽器緩存 (LocalStorage) 中，重新整理不會遺失。
 * 冷備份/跨裝置轉移：點擊右上角 「💾 匯出備份」，下載完整的 JSON 檔案。
 * 還原資料：點擊 「📂 匯入」 選擇你的 JSON，看板將瞬間回到備份狀態。


🤝 團隊協作工作流 (Team Workflow)
本系統採「集線器與輪輻 (Hub-and-Spoke)」模型，請遵循以下協作規範：
 * 專案建檔 (主責人)：主責人員在 kanban.html 建立卡片，設定好「專案代碼」與子任務。
 * 交接設定 (備援人)：主責人員在編輯視窗點擊 「📤 匯出此卡片」，傳送給備援人員。備援人員點擊 「📂 匯入」 載入卡片。
 * 日常推進：主責人員日常推進任務進度。若有重大設定修改，可再次「匯出此卡片」請備援人員匯入覆蓋。
 * 主管查核：
   * 全體成員每週五下班前，點擊 「💾 匯出備份」，將各自的 JSON 上傳至公司共用資料夾。
   * 主管打開 tracker.html，點擊 「📂 匯入團隊 JSON」，全選共用資料夾內的檔案，即可查看最準確的專案全局進度。

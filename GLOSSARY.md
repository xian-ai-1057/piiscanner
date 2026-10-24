# piiscanner

piiscanner 在地端找出文件與訊息中的個資，先遮蔽或假名化再交給雲端模型處理，並在地端把雲端回覆還原成真實值。

## Language

### 資料

**個資 (Personal data)**:
能直接或間接識別特定自然人的資料，範圍以個資法第 2 條為準。
_Avoid_: 敏感資訊、隱私資料

**直接識別資訊 (Direct identifier)**:
單獨就能識別特定個人的個資，例如姓名、證號、聯絡方式、金融帳號、地址。
_Avoid_: 強識別資料

**間接識別資訊 (Quasi-identifier)**:
單獨不足以識別、但與其他資訊組合後能推出特定個人的資訊，例如職稱加公司加事件。
_Avoid_: 準識別符、弱識別資料

**個資實體 (PII entity)**:
文字中被判定為個資的一段連續內容，帶有一個實體類型。
_Avoid_: 敏感詞、token

**實體類型 (Entity type)**:
個資實體的分類，例如人名、身分證字號、地址。
_Avoid_: 標籤、PII 類別

### 處理方式

**遮蔽 (Redaction)**:
以不可還原的標記取代個資實體，雲端回覆中不會換回真實值。
_Avoid_: 遮罩、masking、塗黑

**假名化 (Pseudonymization)**:
以可還原的假名取代個資實體，假名與真實值的對應只存在地端。
_Avoid_: 匿名化、替換、去識別化、tokenization

**假名 (Pseudonym)**:
假名化時用來取代一個個資實體的值。
_Avoid_: 替代值、佔位符、surrogate

**對照表 (Mapping)**:
地端保存的假名與真實值的對應紀錄。
_Avoid_: vault、字典、映射表

**還原 (Restoration)**:
在地端把雲端回覆中的假名換回對照表裡的真實值。
_Avoid_: 反假名化、unmask、de-anonymize

**擋下 (Block)**:
拒絕整筆請求，不讓任何內容送往雲端模型。
_Avoid_: 攔截、reject

### 環境

**地端 (On-prem)**:
由使用者自己掌控、允許個資存在的運算環境。
_Avoid_: 本地、邊緣、edge

**雲端模型 (Cloud model)**:
地端以外的 LLM，只會收到遮蔽或假名化之後的內容。
_Avoid_: 外部模型、雲端 LLM

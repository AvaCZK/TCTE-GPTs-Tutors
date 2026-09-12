# 統測 AI 教師

一套針對 **四技二專統一入學測驗** 所建立的 Custom GPT 學習資源。

目前包含：

- 國文
- 英文
- 數學 B
- 商業與管理群－專業科目（一）
- 商業與管理群－專業科目（二）

各科皆依照統測官方資料建立專用 Instructions 與 Knowledge，目標是讓 GPT 更熟悉統測考試範圍、歷屆命題方式與各科解題邏輯。

本專案並非 Fine-tuning，而是透過：

```text
基礎模型
+
Custom GPT Instructions
+
Knowledge Retrieval
+
統測官方資料
````

建立各科專用的統測學習 GPT。

---

# 科目

| 科目                  | 內容                   |
| ------------------- | -------------------- |
| [國文](./Chinese/)         | 字詞、文言文、閱讀理解、文學常識、修辭  |
| [英文](./English/)         | 單字、文法、克漏字、閱讀理解       |
| [數學 B](./Mathematics-B/)       | 統測數學 B 觀念、計算、解題與弱點分析 |
| [專業科目（一）](./Professional-Subject-I/) | 商業概論、數位科技概論、數位科技應用   |
| [專業科目（二）](./Professional-Subject-II/) | 會計學、經濟學              |

---

# 專案結構

```text
.
├─ README.md
│
├─ English/
│  ├─ icon.png
│  ├─ v1.0.0/
│  │  ├─ Instructions.txt
│  │  ├─ README.txt
│  │  └─ knowledge/
│  └─ ...
│
├─ Chinese/
│  ├─ icon.png
│  ├─ v1.0.0/
│  │  ├─ Instructions.txt
│  │  ├─ README.txt
│  │  └─ knowledge/
│  └─ ...
│
├─ Mathematics-B/
│  ├─ icon.png
│  ├─ v1.0.0/
│  │  ├─ Instructions.txt
│  │  ├─ README.txt
│  │  └─ knowledge/
│  └─ ...
│
├─ Professional-Subject-I/
│  ├─ icon.png
│  ├─ v1.0.0/
│  │  ├─ Instructions.txt
│  │  ├─ README.txt
│  │  └─ knowledge/
│  └─ ...
│
└─ Professional-Subject-II/
   ├─ icon.png
   ├─ v1.0.0/
   │  ├─ Instructions.txt
   │  ├─ README.txt
   │  └─ knowledge/
   └─ ...
```

---

# 檔案說明

## `icon.png`

對應科目的 Custom GPT 頭像。

可在建立 GPT 時直接上傳使用。

---

## `版本號/Instructions.txt`

該版本 Custom GPT 使用的完整 Instructions。

建立 GPT 時將內容完整複製至：

```text
設定
→ 指令 / Instructions
```

---

## `版本號/README.txt`

該版本的 GPT 建立方式與建議設定。

內容通常包含：

```text
名稱
說明
Instructions 使用方式
對話啟動器
Knowledge
模型設定
功能設定
```

---

## `版本號/knowledge/`

該版本建議上傳至 Custom GPT Knowledge 的資料。

可能包含：

```text
當年度統測考試大綱
歷屆正式試題與答案
官方學習指引
官方試題特色
官方試題研討會
官方參考樣卷
官方更正或釋疑資料
```

建立 GPT 時將該版本 `knowledge/` 中需要的文件上傳至知識庫。

---

# 建立方式

## 1. 選擇科目

例如：

```text
./English/
```

---

## 2. 選擇版本

例如：

```text
./English/v1.0.0/
```

原則上建議使用最新版本。

---

## 3. 設定頭像

上傳：

```text
./English/icon.png
```

---

## 4. 查看版本說明

開啟：

```text
./English/v1.0/README.txt
```

依其中提供的：

```text
名稱
說明
對話啟動器
模型
功能
```

建立 Custom GPT。

---

## 5. 匯入 Instructions

開啟：

```text
./English/v1.0/Instructions.txt
```

將內容完整複製至 Custom GPT 的：

```text
指令 / Instructions
```

---

## 6. 上傳 Knowledge

將：

```text
./English/v1.0/knowledge/
```

中的文件依該版本說明上傳至 GPT Knowledge。

---

## 7. 完成建立

完成後即可開始進行：

```text
觀念學習
↓
歷屆題解析
↓
模擬練習
↓
錯題檢討
↓
弱點分析
↓
補強練習
```

---

# 版本制度

版本格式：

```text
v主版本.次版本.子版本
```

例如：

```text
v1.0.0
v1.1.0
v1.2.1
v2.0.2
```

一般原則：

```text
v1.0.0
首次公開版本

v1.0.1
Instructions 小幅修正
錯題處理改善
回答方式調整

v1.1.0
新增官方資料
修正已知問題

v2.0.0
架構或 Instructions 大幅更新
```

舊版本可保留，以方便比較不同版本的設定與效果。

---

# 資料來源原則

各科主要以統測官方資料作為 Knowledge 核心。

資料優先順序原則為：

```text
當年度官方考試大綱
↓
官方最終釋疑／更正／答案確認
↓
官方歷屆試題與標準答案
↓
官方學習指引
↓
官方試題特色
↓
官方試題研討會
↓
其他整理資料
```

不同年度資料若存在差異，應優先依目前準備年度所適用的官方資料判斷。

---

# 關於 RAG

本專案的 Knowledge 使用方式可視為一種簡化的 RAG：

**Retrieval-Augmented Generation
檢索增強生成**

基本流程：

```text
使用者提出問題
↓
系統從 Knowledge 檢索相關內容
↓
將相關內容提供給模型
↓
GPT 根據資料與 Instructions 生成回答
```

因此，這些資料並不是透過 Fine-tuning 寫入模型權重，而是在回答時作為知識來源使用。

---

# 使用注意事項

本專案的目標是提升 GPT 在統測學習情境中的實用性，但 AI 仍可能發生：

```text
計算錯誤
讀題錯誤
文件檢索錯誤
PDF 解析不完整
年份或題號誤判
過度推論
錯誤理解選項
生成品質不穩定
```

因此重要答案仍應與官方資料進行確認。

尤其涉及：

```text
官方答案
爭議題
考試範圍
官方更正
法規
考試制度
升學規則
```

時，應以相關官方機構最新公告為準。

---

# 免責聲明

本專案為非官方學習輔助專案。

本專案：

* 並非技專校院入學測驗中心官方產品
* 並非任何學校官方服務
* 並非任何出版社或補習班官方服務
* 不代表任何官方機構立場
* 不保證 AI 所產生的答案、解析、計算或模擬題完全正確

ChatGPT 與其他生成式 AI 皆可能產生錯誤資訊。

使用者應自行查核重要資訊。

本專案僅供：

```text
學習
練習
複習
解題輔助
研究
```

用途。

---

# 著作權聲明

各官方文件、歷屆試題、答案、學習指引、試題特色、試題研討會及其他第三方資料，其著作權與相關權利均屬原著作權人或權利人所有。

本專案自行撰寫的：

```text
Instructions
README
設定方式
資料組織方式
```

與第三方原始資料之著作權應分別看待。

若 Repository 為公開專案，在重新發布第三方 PDF 或教材前，應先確認其授權範圍。

若相關資料不允許公開再散布，建議只提供：

```text
資料名稱
官方來源
下載方式
```

並由使用者自行取得資料後加入 Knowledge。

---

# 隱私與安全

請勿將下列內容提交至公開 Repository：

```text
密碼
API Key
Token
個人身分資料
學生個資
私人考卷
未公開教材
未取得公開授權的付費教材
```

---

# 最後提醒

本專案希望將統測複習流程簡化為：

```text
理解觀念
↓
練習題目
↓
找出錯因
↓
分析弱點
↓
針對弱點補強
↓
再次練習
```

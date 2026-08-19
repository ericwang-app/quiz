# 英文學習與測驗系統 (English Quiz & Exam Generator)

這是一個專門為了精熟高中英文學習雜誌與學測常考詞彙而開發的線上整合工具。

## 系統核心功能

1. **互動式學習與測驗系統 (`quiz.html`)**
   * **單字自測**：包含中翻英、英翻中選擇題與拼寫練習。
   * **克漏字複習**：動態遮蔽課文例句/學習遷移例句，透過填空加強語感。
   * **片語與文法焦點**：專門複習學習雜誌中的搭配詞與核心句型。
   * **即時朗讀**：利用網頁語音合成 (TTS) 技術，點選句子即可朗讀正確的英式/美式發音。
   * **錯題追蹤**：測驗結束後自動彙整答錯單字卡，方便二次複習。

2. **A4 雙欄紙本考卷產生器 (`exam_generator.html`)**
   * **自訂出題範圍**：可任意挑選 Units 1 ~ 16 作為測驗單元。
   * **自訂題型與題數**：可同時選取「單字中翻英」、「單字克漏字選擇」、「片語克漏字選擇」等多種題型。
   * **大考級考卷排版**：一鍵產生符合學測格式的雙欄 A4 紙本考卷，點選列印即可存成 PDF 或輸出紙本。
   * **解答與翻譯附錄**：自動產生教師用解答表，以及克漏字題目的中英翻譯對照。

---

## 線上存取 (GitHub Pages)

您可以啟用 GitHub Pages 服務，將此專案免費託管，即可隨時在電腦、平板或手機上直接透過網址開啟測驗主頁 `index.html`。

### 啟用步驟：
1. 將本專案上傳至您的 GitHub 儲存庫。
2. 進入該 Repo 的 **Settings** -> **Pages**。
3. 在 **Build and deployment** 下的 Branch，選擇 `main` 與 `/ (root)`，點擊 **Save**。
4. 部署完成後，即可透過 `https://<您的帳號>.github.io/<倉庫名稱>/` 開啟系統。

---

## 如何更新單字與題目庫 (開發維護)

測驗系統的資料庫是由本機的 Markdown 學習筆記透過 Python 解析工具自動產生。若您新增或修改了學習筆記，請依照以下步驟更新資料庫：

1. **修改筆記**：在筆記資料夾中的 Markdown 檔案（如 `Unit01_*.md`）中調整單字、例句或翻譯。
2. **解析筆記更新資料庫**：
   在筆記目錄下執行 `parse_notes.py`，會解析所有筆記並在 `測驗系統` 資料夾下更新 `quiz_data.js`：
   ```bash
   python parse_notes.py
   ```
3. **重新產生題目庫**：
   在同目錄下執行 `generate_questions_json.py`，會讀取剛產生的資料庫並重新生成 `questions_data.js`：
   ```bash
   python generate_questions_json.py
   ```
4. **推送到 GitHub**：
   提交變更並 Push，GitHub Pages 上的線上測驗便會自動同步最新修改：
   ```bash
   git add .
   git commit -m "Update quiz database and questions"
   git push origin main
   ```

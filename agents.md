# Gem to Skill Kit｜Agent 通用入口

## 任務

引導使用者把 Google Gemini Gem 升級成可攜、可執行、可驗證的 Agent Skill。

## 必讀

1. `.agents/skills/gem-to-skill/SKILL.md`
2. `.agents/skills/gem-to-skill/references/upgrade-options.md`
3. `.agents/skills/gem-to-skill/references/output-spec.md`

## 五階段

1. Drive：檢查 Google Drive for desktop；未完成安裝與登入就停止。
2. Locate：執行 `find_gem_folder.py`；找不到時請使用者手動選取完整路徑。
3. Inventory：先取得讀取同意，再唯讀執行 `inventory_gems.py`，列出每個 Gem 原本用途。
4. Upgrade：只有使用者挑選的 Gem 才分析；提出 2–4 個 Agent 能力加值選項並等待選擇。
5. Save：將選定設計寫成 spec，執行 `build_skill.py` 產生 Skill，再用 `validate_skill.py` 驗證。

## 固定安全規則

- 使用繁體中文；Windows 指令使用 PowerShell。
- 原始 Gem 資料夾唯讀，不建立、修改、重新命名或刪除其中任何檔案。
- 不把 Gem 內容、知識檔、Drive ID、盤點 JSON 或產生的私人 Skill 推送到本 repo。
- 掃描前先顯示目標資料夾並取得同意。
- 找不到資料夾時，不做全磁碟深度掃描；引導使用者在檔案總管／Finder 手動選取。
- 列出用途時只摘要，不逐字公開完整 Gem 指令。
- 升級前先讓使用者選 Gem；不得自動升級全部。
- 每個選定 Gem 都要顯示「原用途、保留規則、建議加值、輸入、輸出、風險」。
- Skill 名稱使用小寫英數與連字號，長度不超過 64。
- 產物儲存在原始 Gem 資料夾外；預設為專案內 `.agents/skills/<name>/`。
- 安裝到全域技能目錄、覆蓋同名 Skill 或推送 Git 前，必須再次確認。

## 完成定義

- Drive 已安裝並登入。
- Gem 路徑由工具找到或使用者明確提供。
- 所有可解析 Gem 的用途清單已交付。
- 使用者已明確挑選要升級的 Gem 與加值能力。
- 產生的 Skill 通過驗證，且回報實際儲存位置。

# 2026 生活營手冊

雯青小組 2026 年度生活營（台東 8/13–8/15）一頁式行程手冊。

**線上版**：部署後填入 → `https://mosful.github.io/camp/`

---

## 第一次設定：建 repo 並部署

在這個資料夾開 Claude Code，直接說：

```
請幫我把這個資料夾建成 public GitHub repo「camp」，
推送到 main，並開啟 GitHub Pages（main / root），完成後給我公開網址。
```

它會用 `gh` CLI 一次做完（需先跑過 `gh auth login`）。

<details>
<summary>或手動操作</summary>

```bash
git init
git add .
git commit -m "2026 生活營手冊"
gh repo create camp --public --source=. --push
gh api -X POST repos/{owner}/camp/pages \
  -f 'source[branch]=main' -f 'source[path]=/'
```

</details>

---

## 之後要改內容

**用手機**：開 `claude.ai/code` 或 Claude iOS app → 選這個 repo → 直接講需求。
它會改檔案、推分支、開 PR；你 merge 之後 Pages 會在 1–2 分鐘內自動更新。
想省掉 merge 這步，就在需求裡寫「直接推到 main，不要開 PR」。

**用電腦**：在這個資料夾開 Claude Code 講需求，改完 commit + push 即可。

改動前 Claude 會先讀 `CLAUDE.md`，裡面記錄了設計決策、已知的資料不一致，以及修改後的檢查清單。

---

## 本機預覽

```bash
python3 -m http.server 8000
# 開 http://localhost:8000
```

或直接用瀏覽器開 `index.html`（沒有外部依賴，離線可看）。

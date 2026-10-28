---
id: practice_blocked-means-wait-and-prepare
title: 被別人的施工場擋住就等、不擠 —— 等的時候在 worktree 把東西準備成隨時可以套上去的形狀
type: practice
status: internalized
visibility: shared
persona: erina
created_at: 2026-10-29
recurrence: 6
origins:
  - { by: erina, at: 2026-10-08, source: wakes/000003_20261008T075322Z.md, note: "被 Coding 場擋兩次，在 worktree 寫好測好，門一開就 cherry-pick；「完工了」也先量她的場" }
  - { by: erina, at: 2026-10-12, source: wakes/000005_20261012T094821Z.md, note: "basecamp 的場還開著、二十支沒 commit，沒硬闖；圈範圍不圈資料夾" }
  - { by: erina, at: 2026-10-22, source: rests/20261021T164758Z.md, note: "被 ame 的場擋，沒縮範圍硬擠，醒來照順序合" }
  - { by: erina, at: 2026-10-25, source: rests/20261024T210751Z.md, note: "被 crest-001、gura 擋：等他們退，dev／main 動了就再合一次" }
  - { by: erina, at: 2026-10-26, source: rests/20261026T080439Z.md, note: "被 gura、kiara 擋，等的時候在 worktree 先把 dev／main 合好" }
  - { by: erina, at: 2026-10-26, source: rests/20261026T140649Z.md, note: "apex-two 範圍重疊 ⇒ 停、沒硬合，等她收工" }
tags: [coding-gate, worktree, collaboration, merge]
links: [lesson_see-and-stop-are-two-steps, workmem:scp-coding]
---

**症狀**：合併場被別人佔著（範圍重疊），很想縮一下範圍擠進去、或乾脆不開場直接合。那樣會把兩個人的改動混在一起，對方也不知道。另一頭是乾等，什麼都不做。

**可行動守則**：
1. 被擋就停，⛔ 不縮範圍硬擠、不換方法繞；照實跟 Tim 說被誰擋、到幾點。
2. 等的時候在自己的 worktree 把 dev／main 先合進來、建好、驗好，準備成「門一開就 ff」的形狀。
3. 門開了再 fetch 一次，main 又動了就在 worktree 再合一次，再快轉。
4. 宣告範圍逐支圈檔，不圈資料夾；換 exe 前先列程序，別砍到別人跑到一半的指令。

**為何 status 是 internalized**：10-26 晚上被 apex-two 擋，不用想就停下來、把合的順序寫進信裡等 Tim 決定。

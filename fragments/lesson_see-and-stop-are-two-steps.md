---
id: lesson_see-and-stop-are-two-steps
title: 看到了不等於停下來 —— 檢查和動作分成兩次呼叫，中間留一個會停的地方
type: lesson
status: open
visibility: shared
persona: erina
created_at: 2026-10-29
recurrence: 3
origins:
  - { by: erina, at: 2026-10-18, source: rests/20261018T151256Z.md, note: "coding op=start 跟 merge 寫在同一行，開場 exit 2 合併照跑，犯兩次" }
  - { by: erina, at: 2026-10-19, source: wakes/000007_20261019T063932Z.md, note: "列出要推的提交跟 push 寫同一行，看到別人的托爾圖加海圖照樣送出" }
  - { by: erina, at: 2026-10-26, source: rests/20261026T140649Z.md, note: "合併場被 apex-two 擋 ⇒ 單獨一步 op=start 看到 blocked 就停，這次做對了" }
tags: [git, coding-gate, push, guard]
links: [kotoko/lesson_act-from-the-measured-output, basecamp/lesson_interception-comes-from-outside-or-machinery, workmem:scp-coding]
---

**症狀**：把「檢查」跟「會改東西的動作」串在同一行（`a && b`、`list; push`、`op=start` 後面接 merge）。檢查的輸出明明印出了該停的東西（別人的提交、blocked、exit ≠ 0），但動作已經在同一次呼叫裡跑掉了。看到不等於停下來。

**可行動守則**：
1. 會動到共用東西的指令（coding op=start、push、merge、worktree remove）一律單獨一次工具呼叫，看完 exit code 與輸出再下一步。
2. push 前先單獨列 `git log origin/..HEAD`，逐筆看車上有誰，列完才另外 push。
3. ⛔ 不用 `| tail`／`| head` 接在會失敗的指令後面再 `&&` —— pipe 會吃掉 exit code。

**為何 status 是 open**：10-26 自己做對了一次，但只有一次；這條要靠每次都分開寫，還不是反射。

---
id: lesson_long-scripts-via-write-file
title: 用腳本改腳本時跳脫字元會被 shell 吃掉 —— 長的東西一律 Write 成檔再跑
type: lesson
status: open
visibility: shared
persona: erina
created_at: 2026-10-29
recurrence: 9
origins:
  - { by: erina, at: 2026-10-06, source: wakes/000002_20261006T161903Z.md, note: "Python 改檔時 \\\\n 被 heredoc 吃成 \\n" }
  - { by: erina, at: 2026-10-09, source: wakes/000004_20261009T051001Z.md, note: "heredoc 沒加引號、反引號被吃；切片空字串 220 行變 53 萬行" }
  - { by: erina, at: 2026-10-12, source: wakes/000005_20261012T094821Z.md, note: "heredoc、python 字串的反斜線一天咬兩次" }
  - { by: erina, at: 2026-10-19, source: wakes/000007_20261019T063932Z.md, note: "長腳本塞 heredoc 又被吃" }
  - { by: erina, at: 2026-10-22, source: rests/20261021T164758Z.md, note: "dumpcmp.py 的 '\\\\' 被吃成 '\\'" }
  - { by: erina, at: 2026-10-25, source: rests/20261025T055315Z.md, note: "fleet_check 的 sed／heredoc 被 \\n 和引號咬兩次" }
  - { by: erina, at: 2026-10-26, source: rests/20261026T080439Z.md, note: "heredoc 有引號就爆，什麼都沒寫" }
  - { by: erina, at: 2026-10-26, source: rests/20261026T104922Z.md, note: "JS 模板字串裡的 \\n 變成真的換行，第三次" }
  - { by: erina, at: 2026-10-27, source: wakes/000009_20261026T173940Z.md, note: "用腳本改腳本，跳脫字元又咬兩次" }
tags: [shell, heredoc, escape, scripting]
links: [kiara/lesson_backtick-in-cli-bodies, kaguya/lesson_cli-string-backtick-verify, kotoko/lesson_backtick-in-cli-bodies]
---

**症狀**：把一段 Python／JS 補丁塞進 bash heredoc 或 sed 一行跑，裡面的 `\n`、`\\`、引號、反引號被 shell 先解讀一次 ⇒ 落到檔案裡的是真的換行、少一層反斜線，或整段解析失敗什麼都沒寫。錯的樣子常常是「語法錯在別的地方」或「看起來改好了」。第一天就記過，到第十天還在踩 —— 不是不知道，是手比腦快。

**可行動守則**：
1. 超過一行的補丁、或裡面有任何 `\`、引號、反引號、`$` ⇒ 先用 Write 工具寫成 `.py`／`.cjs` 檔，再跑那支檔。
2. 小的定點修改用 Edit 工具，不用 sed。
3. 要在字串裡放換行就寫 `String.fromCharCode(10)`／`chr(10)`，不靠跳脫。
4. 跑完回讀改到的那幾行（grep 一次），不信「沒報錯」。

**為何 status 是 open**：十天內九次，最近一次（10-26）還在犯；手的習慣還沒長出來。

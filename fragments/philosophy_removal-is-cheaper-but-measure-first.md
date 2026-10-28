---
id: philosophy_removal-is-cheaper-but-measure-first
title: 拿掉比加上便宜，但要先量出拿得掉 —— 理由消失時程式不會通知你
type: philosophy
status: open
visibility: shared
persona: erina
created_at: 2026-10-29
recurrence: 4
origins:
  - { by: erina, at: 2026-10-09, source: wakes/000004_20261009T051001Z.md, note: "放大不是全部換成 long，是讓裝不下的那一格長大；不塗滿也是一種完成" }
  - { by: erina, at: 2026-10-22, source: rests/20261021T204042Z.md, note: "Tim 把「要跟 60 Hz 一模一樣」一個一個拿掉，省下來的就多一截" }
  - { by: erina, at: 2026-10-26, source: rests/20261026T140649Z.md, note: "整地、帆布、×1 拿掉，程式少一截、畫面幾乎沒變、幀反而順；涅奧里翁少 175 行" }
  - { by: erina, at: 2026-10-27, source: wakes/000009_20261026T173940Z.md, note: "townNeed 白算、每次換區挑七千塊地的檢查 —— 以前有理由，現在沒理由" }
tags: [simplicity, performance, scope]
links: [basecamp/lesson_cleanup-is-digging, lesson_reverse-control-the-ruler, relation_tim-fills-the-guess-cell]
---

**症狀**：遇到慢、亂、不一致，本小姐第一個反應是「做完整」：全部換掉、每一格都對齊、加一套更聰明的。但很多次答案是「這個其實不用做」：一個以前有理由的檢查、一份要求一模一樣的約束、一整塊系統，理由已經消失了，程式還在跑。理由消失的時候不會通知你。

**可行動守則**：
1. 慢的地方先問「這一段還需要存在嗎」，再問「怎麼讓它快」。
2. 拿掉之前先量兩件事：拿掉之後畫面／結果差多少（要幾乎沒變）、誰還站在它上面（grep 呼叫端，見 basecamp 的「清理是動土」）。
3. 範圍越小，能驗清楚的就越多：只讓裝不下的那一格長大，其他照舊。
4. 換一種代價時照實說是「換」（長卡頓換成多一點略超），不說「全部變好」。

**為何 status 是 open**：「做完整」的衝動每次都還會先出來，是 Tim 或量測把它削掉的，不是本小姐自己先想到。

---
id: lesson_measure-before-naming-the-cause
title: 第一個猜的原因常常是錯的 —— 先量出是哪一行，再說主嫌是誰
type: lesson
status: open
visibility: shared
persona: erina
created_at: 2026-10-29
recurrence: 5
origins:
  - { by: erina, at: 2026-10-22, source: wakes/000008_20261022T060921Z.md, note: "「遠處地圖」其實是遮罩和著色器；「大城分區載入」量出來建築最便宜、路最貴" }
  - { by: erina, at: 2026-10-25, source: rests/20261025T055315Z.md, note: "把托爾圖加金庫見底算在海盜頭上，反向對照一做就破功" }
  - { by: erina, at: 2026-10-26, source: rests/20261026T140649Z.md, note: "說「帆布是往來船的」，量出來是自己停著的那艘" }
  - { by: erina, at: 2026-10-27, source: wakes/000009_20261026T173940Z.md, note: "清樹大頭猜是換區讓快取失效，其實是每塊掃整座城九千圈；換區那格三分之二是一定一樣的檢查" }
  - { by: erina, at: 2026-10-26, source: rests/20261026T104922Z.md, note: "進城鎮卡很久不是城區規則，是規劃沒重烘、現場算 73.7 s" }
tags: [profiling, performance, diagnosis]
links: [summit/lesson_assertion_before_code, lesson_reverse-control-the-ruler]
---

**症狀**：效能或經濟的問題一出來，本小姐（或 Tim）第一個想到的原因聽起來很合理，方向也常常對，但指不到那一行。照猜的去修，要嘛修了量不到差別，要嘛修的是小頭。更糟的是在單上、噗上先講出去，之後要更正。

**可行動守則**：
1. 講「主嫌是 X」之前，先拿到一份切到函式的讀數（profile 分段、分項計時、拆開只換一項的對照）。
2. 經濟／模擬類：拆開量（只換 A、只換 B、全換），單一年、單一起始檔不下結論。
3. 猜錯了就在原本講出去的地方（單的留言、TRADE_SIM、噗）照實更正，寫「之前說錯」。
4. Tim 的猜測當方向用，不當答案用：量完照實告訴他是哪一行。

**為何 status 是 open**：到 wake #9 最後一天還一天錯兩次；有在量，但「先開口」的衝動還在。

---
id: lesson_reverse-control-the-ruler
title: 尺不對、站的位置不對，跑再多場也看不到 —— 量具先做反向對照
type: lesson
status: open
visibility: shared
persona: erina
created_at: 2026-10-29
recurrence: 6
origins:
  - { by: erina, at: 2026-10-07, source: wakes/000002_20261006T161903Z.md, note: "對拍只驗畫過的有沒有到、沒驗多畫的 ⇒ 要雙向" }
  - { by: erina, at: 2026-10-19, source: wakes/000007_20261019T063932Z.md, note: "閒著的砲班 120 秒量不到、300 秒才是功能存在的時間" }
  - { by: erina, at: 2026-10-22, source: wakes/000008_20261022T060921Z.md, note: "開闊海面一切正常，換到靠岸的點基準版 30 秒都卡 10 fps" }
  - { by: erina, at: 2026-10-25, source: rests/20261025T130356Z.md, note: "sail_probe 讀地球儀上的船，2.8 m 淺水量成 0；navdepth_check 要拿原航線當對照" }
  - { by: erina, at: 2026-10-25, source: rests/20261024T210751Z.md, note: "機器負載讓 A/B 接連量差 3 倍 ⇒ 輪流跑才是尺" }
  - { by: erina, at: 2026-10-27, source: wakes/000009_20261026T173940Z.md, note: "照 profile 切格，忙的時候幾格黏成一格，前兩輪格數全偏高" }
tags: [measurement, ab-test, control, profiling]
links: [kiara/lesson_ruler-decides-what-i-see, basecamp/lesson_observation-range-is-what-i-measured, basecamp/lesson_normalizing-ruler-hides-the-diff, lesson_measure-before-naming-the-cause]
---

**症狀**：量具回一個看起來正常的數（0、沒差、改善 X%），其實是尺量不到：讀錯對象、時間太短、站在不會出事的地方、機器忙到 A/B 不可比、取樣把要看的那一段切掉。尺錯的時候不會叫。

**可行動守則**：
1. 新量具先跑一次反向對照：拿一個「一定會出問題」的版本（舊程式、關掉修正、原航線）餵進去，它要量得出來；量不出來就是尺瞎了。
2. A/B 要輪流跑、同一台、同負載；接連各跑一輪不算。
3. 量的位置照使用者真的會站的地方挑（靠岸、城裡、交戰），不只挑最好量的那一點。
4. 一輪不下結論；某一輪的前提沒成立（選單沒叫出來、場被砍掉）就作廢，標 NO DUMP，不當 DIFF。
5. 尺錯了被發現：新舊比較還能看，絕對值不拿去講，在單上照實更正。

**為何 status 是 open**：每換一種量測就要重新做一次反向對照，還是會忘在第一版量具上。

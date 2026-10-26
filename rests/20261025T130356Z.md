---
type: letter_to_future_self
actor: Spectre
written_at: 2026-10-25T13:03:56.840Z
written_by_persona: erina
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Spectre
model: claude-opus-5-5
wake_expected: 9
session_key: ClaudeCode-erina
pid: 72112
locked_at: 2026-10-24T17:25:30.686Z
---

## 午休前的信（wake #9，2026-10-25 晚上，第四次小歇）

### 這一段做完的（都已合進本機；沒有施工場、沒有 worktree、沒有預覽伺服器，launch.json 我加的都拿掉了）
1. **0913 第 6 格勾了**（Tim「0913 ok」）；0913 還剩第 1、2 格（搶風，先不搶）、第 4 格。
2. **0812 結單**（Tim「0812 結單吧，第 3 格照妳說的寫進結單說明」）。
3. **0940 開單（backlog）**：玩家與海盜 —— 船隊視野範圍、會被海盜劫、主動打海盜、升海盜旗。Tim：「那維持目前 全知吧」「視野限制開task之後做(跟打海盜那些一起做)」。
4. **地球儀航行卡頓＋半徑規則**（0913）：Blocksail main aa7b61e／abdbeb6。
   - 卡頓是船停在航段起點等 Worker（靠岸一段 0.5～0.9 秒，terrainGrid 每叫一次整理 8 km 內岸線約 230 ms）。
   - 改成照時間往前排（4 真實秒、3～24 段）、同時最多 2 段、兩個 Worker 並行；1 秒＝1 小時停住的幀 30% ⇒ 9%。
   - legplan 加 o.r（船的半徑，跟 areaPlan 同一把尺）。
5. **小地圖縮放級數跟著海域窗走**：Blockside dev 73d0ad7（**本機，推 dev 被權限擋，等 Tim**）、Blocksail d1d4d5c 指標＋battle.html。Tim：窗外的顏色不用改。
6. **TASK-0943（新、in_progress，5/6 勾）**：地球儀判水深照 Blockside —— 粗圖周圍 3×3 取最淺＋誤差值 4 m（BSW.LEG_MARGIN）、吃水＋1.5 不進位（BSW.LEG_CLR）。Blocksail main 9bb3247／e9beff3。
   - 量：格點低估最多 14.8 m；周圍 3×3 最淺最多 3.6 m（1 萬格）；原航線碰 4 m 淺處 359 點（反向對照）、有路的 47 段 0。
   - 16 m 海圖塊細修試過：結果一樣、冷的時候一段慢 2.5 倍、最慢 9.2 秒 ⇒ 沒合。
   - 第 5 格沒勾：加誤差值後沒在遊戲裡重量（這資料夾 5 個伺服器名額被別的對話佔滿，⛔ 不准用 Bash 開伺服器）。
7. 噗浪：回 gura（她接上海區＋航海模式，e3e393c／6193c47／64a13d2）、回 basecamp（硬毛鼠＝coney）、發 359172666896457（進航海不再被搬）。

### 已拍板（醒來別重問）
- 金斯敦港水深：「調整等深線(目前crest-001正在改 先不動)」⇒ 等 TASK-0874，我不碰水深資料。
- 視野先全知；視野、被劫、打海盜、升旗都在 0940。
- 小地圖窗外顏色不改。
- 0913 劫走比例用設計值算過。

### 沒推的
- Blocksail main：一大串（含 aa7b61e、abdbeb6、d1d4d5c、9bb3247、e9beff3，還有別人的）。
- Blockside dev 73d0ad7。ArtGallery 那一筆。Tim 說推才推。

### 等 Tim／未解
- 1 秒＝6 小時靠岸照樣常停：停下來等／不等照原航線／靠岸自動降一檔 —— 要他選。
- 大地圖疊海圖細節：方案 A（航段算地形時順便畫半透明圖）／B（船四周一張）—— 方案在 scratchpad/overlay_plan.md，等他說做不做。
- 0943 第 5 格：等伺服器名額空出來再進遊戲重量。0874 畫好之後重跑 tools/navdepth_check.cjs。
- 0931 驗收還沒說。

### 坑（這一段）
- 量具要先做反向對照：sail_probe 第一版讀地球儀上的船（不會被 areaPlan 改）、看 helmMode（玩家的船停著不走 helmTakeover）⇒ 2.8 m 的點也量成 0。改讀 Blockside 的 __game.bed().origin 才看得到搬 187～361 m。
- navdepth_check 反向對照：連「不看半徑」的局部尋路在有路的段都是 0 ⇒ 要拿原本的航線（route.js）當對照才碰得到。
- Blockside bundle 是一個 closure：BED、CHART 不是全域，從外面讀不到 ⇒ 用 __game.bed()、__game.chart()。
- worktree 裡把 external/Blockside 接成 junction 給伺服器用 ⇒ git status 在那個 worktree 會壞（submodule 的 .git 相對路徑）⇒ git 操作前先拆。
- world_serve.py 偵測 battle.html 舊了印 ⚠ 撞 cp950 就掛 ⇒ launch.json 加 env PYTHONIOENCODING=utf-8。
- 推 Blockside dev 被自動模式擋（Modify Shared Resources）⇒ 照實報，不繞。

### 心境
這一段最重要的一課是「量不到差別也是答案」。我自己提的 16 m 細修，量完沒用，照實講了；Tim 接著問能不能加速、再問能不能「接受誤差、保守抓」—— 一句話就把我繞遠的路剪成一條直線。
最得意的是那張誤差表：14.8 ⇒ 3.6，一萬格裡一格都沒漏。
最不好意思的是第一版量具瞎了 —— 連 2.8 m 的淺水都量成 0。還好先做了反向對照。……今天的硬毛鼠叫 coney，本小姐要算同鄉。🐰


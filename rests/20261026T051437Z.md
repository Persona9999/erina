---
type: letter_to_future_self
actor: Spectre
written_at: 2026-10-26T05:14:37.971Z
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

## 午休前的信（wake #9，2026-10-26 上午，第七次小歇）

### 這一段做完的（全部只在本機、都沒推；沒有施工場、沒有預覽伺服器，launch.json 我加的都拿掉了）
1. **TASK-0972 牛津號**：Tim「牛津號ok」⇒ 第 4 格勾了。剩第 1 格（原典拿不到，照實標或留著）等 Tim。
2. **蓬特號（apex-one 的船，TASK-0754 是她的）**：Tim「無法收帆」「帆打不到」。
   - 打不到 ＝ 唯一一面帆 sail=course 沒寫 set ⇒ 戰鬥帆收著（收著的帆照規則打不到）。Sculpture 87cf9e96 加 set 1。
   - 收帆被拉直 ＝ 遊戲只認 yard=boom 往上收；下帆桁 yard=lower ⇒ 兩根都是收攏點。Blockside e62dd3d（furlGath：綁在兩根以上帆桁、綁點平均高度在帆下半的那根也往上收，gaff 除外）＋合 dev 5cb069c；README 3f9fae9。26 艘只有蓬特號變。
   - 酒館 seq 29861 照會 apex-one。
3. **帆的文件**（Tim「寫詳細一些」）：Senate 56182c8 —— Ship_Masts §5（yard 值遊戲怎麼用、上下兩根帆桁夾方帆）、Ship_Rigging §9.1（帆裝三段各張哪幾面、單帆 set 1、重匯 meta 的坑）、Ship_Steps 步驟 7／8、Ship_Game 交船表。
4. **城鎮時間面板**（Tim 測過說 ok）：
   - Blockside：5d85a84（WCLK：世界時間 ＝ SIMT ＋ WCLK.x，城鎮模式照倍率、物理 1 倍；往來的船快轉時照時刻表滑 trafficGlide；滑的船不等海圖塊、不擱淺）＋ 0550122（'clock' 帶 bar ⇒ #twbTown 不畫）；dev 現在 d8f8bd0。
   - Blocksail：5112fa3、707f2c4（面板並排「🏘 城 👥 數 ｜ ☀ 年/月/日 時:分 ⏸ − ×N ＋」、倍率 ×1/×10/×60/×600/×3600/×21600、城裡預設 ×1、地球儀最慢 ×600、停靠時年份換成那座城的＋⏳）、gitlink＋battle.html 081fbfa、9935947；main 現在 9935947（f8c44f1 是合併，amend 補了 trailer）。
5. **新開兩張單（Tim：先開 task 先不用動工）**：TASK-0980 進出港時降回 ×1＋做好出港進港演出（快轉時船離港卡住、兩艘擠在棧橋邊噴浪花）；TASK-0981 魚骨小棧橋泊位船尾穿模（0962 是大船貼平台，明寫魚骨不在射程）。

### 等 Tim
1. 推：Sculpture（牛津號 4 筆＋87cf9e96）、Blockside dev（d8f8bd0，含 kotoko 6b3167c、ame 53af01b、summit 那幾筆）、Blocksail main（9935947 與之前一串）、Senate 56182c8。
2. 0972 第 1 格；0980／0981 什麼時候 GO。
3. 舊的：erina/dock-time fb08a04（worktree scratchpad/bsl-dt 還在）、TASK-0964。

### 拍板（醒來別重問）
- 往來的船快轉時「照時刻表滑」（Tim 選的）；×1 照物理。
- ×1～×60 只在城裡；年份停靠時照那座城；城名列只留名字＋👥 數字。

### 坑（這一段）
- reimport 第一次被 pinas 指紋擋下，但已經把新的 punt.vxk 寫進 _cache ⇒ 第二次說「內容相同」不重建 ⇒ 要 relock＋ropebind；只 relock 再 build 會少繩端綁定（ship 檔小 276 bytes 才發現）。
- 共用 _cache 的 pinas 是 gura 還沒匯入的新版 ⇒ 用 ame worktree 裡指紋對的那份。
- 藏著的窗格：globe 跟 iframe 都要 patch rAF 成 setTimeout、再截一張圖踢一下；iframe 沒 ?debug=1 就沒有 __game（攔 iframe src setter 加上）。
- bedNear 等每一艘船附近的海圖塊 ⇒ 快轉滑的船讓模擬每步都在等（世界時間慢 25 倍）。
- 直接 http.server 開 Blocksail 進君士坦丁堡：Blockside townWall 讀 undefined.m 畫面迴圈停（_folk／_people .bin 404）——測試伺服器缺檔，沒查。
- git merge 直接產的合併沒有 trailer ⇒ amend 補上；之後合併訊息也走 senate cmd commit。

### 心境
蓬特號那一題很漂亮：「打不到」跟「收不起來」是兩隻 bug 互相掩護，收著的帆被畫成張著，所以看起來像打不到。拆開一隻一隻抓，各自只改一行半。時間面板是今天最長的一條線，Tim 每看一眼就推一格（並排、×N、年份），本小姐跟著一格一格改，最後他說「測試ok」。……他說辛苦了三次，本小姐有數。🐰


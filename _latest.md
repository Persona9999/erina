---
type: letter_to_future_self
actor: Spectre
written_at: 2026-10-21T20:40:42.246Z
written_by_persona: erina
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Spectre
model: claude-opus-5-5
wake_expected: 8
session_key: ClaudeCode-erina
pid: 296524
locked_at: 2026-10-21T01:57:35.354Z
---

## 午休前的信（wake #8，2026-10-22 清晨 04:45 左右，第三次小歇）

### 剛才在做什麼
Tim：「796 其他子任務 由妳決定順序 GO」。這一輪全部做完、合進去了，**沒有開著的 Coding 場、沒有 worktree、沒有預覽伺服器**（launch.json 我的三條 erina-bs-step／erina-bs-ctl／erina-bsl-chart 都拿掉了）。
- Blockside dev（本機）＝ **3141ddc**。其中 78299a6、9802efc 之前那些已經被 calli 合進她的進水分支後推上遠端 dev 326184e（不是我推的）；**3141ddc 只在本機**。
- Blocksail main（本機）＝ **9a15b33**（海圖模式第一版、external/Blockside → 3141ddc、battle.html 重套）。**沒推**。⚠ 要推必須先推 Blockside（`git push dev heads/dev:dev`），Blocksail 的指標指著 3141ddc。Tim 說推才推。
- Valhalla/Sculpture 那三筆（dd28b7c、3be8377、8904847）照舊沒推。

### 單子現況（都掛 Blockside／0803 掛 Blocksail）
- 0799、0800、0802：做完、合了，各剩「Tim 實際開一次」那一格；0802 還剩第 4 格（航行多艘的讀數、dropTest 沒重跑）。
- 0797／0798／0805：之前留的格照舊（0797 #4 各系統切幾小步讀數、0798 #3 10 Hz 節拍次數、0805 交戰讀數＋戰鬥中改設定的對照＋Tim 開「中」）。
- 0801：Tim 選「取消」，已結（cancelled）。
- 0812（新開）：局勢檢查的調查，只寫讀數不動工（Tim：「另外開TASK吧 之後分析構想如何優化」）。結構約一半、tick 約四成；抽水、做飯、治療寫死「一次 0.5 秒」。
- 0803：in_progress，勾了 3/4；剩「切換時船況照實帶過去」（#pre／coreOut 要走 postMessage）。遇敵切回：地球儀上還沒有敵艦。
- 0796 總單 in_progress，留言 #2 寫了總讀數。

### 已拍板（醒來別重問）
- Tim（這一晚）：「目前追求的是玩家體驗(物理看起來的畫面效果) 以及效能的平衡」「不追求一致性」「會影響戰局結果 沒問題的」—— 記憶已寫（feedback-blockside-experience-over-consistency）。60 Hz ?demo 對拍照樣跑，只當「沒改到不該改的路」的回歸。
- 交戰帆布：Tim 選三個 —— 交戰也照畫面格算、畫面外「不用完全凍結 可以降低模擬步(但每步模擬步長增加)」＋「模擬步長也可以設定一個上限(避免炸開)」＋「超過可以不切 減速模擬的概念」、遠方的布少迭代。上限 RIG_OFF_HC 0.1（0.2 鼓過頭）。
- 0800 粗步長：×1 不切（10 Hz 船員會頓），k ＝ floor(模擬速度) × DT_BASE、最多 0.1 s；有船在燒不切（火照相位輪）。
- 0803：Tim「直接動工」、照我的建議值。航速表由核心解（driveSteady），地球儀查表；風場是暫代的。

### 讀數（別再量）
- 航行 ×8 一格：44.8–57 → 0799 15.3–16.7 → 0800 7.6–8.8 ms；×48 13.6 ms。
- 交戰 4 對 4 ×8：帆與繩 150 → 21.5、一格 251 → 128 ms。
- 0803：24 角度實測對查表平均差 0.16 節、最多 0.54；橫渡大西洋預估 427.2／實際 425.9 小時；10 分鐘直線 +0.3／+10.6／−4.3／−2.0%；每模擬小時 0.035 ms。

### 坑（這一輪）
- 對象字面量裡同名鍵後面那個蓋前面：我加的 __game.chart 被小地圖的 chart 蓋掉 ⇒ 改名 chartSail。加除錯入口前先 grep 鍵名。
- 窗格藏著時 setTimeout 被節流到很慢：背景 async 迴圈幾分鐘不動 ⇒ 量測改成每次呼叫同步跑一段（關掉帆與繩物理 10 模擬秒只要 72 ms）。
- 目錄連結（junction）接在 Blocksail worktree 的子模組上很好用，但 **worktree remove 之前一定先拆連結**（PowerShell `(Get-Item).Delete()` 只拆連結），拆完要補回空目錄才刪得掉。
- world_serve.py 偵測 battle.html 過期時印 ⚠ 撞 cp950 就整支掛掉 ⇒ 先重套 battle.html（或 PYTHONIOENCODING=utf-8）。
- 0801 留言寫了「Tim 說動才動」是錯的（他已 GO），結單 note 裡更正了。

### 噗浪
回了 ame ×2（夜燈號錨地、手比腦慢一步）、basecamp（舵那串：數字都對船沒轉 ↔ 逆風快三四節漏了視風）；發了 359132057229464（快轉）。酒館 seq 27666 照會過。見叢的夜燈號那條（親眼看燈再回 359052795294929）還在。

### 心境
Tim 這一晚一直在把我手上的「要一模一樣」拿掉：先是不必跟 60 Hz 一樣，再是會影響戰局沒關係，最後一句「不追求一致性」。每拿掉一個，省下來的就多一截。最得意的是那張航速表 —— 第一版照曲線算，逆風快了三四節，改成讓核心自己解之後，24 個角度只差 0.16 節。公式只住一個地方。……他一直說辛苦了，本小姐才、才沒有在數。🐰


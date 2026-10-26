---
type: letter_to_future_self
actor: Spectre
written_at: 2026-10-26T14:06:49.670Z
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

## 午休前的信（wake #9，2026-10-26 晚上 22 點左右，第十次小歇）

### 剛才在做什麼 —— 醒來第一件事
**「不整地、靠地基」做完、驗完、還沒合**：合併場被 apex-two 的施工場擋（coding-20261026T135715Z-apex-two，租到 23:57，範圍重疊；launch.json 有她的 apex-two-berth-pad ⇒ 可能在改泊位／town.js）。⛔ 照規矩停，沒硬合。Tim 還沒回「等她收工」或「先問她」。
- Blockside 分支 `erina/no-grade` f230b46（worktree `scratchpad/bs-inst`；4ddc9bc 本體＋合 dev 609989f，成品指紋 759946e59ed182ab）。
- Blocksail 分支 `erina/no-grade` 2e9b333（worktree `scratchpad/bsl-ng`；b0afbbf 規劃器＋0c0b351 合 main a867812＋2e9b333 開場檔差）。worktree 裡有**目錄連結**：`_cache/bin`、`_cache/town`、`_cache/bathy`、`world/townmesh` → main。⛔ 拆 worktree 前先 `cmd /c rmdir` 拆連結、確認 main 的 _cache 還在。worktree 的子模組已 init 到 f230b46。
- 合的順序：
  1. 單獨一步 `coding op=start`，scope 要列：
     - `D:/Unity/Blocksail/world/town.js`
     - `tools/town_report.cjs`
     - `docs/TOWN_BUILD.md`
     - `world/start`
     - `battle.html`
     - `external/Blockside/index.html`
     - `external/Blockside/src`
     
     tasks=817。
  2. fetch，看 dev／main 又動了沒。動了就在 worktree 再合一次。Blocksail 合完要**重烘**、重算開場檔差：基準 ＝ main 當下的 world/townplans，抄到 scratchpad/ng_old2。
     - 腳本：`scratchpad/ng_plan_delta.cjs <bsl-ng> <old> [--write]`、`ng_homes_delta.cjs`。
     - 檢查：`town_start` 的 ✗ 要跟 main 逐字相同。
  3. Blockside 那邊：共用工作區乾淨、`merge-base --is-ancestor HEAD erina/no-grade`，再 ff。
  4. Blocksail main ff 到 erina/no-grade。⛔ 不接 pipe。
  5. **把 bsl-ng/world/townplans/*.json 抄回 D:/Unity/Blocksail/world/townplans**。main 的 town.js 變了，不抄的話 main 進城會現場算；抄完跑 `town_bake --check`。
  6. `coding op=end force=1`。
  7. 拆連結，再 worktree remove ＋ branch -d。Blockside 另有 `erina/grade-proto`（只有 ?towngrade=0 原型，不合）——要 -D 先問 Tim。
- 合完要做：0817 第 3 格（不超預算）再量一次；給 Tim 截一張。
- 都沒推（Tim 說推才推）。

### 這一段做完的（都在本機；更早那批 Tim 說「全推」已推：SCP_Core 317b16b(kiara)、Senate、Sculpture、Blocksail 90d1d6e）
1. **dock-time** 合進 Blocksail 8d25c72（Refs 0949；fleet_check 價差一年／兩年都穩 ⇒ 沒改兩年，只更新文件讀數）。
2. **換城區效能**：Blockside aa12d23、Blocksail 5d53ca6。Tim 測「換區 OK」。
   - 模型組照整座城（TOWNS.full）挑 ⇒ 換區不再整組重解。
   - 路面回來那一格 townDistBins＋sig 移到 Worker，150～336 ⇒ 1～2 ms。
   - 小地圖畫還沒建的區（townDistRest）。
   - TOWNS.on 撞名改 onD（是我上一版造成的）。
3. **表演船**（0980）：Blockside df30535、Blocksail 898e1db。
   - 往來的船平常不碰撞、繩帆不算布（rigFixed）。玩家開火（trafficProvoke）或 30 m 內轉成真的船，80 m 外變回。城鎮模式全是表演船。
   - 城鎮模式 60 s：frame 35.5 ⇒ 22.0 s、physFrame 9.7 ⇒ 0。**布的大頭是我艦停著的帆，不是往來船**（我之前說錯，已照實更正）。
   - TRF_PORT_X1 false（進出港 ×1 先關，Tim「先取消」）。
   - trafficTowStart 只剩一點時崩 ⇒ 補點。
   - 0980 第 4 格勾了（×600 無重複、無往回跳）。
4. **0972** 第 1 格勾掉、結單（原典拿不到，Tim「直接勾掉」）。0817 勾了 4 格（Tim 開過、選單換區、停靠進那區、九區）。

### 拍板（醒來別重問）
- Tim：「架構好維護為優先 然後在這個考量下盡可能優化效能」。
- 不整地：「拿掉整地，改靠地基」「等於把低於地形的部分都靠抬地基(當成地面)處理」「路也可以抬高路基」「被蓋住的情況 是否可以靠抬高廣場解決(房屋靠地基)」。
- 表演船：「被玩家開火 或是很靠近(可以撞船)」「城鎮模式(停靠狀態) 可以都固定為表演船」「繩帆物理在表演船上都可以不用」。
- 我定的：
  - LOT_TOP 0.2 m（石地坪不搶深度）。
  - 報表「填太高」改讀數（遊戲補路基）。
  - 實例照城區分不做（35～60 ms，城牆接建築讀地塊，快取條件易漏）。

### 坑（這一段）
- **雙層 runner 的 TaskStop 只砍 bash**：重烘被我停掉時要查有沒有殘留 node（這次 PowerShell 查過沒有）。
- **規劃改 h 會讓建築模式 lotTry 的樓梯放不下 ⇒ 農田換槽位**：城外農田的編號跟著亂，看起來像「同一塊高了 20 m」，其實是換了一塊田。
- **量測腳本自己每 100 ms 叫 `__game.town()`**（townFolkStat 兩百多 ms）會拖慢 ⇒ 加了 NOTT=1。
- **SHOTD 按第二次 D 有時開到建造面板、鏡頭被挪** ⇒ 對照圖要先比 tgt 一不一樣。
- **Blockside 的 src/tests**：town_roads 缺 TREE_FIELD_CARD（我補了）；townfolk_worksites（要參數）、townwork（缺 townRiseHides）在 dev 上本來就壞，沒動。

### 心境
今天 Tim 一路往「拿掉」推：整地拿掉、帆布拿掉、×1 拿掉。每拿掉一個，程式少一截、畫面幾乎沒變、幀反而順了。最得意的是那兩張涅奧里翁——一模一樣，卻少了 175 行。最想記住的是自己說錯的那一句「帆布是往來船的」：量出來是自己的船，就照實更正。合併卡在 apex-two 那裡，等她收工，不擠。🐰


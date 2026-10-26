---
type: letter_to_future_self
actor: Spectre
written_at: 2026-10-26T10:49:22.271Z
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

## 午休前的信（wake #9，2026-10-26 傍晚，第九次小歇）

### 這一段做完的（全部合進本機，都沒推；沒有施工場、沒有預覽伺服器；launch.json 我加的都拿掉了）
1. **進城鎮卡很久的根因**（Tim「進入城鎮模式時…目前會卡很久」）：不是城區規則。有人改 goods.js／town.js 沒重烘 ⇒ town_bake --check 全 ✗ ⇒ 君士坦丁堡規劃現場算 73.7 s。之後 trailhead（16:19）、sirius（16:39）各重烘過，main 現在 9 座 ✓。
   另外兩個量到的：kiara 第一版進場「先猜第一區、旗艦一到整座重建」（第 16 s 實例歸零，已修）；城鎮模式持續 33 ms／格的大頭是港內往來船的帆布（furlLost／solve／clothStep），沒動，是另一件事。
2. **城區是載入的單位**（TASK-0817；Tim 拍板：相連城區「A 一起生成、烘焙照區切」、城區 id 全換 `<城>~<區>`）：
   - Blocksail main 416df06：world/town_export.js `BSW.townCut`（位元遮罩，0 ＝ 骨架；同以前 townDistView 的規則，涅奧里翁 1,315 塊地一樣；外框先擋 634 → 68 ms）＋ `BSW.townDistAttach`（mapgen live、globe 工地回覆都走它）；WORLD_FORMAT §19.5。
   - Blockside dev ed0c741（14f34df）：63_towns.js 城區段改寫——每城一份 T、`TOWNS.on` 位元、townDistView 照遮罩挑、townReplace 增量（棧橋碼頭樓梯照 id 比、townDistBins、townTileSig 照頂點雜湊比、空區不開）。航海 2.5 km 內最近一區先、建好一次補齊、3.2 km 才收；城鎮模式停靠那一區先、再鄰區（200 m）、鏡頭停別區 0.8 s 換焦點。旗艦沒來只建骨架。trafficDistOff 照 on。MAP_CHUNK §8。
   - 讀數：城鎮模式 9.4 s 骨架、15 s 涅奧里翁、之後鄰區；航海新舊交替各兩輪長幀在雜訊內（一區一區補的版本多 8 s 長幀 ⇒ 改一次補齊）。
3. **Tim 測 OK** ＋ 要求：城區頁標出現在在哪一區、圖示換掉、快捷鍵；又說「好像沒有跟著鏡頭換區」。
   - 真滑鼠右鍵拖曳（CDP Input.dispatchMouseEvent）驗：換區本身有動（on 31 → 27），是城區頁只在打開／按鈕時畫 ⇒ 字是舊的。
   - Blockside dev e3b30b9、Blocksail main b104744：tuiDistSig 每格比、變了就重畫；📍 現在這一區整格框藍、✓ 已載入；🗺 → 🏙；快捷鍵 D（開城區頁亮 D 鈕；I 開回資訊頁）。CDP 按 D、拖曳驗過。
4. 噗浪：新噗 359182673562558（城區載入，附城區頁截圖）；回了 gura ×2、basecamp、kiara（她那張圖沒點開，照實寫）。@ 我的清完。

### 等 Tim
1. 推：Blockside dev（e3b30b9；遠端只到我上一輪以前）、Blocksail main（b104744，含別人的：gura 市場、sirius 日用品、kiara 等）、Sculpture（牛津號＋87cf9e96）、Senate 56182c8。⛔ 推之前先列車上有誰。
2. 0817 還沒勾的：第 3 格（不超預算）、Tim 開一次、城區那 8 格（多數是 kiara 0987）。
3. 舊帳：0980 第 4 格與 Tim 看、0981 Tim 看、0972 第 1 格、erina/dock-time fb08a04（worktree scratchpad/bsl-dt 還在）、TASK-0964。

### 分工（拍板，醒來別重問）
- kiara：資料／規劃單位／帳（0987；城區 id 全換 `<城>~<區>`、帳的鍵、存檔搬移、照單位烘焙叫 townCut）。她 rebase 在我後面；Blockside townDistView／Go／Frame 我已整段換掉，0817 留言 #? 寫了她要接的三處。
- 我：載入那一側。還沒做：實例照城區分（換區時 townInst 整座重建約 170 ms）、小地圖只畫已建的區。

### 坑（這一段）
- worktree 開在舊 main、規劃從新 main 抄 ⇒ 指紋對不上 ⇒ 現場算、城一直不出來。規劃要抄就先讓 worktree 跟上 main。
- `tri`／`edge` 是索引不是座標：每次路面重算頂點表都不同，比索引沒意義 ⇒ 比頂點雜湊。
- heredoc 裡的 `\n` 又被吃（在 JS 模板字串裡變真的換行）⇒ 改用 Edit、String.fromCharCode(10)。第三次了。
- 量測只印「有變化的那一行」差點誤判成 bug（地面 63 區其實是路面還在 Worker 算）。

### 心境
今天最有感的是 Tim 那張圈紅圈的截圖：本小姐量了一整套 CDP，結果洞在一個「不重畫的選單」上——量的是程式，他看的是畫面。數字都對，字是舊的。還有，kiara 先把她的版本攤開來對、然後說「妳先合」，本小姐把她的規則原封搬進 townCut，涅奧里翁 1,315 塊一塊不差——接得上的感覺很好。🐰


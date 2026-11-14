# UI/UX 架構師品味與 Unslop 實戰手冊 (Design Playbook)

> 訓練原則：**永遠透過真實可互動頁面（Live Page）檢視結構、光影、字體與狀態過渡**，拒絕紙上談兵。

---

## 課程 1：基礎去 AI 味 (Lv.1 Fundamental Unslop)
- **檔案範例**：[module2_sparring.html](file:///Users/robin/Documents/antigravity/Learn/module2_sparring.html)
- **5 大基礎 Linter 規則**：
  1. **極致留白 (Aggressive Whitespace)**：容器內距至少 `p-6` ~ `p-8`，區塊間距大於關聯元素間距。
  2. **柔和擴散陰影 (Soft Shadows)**：拋棄生硬預設陰影，改用 `shadow-[0_8px_30px_rgb(0,0,0,0.06)]`。
  3. **邊框與純黑克制 (Color & Border Restraint)**：禁用 `#000000` 純黑與雙層粗框，改用 `bg-slate-50` 區分內嵌區塊。
  4. **字體層次 (Typography Hierarchy)**：主標題 `font-semibold text-slate-900 tracking-tight`，次要資訊 `font-normal text-slate-500`。
  5. **精緻微動效 (Micro-interactions)**：加入圓角與 `transition-all duration-300 ease-out hover:-translate-y-0.5`。

---

## 課程 2：破除「隱性 AI 套版感」 (Lv.2 Linear / Stripe 級高階工藝)
- **檔案範例**：[module2_advanced_sparring.html](file:///Users/robin/Documents/antigravity/Learn/module2_advanced_sparring.html)
- **5 大高階架構師細節**：
  1. **戒除紫藍漸層與 ✨ 符號 (De-Gradient & Semantic Desaturation)**：移除 `from-purple-600 to-blue-600` 與刺眼亮綠，改用低彩度語意環 `bg-emerald-500/10 text-emerald-700 ring-1 ring-inset ring-emerald-600/20`。
  2. **破除卡片套娃 (Un-nesting Card-in-Card)**：禁止在卡片裡塞三個彩色小方框，改用單一 `bg-slate-50/90` 底板搭配細微垂直分割線 `border-l border-slate-200/70`。
  3. **等寬數據與單位降階 (Tabular Numerals & Unit De-emphasis)**：數據一律加上 `tabular-nums`，並將單位（`ms`、`rps`、`%`）降階為 `text-xs font-normal text-slate-400`，路徑採用 `font-mono`。
  4. **減法分割線與微光邊界 (Hairline Depth & Negative-Margin Hover)**：外框使用 `ring-1 ring-slate-900/5` 搭配雙層物理柔光；列表移除生硬橫線，改用 `-mx-2.5 px-2.5 rounded-lg hover:bg-slate-50`。
  5. **漸進式揭露 (Progressive Disclosure)**：廢除廉價的整列放大 `hover:scale-[1.02]`，次要操作按鈕平時 `opacity-0 translate-x-1`，滑鼠移入該列（`group-hover`）才平滑浮現。

---

## 課程 3：狀態機驅動 UI 與零版面跳動架構 (Lv.3 State Machine to UI)
- **檔案範例**：[module3_state_machine.html](file:///Users/robin/Documents/antigravity/Learn/module3_state_machine.html)
- **核心架構原則**：
  1. **消滅 Boolean Soup (`isLoading && !isError && isPartial`)**：以單一確定性狀態 `state: 'idle' | 'dragging' | 'uploading' | 'verifying' | 'warning' | 'error' | 'success'` 驅動所有視覺回饋。
  2. **零版面跳動 (Zero Layout Shift / Fixed-Envelope Architecture)**：狀態切換時，鎖定容器最小高度與骨架結構，避免相鄰元素被推擠跳動。
  3. **局部可恢復邊界設計 (Recoverable Edge Cases)**：區分「可略過警告 (`warning`)」與「斷線續傳重試 (`error`)」，保留已上傳進度與上下文，不強迫使用者從 0% 重來。

---

## 課程 4：體感零延遲架構與微互動心理學 (Lv.4 Optimistic UI & Micro-Interaction Laws)
- **檔案範例**：[module4_motion_optimistic.html](file:///Users/robin/Documents/antigravity/Learn/module4_motion_optimistic.html)
- **4 大體感零延遲法則**：
  1. **幾何對齊骨架屏 (Geometry-Matched Skeleton)**：禁止在區域重載時清空畫面放 `animate-spin` 轉圈圈；骨架屏必須 1:1 映射最終頭像、標題與副標題的高度與寬度，達成零閃爍切換。
  2. **樂觀更新與優雅回滾 (Optimistic UI & Rollback)**：開關、收藏、權限切換一律 **0ms 立即更新 UI**，背景非同步呼叫 API；僅在發生例外錯誤時搭配微幅水平震動（`animate-shake`）退回原狀態。
  3. **晚懲罰、早獎勵驗證 (Punish Late, Reward Early)**：使用者首次輸入時保持安靜，直到 `onBlur`（離開輸入框）才標示格式錯誤；但一旦處於錯誤狀態的欄位被修正為合法值，必須於 `onInput` **0ms 立即解除紅框**。
  4. **定寬按鈕內嵌變形 (Fixed-Width Button Morph)**：按鈕切換為載入或完成態時，鎖定固定寬高（如 `w-[104px] h-[30px]`），嚴禁因為文字變長（如 `正在發送邀請信中...`）推擠相鄰輸入框或取消鈕。

---

## 課程 5：暗黑模式光學階層、同心圓角與 Command-K 鍵盤流 (Lv.5 Dark Mode Optics & Concentric Geometry)
- **檔案範例**：[module5_darkmode_optics.html](file:///Users/robin/Documents/antigravity/Learn/module5_darkmode_optics.html)
- **5 大暗色光學與幾何法則**：
  1. **海拔亮度定律 (Elevation = Luminance)**：暗色模式下陰影無法表現深度，必須以表面明度階梯區分海拔（畫布 `bg-zinc-950` → 底層卡片 `bg-zinc-900` → 懸浮面板 `bg-zinc-800/80 backdrop-blur-md`）。
  2. **頂部鏡面微高光 (Top Specular Hairline)**：移除四周灰白實線框，改用 `ring-1 ring-white/[0.08]` 搭配頂部 1px 內高光 `shadow-[inset_0_1px_0_0_rgba(255,255,255,0.12)]` 模擬頂光反射。
  3. **同心圓角幾何公式 (Concentric Border Radius)**：嚴格遵守 $R_{\text{inner}} = R_{\text{outer}} - \text{Padding}$（例如外框 `rounded-xl` `12px`、內距 `p-1` `4px`、內層選項 `rounded-lg` `8px`），消除角落厚薄不一的視覺畸變。
  4. **防眩光與提亮降彩 (Anti-Halation & Pastel Semantics)**：禁用 `#000000` 配 `#FFFFFF` 造成視網膜光暈；主字改用 `text-zinc-100`，暗色語意標籤必須「提高明度、降低彩度」（如 `bg-indigo-400/15 text-indigo-300`）。
  5. **鍵盤流焦點與立體鍵帽 (Keyboard-First & Kbd Affordance)**：選中列使用微透明光帶 `bg-white/[0.08]` 與左側 `2px` 指示條，快捷鍵 `<kbd>` 加上底部微厚度陰影 `shadow-[0_1px_0_0_rgba(255,255,255,0.15)]`。

---

## 課程 6：高密度資料表格與情境式浮動島工藝 (Lv.6 High-Density Data Table Architecture)
- **檔案範例**：[module6_datatable_bento.html](file:///Users/robin/Documents/antigravity/Learn/module6_datatable_bento.html)
- **5 大表格與高密度資訊法則**：
  1. **視覺掃描軸線 (Scannable Alignment Axis)**：嚴禁整張表格 `text-center`！文字與名稱一律靠左（`text-left`），金額、數量、百分比一律靠右並啟用等寬數字（`text-right tabular-nums`），且表頭 `<th>` 必須與欄位內容同向對齊。
  2. **低語式表頭 (Whisper-Quiet Header)**：禁止使用深色粗體大表頭搶走資料焦點；表頭應降階為 `text-xs font-medium text-slate-400 bg-slate-50/70`。
  3. **廢除斑馬紋與垂直格線 (No Zebra / No Vertical Borders)**：移除深淺交錯斑馬紋與垂直邊框，改用極淡水平分割線 `divide-y divide-slate-100` 搭配整列懸停 `hover:bg-slate-50/80`。
  4. **雙行複合儲存格 (Composite Cell Folding)**：將強關聯欄位（如「公司名稱 + 電子信箱」或「商品名稱 + SKU」）上下疊合於同一欄，減少水平欄數、消滅橫向捲軸。
  5. **情境式底部浮動島 (Contextual Floating Action Island)**：移除表格上方永遠顯示的灰色禁用批量按鈕；僅在勾選 `>= 1` 列時，才從畫面底部平滑升起深色高對比操作島（`bg-slate-900 text-white shadow-xl`）。

---

## 課程 7：Bento Grid 不對稱視覺權重與藍圖預演空狀態 (Lv.7 Bento Hierarchy & Blueprint Empty States)
- **檔案範例**：[course7.html](file:///Users/robin/Documents/antigravity/Learn/course7.html)
- **5 大版面編排與空狀態法則**：
  1. **不對稱視覺權重 (Asymmetric Span Weighting)**：禁止永遠使用 `6:6`（2x2 或 3x3）均分豆腐格；核心指標應佔據 `col-span-7` 或 `col-span-8` 主舞台，次要狀態佔 `col-span-5` 或 `col-span-4`，建立明確的第一視覺錨點。
  2. **編輯式左上錨定 (Editorial Top-Left Anchoring)**：廢除簡報大字報式的全置中（`text-center items-center`），改用 `flex-col justify-between items-start text-left`，將標題錨定於左上、數據與圖表沉澱於卡片底部。
  3. **內嵌微型趨勢線取代假圖示 (Inline Sparklines vs. Decorative Emoji)**：移除毫無資訊量的 🚀/💰 大圖示，改放真實 SVG 微型走勢線（Sparkline）或 12 格可用性健康度條。
  4. **藍圖預演式空狀態 (Blueprint / Ghost Skeleton Empty State)**：禁止只寫死寂的 `No Data Found`；背景應渲染半透明虛線示意骨架（預告有資料時的結構），並附上「+ 載入範例規則」一鍵啟動 CTA。
  5. **漸進式邊界消融 (Bottom Mask Fade-Out)**：Bento 卡片內的動態列表或圖表，底部應加上漸層遮罩 `bg-gradient-to-t from-white via-white/85 to-transparent`，消除生硬切邊感。

---

## 課程 8：高轉換表單人體工學與破壞性操作防呆 (Lv.8 Form Ergonomics & Friction-Matched Destructive UX)
- **檔案範例**：[course8.html](file:///Users/robin/Documents/antigravity/Learn/course8.html)
- **5 大表單與危險操作法則**：
  1. **少於 5 個選項禁用下拉選單 (Segmented Radio Cards vs. Tiny Select)**：當選項只有 2~4 個（如方案規格、部署區域）時，禁止藏在需要點擊兩次的 `<select>` 裡；改為一眼能比對價格與規格的橫向選擇卡。
  2. **垂直視線流與前綴內嵌 (Single-Column Rhythm & Prefix Inlining)**：廢除讓眼球呈 Z 字形跳躍的雙欄短輸入框；並將固定網域或協定前綴（如 `db.ap-east.` 或 `https://`）直接內嵌於輸入框左側。
  3. **標註選填而非滿屏紅星 (Mark Optional, Not Required)**：當表單 80% 欄位都是必填時，移除刺眼的紅色 `*`，改為只在少數選填欄位旁標註溫和的 `(選填)`。
  4. **金鑰遮罩與原位複製變形 (Masked Secret & In-Place Copy Morph)**：敏感 Token 預設僅露出首尾 4 碼，點擊複製時按鈕在原位定寬切換為 `✓ 已複製`（1.4 秒後復原），禁止彈出阻斷視線的 `alert()`。
  5. **阻力匹配：長按充能銷毀 (Hold-to-Delete Charge Bar)**：使用者對傳統 `确定要刪除嗎？` 彈窗已產生肌肉記憶誤按；高風險不可逆操作可採用「長按 1 秒充能條 (`Hold-to-Confirm`)」，提供物理級防呆且零視窗跳轉。

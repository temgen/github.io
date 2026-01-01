<!doctype html>
<html lang="ja">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<title>画像ヒント＋4択（楕円・四角ヒント対応 / 編集つき）</title>
<style>
:root{ --headerH:56px; --controlsH:72px; --pad:10px; }
body{margin:0;font-family:-apple-system,BlinkMacSystemFont,Segoe UI,Roboto;background:#f8fafc;overflow:hidden;}
header{box-sizing:border-box;padding:10px 12px;background:#111827;color:#fff;display:flex;align-items:center;justify-content:space-between;gap:10px;}
#qText{font-size:18px;line-height:1.25;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;flex:1;}
#editBtn{font-size:14px;padding:8px 12px;border-radius:10px;border:1px solid rgba(255,255,255,.35);background:rgba(255,255,255,.08);color:#fff;}
main{box-sizing:border-box;padding:var(--pad);height:calc(100vh - var(--headerH));display:flex;flex-direction:column;gap:10px;}
#imageWrap{position:relative;width:100%;flex:1;display:flex;align-items:center;justify-content:center;background:#fff;border:1px solid #cbd5e1;border-radius:10px;overflow:hidden;}
canvas{display:block;width:auto;height:auto;max-height:calc(100vh - var(--headerH) - var(--controlsH) - (var(--pad) * 3));touch-action:none;background:#fff;}
#overlayMessage{position:absolute;inset:0;display:none;align-items:center;justify-content:center;font-size:56px;font-weight:bold;background:rgba(255,255,255,0.7);pointer-events:none;}
#overlayMessage.ok{color:#16a34a;} #overlayMessage.ng{color:#dc2626;}
#toast{
  position:absolute;left:12px;right:12px;bottom:12px;
  background:rgba(17,24,39,0.92);color:#fff;
  padding:16px 14px;border-radius:14px;
  font-size:22px;line-height:1.25;
  display:none;
}
#controls{height:var(--controlsH);display:flex;justify-content:center;gap:16px;align-items:center;}
button{padding:14px 24px;font-size:18px;border-radius:12px;border:none;background:#2563eb;color:#fff;}
button.secondary{background:#64748b;} button:disabled{opacity:.5;}
#choices{position:fixed;inset:0;background:rgba(0,0,0,.5);display:none;align-items:center;justify-content:center;}
#choices .panel{background:#fff;padding:20px;border-radius:16px;width:80%;max-width:420px;}
.choice{margin:10px 0;padding:12px;border:1px solid #cbd5e1;border-radius:10px;font-size:18px;}

/* editor */
#editModal{position:fixed;inset:0;display:none;background:rgba(0,0,0,.45);align-items:center;justify-content:center;}
#editModal .box{background:#fff;width:min(980px,94vw);max-height:88vh;overflow:auto;border-radius:16px;padding:16px;}
.row{display:flex;gap:12px;align-items:center;flex-wrap:wrap;}
.badge{font-size:14px;padding:6px 10px;border-radius:999px;background:#eef2ff;color:#1e3a8a;}
.field{margin-top:12px;}
label{display:block;font-size:14px;color:#334155;margin-bottom:6px;}
input[type="text"]{width:100%;font-size:16px;padding:10px 12px;border:1px solid #cbd5e1;border-radius:12px;box-sizing:border-box;}
.choiceRow{display:grid;grid-template-columns:34px 1fr;gap:10px;align-items:center;margin-top:8px;}
.smallBtn{padding:10px 14px;font-size:14px;border-radius:12px;border:none;background:#2563eb;color:#fff;}
.smallBtn.secondary{background:#64748b;}
.smallBtn.danger{background:#dc2626;}
.smallBtn.active{background:#16a34a;}
hr{border:none;border-top:1px solid #e2e8f0;margin:14px 0;}
.note{font-size:13px;color:#64748b;}
.tabs{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px;}
.tabBtn{padding:8px 12px;border-radius:999px;border:1px solid #cbd5e1;background:#fff;color:#0f172a;font-size:14px;}
.tabBtn.active{background:#111827;color:#fff;border-color:#111827;}
.tabPanel{display:none;} .tabPanel.active{display:block;}
#editCanvasWrap{border:1px solid #cbd5e1;border-radius:12px;overflow:hidden;background:#fff;height:min(72vh,680px);display:flex;align-items:center;justify-content:center;}
#editCanvas{width:auto;height:auto;touch-action:none;display:block;}
#hintTools{display:flex;gap:10px;align-items:center;flex-wrap:wrap;margin-top:10px;}
#hintText{width:100%;min-height:64px;font-size:16px;padding:10px 12px;border:1px solid #cbd5e1;border-radius:12px;box-sizing:border-box;}
</style>

<style id="responsiveSafeViewport">
:root{ --real-vh: 100vh; }
html,body{height:100%;}
/* iOS Safari の実表示高さに合わせる */
.appRoot{height:var(--real-vh);}

/* 下部UIは安全領域を確保 */
.safeBottomPad{ padding-bottom: calc(env(safe-area-inset-bottom, 0px) + 10px); }

/* iPad/iPhone向け：ボタンが見切れにくいサイズ */
button, .btn, .smallBtn{
  font-size: clamp(14px, 2.1vw, 18px);
  padding: clamp(10px, 2.0vw, 14px) clamp(12px, 2.4vw, 18px);
}
</style>


<style id="revealButtonNoClip">
/* iPad/iPhone: 「答えがわかった」ボタンをビューポート基準で固定して見切れ防止 */
@media (max-width: 1024px){
  #btnReveal{
    position: fixed !important;
    right: 12px !important;
    bottom: calc(env(safe-area-inset-bottom, 0px) + 12px) !important;
    z-index: 50 !important;
    max-width: min(44vw, 280px);
    box-shadow: 0 6px 18px rgba(0,0,0,0.18);
  }
  /* ボタンが被らないよう右/下に余白を確保 */
  #main, .main, #content, .content{
    padding-right: min(46vw, 300px);
    padding-bottom: calc(env(safe-area-inset-bottom, 0px) + 80px);
  }
}
</style>

</head>
<body class="appRoot">

<header>
  <div id="qText">（問題文を設定してください）</div>
  <button id="editBtn">編集</button>
</header>

<main>
  <div id="imageWrap">
    <canvas id="canvas"></canvas>
    <div id="overlayMessage"></div>
    <div id="toast"></div>
  </div>
  <div id="controls">
    <button id="knowBtn">答えがわかった</button>
    <button id="nextBtn" class="secondary" style="display:none;">次へ</button>
    <button id="restartBtn" class="secondary" style="display:none;">もう一回</button>
  </div>
</main>

<div id="choices">
  <div class="panel">
    <div class="choice" data-i="0"></div>
    <div class="choice" data-i="1"></div>
    <div class="choice" data-i="2"></div>
    <div class="choice" data-i="3"></div>
  </div>
</div>

<!-- 編集モーダル -->
<div id="editModal">
  <div class="box">
    <div class="row" style="justify-content:space-between;">
      <div class="row">
        <span class="badge" id="editIndexBadge">問題 1 / 10</span>
        <label class="row" style="gap:6px;font-size:14px;color:#0f172a;">
          <input type="checkbox" id="editEnabled">この問題を使う
        </label>
      </div>
      <div class="row">
        <button class="smallBtn secondary" id="editPrev">← 前へ</button>
        <button class="smallBtn secondary" id="editNext">次へ →</button>
        <button class="smallBtn danger" id="editClose">閉じる</button>
        <button class="smallBtn" id="exportHtml">書き出し</button>
      </div>
    </div>

    <div class="tabs">
      <button class="tabBtn active" data-tab="tabQ">問題設定</button>
      <button class="tabBtn" data-tab="tabH">画像・ヒント</button>
    </div>

    <div id="tabQ" class="tabPanel active">
      <hr>
      <div class="field">
        <label>問題文（1行）</label>
        <input type="text" id="editQuestion">
      </div>
      <div class="field">
        <label>4択（正解にチェック）</label>
        <div class="choiceRow"><input type="radio" name="correct" id="r0" value="0"><input type="text" id="c0"></div>
        <div class="choiceRow"><input type="radio" name="correct" id="r1" value="1"><input type="text" id="c1"></div>
        <div class="choiceRow"><input type="radio" name="correct" id="r2" value="2"><input type="text" id="c2"></div>
        <div class="choiceRow"><input type="radio" name="correct" id="r3" value="3"><input type="text" id="c3"></div>
        <div class="note" style="margin-top:10px;">
          ・最大10問スロット。ONの問題だけ出題されます。<br>
          ・変更は自動保存（端末内）されます。
        </div>
      </div>
      <hr>
      <div class="row" style="justify-content:flex-end;">
        <button class="smallBtn secondary" id="editReset">初期状態に戻す</button>
      </div>
    </div>

    <div id="tabH" class="tabPanel">
      <hr>
      <div class="field">
        <label>問題の画像（この問題専用）</label>
        <input type="file" id="imgInput" accept="image/*">
        <div class="note" id="imgStatus">（未設定）</div>
        <div class="note">・読み込んだ画像は端末内に保存されます。</div>
      </div>

      <div class="field">
        <label>ヒント領域（楕円・四角）</label>
        <div id="editCanvasWrap"><canvas id="editCanvas"></canvas></div>

        <div id="hintTools">
          <span class="badge" id="selBadge">未選択</span>
          <button class="smallBtn secondary" id="btnNewEllipse">新規楕円</button>
          <button class="smallBtn secondary" id="btnNewRect">新規四角</button>
          <button class="smallBtn secondary" id="btnNewPoly">新規多角形</button>
          <button class="smallBtn secondary" id="btnPolyDone" style="display:none;">多角形確定</button>
          <button class="smallBtn secondary" id="btnPolyUndo" style="display:none;">1点戻す</button>
          <button class="smallBtn secondary" id="btnDelete">削除</button>
          <button class="smallBtn secondary" id="btnClearHints">全消し</button>
        </div>

        <div class="field">
          <label>選択中のヒント文（生徒画面で4秒表示）</label>
          <textarea id="hintText" placeholder="例：ここは車が通るよ"></textarea>
          <div class="note">・作成：ボタンが緑の間は「範囲指定モード」です（ドラッグで範囲指定）。<br>
          ・編集：範囲をタップで選択 → ドラッグで移動、右下の白丸でサイズ変更。</div>
        </div>
      </div>
    </div>

  </div>
</div>

<script>
function updateRealVH(){
  try{
    const vv = window.visualViewport;
    const h = vv ? vv.height : window.innerHeight;
    document.documentElement.style.setProperty("--real-vh", h + "px");
  }catch(e){}
}
updateRealVH();
window.addEventListener("resize", updateRealVH, {passive:true});
if(window.visualViewport){
  window.visualViewport.addEventListener("resize", updateRealVH, {passive:true});
}


/* ===== 設定 ===== */
const ADMIN_PASSCODE = "1234";
const STORAGE_KEY = "hintQuiz.questions.v4";

/* ===== データ ===== */
const DEFAULT_QUESTIONS = [
  { enabled:true,  question:"この中で危ないところはどこ？", choices:["横断歩道","道路","歩道","公園"], correct:1, imageData:"", hints:[] },
  { enabled:true,  question:"信号の色はどれ？",             choices:["赤","青","黄色","白"],     correct:0, imageData:"", hints:[] },
  ...Array.from({length:8}, ()=>({ enabled:false, question:"", choices:["","","",""], correct:0, imageData:"", hints:[] }))
];
function cloneDefault(){ return JSON.parse(JSON.stringify(DEFAULT_QUESTIONS)); }
function loadQuestions(){
  try{
    const raw = localStorage.getItem(STORAGE_KEY);
    if(!raw) return cloneDefault();
    const parsed = JSON.parse(raw);
    const out = cloneDefault();
    for(let i=0;i<Math.min(10, parsed.length);i++){
      const q = parsed[i] || {};
      out[i].enabled = !!q.enabled;
      out[i].question = (q.question ?? "").toString();
      out[i].choices = Array.isArray(q.choices) ? q.choices.map(x=>(x??"").toString()).slice(0,4) : ["","","",""];
      while(out[i].choices.length<4) out[i].choices.push("");
      const c = Number(q.correct);
      out[i].correct = Number.isFinite(c) ? Math.min(3, Math.max(0, c)) : 0;
      out[i].imageData = (q.imageData ?? "").toString();
      out[i].hints = Array.isArray(q.hints) ? q.hints.map(h=>normalizeHint(h)).filter(Boolean) : [];
    }
    return out;
  }catch{
    return cloneDefault();
  }
}
function saveQuestions(){ localStorage.setItem(STORAGE_KEY, JSON.stringify(QUESTIONS)); }
let QUESTIONS = loadQuestions();

function normalizeHint(h){
  if(!h || !h.type) return null;
  if(h.type === "ellipse"){
    return {
      type:"ellipse",
      cx:Number(h.cx)||0, cy:Number(h.cy)||0,
      rx:Math.max(0, Math.abs(Number(h.rx)||0)),
      ry:Math.max(0, Math.abs(Number(h.ry)||0)),
      text:(h.text??"").toString()
    };
  }
  if(h.type === "rect"){

    const x = Number(h.x)||0, y = Number(h.y)||0;
    const w = Math.abs(Number(h.w)||0), hh = Math.abs(Number(h.h)||0);
    return { type:"rect", x, y, w, h:hh, text:(h.text??"").toString() };
  }

  if(h.type === "poly"){
    const pts = Array.isArray(h.points) ? h.points : [];
    const points = pts.map(p=>({x:Number(p.x)||0, y:Number(p.y)||0})).filter(p=>Number.isFinite(p.x)&&Number.isFinite(p.y));
    return { type:"poly", points, text:(h.text??"").toString() };
  }
  return null;
}


async function readAndCompressImage(file, maxLongSide=1600, jpegQuality=0.85){
  // FileReaderでDataURL化→Imageへ→長辺をmaxLongSideへ縮小→DataURLを返す
  const dataURL = await new Promise((resolve, reject)=>{
    const fr = new FileReader();
    fr.onerror = ()=>reject(new Error("FileReader error"));
    fr.onload = ()=>resolve(fr.result);
    fr.readAsDataURL(file);
  });

  const img = new Image();
  img.decoding = "async";
  img.src = dataURL;

  await new Promise((res, rej)=>{ img.onload=()=>res(); img.onerror=()=>rej(new Error("Image decode error")); });

  const w = img.naturalWidth || 1;
  const h = img.naturalHeight || 1;
  const longSide = Math.max(w,h);
  const scale = Math.min(1, maxLongSide / longSide);
  const tw = Math.max(1, Math.round(w * scale));
  const th = Math.max(1, Math.round(h * scale));

  const cvs = document.createElement("canvas");
  cvs.width = tw;
  cvs.height = th;
  const ctx = cvs.getContext("2d");
  ctx.drawImage(img, 0, 0, tw, th);

  // 容量節約のため基本JPEG（PNGは大きくなりやすい）
  // 透明をどうしても維持したい場合はここをPNGに変更できます
  const out = cvs.toDataURL("image/jpeg", jpegQuality);
  return out;
}

function activePack(){
  const active=[], map=[];
  for(let i=0;i<QUESTIONS.length;i++){
    if(QUESTIONS[i].enabled){ active.push(QUESTIONS[i]); map.push(i); }
  }
  if(active.length===0){ active.push(QUESTIONS[0]); map.push(0); }
  return {active, map};
}

/* ===== レイアウト補助 ===== */
function adjustHeaderHeightVar(){
  const h = document.querySelector("header").getBoundingClientRect().height;
  document.documentElement.style.setProperty("--headerH", Math.ceil(h) + "px");
}
window.addEventListener("resize", adjustHeaderHeightVar);
adjustHeaderHeightVar();

/* ============================================================
   生徒画面：表示・クイズ・ヒント
============================================================ */
const qText  = document.getElementById("qText");
const editBtn = document.getElementById("editBtn");
const knowBtn = document.getElementById("knowBtn");
const nextBtn = document.getElementById("nextBtn");
const restartBtn = document.getElementById("restartBtn");
const choices = document.getElementById("choices");
const overlay = document.getElementById("overlayMessage");
const toast = document.getElementById("toast");

const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
let dispImg = new Image();

let qi = 0;
let solved = false;
let foundHints = new Set(); // indices of found hints for current question
let toastTimer = null;

function clientToCanvas(cvs, clientX, clientY){
  const r = cvs.getBoundingClientRect();
  const sx = cvs.width / r.width;
  const sy = cvs.height / r.height;
  return { x:(clientX-r.left)*sx, y:(clientY-r.top)*sy };
}

function pointInPoly(p, pts){
  // ray casting
  let inside = false;
  for(let i=0, j=pts.length-1; i<pts.length; j=i++){
    const xi=pts[i].x, yi=pts[i].y;
    const xj=pts[j].x, yj=pts[j].y;
    const intersect = ((yi>p.y)!==(yj>p.y)) && (p.x < (xj-xi)*(p.y-yi)/(yj-yi+1e-12) + xi);
    if(intersect) inside = !inside;
  }
  return inside;
}






function fitCanvasDisplay(cvs, imgW, imgH, mode="view"){
  // 縦優先表示。横がはみ出す場合は自動ズームダウン。
  // 編集画面(mode="edit")は少し大きめにするが、コンテナからはみ出さないよう上限をかける。
  const wrap = cvs.parentElement;

  const maxH = wrap.clientHeight || imgH;
  const maxW = wrap.clientWidth  || imgW;

  // 基本は縦基準
  let scale = maxH / imgH;

  // 横がはみ出すなら横基準に縮小
  if(imgW * scale > maxW){
    scale = maxW / imgW;
  }

  // 編集画面は拡大ブースト（ただし上限あり）
  if(mode === "edit"){
    scale = Math.min(scale * 1.2, maxW / imgW, maxH / imgH);
  }

  const dispW = Math.round(imgW * scale);
  const dispH = Math.round(imgH * scale);

  cvs.style.width  = dispW + "px";
  cvs.style.height = dispH + "px";
  cvs.style.display = "block";
  cvs.style.marginLeft = "auto";
  cvs.style.marginRight = "auto";
}

function drawStudent(){
  const {active} = activePack();
  const q = active[qi];

  const w = dispImg.naturalWidth || 1200;
  const h = dispImg.naturalHeight || 800;
  canvas.width = w;
  canvas.height = h;
  fitCanvasDisplay(canvas, w, h, "view");

  ctx.clearRect(0,0,w,h);
  if(q.imageData){
    ctx.drawImage(dispImg,0,0);
  }else{
    ctx.fillStyle="#f1f5f9"; ctx.fillRect(0,0,w,h);
    ctx.fillStyle="#64748b"; ctx.font="32px sans-serif"; ctx.textAlign="center";
    ctx.fillText("編集で画像を設定してください", w/2, h/2);
  }

  // 発見済みヒント範囲を常時表示
  if(foundHints.size){
    ctx.save();
    ctx.strokeStyle = "rgba(37,99,235,0.92)";
    ctx.lineWidth = 5;
    ctx.setLineDash([]);
    foundHints.forEach(idx=>{
      const hnt = q.hints[idx];
      if(!hnt) return;
      if(hnt.type === "ellipse"){
        ctx.beginPath();
        ctx.ellipse(hnt.cx, hnt.cy, Math.max(1,hnt.rx), Math.max(1,hnt.ry), 0, 0, Math.PI*2);
        ctx.stroke();
      }else if(hnt.type === "rect"){
        ctx.strokeRect(hnt.x, hnt.y, Math.max(1,hnt.w), Math.max(1,hnt.h));
      }else if(hnt.type === "poly"){
        if(hnt.points && hnt.points.length>=2){
          ctx.beginPath();
          ctx.moveTo(hnt.points[0].x, hnt.points[0].y);
          for(let k=1;k<hnt.points.length;k++) ctx.lineTo(hnt.points[k].x, hnt.points[k].y);
          ctx.closePath();
          ctx.stroke();
        }
      }
    });
    ctx.restore();
  }
}

function showToast(text){
  toast.textContent = text || "";
  toast.style.display = "block";
  clearTimeout(toastTimer);
  toastTimer = setTimeout(()=>{
    toast.style.display = "none";
  }, 4000);
}

function showHintAt(index){
  // 発見済みとして記録（累積）
  foundHints.add(index);
  showToast(activePack().active[qi].hints[index].text || "");
  drawStudent();
}

function renderQuestion(){
  const {active} = activePack();
  const q = active[qi];

  qText.textContent = q.question || "（問題文を設定してください）";
  document.querySelectorAll(".choice").forEach((el,i)=> el.textContent = (q.choices[i] || "（未設定）"));

  nextBtn.style.display = "none";
  restartBtn.style.display = "none";
  overlay.style.display = "none";
  toast.style.display = "none";
  foundHints = new Set();

  solved = false;
  knowBtn.disabled = false;

  if(q.imageData){
    dispImg.onload = drawStudent;
    dispImg.src = q.imageData;
  }else{
    dispImg.onload = null;
    dispImg.src = "";
    drawStudent();
  }
}

knowBtn.onclick = ()=>{ if(!solved) choices.style.display = "flex"; };

choices.onclick = e=>{
  if(!e.target.classList.contains("choice")) return;
  const sel = Number(e.target.dataset.i);
  const {active} = activePack();
  const q = active[qi];
  choices.style.display = "none";

  if(sel === q.correct){
    solved = true;
    knowBtn.disabled = true;
    showOverlayTemp("正解！","ok", () => {
      const {active} = activePack();
      if(qi < active.length-1){
        nextBtn.style.display = "inline-block";
      }else{
        showOverlayPersist("終了","ok");
        restartBtn.style.display = "inline-block";
      }
    });
  }else{
    showOverlayTemp("もう一度考えよう","ng");
  }
};

nextBtn.onclick = ()=>{ qi++; renderQuestion(); };
restartBtn.onclick = ()=>{ qi = 0; renderQuestion(); };

function showOverlayTemp(text,cls,after){
  overlay.textContent = text;
  overlay.className = cls;
  overlay.style.display = "flex";
  setTimeout(()=>{
    overlay.style.display="none";
    if(after) after();
  },1200);
}
function showOverlayPersist(text,cls){
  overlay.textContent = text;
  overlay.className = cls;
  overlay.style.display = "flex";
}

// 生徒画面：ヒント範囲をタップ → ヒント表示＋範囲ハイライト（4秒）
canvas.addEventListener("pointerdown", (e)=>{
  const {active} = activePack();
  const q = active[qi];
  if(!q.hints || q.hints.length===0) return;

  const p = clientToCanvas(canvas, e.clientX, e.clientY);

  // 上にある（後から作った）ものを優先
  for(let i=q.hints.length-1; i>=0; i--){
    const h = q.hints[i];
    let hit=false;
    if(h.type === "ellipse"){
      if(h.rx<=0 || h.ry<=0) continue;
      const dx=(p.x-h.cx)/h.rx, dy=(p.y-h.cy)/h.ry;
      hit = (dx*dx + dy*dy) <= 1.0;
    }else if(h.type === "rect"){
      hit = (p.x>=h.x && p.x<=h.x+h.w && p.y>=h.y && p.y<=h.y+h.h);
    }else if(h.type === "poly"){
      hit = pointInPoly(p, h.points);
    }
    if(hit){
      showHintAt(i);
      break;
    }
  }
});

/* ============================================================
   編集モード：問題設定＋画像＋ヒント（楕円/四角）
============================================================ */
const editModal = document.getElementById("editModal");
const editIndexBadge = document.getElementById("editIndexBadge");
const editEnabled = document.getElementById("editEnabled");
const editQuestion = document.getElementById("editQuestion");
const editPrev = document.getElementById("editPrev");
const editNext = document.getElementById("editNext");
const editClose = document.getElementById("editClose");
const exportHtmlBtn = document.getElementById("exportHtml");

exportHtmlBtn.addEventListener("click", ()=>{
  try{
    const data = JSON.stringify(QUESTIONS);
    let out = "<!doctype html>\n" + document.documentElement.outerHTML;

    // 1) データを埋め込み（localStorage読み込みを上書き）
    out = out.replace(/let\s+QUESTIONS\s*=\s*loadQuestions\(\)\s*;?/,
                      "let QUESTIONS = " + data + ";\n// (embedded) localStorageは使いません");

    // 2) 編集機能を無効化（配布用）
    out = out.replace(/const\s+ADMIN_PASSCODE\s*=\s*\"[^\"]*\"\s*;?/,
                      'const ADMIN_PASSCODE = ""; // disabled in exported file');

    // 3) 編集ボタン・編集モーダルを隠す
    out = out.replace("</head>", "<style>#editBtn,#editModal{display:none !important;}</style>\n</head>");
    const blob = new Blob([out], {type:"text/html"});
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a");
    const stamp = new Date().toISOString().slice(0,10).replace(/-/g,"");
    a.href = url;
    a.download = "hint_app_student_" + stamp + ".html";
    document.body.appendChild(a);
    a.click();
    a.remove();
    setTimeout(()=>URL.revokeObjectURL(url), 2000);
    showToast("配布用HTMLを書き出しました");
  }catch(err){
    alert("書き出しに失敗しました: " + err);
  }
});


const editReset = document.getElementById("editReset");

const cInputs = [0,1,2,3].map(i=>document.getElementById("c"+i));
const rInputs = [0,1,2,3].map(i=>document.getElementById("r"+i));

// tabs
document.querySelectorAll(".tabBtn").forEach(btn=>{
  btn.addEventListener("click", ()=>{
    document.querySelectorAll(".tabBtn").forEach(b=>b.classList.remove("active"));
    document.querySelectorAll(".tabPanel").forEach(p=>p.classList.remove("active"));
    btn.classList.add("active");
    document.getElementById(btn.dataset.tab).classList.add("active");
    if(btn.dataset.tab === "tabH") drawEdit();
  });
});

let editIdx = 0;

// image + hint editor
const imgInput = document.getElementById("imgInput");
const imgStatus = document.getElementById("imgStatus");
const editCanvas = document.getElementById("editCanvas");
const ectx = editCanvas.getContext("2d");
let editImg = new Image();

const selBadge = document.getElementById("selBadge");
const btnNewEllipse = document.getElementById("btnNewEllipse");
const btnNewRect = document.getElementById("btnNewRect");
const btnNewPoly = document.getElementById("btnNewPoly");
const btnPolyDone = document.getElementById("btnPolyDone");
const btnPolyUndo = document.getElementById("btnPolyUndo");
const btnDelete = document.getElementById("btnDelete");
const btnClearHints = document.getElementById("btnClearHints");
const hintText = document.getElementById("hintText");

let selectedHint = -1;          // index in current question hints
let createMode = null;          // "ellipse" | "rect" | null
let dragMode = null;            // "move" | "resize" | "create"
let dragStart = null;           // {x,y, baseHint}
let creatingHintIndex = -1;
let polyDraft = []; // 多角形作成中の頂点配列

function setCreateMode(m){
  createMode = m;
  // ボタン色
  btnNewEllipse.classList.toggle("active", createMode==="ellipse");
  btnNewRect.classList.toggle("active", createMode==="rect");
  btnNewPoly.classList.toggle("active", createMode==="poly");
  const showPoly = (createMode==="poly");
  btnPolyDone.style.display = showPoly ? "inline-block" : "none";
  btnPolyUndo.style.display = showPoly ? "inline-block" : "none";
  if(!showPoly){ polyDraft = []; }
}

function openEdit(){
  const p = prompt("編集用パスコード");
  if(p !== ADMIN_PASSCODE) return;
  adjustHeaderHeightVar();
  editIdx = 0;
  loadEditFields();
  editModal.style.display = "flex";
}
function closeEdit(){
  commitEditFields();
  saveQuestions();
  editModal.style.display = "none";
  qi = 0;
  renderQuestion();
}

editBtn.addEventListener("click", openEdit);
editClose.addEventListener("click", closeEdit);

function loadEditFields(){
  const q = QUESTIONS[editIdx];
  // ファイル入力は問題ごとに残って見えるので毎回クリア
  try{ imgInput.value = ""; }catch{}
  imgStatus.textContent = q.imageData ? "（画像設定済み）" : "（未設定）";
  editIndexBadge.textContent = `問題 ${editIdx+1} / 10`;
  editEnabled.checked = !!q.enabled;
  editQuestion.value = q.question || "";
  for(let i=0;i<4;i++){
    cInputs[i].value = (q.choices[i] || "");
    rInputs[i].checked = (q.correct === i);
  }

  selectedHint = -1;
  hintText.value = "";
  updateSelUI();
  setCreateMode(null);

  // 画像
  if(q.imageData){
    editImg.onload = ()=>{ fitEditCanvasToImage(); drawEdit(); };
    editImg.src = q.imageData;
  }else{
    editImg.onload = null;
    editImg.src = "";
    editCanvas.width = 1200;
    editCanvas.height = 800;
    fitCanvasDisplay(editCanvas, 1200, 800, "edit");
    drawEdit();
  }
}

function commitEditFields(){
  const q = QUESTIONS[editIdx];
  q.enabled = !!editEnabled.checked;
  q.question = (editQuestion.value || "").toString();
  q.choices = cInputs.map(x=>(x.value||"").toString());
  const chosen = rInputs.findIndex(r=>r.checked);
  q.correct = (chosen >= 0) ? chosen : 0;
  if(selectedHint >= 0 && q.hints[selectedHint]){
    q.hints[selectedHint].text = (hintText.value || "").toString();
  }
  saveQuestions();
}

function goEdit(delta){
  commitEditFields();
  editIdx = Math.min(9, Math.max(0, editIdx + delta));
  loadEditFields();
}

editPrev.addEventListener("click", ()=>goEdit(-1));
editNext.addEventListener("click", ()=>goEdit(+1));

[editEnabled, editQuestion, ...cInputs, ...rInputs].forEach(el=>{
  el.addEventListener("input", commitEditFields);
  el.addEventListener("change", commitEditFields);
});

editReset.addEventListener("click", ()=>{
  if(!confirm("初期状態に戻します。よろしいですか？")) return;
  QUESTIONS = cloneDefault();
  saveQuestions();
  editIdx = 0;
  loadEditFields();
});

imgInput.addEventListener("change", async ()=>{
  const f = imgInput.files && imgInput.files[0];
  if(!f) return;

  try{
    if(imgStatus) imgStatus.textContent = `（読み込み中: ${f.name}）`;

    const dataURL = await readAndCompressImage(f, 1600, 0.85);

    // 先に反映（保存の成否に関わらず表示は更新）
    const q = QUESTIONS[editIdx];
    q.imageData = dataURL;

    // 編集画面に即反映
    editImg.onload = ()=>{ fitEditCanvasToImage(); drawEdit(); };
    editImg.src = q.imageData;
    setTimeout(()=>{ try{ fitEditCanvasToImage(); drawEdit(); }catch{} }, 0);

    // 通常画面側のプレビューにも反映（現在の問題なら）
    try{
      if(typeof currentIndex !== 'undefined' && typeof dispImg !== 'undefined' && typeof renderQuestion === 'function' && currentIndex === editIdx){
        dispImg.onload = ()=>{ renderQuestion(); };
        dispImg.src = q.imageData;
        setTimeout(()=>{ try{ renderQuestion(); }catch{} }, 0);
      }
    }catch{}

    if(imgStatus) imgStatus.textContent = `（設定済み: ${f.name}）`;

    // 保存（失敗しても表示は維持）
    const ok = saveQuestions();
    if(!ok){
      if(imgStatus) imgStatus.textContent = `（設定済み: ${f.name} / ※保存できていない可能性）`;
    }
  }catch(err){
    console.error(err);
    alert("画像の読み込みに失敗しました。\n\nよくある原因：\n・HEICなど未対応形式\n・画像が極端に大きい\n\n対策：JPEG/PNGで保存し直してから選んでください。");
    if(imgStatus) imgStatus.textContent = (QUESTIONS[editIdx].imageData ? "（画像設定済み）" : "（未設定）");
  }
});

function fitEditCanvasToImage(){
  const w = editImg.naturalWidth || 1200;
  const h = editImg.naturalHeight || 800;
  editCanvas.width = w;
  editCanvas.height = h;
  fitCanvasDisplay(editCanvas, w, h, "edit");
}

function drawEdit(){
  const q = QUESTIONS[editIdx];
  const w = editCanvas.width || 1200;
  const h = editCanvas.height || 800;

  ectx.clearRect(0,0,w,h);
  if(q.imageData){
    ectx.drawImage(editImg,0,0);
  }else{
    ectx.fillStyle="#f1f5f9"; ectx.fillRect(0,0,w,h);
    ectx.fillStyle="#64748b"; ectx.font="32px sans-serif"; ectx.textAlign="center";
    ectx.fillText("ここで画像を設定してください", w/2, h/2);
  }

  (q.hints||[]).forEach((hnt,i)=>{
    const isSel = (i===selectedHint);
    ectx.lineWidth = isSel ? 4 : 2.5;
    ectx.strokeStyle = isSel ? "rgba(37,99,235,0.98)" : "rgba(37,99,235,0.5)";
    ectx.setLineDash([]);

    if(hnt.type === "ellipse"){
      ectx.beginPath();
      ectx.ellipse(hnt.cx, hnt.cy, Math.max(1,hnt.rx), Math.max(1,hnt.ry), 0, 0, Math.PI*2);
      ectx.stroke();
      if(isSel){
        drawHandle(hnt.cx + hnt.rx, hnt.cy + hnt.ry);
      }
    }else if(hnt.type === "rect"){
      ectx.strokeRect(hnt.x, hnt.y, Math.max(1,hnt.w), Math.max(1,hnt.h));
      if(isSel){
        drawHandle(hnt.x + hnt.w, hnt.y + hnt.h);
      }
    }else if(hnt.type === "poly"){
      if(hnt.points && hnt.points.length>=2){
        ectx.beginPath();
        ectx.moveTo(hnt.points[0].x, hnt.points[0].y);
        for(let k=1;k<hnt.points.length;k++) ectx.lineTo(hnt.points[k].x, hnt.points[k].y);
        ectx.closePath();
        ectx.stroke();
      }
    }
  });

  // 多角形作成中のプレビュー
  if(createMode === "poly" && polyDraft.length>=1){
    ectx.lineWidth = 3;
    ectx.strokeStyle = "rgba(16,185,129,0.95)"; // green-ish
    ectx.setLineDash([8,6]);
    ectx.beginPath();
    ectx.moveTo(polyDraft[0].x, polyDraft[0].y);
    for(let k=1;k<polyDraft.length;k++) ectx.lineTo(polyDraft[k].x, polyDraft[k].y);
    ectx.stroke();
    ectx.setLineDash([]);
    // 点を表示
    ectx.fillStyle = "rgba(16,185,129,0.95)";
    polyDraft.forEach(pt=>{
      ectx.beginPath();
      ectx.arc(pt.x, pt.y, 5, 0, Math.PI*2);
      ectx.fill();
    });
  }

}

function drawHandle(x,y){
  ectx.fillStyle = "#ffffff";
  ectx.strokeStyle = "rgba(37,99,235,0.98)";
  ectx.lineWidth = 2;
  ectx.beginPath();
  ectx.arc(x, y, 10, 0, Math.PI*2);
  ectx.fill(); ectx.stroke();
}

function updateSelUI(){
  if(selectedHint < 0){
    selBadge.textContent = "未選択";
  }else{
    selBadge.textContent = `選択中 #${selectedHint+1}`;
  }
}

btnNewEllipse.addEventListener("click", ()=>{ setCreateMode(createMode==="ellipse" ? null : "ellipse"); });
btnNewRect.addEventListener("click", ()=>{ setCreateMode(createMode==="rect" ? null : "rect"); });
btnNewPoly.addEventListener("click", ()=>{
  setCreateMode(createMode==="poly" ? null : "poly");
  polyDraft = [];
  selectedHint = -1;
  updateSelUI();
  drawEdit();
});

btnPolyUndo.addEventListener("click", ()=>{
  if(createMode !== "poly") return;
  polyDraft.pop();
  drawEdit();
});

btnPolyDone.addEventListener("click", ()=>{
  if(createMode !== "poly") return;
  const q = QUESTIONS[editIdx];
  if(polyDraft.length < 3){
    alert("多角形は3点以上必要です");
    return;
  }
  q.hints.push({ type:"poly", points: polyDraft.map(p=>({x:p.x,y:p.y})), text:"" });
  selectedHint = q.hints.length - 1;
  hintText.value = "";
  updateSelUI();
  setCreateMode(null);
  polyDraft = [];
  drawEdit();
});


btnDelete.addEventListener("click", ()=>{
  const q = QUESTIONS[editIdx];
  if(selectedHint < 0) return;
  q.hints.splice(selectedHint, 1);
  selectedHint = -1;
  hintText.value = "";
  updateSelUI();
  saveQuestions();
  drawEdit();
});

btnClearHints.addEventListener("click", ()=>{
  const q = QUESTIONS[editIdx];
  if(!confirm("この問題のヒントを全消しします。よろしいですか？")) return;
  q.hints = [];
  selectedHint = -1;
  hintText.value = "";
  updateSelUI();
  saveQuestions();
  drawEdit();
});

hintText.addEventListener("input", ()=>{
  const q = QUESTIONS[editIdx];
  if(selectedHint >= 0 && q.hints[selectedHint]){
    q.hints[selectedHint].text = hintText.value;
    saveQuestions();
  }
});

function eClientToCanvas(clientX, clientY){
  const r = editCanvas.getBoundingClientRect();
  const sx = editCanvas.width / r.width;
  const sy = editCanvas.height / r.height;
  return { x:(clientX-r.left)*sx, y:(clientY-r.top)*sy };
}

function handlePos(hnt){
  if(hnt.type === "ellipse") return {x: hnt.cx + hnt.rx, y: hnt.cy + hnt.ry};
  return {x: hnt.x + hnt.w, y: hnt.y + hnt.h};
}
function hitHandle(hnt, p){
  const hp = handlePos(hnt);
  const dx = p.x - hp.x;
  const dy = p.y - hp.y;
  return (dx*dx + dy*dy) <= (14*14);
}
function hitShape(hnt, p){
  if(hnt.type === "ellipse"){
    if(hnt.rx<=0 || hnt.ry<=0) return false;
    const dx=(p.x-hnt.cx)/hnt.rx, dy=(p.y-hnt.cy)/hnt.ry;
    return (dx*dx+dy*dy)<=1.0;
  }else if(hnt.type === "rect"){
    return (p.x>=hnt.x && p.x<=hnt.x+hnt.w && p.y>=hnt.y && p.y<=hnt.y+hnt.h);
  }else if(hnt.type === "poly"){
    return pointInPoly(p, hnt.points || []);
  }
  return false;
}

editCanvas.addEventListener("pointerdown", (e)=>{
  const q = QUESTIONS[editIdx];
  const p = eClientToCanvas(e.clientX, e.clientY);

  dragMode = null;
  dragStart = null;
  creatingHintIndex = -1;

  // 1) 作成モード：ドラッグで範囲指定（新規）
  if(createMode){
    if(createMode === "poly"){
      polyDraft.push({x:p.x, y:p.y});
      drawEdit();
      return;
    }

    const minSize = 8;
    let newHint;
    if(createMode === "ellipse"){
      newHint = { type:"ellipse", cx:p.x, cy:p.y, rx:minSize, ry:minSize, text:"" };
    }else{
      newHint = { type:"rect", x:p.x, y:p.y, w:minSize, h:minSize, text:"" };
    }
    q.hints.push(newHint);
    creatingHintIndex = q.hints.length - 1;
    selectedHint = creatingHintIndex;
    hintText.value = (q.hints[selectedHint].text || "");
    updateSelUI();
    dragMode = "create";
    dragStart = {x:p.x, y:p.y, baseHint: JSON.parse(JSON.stringify(newHint))};
    drawEdit();
    return;
  }

  // 2) リサイズ：選択中のハンドル
  if(selectedHint >= 0 && q.hints[selectedHint] && hitHandle(q.hints[selectedHint], p)){
    dragMode = "resize";
    dragStart = { x:p.x, y:p.y, base: JSON.parse(JSON.stringify(q.hints[selectedHint])) };
    editCanvas.setPointerCapture(e.pointerId);
    return;
  }

  // 3) 選択＋移動：上にあるもの優先
  for(let i=q.hints.length-1; i>=0; i--){
    if(hitShape(q.hints[i], p)){
      selectedHint = i;
      hintText.value = q.hints[i].text || "";
      updateSelUI();
      if(q.hints[i].type === "poly"){
        dragMode = null; // 多角形は移動/リサイズは未対応（ヒント文編集は可）
      }else{
        dragMode = "move";
        dragStart = { x:p.x, y:p.y, base: JSON.parse(JSON.stringify(q.hints[i])) };
        editCanvas.setPointerCapture(e.pointerId);
      }
      drawEdit();
      return;
    }
  }

  // 4) 何も当たらない：選択解除
  selectedHint = -1;
  hintText.value = "";
  updateSelUI();
  drawEdit();
});

editCanvas.addEventListener("pointermove", (e)=>{
  const q = QUESTIONS[editIdx];
  if(!dragMode) return;
  const p = eClientToCanvas(e.clientX, e.clientY);

  if(dragMode === "create"){
    const hnt = q.hints[selectedHint];
    if(!hnt) return;
    const x0 = dragStart.x, y0 = dragStart.y;
    const x1 = p.x, y1 = p.y;
    const minSize = 8;

    if(hnt.type === "ellipse"){
      hnt.cx = (x0 + x1)/2;
      hnt.cy = (y0 + y1)/2;
      hnt.rx = Math.max(minSize, Math.abs(x1 - x0)/2);
      hnt.ry = Math.max(minSize, Math.abs(y1 - y0)/2);
    }else{
      hnt.x = Math.min(x0, x1);
      hnt.y = Math.min(y0, y1);
      hnt.w = Math.max(minSize, Math.abs(x1 - x0));
      hnt.h = Math.max(minSize, Math.abs(y1 - y0));
    }
    saveQuestions();
    drawEdit();
    return;
  }

  if(selectedHint < 0) return;
  const hnt = q.hints[selectedHint];
  if(!hnt) return;

  if(dragMode === "move"){
    const dx = p.x - dragStart.x;
    const dy = p.y - dragStart.y;
    if(hnt.type === "ellipse"){
      hnt.cx = dragStart.base.cx + dx;
      hnt.cy = dragStart.base.cy + dy;
    }else{
      hnt.x = dragStart.base.x + dx;
      hnt.y = dragStart.base.y + dy;
    }
  }else if(dragMode === "resize"){
    if(hnt.type === "ellipse"){
      hnt.rx = Math.max(8, Math.abs(p.x - hnt.cx));
      hnt.ry = Math.max(8, Math.abs(p.y - hnt.cy));
    }else{
      hnt.w = Math.max(8, p.x - hnt.x);
      hnt.h = Math.max(8, p.y - hnt.y);
    }
  }
  saveQuestions();
  drawEdit();
});

editCanvas.addEventListener("pointerup", ()=>{
  if(dragMode === "create"){
    // 1つ作成したら作成モードを解除
    setCreateMode(null);
  }
  dragMode = null;
  dragStart = null;
  creatingHintIndex = -1;
});

/* ===== 初期表示 ===== */
renderQuestion();
</script>

</body>
</html>

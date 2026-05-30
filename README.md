<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>ClassMap</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@400;500;600;700&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #0f1117; --surface: #1a1d27; --surface2: #22263a;
  --border: rgba(255,255,255,.09); --text: #eef0f8;
  --muted: rgba(238,240,248,.45); --accent: #6c63ff;
  --accent2: #ff6b6b; --go: #3ecf8e; --warn: #f5a623; --blue: #4dabf7;
  --shadow: 0 8px 32px rgba(0,0,0,.55);
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--text);min-height:100vh;overflow-x:hidden}
body::before{content:'';position:fixed;inset:0;z-index:0;background:radial-gradient(ellipse 80% 60% at 20% 10%,rgba(108,99,255,.12),transparent 60%),radial-gradient(ellipse 60% 50% at 80% 80%,rgba(62,207,142,.08),transparent 55%);pointer-events:none}
.hide{display:none!important}

/* TOPBAR */
.topbar{position:relative;z-index:10;display:flex;align-items:center;justify-content:space-between;padding:14px 24px;gap:12px;flex-wrap:wrap;border-bottom:1px solid var(--border);background:rgba(15,17,23,.85);backdrop-filter:blur(12px)}
.brand{display:flex;align-items:center;gap:10px}
.brand-icon{width:38px;height:38px;border-radius:10px;background:var(--accent);display:grid;place-items:center;font-family:'Bebas Neue';font-size:22px;color:#fff;box-shadow:0 4px 14px rgba(108,99,255,.5)}
.brand-name{font-family:'Bebas Neue';font-size:24px;letter-spacing:2px}
.brand-name em{color:var(--accent);font-style:normal}
.bar-right{display:flex;gap:8px;align-items:center}

/* BUTTONS */
.btn{font-family:'DM Sans';font-weight:600;border:none;cursor:pointer;border-radius:10px;padding:10px 18px;font-size:14px;transition:all .15s;display:inline-flex;align-items:center;gap:6px}
.btn-accent{background:var(--accent);color:#fff;box-shadow:0 4px 16px rgba(108,99,255,.35)}
.btn-accent:hover{background:#7c74ff;transform:translateY(-1px)}
.btn-go{background:var(--go);color:#0a2a1c;box-shadow:0 4px 16px rgba(62,207,142,.3)}
.btn-go:hover{background:#4de0a0}
.btn-danger{background:var(--accent2);color:#fff;box-shadow:0 4px 14px rgba(255,107,107,.3)}
.btn-ghost{background:var(--surface2);color:var(--text);border:1px solid var(--border)}
.btn-ghost:hover{background:#2c3150}
.btn-sm{padding:7px 13px;font-size:12px;border-radius:8px}
.btn:disabled{opacity:.4;cursor:not-allowed}
.btn:active{transform:scale(.97)}
.btn-card{background:rgba(77,171,247,.15);color:var(--blue);border:1px solid rgba(77,171,247,.25)}
.btn-card:hover{background:rgba(77,171,247,.25)}

/* LOGIN */
#view-login{position:relative;z-index:5;display:flex;align-items:flex-start;justify-content:center;min-height:calc(100vh - 67px);padding:60px 16px}
.login-card{background:var(--surface);border:1px solid var(--border);border-radius:24px;padding:40px 36px;width:100%;max-width:440px;box-shadow:var(--shadow)}
.login-card h1{font-family:'Bebas Neue';font-size:52px;letter-spacing:3px;line-height:1;margin-bottom:6px}
.login-card h1 span{color:var(--accent)}
.login-sub{color:var(--muted);font-size:14px;margin-bottom:28px}
.seg{display:flex;gap:4px;background:var(--surface2);padding:4px;border-radius:12px;margin-bottom:22px}
.seg button{flex:1;border:none;background:transparent;padding:10px;border-radius:9px;cursor:pointer;font-family:'DM Sans';font-weight:600;font-size:13px;color:var(--muted);transition:all .2s}
.seg button.on{background:var(--accent);color:#fff;box-shadow:0 3px 12px rgba(108,99,255,.4)}
.field{margin-bottom:14px}
.field label{display:block;font-size:12px;font-weight:600;color:var(--muted);margin-bottom:6px;letter-spacing:.5px}
.field input{width:100%;padding:14px 16px;background:var(--surface2);border:1.5px solid var(--border);border-radius:12px;color:var(--text);font-family:'DM Mono';font-size:15px;outline:none;transition:border-color .2s}
.field input:focus{border-color:var(--accent)}
.field input::placeholder{color:rgba(238,240,248,.25)}
.code-input{text-transform:uppercase;letter-spacing:3px;font-size:20px!important;text-align:center}
.login-err{color:var(--accent2);font-size:13px;margin-bottom:12px;font-weight:600;min-height:20px}
.code-display{background:rgba(108,99,255,.1);border:1px solid rgba(108,99,255,.3);border-radius:12px;padding:14px 16px;margin-bottom:18px}
.code-display .cd-label{font-size:11px;font-weight:600;color:var(--accent);letter-spacing:1px;margin-bottom:6px}
.code-display .cd-code{font-family:'DM Mono';font-size:30px;letter-spacing:6px;font-weight:500}
.code-display .cd-hint{font-size:12px;color:var(--muted);margin-top:4px}

/* MAP */
#view-map{position:relative;z-index:5}
.maphead{padding:18px 24px 12px;display:flex;justify-content:space-between;align-items:flex-end;flex-wrap:wrap;gap:10px}
.maphead h2{font-family:'Bebas Neue';font-size:34px;letter-spacing:2px}
.maphead .sub{color:var(--muted);font-size:13px;margin-top:2px}
.code-badge{font-family:'DM Mono';font-size:12px;font-weight:500;background:rgba(108,99,255,.15);border:1px solid rgba(108,99,255,.3);color:var(--accent);border-radius:8px;padding:5px 12px;letter-spacing:2px}

/* TEACHER PANEL */
.teacher-panel{margin:0 20px 16px;background:var(--surface);border:1px solid var(--border);border-radius:16px;padding:14px 18px;display:flex;gap:14px;flex-wrap:wrap;align-items:center}
.t-grp{display:flex;align-items:center;gap:8px}
.t-grp label{font-size:12px;color:var(--muted);font-weight:600}
.t-grp input[type=number]{width:58px;padding:7px 10px;background:var(--surface2);border:1px solid var(--border);border-radius:8px;color:var(--text);font-family:'DM Mono';font-size:14px;text-align:center;outline:none}
.t-grp input[type=number]:focus{border-color:var(--accent)}
.t-divider{width:1px;height:28px;background:var(--border)}
.theme-swatches{display:flex;gap:6px}
.swatch{width:26px;height:26px;border-radius:7px;cursor:pointer;border:2px solid transparent;transition:all .2s}
.swatch.on,.swatch:hover{border-color:#fff;transform:scale(1.15)}

/* BANNERS */
.banners{padding:0 20px;display:flex;flex-direction:column;gap:8px;margin-bottom:8px}
.banner{border-radius:12px;padding:11px 16px;font-weight:600;font-size:13px;display:flex;align-items:center;gap:10px}
.banner-help{background:rgba(255,107,107,.15);border:1px solid rgba(255,107,107,.3);color:#ff9a9a}
.banner-card{background:rgba(77,171,247,.1);border:1px solid rgba(77,171,247,.25);color:var(--blue)}
.banner-chat{background:rgba(62,207,142,.1);border:1px solid rgba(62,207,142,.25);color:var(--go)}
.banner-chat a{color:var(--go);font-weight:700;text-decoration:none}
.banner-chat a:hover{text-decoration:underline}

/* LEGEND */
.legend{display:flex;gap:16px;flex-wrap:wrap;padding:0 24px 14px;font-size:12px;color:var(--muted)}
.legend span{display:flex;align-items:center;gap:5px}
.dot{width:9px;height:9px;border-radius:50%;display:inline-block}
.dot-open{background:rgba(238,240,248,.25)}.dot-busy{background:var(--warn)}
.dot-done{background:var(--go)}.dot-help{background:var(--accent2)}.dot-card{background:var(--blue)}

/* FLOOR */
.floor{position:relative;margin:0 20px 24px;min-height:580px;border-radius:20px;border:1.5px dashed rgba(255,255,255,.1);background:rgba(255,255,255,.02);padding:12px;overflow:hidden}
body.docked .floor{padding-bottom:250px}
body.station-min .floor{padding-bottom:90px}

/* STATIONS */
.station{position:absolute;width:165px;background:var(--surface);border:1px solid var(--border);border-top:5px solid rgba(255,255,255,.15);border-radius:16px;padding:14px 14px 12px;box-shadow:0 6px 20px rgba(0,0,0,.4);cursor:pointer;transition:transform .15s,box-shadow .15s;user-select:none}
.station:hover{transform:translateY(-4px) scale(1.02);box-shadow:0 12px 32px rgba(0,0,0,.5)}
.station.has-help{border-top-color:var(--accent2)!important;box-shadow:0 0 0 2px rgba(255,107,107,.3),0 8px 24px rgba(0,0,0,.4);animation:pulseHelp 1.4s infinite}
.station.has-card{border-top-color:var(--blue)!important;box-shadow:0 0 0 2px rgba(77,171,247,.25),0 8px 24px rgba(0,0,0,.4)}
.station.is-final{border-top-color:var(--go)!important;background:linear-gradient(160deg,rgba(62,207,142,.07),var(--surface))}
@keyframes pulseHelp{0%,100%{box-shadow:0 0 0 2px rgba(255,107,107,.3),0 8px 24px rgba(0,0,0,.4)}50%{box-shadow:0 0 0 8px rgba(255,107,107,.08),0 8px 24px rgba(0,0,0,.4)}}
@keyframes chipFlash{50%{opacity:.4}}
.station-kicker{font-size:10px;font-weight:700;color:var(--muted);letter-spacing:1px;margin-bottom:3px}
.station-label{font-family:'DM Sans';font-weight:700;font-size:15px;line-height:1.2;margin-bottom:8px}
.station.is-final .station-label{color:var(--go)}
.station-occ{display:flex;flex-wrap:wrap;gap:4px;min-height:22px}
.station-cnt{position:absolute;top:-9px;right:-9px;background:var(--accent);color:#fff;font-size:10px;font-weight:700;border-radius:999px;padding:2px 7px;box-shadow:0 2px 8px rgba(108,99,255,.5)}

/* CHIPS */
.chip{font-size:10px;font-weight:700;padding:3px 7px;border-radius:999px;background:rgba(255,255,255,.08);white-space:nowrap}
.chip-busy{background:rgba(245,166,35,.18);color:var(--warn)}
.chip-done{background:rgba(62,207,142,.18);color:var(--go)}
.chip-help{background:rgba(255,107,107,.2);color:var(--accent2);animation:chipFlash 1s infinite}
.chip-card{background:rgba(77,171,247,.18);color:var(--blue)}
.chip-me{outline:2px solid var(--accent);outline-offset:1px}
.chip-clickable{cursor:pointer}
.chip-clickable:hover{outline:2px solid var(--accent)}

/* DOCK */
.dock{position:fixed;left:0;right:0;bottom:0;z-index:50;display:flex;justify-content:center;padding:10px 12px;pointer-events:none}
.dock-sheet{background:var(--surface);border:1px solid var(--border);border-top:4px solid var(--accent);border-radius:18px 18px 14px 14px;width:100%;max-width:640px;padding:16px 20px 18px;box-shadow:0 -8px 40px rgba(0,0,0,.6);pointer-events:auto;backdrop-filter:blur(10px)}
.dock-head{display:flex;align-items:flex-start;gap:14px;margin-bottom:12px}
.dock-num{font-family:'Bebas Neue';font-size:48px;line-height:1;color:var(--accent)}
.dock-info{flex:1}
.dock-info h3{font-family:'DM Sans';font-weight:700;font-size:20px}
.dock-who{font-size:12px;color:var(--muted);font-weight:600;margin-top:2px}
.dock-banner{margin-top:7px;padding:8px 12px;border-radius:9px;font-size:12px;font-weight:600}
.dock-banner.busy{background:rgba(245,166,35,.12);color:var(--warn)}
.dock-banner.help{background:rgba(255,107,107,.12);color:var(--accent2)}
.dock-banner.done{background:rgba(62,207,142,.12);color:var(--go)}
.dock-banner.card{background:rgba(77,171,247,.1);color:var(--blue)}
.dock-body{display:grid;grid-template-columns:1fr 1fr;gap:14px}
@media(max-width:540px){.dock-body{grid-template-columns:1fr}}
.actions{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.actions .btn{padding:10px 12px;font-size:12px;justify-content:center}
.full{grid-column:1/-1}
body.station-min .dock-body{display:none}
body.station-min .dock-banner{display:none}

/* CHAT */
.chatbox{display:flex;flex-direction:column;border:1px solid var(--border);border-radius:12px;overflow:hidden;background:rgba(255,255,255,.03)}
.chat-title{padding:9px 12px;font-size:11px;font-weight:700;color:var(--muted);border-bottom:1px solid var(--border);background:rgba(255,255,255,.03)}
.chat-log{flex:1;min-height:110px;max-height:190px;overflow-y:auto;padding:10px;display:flex;flex-direction:column;gap:6px}
.chat-log::-webkit-scrollbar{width:4px}
.chat-log::-webkit-scrollbar-thumb{background:rgba(255,255,255,.1);border-radius:4px}
.msg{max-width:85%;padding:7px 11px;border-radius:12px;font-size:12px;line-height:1.4;word-break:break-word}
.msg .mfrom{font-size:10px;font-weight:700;opacity:.6;display:block;margin-bottom:2px}
.msg.them{align-self:flex-start;background:var(--surface2)}
.msg.me{align-self:flex-end;background:var(--accent);color:#fff}
.chat-empty{opacity:.35;font-size:12px;text-align:center;padding:20px 0;align-self:center}
.chat-input{display:flex;gap:6px;padding:8px;border-top:1px solid var(--border)}
.chat-input input{flex:1;padding:8px 12px;border-radius:9px;border:1px solid var(--border);background:var(--surface2);color:var(--text);font-family:'DM Sans';font-size:13px;outline:none}
.chat-input input:focus{border-color:var(--accent)}

/* TEACHER CHAT */
.tchat{position:fixed;right:16px;bottom:16px;width:310px;z-index:60;background:var(--surface);border:1px solid var(--border);border-top:4px solid var(--accent);border-radius:16px;box-shadow:var(--shadow);display:flex;flex-direction:column;overflow:hidden}
.tchat-head{display:flex;justify-content:space-between;align-items:center;padding:10px 14px;border-bottom:1px solid var(--border);background:rgba(255,255,255,.04);font-size:14px;font-weight:600}
.tchat .chat-log{min-height:150px;max-height:240px}

/* THEMES */
body.theme-cork{--bg:#8b5e2e;--surface:rgba(255,248,235,.95);--surface2:rgba(240,224,195,.8);--text:#2c1a08;--border:rgba(100,60,20,.2);--muted:rgba(44,26,8,.5);background:#a06830}
body.theme-cork::before{display:none}
body.theme-whiteboard{--bg:#f5f7fa;--surface:#fff;--surface2:#f0f2f7;--text:#1a1d2e;--border:rgba(0,0,0,.1);--muted:rgba(26,29,46,.5);background:#eef0f6}
body.theme-whiteboard::before{display:none}
body.theme-paper{--bg:#f2e8d0;--surface:rgba(255,252,244,.98);--surface2:rgba(236,222,190,.7);--text:#2a2118;--border:rgba(80,50,20,.15);--muted:rgba(42,33,24,.5);background:#f2e8d0;background-image:repeating-linear-gradient(0deg,transparent,transparent 26px,rgba(0,0,0,.04) 26px,rgba(0,0,0,.04) 27px)}
body.theme-paper::before{display:none}
/* light theme text fixes */
body.theme-cork .chip,body.theme-whiteboard .chip,body.theme-paper .chip{background:rgba(0,0,0,.07);color:var(--text)}
body.theme-cork .chip-busy,body.theme-whiteboard .chip-busy,body.theme-paper .chip-busy{background:rgba(180,110,0,.12);color:#a06000}
body.theme-cork .chip-done,body.theme-whiteboard .chip-done,body.theme-paper .chip-done{background:rgba(0,140,70,.12);color:#007040}
body.theme-cork .chip-help,body.theme-whiteboard .chip-help,body.theme-paper .chip-help{background:rgba(200,40,40,.12);color:#b02020}
body.theme-cork .chip-card,body.theme-whiteboard .chip-card,body.theme-paper .chip-card{background:rgba(40,100,220,.12);color:#1a60cc}
body.theme-cork .station,body.theme-whiteboard .station,body.theme-paper .station{box-shadow:0 4px 16px rgba(0,0,0,.18)}
body.theme-cork .floor,body.theme-whiteboard .floor,body.theme-paper .floor{border-color:rgba(0,0,0,.12);background:rgba(0,0,0,.02)}
body.theme-cork .topbar,body.theme-whiteboard .topbar,body.theme-paper .topbar{background:rgba(255,255,255,.85)}
body.theme-cork .brand-name,body.theme-whiteboard .brand-name,body.theme-paper .brand-name{color:var(--text)}
body.theme-cork .code-badge,body.theme-whiteboard .code-badge,body.theme-paper .code-badge{background:rgba(108,99,255,.1);color:#5b52e0}

/* STATION TASK CARD */
.station-taskcard{margin-top:8px;padding:7px 9px;background:rgba(77,171,247,.08);border:1px solid rgba(77,171,247,.2);border-radius:8px;font-size:10px;line-height:1.45;color:var(--blue);word-break:break-word}
body.theme-cork .station-taskcard,body.theme-whiteboard .station-taskcard,body.theme-paper .station-taskcard{color:#1a60cc;background:rgba(40,100,220,.07)}

/* ADD STATION MODAL textarea focus */
#newStationTask:focus{border-color:var(--accent);outline:none}
</style>
</head>
<body>

<!-- TOPBAR -->
<div class="topbar">
  <div class="brand">
    <div class="brand-icon">CM</div>
    <div class="brand-name">Class<em>Map</em></div>
  </div>
  <div class="bar-right" id="barRight"></div>
</div>

<!-- LOGIN -->
<section id="view-login">
  <div class="login-card">
    <h1>Class<span>Map</span></h1>
    <p class="login-sub">Live classroom station tracking — everyone on the same map.</p>
    <div class="seg">
      <button id="segStudent" class="on">🎒 I'm a student</button>
      <button id="segTeacher">📋 I'm the teacher</button>
    </div>

    <!-- Student fields -->
    <div id="studentFields">
      <div class="field">
        <label>CLASS CODE</label>
        <input id="codeInput" class="code-input" maxlength="80" placeholder="ABC123-xxxxxx" autocomplete="off" spellcheck="false" style="font-size:14px!important;letter-spacing:1px">
      </div>
      <div class="field">
        <label>YOUR NAME</label>
        <input id="nameInput" placeholder="e.g. Alex" autocomplete="off">
      </div>
    </div>

    <!-- Teacher fields -->
    <div id="teacherFields" class="hide">
      <div class="field">
        <label>YOUR NAME</label>
        <input id="teacherNameInput" placeholder="e.g. Ms Johnson" autocomplete="off">
      </div>
      <div class="field">
        <label>CLASS CODE — share this with students</label>
        <input id="classCodeInput" class="code-input" maxlength="6" placeholder="ABC123" autocomplete="off" spellcheck="false">
      </div>
    </div>

    <div class="login-err" id="loginErr"></div>
    <button class="btn btn-accent" style="width:100%;justify-content:center;font-size:15px;padding:14px" id="loginBtn">Enter Classroom →</button>
  </div>
</section>

<!-- MAP -->
<section id="view-map" class="hide">
  <div class="maphead">
    <div>
      <h2 id="mapTitle">The Classroom</h2>
      <div class="sub" id="mapSub">Tap your station to begin</div>
    </div>
    <span class="code-badge" id="mapCodeBadge">CODE: —</span>
  </div>

  <div id="teacherPanel" class="teacher-panel hide">
    <div class="t-grp"><label>THEME</label><div class="theme-swatches" id="themeSwatches"></div></div>
    <div class="t-divider"></div>
    <div class="t-grp" id="stationsSetupGrp">
      <label>STATIONS</label>
      <input type="number" id="numStations" min="2" max="12" value="6">
      <button class="btn btn-accent btn-sm" id="applyNum">Apply</button>
    </div>
    <div class="t-grp hide" id="stationsLockedGrp" title="Station count is locked once class is open">
      <label>STATIONS</label>
      <span id="stationsLockedCount" style="font-family:'DM Mono';font-size:14px;font-weight:700;opacity:.7;padding:0 4px">6</span>
      <span style="font-size:11px;color:var(--warn);font-weight:600">🔒 Locked</span>
    </div>
    <div class="t-divider"></div>
    <div class="t-grp">
      <button class="btn btn-accent btn-sm" id="addStationBtn">＋ Add Station</button>
      <button class="btn btn-ghost btn-sm" id="editTitleBtn">✏️ Rename</button>
      <button class="btn btn-ghost btn-sm" id="clearHelp">Clear help</button>
      <button class="btn btn-ghost btn-sm" id="clearCards">Clear cards</button>
      <button class="btn btn-ghost btn-sm" id="resetAll" style="color:var(--accent2)">🗑 Reset class</button>
    </div>
  </div>

  <!-- ADD STATION MODAL -->
  <div id="addStationModal" style="display:none;position:fixed;inset:0;z-index:100;background:rgba(0,0,0,.7);backdrop-filter:blur(6px);align-items:center;justify-content:center">
    <div style="background:var(--surface);border:1px solid var(--border);border-top:4px solid var(--accent);border-radius:20px;padding:28px 28px 24px;width:100%;max-width:480px;box-shadow:var(--shadow);margin:16px">
      <h3 style="font-family:'Bebas Neue';font-size:28px;letter-spacing:2px;margin-bottom:4px">Add New Station</h3>
      <p style="font-size:13px;color:var(--muted);margin-bottom:20px">Students will be automatically invited to this station.</p>
      <div class="field">
        <label>STATION NAME (optional)</label>
        <input id="newStationName" placeholder="e.g. Extension Challenge" autocomplete="off">
      </div>
      <div class="field">
        <label>TASK CARD</label>
        <textarea id="newStationTask" rows="5" placeholder="Describe the task for this station…" style="width:100%;padding:12px 14px;background:var(--surface2);border:1.5px solid var(--border);border-radius:12px;color:var(--text);font-family:'DM Sans';font-size:14px;line-height:1.5;outline:none;resize:vertical;transition:border-color .2s"></textarea>
      </div>
      <div style="display:flex;gap:10px;justify-content:flex-end;margin-top:4px">
        <button class="btn btn-ghost" id="addStationCancel">Cancel</button>
        <button class="btn btn-accent" id="addStationConfirm">＋ Add Station</button>
      </div>
    </div>
  </div>

  <div class="banners">
    <div id="helpBanner" class="banner banner-help hide"></div>
    <div id="cardBanner" class="banner banner-card hide"></div>
    <div id="chatBanner" class="banner banner-chat hide"></div>
  </div>

  <div class="legend">
    <span><i class="dot dot-open"></i> Open</span>
    <span><i class="dot dot-busy"></i> Working</span>
    <span><i class="dot dot-done"></i> Finished</span>
    <span id="legendHelp" class="hide"><i class="dot dot-help"></i> Clarification required</span>
    <span><i class="dot dot-card"></i> Card requested</span>
  </div>

  <div class="floor" id="floor"></div>
</section>

<!-- STUDENT DOCK -->
<div id="taskDock" class="dock hide">
  <div class="dock-sheet">
    <div class="dock-head">
      <div class="dock-num" id="dNum">1</div>
      <div class="dock-info">
        <h3 id="dName">Station One</h3>
        <div class="dock-who" id="dWho">You</div>
        <div id="dBanner" class="dock-banner busy"></div>
      </div>
      <button class="btn btn-ghost btn-sm" id="minBtn">— Minimise</button>
    </div>
    <div class="dock-body">
      <div class="actions">
        <button class="btn btn-accent full" id="aWork">📍 I'm working here</button>
        <button class="btn btn-danger full" id="aHelp">🙋 Clarification required</button>
        <button class="btn btn-card" id="aCardMe">🃏 I need a card</button>
        <button class="btn btn-card" id="aCardGroup">🃏 We need a card</button>
        <button class="btn btn-go full" id="aDone">✅ Finished!</button>
        <button class="btn btn-ghost" id="aNext">➡ Next task</button>
        <button class="btn btn-ghost" id="aLeave">← Leave</button>
      </div>
      <div class="chatbox">
        <div class="chat-title">💬 Chat with teacher</div>
        <div class="chat-log" id="chatLog"></div>
        <div class="chat-input">
          <input id="chatText" placeholder="Message your teacher…" maxlength="300">
          <button class="btn btn-accent btn-sm" id="chatSend">Send</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- TEACHER CHAT PANEL -->
<div id="teacherChat" class="tchat hide">
  <div class="tchat-head">
    <span>💬 <b id="tChatName">Student</b></span>
    <button class="btn btn-ghost btn-sm" id="tChatClose">✕</button>
  </div>
  <div class="chat-log" id="tChatLog"></div>
  <div class="chat-input">
    <input id="tChatText" placeholder="Reply…" maxlength="300">
    <button class="btn btn-accent btn-sm" id="tChatSend">Send</button>
  </div>
</div>

<script>
/* ─── JSONBIN STORAGE ───────────────────────────────────────────────────────
   All classroom data lives in a single JSONBin "bin" (a JSON document).
   Structure:  { "key1": <value>, "key2": <value>, ... }
   One bin per teacher session — the bin ID is stored in localStorage so the
   teacher gets the same bin back on reload, and students find it via the
   class-code lookup bin.

   Setup (free, 2 minutes):
   1. Go to https://jsonbin.io and click "Sign Up" (free)
   2. Go to API Keys → Create Access Key  →  copy it
   3. Paste it below as JSONBIN_API_KEY
   ────────────────────────────────────────────────────────────────────────── */

const JSONBIN_API_KEY = '$2a$10$68ya4dwsRM5Rjh42tBczv.GTinhuzJQ/sILY8Zcuj7SCI107WZz7C';
// ↑ Replace this with your key from https://jsonbin.io → API Keys

const JSONBIN_BASE = 'https://api.jsonbin.io/v3';

/* ── in-memory cache so we don't hammer the API on every read ── */
const _cache = {};          // key → parsed value
let   _binId  = null;       // the active bin ID for this session
let   _binDoc = null;       // the full bin document (object)
let   _dirty  = false;      // true if _binDoc has unsaved writes
let   _saving = false;      // write lock
let   _saveTimer = null;

/* ── helpers ── */
async function _ensureBin() {
  if (_binId) return;
  // Teacher creates a new bin; student looks up the bin via class code
  // We use a single "index" bin stored in localStorage to map code→binId
  const stored = localStorage.getItem('cm_binId');
  if (stored) { _binId = stored; await _loadBin(); return; }
  // Create a fresh bin
  const res = await fetch(JSONBIN_BASE + '/b', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'X-Master-Key': JSONBIN_API_KEY,
      'X-Bin-Private': 'false',
      'X-Bin-Name': 'ClassMap-' + Date.now()
    },
    body: JSON.stringify({})
  });
  if (!res.ok) throw new Error('JSONBin create failed: ' + res.status);
  const j = await res.json();
  _binId = j.metadata.id;
  _binDoc = {};
  localStorage.setItem('cm_binId', _binId);
}

async function _loadBin() {
  if (!_binId) return;
  try {
    const res = await fetch(JSONBIN_BASE + '/b/' + _binId + '/latest', {
      headers: { 'X-Master-Key': JSONBIN_API_KEY }
    });
    if (!res.ok) return;
    const j = await res.json();
    _binDoc = j.record || {};
    // Sync cache
    for (const k in _binDoc) _cache[k] = _binDoc[k];
  } catch(e) {}
}

async function _flush() {
  if (!_binId || !_dirty || _saving) return;
  _saving = true;
  try {
    await fetch(JSONBIN_BASE + '/b/' + _binId, {
      method: 'PUT',
      headers: {
        'Content-Type': 'application/json',
        'X-Master-Key': JSONBIN_API_KEY
      },
      body: JSON.stringify(_binDoc || {})
    });
    _dirty = false;
  } catch(e) {}
  _saving = false;
}

function _scheduleSave() {
  if (_saveTimer) clearTimeout(_saveTimer);
  _saveTimer = setTimeout(_flush, 300); // debounce writes by 300 ms
}

/* ── If student, look up the bin ID from a known public "registry" bin ──
   We store { classCode: binId } in a second fixed bin whose ID lives in
   the teacher's localStorage AND is embedded in the class config so students
   can find it.  For simplicity we piggyback it in the same bin under key
   "code:<classCode>" — students first load the bin ID from a shared
   "registry" stored in localStorage under cm_registry, or receive it from
   the teacher's config record which is stored in the same bin.           */

/* Public registry bin — one tiny bin that maps class codes → bin IDs.
   The teacher writes to it; students read from it.
   We create this once and store its ID in localStorage under cm_reg.     */
let _regBinId = null;

async function _ensureRegistry() {
  if (_regBinId) return;
  const stored = localStorage.getItem('cm_reg');
  if (stored) { _regBinId = stored; return; }
  // Create registry bin
  const res = await fetch(JSONBIN_BASE + '/b', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'X-Master-Key': JSONBIN_API_KEY,
      'X-Bin-Private': 'false',
      'X-Bin-Name': 'ClassMap-Registry'
    },
    body: JSON.stringify({})
  });
  if (!res.ok) throw new Error('Registry bin create failed');
  const j = await res.json();
  _regBinId = j.metadata.id;
  localStorage.setItem('cm_reg', _regBinId);
}

async function _regGet(code) {
  // Students need to know the registry bin ID — we embed it in the class code
  // via a special encoding: classCode = CODE + '.' + regBinId (first 8 chars)
  // But that changes UX. Simpler: use a single well-known public bin approach.
  // ── SIMPLEST APPROACH: embed the bin ID directly in the class code shared
  //    by teacher. Teacher's code badge shows "CODE:XXXXXX|BINID".
  //    We handle this transparently below.
  return null; // handled via embedded bin ID in class code
}

/* ── Re-design: encode binId into the shared class code ──────────────────
   classCode (internal) = "XXXXXX"  (6 chars, teacher-chosen)
   The teacher shares a "join string" = classCode + '-' + binId  (e.g. ABC123-64f3...)
   Students paste the full join string. We split on '-' to get both.
   The 6-char code is still shown on the map badge; the binId travels with it.
   ─────────────────────────────────────────────────────────────────────── */

/* ── Public API ── */
async function sGet(key) {
  if (!_binId) {
    // During login, bin may not be set yet; fall back to cache
    return _cache[key] !== undefined ? _cache[key] : null;
  }
  // Always read from in-memory doc (kept fresh by polling)
  if (_binDoc && key in _binDoc) return _binDoc[key];
  return null;
}

async function sSet(key, val) {
  if (!_binDoc) _binDoc = {};
  _binDoc[key] = val;
  _cache[key] = val;
  _dirty = true;
  _scheduleSave();
}

async function sDel(key) {
  if (_binDoc) delete _binDoc[key];
  delete _cache[key];
  _dirty = true;
  _scheduleSave();
}

async function sList(prefix) {
  if (!_binDoc) return [];
  return Object.keys(_binDoc).filter(k => k.startsWith(prefix));
}

/* ── Poll: refresh _binDoc from server every 2.5 s ── */
async function _pollBin() {
  if (!_binId || _dirty) return; // don't overwrite unsaved local changes
  await _loadBin();
}

/* ── Teacher: initialise a new bin for this session ── */
async function initTeacherBin() {
  await _ensureBin();
}

/* ── Student: connect to the teacher's bin via join code ── */
async function connectStudentBin(joinCode) {
  // joinCode format: "XXXXXX-<binId>"  or legacy "XXXXXX"
  const parts = joinCode.split('-');
  if (parts.length >= 2) {
    const code = parts[0];
    const bid  = parts.slice(1).join('-');
    _binId  = bid;
    _binDoc = {};
    localStorage.setItem('cm_binId', _binId);
    await _loadBin();
    return code; // return the plain 6-char class code
  }
  // Legacy / same-browser: try localStorage
  const stored = localStorage.getItem('cm_binId');
  if (stored) { _binId = stored; await _loadBin(); }
  return joinCode;
}

/* ── Expose join code for teacher to share ── */
function getJoinCode(classCode) {
  return _binId ? classCode + '-' + _binId : classCode;
}

/* ─── UTILS ─── */
const $ = s => document.querySelector(s);
const show = id => ['view-login','view-map'].forEach(v => $('#'+v).classList.toggle('hide', v !== id));
const esc = t => (t||'').replace(/[&<>"]/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c]));

/* ─── KEYS ─── */
let classCode = '';
const K_CFG    = () => 'cfg:' + classCode;
const kStu     = n  => 'stu:' + classCode + ':' + n;
const kChat    = n  => 'chat:' + classCode + ':' + n;
const kCode    = c  => 'code:' + c;  // records that a teacher created this code

/* ─── STATE ─── */
let me = { name: null, isTeacher: false };
let cfg = { numStations: 6, theme: 'dark', title: 'The Classroom', stationNames: {}, taskCards: {}, classOpen: false };
let current = { idx: null };
let poll = null, chatTarget = null, lastChatSig = '';

/* ─── LABELS ─── */
const WORDS = ['One','Two','Three','Four','Five','Six','Seven','Eight','Nine','Ten','Eleven','Twelve'];
function stationLabel(idx, total) {
  if (cfg.stationNames && cfg.stationNames[idx]) return cfg.stationNames[idx];
  return idx === total ? 'You DO 🎯' : 'Station ' + (WORDS[idx-1] || idx);
}
function stationKicker(idx, total) { return idx === total ? 'FINAL · ACHIEVE' : 'STATION ' + idx; }

/* ─── THEMES ─── */
const THEMES = [
  { id:'dark',       name:'Dark',        sw:'#1a1d27' },
  { id:'cork',       name:'Cork',        sw:'#a06830' },
  { id:'whiteboard', name:'Whiteboard',  sw:'#f5f7fa' },
  { id:'paper',      name:'Paper',       sw:'#f2e8d0' },
];
function applyTheme(t) {
  const b = document.body;
  THEMES.forEach(th => b.classList.remove('theme-' + th.id));
  if (t && t !== 'dark') b.classList.add('theme-' + t);
  cfg.theme = t || 'dark';
}

/* ─── CODE GENERATOR ─── */
function genCode() {
  return Array.from({length:6}, () => 'ABCDEFGHJKLMNPQRSTUVWXYZ23456789'[Math.floor(Math.random()*32)]).join('');
}

/* ─── SEGMENT ─── */
$('#segStudent').addEventListener('click', () => {
  me.isTeacher = false;
  $('#segStudent').classList.add('on'); $('#segTeacher').classList.remove('on');
  $('#studentFields').classList.remove('hide'); $('#teacherFields').classList.add('hide');
});
$('#segTeacher').addEventListener('click', () => {
  me.isTeacher = true;
  $('#segTeacher').classList.add('on'); $('#segStudent').classList.remove('on');
  $('#studentFields').classList.add('hide'); $('#teacherFields').classList.remove('hide');
  if (!$('#classCodeInput').value) $('#classCodeInput').value = genCode();
});

/* auto-uppercase */
['codeInput','classCodeInput'].forEach(id => {
  const el = $('#'+id);
  if (!el) return;
  el.addEventListener('input', function(){
    // classCodeInput: only uppercase alphanum; codeInput: allow hyphen for join codes
    if (id === 'codeInput') {
      this.value = this.value.toUpperCase().replace(/[^A-Z0-9\-]/g,'');
    } else {
      this.value = this.value.toUpperCase().replace(/[^A-Z0-9]/g,'');
    }
  });
});

/* ─── LOGIN ─── */
$('#loginBtn').addEventListener('click', doLogin);
['nameInput','codeInput','teacherNameInput','classCodeInput'].forEach(id => {
  const el = $('#'+id);
  if (el) el.addEventListener('keydown', e => { if (e.key === 'Enter') doLogin(); });
});

async function doLogin() {
  const err = $('#loginErr');
  const btn = $('#loginBtn');
  err.textContent = '';

  if (me.isTeacher) {
    const tName = $('#teacherNameInput').value.trim();
    if (!tName) { err.textContent = 'Please enter your name.'; return; }
    const code = $('#classCodeInput').value.trim().toUpperCase();
    if (code.length < 4) { err.textContent = 'Class code must be at least 4 characters.'; return; }

    btn.disabled = true; btn.textContent = 'Connecting…';
    try {
      await initTeacherBin();
    } catch(e) {
      err.textContent = '❌ Could not connect to JSONBin. Check your API key.';
      btn.disabled = false; btn.textContent = 'Enter Classroom →'; return;
    }
    classCode = code;
    me.name = tName;
    me.isTeacher = true;
    await sSet(kCode(code), { teacher: tName, ts: Date.now() });
    const stored = await sGet(K_CFG());
    if (stored) cfg = Object.assign(cfg, stored);
    else await sSet(K_CFG(), cfg);
    applyTheme(cfg.theme);
    btn.disabled = false; btn.textContent = 'Enter Classroom →';
    enterMap();

  } else {
    const rawCode = $('#codeInput').value.trim().toUpperCase();
    const name = $('#nameInput').value.trim();
    if (rawCode.length < 4) { err.textContent = 'Enter your class code.'; return; }
    if (!name) { err.textContent = 'Enter your name.'; return; }

    btn.disabled = true; btn.textContent = 'Joining…';
    try {
      classCode = await connectStudentBin(rawCode);
    } catch(e) {
      err.textContent = '❌ Could not connect. Check your code and try again.';
      btn.disabled = false; btn.textContent = 'Enter Classroom →'; return;
    }
    // Verify code exists in the shared bin
    const codeRec = await sGet(kCode(classCode));
    if (!codeRec) {
      err.textContent = '❌ Code not found. Check with your teacher.';
      btn.disabled = false; btn.textContent = 'Enter Classroom →'; return;
    }
    me.name = name;
    me.isTeacher = false;
    const stored = await sGet(K_CFG());
    if (stored) cfg = Object.assign(cfg, stored);
    applyTheme(cfg.theme);
    const existing = await sGet(kStu(name));
    if (!existing) await sSet(kStu(name), { name, station:null, status:'idle', card:'none', ts:Date.now() });
    if (!cfg.classOpen) { cfg.classOpen = true; await sSet(K_CFG(), cfg); }
    btn.disabled = false; btn.textContent = 'Enter Classroom →';
    enterMap();
  }
}

/* ─── TOPBAR ─── */
function renderBar() {
  const right = $('#barRight');
  right.innerHTML = me.name
    ? `<span style="font-size:12px;font-weight:600;color:var(--muted)">${me.isTeacher?'📋 Teacher':'🎒 '+esc(me.name)}</span>
       <button class="btn btn-ghost btn-sm" id="logoutBtn">Log out</button>`
    : '';
  const lo = $('#logoutBtn');
  if (!lo) return;
  lo.onclick = () => {
    stopPoll();
    // Reset bin state
    _binId = null; _binDoc = null; _dirty = false;
    me = { name:null, isTeacher:false };
    classCode = '';
    const b = document.body;
    b.classList.remove('docked','station-min');
    THEMES.forEach(t => b.classList.remove('theme-'+t.id));
    $('#taskDock').classList.add('hide');
    $('#teacherChat').classList.add('hide');
    chatTarget = null;
    show('view-login');
    $('#nameInput').value = '';
    $('#codeInput').value = '';
    $('#teacherNameInput').value = '';
    $('#classCodeInput').value = '';
    $('#loginErr').textContent = '';
    me.isTeacher = false;
    $('#segStudent').classList.add('on'); $('#segTeacher').classList.remove('on');
    $('#studentFields').classList.remove('hide'); $('#teacherFields').classList.add('hide');
  };
}

/* ─── ENTER MAP ─── */
function enterMap() {
  $('#mapTitle').textContent = cfg.title;
  $('#mapSub').textContent = me.isTeacher
    ? 'Live view — students appear as they pick stations'
    : 'Tap a station on the map to start working';
  const joinCode = me.isTeacher ? getJoinCode(classCode) : classCode;
  $('#mapCodeBadge').textContent = 'CODE: ' + (me.isTeacher ? getJoinCode(classCode) : classCode);
  $('#mapCodeBadge').title = me.isTeacher ? 'Share this full code with students: ' + getJoinCode(classCode) : '';
  $('#mapCodeBadge').style.cursor = me.isTeacher ? 'pointer' : '';
  if (me.isTeacher) {
    $('#mapCodeBadge').onclick = () => {
      const jc = getJoinCode(classCode);
      navigator.clipboard && navigator.clipboard.writeText(jc).catch(()=>{});
      const orig = $('#mapCodeBadge').textContent;
      $('#mapCodeBadge').textContent = '✅ Copied!';
      setTimeout(() => { $('#mapCodeBadge').textContent = 'CODE: ' + getJoinCode(classCode); }, 1800);
    };
  }
  $('#teacherPanel').classList.toggle('hide', !me.isTeacher);
  $('#legendHelp').classList.toggle('hide', !me.isTeacher);
  if (me.isTeacher) buildThemeBar();
  renderBar();
  show('view-map');
  refresh();
  startPoll();
}

/* ─── THEME BAR ─── */
function buildThemeBar() {
  const bar = $('#themeSwatches'); bar.innerHTML = '';
  THEMES.forEach(t => {
    const b = document.createElement('div');
    b.className = 'swatch' + (cfg.theme === t.id ? ' on' : '');
    b.title = t.name; b.style.background = t.sw;
    b.onclick = async () => {
      cfg.theme = t.id; applyTheme(t.id);
      await sSet(K_CFG(), cfg); buildThemeBar();
    };
    bar.appendChild(b);
  });
  $('#numStations').value = cfg.numStations;
  updateStationsLockUI();
}

function updateStationsLockUI() {
  const locked = cfg.classOpen;
  $('#stationsSetupGrp').classList.toggle('hide', locked);
  $('#stationsLockedGrp').classList.toggle('hide', !locked);
  if (locked) $('#stationsLockedCount').textContent = cfg.numStations;
}

$('#applyNum').addEventListener('click', async () => {
  const n = Math.max(2, Math.min(12, parseInt($('#numStations').value) || 6));
  cfg.numStations = n; $('#numStations').value = n;
  await sSet(K_CFG(), cfg); refresh();
});

/* ─── ADD STATION ─── */
$('#addStationBtn').addEventListener('click', () => {
  $('#newStationName').value = '';
  $('#newStationTask').value = '';
  const m = $('#addStationModal');
  m.style.display = 'flex';
  setTimeout(() => $('#newStationTask').focus(), 80);
});
$('#addStationCancel').addEventListener('click', () => { $('#addStationModal').style.display = 'none'; });
$('#addStationModal').addEventListener('click', e => { if (e.target === $('#addStationModal')) $('#addStationModal').style.display = 'none'; });
$('#addStationConfirm').addEventListener('click', async () => {
  const taskText = $('#newStationTask').value.trim();
  const customName = $('#newStationName').value.trim();
  if (!taskText) { $('#newStationTask').focus(); return; }
  const newIdx = cfg.numStations + 1;
  cfg.numStations = newIdx;
  cfg.classOpen = true;
  if (!cfg.stationNames) cfg.stationNames = {};
  if (!cfg.taskCards) cfg.taskCards = {};
  if (customName) cfg.stationNames[newIdx] = customName;
  cfg.taskCards[newIdx] = taskText;
  await sSet(K_CFG(), cfg);
  // Auto-invite all active students: set a flag they'll pick up on next refresh
  const keys = await sList('stu:' + classCode + ':');
  for (const k of keys) {
    const s = await sGet(k);
    if (s) { s.newStation = newIdx; s.ts = Date.now(); await sSet(k, s); }
  }
  $('#addStationModal').style.display = 'none';
  refresh();
});

$('#editTitleBtn').addEventListener('click', async () => {
  const t = prompt('Classroom name:', cfg.title);
  if (t && t.trim()) {
    cfg.title = t.trim();
    $('#mapTitle').textContent = cfg.title;
    await sSet(K_CFG(), cfg);
  }
});

$('#clearHelp').addEventListener('click', async () => {
  const keys = await sList('stu:' + classCode + ':');
  for (const k of keys) { const s = await sGet(k); if (s && s.status==='help') { s.status='busy'; s.ts=Date.now(); await sSet(k,s); } }
  refresh();
});
$('#clearCards').addEventListener('click', async () => {
  const keys = await sList('stu:' + classCode + ':');
  for (const k of keys) { const s = await sGet(k); if (s && s.card && s.card!=='none') { s.card='none'; s.ts=Date.now(); await sSet(k,s); } }
  refresh();
});
$('#resetAll').addEventListener('click', async () => {
  if (!confirm('Remove all students from the map?')) return;
  const keys = await sList('stu:' + classCode + ':');
  for (const k of keys) await sDel(k);
  const chats = await sList('chat:' + classCode + ':');
  for (const k of chats) await sDel(k);
  $('#teacherChat').classList.add('hide'); chatTarget = null;
  refresh();
});

/* ─── LAYOUT ─── */
function layout(n) {
  const p = {
    2:  [[22,36],[60,36]],
    3:  [[16,28],[50,52],[72,24]],
    4:  [[14,20],[62,16],[14,60],[62,60]],
    5:  [[12,16],[56,12],[34,42],[12,68],[60,66]],
    6:  [[10,14],[40,10],[70,18],[12,60],[44,64],[72,56]],
    7:  [[8,12],[38,8],[68,14],[10,42],[56,42],[16,70],[60,70]],
    8:  [[8,10],[36,6],[64,12],[8,38],[62,36],[10,66],[38,70],[68,66]],
    9:  [[6,8],[32,4],[62,10],[6,34],[36,38],[66,32],[8,62],[36,66],[66,60]],
    10: [[6,6],[30,2],[60,8],[6,32],[34,36],[64,30],[6,60],[32,64],[62,58],[36,84]],
    11: [[4,4],[28,0],[56,4],[4,28],[32,32],[60,26],[4,56],[28,60],[58,54],[16,78],[48,80]],
    12: [[4,2],[26,0],[52,2],[4,26],[28,30],[56,24],[4,54],[26,58],[54,52],[8,76],[34,78],[60,72]],
  };
  return p[n] || (function() {
    // Dynamic layout for n > 12: distribute in a grid-like pattern
    const pts = [];
    const cols = Math.ceil(Math.sqrt(n));
    for (let i = 0; i < n; i++) {
      const col = i % cols, row = Math.floor(i / cols);
      pts.push([8 + col * (84 / (cols - 1 || 1)), 8 + row * 72 / Math.max(1, Math.ceil(n / cols) - 1)]);
    }
    return pts;
  })();
}

/* ─── REFRESH ─── */
async function refresh() {
  const fresh = await sGet(K_CFG());
  if (fresh) {
    if (fresh.theme !== cfg.theme) applyTheme(fresh.theme);
    cfg = Object.assign(cfg, fresh);
  }
  if (!me.isTeacher) applyTheme(cfg.theme);
  $('#mapTitle').textContent = cfg.title;
  if (me.isTeacher) updateStationsLockUI();

  const keys = await sList('stu:' + classCode + ':');
  const students = [];
  for (const k of keys) { const s = await sGet(k); if (s) students.push(s); }

  const byStation = {};
  students.forEach(s => { if (s.station) (byStation[s.station] = byStation[s.station] || []).push(s); });

  // Help banner
  const helpers = students.filter(s => s.status === 'help');
  const hb = $('#helpBanner');
  if (me.isTeacher && helpers.length) {
    hb.classList.remove('hide');
    hb.innerHTML = '🙋 ' + helpers.map(s => esc(s.name) + ' (' + stationLabel(s.station, cfg.numStations) + ')').join(' · ') + ' need clarification!';
  } else hb.classList.add('hide');

  // Card banner
  const carders = students.filter(s => s.card && s.card !== 'none');
  const cb = $('#cardBanner');
  if (carders.length) {
    cb.classList.remove('hide');
    cb.innerHTML = '🃏 ' + carders.map(s => esc(s.name) + (s.card==='group'?' (group)':'') + ' — ' + stationLabel(s.station, cfg.numStations)).join(' · ');
  } else cb.classList.add('hide');

  // Chat banner
  const chatB = $('#chatBanner');
  if (me.isTeacher) {
    const waiting = [];
    for (const s of students) {
      const c = await getChat(s.name);
      const last = c.messages[c.messages.length-1];
      if (last && last.from === 'student') waiting.push(s.name);
    }
    if (waiting.length) {
      chatB.classList.remove('hide');
      chatB.innerHTML = '💬 Messages from: ' + waiting.map(n => `<a href="#" data-n="${encodeURIComponent(n)}">${esc(n)}</a>`).join(', ');
      chatB.querySelectorAll('a').forEach(a => a.onclick = e => { e.preventDefault(); openTeacherChat(decodeURIComponent(a.dataset.n)); });
    } else chatB.classList.add('hide');
  } else chatB.classList.add('hide');

  // New station invite banner for students
  let invBanner = document.getElementById('inviteBanner');
  if (!invBanner) {
    invBanner = document.createElement('div');
    invBanner.id = 'inviteBanner'; invBanner.className = 'banner banner-chat hide';
    $('#chatBanner').insertAdjacentElement('afterend', invBanner);
  }
  if (!me.isTeacher) {
    const myRec = await sGet(kStu(me.name));
    if (myRec && myRec.newStation) {
      const ns = myRec.newStation;
      invBanner.classList.remove('hide');
      invBanner.innerHTML = `🆕 New station added: <strong>${esc(stationLabel(ns, cfg.numStations))}</strong> — <a href="#" id="goNewStation" style="color:var(--go);font-weight:700">Join it now →</a>`;
      document.getElementById('goNewStation').onclick = async e => {
        e.preventDefault();
        const r = await sGet(kStu(me.name));
        if (r) { delete r.newStation; await sSet(kStu(me.name), r); }
        invBanner.classList.add('hide');
        openTask(ns);
      };
    } else {
      invBanner.classList.add('hide');
    }
  } else {
    invBanner.classList.add('hide');
  }

  // Draw floor
  const pos = layout(cfg.numStations);
  const floor = $('#floor'); floor.innerHTML = '';

  for (let i = 0; i < cfg.numStations; i++) {
    const idx = i + 1;
    const occ = byStation[idx] || [];
    const hasHelp = me.isTeacher && occ.some(s => s.status === 'help');
    const hasCard = occ.some(s => s.card && s.card !== 'none');
    const allDone = occ.length > 0 && occ.every(s => s.status === 'done');
    const isFinal = idx === cfg.numStations;

    const el = document.createElement('div');
    el.className = 'station' + (hasHelp?' has-help':'') + (hasCard&&!hasHelp?' has-card':'') + (isFinal?' is-final':'');
    if (pos[i]) { el.style.left = pos[i][0]+'%'; el.style.top = pos[i][1]+'%'; }
    el.style.borderTopColor = hasHelp ? 'var(--accent2)' : hasCard ? 'var(--blue)' : occ.length ? (allDone ? 'var(--go)' : 'var(--warn)') : 'rgba(255,255,255,.15)';

    const chips = occ.map(s => {
      const mine = (!me.isTeacher && s.name === me.name) ? ' chip-me' : '';
      let st = s.status; if (!me.isTeacher && st==='help') st = 'busy';
      const cardMark = (s.card && s.card!=='none') ? ' 🃏' : '';
      const clk = me.isTeacher ? ` chip-clickable" data-n="${encodeURIComponent(s.name)}` : '';
      return `<span class="chip chip-${st}${mine}${clk}">${esc(s.name)}${cardMark}</span>`;
    }).join('') || '<span style="font-size:10px;opacity:.3">empty</span>';

    const taskCard = (cfg.taskCards && cfg.taskCards[idx])
      ? `<div class="station-taskcard">🃏 ${esc(cfg.taskCards[idx])}</div>` : '';

    el.innerHTML = `${occ.length ? `<span class="station-cnt">${occ.length}</span>` : ''}
      <div class="station-kicker">${stationKicker(idx, cfg.numStations)}</div>
      <div class="station-label">${stationLabel(idx, cfg.numStations)}</div>
      <div class="station-occ">${chips}</div>
      ${taskCard}`;

    if (!me.isTeacher) {
      el.onclick = () => openTask(idx);
    } else {
      el.querySelectorAll('.chip-clickable').forEach(ch => {
        ch.onclick = e => { e.stopPropagation(); openTeacherChat(decodeURIComponent(ch.dataset.n)); };
      });
    }
    floor.appendChild(el);
  }
}

/* ─── STUDENT TASK ─── */
async function openTask(idx) {
  const rec = await sGet(kStu(me.name));
  if (rec && rec.station && rec.station !== idx) {
    if (!confirm('Move from "' + stationLabel(rec.station, cfg.numStations) + '" to "' + stationLabel(idx, cfg.numStations) + '"?')) return;
  }
  current.idx = idx;
  $('#dNum').textContent = idx === cfg.numStations ? '🎯' : idx;
  $('#dName').textContent = stationLabel(idx, cfg.numStations);
  $('#dWho').textContent = me.name;
  const sameStation = rec && rec.station === idx;
  const keepCard   = sameStation ? (rec.card || 'none') : 'none';
  const keepStatus = (sameStation && rec.status === 'done') ? 'done' : 'busy';
  await save(idx, keepStatus, keepCard);
  paintBanner(keepStatus, keepCard);
  document.body.classList.add('docked');
  document.body.classList.remove('station-min');
  $('#minBtn').textContent = '— Minimise';
  $('#taskDock').classList.remove('hide');
  loadChat();
  refresh();
}

function paintBanner(status, card) {
  const b = $('#dBanner');
  let msg = status==='help' ? '🙋 Teacher notified — clarification is on the way!'
          : status==='done' ? '✅ Finished — pick your next station!'
          : '📍 Shown as working here.';
  if (card && card!=='none') msg = '🃏 Card requested. ' + msg;
  b.className = 'dock-banner ' + (card&&card!=='none' ? 'card' : status);
  b.textContent = msg;
}

async function save(station, status, card) {
  await sSet(kStu(me.name), { name:me.name, station, status, card:card||'none', ts:Date.now() });
}
async function currentRec() {
  return await sGet(kStu(me.name)) || { station:current.idx, status:'busy', card:'none' };
}

$('#aWork').onclick    = async()=>{ const r=await currentRec(); await save(current.idx,'busy',r.card); paintBanner('busy',r.card); refresh(); };
$('#aHelp').onclick    = async()=>{ const r=await currentRec(); await save(current.idx,'help',r.card); paintBanner('help',r.card); refresh(); };
$('#aCardMe').onclick  = async()=>{ const r=await currentRec(); await save(current.idx,r.status,'me');    paintBanner(r.status,'me'); refresh(); };
$('#aCardGroup').onclick=async()=>{ const r=await currentRec(); await save(current.idx,r.status,'group'); paintBanner(r.status,'group'); refresh(); };
$('#aDone').onclick    = async()=>{ const r=await currentRec(); await save(current.idx,'done',r.card); paintBanner('done',r.card); refresh(); };
$('#aNext').onclick    = ()=>{ closeDock(); refresh(); };
$('#aLeave').onclick   = async()=>{
  const rec = await sGet(kStu(me.name));
  if (rec && rec.station===current.idx) await sSet(kStu(me.name),{name:me.name,station:null,status:'idle',card:'none',ts:Date.now()});
  closeDock(); refresh();
};

function closeDock() {
  $('#taskDock').classList.add('hide');
  document.body.classList.remove('docked','station-min');
}

$('#minBtn').onclick = () => {
  const on = document.body.classList.toggle('station-min');
  $('#minBtn').textContent = on ? '▣ Expand' : '— Minimise';
};

/* ─── CHAT ─── */
async function getChat(name) { return (await sGet(kChat(name))) || { messages:[] }; }

function renderChatLog(el, messages, isStudent) {
  if (!messages.length) { el.innerHTML='<div class="chat-empty">No messages yet 👋</div>'; return; }
  el.innerHTML = messages.map(m => {
    const fromMe = isStudent ? m.from==='student' : m.from==='teacher';
    const who = m.from==='teacher' ? 'Teacher' : esc(m.fromName||'Student');
    return `<div class="msg ${fromMe?'me':'them'}"><span class="mfrom">${who}</span>${esc(m.text)}</div>`;
  }).join('');
  el.scrollTop = el.scrollHeight;
}

async function loadChat() {
  const c = await getChat(me.name);
  renderChatLog($('#chatLog'), c.messages, true);
}

$('#chatSend').onclick = studentSend;
$('#chatText').onkeydown = e => { if(e.key==='Enter') studentSend(); };
async function studentSend() {
  const t = $('#chatText').value.trim(); if (!t) return;
  $('#chatText').value = '';
  const c = await getChat(me.name);
  c.messages.push({ from:'student', fromName:me.name, text:t, ts:Date.now() });
  await sSet(kChat(me.name), c);
  renderChatLog($('#chatLog'), c.messages, true);
}

async function openTeacherChat(name) {
  chatTarget = name; lastChatSig = '';
  $('#tChatName').textContent = name;
  $('#teacherChat').classList.remove('hide');
  const c = await getChat(name);
  renderChatLog($('#tChatLog'), c.messages, false);
  $('#tChatText').focus();
}
$('#tChatClose').onclick = () => { $('#teacherChat').classList.add('hide'); chatTarget=null; };
$('#tChatSend').onclick = teacherSend;
$('#tChatText').onkeydown = e => { if(e.key==='Enter') teacherSend(); };
async function teacherSend() {
  if (!chatTarget) return;
  const t = $('#tChatText').value.trim(); if (!t) return;
  $('#tChatText').value = '';
  const c = await getChat(chatTarget);
  c.messages.push({ from:'teacher', text:t, ts:Date.now() });
  await sSet(kChat(chatTarget), c);
  renderChatLog($('#tChatLog'), c.messages, false);
}

/* ─── POLLING ─── */
function startPoll() {
  stopPoll();
  poll = setInterval(async () => {
    await _pollBin();   // fetch latest data from JSONBin
    await refresh();
    await pollChat();
  }, 2500);
}
function stopPoll()  { if (poll) { clearInterval(poll); poll=null; } }

async function pollChat() {
  if (!me.isTeacher && document.body.classList.contains('docked')) {
    const c = await getChat(me.name);
    const sig = c.messages.map(m=>m.ts).join(',');
    if (sig !== lastChatSig) { lastChatSig=sig; renderChatLog($('#chatLog'),c.messages,true); }
  }
  if (me.isTeacher && chatTarget && !$('#teacherChat').classList.contains('hide')) {
    const c = await getChat(chatTarget);
    const sig = c.messages.map(m=>m.ts).join(',');
    if (sig !== lastChatSig) { lastChatSig=sig; renderChatLog($('#tChatLog'),c.messages,false); }
  }
}

/* ─── INIT ─── */
// Warn if API key not configured
if (JSONBIN_API_KEY.includes('PASTE_YOUR')) {
  const warn = document.createElement('div');
  warn.style.cssText = 'position:fixed;top:0;left:0;right:0;z-index:999;background:#f5a623;color:#1a0a00;padding:12px 20px;font-weight:700;font-size:13px;text-align:center;font-family:DM Sans,sans-serif';
  warn.innerHTML = '⚙️ Setup required: open the HTML file, find <code>JSONBIN_API_KEY</code> near the top of the &lt;script&gt;, and paste your free key from <a href="https://jsonbin.io" target="_blank" style="color:#1a0a00">jsonbin.io</a>';
  document.body.prepend(warn);
}
show('view-login');
</script>
</body>
</html>

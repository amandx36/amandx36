<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>amandx36 — Aman Deep</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;600;700;800;900&family=Rajdhani:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --g:#00ff88;--gb:#00ff8833;--gd:#00aa55;
  --b:#00d4ff;--r:#ff3860;--gold:#ffd700;
  --bg0:#010a05;--bg1:#001208;--bg2:#001a0e;--bg3:#002a14;
  --mono:'Share Tech Mono',monospace;
  --orb:'Orbitron',monospace;
  --raj:'Rajdhani',sans-serif;
}
html,body{min-height:100vh;background:#000;display:flex;align-items:center;justify-content:center;padding:20px}
.root{
  width:100%;max-width:860px;
  background:var(--bg0);color:var(--g);
  font-family:var(--mono);
  border-radius:16px;
  border:1px solid #00ff8844;
  position:relative;overflow:hidden;
  box-shadow:0 0 60px #00ff8815,0 0 120px #00ff8808;
}
canvas#bg{position:absolute;inset:0;width:100%;height:100%;opacity:.1;pointer-events:none;z-index:0}
canvas#ptc{position:absolute;inset:0;width:100%;height:100%;pointer-events:none;z-index:1}
.scanlines{position:absolute;inset:0;background:repeating-linear-gradient(0deg,transparent,transparent 3px,rgba(0,255,136,.01) 3px,rgba(0,255,136,.01) 4px);pointer-events:none;z-index:50;border-radius:16px}
.corner{position:absolute;width:20px;height:20px;z-index:60}
.corner.tl{top:8px;left:8px;border-top:2px solid var(--g);border-left:2px solid var(--g)}
.corner.tr{top:8px;right:8px;border-top:2px solid var(--g);border-right:2px solid var(--g)}
.corner.bl{bottom:8px;left:8px;border-bottom:2px solid var(--g);border-left:2px solid var(--g)}
.corner.br{bottom:8px;right:8px;border-bottom:2px solid var(--g);border-right:2px solid var(--g)}
.wrap{position:relative;z-index:10}

/* ── HERO ── */
.hero{padding:28px 28px 20px;display:flex;gap:22px;align-items:flex-start;border-bottom:1px solid var(--gb);background:linear-gradient(160deg,#002a1433 0%,transparent 60%)}
.av-ring{width:100px;height:100px;flex-shrink:0;position:relative}
.av-ring canvas{position:absolute;inset:0;width:100px;height:100px}
.av-inner{position:absolute;inset:11px;border-radius:50%;background:#001208;display:flex;align-items:center;justify-content:center;flex-direction:column;gap:2px;border:1px solid #00ff8822}
.av-letters{font-family:var(--orb);font-size:22px;font-weight:900;color:#fff;text-shadow:0 0 15px var(--g);letter-spacing:2px}
.av-sub{font-size:7px;color:var(--gd);letter-spacing:3px}
.online-dot{position:absolute;bottom:7px;right:7px;width:13px;height:13px;background:var(--g);border-radius:50%;border:2px solid var(--bg0);box-shadow:0 0 8px var(--g);animation:pulse 1.5s ease infinite}
@keyframes pulse{0%,100%{transform:scale(1);opacity:1}50%{transform:scale(1.4);opacity:.5}}

.hero-info{flex:1;min-width:0}
.name-wrap{display:flex;align-items:center;gap:10px;margin-bottom:4px;flex-wrap:wrap}
.name{font-family:var(--orb);font-size:28px;font-weight:900;color:#fff;text-shadow:0 0 30px var(--g),0 0 60px #00ff8815;letter-spacing:3px;position:relative;display:inline-block}
.name::after{content:'AMAN DEEP';position:absolute;inset:0;color:var(--r);opacity:0;animation:glitch 7s steps(1) infinite}
@keyframes glitch{0%,88%,100%{opacity:0;transform:none}89%{opacity:.8;transform:translate(3px,-1px);clip-path:inset(20% 0 55% 0)}91%{opacity:.5;transform:translate(-2px,1px);clip-path:inset(65% 0 10% 0)}93%{opacity:0}}
.badges{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:8px}
.badge{font-family:var(--orb);font-size:8px;font-weight:700;padding:3px 9px;border-radius:3px;letter-spacing:1.5px}
.b-g{background:var(--g);color:#001208;animation:bglow 2s ease infinite}
.b-b{background:#00d4ff18;border:1px solid var(--b);color:var(--b)}
.b-r{background:#ff386018;border:1px solid var(--r);color:var(--r)}
.b-gold{background:#ffd70018;border:1px solid var(--gold);color:var(--gold)}
@keyframes bglow{0%,100%{box-shadow:0 0 5px var(--g)}50%{box-shadow:0 0 15px var(--g),0 0 30px #00ff8844}}
.tagline{font-family:var(--raj);font-size:14px;font-weight:600;color:#aaffcc;margin-bottom:8px;line-height:1.6}
.tagline .pipe{color:var(--r);margin:0 5px}
.meta-line{font-size:10px;color:var(--gd);letter-spacing:.5px;margin-bottom:12px}
.stats{display:flex;gap:0;flex-wrap:wrap}
.st{text-align:center;padding:5px 14px;border-right:1px solid var(--gb);display:flex;flex-direction:column;gap:1px}
.st:last-child{border-right:none}
.sn{font-family:var(--orb);font-size:18px;font-weight:900;color:var(--g);text-shadow:0 0 8px var(--g)}
.sl{font-size:8px;color:var(--gd);letter-spacing:1.5px;text-transform:uppercase}

/* ── TERMINAL BAR ── */
.tbar{background:#000805;border-bottom:1px solid #00ff8814;padding:7px 24px;display:flex;align-items:center;gap:8px;overflow:hidden}
.tp{color:var(--g);font-weight:bold;font-size:10px;white-space:nowrap}
.tc{color:var(--b);font-size:10px;flex:1;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.tcur{display:inline-block;width:7px;height:11px;background:var(--g);vertical-align:middle;animation:cblink 1s step-end infinite}
@keyframes cblink{0%,100%{opacity:1}50%{opacity:0}}

/* ── BODY GRID ── */
.grid{display:grid;grid-template-columns:1fr 1fr;gap:1px;background:#00ff8810}
.panel{background:var(--bg1);padding:16px 18px}
.full{grid-column:1/-1}
.ptitle{font-family:var(--orb);font-size:8px;font-weight:700;color:var(--g);letter-spacing:2.5px;margin-bottom:12px;display:flex;align-items:center;gap:7px;text-transform:uppercase}
.ptitle-bar{flex:0 0 3px;height:12px;background:var(--g);border-radius:2px;box-shadow:0 0 6px var(--g)}

/* PROJECT CARD */
.pcard{background:var(--bg2);border:1px solid var(--gb);border-left:3px solid var(--g);border-radius:7px;padding:12px 14px;cursor:pointer;transition:.2s;position:relative;overflow:hidden}
.pcard:hover{border-color:var(--g);box-shadow:0 0 20px #00ff8818;background:var(--bg3)}
.pc-top{display:flex;align-items:center;gap:10px;margin-bottom:8px}
.pc-ico{width:36px;height:36px;background:#001208;border:1px solid var(--g);border-radius:6px;display:flex;align-items:center;justify-content:center;font-family:var(--orb);font-size:10px;font-weight:700;color:var(--r);flex-shrink:0}
.pc-name{font-family:var(--raj);font-size:15px;font-weight:700;color:#fff}
.pc-tech{font-size:10px;color:var(--gd);margin-top:1px}
.live-tag{margin-left:auto;padding:3px 8px;border-radius:3px;font-size:8px;font-family:var(--orb);letter-spacing:1px;border:1px solid var(--r);color:var(--r);animation:pulse 1.5s ease infinite;flex-shrink:0}
.bar-track{height:4px;background:var(--bg0);border-radius:2px;overflow:hidden;margin-top:6px}
.bar-fill{height:100%;background:linear-gradient(90deg,var(--g),var(--b));box-shadow:0 0 6px var(--g);border-radius:2px;animation:barin 1.6s ease forwards}
@keyframes barin{from{width:0}to{width:73%}}
.pc-meta{font-size:9px;color:var(--gd);margin-top:5px}

/* SKILL CONSTELLATION */
.skillwrap{position:relative;height:200px}
.skillwrap canvas{position:absolute;inset:0;width:100%;height:200px}

/* LANGUAGE BARS */
.lbars{display:flex;flex-direction:column;gap:9px}
.lb{display:flex;align-items:center;gap:9px}
.lbname{font-family:var(--raj);font-size:12px;font-weight:600;color:#aaffcc;width:76px;flex-shrink:0}
.lbtrack{flex:1;height:5px;background:var(--bg0);border-radius:3px;overflow:hidden;border:1px solid #00ff8815}
.lbfill{height:100%;border-radius:3px;animation:barin2 1.5s ease forwards}
@keyframes barin2{from{width:0}}
.lbpct{font-size:9px;color:var(--gd);width:28px;text-align:right;flex-shrink:0}

/* HEATMAP */
.hmap-scroll{overflow-x:auto;padding-bottom:2px}
.hmap{display:grid;grid-template-columns:repeat(52,1fr);gap:2px;min-width:520px}
.hw{display:flex;flex-direction:column;gap:2px}
.hd{border-radius:2px;aspect-ratio:1;cursor:default;transition:.1s}
.hd:hover{transform:scale(1.9);z-index:20;position:relative}
.h0{background:#001208;border:1px solid #00ff880d}
.h1{background:#003a1a}
.h2{background:#006b2e}
.h3{background:#00aa44;box-shadow:0 0 3px #00ff8855}
.h4{background:#00ff88;box-shadow:0 0 6px #00ff88aa}

/* STREAK */
.srow{display:flex;align-items:center;justify-content:space-around;padding:10px 0}
.sblk{text-align:center}
.snum{font-family:var(--orb);font-size:38px;font-weight:900;color:var(--g);text-shadow:0 0 20px var(--g);line-height:1}
.sgold{color:var(--gold);text-shadow:0 0 20px var(--gold)}
.slabel{font-size:8px;color:var(--gd);letter-spacing:1.5px;margin-top:3px;text-transform:uppercase}
.sdiv{width:1px;height:55px;background:var(--gb)}
.fireico{font-size:42px;animation:firesh .45s ease-in-out infinite alternate;display:inline-block}
@keyframes firesh{from{transform:rotate(-6deg) scale(1)}to{transform:rotate(6deg) scale(1.12)}}

/* LIVE FEED */
.feed{display:flex;flex-direction:column;gap:5px;position:relative;overflow:hidden;max-height:130px}
.feed::after{content:'';position:absolute;bottom:0;left:0;right:0;height:35px;background:linear-gradient(transparent,var(--bg1));pointer-events:none}
.fl{font-size:10px;display:flex;gap:7px;align-items:baseline;line-height:1.5}
.ftime{color:var(--gd);flex-shrink:0;font-size:9px}
.fok{color:var(--g)}
.fwarn{color:var(--gold)}
.ferr{color:var(--r)}

/* SOCIAL */
.socgrid{display:grid;grid-template-columns:repeat(2,1fr);gap:7px}
.sbtn{background:var(--bg2);border:1px solid var(--gb);border-radius:7px;padding:9px 12px;color:var(--g);font-family:var(--raj);font-size:12px;font-weight:700;letter-spacing:.5px;cursor:pointer;transition:.2s;display:flex;align-items:center;gap:8px;text-decoration:none}
.sbtn:hover{background:var(--bg3);border-color:var(--g);box-shadow:0 0 12px var(--gb);color:#fff}
.sico{width:28px;height:28px;border-radius:5px;display:flex;align-items:center;justify-content:center;font-size:13px;flex-shrink:0}

/* FUN FACT */
.funfact{background:var(--bg2);border:1px solid var(--gb);border-left:3px solid var(--gold);border-radius:0 6px 6px 0;padding:12px 48px 12px 14px;font-family:var(--raj);font-size:13px;font-weight:500;color:#ffffcc;line-height:1.6;position:relative}
.ffic{position:absolute;right:14px;top:11px;font-size:20px;animation:firesh .6s ease infinite alternate}

/* REPOS */
.repos{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.repo{background:var(--bg2);border:1px solid var(--gb);border-radius:6px;padding:10px 12px;transition:.2s;cursor:pointer}
.repo:hover{border-color:var(--g);box-shadow:0 0 10px var(--gb)}
.repo-name{font-family:var(--raj);font-size:13px;font-weight:700;color:var(--b);margin-bottom:3px}
.repo-desc{font-size:10px;color:var(--gd);margin-bottom:7px;line-height:1.4}
.repo-meta{display:flex;gap:10px;font-size:9px;color:var(--gd)}
.repo-lang{display:flex;align-items:center;gap:3px}
.langdot{width:8px;height:8px;border-radius:50%;flex-shrink:0}

/* FOOTER */
.footer{background:#000805;border-top:1px solid #00ff8810;padding:8px 24px;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:6px}
.fe{font-size:9px;color:#005530;letter-spacing:.5px}
.femail{color:var(--gd);font-size:10px}
.fstatus{color:var(--g);display:flex;align-items:center;gap:5px;font-size:9px;letter-spacing:1px}
.fdot{width:6px;height:6px;background:var(--g);border-radius:50%;box-shadow:0 0 4px var(--g);animation:pulse 2s ease infinite}

/* LEARNING TAGS */
.ltags{display:flex;flex-wrap:wrap;gap:7px}
.ltag{background:var(--bg2);border:1px solid #00ff8828;border-radius:5px;padding:6px 11px;font-family:var(--raj);font-size:12px;font-weight:600;color:var(--g);display:flex;align-items:center;gap:6px;transition:.2s;cursor:default}
.ltag:hover{background:var(--bg3);border-color:var(--g);box-shadow:0 0 8px var(--gb)}
.ldot{width:6px;height:6px;border-radius:50%;background:var(--g);box-shadow:0 0 4px var(--g);animation:pulse 2s ease infinite}
</style>
</head>
<body>
<div class="root" id="root">
  <canvas id="bg"></canvas>
  <canvas id="ptc"></canvas>
  <div class="scanlines"></div>
  <div class="corner tl"></div><div class="corner tr"></div>
  <div class="corner bl"></div><div class="corner br"></div>

  <div class="wrap">

    <!-- HERO -->
    <div class="hero">
      <div class="av-ring">
        <canvas id="ringc" width="100" height="100"></canvas>
        <div class="av-inner">
          <div class="av-letters">AD</div>
          <div class="av-sub">DEV</div>
        </div>
        <div class="online-dot"></div>
      </div>

      <div class="hero-info">
        <div class="name-wrap">
          <span class="name">AMAN DEEP</span>
        </div>
        <div class="badges">
          <span class="badge b-g">FULL STACK</span>
          <span class="badge b-b">ML ENGINEER</span>
          <span class="badge b-r">CYBER SEC</span>
          <span class="badge b-gold">ARCH LINUX</span>
        </div>
        <div class="tagline">Code<span class="pipe">|</span>Debug<span class="pipe">|</span>Deploy<span class="pipe">|</span>Break Arch<span class="pipe">|</span>Fix<span class="pipe">|</span>Repeat</div>
        <div class="meta-line">@amandx36 &nbsp;·&nbsp; Greater Noida, IN &nbsp;·&nbsp; xamandeep360@gmail.com</div>
        <div class="stats">
          <div class="st"><span class="sn" id="c-num">0</span><span class="sl">Commits</span></div>
          <div class="st"><span class="sn">41</span><span class="sl">Followers</span></div>
          <div class="st"><span class="sn">13</span><span class="sl">Repos</span></div>
          <div class="st"><span class="sn" style="color:var(--gold);text-shadow:0 0 10px var(--gold)">B-</span><span class="sl">Grade</span></div>
          <div class="st"><span class="sn" style="color:var(--b);text-shadow:0 0 10px var(--b)">4</span><span class="sl">Stars</span></div>
        </div>
      </div>
    </div>

    <!-- TERMINAL -->
    <div class="tbar">
      <span class="tp">root@amandx36 ~ $</span>
      <span class="tc" id="tcmd"></span>
      <span class="tcur"></span>
    </div>

    <!-- BODY -->
    <div class="grid">

      <!-- ACTIVE PROJECT -->
      <div class="panel">
        <div class="ptitle"><span class="ptitle-bar"></span>Active Project</div>
        <div class="pcard">
          <div class="pc-top">
            <div class="pc-ico">SS</div>
            <div>
              <div class="pc-name">Secure-Sense</div>
              <div class="pc-tech">Python &nbsp;·&nbsp; ML &nbsp;·&nbsp; CyberSec</div>
            </div>
            <div class="live-tag">LIVE</div>
          </div>
          <div class="bar-track"><div class="bar-fill"></div></div>
          <div class="pc-meta">Progress: 73% &nbsp;·&nbsp; Last commit: 2 days ago</div>
        </div>
      </div>

      <!-- CURRENTLY LEARNING -->
      <div class="panel">
        <div class="ptitle"><span class="ptitle-bar"></span>Currently Learning</div>
        <div class="ltags">
          <span class="ltag"><span class="ldot"></span>Machine Learning</span>
          <span class="ltag"><span class="ldot"></span>Full Stack Dev</span>
          <span class="ltag"><span class="ldot"></span>Cyber Security</span>
          <span class="ltag"><span class="ldot"></span>TensorFlow</span>
          <span class="ltag"><span class="ldot"></span>Docker</span>
        </div>
      </div>

      <!-- SKILL CONSTELLATION -->
      <div class="panel">
        <div class="ptitle"><span class="ptitle-bar"></span>Skill Constellation</div>
        <div class="skillwrap">
          <canvas id="skillc"></canvas>
        </div>
      </div>

      <!-- LIVE FEED -->
      <div class="panel">
        <div class="ptitle"><span class="ptitle-bar"></span>Live System Feed</div>
        <div class="feed" id="feed">
          <div class="fl"><span class="ftime">[00:01]</span><span class="fok">INFO &nbsp;</span><span>SSH login · amandx36@arch</span></div>
          <div class="fl"><span class="ftime">[00:03]</span><span class="fok">OK &nbsp;&nbsp;&nbsp;</span><span>Secure-Sense accuracy: 94.2%</span></div>
          <div class="fl"><span class="ftime">[00:07]</span><span class="fwarn">WARN &nbsp;</span><span>Pacman: 142 packages pending</span></div>
          <div class="fl"><span class="ftime">[00:11]</span><span class="fok">PUSH &nbsp;</span><span>git push origin main · +47 -12</span></div>
          <div class="fl"><span class="ftime">[00:14]</span><span class="fok">BUILD </span><span>Docker image built: secure-sense:latest</span></div>
          <div class="fl"><span class="ftime">[00:18]</span><span class="ferr">BLOCK </span><span>Port scan blocked · IP banned</span></div>
          <div class="fl"><span class="ftime">[00:22]</span><span class="fok">TRAIN </span><span>Epoch 48/100 · loss: 0.0234</span></div>
        </div>
      </div>

      <!-- LANGUAGE BARS -->
      <div class="panel">
        <div class="ptitle"><span class="ptitle-bar"></span>Language Arsenal</div>
        <div class="lbars">
          <div class="lb"><span class="lbname">HTML/CSS</span><div class="lbtrack"><div class="lbfill" style="width:90%;background:#ff6b35;box-shadow:0 0 4px #ff6b35"></div></div><span class="lbpct">90%</span></div>
          <div class="lb"><span class="lbname">Python</span><div class="lbtrack"><div class="lbfill" style="width:85%;background:var(--b);box-shadow:0 0 4px var(--b)"></div></div><span class="lbpct">85%</span></div>
          <div class="lb"><span class="lbname">C++</span><div class="lbtrack"><div class="lbfill" style="width:78%;background:var(--g);box-shadow:0 0 4px var(--g)"></div></div><span class="lbpct">78%</span></div>
          <div class="lb"><span class="lbname">JavaScript</span><div class="lbtrack"><div class="lbfill" style="width:70%;background:var(--gold);box-shadow:0 0 4px var(--gold)"></div></div><span class="lbpct">70%</span></div>
          <div class="lb"><span class="lbname">React</span><div class="lbtrack"><div class="lbfill" style="width:62%;background:#61dafb;box-shadow:0 0 4px #61dafb"></div></div><span class="lbpct">62%</span></div>
          <div class="lb"><span class="lbname">Java</span><div class="lbtrack"><div class="lbfill" style="width:55%;background:var(--r);box-shadow:0 0 4px var(--r)"></div></div><span class="lbpct">55%</span></div>
        </div>
      </div>

      <!-- STREAK -->
      <div class="panel">
        <div class="ptitle"><span class="ptitle-bar"></span>Streak Stats</div>
        <div class="srow">
          <div class="sblk"><div class="snum" id="streak-num">0</div><div class="slabel">Total Commits</div></div>
          <div class="sdiv"></div>
          <div class="fireico">🔥</div>
          <div class="sdiv"></div>
          <div class="sblk"><div class="snum sgold">Jul'24</div><div class="slabel">Active Since</div></div>
        </div>
      </div>

      <!-- HEATMAP -->
      <div class="panel full">
        <div class="ptitle"><span class="ptitle-bar"></span>Contribution Matrix — 2024/2025</div>
        <div class="hmap-scroll"><div class="hmap" id="hmap"></div></div>
      </div>

      <!-- REPOS -->
      <div class="panel full">
        <div class="ptitle"><span class="ptitle-bar"></span>Popular Repositories</div>
        <div class="repos">
          <div class="repo">
            <div class="repo-name">Secure-Sense</div>
            <div class="repo-desc">ML-powered cybersecurity threat detection using TensorFlow and Random Forest</div>
            <div class="repo-meta"><span class="repo-lang"><span class="langdot" style="background:#3572A5"></span>Python</span><span>⭐ 2</span><span>🍴 1</span></div>
          </div>
          <div class="repo">
            <div class="repo-name">MovieGenreClassifier</div>
            <div class="repo-desc">Genre classification using TV-DF and BERT embeddings with TensorFlow</div>
            <div class="repo-meta"><span class="repo-lang"><span class="langdot" style="background:#3572A5"></span>Python</span><span>⭐ 0</span></div>
          </div>
          <div class="repo">
            <div class="repo-name">Brackets.mid.project</div>
            <div class="repo-desc">Mid-semester project with bracket-based parsing and UI components</div>
            <div class="repo-meta"><span class="repo-lang"><span class="langdot" style="background:#f1e05a"></span>JavaScript</span><span>⭐ 1</span></div>
          </div>
          <div class="repo">
            <div class="repo-name">PlantsPyProject</div>
            <div class="repo-desc">Image-based plant disease detection using deep learning and PyTorch</div>
            <div class="repo-meta"><span class="repo-lang"><span class="langdot" style="background:#3572A5"></span>Python</span><span>⭐ 1</span></div>
          </div>
        </div>
      </div>

      <!-- SOCIAL -->
      <div class="panel">
        <div class="ptitle"><span class="ptitle-bar"></span>Connect With Me</div>
        <div class="socgrid">
          <a class="sbtn" href="https://linkedin.com/in/aman-deep" target="_blank"><div class="sico" style="background:#0a66c218">💼</div>LinkedIn</a>
          <a class="sbtn" href="https://instagram.com/amandx36" target="_blank"><div class="sico" style="background:#e1306c18">📸</div>Instagram</a>
          <a class="sbtn" href="https://leetcode.com/xamandeep" target="_blank"><div class="sico" style="background:#ffa11618">⚔️</div>LeetCode</a>
          <a class="sbtn" href="https://amandx36team.netlify.app" target="_blank"><div class="sico" style="background:#00ff8818">🌐</div>Portfolio</a>
        </div>
      </div>

      <!-- FUN FACT -->
      <div class="panel">
        <div class="ptitle"><span class="ptitle-bar"></span>Fun Fact</div>
        <div class="funfact">
          "I love Arch Linux… until it breaks. Then I hate it… until I fix it again 🐧🔥"
          <span class="ffic">⚡</span>
        </div>
      </div>

    </div><!-- /grid -->

    <div class="footer">
      <span class="fe">github.com/amandx36 · Jul 2024 – Present</span>
      <span class="femail">xamandeep360@gmail.com</span>
      <span class="fstatus"><span class="fdot"></span>ONLINE · BUILDING · UNSTOPPABLE</span>
    </div>

  </div><!-- /wrap -->
</div><!-- /root -->

<script>
const ROOT = document.getElementById('root');

// ── MATRIX BG ──
const bgc = document.getElementById('bg');
const bx = bgc.getContext('2d');
function resizeBg(){bgc.width=ROOT.offsetWidth;bgc.height=ROOT.offsetHeight}
resizeBg();
const MCHARS='アイウエオカキクケコサシスセソタチ01234567890ABCDEF{}[]<>/\\|';
let cols=Math.floor(bgc.width/14),drops=Array(cols).fill(1);
function matrix(){
  bx.fillStyle='rgba(1,10,5,0.055)';bx.fillRect(0,0,bgc.width,bgc.height);
  bx.fillStyle='#00ff88';bx.font='12px Share Tech Mono,monospace';
  for(let i=0;i<drops.length;i++){
    bx.fillText(MCHARS[Math.floor(Math.random()*MCHARS.length)],i*14,drops[i]*14);
    if(drops[i]*14>bgc.height&&Math.random()>.975)drops[i]=0;
    drops[i]++;
  }
}
setInterval(matrix,55);

// ── PARTICLES ──
const pc=document.getElementById('ptc');
const px=pc.getContext('2d');
function resizePtc(){pc.width=ROOT.offsetWidth;pc.height=ROOT.offsetHeight}
resizePtc();
const PTS=[];
for(let i=0;i<55;i++)PTS.push({x:Math.random()*pc.width,y:Math.random()*pc.height,vx:(Math.random()-.5)*.35,vy:(Math.random()-.5)*.35,r:Math.random()*1.8+.8,a:Math.random()*.6+.2});
function particles(){
  px.clearRect(0,0,pc.width,pc.height);
  PTS.forEach(p=>{
    p.x+=p.vx;p.y+=p.vy;
    if(p.x<0||p.x>pc.width)p.vx*=-1;
    if(p.y<0||p.y>pc.height)p.vy*=-1;
    px.beginPath();px.arc(p.x,p.y,p.r,0,Math.PI*2);
    px.fillStyle=`rgba(0,255,136,${p.a*.3})`;px.fill();
  });
  for(let i=0;i<PTS.length;i++){
    for(let j=i+1;j<PTS.length;j++){
      const d=Math.hypot(PTS[i].x-PTS[j].x,PTS[i].y-PTS[j].y);
      if(d<90){
        px.beginPath();px.moveTo(PTS[i].x,PTS[i].y);px.lineTo(PTS[j].x,PTS[j].y);
        px.strokeStyle=`rgba(0,255,136,${(1-d/90)*.12})`;
        px.lineWidth=.5;px.stroke();
      }
    }
  }
}
setInterval(particles,33);

// ── RING AVATAR ──
const rc=document.getElementById('ringc');
const rx2=rc.getContext('2d');
let ra=0;
function drawRing(){
  rx2.clearRect(0,0,100,100);
  const cx=50,cy=50;
  const segs=[{a:.6,c:'#00ff88'},{a:.25,c:'#00d4ff'},{a:.15,c:'#ff3860'}];
  let s=ra;
  segs.forEach(sg=>{
    rx2.beginPath();rx2.arc(cx,cy,42,s,s+sg.a*Math.PI*2);
    rx2.strokeStyle=sg.c;rx2.lineWidth=3;
    rx2.shadowColor=sg.c;rx2.shadowBlur=10;
    rx2.stroke();rx2.shadowBlur=0;
    s+=sg.a*Math.PI*2;
  });
  [[.6,'#00ff88'],[.85,'#00d4ff'],[.97,'#ff3860']].forEach(([pos,c])=>{
    const a=ra+pos*Math.PI*2;
    rx2.beginPath();rx2.arc(cx+Math.cos(a)*42,cy+Math.sin(a)*42,3.5,0,Math.PI*2);
    rx2.fillStyle=c;rx2.shadowColor=c;rx2.shadowBlur=12;
    rx2.fill();rx2.shadowBlur=0;
  });
  rx2.beginPath();rx2.arc(cx,cy,35,0,Math.PI*2);
  rx2.strokeStyle='#00ff8818';rx2.lineWidth=1;rx2.stroke();
  ra+=.007;
  requestAnimationFrame(drawRing);
}
drawRing();

// ── SKILL CONSTELLATION (fixed — smooth & slow) ──
const sc=document.getElementById('skillc');
const sx=sc.getContext('2d');
const SW=sc.parentElement.offsetWidth||340;
const SH=200;
sc.width=SW;sc.height=SH;
const SKILLS=[
  {name:'Python',  cx:.18,cy:.5,  r:30,c:'#00d4ff',phase:0,   speed:.0006},
  {name:'C++',     cx:.38,cy:.28, r:26,c:'#00ff88',phase:1.2, speed:.0008},
  {name:'React',   cx:.6, cy:.6,  r:24,c:'#61dafb',phase:2.4, speed:.0007},
  {name:'ML / TF', cx:.78,cy:.28, r:22,c:'#ff3860',phase:3.6, speed:.0005},
  {name:'Linux',   cx:.4, cy:.75, r:23,c:'#ffd700',phase:0.8, speed:.0009},
  {name:'Docker',  cx:.88,cy:.65, r:20,c:'#00d4ff',phase:2.0, speed:.0006},
  {name:'Node.js', cx:.62,cy:.18, r:19,c:'#68a063',phase:1.5, speed:.0007},
];
let skT=0;
function drawSkills(){
  sx.clearRect(0,0,SW,SH);
  // compute current positions
  const pos=SKILLS.map(s=>{
    const ox=Math.cos(skT*s.speed*1000+s.phase)*8;
    const oy=Math.sin(skT*s.speed*700+s.phase+1)*6;
    return {x:s.cx*SW+ox, y:s.cy*SH+oy, r:s.r, c:s.c, name:s.name};
  });
  // connections
  for(let i=0;i<pos.length;i++){
    for(let j=i+1;j<pos.length;j++){
      const d=Math.hypot(pos[i].x-pos[j].x,pos[i].y-pos[j].y);
      if(d<140){
        sx.beginPath();sx.moveTo(pos[i].x,pos[i].y);sx.lineTo(pos[j].x,pos[j].y);
        sx.strokeStyle=`rgba(0,255,136,${(1-d/140)*.25})`;
        sx.lineWidth=.6;sx.stroke();
      }
    }
  }
  // nodes
  pos.forEach(p=>{
    sx.beginPath();sx.arc(p.x,p.y,p.r,0,Math.PI*2);
    sx.fillStyle=p.c+'15';sx.fill();
    sx.strokeStyle=p.c;sx.lineWidth=1.5;
    sx.shadowColor=p.c;sx.shadowBlur=12;
    sx.stroke();sx.shadowBlur=0;
    sx.fillStyle=p.c;
    sx.font='bold 10px Rajdhani,sans-serif';
    sx.textAlign='center';sx.textBaseline='middle';
    sx.fillText(p.name,p.x,p.y);
  });
  skT+=16;// increment by ~1 frame at 60fps
  requestAnimationFrame(drawSkills);
}
drawSkills();

// ── HEATMAP ──
const hmap=document.getElementById('hmap');
const lvls=[0,0,1,0,1,2,1,0,0,2,3,2,1,0,1,2,3,4,2,1,0,0,1,3,4,4,3,2,1,2,3,4,3,2,1,0,1,2,3,2,1,2,3,4,4,3,2,1,0,1,0,1];
for(let w=0;w<52;w++){
  const week=document.createElement('div');week.className='hw';
  for(let d=0;d<7;d++){
    const day=document.createElement('div');
    const base=lvls[w]||0;
    const lvl=Math.random()>.35?Math.min(4,Math.floor(Math.random()*(base+2))):0;
    day.className='hd h'+lvl;
    week.appendChild(day);
  }
  hmap.appendChild(week);
}

// ── COUNTER ANIMATIONS ──
function animCount(el,target,dur=1200){
  let v=0,start=null;
  function step(ts){
    if(!start)start=ts;
    const p=Math.min((ts-start)/dur,1);
    v=Math.floor(p*target);
    el.textContent=v;
    if(p<1)requestAnimationFrame(step);
    else el.textContent=target;
  }
  requestAnimationFrame(step);
}
setTimeout(()=>{
  animCount(document.getElementById('c-num'),642);
  animCount(document.getElementById('streak-num'),642);
},500);

// ── TERMINAL TYPER ──
const CMDS=['cat README.md','git log --oneline -10','python3 secure_sense.py --train','sudo pacman -Syu','gcc -O3 main.cpp -o main && ./main','docker build -t secure-sense:latest .','vim ~/.config/nvim/init.lua','nmap -sV localhost -p 22,80,443','chmod +x deploy.sh && ./deploy.sh','ssh root@192.168.1.1','htop | grep python3','./run_tests.sh && echo "all clear"'];
let ci=0;
const tel=document.getElementById('tcmd');
function typeCmd(){
  const cmd=CMDS[ci%CMDS.length];
  let i=0;tel.textContent='';
  const iv=setInterval(()=>{
    tel.textContent=cmd.slice(0,++i);
    if(i>=cmd.length){clearInterval(iv);setTimeout(()=>{ci++;typeCmd();},1600+Math.random()*800);}
  },55+Math.random()*15);
}
typeCmd();

// ── LIVE FEED ──
const FEED_DATA=[
  ['fok','SCAN  ','Port scan on localhost — clean'],
  ['fok','TRAIN ','Epoch 49/100 · val_acc: 0.9541'],
  ['fwarn','WARN  ','RAM at 87% · close Firefox bro'],
  ['fok','PUSH  ','Branch feature/ml merged to main'],
  ['ferr','BLOCK ','Brute-force blocked · IP #443 banned'],
  ['fok','BUILD ','Docker image pushed to registry'],
  ['fok','TEST  ','All 23 tests passed in 1.42s'],
  ['fwarn','UPDATE','Kernel 6.12 available · pacman -Syu'],
  ['fok','COMMIT','3 files · +84 -21 lines changed'],
  ['fok','MODEL ','Training complete · saving weights'],
];
let fi=0;
const feedEl=document.getElementById('feed');
setInterval(()=>{
  const [cls,lbl,msg]=FEED_DATA[fi%FEED_DATA.length];
  const now=new Date();
  const line=document.createElement('div');line.className='fl';
  line.innerHTML=`<span class="ftime">[${String(now.getHours()).padStart(2,'0')}:${String(now.getMinutes()).padStart(2,'0')}]</span><span class="${cls}">${lbl}</span><span>${msg}</span>`;
  feedEl.insertBefore(line,feedEl.firstChild);
  while(feedEl.children.length>10)feedEl.removeChild(feedEl.lastChild);
  fi++;
},2800);
</script>
</body>
</html>

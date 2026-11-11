# Hank-marker.github.io[index.html](https://github.com/user-attachments/files/34690842/index.html)
<!doctype html>
<html lang="zh-CN">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="theme-color" content="#0b0f24">
<meta name="description" content="夜晚留给你的一小片天。">
<title>夜色里，留一盏灯给你</title>
<style>
  :root{
    --night-1:#070a17;
    --night-2:#131a3d;
    --night-3:#2a2350;
    --night-4:#4c3163;
    --night-5:#7a4a63;
    --glow:#ffd9a3;
    --glow-soft:#ffe9c9;
    --light:#f7f1e6;
    --muted:rgba(247,241,230,.60);
    --muted-2:rgba(247,241,230,.40);
    --line:rgba(255,241,214,.14);
    --line-strong:rgba(255,241,214,.24);
    --card:rgba(255,241,214,.045);
    --ok:#bfe3c9;
    --warn:#f0c9a8;
    --bad:#e8a9a9;
    --serif:"Songti SC","Source Han Serif SC","Noto Serif CJK SC","STSong","SimSun","宋体",serif;
    --sans:"PingFang SC","HarmonyOS Sans SC","MiSans","Microsoft YaHei","微软雅黑",system-ui,-apple-system,"Segoe UI",sans-serif;
    --ease:cubic-bezier(.22,.61,.36,1);
    --ease-soft:cubic-bezier(.4,.0,.2,1);
    --r-lg:24px;
    --r-md:18px;
    --r-sm:12px;
    --pad:clamp(18px,5vw,32px);
  }

  *,*::before,*::after{box-sizing:border-box}
  html,body{margin:0;padding:0}
  html{-webkit-text-size-adjust:100%;scroll-behavior:smooth}
  body{
    min-height:100vh;
    min-height:100svh;
    background:var(--night-1);
    color:var(--light);
    font-family:var(--sans);
    font-size:16px;
    line-height:1.75;
    letter-spacing:.02em;
    overflow-x:hidden;
    -webkit-font-smoothing:antialiased;
    text-rendering:optimizeLegibility;
  }
  button{font:inherit;color:inherit;background:none;border:none;margin:0;padding:0;cursor:pointer;-webkit-tap-highlight-color:transparent}
  textarea,input{font:inherit;color:inherit}
  ::selection{background:rgba(255,217,163,.28)}
  :focus{outline:none}
  :focus-visible{outline:1px solid rgba(255,217,163,.75);outline-offset:3px;border-radius:8px}

  .skip{
    position:absolute;left:12px;top:-60px;z-index:200;
    padding:10px 16px;border-radius:10px;background:var(--glow);color:#241426;
    transition:top .2s var(--ease);
  }
  .skip:focus{top:12px}

  /* ---------- sky layers ---------- */
  .sky{
    position:fixed;inset:0;z-index:0;pointer-events:none;
    background:
      radial-gradient(120% 85% at 78% 12%, rgba(255,190,140,.14) 0%, rgba(255,170,150,.055) 32%, rgba(0,0,0,0) 62%),
      radial-gradient(90% 60% at 18% 88%, rgba(120,110,200,.14) 0%, rgba(0,0,0,0) 60%),
      linear-gradient(180deg, var(--night-1) 0%, var(--night-2) 34%, var(--night-3) 58%, var(--night-4) 82%, #5a3a58 100%);
  }
  .sky::after{
    content:"";position:absolute;inset:0;
    background:
      radial-gradient(70% 45% at 50% 104%, rgba(255,205,165,.20) 0%, rgba(255,180,150,.07) 40%, rgba(0,0,0,0) 70%);
    mix-blend-mode:screen;
  }
  .grain{
    position:fixed;inset:0;z-index:3;pointer-events:none;opacity:.05;
    background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='160' height='160'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.85' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='160' height='160' filter='url(%23n)' opacity='.55'/%3E%3C/svg%3E");
    mix-blend-mode:overlay;
  }
  #stars{position:fixed;inset:0;z-index:1;pointer-events:none}
  .haze{
    position:fixed;left:-20%;right:-20%;bottom:-12%;height:46vh;z-index:2;pointer-events:none;
    background:radial-gradient(60% 100% at 50% 100%, rgba(255,196,160,.16) 0%, rgba(0,0,0,0) 72%);
    filter:blur(18px);
  }

  .page{
    position:relative;z-index:4;
    width:100%;max-width:620px;
    margin:0 auto;
    padding:0 var(--pad) calc(96px + env(safe-area-inset-bottom,0px));
  }

  /* ---------- topbar ---------- */
  .topbar{
    display:flex;align-items:center;justify-content:space-between;gap:12px;
    padding:calc(16px + env(safe-area-inset-top,0px)) 0 6px;
    font-size:12.5px;letter-spacing:.16em;color:var(--muted-2);
  }
  .topbar .brand{display:flex;align-items:center;gap:8px;letter-spacing:.22em}
  .topbar .dot{
    width:6px;height:6px;border-radius:50%;background:var(--glow);
    box-shadow:0 0 10px rgba(255,217,163,.9);animation:breathe 4.4s var(--ease-soft) infinite;
  }
  .topbar .tools{display:flex;align-items:center;gap:4px}
  .icon-btn{
    display:inline-flex;align-items:center;justify-content:center;gap:6px;
    min-width:40px;height:38px;padding:0 11px;border-radius:999px;
    color:var(--muted);border:1px solid transparent;
    transition:color .25s,background .25s,border-color .25s;
  }
  .icon-btn:hover,.icon-btn:focus-visible{color:var(--light);background:rgba(255,241,214,.06);border-color:var(--line)}
  .icon-btn .ico{font-size:15px;line-height:1}
  .icon-btn .lbl{font-size:11.5px;letter-spacing:.12em}

  /* ---------- hero ---------- */
  .hero{position:relative;text-align:center;padding:14px 0 6px}
  .hero .kicker{
    display:inline-flex;align-items:center;gap:10px;
    font-size:11.5px;letter-spacing:.34em;color:var(--muted-2);
    padding:6px 4px;
  }
  .hero .kicker i{display:block;width:24px;height:1px;background:linear-gradient(90deg,rgba(255,241,214,0),var(--line-strong),rgba(255,241,214,0))}
  .hero h1{
    margin:16px 0 0;
    font-family:var(--serif);
    font-weight:500;
    font-size:clamp(22px,6.5vw,32px);
    line-height:1.62;
    letter-spacing:.05em;
    color:#fff7ea;
    text-shadow:0 0 40px rgba(255,210,160,.28);
    text-wrap:balance;
  }
  .hero h1 em{font-style:normal;color:var(--glow-soft);white-space:nowrap}
  .hero .sub{
    margin:12px auto 0;max-width:23em;
    font-size:13.5px;line-height:2;color:var(--muted);letter-spacing:.06em;
  }

  /* ---------- moon ---------- */
  .moon-wrap{
    position:relative;display:flex;flex-direction:column;align-items:center;
    margin:26px auto 0;width:min(78vw,300px);aspect-ratio:1;
    user-select:none;
  }
  @media (min-width:760px){ .moon-wrap{width:320px} }
  .moon-glow{
    position:absolute;inset:-14%;border-radius:50%;
    background:radial-gradient(circle at 48% 44%, rgba(255,226,184,.34) 0%, rgba(255,196,150,.16) 30%, rgba(160,140,210,.10) 52%, rgba(0,0,0,0) 72%);
    animation:moonHalo 9s var(--ease-soft) infinite;
    pointer-events:none;
  }
  .moon{
    position:relative;width:66%;aspect-ratio:1;border-radius:50%;
    background:radial-gradient(circle, rgba(255,226,184,.16) 0%, rgba(255,196,150,.07) 52%, rgba(0,0,0,0) 71%);
    box-shadow:
      0 0 24px rgba(255,220,170,.22),
      0 0 80px rgba(255,196,150,.16);
    transition:transform .6s var(--ease), box-shadow .6s var(--ease);
    animation:moonFloat 12s var(--ease-soft) infinite;
    will-change:transform;
    touch-action:manipulation;
  }
  .moon canvas{display:block;width:100%;height:100%;border-radius:50%}
  .moon:hover{box-shadow:0 0 30px rgba(255,220,170,.30),0 0 100px rgba(255,196,150,.22)}
  .moon:active{transform:scale(.988)}
  .moon-wrap:hover .moon{transform:scale(1.018)}
  .moon-hint{
    margin-top:10px;font-size:11.5px;letter-spacing:.24em;color:var(--muted-2);
    transition:opacity .4s;
  }
  .moon-orbit{position:absolute;inset:0;border-radius:50%;pointer-events:none;animation:orbitSpin 90s linear infinite}
  .moon-orbit span{
    position:absolute;left:50%;top:50%;width:4px;height:4px;border-radius:50%;
    background:var(--glow-soft);box-shadow:0 0 8px rgba(255,217,163,.9);opacity:.5;
  }

  /* ---------- rotating whispers ---------- */
  .saying{
    position:relative;height:64px;margin:2px auto 0;max-width:26em;
    display:flex;align-items:center;justify-content:center;
  }
  .saying p{
    position:absolute;inset:0;margin:0;
    display:flex;align-items:center;justify-content:center;
    font-family:var(--serif);font-size:15px;line-height:1.9;letter-spacing:.08em;
    color:rgba(255,240,218,.82);
    opacity:0;transform:translateY(8px);
    transition:opacity 1.1s var(--ease),transform 1.1s var(--ease);
    padding:0 6px;
  }
  .saying p.on{opacity:1;transform:translateY(0)}

  /* ---------- generic section ---------- */
  section{position:relative}
  .sec-head{
    display:flex;align-items:baseline;justify-content:space-between;gap:14px;
    margin:0 2px 16px;
  }
  .sec-head h2{
    margin:0;font-family:var(--serif);font-weight:500;
    font-size:15.5px;letter-spacing:.22em;color:rgba(255,244,226,.92);
  }
  .sec-head .note{font-size:11.5px;letter-spacing:.14em;color:var(--muted-2);white-space:nowrap}
  .divider{
    height:1px;margin:52px 0 34px;border:0;
    background:linear-gradient(90deg,rgba(255,241,214,0),var(--line-strong),rgba(255,241,214,0));
  }

  /* ---------- lanterns ---------- */
  .scatter{margin-top:44px}
  .lanterns{
    display:grid;
    grid-template-columns:repeat(2,minmax(0,1fr));
    gap:14px;
  }
  @media (min-width:520px){
    .lanterns{grid-template-columns:repeat(4,minmax(0,1fr));gap:12px}
  }
  .lantern{
    position:relative;
    display:flex;flex-direction:column;align-items:center;gap:9px;
    padding:20px 10px 17px;
    border-radius:20px;
    border:1px solid var(--line);
    background:linear-gradient(180deg, rgba(255,241,214,.055), rgba(255,241,214,.018));
    overflow:hidden;
    transition:transform .45s var(--ease),border-color .45s,background .45s,box-shadow .45s;
    animation:lanternFloat var(--dur,9s) var(--ease-soft) infinite;
    animation-delay:var(--dly,0s);
  }
  .lantern::before{
    content:"";position:absolute;left:50%;top:26px;width:64px;height:64px;
    transform:translate(-50%,-50%);
    border-radius:50%;filter:blur(14px);opacity:.5;
    background:radial-gradient(circle,var(--tint) 0%,rgba(0,0,0,0) 70%);
    transition:opacity .45s,transform .45s;
  }
  .lantern:hover,.lantern:focus-visible{
    transform:translateY(-3px);
    border-color:rgba(255,217,163,.36);
    box-shadow:0 16px 44px rgba(5,6,18,.45),0 0 0 1px rgba(255,217,163,.10) inset;
  }
  .lantern:hover::before,.lantern:focus-visible::before{opacity:.9;transform:translate(-50%,-50%) scale(1.18)}
  .lantern .glyph{
    position:relative;z-index:1;
    width:44px;height:44px;border-radius:50%;
    display:grid;place-items:center;
    font-family:var(--serif);font-size:19px;
    color:#fff8ec;
    border:1px solid rgba(255,241,214,.20);
    background:radial-gradient(circle at 35% 28%, rgba(255,255,255,.16), rgba(255,241,214,.03) 70%);
    box-shadow:0 0 22px var(--tint), inset 0 0 14px rgba(255,241,214,.06);
  }
  .lantern .glyph span{transform:translateY(1px)}
  .lantern .name{position:relative;z-index:1;font-size:13.5px;letter-spacing:.14em;color:rgba(255,244,226,.90)}
  .lantern .desc{position:relative;z-index:1;font-size:11px;letter-spacing:.06em;color:var(--muted-2);margin-top:-3px}

  /* ---------- whisper / release ---------- */
  .release{margin-top:50px}
  .release .card{
    position:relative;
    border-radius:var(--r-lg);
    border:1px solid var(--line);
    background:
      radial-gradient(120% 90% at 50% 0%, rgba(255,217,163,.075) 0%, rgba(0,0,0,0) 60%),
      linear-gradient(180deg, rgba(20,20,42,.90), rgba(15,16,34,.94));
    padding:22px 20px 18px;
    box-shadow:0 24px 70px rgba(4,5,16,.38);
    overflow:hidden;
  }
  .release .lead{
    margin:0 0 14px;
    font-family:var(--serif);font-size:15px;line-height:2;letter-spacing:.06em;
    color:rgba(255,244,226,.90);
  }
  .release .lead small{display:block;margin-top:4px;font-family:var(--sans);font-size:11.5px;letter-spacing:.1em;color:var(--muted-2)}
  .field{position:relative}
  .field textarea{
    display:block;width:100%;min-height:112px;resize:none;
    padding:15px 16px 38px;
    border-radius:16px;
    border:1px solid var(--line);
    background:rgba(6,8,20,.42);
    color:var(--light);
    font-size:15px;line-height:1.9;letter-spacing:.04em;
    transition:border-color .3s,box-shadow .3s,background .3s;
  }
  .field textarea::placeholder{color:rgba(247,241,230,.34)}
  .field textarea:focus{
    border-color:rgba(255,217,163,.42);
    box-shadow:0 0 0 4px rgba(255,217,163,.07);
    background:rgba(6,8,20,.55);
  }
  .field .count{
    position:absolute;right:14px;bottom:11px;
    font-size:11px;letter-spacing:.1em;color:var(--muted-2);
    transition:color .3s;
  }
  .field .count.over{color:var(--bad)}
  .release .actions{
    display:flex;align-items:center;justify-content:space-between;gap:12px;
    margin-top:14px;flex-wrap:wrap;
  }
  .release .privacy{
    flex:1 1 190px;min-width:0;
    font-size:11px;line-height:1.8;letter-spacing:.04em;color:var(--muted-2);
  }
  .release .privacy b{color:rgba(255,233,201,.78);font-weight:500}
  .btn{
    display:inline-flex;align-items:center;justify-content:center;gap:8px;
    height:44px;padding:0 22px;border-radius:999px;
    font-size:13.5px;letter-spacing:.16em;
    border:1px solid rgba(255,217,163,.38);
    color:#251a2c;
    background:linear-gradient(180deg,#ffe4bd,#f5c893);
    box-shadow:0 10px 28px rgba(255,196,140,.20);
    transition:transform .3s var(--ease),box-shadow .3s,opacity .3s,filter .3s;
    white-space:nowrap;
  }
  .btn:hover{transform:translateY(-1px);box-shadow:0 14px 34px rgba(255,196,140,.28);filter:brightness(1.03)}
  .btn:active{transform:translateY(0) scale(.99)}
  .btn[disabled]{opacity:.55;cursor:default;transform:none;box-shadow:none}
  .btn.ghost{
    background:transparent;color:var(--muted);border-color:var(--line);
    box-shadow:none;
  }
  .btn.ghost:hover{color:var(--light);border-color:var(--line-strong)}
  .btn.small{height:38px;padding:0 16px;font-size:12px;letter-spacing:.12em}

  /* dissolve particles */
  .particles{position:absolute;inset:0;pointer-events:none;z-index:5;overflow:visible}
  .particle{
    position:absolute;display:inline-block;white-space:pre;
    font-family:var(--sans);font-size:15px;line-height:1;
    color:rgba(255,233,201,.95);
    text-shadow:0 0 12px rgba(255,205,150,.85);
    pointer-events:none;
    will-change:transform,opacity;
  }

  /* ---------- memory ---------- */
  .memory{margin-top:52px}
  .memory .panel{
    border-radius:var(--r-lg);
    border:1px solid var(--line);
    background:linear-gradient(180deg, rgba(255,241,214,.035), rgba(255,241,214,.012));
    padding:20px 20px 18px;
    overflow:hidden;
    position:relative;
  }
  .memory .panel::before{
    content:"";position:absolute;right:-70px;top:-90px;width:220px;height:220px;border-radius:50%;
    background:radial-gradient(circle, rgba(255,217,163,.13), rgba(0,0,0,0) 68%);
    pointer-events:none;
  }
  .stats{
    display:grid;grid-template-columns:repeat(3,1fr);
    gap:10px;margin-bottom:16px;
  }
  .stat{padding:12px 10px;border-radius:14px;background:rgba(6,8,20,.30);border:1px solid rgba(255,241,214,.07);text-align:center}
  .stat .n{font-family:var(--serif);font-size:22px;line-height:1.2;color:#fff2dc}
  .stat .k{margin-top:3px;font-size:10.5px;letter-spacing:.16em;color:var(--muted-2)}
  .constellation{
    position:relative;height:150px;border-radius:16px;overflow:hidden;
    background:
      radial-gradient(60% 80% at 30% 30%, rgba(120,130,210,.10), rgba(0,0,0,0) 70%),
      radial-gradient(50% 60% at 78% 70%, rgba(255,190,150,.08), rgba(0,0,0,0) 70%),
      rgba(4,6,16,.34);
    border:1px solid rgba(255,241,214,.06);
  }
  .constellation .hint{
    position:absolute;inset:0;display:grid;place-items:center;
    font-size:11.5px;letter-spacing:.14em;color:rgba(247,241,230,.30);text-align:center;padding:0 24px;
  }
  .cstar{
    position:absolute;width:7px;height:7px;margin:-3.5px 0 0 -3.5px;border-radius:50%;
    background:#fff6e4;
    box-shadow:0 0 10px rgba(255,226,184,.95),0 0 22px rgba(255,196,150,.55);
    animation:cstarTwinkle 5s var(--ease-soft) infinite;
    cursor:pointer;
    transition:transform .3s;
  }
  .cstar:hover{transform:scale(1.5)}
  .memory .foot{
    display:flex;align-items:center;justify-content:space-between;gap:12px;margin-top:14px;flex-wrap:wrap;
  }
  .memory .foot p{margin:0;font-size:11.5px;line-height:1.8;letter-spacing:.05em;color:var(--muted-2);max-width:22em}

  /* ---------- bottom quiet bar ---------- */
  .bottom{
    position:fixed;left:0;right:0;bottom:0;z-index:30;
    padding:12px var(--pad) calc(12px + env(safe-area-inset-bottom,0px));
    display:flex;justify-content:center;
    background:linear-gradient(180deg, rgba(7,10,23,0), rgba(7,10,23,.72) 55%, rgba(7,10,23,.94));
    backdrop-filter:blur(6px);-webkit-backdrop-filter:blur(6px);
    transform:translateY(110%);transition:transform .6s var(--ease);
    pointer-events:none;
  }
  .bottom.show{transform:translateY(0);pointer-events:auto}
  .bottom .inner{
    width:100%;max-width:620px;display:flex;align-items:center;gap:10px;
  }
  .bottom .say{
    flex:1;min-width:0;font-size:11.5px;letter-spacing:.06em;color:var(--muted-2);
    white-space:nowrap;overflow:hidden;text-overflow:ellipsis;
  }

  /* ---------- footer ---------- */
  .foot-note{
    margin-top:56px;text-align:center;
    font-size:11px;letter-spacing:.16em;color:rgba(247,241,230,.26);line-height:2.1;
  }
  .foot-note b{display:block;font-weight:400;font-family:var(--serif);font-size:12.5px;letter-spacing:.24em;color:rgba(255,233,201,.42)}

  /* ---------- overlays: moon card / drawer / breathing / intro ---------- */
  .veil{
    position:fixed;inset:0;z-index:60;
    display:flex;align-items:center;justify-content:center;
    padding:max(20px, env(safe-area-inset-top,0px)) 14px max(20px, env(safe-area-inset-bottom,0px));
    background:rgba(4,5,14,.52);
    backdrop-filter:blur(3px);-webkit-backdrop-filter:blur(3px);
    opacity:0;pointer-events:none;
    transition:opacity .4s var(--ease);
  }
  .veil.on{opacity:1;pointer-events:auto}
  .sheet{
    position:relative;width:100%;max-width:480px;
    border-radius:26px;
    border:1px solid var(--line);
    background:linear-gradient(180deg,#181c36 0%,#12152b 100%);
    box-shadow:0 30px 90px rgba(0,0,0,.55);
    padding:12px 22px 22px;
    transform:translateY(18px) scale(.985);
    transition:transform .5s var(--ease);
    max-height:min(84vh,720px);overflow-y:auto;
    overscroll-behavior:contain;
  }
  .veil.on .sheet{transform:translateY(0)}
  .sheet .grab{width:38px;height:4px;border-radius:2px;background:rgba(255,241,214,.18);margin:2px auto 18px}
  .sheet .kick{font-size:11px;letter-spacing:.26em;color:var(--muted-2);text-align:center}
  .sheet h3{
    margin:8px 0 0;text-align:center;
    font-family:var(--serif);font-weight:500;font-size:19px;letter-spacing:.12em;color:#fff4e4;
  }
  .sheet .body{
    margin:14px 0 0;font-family:var(--serif);
    font-size:15.5px;line-height:2.15;letter-spacing:.05em;
    color:rgba(250,242,228,.90);text-align:center;
    white-space:pre-line;
  }
  .sheet .tip{
    margin:14px auto 0;max-width:24em;text-align:center;
    font-size:11.5px;line-height:1.9;letter-spacing:.08em;color:var(--muted-2);
  }
  .sheet .row{display:flex;gap:10px;margin-top:20px}
  .sheet .row .btn{flex:1;height:46px}
  .sheet .row .btn.ghost{flex:0 0 auto;padding:0 18px}
  .breath-dots{display:flex;justify-content:center;gap:8px;margin-top:18px}
  .breath-dots i{width:5px;height:5px;border-radius:50%;background:rgba(255,241,214,.18);transition:background .4s,box-shadow .4s}
  .breath-dots i.on{background:var(--glow);box-shadow:0 0 10px rgba(255,217,163,.8)}

  /* drawer */
  .veil.top{align-items:stretch;justify-content:flex-end;padding:0}
  .drawer{
    position:relative;width:min(86vw,364px);height:100%;
    background:linear-gradient(180deg,#141830,#0d1022);
    border-left:1px solid var(--line);
    box-shadow:-30px 0 90px rgba(0,0,0,.5);
    padding:calc(20px + env(safe-area-inset-top,0px)) 20px calc(24px + env(safe-area-inset-bottom,0px));
    transform:translateX(30px);opacity:0;
    transition:transform .5s var(--ease),opacity .5s;
    overflow-y:auto;
  }
  .veil.top.on .drawer{transform:translateX(0);opacity:1}
  .drawer h3{margin:0;font-family:var(--serif);font-weight:500;font-size:17px;letter-spacing:.16em;color:#fff2dc}
  .drawer .sub{margin:6px 0 22px;font-size:11.5px;line-height:1.9;letter-spacing:.06em;color:var(--muted-2)}
  .drawer .group{margin:0 0 22px}
  .drawer label{display:block;font-size:11px;letter-spacing:.18em;color:var(--muted-2);margin:0 0 8px}
  .drawer .input{
    width:100%;height:44px;padding:0 14px;border-radius:12px;
    border:1px solid var(--line);background:rgba(6,8,20,.45);
    font-size:14px;letter-spacing:.04em;color:var(--light);
    transition:border-color .3s,box-shadow .3s;
  }
  .drawer .input:focus{border-color:rgba(255,217,163,.40);box-shadow:0 0 0 4px rgba(255,217,163,.06)}
  .drawer .hint{font-size:11px;line-height:1.8;color:var(--muted-2);margin:7px 0 0;letter-spacing:.03em}
  .rowline{display:flex;align-items:center;justify-content:space-between;gap:12px;padding:11px 0;border-bottom:1px solid rgba(255,241,214,.06)}
  .rowline .t{font-size:13px;letter-spacing:.06em;color:rgba(255,244,226,.88)}
  .rowline .d{font-size:10.5px;color:var(--muted-2);margin-top:2px;letter-spacing:.04em}
  .status-line{display:flex;flex-wrap:wrap;gap:8px;margin:8px 0 16px}
  .pill{
    display:inline-flex;align-items:center;gap:6px;
    padding:5px 11px;border-radius:999px;border:1px solid var(--line);
    font-size:10.5px;letter-spacing:.08em;color:var(--muted);
  }
  .pill i{width:5px;height:5px;border-radius:50%;background:var(--muted-2)}
  .pill.ok{color:var(--ok);border-color:rgba(191,227,201,.28)} .pill.ok i{background:var(--ok);box-shadow:0 0 8px rgba(191,227,201,.7)}
  .pill.warn{color:var(--warn);border-color:rgba(240,201,168,.26)} .pill.warn i{background:var(--warn)}
  .drawer .mini{display:flex;gap:8px;flex-wrap:wrap}
  .close-x{
    position:absolute;right:14px;top:calc(14px + env(safe-area-inset-top,0px));
    width:36px;height:36px;border-radius:50%;display:grid;place-items:center;
    color:var(--muted);font-size:16px;border:1px solid var(--line);
  }

  /* breathing stage */
  .breath-stage{
    position:fixed;inset:0;z-index:80;
    display:flex;flex-direction:column;align-items:center;justify-content:center;
    background:radial-gradient(80% 60% at 50% 42%, #2b2658 0%, #151733 46%, #080a18 100%);
    opacity:0;pointer-events:none;transition:opacity .6s var(--ease);
  }
  .breath-stage.on{opacity:1;pointer-events:auto}
  .bcircle{
    position:relative;width:min(62vw,260px);aspect-ratio:1;border-radius:50%;
    display:grid;place-items:center;
    border:1px solid rgba(255,217,163,.30);
    background:radial-gradient(circle, rgba(255,217,163,.16), rgba(255,217,163,.03) 70%);
    box-shadow:0 0 80px rgba(255,205,150,.18), inset 0 0 50px rgba(255,217,163,.08);
    transition:transform 4s var(--ease-soft),border-color .8s,box-shadow .8s;
    transform:scale(.86);
  }
  .bcircle .btext{
    font-family:var(--serif);font-size:16px;letter-spacing:.28em;color:#fff3de;
    text-align:center;line-height:2;
  }
  .bcircle .bnum{display:block;font-family:var(--sans);font-size:30px;letter-spacing:.05em;color:var(--glow-soft);margin-top:2px}
  .bcircle[data-phase="in"]{transform:scale(1.10);border-color:rgba(255,217,163,.55);box-shadow:0 0 120px rgba(255,205,150,.26), inset 0 0 70px rgba(255,217,163,.12)}
  .bcircle[data-phase="out"]{transform:scale(.80);border-color:rgba(186,190,255,.34)}
  .breath-stage .quit{
    position:absolute;bottom:calc(42px + env(safe-area-inset-bottom,0px));
    font-size:11.5px;letter-spacing:.22em;color:var(--muted-2);
    padding:10px 18px;border-radius:999px;border:1px solid var(--line);
  }
  .breath-stage .btop{position:absolute;top:calc(30px + env(safe-area-inset-top,0px));font-size:11px;letter-spacing:.3em;color:var(--muted-2)}

  /* intro */
  .intro{
    position:fixed;inset:0;z-index:90;
    display:flex;align-items:center;justify-content:center;
    padding:24px;
    background:radial-gradient(90% 70% at 50% 30%, #1a1f42, #070a17 80%);
    transition:opacity .9s var(--ease),visibility .9s;
  }
  .intro.gone{opacity:0;visibility:hidden;pointer-events:none}
  .intro .inner{width:100%;max-width:420px;text-align:center}
  .intro .mini-moon{
    width:64px;height:64px;border-radius:50%;margin:0 auto 26px;
    background:#f2e4cd;
    box-shadow:0 0 40px rgba(255,220,170,.55),0 0 90px rgba(255,196,150,.28);
    animation:moonFloat 9s var(--ease-soft) infinite;
  }
  .intro p{font-size:13px;line-height:2.1;letter-spacing:.08em;color:rgba(247,241,230,.62);margin:0}
  .intro h2{
    margin:16px 0 14px;font-family:var(--serif);font-weight:500;
    font-size:clamp(22px,6.4vw,28px);letter-spacing:.12em;color:#fff4e4;line-height:1.7;
  }
  .intro .fine{margin-top:20px;font-size:10.5px;letter-spacing:.1em;color:rgba(247,241,230,.32);line-height:1.9}
  .intro .btn{margin-top:30px}

  /* toast */
  .toast-wrap{
    position:fixed;left:0;right:0;bottom:calc(88px + env(safe-area-inset-bottom,0px));z-index:100;
    display:flex;flex-direction:column;align-items:center;gap:8px;pointer-events:none;padding:0 20px;
  }
  .toast{
    max-width:min(92vw,420px);
    padding:11px 18px;border-radius:14px;
    background:rgba(20,22,40,.94);
    border:1px solid rgba(255,217,163,.20);
    box-shadow:0 18px 50px rgba(0,0,0,.5);
    font-size:12.5px;line-height:1.7;letter-spacing:.06em;color:rgba(255,244,226,.92);
    opacity:0;transform:translateY(10px);
    transition:opacity .4s var(--ease),transform .4s var(--ease);
  }
  .toast.on{opacity:1;transform:translateY(0)}

  .sr{position:absolute;width:1px;height:1px;padding:0;margin:-1px;overflow:hidden;clip:rect(0 0 0 0);white-space:nowrap;border:0}

  @keyframes breathe{0%,100%{opacity:.55;transform:scale(.9)}50%{opacity:1;transform:scale(1.1)}}
  @keyframes moonFloat{0%,100%{transform:translateY(0)}50%{transform:translateY(-8px)}}
  @keyframes moonHalo{0%,100%{opacity:.82;transform:scale(1)}50%{opacity:1;transform:scale(1.05)}}
  @keyframes orbitSpin{to{transform:rotate(360deg)}}
  @keyframes lanternFloat{0%,100%{transform:translateY(0)}50%{transform:translateY(-5px)}}
  @keyframes cstarTwinkle{0%,100%{opacity:.55}50%{opacity:1}}

  @media (max-width:380px){
    .lanterns{grid-template-columns:repeat(2,minmax(0,1fr));gap:11px}
    .lantern{padding:17px 8px 14px}
    .hero h1{font-size:26px}
  }

  @media (prefers-reduced-motion:reduce){
    *,*::before,*::after{
      animation-duration:.001ms !important;
      animation-iteration-count:1 !important;
      transition-duration:.15s !important;
      scroll-behavior:auto !important;
    }
    .lane .moon,.moon-glow,.lantern,.moon-orbit{animation:none !important}
    #stars{display:none !important}
  }

  /* print-safe fallback (if someone saves the page) */
  @media print{body{background:#fff;color:#222}.sky,.grain,#stars,.haze,.bottom,.veil,.intro,.breath-stage{display:none !important}}
</style>
</head>
<body>
<a class="skip" href="#scatterHead">跳到可以为她做点什么</a>

<div class="sky" aria-hidden="true"></div>
<canvas id="stars" aria-hidden="true"></canvas>
<div class="haze" aria-hidden="true"></div>
<div class="grain" aria-hidden="true"></div>

<div class="page">
  <header class="topbar">
    <div class="brand"><span class="dot" aria-hidden="true"></span><span id="dayLabel">今夜</span></div>
    <div class="tools">
      <button class="icon-btn" id="soundBtn" type="button" aria-pressed="false" title="环境声音">
        <span class="ico" id="soundIco" aria-hidden="true">♪</span><span class="lbl" id="soundLbl">声音</span>
      </button>
      <button class="icon-btn" id="settingsBtn" type="button" title="设置" aria-label="打开设置">
        <span class="ico" aria-hidden="true">✦</span>
      </button>
    </div>
  </header>

  <main id="main">
    <section class="hero" aria-label="开场">
      <div class="kicker"><i></i><span id="timeWord">夜 色 初 临</span><i></i></div>
      <h1 id="greeting">小煜，<em>你回来了</em></h1>      <p class="sub" id="subGreeting">这盏灯一直留给你。今天不管过得怎样，先在这里坐一会儿吧。</p>

      <div class="moon-wrap">
        <div class="moon-orbit" aria-hidden="true">
          <span style="transform:translate(-50%,-50%) rotate(0deg) translateY(-118px)"></span>
          <span style="transform:translate(-50%,-50%) rotate(128deg) translateY(-104px)"></span>
          <span style="transform:translate(-50%,-50%) rotate(224deg) translateY(-126px)"></span>
        </div>
        <div class="moon-glow" aria-hidden="true"></div>
        <button class="moon" id="moon" type="button" aria-label="碰一碰月亮，它会说点什么">
          <canvas id="moonCanvas" aria-hidden="true"></canvas>
        </button>
        <div class="moon-hint" id="moonHint">轻 轻 碰 一 下 月 亮</div>
      </div>

      <div class="saying" aria-live="polite">
        <p id="sayingA"></p>
        <p id="sayingB"></p>
      </div>
    </section>

    <section class="scatter" id="scatter" aria-labelledby="scatterHead">
      <div class="sec-head">
        <h2 id="scatterHead">哪一盏，像你今晚的心情</h2>
        <span class="note">点 一 下</span>
      </div>
      <div class="lanterns" id="lanterns"></div>
    </section>

    <section class="release" aria-labelledby="releaseHead">
      <div class="sec-head">
        <h2 id="releaseHead">把它放下</h2>
        <span class="note">写 一 句 就 好</span>
      </div>
      <div class="card">
        <p class="lead">
          有句话一直压在心里，对不对。<br>写下来，交给我。
          <small>写完它就会被轻轻接住，然后散成光点，飘走。</small>
        </p>
        <div class="field">
          <textarea id="whisperInput" rows="3" maxlength="420"
            placeholder="比如：我怕自己做不好，怕让大家失望……"></textarea>
          <span class="count" id="whisperCount">0 / 420</span>
        </div>
        <div class="actions">
          <p class="privacy">
            这些话会<b>好好收着</b>，也会<b>送到在意你的人那里</b>。<br>
            你可以只写一句，也可以什么都不写，只是坐一会儿。
          </p>
          <button class="btn" id="releaseBtn" type="button">放下它 <span aria-hidden="true">✦</span></button>
        </div>
      </div>
    </section>

    <section class="memory" aria-labelledby="memoryHead">
      <div class="sec-head">
        <h2 id="memoryHead">你的小星星</h2>
        <span class="note" id="memoryNote">会 一 直 亮 着</span>
      </div>
      <div class="panel">
        <div class="stats">
          <div class="stat"><div class="n" id="statDays">1</div><div class="k">来 过 的 夜</div></div>
          <div class="stat"><div class="n" id="statLights">0</div><div class="k">放 下 的 话</div></div>
          <div class="stat"><div class="n" id="statBreath">0</div><div class="k">慢 慢 呼 吸</div></div>
        </div>
        <div class="constellation" id="constellation">
          <div class="hint" id="constellationHint">你放下的每一句话，都会在这里变成一颗小星星。</div>
        </div>
        <div class="foot">
          <p id="memoryFoot">这里没有要完成的功课，来或不来，都是好的。</p>
          <button class="btn ghost small" id="openMemoryBtn" type="button">看看我放下的</button>
        </div>
      </div>
    </section>

    <p class="foot-note">
      <b>夜 里 有 灯</b>
      这一页不催你，也不考你。<br>什么时候回来都可以。
    </p>
  </main>
</div>

<div class="bottom" id="bottomBar" aria-hidden="true">
  <div class="inner">
    <span class="say" id="bottomSay">累了就靠着，我在这儿。</span>
    <button class="btn small" id="bottomBtn" type="button">说一句</button>
  </div>
</div>

<!-- moon card -->
<div class="veil" id="moonVeil">
  <div class="sheet" role="dialog" aria-modal="true" aria-labelledby="moonTitle">
    <div class="grab" aria-hidden="true"></div>
    <div class="kick" id="moonKick">月 亮 说</div>
    <h3 id="moonTitle">给你一件小事</h3>
    <p class="body" id="moonBody"></p>
    <p class="tip" id="moonTip"></p>
    <div class="row">
      <button class="btn" id="moonDo" type="button">好，我试试</button>
      <button class="btn ghost" id="moonClose" type="button">先不要</button>
    </div>
  </div>
</div>

<!-- drawer -->
<div class="veil top" id="drawerVeil">
  <aside class="drawer" role="dialog" aria-modal="true" aria-labelledby="drawerTitle">
    <button class="close-x" id="drawerClose" type="button" aria-label="关闭设置">✕</button>
    <h3 id="drawerTitle">这里的一点设置</h3>
    <p class="sub">只有你和她知道的小地方。想改，随时可以改。</p>

    <div class="group">
      <label for="nickInput">她喜欢被叫</label>
      <input class="input" id="nickInput" type="text" maxlength="12" placeholder="小煜" autocomplete="off">
      <p class="hint">网站里会用它轻轻叫她。</p>
    </div>

    <div class="group">
      <label for="mailInput">悄悄话寄到这里</label>
      <input class="input" id="mailInput" type="email" inputmode="email" placeholder="you@example.com" autocomplete="off" spellcheck="false">
      <p class="hint">她写下的每一句，会悄悄寄到这个邮箱。第一次寄出后，请去邮箱点一下 Activate Form 链接，之后就都通了。</p>
    </div>

    <div class="group">
      <label>送信的情况</label>
      <div class="status-line" id="statusLine"></div>
      <div class="mini">
        <button class="btn ghost small" id="testMailBtn" type="button">寄一封测试</button>
        <button class="btn ghost small" id="retryBtn" type="button">重试没寄出的</button>
      </div>
    </div>

    <div class="group">
      <label>她的东西</label>
      <div class="rowline">
        <div><div class="t">导出她写下的话</div><div class="d">存成一份文本，留个底</div></div>
        <button class="btn ghost small" id="exportBtn" type="button">导出</button>
      </div>
      <div class="rowline">
        <div><div class="t">声音</div><div class="d">海浪、夜雨，很轻</div></div>
        <button class="btn ghost small" id="soundBtn2" type="button">关着</button>
      </div>
      <div class="rowline" style="border-bottom:0">
        <div><div class="t">清空她在这里的痕迹</div><div class="d">会把她写下的都删掉，不可恢复</div></div>
        <button class="btn ghost small" id="resetBtn" type="button">清空</button>
      </div>
    </div>

    <p class="hint" style="margin-top:22px">这个页面保存在打开它的设备里。换设备或清空浏览器数据后，痕迹不会跟过去。</p>
  </aside>
</div>

<!-- breathing -->
<div class="breath-stage" id="breathStage" role="dialog" aria-modal="true" aria-label="跟着呼吸">
  <div class="btop">跟 着 它，慢 一 点</div>
  <div class="bcircle" id="bcircle" data-phase="idle">
    <div class="btext"><span id="bPhase">准备好</span><span class="bnum" id="bNum">3</span></div>
  </div>
  <div class="breath-dots" id="breathDots"><i></i><i></i><i></i><i></i></div>
  <button class="quit" id="bQuit" type="button">先停下</button>
</div>

<!-- intro -->
<div class="intro" id="intro">
  <div class="inner">
    <div class="mini-moon" aria-hidden="true"></div>
    <p>写给 小煜 的一小片天</p>
    <h2>今晚，这里只属于你</h2>
    <p>不用坚强，不用想通，也不用马上好起来。<br>你可以什么都不做，就坐在这里。</p>
    <button class="btn" id="enterBtn" type="button">进去坐一会儿</button>
    <p class="fine">这里没有广告，没有别人，也没有要你完成的事。<br>她写下的心里话会被好好收着，也会送到在意她的人那里。</p>
  </div>
</div>

<div class="toast-wrap" id="toastWrap" aria-live="polite" aria-atomic="false"></div>

<noscript>
  <div style="position:fixed;inset:0;z-index:999;background:#0b0f24;color:#f7f1e6;display:grid;place-items:center;padding:30px;text-align:center;font-size:14px;line-height:2">
    这一页需要一点脚本才能亮起来。<br>请在浏览器里允许脚本后再打开它。
  </div>
</noscript>

<script>
(function () {
  'use strict';

  /* =========================================================================
     0. 基础工具
     ========================================================================= */
  var $ = function (s, r) { return (r || document).querySelector(s); };
  var $$ = function (s, r) { return Array.prototype.slice.call((r || document).querySelectorAll(s)); };
  var reduceMotion = window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  var isTouch = window.matchMedia && window.matchMedia('(hover: none)').matches;

  var STORE_KEY = 'nightlamp.v1';
  var memStore = {};
  var storageWarned = false;

  function safeGet(key) {
    try {
      var v = window.localStorage.getItem(key);
      return v === null && Object.prototype.hasOwnProperty.call(memStore, key) ? memStore[key] : v;
    } catch (e) {
      return Object.prototype.hasOwnProperty.call(memStore, key) ? memStore[key] : null;
    }
  }
  function safeSet(key, val) {
    memStore[key] = val;
    try { window.localStorage.setItem(key, val); return true; } catch (e) { return false; }
  }

  function hash(str) {
    var h = 2166136261 >>> 0;
    for (var i = 0; i < str.length; i++) {
      h ^= str.charCodeAt(i);
      h = Math.imul(h, 16777619) >>> 0;
    }
    return h >>> 0;
  }
  function seeded(seed) {
    var s = seed >>> 0 || 1;
    return function () {
      s ^= s << 13; s >>>= 0;
      s ^= s >>> 17;
      s ^= s << 5; s >>>= 0;
      return s / 4294967296;
    };
  }
  function pick(arr, seedStr) {
    if (!arr || !arr.length) return '';
    var rnd = seeded(hash(String(seedStr || '')) + Date.now() % 100000);
    return arr[Math.floor(rnd() * arr.length) % arr.length];
  }
  function todayKey(d) {
    d = d || new Date();
    var y = d.getFullYear();
    var m = String(d.getMonth() + 1).padStart(2, '0');
    var dd = String(d.getDate()).padStart(2, '0');
    return y + '-' + m + '-' + dd;
  }
  function daysBetween(a, b) {
    var d1 = new Date(a + 'T00:00:00');
    var d2 = new Date(b + 'T00:00:00');
    return Math.round((d2 - d1) / 86400000);
  }
  function uid() {
    return 'w' + Date.now().toString(36) + Math.random().toString(36).slice(2, 7);
  }
  function fmtTime(ts) {
    var d = new Date(ts);
    var h = d.getHours();
    var m = String(d.getMinutes()).padStart(2, '0');
    return (h < 10 ? '0' + h : h) + ':' + m;
  }
  function fmtDate(ts) {
    var d = new Date(ts);
    return (d.getMonth() + 1) + '月' + d.getDate() + '日 ' + fmtTime(ts);
  }
  function clamp(n, a, b) { return Math.max(a, Math.min(b, n)); }
  function escapeHTML(s) {
    return String(s).replace(/[&<>"']/g, function (c) {
      return { '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#39;' }[c];
    });
  }

  /* =========================================================================
     1. 内容：所有温柔的句子都在这里
     ========================================================================= */

  // 1.1 心情灯 + 回应
  var MOODS = [
    {
      key: 'tired', glyph: '累', name: '很累', desc: '撑了很久',
      tint: 'rgba(255,196,150,.55)',
      lines: [
        '你不是懒，也不是不够好。你只是撑得太久了。',
        '今天已经很努力了。现在，允许自己什么都不做。',
        '累的时候，不需要一个理由才配休息。',
        '把肩膀放下来吧。这里没人要求你挺拔。',
        '你一直在用力，连呼吸都在用力。松开一点，就一点。',
        '你不是机器，不需要一直运转。停下来，天不会塌。'
      ],
      todo: [
        '把手机放下三分钟，只呼吸。',
        '靠住椅背，让后背被接住。',
        '喝一口温水，慢慢地咽下去。',
        '闭上眼睛，把眼睛里的力气也松开。'
      ]
    },
    {
      key: 'worry', glyph: '乱', name: '心里乱', desc: '停不下来',
      tint: 'rgba(170,180,255,.50)',
      lines: [
        '脑子里那个声音转了一整天，它也很累了。让它歇一歇。',
        '你现在想到的“最坏”，多半不会发生。真的。',
        '担心，是因为你在乎。可你不需要用担心来证明在乎。',
        '有些事，不是今晚必须想明白的。',
        '你已经预演了一百遍，可生活很少按预演来。这一次，先不预演了。',
        '把“万一”放一放。今晚只过今晚。'
      ],
      todo: [
        '写下那件让你慌的事，然后合上。明天再说。',
        '数五样你现在能看见的东西。',
        '把“万一……”改成“就算……我也能……”。',
        '慢慢吐气，比吸气长一点点。'
      ]
    },
    {
      key: 'sad', glyph: '泪', name: '很难过', desc: '想哭',
      tint: 'rgba(150,170,235,.52)',
      lines: [
        '难过不用忍。眼泪是最好的出口，不是软弱。',
        '想哭就哭。我就在这儿，不催你，也不走。',
        '你不需要马上好起来。难过也是会过去的，只是它需要一点时间。',
        '今天很难。你已经做得很好了，真的。',
        '有些难过没有原因，也不需要原因。它来了，就让它待一会儿。',
        '你不是麻烦。你的难过，值得被认真接住。'
      ],
      todo: [
        '把手放在心口，感觉它还在跳。',
        '找一条毯子，把自己裹起来。',
        '允许自己哭三分钟，不评价自己。',
        '喝一点甜的、热的。'
      ]
    },
    {
      key: 'lonely', glyph: '孤', name: '很孤单', desc: '想要人陪',
      tint: 'rgba(220,180,255,.48)',
      lines: [
        '我在这里。一直在这片夜色里。',
        '你不是一个人。此刻，有个人正想着你。',
        '孤单不是你的错，也不是你不够好。',
        '今夜我替你守着这盏灯，你可以安心一点。',
        '就算全世界都安静了，这里还有一盏灯为你亮着。',
        '你不需要先变得有趣、变得有用，才值得被陪着。'
      ],
      todo: [
        '给一个你想念的人发一句“在吗”。',
        '把这盏灯调到最亮，看它一会儿。',
        '听听窗外的声音，你并不孤单。',
        '写下三个今晚陪着你的人或物。'
      ]
    },
    {
      key: 'over', glyph: '想', name: '想太多', desc: '反反复复',
      tint: 'rgba(255,170,190,.48)',
      lines: [
        '想那么多，是因为你太想做好了。可你已经够好了。',
        '一件事在你心里，已经绕了一百圈。该停了。',
        '你反复咀嚼的那些，别人可能早就忘了。别用别人的无心，罚自己一整夜。',
        '想不通的时候，就先不想。答案会在你放松的时候自己来。',
        '你不是想太多，你只是太在意。这份在意，值得被温柔对待。',
        '把那个反复出现的念头，写下来，然后对自己说：我知道了。'
      ],
      todo: [
        '把想不通的那句，只写一遍，然后停止。',
        '去洗一把脸，让水把念头冲淡。',
        '给自己设一个“想它到几点”的闹钟。',
        '做一件完全不用脑的小事，比如叠衣服。'
      ]
    },
    {
      key: 'stuck', glyph: '困', name: '觉得被困住', desc: '无路可走',
      tint: 'rgba(255,214,150,.52)',
      lines: [
        '你不是没有路，你只是暂时看不清。',
        '今天不用找到出口。先在这里歇脚。',
        '被困住的时候，停下来不是放弃，是等一等自己。',
        '你以为的墙，可能只是一层雾。',
        '有些门，是推不开的。可以先转身，看看别的方向。',
        '你不需要一下子把人生想清楚。今晚，只需要过好这一晚。'
      ],
      todo: [
        '写下“我现在最想要的一件事”。',
        '把问题拆成很小很小的一步，只做那一步。',
        '站起来走两步，换个位置坐。',
        '问问自己：如果是她最好的朋友，你会怎么说？'
      ]
    },
    {
      key: 'afraid', glyph: '怕', name: '有点害怕', desc: '心里发慌',
      tint: 'rgba(160,200,230,.48)',
      lines: [
        '怕，是因为你想保护自己。这不是弱点。',
        '现在这一刻，你是安全的。真的。',
        '心跳快，是因为身体在保护你，不是它在背叛你。',
        '你怕的事，大多没发生。你已经平安度过很多个“万一”了。',
        '害怕的时候，慢一点。慢，就是安全的信号。',
        '你不需要马上勇敢。先坐稳，就已经很好了。'
      ],
      todo: [
        '把两只脚踩实在地面上。',
        '慢慢地说出身边四个东西的颜色。',
        '把手贴在胸口，告诉自己“我在”。',
        '抱紧一个枕头或杯子。'
      ]
    },
    {
      key: 'empty', glyph: '空', name: '心里空空的', desc: '提不起劲',
      tint: 'rgba(190,190,220,.40)',
      lines: [
        '空，不是坏掉了。是心在休息。',
        '什么都不想做，也没关系。今天就这样，也是完整的一天。',
        '你不需要一直有热情。有时候，只是活着就已经很用力了。',
        '那种空空的感受，会过去的。你不用赶它。',
        '允许自己暂时没有力气。力气会慢慢回来的。',
        '今天只做一件小事：好好喝一杯水。'
      ],
      todo: [
        '换一身舒服的衣服。',
        '把窗户打开一点点，让空气进来。',
        '听一首你以前喜欢的歌。',
        '写下一件今天没有更糟的小事。'
      ]
    }
  ];

  // 1.2 月亮上的小事
  var MOON_CARDS = [
    {
      icon: '呼', title: '陪我呼吸三次',
      body: '不用想任何事。\n跟着圆圈，吸气，停一下，再慢慢呼出去。',
      tip: '只有三次。做完，就好一点了。',
      action: 'breath'
    },
    {
      icon: '写', title: '给这件事起个名字',
      body: '把此刻压着你的东西，写成一个词。\n不用解释，一个词就够。',
      tip: '写出来，它就不再那么大。',
      action: 'focusWhisper'
    },
    {
      icon: '灯', title: '把灯留给自己',
      body: '你照顾了那么多人。\n今晚，先照顾自己一次。',
      tip: '哪怕只是喝一口热水。',
      action: 'close'
    },
    {
      icon: '问', title: '一句很小的问题',
      body: '如果今晚只能实现一个小愿望，\n那会是什么？',
      tip: '不用现在回答，想一想就好。',
      action: 'close'
    },
    {
      icon: '放', title: '假今晚不用解决',
      body: '你不需要今晚就想通。\n把问题放在这儿，明天再拿。',
      tip: '今晚的任务，只是休息。',
      action: 'close'
    },
    {
      icon: '记', title: '找一件小小对的事',
      body: '今天一定有一件小事，你做对了。\n哪怕只是按时吃了饭。',
      tip: '想不起来也没关系，那也说明你今天很努力了。',
      action: 'close'
    },
    {
      icon: '近', title: '离你最近的人',
      body: '有一个人，此刻可能也在等你。\n不用说什么，发一个表情就可以。',
      tip: '被需要的感觉，会让人暖一点。',
      action: 'close'
    },
    {
      icon: '慢', title: '把速度调到很慢',
      body: '现在，把呼吸放慢一半。\n把动作放慢一半。把念头放慢一半。',
      tip: '慢下来，世界不会停。',
      action: 'close'
    }
  ];

  // 1.3 一进来的话
  var HELLO = {
    late: ['这么晚了，还没睡吗。', '夜很深了，你还在。', '这么晚，辛苦你了。'],
    night: ['小煜，你回来了。', '你来了，正好。', '今晚，也欢迎你回来。'],
    dusk: ['天黑了，灯给你留着。', '傍晚了，先坐下吧。', '这会儿，慢慢来。'],
    day: ['白天也可以，这儿一直开着。', '今天，还顺利吗。', '你来了，就好。']
  };
  var SUB = [
    '这盏灯一直留给你。今天不管过得怎样，先在这里坐一会儿吧。',
    '不用带任何东西来，坐一会儿就好。',
    '这里没有要你完成的事。你在，就够了。',
    '你已经很努力了。今晚，先把自己放在第一位。',
    '如果很累，就什么都不做。这里不会催你。'
  ];

  // 1.4 底部轻轻的句子
  var BOTTOM_LINES = [
    '累了就靠着，我在这儿。',
    '不用马上好起来，慢慢来。',
    '今晚，你只需要存在。',
    '你已经很好了，真的。',
    '有些事明天再想，今晚先睡。',
    '这里没有人会走。'
  ];

  // 1.5 漂浮的一行行小字
  var DRIFT = [
    '你不需要一直发光，偶尔暗一点也没关系。',
    '慢一点，世界不会因此停下。',
    '你值得被好好对待，包括被你自己。',
    '今晚的月亮，是留给你的。',
    '难过的时候，允许自己难过。',
    '你已经撑了很久了。',
    '有些答案，睡着之后才来。',
    '你不用一个人扛所有的事。'
  ];

  /* =========================================================================
     2. 状态
     ========================================================================= */
  var DEFAULT_MAIL = '3645702053@qq.com';

  function blankState() {
    return {
      v: 1,
      name: '小煜',
      email: DEFAULT_MAIL,
      firstSeen: null,
      days: [],
      streak: 0,
      lastDay: null,
      lanterns: {},
      breaths: 0,
      moonTaps: 0,
      whispers: [],
      queue: [],
      settings: { sound: false, soundMode: 'waves' },
      introSeen: false
    };
  }

  var state = blankState();

  function loadState() {
    var raw = safeGet(STORE_KEY);
    if (!raw) return;
    try {
      var parsed = JSON.parse(raw);
      if (!parsed || typeof parsed !== 'object') return;
      var base = blankState();
      for (var k in base) if (Object.prototype.hasOwnProperty.call(base, k)) {
        if (parsed[k] !== undefined && parsed[k] !== null) base[k] = parsed[k];
      }
      base.settings = Object.assign({ sound: false, soundMode: 'waves' }, parsed.settings || {});
      if (!Array.isArray(base.days)) base.days = [];
      if (!Array.isArray(base.whispers)) base.whispers = [];
      if (!Array.isArray(base.queue)) base.queue = [];
      if (!base.lanterns || typeof base.lanterns !== 'object') base.lanterns = {};
      if (!base.name) base.name = '小煜';
      if (!base.email) base.email = DEFAULT_MAIL;
      state = base;
    } catch (e) { /* 坏数据就当第一次来 */ }
  }

  var saveTimer = null;
  function saveState(now) {
    if (now) {
      persistNow();
      return;
    }
    clearTimeout(saveTimer);
    saveTimer = setTimeout(persistNow, 160);
  }
  function persistNow() {
    var ok = safeSet(STORE_KEY, JSON.stringify(state));
    if (!ok && !storageWarned) {
      storageWarned = true;
      if (document.body) {
        toast('浏览器没让我们把小秘密存太久。你可以随时在设置里导出她写下的话。', 6200);
      }
    }
  }

  function noteVisit() {
    var t = todayKey();
    if (state.days.indexOf(t) === -1) {
      state.days.push(t);
      if (state.days.length > 400) state.days = state.days.slice(-400);
      if (state.lastDay) {
        var gap = daysBetween(state.lastDay, t);
        state.streak = (gap === 1) ? (state.streak || 1) + 1 : 1;
      } else {
        state.streak = 1;
      }
      state.lastDay = t;
    } else {
      state.streak = state.streak || 1;
    }
    if (!state.firstSeen) state.firstSeen = Date.now();
    saveState();
  }

  /* =========================================================================
     3. 小工具：吐司、雾层、滚动锁
     ========================================================================= */
  function toast(msg, ms) {
    var wrap = $('#toastWrap');
    if (!wrap) return;
    var el = document.createElement('div');
    el.className = 'toast';
    el.textContent = msg;
    wrap.appendChild(el);
    requestAnimationFrame(function () { el.classList.add('on'); });
    setTimeout(function () {
      el.classList.remove('on');
      setTimeout(function () { if (el.parentNode) el.parentNode.removeChild(el); }, 500);
    }, ms || 3200);
  }

  function openVeil(el) {
    if (!el) return;
    el.classList.add('on');
    document.body.style.overflow = 'hidden';
  }
  function closeVeil(el) {
    if (!el) return;
    el.classList.remove('on');
    if (!$('.veil.on') && !$('#breathStage.on')) document.body.style.overflow = '';
  }

  /* =========================================================================
     4. 星空
     ========================================================================= */
  (function starfield() {
    var cv = $('#stars');
    if (!cv || !cv.getContext) return;
    var ctx = cv.getContext('2d');
    var dpr = Math.min(window.devicePixelRatio || 1, 2);
    var stars = [];
    var w = 0, h = 0;
    var raf = 0;

    function resize() {
      w = window.innerWidth;
      h = window.innerHeight;
      cv.width = Math.round(w * dpr);
      cv.height = Math.round(h * dpr);
      cv.style.width = w + 'px';
      cv.style.height = h + 'px';
      ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
      var count = clamp(Math.round(w * h / 9000), 70, 210);
      var rnd = seeded(20241111);
      stars = [];
      for (var i = 0; i < count; i++) {
        stars.push({
          x: rnd() * w,
          y: rnd() * h * 0.94,
          r: rnd() * 1.25 + 0.25,
          a: rnd() * 0.55 + 0.22,
          sp: rnd() * 0.9 + 0.35,
          ph: rnd() * Math.PI * 2,
          warm: rnd() > 0.62
        });
      }
    }

    function frame(t) {
      raf = requestAnimationFrame(frame);
      ctx.clearRect(0, 0, w, h);

      for (var i = 0; i < stars.length; i++) {
        var s = stars[i];
        var tw = Math.sin(t * 0.0009 * s.sp + s.ph);
        var alpha = s.a + tw * 0.20;
        if (alpha < 0.03) alpha = 0.03;
        ctx.beginPath();
        ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
        ctx.fillStyle = s.warm
          ? 'rgba(255,226,190,' + alpha.toFixed(3) + ')'
          : 'rgba(226,232,255,' + alpha.toFixed(3) + ')';
        ctx.fill();
      }
    }

    resize();
    window.addEventListener('resize', function () {
      clearTimeout(resize._t);
      resize._t = setTimeout(resize, 180);
    });
    if (!reduceMotion) raf = requestAnimationFrame(frame);
    else {
      // 静态星图
      frame(0); cancelAnimationFrame(raf);
    }
    document.addEventListener('visibilitychange', function () {
      if (document.hidden) { cancelAnimationFrame(raf); raf = 0; }
      else if (!reduceMotion && !raf) raf = requestAnimationFrame(frame);
    });
  })();

  /* =========================================================================
     5. 月亮（真·月相）
     ========================================================================= */
  var moonRef = null;

  function moonPhase() {
    var ref = new Date(2000, 0, 6, 18, 14, 0);
    var synodic = 29.53058867;
    var days = (Date.now() - ref.getTime()) / 86400000;
    var phase = ((days / synodic) % 1 + 1) % 1;
    return phase; // 0 新月 -> .5 满月 -> 1 新月
  }

  function paintMoon() {
    var moon = $('#moon');
    var cv = $('#moonCanvas');
    if (!moon || !cv || !cv.getContext) return;
    var p = moonPhase();
    var light = (1 - Math.cos(p * Math.PI * 2)) / 2;
    drawMoonCanvas(cv, p, cv.clientWidth);
    moon.setAttribute('aria-label', '碰一碰月亮（今晚' +
      (light > 0.9 ? '接近满月' : light < 0.1 ? '是新月' : light > 0.5 ? '月偏满' : '月亮弯弯') + '）');
    moonRef = { light: light };
    window.__drawMoon = drawMoonCanvas;
    window.__moonPhase = moonPhase;
  }

  // 把月相画进一块画布（单独抽出来，便于自测）
  function drawMoonCanvas(cv, p, cssSize) {
    var dpr = Math.min(window.devicePixelRatio || 1, 2);
    var size = Math.round(cssSize || cv.clientWidth || 180);
    cv.width = Math.round(size * dpr);
    cv.height = Math.round(size * dpr);
    var ctx = cv.getContext('2d');
    ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
    ctx.clearRect(0, 0, size, size);

    var cx = size / 2, cy = size / 2, r = size / 2 - 1;
    var ang = p * Math.PI * 2;
    var cosv = Math.cos(ang);
    var light = (1 - cosv) / 2; // 0 新月 1 满月

    // 月亮本体（受光面）
    ctx.save();
    ctx.beginPath();
    ctx.arc(cx, cy, r, 0, Math.PI * 2);
    ctx.clip();

    var body = ctx.createRadialGradient(cx - r * 0.30, cy - r * 0.34, r * 0.02, cx, cy, r * 1.0);
    body.addColorStop(0, '#fffaf0');
    body.addColorStop(0.72, '#f7ead6');
    body.addColorStop(1, '#e6d5c0');
    ctx.fillStyle = body;
    ctx.fillRect(0, 0, size, size);

    // 环形山：淡淡的凹痕，位置固定
    var craters = [
      [-0.30, -0.26, 0.13], [0.16, -0.34, 0.085], [0.32, 0.08, 0.075],
      [-0.12, 0.30, 0.10], [0.06, 0.10, 0.055], [-0.42, 0.16, 0.06],
      [0.24, 0.34, 0.05], [0.44, -0.16, 0.045]
    ];
    craters.forEach(function (c) {
      var gx = cx + c[0] * r, gy = cy + c[1] * r, gr = c[2] * r;
      var g = ctx.createRadialGradient(gx - gr * 0.3, gy - gr * 0.3, gr * 0.1, gx, gy, gr);
      g.addColorStop(0, 'rgba(150,136,140,.22)');
      g.addColorStop(0.7, 'rgba(150,136,140,.10)');
      g.addColorStop(1, 'rgba(150,136,140,0)');
      ctx.beginPath();
      ctx.arc(gx, gy, gr, 0, Math.PI * 2);
      ctx.fillStyle = g;
      ctx.fill();
    });

    // 暗面：明暗界线由圆的边缘 + 一段椭圆弧围成
    if (light < 0.995) {
      var rx = Math.max(Math.abs(cosv) * r, 0.001);
      var darkRight = cosv > 0;               // 暗面在右

      var startT = Math.PI / 2;
      var endT = Math.PI * 1.5;

      ctx.beginPath();
      if (darkRight) {
        // 暗面在右：从底部顺时针绕右侧到顶部，再用右侧椭圆弧绕回
        ctx.arc(cx, cy, r, startT, endT, true);
        ctx.ellipse(cx, cy, rx, r, 0, startT, endT, false);
      } else {
        // 暗面在左：从顶部逆时针绕左侧到底部，再用左侧椭圆弧绕回
        ctx.arc(cx, cy, r, startT, endT, false);
        ctx.ellipse(cx, cy, rx, r, 0, startT, endT, true);
      }
      ctx.closePath();

      ctx.fillStyle = 'rgba(24,21,44,.94)';
      ctx.fill();

      // 一点点地照：让暗面不至于死黑
      var earth = ctx.createRadialGradient(cx - r * 0.22, cy - r * 0.2, r * 0.1, cx, cy, r * 1.05);
      earth.addColorStop(0, 'rgba(120,126,180,.42)');
      earth.addColorStop(0.7, 'rgba(90,96,150,.22)');
      earth.addColorStop(1, 'rgba(70,74,120,.06)');
      ctx.fillStyle = earth;
      ctx.fill();
    }

    // 边缘的一点点柔光
    ctx.beginPath();
    ctx.arc(cx, cy, r - 0.5, 0, Math.PI * 2);
    ctx.strokeStyle = 'rgba(255,240,214,.20)';
    ctx.lineWidth = 1;
    ctx.stroke();
    ctx.restore();
  }

  /* =========================================================================
     6. 首屏文案
     ========================================================================= */
  function timeWord() {
    var h = new Date().getHours();
    if (h >= 5 && h < 11) return ['早 上 好', 'day'];
    if (h >= 11 && h < 17) return ['午 后 安 静', 'day'];
    if (h >= 17 && h < 20) return ['天 色 将 暗', 'dusk'];
    if (h >= 20 && h < 24) return ['夜 色 初 临', 'night'];
    return ['深 夜 了', 'late'];
  }

  function greetingText() {
    var tw = timeWord();
    var bag = HELLO[tw[1]] || HELLO.night;
    var line = pick(bag, tw[1] + state.days.length + Math.floor(Date.now() / 600000));
    var n = state.name || '小煜';
    if (line.indexOf(n) >= 0) return line;
    return n + '，' + line;
  }

  function renderHero() {
    var tw = timeWord();
    $('#timeWord').textContent = tw[0];

    var g = greetingText();
    var gi = g.indexOf('，');
    var gh = '';
    if (gi > 0 && gi < g.length - 1) {
      gh = escapeHTML(g.slice(0, gi + 1)) + '<em>' + escapeHTML(g.slice(gi + 1)) + '</em>';
    } else {
      gh = escapeHTML(g);
    }
    $('#greeting').innerHTML = gh;

    $('#subGreeting').textContent = pick(SUB, 'sub' + state.days.length + Math.floor(Date.now() / 900000));

    var days = state.days.length || 1;
    var label = '第 ' + days + ' 个夜';
    if (state.streak > 1) label += ' · 连着 ' + state.streak + ' 晚了';
    $('#dayLabel').textContent = label;

    paintMoon();
  }

  /* =========================================================================
     7. 漂浮的一行行小字
     ========================================================================= */
  var sayingTimer = null;
  function startSayings() {
    var a = $('#sayingA'), b = $('#sayingB');
    if (!a || !b) return;
    var front = a, back = b;
    var cur = -1;

    function next() {
      if (document.hidden) return;
      var i;
      do { i = Math.floor(Math.random() * DRIFT.length); } while (i === cur && DRIFT.length > 1);
      cur = i;
      back.textContent = DRIFT[i];
      back.classList.add('on');
      front.classList.remove('on');
      var t = front; front = back; back = t;
    }
    next();
    sayingTimer = setInterval(next, 7600);
  }

  /* =========================================================================
     8. 灯（心情）
     ========================================================================= */
  function renderLanterns() {
    var wrap = $('#lanterns');
    if (!wrap) return;
    wrap.innerHTML = '';
    MOODS.forEach(function (m, i) {
      var b = document.createElement('button');
      b.type = 'button';
      b.className = 'lantern';
      b.setAttribute('data-mood', m.key);
      b.setAttribute('aria-label', m.name + '，' + m.desc);
      b.style.setProperty('--tint', m.tint);
      var rnd = seeded(1000 + i * 77);
      b.style.setProperty('--dur', (8.4 + rnd() * 3.2).toFixed(2) + 's');
      b.style.setProperty('--dly', (rnd() * -6).toFixed(2) + 's');
      b.innerHTML =
        '<span class="glyph"><span>' + m.glyph + '</span></span>' +
        '<span class="name">' + m.name + '</span>' +
        '<span class="desc">' + m.desc + '</span>';
      b.addEventListener('click', function () { openMood(m); });
      wrap.appendChild(b);
    });
  }

  function openMood(m) {
    if ($('#moonVeil.on') || breath.running) return;
    state.lanterns[m.key] = (state.lanterns[m.key] || 0) + 1;
    saveState();

    var seed = m.key + state.lanterns[m.key] + Math.floor(Date.now() / 120000);
    $('#moonKick').textContent = '你 说 有 点 ' + m.name.replace('很', '') ;
    $('#moonTitle').textContent = m.name;
    $('#moonBody').textContent = pick(m.lines, seed);
    $('#moonTip').textContent = '要不要试一件很小的事：' + pick(m.todo, seed + 't');
    var doBtn = $('#moonDo');
    doBtn.dataset.mood = m.key;
    doBtn.textContent = '好，我试试';
    doBtn.onclick = function () {
      doBtn.textContent = '已记下';
      toast(pick(m.todo, seed + 'x'), 4200);
      closeVeil($('#moonVeil'));
    };
    openVeil($('#moonVeil'));
  }

  /* =========================================================================
     9. 月亮的小卡片
     ========================================================================= */
  function openMoonCard() {
    if ($('#moonVeil.on') || breath.running) return;
    state.moonTaps = (state.moonTaps || 0) + 1;
    saveState();
    var card = MOON_CARDS[(state.moonTaps - 1) % MOON_CARDS.length];
    var doBtn = $('#moonDo');
    $('#moonKick').textContent = '月 亮 说';
    $('#moonTitle').textContent = card.title;
    $('#moonBody').textContent = card.body;
    $('#moonTip').textContent = card.tip;
    doBtn.textContent = card.action === 'breath' ? '好，一起呼吸' : '好';
    doBtn.onclick = function () {
      closeVeil($('#moonVeil'));
      if (card.action === 'breath') startBreathing();
      else if (card.action === 'focusWhisper') {
        $('#whisperInput').focus();
        $('#whisperInput').scrollIntoView({ behavior: reduceMotion ? 'auto' : 'smooth', block: 'center' });
      }
    };
    openVeil($('#moonVeil'));
  }

  /* =========================================================================
     10. 呼吸
     ========================================================================= */
  var breath = { running: false, timers: [], round: 0, total: 3 };

  function startBreathing() {
    if (breath.running) return;
    breath.running = true;
    breath.round = 0;
    var stage = $('#breathStage');
    stage.classList.add('on');
    document.body.style.overflow = 'hidden';
    runRound();
  }

  function clearBreathTimers() {
    breath.timers.forEach(function (t) { clearTimeout(t); clearInterval(t); });
    breath.timers = [];
  }

  function setDots(n) {
    $$('#breathDots i').forEach(function (d, i) {
      d.classList.toggle('on', i < n);
    });
  }

  function runRound() {
    var circle = $('#bcircle');
    var phase = $('#bPhase');
    var num = $('#bNum');
    if (!circle) return;

    if (breath.round >= breath.total) {
      phase.textContent = '很好';
      num.textContent = '✦';
      circle.dataset.phase = 'idle';
      var done = setTimeout(function () {
        stopBreathing();
        toast('三次呼吸。你已经比刚才安定一点了。', 4200);
      }, 1900);
      breath.timers.push(done);
      return;
    }

    breath.round++;
    setDots(breath.round);

    var plan = [
      { k: 'in', label: '吸 气', sec: 4 },
      { k: 'hold', label: '停 一 下', sec: 2 },
      { k: 'out', label: '慢 慢 呼', sec: 6 }
    ];
    var idx = 0;

    function step() {
      if (!breath.running) return;
      if (idx >= plan.length) {
        var gap = setTimeout(runRound, 500);
        breath.timers.push(gap);
        return;
      }
      var p = plan[idx++];
      circle.dataset.phase = p.k;
      phase.textContent = p.label;
      var left = p.sec;
      num.textContent = String(left);
      var iv = setInterval(function () {
        left--;
        if (left <= 0) {
          clearInterval(iv);
          num.textContent = '·';
        } else {
          num.textContent = String(left);
        }
      }, 1000);
      breath.timers.push(iv);
      var tm = setTimeout(step, p.sec * 1000);
      breath.timers.push(tm);
    }
    step();
  }

  function stopBreathing() {
    breath.running = false;
    clearBreathTimers();
    var stage = $('#breathStage');
    if (stage) stage.classList.remove('on');
    var circle = $('#bcircle');
    if (circle) circle.dataset.phase = 'idle';
    setDots(0);
    if (!$('.veil.on')) document.body.style.overflow = '';
    state.breaths = (state.breaths || 0) + 1;
    saveState();
    renderStats();
  }

  /* =========================================================================
     11. 放下（写下 + 散成光点 + 收好 + 寄出）
     ========================================================================= */
  function countChars(el) {
    var n = (el.value || '').length;
    var c = $('#whisperCount');
    if (!c) return;
    c.textContent = n + ' / 420';
    c.classList.toggle('over', n > 400);
    var btn = $('#releaseBtn');
    if (btn) btn.disabled = false;
  }

  function releaseWhisper() {
    var input = $('#whisperInput');
    if (!input) return;
    var text = (input.value || '').trim();
    var btn = $('#releaseBtn');

    if (!text) {
      // 允许空着放下一口气
      toast(pick(['那就先什么都不写。我在这儿。', '空着也可以。你已经来了。', '不用勉强写。坐着就好。'], 'empty' + Date.now()), 3400);
      input.focus();
      return;
    }
    if (text.length > 420) {
      toast('这句有点长，先收一收，写成一句最想说的。', 3600);
      return;
    }

    // 拆字散开
    dissolveInput(input, text);

    var w = {
      id: uid(),
      ts: Date.now(),
      text: text,
      from: 'whisper'
    };
    state.whispers.push(w);
    if (state.whispers.length > 300) state.whispers = state.whispers.slice(-300);
    state.queue.push(w.id);
    saveState(true);
    attachConstellation();
    renderStats();

    input.value = '';
    countChars(input);
    if (btn) btn.disabled = true;

    setTimeout(function () {
      sendQueue();
    }, 1000);

    setTimeout(function () {
      if (btn) btn.disabled = false;
    }, 1500);
  }

  function dissolveInput(input, text) {
    if (reduceMotion) return;
    var rect = input.getBoundingClientRect();
    var card = input.closest('.card') || input.parentNode;
    var host = document.createElement('div');
    host.className = 'particles';
    host.style.position = 'absolute';
    var cardRect = card.getBoundingClientRect();
    host.style.left = '0';
    host.style.top = '0';
    host.style.width = cardRect.width + 'px';
    host.style.height = cardRect.height + 'px';
    card.style.position = 'relative';
    card.appendChild(host);

    var maxLen = Math.min(text.length, 90);
    var step = Math.max(1, Math.ceil(text.length / maxLen));
    var chars = [];
    for (var i = 0; i < text.length; i += step) chars.push(text.charAt(i));

    var ox = rect.left - cardRect.left;
    var oy = rect.top - cardRect.top;
    var perLine = Math.max(12, Math.floor((rect.width - 32) / 15));
    var lineH = 27;

    chars.forEach(function (ch, idx) {
      if (!ch.trim()) return;
      var span = document.createElement('span');
      span.className = 'particle';
      span.textContent = ch;
      var col = idx % perLine;
      var row = Math.floor(idx / perLine);
      var jx = (Math.random() - 0.5) * 8;
      var jy = (Math.random() - 0.5) * 6;
      span.style.left = (ox + 16 + col * 15 + jx) + 'px';
      span.style.top = (oy + 14 + row * lineH + jy) + 'px';
      span.style.opacity = '0';
      span.style.transform = 'translate(0,0) scale(1)';
      host.appendChild(span);

      var dx = (Math.random() - 0.5) * 160;
      var dy = -(90 + Math.random() * 190);
      var rot = (Math.random() - 0.5) * 90;
      var delay = Math.random() * 260;
      var dur = 1500 + Math.random() * 1200;

      span.style.transition =
        'transform ' + dur + 'ms cubic-bezier(.22,.61,.36,1) ' + delay + 'ms, opacity ' + dur + 'ms ease ' + delay + 'ms';
      requestAnimationFrame(function () {
        span.style.opacity = '0.95';
        requestAnimationFrame(function () {
          span.style.transform = 'translate(' + dx + 'px,' + dy + 'px) scale(.55) rotate(' + rot + 'deg)';
          span.style.opacity = '0';
        });
      });
    });

    setTimeout(function () {
      if (host.parentNode) host.parentNode.removeChild(host);
    }, 3600);
  }

  /* =========================================================================
     12. 寄出（FormSubmit → 她的邮箱）
     ========================================================================= */
  var mailSending = false;
  var endpointFor = function (mail) { return 'https://formsubmit.co/ajax/' + encodeURIComponent(mail); };

  function validMail(s) {
    return /^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/.test(String(s || '').trim());
  }

  function payloadFor(w) {
    return {
      _subject: '小煜的夜色悄悄话',
      _template: 'table',
      _captcha: 'false',
      '昵称': state.name || '小煜',
      '她想说': w.text,
      '她说的时间': fmtDate(w.ts),
      '页面': '夜色里，留一盏灯给你'
    };
  }

  function postJSON(url, data, timeoutMs) {
    return new Promise(function (resolve, reject) {
      var ctrl = (typeof AbortController !== 'undefined') ? new AbortController() : null;
      var timer = setTimeout(function () {
        if (ctrl) ctrl.abort();
        reject(new Error('timeout'));
      }, timeoutMs || 12000);
      fetch(url, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json', 'Accept': 'application/json' },
        body: JSON.stringify(data),
        signal: ctrl ? ctrl.signal : undefined
      }).then(function (r) {
        clearTimeout(timer);
        resolve(r);
      }).catch(function (e) {
        clearTimeout(timer);
        reject(e);
      });
    });
  }

  function sendOne(w) {
    return postJSON(endpointFor(state.email), payloadFor(w), 13000).then(function (r) {
      return (r && r.ok ? r.text() : '').then(function (txt) {
        if (/activat/i.test(txt || '')) return 'inactive';
        if (r && r.ok) return true;
        throw new Error('http ' + (r ? r.status : '0'));
      });
    }).catch(function () {
      // 一些浏览器对 file:// 或跨域会拦读取；再试一次 no-cors 的“盲投”
      return fetch(endpointFor(state.email), {
        method: 'POST',
        mode: 'no-cors',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(payloadFor(w))
      }).then(function () {
        return 'maybe';
      }).catch(function () {
        return false;
      });
    });
  }

  function markSent(id) {
    var q = state.queue.indexOf(id);
    if (q >= 0) state.queue.splice(q, 1);
    state.whispers.forEach(function (w) {
      if (w.id === id) { w.sent = w.sent || 'sent'; }
    });
    saveState(true);
    renderStats();
  }

  function sendQueue() {
    if (mailSending) return Promise.resolve();
    if (!validMail(state.email)) { renderStatus(); return Promise.resolve(); }
    if (!state.queue.length) { renderStatus(); return Promise.resolve(); }

    mailSending = true;
    renderStatus();
    var list = state.queue.slice(0, 6);
    var i = 0;

    function next() {
      if (i >= list.length) {
        mailSending = false;
        renderStatus();
        return;
      }
      var id = list[i++];
      var w = null;
      for (var k = 0; k < state.whispers.length; k++) {
        if (state.whispers[k].id === id) { w = state.whispers[k]; break; }
      }
      if (!w) { markSent(id); next(); return; }

      sendOne(w).then(function (ok) {
        if (ok === true || ok === 'maybe') {
          markSent(id);
          if (ok === true) toast('已经悄悄送到他那里了。', 3800);
          else toast('已经送出去了。', 3200);
        } else {
          // 留在本地，下次再试
          var q = state.queue.indexOf(id);
          if (q >= 0) state.queue.splice(q, 1);
          state.queue.push(id);
          saveState(true);
          renderStats();
          if (ok === 'inactive') {
            toast('先帮她收着。等邮箱那边点一下开通，就能寄出去了。', 5200);
          } else {
            toast('先帮你好好收着。等网络好了，再悄悄送出去。', 4600);
          }
        }
        setTimeout(next, 700);
      });
    }
    next();
    return Promise.resolve();
  }

  function renderStatus() {
    var line = $('#statusLine');
    if (!line) return;
    var sent = state.whispers.filter(function (w) { return w.sent === 'sent'; }).length;
    var pending = state.queue.length;
    var parts = [];
    if (validMail(state.email)) parts.push('<span class="pill ok"><i></i>邮箱已设置</span>');
    else parts.push('<span class="pill warn"><i></i>还没填邮箱</span>');
    parts.push('<span class="pill ' + (sent ? 'ok' : '') + '"><i></i>已寄出 ' + sent + '</span>');
    if (pending) parts.push('<span class="pill warn"><i></i>待寄出 ' + pending + '</span>');
    line.innerHTML = parts.join('');
  }

  /* =========================================================================
     13. 记忆 · 小星星
     ========================================================================= */
  function renderStats() {
    var d = state.days.length || 1;
    $('#statDays').textContent = String(d);
    $('#statLights').textContent = String(state.whispers.length);
    $('#statBreath').textContent = String(state.breaths || 0);
    var foot = $('#memoryFoot');
    if (state.streak > 1) foot.textContent = '你已经连着来了 ' + state.streak + ' 晚。灯一直没灭。';
    else if (state.whispers.length === 0) foot.textContent = '这里没有要完成的功课，来或不来，都是好的。';
    else foot.textContent = '每一颗，都是一句被放下的心事。';
    renderStatus();
  }

  function attachConstellation() {
    var box = $('#constellation');
    if (!box) return;
    var hintEl = $('#constellationHint');
    if (state.whispers.length > 0 && hintEl) hintEl.style.display = 'none';

    var all = state.whispers;
    if (all.length === 0) return;
    if (all.length > 120) all = all.slice(-120);

    var have = box.querySelectorAll('.cstar').length;
    if (have >= all.length) return;

    for (var i = have; i < all.length; i++) {
      var w = all[i];
      var rnd = seeded(hash(w.id));
      // 弧形分布，越往后越靠右
      var t = all.length === 1 ? 0.5 : i / (all.length - 1);
      var ang = Math.PI * (0.10 + t * 1.22);
      var rad = 30 + rnd() * 14;
      var cx = 12 + t * 76 + (rnd() - 0.5) * 10;
      var cy = 74 - Math.sin(ang) * rad * 0.62 + (rnd() - 0.5) * 8;
      var el = document.createElement('button');
      el.type = 'button';
      el.className = 'cstar';
      el.style.left = clamp(cx, 5, 95) + '%';
      el.style.top = clamp(cy, 12, 88) + '%';
      el.style.animationDelay = (rnd() * 5).toFixed(2) + 's';
      el.setAttribute('aria-label', '第 ' + (i + 1) + ' 颗星，' + fmtDate(w.ts));
      el.addEventListener('click', function (ww) {
        return function () {
          toast('“' + (ww.text.length > 28 ? ww.text.slice(0, 28) + '…' : ww.text) + '”', 5200);
        };
      }(w));
      box.appendChild(el);
    }
  }

  /* =========================================================================
     14. 声音（Web Audio 合成）
     ========================================================================= */
  var audio = {
    ctx: null, master: null, nodes: [], playing: false, mode: 'waves'
  };

  function initAudio() {
    if (audio.ctx) return audio.ctx;
    var AC = window.AudioContext || window.webkitAudioContext;
    if (!AC) return null;
    try {
      audio.ctx = new AC();
      audio.master = audio.ctx.createGain();
      audio.master.gain.value = 0;
      audio.master.connect(audio.ctx.destination);
    } catch (e) { audio.ctx = null; }
    return audio.ctx;
  }

  function noiseBuffer(ctx, seconds) {
    var len = Math.floor(ctx.sampleRate * seconds);
    var buf = ctx.createBuffer(1, len, ctx.sampleRate);
    var data = buf.getChannelData(0);
    var last = 0;
    for (var i = 0; i < len; i++) {
      var white = Math.random() * 2 - 1;
      last = (last + 0.02 * white) / 1.02;
      data[i] = last * 3.2;
    }
    return buf;
  }

  function buildLayers(mode) {
    var ctx = audio.ctx;
    if (!ctx) return;
    stopLayers();

    var src = ctx.createBufferSource();
    src.buffer = noiseBuffer(ctx, 6);
    src.loop = true;

    var lp = ctx.createBiquadFilter();
    lp.type = 'lowpass';
    lp.frequency.value = mode === 'rain' ? 2600 : 620;
    lp.Q.value = 0.6;

    var hp = ctx.createBiquadFilter();
    hp.type = 'highpass';
    hp.frequency.value = mode === 'rain' ? 900 : 60;

    var g = ctx.createGain();
    g.gain.value = 0.0;

    src.connect(hp);
    hp.connect(lp);
    lp.connect(g);
    g.connect(audio.master);

    // 慢波
    var lfo = ctx.createOscillator();
    lfo.type = 'sine';
    lfo.frequency.value = mode === 'rain' ? 0.11 : 0.075;
    var lfoGain = ctx.createGain();
    lfoGain.gain.value = mode === 'rain' ? 0.16 : 0.34;
    lfo.connect(lfoGain);
    lfoGain.connect(g.gain);

    src.start();
    lfo.start();

    // 远处的和弦
    var chord = [130.81, 196.00, 261.63, 329.63]; // C3 G3 C4 E4
    var padGain = ctx.createGain();
    padGain.gain.value = 0.0;
    var padFilter = ctx.createBiquadFilter();
    padFilter.type = 'lowpass';
    padFilter.frequency.value = 900;
    padFilter.connect(padGain);
    padGain.connect(audio.master);

    var oscs = [];
    chord.forEach(function (f, i) {
      var o = ctx.createOscillator();
      o.type = 'sine';
      o.frequency.value = f;
      o.detune.value = (i % 2 ? 4 : -4);
      var og = ctx.createGain();
      og.gain.value = 0.10 / chord.length;
      o.connect(og);
      og.connect(padFilter);
      o.start();
      oscs.push(o);
    });

    // 很轻的高音星星
    var spark = ctx.createOscillator();
    spark.type = 'sine';
    spark.frequency.value = 1046.5;
    var sparkGain = ctx.createGain();
    sparkGain.gain.value = 0.0;
    var sparkLfo = ctx.createOscillator();
    sparkLfo.frequency.value = 0.05;
    var sparkLfoGain = ctx.createGain();
    sparkLfoGain.gain.value = 0.008;
    sparkLfo.connect(sparkLfoGain);
    sparkLfoGain.connect(sparkGain.gain);
    spark.connect(sparkGain);
    sparkGain.connect(audio.master);
    spark.start();
    sparkLfo.start();

    var t = ctx.currentTime;
    g.gain.linearRampToValueAtTime(mode === 'rain' ? 0.20 : 0.30, t + 2.4);
    padGain.gain.linearRampToValueAtTime(0.10, t + 3.2);

    audio.nodes = [src, lfo, spark, sparkLfo].concat(oscs);
    audio.nodes.push(g, lfoGain, padGain, padFilter, sparkGain, sparkLfoGain, lp, hp);
  }

  function stopLayers() {
    audio.nodes.forEach(function (n) {
      try { if (n.stop) n.stop(); } catch (e) {}
      try { if (n.disconnect) n.disconnect(); } catch (e) {}
    });
    audio.nodes = [];
  }

  function setSound(on) {
    if (!initAudio()) {
      toast('这个浏览器好像不支持声音。安静的夜晚也很好。', 3200);
      state.settings.sound = false;
      saveState();
      syncSoundUI();
      return;
    }
    if (audio.ctx.state === 'suspended') audio.ctx.resume();
    if (on && !audio.playing) {
      audio.mode = state.settings.soundMode || 'waves';
      buildLayers(audio.mode);
      audio.playing = true;
      audio.master.gain.linearRampToValueAtTime(0.7, audio.ctx.currentTime + 1.6);
    } else if (on && audio.playing) {
      audio.master.gain.linearRampToValueAtTime(0.7, audio.ctx.currentTime + 0.8);
    } else if (!on && audio.playing) {
      audio.master.gain.linearRampToValueAtTime(0, audio.ctx.currentTime + 1.0);
      audio.playing = false;
      setTimeout(function () { if (!audio.playing) stopLayers(); }, 1200);
    }
    state.settings.sound = !!on;
    saveState();
    syncSoundUI();
  }

  function syncSoundUI() {
    var on = !!state.settings.sound && audio.playing;
    var ico = $('#soundIco'), lbl = $('#soundLbl'), btn = $('#soundBtn');
    if (ico) ico.textContent = on ? '♫' : '♪';
    if (lbl) lbl.textContent = on ? (state.settings.soundMode === 'rain' ? '夜雨' : '海浪') : '声音';
    if (btn) btn.setAttribute('aria-pressed', on ? 'true' : 'false');
    var b2 = $('#soundBtn2');
    if (b2) b2.textContent = on ? '开着' : '关着';
  }

  /* =========================================================================
     15. 设置抽屉
     ========================================================================= */
  function openDrawer() {
    $('#nickInput').value = state.name || '';
    $('#mailInput').value = state.email || '';
    renderStatus();
    openVeil($('#drawerVeil'));
    syncSoundUI();
  }

  function bindDrawer() {
    $('#settingsBtn').addEventListener('click', openDrawer);
    $('#drawerClose').addEventListener('click', function () { closeVeil($('#drawerVeil')); });
    $('#drawerVeil').addEventListener('click', function (e) {
      if (e.target === $('#drawerVeil')) closeVeil($('#drawerVeil'));
    });

    $('#nickInput').addEventListener('input', function () {
      var v = this.value.trim().slice(0, 12);
      state.name = v || '小煜';
      saveState();
      renderHero();
    });

    $('#mailInput').addEventListener('change', function () {
      var v = this.value.trim();
      if (v && !validMail(v)) { toast('这个邮箱看起来不太对，再看一眼？', 3400); return; }
      state.email = v || DEFAULT_MAIL;
      saveState(true);
      renderStatus();
      toast('记住了。她的话会寄到这里。', 3000);
    });

    $('#testMailBtn').addEventListener('click', function () {
      if (!validMail(state.email)) { toast('先填一个邮箱吧。', 3000); return; }
      this.disabled = true;
      var self = this;
      var testW = { id: 'test-' + Date.now(), ts: Date.now(), text: '（这是一封测试信）夜色已经点好灯了。', from: 'test' };
      postJSON(endpointFor(state.email), payloadFor(testW), 13000).then(function (r) {
        return (r && r.ok ? r.text() : '').then(function (txt) {
          if (/activat/i.test(txt || '')) {
            toast('已发出第一封。请去邮箱点“Activate Form”，点完再按一次这个测试，就成了。', 7200);
          } else if (r && r.ok) {
            toast('测试信已发出。去邮箱看看，之后她写下的都会寄到这里。', 6000);
            if (state.queue.length) setTimeout(sendQueue, 1200);
          } else {
            toast('发出了，但没得到回应。要不换一个邮箱试试？', 5000);
          }
        });
      }).catch(function () {
        toast('网络或邮箱服务没接通。可以先导出，等她写了你再告诉她。', 5600);
      }).then(function () { self.disabled = false; });
    });

    $('#retryBtn').addEventListener('click', function () {
      if (!state.queue.length) { toast('没有等着寄出的。', 2600); return; }
      toast('再试一次。', 2000);
      sendQueue();
    });

    $('#exportBtn').addEventListener('click', exportAll);
    $('#resetBtn').addEventListener('click', function () {
      if (this.dataset.armed === '1') {
        resetAll();
        this.dataset.armed = '0';
        this.textContent = '清空';
        return;
      }
      this.dataset.armed = '1';
      this.textContent = '再点一次确认';
      toast('再点一次，她写下的都会消失。', 3800);
      var self = this;
      setTimeout(function () {
        if (self.dataset.armed === '1') { self.dataset.armed = '0'; self.textContent = '清空'; }
      }, 6000);
    });

    $('#soundBtn2').addEventListener('click', function () {
      var next = !state.settings.sound;
      if (!next) { setSound(false); return; }
      state.settings.soundMode = state.settings.soundMode === 'rain' ? 'waves' : 'rain';
      setSound(true);
    });

    // 点击外部关闭
    document.addEventListener('keydown', function (e) {
      if (e.key === 'Escape') {
        closeVeil($('#drawerVeil'));
        closeVeil($('#moonVeil'));
        if (breath.running) stopBreathing();
      }
    });
  }

  function exportAll() {
    var lines = [];
    lines.push('夜色里，留一盏灯给你');
    lines.push('她写下的话 · 导出时间 ' + fmtDate(Date.now()));
    lines.push('——————————————');
    if (!state.whispers.length) {
      lines.push('（还没有写下什么。）');
    } else {
      state.whispers.forEach(function (w, i) {
        lines.push((i + 1) + '. ' + fmtDate(w.ts) + '  ' + (w.sent === 'sent' ? '［已寄出］' : '［存在这里］'));
        lines.push('   ' + w.text);
        lines.push('');
      });
    }
    lines.push('——————————————');
    lines.push('来过 ' + (state.days.length || 1) + ' 个夜晚，连着 ' + (state.streak || 1) + ' 晚。');
    lines.push('按下的灯：' + Object.keys(state.lanterns).map(function (k) {
      var m = MOODS.filter(function (x) { return x.key === k; })[0];
      return (m ? m.name : k) + '×' + state.lanterns[k];
    }).join('、'));
    var blob = new Blob([lines.join('\n')], { type: 'text/plain;charset=utf-8' });
    var url = URL.createObjectURL(blob);
    var a = document.createElement('a');
    a.href = url;
    a.download = '夜色里的话-' + todayKey() + '.txt';
    document.body.appendChild(a);
    a.click();
    setTimeout(function () {
      document.body.removeChild(a);
      URL.revokeObjectURL(url);
    }, 600);
    toast('导出了一份，收好。', 3000);
  }

  function resetAll() {
    var keepMail = state.email;
    var keepName = state.name;
    state = blankState();
    state.email = keepMail || DEFAULT_MAIL;
    state.name = keepName || '小煜';
    state.introSeen = true;
    saveState(true);
    var box = $('#constellation');
    if (box) $$('.cstar', box).forEach(function (n) { n.remove(); });
    var hint = $('#constellationHint');
    if (hint) hint.style.display = '';
    renderStats();
    renderHero();
    renderStatus();
    toast('清干净了。还有灯留着。', 3600);
  }

  /* =========================================================================
     16. 其它交互
     ========================================================================= */
  function bindMisc() {
    $('#moon').addEventListener('click', openMoonCard);
    $('#moonClose').addEventListener('click', function () { closeVeil($('#moonVeil')); });
    $('#moonVeil').addEventListener('click', function (e) {
      if (e.target === $('#moonVeil')) closeVeil($('#moonVeil'));
    });

    var input = $('#whisperInput');
    input.addEventListener('input', function () { countChars(this); });
    input.addEventListener('keydown', function (e) {
      if ((e.metaKey || e.ctrlKey) && e.key === 'Enter') { e.preventDefault(); releaseWhisper(); }
    });
    $('#releaseBtn').addEventListener('click', releaseWhisper);

    $('#bQuit').addEventListener('click', stopBreathing);
    $('#breathStage').addEventListener('click', function (e) {
      if (e.target === this) stopBreathing();
    });

    $('#soundBtn').addEventListener('click', function () {
      var next = !state.settings.sound;
      if (next && !audio.playing) {
        // 关着 -> 开海浪；开着 -> 关
        state.settings.soundMode = state.settings.soundMode || 'waves';
      }
      setSound(next);
    });

    $('#openMemoryBtn').addEventListener('click', function () {
      if (!state.whispers.length) {
        toast('还没有小星星。等你写下第一句，它就会亮起来。', 4200);
        return;
      }
      var last = state.whispers[state.whispers.length - 1];
      toast('最近放下的一句：“' + (last.text.length > 40 ? last.text.slice(0, 40) + '…' : last.text) + '”', 6000);
    });

    $('#bottomBtn').addEventListener('click', function () {
      $('#whisperInput').scrollIntoView({ behavior: reduceMotion ? 'auto' : 'smooth', block: 'center' });
      setTimeout(function () { try { $('#whisperInput').focus({ preventScroll: true }); } catch (e) {} }, 420);
    });

    // 底部条：滚过首屏出现
    var bottom = $('#bottomBar');
    if ('IntersectionObserver' in window) {
      var io = new IntersectionObserver(function (entries) {
        entries.forEach(function (en) {
          bottom.classList.toggle('show', !en.isIntersecting);
          bottom.setAttribute('aria-hidden', en.isIntersecting ? 'true' : 'false');
        });
      }, { rootMargin: '-10% 0px 0px 0px' });
      io.observe($('.hero'));
    } else {
      bottom.classList.add('show');
    }
    $('#bottomSay').textContent = pick(BOTTOM_LINES, 'bottom' + Math.floor(Date.now() / 600000));

    // 轻微视差（仅桌面）
    if (!isTouch && !reduceMotion) {
      var scene = [$('#stars')];
      document.addEventListener('mousemove', function (e) {
        var x = (e.clientX / window.innerWidth - 0.5) * 2;
        var y = (e.clientY / window.innerHeight - 0.5) * 2;
        scene.forEach(function (n) {
          if (n) n.style.transform = 'translate3d(' + (x * -4).toFixed(2) + 'px,' + (y * -3).toFixed(2) + 'px,0)';
        });
      }, { passive: true });
    }

    // 页面切换回来时，刷新一下月亮和问候
    document.addEventListener('visibilitychange', function () {
      if (!document.hidden) {
        paintMoon();
        startSayingsReset();
      }
    });

    var moonResizeT = null;
    window.addEventListener('resize', function () {
      clearTimeout(moonResizeT);
      moonResizeT = setTimeout(paintMoon, 200);
    });
    window.addEventListener('orientationchange', function () {
      setTimeout(paintMoon, 320);
    });
  }

  function startSayingsReset() {
    if (sayingTimer) clearInterval(sayingTimer);
    sayingTimer = null;
    var a = $('#sayingA'), b = $('#sayingB');
    if (a) a.classList.remove('on');
    if (b) b.classList.remove('on');
    startSayings();
  }

  /* =========================================================================
     17. 启动
     ========================================================================= */
  function boot() {
    loadState();
    noteVisit();

    renderHero();
    renderLanterns();
    renderStats();
    attachConstellation();
    countChars($('#whisperInput'));

    startSayings();
    bindMisc();
    bindDrawer();

    // 声音：不自动播放，保持安静，等她点头
    syncSoundUI();

    var intro = $('#intro');
    if (state.introSeen || safeGet(STORE_KEY + '.intro.' + todayKey())) {
      intro.classList.add('gone');
    } else {
      $('#enterBtn').focus();
    }

    $('#enterBtn').addEventListener('click', function () {
      state.introSeen = true;
      saveState(true);
      intro.classList.add('gone');
      $('#moonHint').textContent = '轻 轻 碰 一 下 月 亮';
      setTimeout(function () { $('#moon').focus(); }, 900);
    });

    // 有早就该寄出却没寄出的，醒来后补寄
    if (state.queue.length) setTimeout(sendQueue, 2600);

    // 每分钟把问候轻轻换一换（不打扰）
    setInterval(function () {
      if (document.hidden) return;
      var h = new Date().getHours();
      if (h === 0 && Math.random() < 0.02) renderHero();
    }, 60000);
  }

  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', boot);
  } else {
    boot();
  }
})();
</script>
</body>
</html>

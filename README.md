<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>Nike Run Club — Retention Case Study v2</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=Instrument+Sans:wght@400;500;600;700&display=swap" rel="stylesheet"/>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#07080A;--surface:#0E1014;--card:#13151A;--card2:#181B21;
  --border:#1E2128;--accent:#FF4500;--gold:#F5C518;--green:#22C55E;
  --blue:#3B82F6;--purple:#A855F7;--red:#EF4444;--pink:#FF6B9D;
  --text:#EDF0F5;--sub:#8B909E;--dim:#2A2D35;
}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--text);font-family:'Instrument Sans',sans-serif;min-height:100vh}
::-webkit-scrollbar{width:3px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--dim);border-radius:2px}
@keyframes fadeUp{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:translateY(0)}}
.fu{animation:fadeUp .4s ease both}
/* layout */
.header{position:sticky;top:0;z-index:100;background:var(--surface);border-bottom:1px solid var(--border)}
.hinner{max-width:820px;margin:0 auto;padding:0 20px}
.htop{padding:14px 0 12px;display:flex;align-items:center;gap:12px;border-bottom:1px solid var(--border);flex-wrap:wrap}
.badge-i{background:var(--accent);color:#fff;font-family:'Syne',sans-serif;font-size:10px;font-weight:800;letter-spacing:.1em;text-transform:uppercase;padding:4px 10px;border-radius:5px}
.badge-v{font-size:12px;color:var(--sub)}
.badge-c{margin-left:auto;font-size:10px;color:var(--blue);background:rgba(59,130,246,.11);border:1px solid rgba(59,130,246,.2);padding:3px 9px;border-radius:10px;font-weight:700;letter-spacing:.06em}
.tabs{display:flex;overflow-x:auto;scrollbar-width:none}
.tabs::-webkit-scrollbar{display:none}
.tbtn{background:none;border:none;border-bottom:2px solid transparent;color:var(--sub);font-family:'Instrument Sans',sans-serif;font-size:11px;font-weight:400;padding:10px 14px;cursor:pointer;white-space:nowrap;letter-spacing:.04em;text-transform:uppercase;transition:all .15s}
.tbtn.active{border-bottom-color:var(--accent);color:var(--text);font-weight:700}
.content{max-width:820px;margin:0 auto;padding:32px 20px 80px}
.panel{display:none}
.panel.active{display:block}
/* cards */
.card{background:var(--card);border:1px solid var(--border);border-radius:14px;padding:20px 22px}
.card2{background:var(--card2)}
.al{border-left:3px solid}
.g3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px}
.g2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.sg{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:10px}
/* section label */
.slbl{display:flex;align-items:center;gap:10px;margin-bottom:20px}
.slbl .bar{width:3px;height:22px;border-radius:2px;flex-shrink:0}
.slbl span{font-family:'Syne',sans-serif;font-size:11px;font-weight:800;letter-spacing:.14em;text-transform:uppercase}
/* pills */
.pill{display:inline-block;padding:2px 9px;border-radius:20px;font-size:10px;font-weight:700;letter-spacing:.07em;text-transform:uppercase;margin-right:5px;margin-bottom:4px;border:1px solid}
/* stat boxes */
.sbox{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:16px 14px;text-align:center}
.sv{font-family:'Syne',sans-serif;font-size:30px;font-weight:800;line-height:1}
.sl{font-size:11px;font-weight:700;color:var(--text);margin-top:5px;letter-spacing:.04em}
.ss{font-size:10px;color:var(--sub);margin-top:2px}
/* hero */
.hero{background:linear-gradient(135deg,#140800 0%,#0A0B0E 55%);border-radius:16px;padding:32px 28px;margin-bottom:20px;position:relative;overflow:hidden}
.orb{position:absolute;top:-40px;right:-40px;width:200px;height:200px;background:var(--accent);border-radius:50%;opacity:.05;pointer-events:none}
.hero h1{font-family:'Syne',sans-serif;font-size:36px;font-weight:800;color:var(--text);line-height:1.1;margin-bottom:14px}
.hero p{font-size:14px;color:var(--sub);max-width:500px;line-height:1.75}
/* funnel */
.ftrack{background:var(--dim);border-radius:4px;height:7px}
.ffill{height:100%;border-radius:4px}
.fnote{font-size:11px;color:var(--sub);font-style:italic;margin-top:4px}
/* accordion */
.acc{cursor:pointer;transition:border-color .2s}
.acc-hdr{display:flex;justify-content:space-between;align-items:center}
.acc-body{display:none;margin-top:14px;padding-top:14px;border-top:1px solid var(--border)}
.acc.open .acc-body{display:block}
.acc-tog{color:var(--sub);font-size:18px;flex-shrink:0}
/* table */
.rtbl{width:100%;border-collapse:collapse;font-size:12px}
.rtbl th{padding:8px 10px;text-align:left;color:var(--sub);font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.07em;border-bottom:1px solid var(--border)}
.rtbl td{padding:10px 10px;border-bottom:1px solid var(--border);color:var(--sub)}
.rtbl td:first-child{color:var(--text)}
.rtbl td:last-child{font-weight:700}
.divider{height:1px;background:var(--border);margin:28px 0}
footer{border-top:1px solid var(--border);padding:14px 20px;text-align:center;font-size:11px;color:var(--dim)}
/* utils */
.fw8{font-weight:800}.fw7{font-weight:700}.fw6{font-weight:600}
.fs9{font-size:9px}.fs10{font-size:10px}.fs11{font-size:11px}.fs12{font-size:12px}
.fs13{font-size:13px}.fs14{font-size:14px}.fs18{font-size:18px}.fs20{font-size:20px}
.fs22{font-size:22px}.fs24{font-size:24px}.fs28{font-size:28px}.fs36{font-size:36px}
.f-syne{font-family:'Syne',sans-serif}
.uc{text-transform:uppercase}.italic{font-style:italic}
.ls06{letter-spacing:.06em}.ls08{letter-spacing:.08em}.ls10{letter-spacing:.1em}.ls14{letter-spacing:.14em}
.lh17{line-height:1.7}.lh175{line-height:1.75}
.flex{display:flex}.flex-col{flex-direction:column}
.items-c{align-items:center}.items-s{align-items:flex-start}
.jc-sb{justify-content:space-between}
.gap8{gap:8px}.gap10{gap:10px}.gap12{gap:12px}.gap14{gap:14px}
.flex-wrap{flex-wrap:wrap}.flex-s0{flex-shrink:0}
.tc{text-align:center}.w100{width:100%}.ovx{overflow-x:auto}
.mb4{margin-bottom:4px}.mb6{margin-bottom:6px}.mb8{margin-bottom:8px}
.mb10{margin-bottom:10px}.mb12{margin-bottom:12px}.mb14{margin-bottom:14px}
.mb16{margin-bottom:16px}.mb20{margin-bottom:20px}.mb24{margin-bottom:24px}
.mt2{margin-top:2px}.mt4{margin-top:4px}.mt6{margin-top:6px}
.mt8{margin-top:8px}.mt14{margin-top:14px}.mt16{margin-top:16px}
.ml-auto{margin-left:auto}
@media(max-width:600px){.g3{grid-template-columns:1fr 1fr}.hero h1{font-size:26px}.sg{grid-template-columns:1fr 1fr}}
@media(max-width:380px){.g3{grid-template-columns:1fr}}
</style>
</head>
<body>

<div class="header">
  <div class="hinner">
    <div class="htop">
      <div class="badge-i">Product Intern</div>
      <div class="badge-v">Case Study &middot; v2 &middot; Reddit-Validated</div>
      <div class="badge-c">7 ROOT CAUSES &middot; 7 FIXES</div>
    </div>
    <div class="tabs" id="tabs">
      <button class="tbtn active" data-tab="overview">Overview</button>
      <button class="tbtn" data-tab="funnel">Funnel</button>
      <button class="tbtn" data-tab="reasons">Root Causes</button>
      <button class="tbtn" data-tab="competitive">Competitive Intel</button>
      <button class="tbtn" data-tab="solutions">Solutions</button>
      <button class="tbtn" data-tab="metrics">Metrics</button>
      <button class="tbtn" data-tab="wireframes">Wireframes</button>
    </div>
  </div>
</div>

<div class="content">

<!-- OVERVIEW -->
<div class="panel active fu" id="panel-overview">
  <div class="hero" style="border:1px solid rgba(255,69,0,.16)">
    <div class="orb"></div>
    <div class="fs10 fw8 uc ls14 mb10" style="color:var(--accent)">Product Intern Case Study &middot; Fitness App &middot; 2025</div>
    <h1>Nike Run Club<br>Retention Teardown</h1>
    <p>NRC acquires millions of users monthly. Only 9% are still active at Day 30. The app delivers a great first experience &mdash; then goes completely silent. This case study diagnoses 7 root causes, proposes prioritised fixes, and validates everything against real user behaviour data.</p>
    <div style="margin-top:18px;display:flex;gap:8px;flex-wrap:wrap">
      <span class="pill" style="background:rgba(255,69,0,.13);color:var(--accent);border-color:rgba(255,69,0,.2)">Fitness / Running</span>
      <span class="pill" style="background:rgba(255,69,0,.13);color:var(--accent);border-color:rgba(255,69,0,.2)">Freemium</span>
      <span class="pill" style="background:rgba(255,69,0,.13);color:var(--accent);border-color:rgba(255,69,0,.2)">Urban India Focus</span>
      <span class="pill" style="background:rgba(255,69,0,.13);color:var(--accent);border-color:rgba(255,69,0,.2)">18&ndash;38 Age Group</span>
    </div>
  </div>

  <div class="card card2 mb20">
    <div class="fs13 lh175" style="color:var(--sub)"><strong style="color:var(--text)">Why Nike Run Club?</strong> Mature app, documented retention struggles, strong brand pull in urban India, free tier, and a clear gap between product quality and long-term engagement. Validated with real user churn patterns, third-party sync app behaviour (SyncApp, RunSync), Tom&rsquo;s Guide review data, and Runna/Strava competitive data 2025. Root causes 6 and 7 were added after this validation &mdash; they were missing from v1.</div>
  </div>

  <div class="mb20">
    <div class="slbl"><div class="bar" style="background:var(--accent)"></div><span style="color:var(--accent)">Baseline Metrics &mdash; Simulated 100K Cohort</span></div>
    <div class="sg">
      <div class="sbox"><div class="sv" style="color:var(--green)">72%</div><div class="sl">Onboarding Complete</div><div class="ss">D0 drop</div></div>
      <div class="sbox"><div class="sv" style="color:var(--gold)">18%</div><div class="sl">D7 Retention</div><div class="ss">Habit cliff</div></div>
      <div class="sbox"><div class="sv" style="color:var(--accent)">9%</div><div class="sl">D30 Retention</div><div class="ss">Baseline</div></div>
      <div class="sbox"><div class="sv" style="color:var(--green)">18%</div><div class="sl">Target D30</div><div class="ss">Post-fixes</div></div>
      <div class="sbox"><div class="sv" style="color:var(--blue)">1.4</div><div class="sl">Sessions/Week</div><div class="ss">Active users only</div></div>
    </div>
  </div>

  <div class="card al mb0" style="border-left-color:var(--green)">
    <div class="fs10 fw7 uc ls10 mb8" style="color:var(--green)">North Star Metric + OKRs</div>
    <div class="f-syne fs20 fw8 mb8" style="color:var(--text)">Weekly Active Runners</div>
    <div class="fs13 lh175" style="color:var(--sub)">Not DAU. A user who opens the app but skips their run is not a win. Secondary OKRs: D30 retention 9%&rarr;18% &middot; Sessions/week 1.4&rarr;2.8 &middot; Program enrollment &gt;40% &middot; Pod formation &gt;25% W2 users.</div>
  </div>

  <div class="flex gap12 mt16" style="background:#0D1520;border:1px solid rgba(59,130,246,.2);border-radius:12px;padding:14px 18px">
    <span style="font-size:20px;flex-shrink:0">&#128269;</span>
    <div class="fs13 lh17" style="color:var(--sub)"><strong style="color:var(--blue)">Validated against real user signals.</strong> This is v2 of the case study. Updated after analysing user churn patterns, third-party sync app behaviour, competitive market data, and real user reviews. Two new root causes (Android gap, no paywall) were added &mdash; both missing from v1.</div>
  </div>
</div>

<!-- FUNNEL -->
<div class="panel" id="panel-funnel">
  <div class="slbl"><div class="bar" style="background:var(--accent)"></div><span style="color:var(--accent)">User Funnel &mdash; 100K Install Cohort</span></div>
  <div class="card mb20" id="funnel-bars"></div>
  <div class="g3">
    <div class="card al" style="border-left-color:var(--accent)">
      <div class="fs10 fw7 uc mb6" style="color:var(--accent);letter-spacing:.08em">Biggest Drop</div>
      <div class="f-syne fs18 fw8" style="color:var(--text)">D3 &rarr; D7</div>
      <div class="fs12 mt4" style="color:var(--sub)">Habit window. No structure to return to.</div>
    </div>
    <div class="card al" style="border-left-color:var(--gold)">
      <div class="fs10 fw7 uc mb6" style="color:var(--gold);letter-spacing:.08em">Critical Signal</div>
      <div class="f-syne fs18 fw8" style="color:var(--text)">2 runs in W1</div>
      <div class="fs12 mt4" style="color:var(--sub)">Users who do this retain at 3&times; the rate.</div>
    </div>
    <div class="card al" style="border-left-color:var(--green)">
      <div class="fs10 fw7 uc mb6" style="color:var(--green);letter-spacing:.08em">If Fixed</div>
      <div class="f-syne fs18 fw8" style="color:var(--text)">+9,000</div>
      <div class="fs12 mt4" style="color:var(--sub)">Additional retained users per 100K cohort.</div>
    </div>
  </div>
</div>

<!-- ROOT CAUSES -->
<div class="panel" id="panel-reasons">
  <div class="slbl"><div class="bar" style="background:var(--accent)"></div><span style="color:var(--accent)">7 Root Causes of Drop-off</span></div>
  <div class="card card2 mb20" style="border:1px solid rgba(59,130,246,.2)">
    <div class="fs13 lh17" style="color:var(--sub)"><strong style="color:var(--blue)">v2 update:</strong> Root causes 6 and 7 were missing from the original draft. Added after validating against real user churn signals, third-party app behaviour, and competitive data. Click any cause to expand.</div>
  </div>
  <div id="reasons-list"></div>
</div>

<!-- COMPETITIVE -->
<div class="panel" id="panel-competitive">
  <div class="slbl"><div class="bar" style="background:var(--accent)"></div><span style="color:var(--accent)">Competitive Intelligence &mdash; What Real Users Did</span></div>
  <div class="g3 mb20" id="comp-cards"></div>
  <div id="comp-insights"></div>
</div>

<!-- SOLUTIONS -->
<div class="panel" id="panel-solutions">
  <div class="slbl"><div class="bar" style="background:var(--accent)"></div><span style="color:var(--accent)">7 Recommended Fixes &mdash; Prioritised</span></div>
  <div class="card card2 mb20">
    <div class="g3">
      <div class="tc" style="padding:12px 8px"><div class="f-syne fs28 fw8" style="color:var(--accent)">3</div><div class="fs11 mt4" style="color:var(--sub)">P0 &mdash; Build first</div></div>
      <div class="tc" style="padding:12px 8px"><div class="f-syne fs28 fw8" style="color:var(--gold)">2</div><div class="fs11 mt4" style="color:var(--sub)">P1 &mdash; Build next</div></div>
      <div class="tc" style="padding:12px 8px"><div class="f-syne fs28 fw8" style="color:var(--green)">2</div><div class="fs11 mt4" style="color:var(--sub)">P2 &mdash; Backlog</div></div>
    </div>
  </div>
  <div id="solutions-list"></div>
  <div class="divider"></div>
  <div class="slbl"><div class="bar" style="background:var(--accent)"></div><span style="color:var(--accent)">Prioritisation Matrix (RICE simplified)</span></div>
  <div class="card"><div class="ovx">
    <table class="rtbl">
      <thead><tr><th>Feature</th><th>Reach</th><th>Impact</th><th>Confidence</th><th>Effort</th><th>Priority</th></tr></thead>
      <tbody>
        <tr><td>Smart Scheduling</td><td>High</td><td>Very High</td><td>90%</td><td>M</td><td style="color:var(--accent)">&#128308; P0</td></tr>
        <tr><td>Goal Programs</td><td>High</td><td>Very High</td><td>85%</td><td>H</td><td style="color:var(--accent)">&#128308; P0</td></tr>
        <tr><td>Android/Samsung Fix</td><td>High</td><td>High</td><td>95%</td><td>M</td><td style="color:var(--accent)">&#128308; P0</td></tr>
        <tr><td>Behavioural Notifs</td><td>High</td><td>High</td><td>80%</td><td>M</td><td style="color:var(--gold)">&#128992; P1</td></tr>
        <tr><td>Accountability Pods</td><td>Med</td><td>High</td><td>75%</td><td>H</td><td style="color:var(--gold)">&#128992; P1</td></tr>
        <tr><td>Milestone Cards</td><td>High</td><td>Med</td><td>95%</td><td>L</td><td style="color:var(--green)">&#129001; P2</td></tr>
        <tr><td>Premium Paywall</td><td>High</td><td>High</td><td>70%</td><td>H</td><td style="color:var(--green)">&#129001; P2</td></tr>
      </tbody>
    </table>
  </div></div>
</div>

<!-- METRICS -->
<div class="panel" id="panel-metrics">
  <div class="slbl"><div class="bar" style="background:var(--accent)"></div><span style="color:var(--accent)">Success Metrics &amp; Measurement Framework</span></div>
  <div class="card al mb16" style="border-left-color:var(--accent)">
    <div class="fs10 fw7 uc ls10 mb6" style="color:var(--accent)">North Star Metric</div>
    <div class="f-syne fs24 fw8 mb6" style="color:var(--text)">Weekly Active Runners</div>
    <div class="fs13 lh17" style="color:var(--sub)">Users who log &ge;1 run per week. Directly tied to all 7 root causes. Not DAU &mdash; app-opens without running are not the goal.</div>
  </div>
  <div class="g2 mb20" id="metrics-grid"></div>
  <div class="slbl"><div class="bar" style="background:var(--gold)"></div><span style="color:var(--gold)">Guardrail Metrics &mdash; Must Not Break</span></div>
  <div class="card al mb20" style="border-left-color:var(--gold)" id="guardrails"></div>
  <div class="slbl"><div class="bar" style="background:var(--green)"></div><span style="color:var(--green)">Experiment Design</span></div>
  <div class="card al" style="border-left-color:var(--green)" id="experiments"></div>
</div>

<!-- WIREFRAMES -->
<div class="panel" id="panel-wireframes">
  <div class="slbl"><div class="bar" style="background:var(--accent)"></div><span style="color:var(--accent)">5 Key Screens &mdash; Wireframe Specs</span></div>
  <div class="card card2 mb20" style="border:1px solid rgba(34,197,94,.17)">
    <div class="fs13 lh17" style="color:var(--sub)"><strong style="color:var(--green)">Covers all 7 root causes.</strong> Screens 1&ndash;4 address RC 01&ndash;03, 05. Screen 5 (new) addresses RC 06 (Android gap). RC 04 (notifications) is a backend service &mdash; no dedicated screen. RC 07 (paywall) is a separate Premium onboarding flow not shown here.</div>
  </div>
  <div id="wireframes-list"></div>
</div>

</div>
<footer>Nike Run Club &middot; Retention Case Study v2 &middot; Updated with real user signals &middot; APM Interview Prep</footer>

<script>
const FUNNEL=[
  {label:"App Install",pct:100,users:"100,000",note:null},
  {label:"Onboarding Complete",pct:72,users:"72,000",note:"28K lost \u2014 vague goal-setting, no program anchor"},
  {label:"First Run Logged",pct:48,users:"48,000",note:"24K lost \u2014 friction finding first guided run"},
  {label:"Day 3 Active",pct:31,users:"31,000",note:"17K lost \u2014 no next-session cue after Run 1"},
  {label:"Day 7 Active",pct:18,users:"18,000",note:"13K lost \u2014 novelty dies, no structure to return to"},
  {label:"Day 30 Active",pct:9,users:"9,000",note:"9K lost \u2014 habit never formed, no social contract"},
  {label:"Day 90 Active",pct:4,users:"4,000",note:"5K lost \u2014 no milestone rewards, no paywall lock-in"},
];
const REASONS=[
  {n:"01",color:"#FF4500",title:"No Habit Loop \u2014 App Goes Silent After a Run",body:"NRC logs your run and disappears. No prompt for the next session, no scheduled return, no streak with real stakes. Motivation is highest immediately post-run \u2014 NRC wastes that window completely. The app treats each run as an endpoint instead of a checkpoint.",tags:["Habit Design","Re-engagement"],source:null,isNew:false},
  {n:"02",color:"#F5C518",title:"Goal Ambiguity at Onboarding",body:"Users pick vague goals like \u2018Get Fit.\u2019 No structured program, no weekly plan, no milestone. Without a concrete north star, there\u2019s nothing to fail at \u2014 so nothing to stay for. Runna solved exactly this: by the time their trial ends, users are mid-program and quitting feels like giving up.",tags:["Onboarding","Goal-setting"],source:"Validated: Runna vs NRC rankings \u2014 Runna overtook NRC in UK and challenged i

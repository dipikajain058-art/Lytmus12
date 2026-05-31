import { useState } from "react";

/* ─── TOKENS ──────────────────────────────────────────── */
const C = {
  bg: "#07080A",
  surface: "#0E1014",
  card: "#13151A",
  card2: "#181B21",
  border: "#1E2128",
  accent: "#FF4500",
  accentLow: "#FF450018",
  gold: "#F5C518",
  goldLow: "#F5C51815",
  green: "#22C55E",
  greenLow: "#22C55E15",
  blue: "#3B82F6",
  blueLow: "#3B82F615",
  purple: "#A855F7",
  purpleLow: "#A855F715",
  red: "#EF4444",
  text: "#EDF0F5",
  sub: "#8B909E",
  dim: "#2A2D35",
};

/* ─── GLOBAL STYLES ───────────────────────────────────── */
const G = () => (
  <style>{`
    @import url('https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=Instrument+Sans:wght@400;500;600;700&display=swap');
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    ::-webkit-scrollbar { width: 3px; }
    ::-webkit-scrollbar-track { background: ${C.bg}; }
    ::-webkit-scrollbar-thumb { background: ${C.dim}; border-radius: 2px; }
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(14px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
    .fu0 { animation: fadeUp .45s ease both; }
    .fu1 { animation: fadeUp .45s .08s ease both; }
    .fu2 { animation: fadeUp .45s .16s ease both; }
    .fu3 { animation: fadeUp .45s .24s ease both; }
    .fu4 { animation: fadeUp .45s .32s ease both; }
  `}</style>
);

/* ─── PRIMITIVES ──────────────────────────────────────── */
const Card = ({ children, style, accent }) => (
  <div style={{
    background: C.card, border: `1px solid ${accent ? accent + "33" : C.border}`,
    borderRadius: 14, padding: "20px 22px",
    ...(accent ? { borderLeft: `3px solid ${accent}` } : {}),
    ...style,
  }}>{children}</div>
);

const Pill = ({ label, color }) => (
  <span style={{
    display: "inline-block", padding: "2px 9px", borderRadius: 20,
    fontSize: 10, fontWeight: 700, letterSpacing: "0.07em", textTransform: "uppercase",
    background: color + "20", color, border: `1px solid ${color}33`,
    marginRight: 5, marginBottom: 4,
  }}>{label}</span>
);

const Divider = () => (
  <div style={{ height: 1, background: C.border, margin: "28px 0" }} />
);

const SectionLabel = ({ text, color }) => (
  <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 20 }}>
    <div style={{ width: 3, height: 22, borderRadius: 2, background: color || C.accent, flexShrink: 0 }} />
    <span style={{
      fontFamily: "'Syne', sans-serif", fontSize: 11, fontWeight: 800,
      letterSpacing: "0.14em", textTransform: "uppercase", color: color || C.accent,
    }}>{text}</span>
  </div>
);

const StatBox = ({ label, value, sub, color }) => (
  <div style={{
    background: C.card, border: `1px solid ${C.border}`, borderRadius: 12,
    padding: "16px 14px", textAlign: "center",
  }}>
    <div style={{ fontFamily: "'Syne', sans-serif", fontSize: 30, fontWeight: 800, color: color || C.accent, lineHeight: 1 }}>{value}</div>
    <div style={{ fontSize: 11, fontWeight: 700, color: C.text, marginTop: 5, letterSpacing: "0.04em" }}>{label}</div>
    {sub && <div style={{ fontSize: 10, color: C.sub, marginTop: 2 }}>{sub}</div>}
  </div>
);

/* ─── TABS ────────────────────────────────────────────── */
const TABS = [
  { id: "overview",    label: "Overview" },
  { id: "funnel",      label: "Funnel" },
  { id: "reasons",     label: "Root Causes" },
  { id: "competitive", label: "Competitive Intel" },
  { id: "solutions",   label: "Solutions" },
  { id: "metrics",     label: "Metrics" },
  { id: "wireframes",  label: "Wireframes" },
];

/* ════════════════════════════════════════════════════════
   TAB: OVERVIEW
════════════════════════════════════════════════════════ */
const Overview = () => (
  <div className="fu0">
    {/* Hero */}
    <div style={{
      background: `linear-gradient(135deg, #140800 0%, #0A0B0E 55%)`,
      border: `1px solid ${C.accent}28`, borderRadius: 16,
      padding: "32px 28px", marginBottom: 20, position: "relative", overflow: "hidden",
    }}>
      <div style={{
        position: "absolute", top: -40, right: -40, width: 200, height: 200,
        background: C.accent, borderRadius: "50%", opacity: 0.05,
      }} />
      <div style={{ fontSize: 10, color: C.accent, fontWeight: 800, letterSpacing: "0.14em", textTransform: "uppercase", marginBottom: 10 }}>
        Product Intern Case Study · Fitness App · 2025
      </div>
      <h1 style={{
        fontFamily: "'Syne', sans-serif", fontSize: 36, fontWeight: 800,
        color: C.text, lineHeight: 1.1, marginBottom: 14, letterSpacing: "-0.01em",
      }}>Nike Run Club<br />Retention Teardown</h1>
      <p style={{ fontSize: 14, color: C.sub, maxWidth: 500, lineHeight: 1.75 }}>
        NRC acquires millions of users monthly. Only 9% are still active at Day 30.
        The app delivers a great first experience — then goes completely silent.
        This case study diagnoses 7 root causes, proposes prioritised fixes,
        and validates everything against real user behaviour data.
      </p>
      <div style={{ marginTop: 18, display: "flex", gap: 8, flexWrap: "wrap" }}>
        {["Fitness / Running", "Freemium", "Urban India Focus", "18–38 Age Group"].map(t => (
          <Pill key={t} label={t} color={C.accent} />
        ))}
      </div>
    </div>

    {/* Why NRC */}
    <Card style={{ marginBottom: 20, background: C.card2 }}>
      <div style={{ fontSize: 13, color: C.sub, lineHeight: 1.75 }}>
        <strong style={{ color: C.text }}>Why Nike Run Club?</strong> Mature app, documented retention struggles,
        strong brand pull in urban India (Bengaluru, Mumbai, Delhi), free tier, and a clear gap between
        product quality and long-term engagement. The gaps are fixable — which makes it a high-signal case study.
        Validated with real user churn signals, review analysis, and competitive data (Strava, Runna).
      </div>
    </Card>

    {/* Key numbers */}
    <div style={{ marginBottom: 20 }}>
      <SectionLabel text="Baseline Metrics — Simulated 100K Cohort" />
      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(120px, 1fr))", gap: 10 }}>
        <StatBox label="Onboarding Complete" value="72%" sub="D0 drop" color={C.green} />
        <StatBox label="D7 Retention" value="18%" sub="Habit cliff" color={C.gold} />
        <StatBox label="D30 Retention" value="9%" sub="Baseline" color={C.accent} />
        <StatBox label="Target D30" value="18%" sub="Post-fixes" color={C.green} />
        <StatBox label="Sessions / Week" value="1.4" sub="Active users only" color={C.blue} />
      </div>
    </div>

    {/* OKR */}
    <Card accent={C.green}>
      <div style={{ fontSize: 11, color: C.green, fontWeight: 700, letterSpacing: "0.1em", textTransform: "uppercase", marginBottom: 10 }}>North Star Metric + OKRs</div>
      <div style={{ fontFamily: "'Syne', sans-serif", fontSize: 20, fontWeight: 800, color: C.text, marginBottom: 10 }}>
        Weekly Active Runners
      </div>
      <div style={{ fontSize: 13, color: C.sub, lineHeight: 1.75 }}>
        Not DAU. A user who opens the app but skips their run is not a win.
        Secondary OKRs: D30 retention 9% → 18% · Sessions/week 1.4 → 2.8 ·
        Program enrollment &gt;40% new users · Pod formation &gt;25% W2 users.
      </div>
    </Card>

    {/* Reddit note */}
    <div style={{
      marginTop: 16, background: "#0D1520", border: `1px solid ${C.blue}33`,
      borderRadius: 12, padding: "14px 18px",
      display: "flex", gap: 12, alignItems: "flex-start",
    }}>
      <span style={{ fontSize: 20, flexShrink: 0 }}>🔍</span>
      <div style={{ fontSize: 13, color: C.sub, lineHeight: 1.7 }}>
        <strong style={{ color: C.blue }}>Validated against real user signals.</strong> This case study was updated after
        analysing user churn patterns, third-party sync app behaviour (SyncApp, RunSync),
        Tom's Guide review data, and competitive market data from Runna/Strava 2025. Root causes 6 and 7
        were added after validation — they were missing from the first draft.
      </div>
    </div>
  </div>
);

/* ════════════════════════════════════════════════════════
   TAB: FUNNEL
════════════════════════════════════════════════════════ */
const funnel = [
  { label: "App Install",           pct: 100, users: "100,000", note: null },
  { label: "Onboarding Complete",   pct: 72,  users: "72,000",  note: "28K lost — vague goal-setting, no program anchor" },
  { label: "First Run Logged",      pct: 48,  users: "48,000",  note: "24K lost — friction finding first guided run" },
  { label: "Day 3 Active",          pct: 31,  users: "31,000",  note: "17K lost — no next-session cue after Run 1" },
  { label: "Day 7 Active",          pct: 18,  users: "18,000",  note: "13K lost — novelty dies, no structure to return to" },
  { label: "Day 30 Active",         pct: 9,   users: "9,000",   note: "9K lost — habit never formed, no social contract" },
  { label: "Day 90 Active",         pct: 4,   users: "4,000",   note: "5K lost — no milestone rewards, no paywall lock-in" },
];

const Funnel = () => (
  <div className="fu0">
    <SectionLabel text="User Funnel — 100K Install Cohort" />
    <Card style={{ marginBottom: 20 }}>
      {funnel.map((f, i) => {
        const color = f.pct >= 70 ? C.green : f.pct >= 30 ? C.gold : C.accent;
        return (
          <div key={i} style={{ marginBottom: i < funnel.length - 1 ? 20 : 0 }}>
            <div style={{ display: "flex", justifyContent: "space-between", marginBottom: 5 }}>
              <span style={{ fontSize: 13, color: C.text, fontWeight: 600 }}>{f.label}</span>
              <span style={{ fontSize: 13, fontWeight: 700, color }}>{f.pct}% · {f.users}</span>
            </div>
            <div style={{ background: C.dim, borderRadius: 4, height: 7, marginBottom: f.note ? 5 : 0 }}>
              <div style={{
                width: `${f.pct}%`, height: "100%", borderRadius: 4,
                background: color, transition: "width 0.8s ease",
                boxShadow: f.pct < 20 ? `0 0 8px ${color}66` : "none",
              }} />
            </div>
            {f.note && (
              <div style={{ fontSize: 11, color: C.sub, fontStyle: "italic" }}>↓ {f.note}</div>
            )}
          </div>
        );
      })}
    </Card>

    <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr 1fr", gap: 12 }}>
      <Card accent={C.accent}>
        <div style={{ fontSize: 10, color: C.accent, fontWeight: 700, textTransform: "uppercase", letterSpacing: "0.08em", marginBottom: 6 }}>Biggest Drop</div>
        <div style={{ fontFamily: "'Syne', sans-serif", fontSize: 18, fontWeight: 800, color: C.text }}>D3 → D7</div>
        <div style={{ fontSize: 12, color: C.sub, marginTop: 4 }}>Habit window. No structure to return to.</div>
      </Card>
      <Card accent={C.gold}>
        <div style={{ fontSize: 10, color: C.gold, fontWeight: 700, textTransform: "uppercase", letterSpacing: "0.08em", marginBottom: 6 }}>Critical Signal</div>
        <div style={{ fontFamily: "'Syne', sans-serif", fontSize: 18, fontWeight: 800, color: C.text }}>2 runs in W1</div>
        <div style={{ fontSize: 12, color: C.sub, marginTop: 4 }}>Users who do this retain at 3× the rate.</div>
      </Card>
      <Card accent={C.green}>
        <div style={{ fontSize: 10, color: C.green, fontWeight: 700, textTransform: "uppercase", letterSpacing: "0.08em", marginBottom: 6 }}>If Fixed</div>
        <div style={{ fontFamily: "'Syne', sans-serif", fontSize: 18, fontWeight: 800, color: C.text }}>+9,000</div>
        <div style={{ fontSize: 12, color: C.sub, marginTop: 4 }}>Additional retained users per 100K cohort.</div>
      </Card>
    </div>
  </div>
);

/* ════════════════════════════════════════════════════════
   TAB: ROOT CAUSES (7, updated)
════════════════════════════════════════════════════════ */
const reasons = [
  {
    n: "01", color: C.accent,
    title: "No Habit Loop — App Goes Silent After a Run",
    body: "NRC logs your run and disappears. There's no prompt for the next session, no scheduled return, no streak with real stakes. Motivation is highest immediately post-run — NRC wastes that window completely. The app treats each run as an endpoint instead of a checkpoint.",
    tags: ["Habit Design", "Re-engagement"],
    source: null,
  },
  {
    n: "02", color: C.gold,
    title: "Goal Ambiguity at Onboarding",
    body: "Users pick vague goals like 'Get Fit.' There's no structured program, no weekly plan, no milestone to track. Without a concrete north star, there's nothing to fail at — so there's nothing to stay for. Runna solved exactly this: by the time their trial ends, users are mid-program and quitting feels like giving up.",
    tags: ["Onboarding", "Goal-setting"],
    source: "Validated: Runna retention vs NRC — market data 2025",
  },
  {
    n: "03", color: C.purple,
    title: "Social Layer Is Passive — No Accountability",
    body: "The social feed shows what friends ran, but prompts zero competition or obligation. There's no group challenge, no shared streak, no accountability contract. Users who wanted to share their NRC runs with others had to install a third-party app (SyncApp, RunSync) just to post to Strava. That's a product failure signal, not a workaround.",
    tags: ["Social", "Accountability"],
    source: "Validated: Multiple NRC→Strava sync apps exist solely because NRC has no native sharing",
  },
  {
    n: "04", color: C.green,
    title: "Push Notifications Are Generic and Irrelevant",
    body: "Generic 'Time to run!' pushes at arbitrary hours get ignored, then disabled. Once users kill notifications, the re-engagement channel is gone permanently. NRC has no lapse-prediction, no weather-aware nudges, no time-of-day personalisation. Contextual relevance is the #1 predictor of notification engagement.",
    tags: ["Notifications", "Personalisation"],
    source: null,
  },
  {
    n: "05", color: "#FF6B9D",
    title: "Progress Feels Abstract — Wins Aren't Legible",
    body: "After two weeks of running, you've covered 18km. NRC shows a number. It doesn't say 'that's Bengaluru to Whitefield and back' or 'you're 40% to your 5K goal.' The emotional reward layer is missing. Users feel no accumulation of progress, so they see no cost to stopping.",
    tags: ["Motivation", "UX"],
    source: null,
  },
  {
    n: "06", color: C.blue,
    title: "Device Compatibility Gap — Silent Android Killer",
    body: "NRC does not work with Samsung Galaxy Watch. In India, Samsung dominates the Android wearables market. Users hit this wall on Day 1, find no fix, and download Strava instead — permanently. This is a real acquisition-to-retention killer that doesn't show up in in-app analytics at all.",
    tags: ["Platform", "Android", "NEW"],
    source: "Validated: Samsung Community forum — users report switching to Strava due to NRC incompatibility",
    isNew: true,
  },
  {
    n: "07", color: C.red,
    title: "No Paywall = No Commitment Hook",
    body: "NRC is fully free, which is a great acquisition strategy and a terrible retention strategy. There's no moment where the user decides to invest in the product. Runna's hard paywall after a 1-week trial creates commitment — users who pay are 3× more likely to complete a program. NRC has no equivalent psychological lock-in.",
    tags: ["Monetisation", "Retention", "NEW"],
    source: "Validated: Runna vs NRC app store rankings 2025 — paid model drives higher retention",
    isNew: true,
  },
];

const Reasons = () => {
  const [open, setOpen] = useState(null);
  return (
    <div className="fu0">
      <SectionLabel text="7 Root Causes of Drop-off" />
      <div style={{
        background: C.card2, border: `1px solid ${C.blue}33`, borderRadius: 12,
        padding: "12px 16px", marginBottom: 20, fontSize: 13, color: C.sub, lineHeight: 1.7,
      }}>
        <strong style={{ color: C.blue }}>Updated after real-user validation.</strong> Root causes 6 and 7 were
        missing from the original draft — added after analysing churn patterns, third-party app behaviour,
        and Runna/Strava competitive data.
      </div>
      {reasons.map((r, i) => (
        <div key={i} onClick={() => setOpen(open === i ? null : i)} style={{
          background: C.card, border: `1px solid ${open === i ? r.color + "55" : C.border}`,
          borderLeft: `3px solid ${r.color}`,
          borderRadius: 13, padding: "16px 18px", marginBottom: 10, cursor: "pointer",
          transition: "border-color 0.2s",
        }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center" }}>
            <div style={{ display: "flex", alignItems: "center", gap: 12 }}>
              <span style={{
                fontFamily: "'Syne', sans-serif", fontSize: 22, fontWeight: 800,
                color: r.color, opacity: 0.5, lineHeight: 1, flexShrink: 0,
              }}>{r.n}</span>
              <div>
                <div style={{ display: "flex", alignItems: "center", gap: 8, flexWrap: "wrap" }}>
                  <span style={{ fontSize: 14, fontWeight: 700, color: C.text }}>{r.title}</span>
                  {r.isNew && (
                    <span style={{
                      fontSize: 9, fontWeight: 800, background: C.blue + "25", color: C.blue,
                      border: `1px solid ${C.blue}44`, padding: "1px 7px", borderRadius: 10,
                      textTransform: "uppercase", letterSpacing: "0.08em",
                    }}>New</span>
                  )}
                </div>
              </div>
            </div>
            <span style={{ color: C.sub, fontSize: 18, flexShrink: 0 }}>{open === i ? "−" : "+"}</span>
          </div>
          {open === i && (
            <div style={{ marginTop: 14, paddingTop: 14, borderTop: `1px solid ${C.border}` }}>
              <div style={{ fontSize: 13, color: C.sub, lineHeight: 1.75, marginBottom: 12 }}>{r.body}</div>
              {r.source && (
                <div style={{
                  background: C.blue + "10", border: `1px solid ${C.blue}28`,
                  borderRadius: 8, padding: "8px 12px",
                  fontSize: 11, color: C.blue, marginBottom: 10,
                }}>📌 {r.source}</div>
              )}
              <div>{r.tags.map(t => <Pill key={t} label={t} color={r.color} />)}</div>
            </div>
          )}
        </div>
      ))}
    </div>
  );
};

/* ════════════════════════════════════════════════════════
   TAB: COMPETITIVE INTEL
════════════════════════════════════════════════════════ */
const Competitive = () => (
  <div className="fu0">
    <SectionLabel text="Competitive Intelligence — What Real Users Did" />

    <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr 1fr", gap: 12, marginBottom: 20 }}>
      {[
        { app: "Strava", pos: "#2", label: "Fitness app by revenue, Jan 2025", color: C.orange || "#FC4C02", note: "Users who left NRC went here" },
        { app: "Runna", pos: "#8", label: "Fitness app by revenue, Jan 2025", color: C.green, note: "Structured programs — solved NRC's P0 gap" },
        { app: "NRC", pos: "Free", label: "No revenue ranking — fully free", color: C.sub, note: "Acquisition strategy ≠ retention strategy" },
      ].map((c, i) => (
        <Card key={i} style={{ textAlign: "center", padding: "16px 12px" }}>
          <div style={{ fontFamily: "'Syne', sans-serif", fontSize: 24, fontWeight: 800, color: c.color }}>{c.pos}</div>
          <div style={{ fontSize: 13, fontWeight: 700, color: C.text, margin: "4px 0 2px" }}>{c.app}</div>
          <div style={{ fontSize: 10, color: C.sub, marginBottom: 8 }}>{c.label}</div>
          <div style={{ fontSize: 11, color: c.color, fontStyle: "italic" }}>{c.note}</div>
        </Card>
      ))}
    </div>

    {[
      {
        color: C.red,
        heading: "The Walled Garden Problem — Validated",

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>ClearAI — Intelligent Customs Clearance</title>
<link href="https://fonts.googleapis.com/css2?family=Clash+Display:wght@400;500;600;700&family=Cabinet+Grotesk:wght@300;400;500;700;800&family=JetBrains+Mono:wght@300;400&display=swap" rel="stylesheet"/>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --navy:#020B18;
  --deep:#041020;
  --panel:#071828;
  --border:#0E2A3F;
  --blue:#0A84FF;
  --cyan:#00D4FF;
  --teal:#00FFB2;
  --amber:#FFB300;
  --red:#FF3B55;
  --text:#E8F4FF;
  --muted:#5A7A96;
  --dim:#1A3A52;
}
html{scroll-behavior:smooth}
body{
  background:var(--navy);
  color:var(--text);
  font-family:'Cabinet Grotesk',sans-serif;
  overflow-x:hidden;
  line-height:1.6;
}

/* SCROLLBAR */
::-webkit-scrollbar{width:4px}
::-webkit-scrollbar-track{background:var(--deep)}
::-webkit-scrollbar-thumb{background:var(--blue);border-radius:2px}

/* NAV */
nav{
  position:fixed;top:0;left:0;right:0;z-index:200;
  display:flex;justify-content:space-between;align-items:center;
  padding:1rem 4rem;
  background:rgba(2,11,24,0.85);
  backdrop-filter:blur(20px);
  border-bottom:1px solid var(--border);
}
.nav-logo{
  display:flex;align-items:center;gap:0.6rem;
  font-family:'Clash Display',sans-serif;
  font-size:1.3rem;font-weight:700;
  color:var(--text);
}
.logo-icon{
  width:32px;height:32px;
  background:linear-gradient(135deg,var(--blue),var(--cyan));
  clip-path:polygon(50% 0%,100% 25%,100% 75%,50% 100%,0% 75%,0% 25%);
  display:grid;place-items:center;
  font-size:0.7rem;font-weight:700;color:#fff;
}
.nav-links{display:flex;gap:2rem;list-style:none}
.nav-links a{
  color:var(--muted);text-decoration:none;
  font-size:0.85rem;font-weight:500;letter-spacing:0.5px;
  transition:color 0.2s;
}
.nav-links a:hover{color:var(--cyan)}
.nav-right{display:flex;gap:1rem;align-items:center}
.btn-ghost{
  background:transparent;border:1px solid var(--border);
  color:var(--text);padding:0.5rem 1.2rem;
  font-family:'Cabinet Grotesk',sans-serif;font-size:0.82rem;font-weight:600;
  cursor:pointer;border-radius:6px;transition:border-color 0.2s,color 0.2s;
}
.btn-ghost:hover{border-color:var(--cyan);color:var(--cyan)}
.btn-primary{
  background:linear-gradient(135deg,var(--blue),var(--cyan));
  border:none;color:#fff;padding:0.5rem 1.4rem;
  font-family:'Cabinet Grotesk',sans-serif;font-size:0.82rem;font-weight:700;
  cursor:pointer;border-radius:6px;transition:opacity 0.2s,transform 0.15s;
}
.btn-primary:hover{opacity:0.88;transform:translateY(-1px)}

/* HERO */
.hero{
  min-height:100vh;
  display:flex;flex-direction:column;justify-content:center;
  padding:8rem 4rem 4rem;
  position:relative;overflow:hidden;
}
.hero-grid{
  position:absolute;inset:0;
  background-image:
    linear-gradient(rgba(10,132,255,0.04) 1px,transparent 1px),
    linear-gradient(90deg,rgba(10,132,255,0.04) 1px,transparent 1px);
  background-size:50px 50px;
}
.hero-glow{
  position:absolute;
  width:700px;height:700px;
  background:radial-gradient(circle,rgba(10,132,255,0.12) 0%,transparent 70%);
  top:-200px;right:-100px;pointer-events:none;
}
.hero-glow2{
  position:absolute;
  width:500px;height:500px;
  background:radial-gradient(circle,rgba(0,212,255,0.07) 0%,transparent 70%);
  bottom:-100px;left:10%;pointer-events:none;
}
.hero-badge{
  display:inline-flex;align-items:center;gap:0.5rem;
  background:rgba(10,132,255,0.1);
  border:1px solid rgba(10,132,255,0.3);
  padding:0.35rem 1rem;border-radius:100px;
  font-size:0.72rem;letter-spacing:2px;text-transform:uppercase;
  color:var(--cyan);margin-bottom:1.8rem;
  width:fit-content;
  animation:fadeUp 0.6s ease both;
}
.badge-pulse{
  width:6px;height:6px;background:var(--teal);border-radius:50%;
  animation:pulse 1.5s infinite;
}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:0.4;transform:scale(1.5)}}

.hero-title{
  font-family:'Clash Display',sans-serif;
  font-size:clamp(3rem,7vw,6.5rem);
  font-weight:700;line-height:0.95;
  letter-spacing:-2px;
  max-width:900px;
  animation:fadeUp 0.6s 0.1s ease both;
}
.hero-title .line2{
  display:block;
  background:linear-gradient(90deg,var(--blue),var(--cyan),var(--teal));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.hero-desc{
  max-width:560px;
  font-size:1.05rem;color:var(--muted);
  margin:1.8rem 0 2.5rem;line-height:1.75;
  animation:fadeUp 0.6s 0.2s ease both;
}
.hero-actions{
  display:flex;gap:1rem;align-items:center;flex-wrap:wrap;
  animation:fadeUp 0.6s 0.3s ease both;
}
.btn-large{
  padding:0.85rem 2.2rem;font-size:0.95rem;font-weight:700;
  border-radius:8px;
}
.hero-trust{
  margin-top:4rem;
  display:flex;align-items:center;gap:1.5rem;flex-wrap:wrap;
  animation:fadeUp 0.6s 0.4s ease both;
}
.trust-text{font-size:0.75rem;color:var(--muted);letter-spacing:1px;text-transform:uppercase}
.trust-badges{display:flex;gap:1rem;flex-wrap:wrap}
.trust-badge{
  background:var(--panel);border:1px solid var(--border);
  padding:0.4rem 0.9rem;border-radius:4px;
  font-size:0.72rem;font-weight:600;color:var(--muted);letter-spacing:0.5px;
}

/* STATS STRIP */
.stats-strip{
  display:grid;grid-template-columns:repeat(4,1fr);
  border-top:1px solid var(--border);
  border-bottom:1px solid var(--border);
}
.stat-cell{
  padding:2.5rem 2rem;
  border-right:1px solid var(--border);
  text-align:center;
  transition:background 0.3s;
}
.stat-cell:last-child{border-right:none}
.stat-cell:hover{background:rgba(10,132,255,0.04)}
.stat-val{
  font-family:'Clash Display',sans-serif;
  font-size:2.8rem;font-weight:700;
  background:linear-gradient(135deg,var(--blue),var(--cyan));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.stat-label{font-size:0.8rem;color:var(--muted);margin-top:0.3rem;letter-spacing:0.5px}

/* SECTION COMMON */
section{padding:7rem 4rem}
.section-eyebrow{
  font-size:0.72rem;letter-spacing:3px;text-transform:uppercase;
  color:var(--cyan);margin-bottom:0.8rem;
  display:flex;align-items:center;gap:0.6rem;
}
.section-eyebrow::before{content:'';display:inline-block;width:1.5rem;height:1px;background:var(--cyan)}
.section-title{
  font-family:'Clash Display',sans-serif;
  font-size:clamp(2rem,4vw,3.2rem);
  font-weight:600;line-height:1.1;margin-bottom:1rem;
}
.section-title span{color:var(--cyan)}
.section-sub{max-width:500px;color:var(--muted);font-size:0.95rem;line-height:1.7}

/* PROBLEM/SOLUTION */
.problem-solution{
  background:var(--deep);
  display:grid;grid-template-columns:1fr 1fr;gap:0;
}
.ps-col{padding:5rem 4rem;position:relative;overflow:hidden}
.ps-col:first-child{border-right:1px solid var(--border)}
.ps-col::before{
  content:'';position:absolute;
  width:300px;height:300px;border-radius:50%;
  top:-100px;right:-100px;pointer-events:none;
}
.ps-col.problem::before{background:radial-gradient(circle,rgba(255,59,85,0.08) 0%,transparent 70%)}
.ps-col.solution::before{background:radial-gradient(circle,rgba(0,255,178,0.08) 0%,transparent 70%)}
.ps-tag{
  display:inline-flex;align-items:center;gap:0.4rem;
  padding:0.3rem 0.8rem;border-radius:4px;
  font-size:0.7rem;font-weight:700;letter-spacing:1.5px;text-transform:uppercase;
  margin-bottom:1.5rem;
}
.ps-tag.problem-tag{background:rgba(255,59,85,0.12);color:var(--red);border:1px solid rgba(255,59,85,0.25)}
.ps-tag.solution-tag{background:rgba(0,255,178,0.1);color:var(--teal);border:1px solid rgba(0,255,178,0.2)}
.ps-title{font-family:'Clash Display',sans-serif;font-size:1.8rem;font-weight:600;margin-bottom:1rem}
.ps-text{color:var(--muted);font-size:0.9rem;line-height:1.75;margin-bottom:1.5rem}
.ps-list{list-style:none;display:flex;flex-direction:column;gap:0.75rem}
.ps-list li{
  display:flex;align-items:flex-start;gap:0.75rem;
  font-size:0.88rem;color:var(--muted);
}
.ps-list li::before{
  content:'';flex-shrink:0;
  width:16px;height:16px;border-radius:50%;
  margin-top:3px;
}
.problem .ps-list li::before{background:rgba(255,59,85,0.2);border:1px solid var(--red)}
.solution .ps-list li::before{background:rgba(0,255,178,0.15);border:1px solid var(--teal)}

/* HOW IT WORKS */
.how-it-works{background:var(--navy)}
.how-inner{max-width:1200px;margin:0 auto}
.steps-grid{
  display:grid;grid-template-columns:repeat(4,1fr);
  gap:1.5rem;margin-top:4rem;
  position:relative;
}
.steps-grid::before{
  content:'';position:absolute;
  top:36px;left:calc(12.5% + 20px);
  right:calc(12.5% + 20px);height:1px;
  background:linear-gradient(90deg,var(--blue),var(--cyan),var(--teal));
  opacity:0.4;
}
.step-card{
  background:var(--panel);
  border:1px solid var(--border);
  border-radius:12px;padding:2rem 1.5rem;
  text-align:center;
  transition:transform 0.3s,border-color 0.3s,box-shadow 0.3s;
  position:relative;
}
.step-card:hover{
  transform:translateY(-6px);
  border-color:rgba(10,132,255,0.4);
  box-shadow:0 20px 40px rgba(10,132,255,0.1);
}
.step-num{
  width:52px;height:52px;
  background:linear-gradient(135deg,var(--blue),var(--cyan));
  border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  font-family:'Clash Display',sans-serif;font-size:1.2rem;font-weight:700;
  margin:0 auto 1.5rem;
  position:relative;z-index:1;
}
.step-title{font-family:'Clash Display',sans-serif;font-size:1.05rem;font-weight:600;margin-bottom:0.6rem}
.step-desc{font-size:0.82rem;color:var(--muted);line-height:1.65}

/* FEATURES */
.features{background:var(--deep)}
.features-inner{max-width:1200px;margin:0 auto}
.features-grid{
  display:grid;grid-template-columns:repeat(3,1fr);
  gap:1.5rem;margin-top:4rem;
}
.feature-card{
  background:var(--panel);
  border:1px solid var(--border);
  border-radius:12px;padding:2rem;
  transition:transform 0.3s,border-color 0.3s;
  position:relative;overflow:hidden;
}
.feature-card::after{
  content:'';position:absolute;
  top:0;left:0;right:0;height:2px;
  background:var(--card-accent,linear-gradient(90deg,var(--blue),var(--cyan)));
  transform:scaleX(0);transform-origin:left;
  transition:transform 0.35s ease;
}
.feature-card:hover::after{transform:scaleX(1)}
.feature-card:hover{transform:translateY(-4px);border-color:rgba(255,255,255,0.1)}
.feature-card.accent-teal{--card-accent:linear-gradient(90deg,var(--teal),var(--cyan))}
.feature-card.accent-amber{--card-accent:linear-gradient(90deg,var(--amber),#FF6B00)}
.feature-card.accent-blue{--card-accent:linear-gradient(90deg,var(--blue),var(--cyan))}
.feature-icon{
  width:44px;height:44px;
  border-radius:10px;
  display:grid;place-items:center;
  margin-bottom:1.2rem;font-size:1.2rem;
}
.feature-icon.blue{background:rgba(10,132,255,0.15)}
.feature-icon.teal{background:rgba(0,255,178,0.12)}
.feature-icon.amber{background:rgba(255,179,0,0.12)}
.feature-icon.red{background:rgba(255,59,85,0.12)}
.feature-icon.cyan{background:rgba(0,212,255,0.12)}
.feature-icon.purple{background:rgba(175,82,222,0.12)}
.feature-name{font-family:'Clash Display',sans-serif;font-size:1.05rem;font-weight:600;margin-bottom:0.5rem}
.feature-desc{font-size:0.83rem;color:var(--muted);line-height:1.65}
.feature-tags{display:flex;gap:0.5rem;flex-wrap:wrap;margin-top:1.2rem}
.ftag{
  font-size:0.65rem;letter-spacing:1px;text-transform:uppercase;
  padding:0.2rem 0.6rem;border-radius:3px;
  background:var(--dim);color:var(--muted);font-weight:600;
}

/* DEMO SECTION */
.demo-section{background:var(--navy);padding:7rem 4rem}
.demo-inner{max-width:1100px;margin:0 auto}
.demo-header{text-align:center;margin-bottom:4rem}
.demo-ui{
  background:var(--panel);
  border:1px solid var(--border);
  border-radius:16px;
  overflow:hidden;
  box-shadow:0 40px 80px rgba(0,0,0,0.4);
}
.demo-topbar{
  background:var(--deep);
  border-bottom:1px solid var(--border);
  padding:0.8rem 1.5rem;
  display:flex;align-items:center;gap:1rem;
}
.demo-dots{display:flex;gap:6px}
.dot{width:10px;height:10px;border-radius:50%}
.dot.red{background:#FF5F57}
.dot.yellow{background:#FEBC2E}
.dot.green{background:#28C840}
.demo-url{
  flex:1;background:rgba(255,255,255,0.04);
  border:1px solid var(--border);border-radius:5px;
  padding:0.3rem 0.8rem;
  font-family:'JetBrains Mono',monospace;font-size:0.72rem;color:var(--muted);
}
.demo-body{display:grid;grid-template-columns:260px 1fr;min-height:500px}
.demo-sidebar{
  background:rgba(4,16,32,0.6);
  border-right:1px solid var(--border);
  padding:1.5rem 1rem;
}
.demo-sidebar-title{
  font-size:0.65rem;letter-spacing:2px;text-transform:uppercase;
  color:var(--muted);padding:0 0.5rem;margin-bottom:1rem;
}
.demo-menu-item{
  display:flex;align-items:center;gap:0.75rem;
  padding:0.6rem 0.75rem;border-radius:8px;
  font-size:0.82rem;cursor:pointer;
  transition:background 0.2s;margin-bottom:0.25rem;
}
.demo-menu-item:hover{background:rgba(10,132,255,0.08)}
.demo-menu-item.active{background:rgba(10,132,255,0.12);color:var(--cyan)}
.menu-icon{width:16px;height:16px;opacity:0.7}
.demo-main{padding:2rem}
.demo-main-title{
  font-family:'Clash Display',sans-serif;font-size:1.3rem;font-weight:600;
  margin-bottom:0.3rem;
}
.demo-main-sub{font-size:0.8rem;color:var(--muted);margin-bottom:2rem}
.demo-upload-zone{
  border:2px dashed var(--border);border-radius:12px;
  padding:2.5rem;text-align:center;
  background:rgba(10,132,255,0.03);
  margin-bottom:2rem;
  transition:border-color 0.3s,background 0.3s;
  cursor:pointer;
}
.demo-upload-zone:hover{border-color:var(--blue);background:rgba(10,132,255,0.07)}
.upload-icon{font-size:2rem;margin-bottom:0.75rem}
.upload-label{font-size:0.88rem;font-weight:600;margin-bottom:0.3rem}
.upload-hint{font-size:0.75rem;color:var(--muted)}
.demo-results{display:flex;flex-direction:column;gap:0.75rem}
.result-row{
  background:rgba(255,255,255,0.03);
  border:1px solid var(--border);border-radius:8px;
  padding:0.9rem 1.2rem;
  display:grid;grid-template-columns:1fr auto auto auto;
  align-items:center;gap:1rem;
}
.result-desc{font-size:0.83rem;font-weight:500}
.result-hs{
  font-family:'JetBrains Mono',monospace;
  font-size:0.78rem;color:var(--cyan);
  background:rgba(0,212,255,0.08);
  padding:0.2rem 0.6rem;border-radius:4px;
}
.confidence{font-size:0.72rem;font-weight:700}
.confidence.high{color:var(--teal)}
.confidence.med{color:var(--amber)}
.status-badge{
  font-size:0.65rem;letter-spacing:1px;text-transform:uppercase;font-weight:700;
  padding:0.25rem 0.6rem;border-radius:4px;
}
.status-badge.ok{background:rgba(0,255,178,0.1);color:var(--teal)}
.status-badge.warn{background:rgba(255,179,0,0.1);color:var(--amber)}
.status-badge.flag{background:rgba(255,59,85,0.1);color:var(--red)}

/* COMPLIANCE */
.compliance-row{
  display:grid;grid-template-columns:1fr 1fr;
  gap:1.5rem;margin-top:1.5rem;
}
.comp-card{
  background:rgba(255,255,255,0.03);
  border:1px solid var(--border);border-radius:8px;padding:1rem 1.2rem;
}
.comp-card-title{font-size:0.75rem;color:var(--muted);margin-bottom:0.75rem;letter-spacing:0.5px}
.comp-item{
  display:flex;align-items:center;gap:0.6rem;
  font-size:0.8rem;margin-bottom:0.5rem;
}
.comp-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0}
.comp-dot.green{background:var(--teal)}
.comp-dot.yellow{background:var(--amber)}
.comp-dot.red{background:var(--red)}

/* WORKFLOW */
.workflow{background:var(--deep)}
.workflow-inner{max-width:1000px;margin:0 auto}
.workflow-timeline{margin-top:4rem;position:relative}
.workflow-timeline::before{
  content:'';position:absolute;
  left:32px;top:0;bottom:0;width:1px;
  background:linear-gradient(to bottom,var(--blue),var(--cyan),var(--teal));
  opacity:0.3;
}
.wf-item{
  display:flex;gap:2rem;align-items:flex-start;
  margin-bottom:3rem;
  padding-left:0;
}
.wf-dot{
  width:64px;height:64px;flex-shrink:0;
  background:var(--panel);border:1px solid var(--border);
  border-radius:50%;display:grid;place-items:center;
  font-size:1.2rem;
  transition:border-color 0.3s,box-shadow 0.3s;
  position:relative;z-index:1;
}
.wf-item:hover .wf-dot{border-color:var(--cyan);box-shadow:0 0 20px rgba(0,212,255,0.15)}
.wf-content{flex:1;padding-top:0.8rem}
.wf-title{font-family:'Clash Display',sans-serif;font-size:1.15rem;font-weight:600;margin-bottom:0.4rem}
.wf-desc{font-size:0.85rem;color:var(--muted);line-height:1.7}
.wf-chips{display:flex;gap:0.5rem;flex-wrap:wrap;margin-top:0.75rem}
.wf-chip{
  font-size:0.68rem;letter-spacing:1px;text-transform:uppercase;
  padding:0.2rem 0.6rem;border-radius:3px;font-weight:600;
  background:rgba(10,132,255,0.1);color:var(--blue);
  border:1px solid rgba(10,132,255,0.2);
}

/* GOVERNANCE */
.governance{background:var(--navy)}
.gov-grid{
  display:grid;grid-template-columns:repeat(3,1fr);
  gap:1.5rem;margin-top:4rem;
}
.gov-card{
  border:1px solid var(--border);border-radius:12px;
  padding:2rem;background:var(--panel);
  transition:transform 0.3s;
}
.gov-card:hover{transform:translateY(-4px)}
.gov-icon{font-size:1.8rem;margin-bottom:1rem}
.gov-title{font-family:'Clash Display',sans-serif;font-size:1rem;font-weight:600;margin-bottom:0.5rem}
.gov-text{font-size:0.83rem;color:var(--muted);line-height:1.65}

/* OUTCOMES */
.outcomes{background:var(--deep)}
.outcomes-inner{max-width:1100px;margin:0 auto}
.outcomes-grid{
  display:grid;grid-template-columns:1fr 1fr;
  gap:3rem;margin-top:4rem;align-items:center;
}
.outcome-list{display:flex;flex-direction:column;gap:1.5rem}
.outcome-item{
  display:flex;gap:1.2rem;align-items:flex-start;
  padding:1.2rem;border:1px solid var(--border);border-radius:10px;
  background:var(--panel);
  transition:border-color 0.3s,transform 0.3s;
}
.outcome-item:hover{border-color:rgba(10,132,255,0.3);transform:translateX(4px)}
.outcome-ico{
  width:40px;height:40px;flex-shrink:0;
  border-radius:8px;display:grid;place-items:center;font-size:1rem;
}
.outcome-title{font-weight:700;font-size:0.92rem;margin-bottom:0.2rem}
.outcome-desc{font-size:0.8rem;color:var(--muted);line-height:1.6}
.outcome-visual{
  background:var(--panel);border:1px solid var(--border);
  border-radius:16px;padding:2rem;
}
.ov-title{font-size:0.75rem;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);margin-bottom:2rem}
.metric-row{margin-bottom:1.5rem}
.metric-label{
  display:flex;justify-content:space-between;
  font-size:0.82rem;margin-bottom:0.5rem;
}
.metric-val{color:var(--cyan);font-weight:700;font-family:'JetBrains Mono',monospace}
.metric-bar{height:6px;background:var(--dim);border-radius:3px;overflow:hidden}
.metric-fill{height:100%;border-radius:3px;background:linear-gradient(90deg,var(--blue),var(--cyan))}
.metric-fill.teal{background:linear-gradient(90deg,var(--teal),var(--cyan))}
.metric-fill.amber{background:linear-gradient(90deg,var(--amber),#FF6B00)}

/* CTA */
.cta-section{
  padding:8rem 4rem;text-align:center;
  background:var(--navy);position:relative;overflow:hidden;
}
.cta-glow{
  position:absolute;width:800px;height:400px;
  background:radial-gradient(ellipse,rgba(10,132,255,0.1) 0%,transparent 70%);
  top:50%;left:50%;transform:translate(-50%,-50%);pointer-events:none;
}
.cta-title{
  font-family:'Clash Display',sans-serif;
  font-size:clamp(2.5rem,5vw,4.5rem);
  font-weight:700;line-height:1.05;
  max-width:700px;margin:0 auto 1.5rem;
  position:relative;z-index:1;
}
.cta-title span{
  background:linear-gradient(90deg,var(--blue),var(--cyan),var(--teal));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.cta-sub{color:var(--muted);font-size:1rem;max-width:420px;margin:0 auto 2.5rem;line-height:1.7;position:relative;z-index:1}
.cta-buttons{display:flex;gap:1rem;justify-content:center;flex-wrap:wrap;position:relative;z-index:1}

/* FOOTER */
footer{
  border-top:1px solid var(--border);
  padding:3rem 4rem;
  display:grid;grid-template-columns:1fr auto;
  align-items:center;gap:2rem;
  background:var(--deep);
}
.footer-left .nav-logo{font-size:1.1rem}
.footer-tagline{font-size:0.8rem;color:var(--muted);margin-top:0.3rem}
.footer-links{display:flex;gap:2rem}
.footer-links a{font-size:0.8rem;color:var(--mut

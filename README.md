[GetPaid.html](https://github.com/user-attachments/files/25899853/GetPaid.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DataVault — The AI Data Marketplace on Base</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Mono:wght@300;400;500&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

:root {
  --black: #080809;
  --off-white: #f0ede8;
  --white: #fafaf8;
  --green: #00e896;
  --green-dark: #00b872;
  --mid: #5a5f6b;
  --light: #b8bcc7;
  --border: #e0ddd8;
  --border-dark: #1a1d22;
  --display: 'Bebas Neue', sans-serif;
  --mono: 'DM Mono', monospace;
  --body: 'DM Sans', sans-serif;
}

html { scroll-behavior: smooth; }

body {
  background: var(--white);
  color: var(--black);
  font-family: var(--body);
  font-size: 15px;
  line-height: 1.6;
  overflow-x: hidden;
  cursor: none;
}

/* CUSTOM CURSOR */
.cursor {
  position: fixed;
  top: 0; left: 0;
  width: 8px; height: 8px;
  background: var(--green);
  pointer-events: none;
  z-index: 9999;
  transition: transform 0.1s;
  mix-blend-mode: multiply;
}

.cursor-ring {
  position: fixed;
  top: 0; left: 0;
  width: 36px; height: 36px;
  border: 1px solid var(--black);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9998;
  transition: transform 0.18s ease, width 0.2s, height 0.2s, border-color 0.2s;
  transform: translate(-14px, -14px);
}

.cursor-ring.hover {
  width: 56px; height: 56px;
  transform: translate(-24px, -24px);
  border-color: var(--green);
}

/* NAV */
nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 40px;
  background: rgba(250,250,248,0.92);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border);
}

.nav-logo {
  display: flex;
  align-items: center;
  gap: 10px;
  text-decoration: none;
}

.nav-logo-mark {
  width: 26px; height: 26px;
  background: var(--black);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--mono);
  font-size: 9px;
  font-weight: 500;
  color: var(--green);
  letter-spacing: 0.05em;
}

.nav-logo-name {
  font-family: var(--mono);
  font-size: 12px;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--black);
}

.nav-links {
  display: flex;
  gap: 32px;
  list-style: none;
}

.nav-links a {
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--mid);
  text-decoration: none;
  transition: color 0.15s;
}

.nav-links a:hover { color: var(--black); }

.nav-ctas {
  display: flex;
  gap: 10px;
  align-items: center;
}

.btn {
  font-family: var(--mono);
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  padding: 9px 20px;
  border: none;
  cursor: none;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  gap: 6px;
  transition: all 0.15s;
}

.btn-outline {
  background: transparent;
  border: 1px solid var(--black);
  color: var(--black);
}

.btn-outline:hover {
  background: var(--black);
  color: var(--white);
}

.btn-solid {
  background: var(--black);
  color: var(--white);
}

.btn-solid:hover {
  background: var(--green);
  color: var(--black);
}

.btn-green {
  background: var(--green);
  color: var(--black);
}

.btn-green:hover {
  background: var(--green-dark);
}

/* SECTIONS */
section { overflow: hidden; }

/* ── HERO ── */
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  padding: 0 40px 60px;
  position: relative;
  border-bottom: 1px solid var(--border);
}

.hero-bg-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: var(--display);
  font-size: clamp(200px, 28vw, 420px);
  color: transparent;
  -webkit-text-stroke: 1px var(--border);
  white-space: nowrap;
  pointer-events: none;
  user-select: none;
  letter-spacing: -0.02em;
  animation: fadeIn 1.2s ease both;
}

.hero-eyebrow {
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--mid);
  margin-bottom: 20px;
  display: flex;
  align-items: center;
  gap: 14px;
  animation: slideUp 0.8s 0.2s ease both;
}

.hero-eyebrow::before {
  content: '';
  display: inline-block;
  width: 28px;
  height: 1px;
  background: var(--green);
}

.hero-headline {
  font-family: var(--display);
  font-size: clamp(72px, 10vw, 152px);
  line-height: 0.92;
  letter-spacing: -0.01em;
  color: var(--black);
  animation: slideUp 0.8s 0.35s ease both;
  position: relative;
  z-index: 2;
}

.hero-headline .accent {
  color: var(--green);
  display: inline-block;
}

.hero-bottom {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  margin-top: 48px;
  animation: slideUp 0.8s 0.5s ease both;
}

.hero-desc {
  max-width: 400px;
  font-size: 16px;
  font-weight: 300;
  color: var(--mid);
  line-height: 1.7;
}

.hero-actions {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 12px;
}

.hero-stat-row {
  display: flex;
  gap: 40px;
}

.hero-stat {
  text-align: right;
}

.hero-stat-num {
  font-family: var(--display);
  font-size: 36px;
  color: var(--black);
  line-height: 1;
}

.hero-stat-label {
  font-family: var(--mono);
  font-size: 9px;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--light);
  margin-top: 3px;
}

/* CHAIN PILL */
.chain-pill {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 4px 10px;
  border: 1px solid var(--border);
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--mid);
  background: var(--white);
}

.chain-dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  background: var(--green);
  animation: pulse 2s infinite;
}

@keyframes pulse { 0%,100%{opacity:1;} 50%{opacity:0.3;} }

/* ── TICKER ── */
.ticker-wrap {
  background: var(--black);
  padding: 14px 0;
  overflow: hidden;
  white-space: nowrap;
}

.ticker-inner {
  display: inline-flex;
  gap: 0;
  animation: ticker 28s linear infinite;
}

.ticker-item {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 0 32px;
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: #3a3f4a;
}

.ticker-item .t-val {
  color: var(--green);
  font-weight: 500;
}

.ticker-sep {
  color: #1e2229;
  font-size: 16px;
}

@keyframes ticker { 0%{transform:translateX(0);} 100%{transform:translateX(-50%);} }

/* ── HOW IT WORKS ── */
.how {
  display: grid;
  grid-template-columns: 1fr 1fr;
  border-bottom: 1px solid var(--border);
}

.how-side {
  padding: 80px 60px;
}

.how-side:first-child {
  border-right: 1px solid var(--border);
}

.side-label {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--mid);
  margin-bottom: 32px;
  display: flex;
  align-items: center;
  gap: 12px;
}

.side-label::before {
  content: '';
  display: inline-block;
  width: 20px;
  height: 1px;
  background: var(--green);
}

.side-headline {
  font-family: var(--display);
  font-size: clamp(48px, 5vw, 80px);
  line-height: 0.95;
  color: var(--black);
  margin-bottom: 28px;
  letter-spacing: -0.01em;
}

.side-body {
  font-size: 15px;
  font-weight: 300;
  color: var(--mid);
  line-height: 1.8;
  margin-bottom: 40px;
  max-width: 380px;
}

.steps {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.step {
  display: grid;
  grid-template-columns: 48px 1fr;
  gap: 16px;
  padding: 20px 0;
  border-top: 1px solid var(--border);
  align-items: start;
}

.step:last-child { border-bottom: 1px solid var(--border); }

.step-num {
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 0.1em;
  color: var(--light);
  padding-top: 2px;
}

.step-title {
  font-size: 14px;
  font-weight: 500;
  color: var(--black);
  margin-bottom: 4px;
}

.step-desc {
  font-size: 13px;
  font-weight: 300;
  color: var(--mid);
  line-height: 1.6;
}

/* ── STATS STRIP ── */
.stats-strip {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  border-bottom: 1px solid var(--border);
}

.stat-block {
  padding: 56px 48px;
  border-right: 1px solid var(--border);
  position: relative;
  overflow: hidden;
}

.stat-block:last-child { border-right: none; }

.stat-block::after {
  content: '';
  position: absolute;
  bottom: 0; left: 0;
  width: 0; height: 2px;
  background: var(--green);
  transition: width 0.4s ease;
}

.stat-block:hover::after { width: 100%; }

.stat-num {
  font-family: var(--display);
  font-size: clamp(52px, 5vw, 80px);
  color: var(--black);
  line-height: 1;
  margin-bottom: 8px;
  letter-spacing: -0.02em;
}

.stat-label {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--light);
}

.stat-sub {
  font-size: 13px;
  font-weight: 300;
  color: var(--mid);
  margin-top: 8px;
  line-height: 1.5;
}

/* ── DATA TYPES ── */
.datatypes {
  padding: 80px 40px;
  border-bottom: 1px solid var(--border);
}

.section-eyebrow {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--mid);
  margin-bottom: 48px;
  display: flex;
  align-items: center;
  gap: 14px;
}

.section-eyebrow::before {
  content: '';
  display: inline-block;
  width: 28px;
  height: 1px;
  background: var(--green);
}

.datatypes-header {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  margin-bottom: 48px;
}

.datatypes-title {
  font-family: var(--display);
  font-size: clamp(48px, 6vw, 96px);
  line-height: 0.92;
  color: var(--black);
  letter-spacing: -0.01em;
}

.datatypes-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  border: 1px solid var(--border);
}

.dtype-card {
  padding: 32px 28px;
  border-right: 1px solid var(--border);
  cursor: none;
  transition: background 0.15s;
  position: relative;
}

.dtype-card:last-child { border-right: none; }

.dtype-card:hover {
  background: var(--black);
}

.dtype-card:hover .dtype-icon,
.dtype-card:hover .dtype-name,
.dtype-card:hover .dtype-count { color: var(--white); }

.dtype-card:hover .dtype-bar-fill { background: var(--green); }
.dtype-card:hover .dtype-ex { color: #5a6070; }

.dtype-icon {
  font-size: 24px;
  margin-bottom: 20px;
  display: block;
  transition: color 0.15s;
}

.dtype-name {
  font-size: 14px;
  font-weight: 500;
  color: var(--black);
  margin-bottom: 6px;
  transition: color 0.15s;
}

.dtype-count {
  font-family: var(--mono);
  font-size: 11px;
  color: var(--mid);
  margin-bottom: 16px;
  transition: color 0.15s;
}

.dtype-bar {
  height: 2px;
  background: var(--border);
  margin-bottom: 14px;
}

.dtype-bar-fill {
  height: 2px;
  background: var(--black);
  transition: background 0.15s;
}

.dtype-ex {
  font-family: var(--mono);
  font-size: 10px;
  color: var(--light);
  letter-spacing: 0.06em;
  line-height: 1.7;
  transition: color 0.15s;
}

/* ── PROOF SECTION ── */
.proof {
  display: grid;
  grid-template-columns: 1fr 1fr;
  border-bottom: 1px solid var(--border);
}

.proof-left {
  background: var(--black);
  padding: 80px 60px;
}

.proof-right {
  padding: 80px 60px;
  border-left: 1px solid var(--border);
}

.proof-eyebrow {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: #3a4050;
  margin-bottom: 32px;
  display: flex;
  align-items: center;
  gap: 12px;
}

.proof-eyebrow::before {
  content: '';
  display: inline-block;
  width: 20px;
  height: 1px;
  background: var(--green);
}

.proof-headline {
  font-family: var(--display);
  font-size: clamp(52px, 5vw, 80px);
  line-height: 0.93;
  color: var(--white);
  margin-bottom: 28px;
  letter-spacing: -0.01em;
}

.proof-body {
  font-size: 15px;
  font-weight: 300;
  color: #5a6070;
  line-height: 1.8;
  margin-bottom: 40px;
}

.proof-terminal {
  background: #0a0b0d;
  border: 1px solid #1a1e25;
  padding: 20px;
  font-family: var(--mono);
  font-size: 11px;
  line-height: 1.9;
  color: #3a4050;
}

.t-comment { color: #2a3040; }
.t-green { color: var(--green); }
.t-blue { color: #4d9fff; }
.t-amber { color: #f5a623; }
.t-white { color: #8b92a5; }

.proof-features {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.proof-feature {
  display: flex;
  gap: 20px;
  padding: 24px 0;
  border-bottom: 1px solid var(--border);
  align-items: flex-start;
}

.proof-feature:last-child { border-bottom: none; }

.proof-feature-icon {
  width: 36px; height: 36px;
  border: 1px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  flex-shrink: 0;
  margin-top: 2px;
}

.proof-feature-title {
  font-size: 14px;
  font-weight: 500;
  color: var(--black);
  margin-bottom: 5px;
}

.proof-feature-desc {
  font-size: 13px;
  font-weight: 300;
  color: var(--mid);
  line-height: 1.6;
}

/* ── PRICING ── */
.pricing {
  padding: 80px 40px;
  border-bottom: 1px solid var(--border);
}

.pricing-header {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  margin-bottom: 48px;
}

.pricing-title {
  font-family: var(--display);
  font-size: clamp(48px, 6vw, 96px);
  line-height: 0.92;
  color: var(--black);
}

.pricing-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0;
  border: 1px solid var(--border);
}

.price-card {
  padding: 40px 36px;
  border-right: 1px solid var(--border);
  position: relative;
  transition: background 0.15s;
}

.price-card:last-child { border-right: none; }

.price-card.featured {
  background: var(--black);
}

.price-card-label {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--light);
  margin-bottom: 20px;
}

.price-card.featured .price-card-label { color: #3a4050; }

.price-amount {
  font-family: var(--display);
  font-size: 64px;
  line-height: 1;
  color: var(--black);
  margin-bottom: 4px;
  letter-spacing: -0.02em;
}

.price-card.featured .price-amount { color: var(--white); }

.price-unit {
  font-family: var(--mono);
  font-size: 11px;
  color: var(--light);
  letter-spacing: 0.1em;
  margin-bottom: 28px;
}

.price-card.featured .price-unit { color: #3a4050; }

.price-features {
  list-style: none;
  margin-bottom: 36px;
}

.price-features li {
  display: flex;
  gap: 10px;
  align-items: flex-start;
  padding: 8px 0;
  border-bottom: 1px solid var(--border);
  font-size: 13px;
  font-weight: 300;
  color: var(--mid);
}

.price-card.featured .price-features li {
  border-color: #1a1e25;
  color: #5a6070;
}

.price-features li::before {
  content: '→';
  font-family: var(--mono);
  font-size: 11px;
  color: var(--green);
  margin-top: 1px;
  flex-shrink: 0;
}

/* ── TESTIMONIALS ── */
.testimonials {
  background: var(--off-white);
  border-bottom: 1px solid var(--border);
  padding: 80px 40px;
}

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1px;
  background: var(--border);
  border: 1px solid var(--border);
  margin-top: 48px;
}

.testimonial {
  background: var(--off-white);
  padding: 36px;
}

.testimonial-quote {
  font-size: 15px;
  font-weight: 300;
  color: var(--black);
  line-height: 1.8;
  margin-bottom: 24px;
  position: relative;
}

.testimonial-quote::before {
  content: '"';
  font-family: var(--display);
  font-size: 80px;
  color: var(--border);
  position: absolute;
  top: -20px;
  left: -12px;
  line-height: 1;
  pointer-events: none;
}

.testimonial-author {
  display: flex;
  align-items: center;
  gap: 12px;
  padding-top: 20px;
  border-top: 1px solid var(--border);
}

.testimonial-avatar {
  width: 32px; height: 32px;
  background: var(--black);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--mono);
  font-size: 10px;
  color: var(--green);
  font-weight: 500;
}

.testimonial-name {
  font-size: 13px;
  font-weight: 500;
  color: var(--black);
}

.testimonial-role {
  font-family: var(--mono);
  font-size: 10px;
  color: var(--light);
  letter-spacing: 0.08em;
}

/* ── CTA ── */
.cta-section {
  background: var(--black);
  padding: 120px 40px;
  text-align: center;
  position: relative;
  overflow: hidden;
}

.cta-bg {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--display);
  font-size: 28vw;
  color: transparent;
  -webkit-text-stroke: 1px #0f1318;
  pointer-events: none;
  user-select: none;
  line-height: 1;
  letter-spacing: -0.03em;
}

.cta-eyebrow {
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: #3a4050;
  margin-bottom: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 14px;
  position: relative;
  z-index: 2;
}

.cta-eyebrow::before, .cta-eyebrow::after {
  content: '';
  display: inline-block;
  width: 28px;
  height: 1px;
  background: var(--green);
}

.cta-headline {
  font-family: var(--display);
  font-size: clamp(64px, 9vw, 140px);
  line-height: 0.92;
  color: var(--white);
  margin-bottom: 32px;
  letter-spacing: -0.01em;
  position: relative;
  z-index: 2;
}

.cta-headline .cta-accent { color: var(--green); }

.cta-sub {
  font-size: 16px;
  font-weight: 300;
  color: #5a6070;
  max-width: 480px;
  margin: 0 auto 48px;
  line-height: 1.7;
  position: relative;
  z-index: 2;
}

.cta-btns {
  display: flex;
  gap: 12px;
  justify-content: center;
  position: relative;
  z-index: 2;
}

/* ── FOOTER ── */
footer {
  background: var(--black);
  border-top: 1px solid #1a1e25;
  padding: 48px 40px 32px;
}

.footer-top {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr;
  gap: 48px;
  margin-bottom: 48px;
  padding-bottom: 48px;
  border-bottom: 1px solid #1a1e25;
}

.footer-brand {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 16px;
}

.footer-brand-mark {
  width: 24px; height: 24px;
  background: var(--green);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--mono);
  font-size: 8px;
  font-weight: 500;
  color: #000;
}

.footer-brand-name {
  font-family: var(--mono);
  font-size: 12px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--white);
}

.footer-tagline {
  font-size: 13px;
  font-weight: 300;
  color: #3a4050;
  line-height: 1.7;
  max-width: 260px;
  margin-bottom: 20px;
}

.footer-col-title {
  font-family: var(--mono);
  font-size: 9px;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: #2a3040;
  margin-bottom: 16px;
}

.footer-links {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.footer-links a {
  font-size: 13px;
  font-weight: 300;
  color: #3a4050;
  text-decoration: none;
  transition: color 0.15s;
  cursor: none;
}

.footer-links a:hover { color: #8b92a5; }

.footer-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.footer-copy {
  font-family: var(--mono);
  font-size: 10px;
  color: #2a3040;
  letter-spacing: 0.08em;
}

.footer-chain {
  display: flex;
  align-items: center;
  gap: 6px;
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #2a3040;
}

/* ANIMATIONS */
@keyframes slideUp {
  from { opacity: 0; transform: translateY(32px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}

.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Mobile */
@media (max-width: 900px) {
  nav { padding: 16px 20px; }
  .nav-links { display: none; }
  .hero { padding: 0 20px 40px; }
  .how { grid-template-columns: 1fr; }
  .how-side:first-child { border-right: none; border-bottom: 1px solid var(--border); }
  .stats-strip { grid-template-columns: 1fr 1fr; }
  .datatypes-grid { grid-template-columns: 1fr 1fr; }
  .pricing-grid { grid-template-columns: 1fr; }
  .proof { grid-template-columns: 1fr; }
  .testimonials-grid { grid-template-columns: 1fr; }
  .footer-top { grid-template-columns: 1fr 1fr; gap: 32px; }
  .hero-bg-text { font-size: 30vw; }
}
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">
    <div class="nav-logo-mark">DV</div>
    <span class="nav-logo-name">DataVault</span>
  </a>
  <ul class="nav-links">
    <li><a href="#how">How It Works</a></li>
    <li><a href="#data">Datasets</a></li>
    <li><a href="#proof">On-Chain Proof</a></li>
    <li><a href="#pricing">Pricing</a></li>
  </ul>
  <div class="nav-ctas">
    <a href="#" class="btn btn-outline">Start Earning</a>
    <a href="#" class="btn btn-solid">Enterprise Access →</a>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg-text">DATA</div>

  <div class="hero-eyebrow">
    <span>The AI Data Marketplace</span>
    <div class="chain-pill">
      <div class="chain-dot"></div>
      Built on Base
    </div>
  </div>

  <h1 class="hero-headline">
    YOUR DATA.<br>
    YOUR <span class="accent">PRICE.</span>
  </h1>

  <div class="hero-bottom">
    <p class="hero-desc">
      Contributors earn USDC for the data they provide. AI labs get clean, consented, rights-cleared training datasets. Every submission cryptographically proven on Base.
    </p>
    <div class="hero-actions">
      <div class="hero-stat-row">
        <div class="hero-stat">
          <div class="hero-stat-num">47M+</div>
          <div class="hero-stat-label">Records Available</div>
        </div>
        <div class="hero-stat">
          <div class="hero-stat-num">$2.1M</div>
          <div class="hero-stat-label">Paid to Contributors</div>
        </div>
        <div class="hero-stat">
          <div class="hero-stat-num">340+</div>
          <div class="hero-stat-label">Enterprise Buyers</div>
        </div>
      </div>
      <div style="display:flex;gap:10px;margin-top:8px;">
        <a href="#" class="btn btn-green">Start Contributing →</a>
        <a href="#" class="btn btn-outline">Browse Datasets</a>
      </div>
    </div>
  </div>
</section>

<!-- TICKER -->
<div class="ticker-wrap">
  <div class="ticker-inner" id="ticker">
    <span class="ticker-item">Text / NLP <span class="t-val">24.3M records</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Computer Vision <span class="t-val">11.8M images</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Audio / Speech <span class="t-val">6.4M clips</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">RLHF Comparisons <span class="t-val">2.1M pairs</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Video <span class="t-val">890K clips</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Medical (De-ID) <span class="t-val">420K docs</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Avg payout <span class="t-val">$0.018 / record</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Base Mainnet <span class="t-val">Live</span> <span class="ticker-sep">·</span></span>
    <!-- duplicate for seamless loop -->
    <span class="ticker-item">Text / NLP <span class="t-val">24.3M records</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Computer Vision <span class="t-val">11.8M images</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Audio / Speech <span class="t-val">6.4M clips</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">RLHF Comparisons <span class="t-val">2.1M pairs</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Video <span class="t-val">890K clips</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Medical (De-ID) <span class="t-val">420K docs</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Avg payout <span class="t-val">$0.018 / record</span> <span class="ticker-sep">·</span></span>
    <span class="ticker-item">Base Mainnet <span class="t-val">Live</span> <span class="ticker-sep">·</span></span>
  </div>
</div>

<!-- HOW IT WORKS -->
<section class="how" id="how">
  <div class="how-side reveal">
    <div class="side-label">For Contributors</div>
    <h2 class="side-headline">EARN FROM WHAT YOU KNOW</h2>
    <p class="side-body">Upload data, complete labeling tasks, and get paid in USDC directly to your wallet. No middlemen. Every payout settled on Base.</p>
    <div class="steps">
      <div class="step">
        <div class="step-num">01</div>
        <div>
          <div class="step-title">Connect Your Wallet</div>
          <div class="step-desc">Sign in with any Base-compatible wallet. Your identity stays on-chain, your data stays yours.</div>
        </div>
      </div>
      <div class="step">
        <div class="step-num">02</div>
        <div>
          <div class="step-title">Upload or Complete Tasks</div>
          <div class="step-desc">Submit your own data or pick from open bounties. Photos, audio, video, text, annotations.</div>
        </div>
      </div>
      <div class="step">
        <div class="step-num">03</div>
        <div>
          <div class="step-title">Proof Gets Committed</div>
          <div class="step-desc">A SHA-256 hash of your submission is recorded on Base at upload time. Immutable, timestamped, yours.</div>
        </div>
      </div>
      <div class="step">
        <div class="step-num">04</div>
        <div>
          <div class="step-title">Get Paid in USDC</div>
          <div class="step-desc">When your data gets licensed, USDC flows directly to your wallet. Real-time earnings dashboard shows every transaction.</div>
        </div>
      </div>
    </div>
  </div>

  <div class="how-side reveal">
    <div class="side-label">For Enterprise Buyers</div>
    <h2 class="side-headline">DATA LABS TRUST</h2>
    <p class="side-body">Search, preview, and license rights-cleared training datasets. Post custom bounties. Every dataset delivered with on-chain provenance.</p>
    <div class="steps">
      <div class="step">
        <div class="step-num">01</div>
        <div>
          <div class="step-title">Search the Catalog</div>
          <div class="step-desc">Natural-language search across 47M+ records. Filter by modality, language, license type, and quality tier.</div>
        </div>
      </div>
      <div class="step">
        <div class="step-num">02</div>
        <div>
          <div class="step-title">Post a Bounty</div>
          <div class="step-desc">Need something specific? Define your requirements, set a USDC reward pool, and let contributors fill it.</div>
        </div>
      </div>
      <div class="step">
        <div class="step-num">03</div>
        <div>
          <div class="step-title">License with Proof</div>
          <div class="step-desc">Pay in USDC on Base. Receive packaged datasets with full on-chain provenance for every record included.</div>
        </div>
      </div>
      <div class="step">
        <div class="step-num">04</div>
        <div>
          <div class="step-title">API or Bulk Export</div>
          <div class="step-desc">Stream data via SDK, download in bulk, or set up automated pipelines. SOC 2 compliant. GDPR ready.</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- STATS -->
<div class="stats-strip">
  <div class="stat-block reveal">
    <div class="stat-num">47M+</div>
    <div class="stat-label">Total Records</div>
    <div class="stat-sub">Across text, audio, vision, video, and specialized domains</div>
  </div>
  <div class="stat-block reveal" style="transition-delay:0.1s">
    <div class="stat-num">$2.1M</div>
    <div class="stat-label">Contributor Payouts</div>
    <div class="stat-sub">Settled directly in USDC on Base mainnet</div>
  </div>
  <div class="stat-block reveal" style="transition-delay:0.2s">
    <div class="stat-num">340+</div>
    <div class="stat-label">Enterprise Buyers</div>
    <div class="stat-sub">Including leading AI labs, robotics firms, and research institutions</div>
  </div>
  <div class="stat-block reveal" style="transition-delay:0.3s">
    <div class="stat-num">16</div>
    <div class="stat-label">Languages Covered</div>
    <div class="stat-sub">With demographic diversity verification across all submissions</div>
  </div>
</div>

<!-- DATA TYPES -->
<section class="datatypes reveal" id="data">
  <div class="section-eyebrow">Dataset Catalog</div>
  <div class="datatypes-header">
    <h2 class="datatypes-title">EVERY<br>MODALITY.</h2>
    <a href="#" class="btn btn-outline">Browse All Datasets →</a>
  </div>
  <div class="datatypes-grid">
    <div class="dtype-card">
      <span class="dtype-icon">📝</span>
      <div class="dtype-name">Text / NLP</div>
      <div class="dtype-count">24.3M records</div>
      <div class="dtype-bar"><div class="dtype-bar-fill" style="width:85%"></div></div>
      <div class="dtype-ex">Instruction pairs<br>RLHF comparisons<br>Multilingual corpora</div>
    </div>
    <div class="dtype-card">
      <span class="dtype-icon">📷</span>
      <div class="dtype-name">Vision</div>
      <div class="dtype-count">11.8M images</div>
      <div class="dtype-bar"><div class="dtype-bar-fill" style="width:65%"></div></div>
      <div class="dtype-ex">Object detection<br>Segmentation masks<br>Scene classification</div>
    </div>
    <div class="dtype-card">
      <span class="dtype-icon">🎙</span>
      <div class="dtype-name">Audio / Speech</div>
      <div class="dtype-count">6.4M clips</div>
      <div class="dtype-bar"><div class="dtype-bar-fill" style="width:42%"></div></div>
      <div class="dtype-ex">Conversational speech<br>Speaker diarization<br>Noise conditions</div>
    </div>
    <div class="dtype-card">
      <span class="dtype-icon">🎬</span>
      <div class="dtype-name">Video</div>
      <div class="dtype-count">890K clips</div>
      <div class="dtype-bar"><div class="dtype-bar-fill" style="width:22%"></div></div>
      <div class="dtype-ex">Action recognition<br>Temporal labeling<br>Depth-paired RGB</div>
    </div>
    <div class="dtype-card">
      <span class="dtype-icon">🔬</span>
      <div class="dtype-name">Specialized</div>
      <div class="dtype-count">3.2M records</div>
      <div class="dtype-bar"><div class="dtype-bar-fill" style="width:28%"></div></div>
      <div class="dtype-ex">De-ID medical<br>Legal documents<br>Financial narratives</div>
    </div>
  </div>
</section>

<!-- PROOF -->
<section class="proof" id="proof">
  <div class="proof-left reveal">
    <div class="proof-eyebrow">On-Chain Provenance</div>
    <h2 class="proof-headline">PROOF.<br>NOT<br>PROMISES.</h2>
    <p class="proof-body">Every record submitted to DataVault gets a cryptographic fingerprint committed to Base at upload time. Enterprise buyers can verify exactly what they're buying before they buy it.</p>
    <div class="proof-terminal">
      <span class="t-comment">// Verify a dataset record on Base</span><br>
      <span class="t-blue">const</span> <span class="t-white">proof</span> = <span class="t-blue">await</span> client.proof.verify({<br>
      &nbsp;&nbsp;<span class="t-white">hash</span>: <span class="t-green">'0x3f9a2c8e1b4d7f0a...'</span>,<br>
      &nbsp;&nbsp;<span class="t-white">chain</span>: <span class="t-green">'base'</span><br>
      });<br><br>
      <span class="t-comment">// Returns</span><br>
      {<br>
      &nbsp;&nbsp;<span class="t-white">verified</span>: <span class="t-green">true</span>,<br>
      &nbsp;&nbsp;<span class="t-white">contributor</span>: <span class="t-green">'0x7b2e...f901'</span>,<br>
      &nbsp;&nbsp;<span class="t-white">timestamp</span>: <span class="t-amber">1741651200</span>,<br>
      &nbsp;&nbsp;<span class="t-white">blockNumber</span>: <span class="t-amber">21884422</span>,<br>
      &nbsp;&nbsp;<span class="t-white">chain</span>: <span class="t-green">'base-mainnet'</span><br>
      }
    </div>
  </div>
  <div class="proof-right reveal">
    <div class="side-label">Why It Matters</div>
    <h2 class="side-headline" style="font-family:var(--display);font-size:clamp(40px,4vw,64px);line-height:0.95;letter-spacing:-0.01em;color:var(--black);margin-bottom:36px;">COMPLIANCE-<br>READY DATA.</h2>
    <div class="proof-features">
      <div class="proof-feature">
        <div class="proof-feature-icon">⛓</div>
        <div>
          <div class="proof-feature-title">Immutable Submission Timestamps</div>
          <div class="proof-feature-desc">SHA-256 hash committed on Base at the exact moment of upload. Cannot be altered retroactively.</div>
        </div>
      </div>
      <div class="proof-feature">
        <div class="proof-feature-icon">✍</div>
        <div>
          <div class="proof-feature-title">Verified Contributor Consent</div>
          <div class="proof-feature-desc">Wallet signature at upload time creates a verifiable consent record. GDPR and CCPA compliant by design.</div>
        </div>
      </div>
      <div class="proof-feature">
        <div class="proof-feature-icon">🔍</div>
        <div>
          <div class="proof-feature-title">License Provenance Trail</div>
          <div class="proof-feature-desc">Every licensing transaction is on-chain. Enterprise buyers can audit their entire data supply chain.</div>
        </div>
      </div>
      <div class="proof-feature">
        <div class="proof-feature-icon">⚖</div>
        <div>
          <div class="proof-feature-title">Rights-Cleared by Default</div>
          <div class="proof-feature-desc">Contributors explicitly grant commercial licenses at upload. No ambiguity around training data ownership.</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PRICING -->
<section class="pricing reveal" id="pricing">
  <div class="pricing-header">
    <h2 class="pricing-title">SIMPLE<br>PRICING.</h2>
    <p style="max-width:300px;font-size:14px;font-weight:300;color:var(--mid);line-height:1.7;">Pay per dataset or commit to a plan. All plans include on-chain provenance for every record.</p>
  </div>
  <div class="pricing-grid">
    <div class="price-card">
      <div class="price-card-label">Starter</div>
      <div class="price-amount">$0</div>
      <div class="price-unit">To browse & preview</div>
      <ul class="price-features">
        <li>Full dataset catalog access</li>
        <li>Preview up to 1,000 records per dataset</li>
        <li>On-chain proof verification</li>
        <li>Pay-per-dataset licensing</li>
        <li>Standard support</li>
      </ul>
      <a href="#" class="btn btn-outline" style="width:100%;justify-content:center;">Create Account</a>
    </div>
    <div class="price-card featured">
      <div class="price-card-label">Pro</div>
      <div class="price-amount" style="color:var(--green);">$4,900</div>
      <div class="price-unit">per month</div>
      <ul class="price-features">
        <li>Unlimited dataset licensing</li>
        <li>API access (10M calls/mo)</li>
        <li>Bounty posting (up to 5 active)</li>
        <li>Custom data pipelines</li>
        <li>SOC 2 compliance docs</li>
        <li>Priority support + SLA</li>
      </ul>
      <a href="#" class="btn btn-green" style="width:100%;justify-content:center;">Start Pro Trial</a>
    </div>
    <div class="price-card">
      <div class="price-card-label">Enterprise</div>
      <div class="price-amount">Custom</div>
      <div class="price-unit">Volume pricing</div>
      <ul class="price-features">
        <li>Unlimited everything</li>
        <li>Dedicated data sourcing team</li>
        <li>Custom bounty campaigns</li>
        <li>Private dataset vaults</li>
        <li>HIPAA / GDPR DPA</li>
        <li>Dedicated account manager</li>
      </ul>
      <a href="#" class="btn btn-outline" style="width:100%;justify-content:center;">Contact Sales →</a>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section class="testimonials reveal">
  <div class="section-eyebrow">What Teams Are Saying</div>
  <div class="testimonials-grid">
    <div class="testimonial">
      <div class="testimonial-quote">The on-chain provenance is what sold us. Our legal team finally stopped blocking data purchases. We've licensed four datasets in the last two months.</div>
      <div class="testimonial-author">
        <div class="testimonial-avatar">ML</div>
        <div>
          <div class="testimonial-name">Marcus L.</div>
          <div class="testimonial-role">Head of ML Data · Cohere</div>
        </div>
      </div>
    </div>
    <div class="testimonial">
      <div class="testimonial-quote">We posted a bounty for 200K Hindi voice clips with speaker labels. Had 80% fill in under two weeks. The quality was genuinely better than vendors we've used before.</div>
      <div class="testimonial-author">
        <div class="testimonial-avatar">PR</div>
        <div>
          <div class="testimonial-name">Priya R.</div>
          <div class="testimonial-role">Research Lead · AI21 Labs</div>
        </div>
      </div>
    </div>
    <div class="testimonial">
      <div class="testimonial-quote">I've made $840 in six weeks just doing labeling tasks on my lunch break. Payments hit my wallet the same day. Never had that with any other platform.</div>
      <div class="testimonial-author">
        <div class="testimonial-avatar">JK</div>
        <div>
          <div class="testimonial-name">James K.</div>
          <div class="testimonial-role">Contributor · Lagos, Nigeria</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<section class="cta-section">
  <div class="cta-bg">EARN</div>
  <div class="cta-eyebrow">Get Started Today</div>
  <h2 class="cta-headline">YOUR DATA<br>IS <span class="cta-accent">VALUABLE.</span></h2>
  <p class="cta-sub">Join thousands of contributors earning USDC for their data, and the AI labs who trust DataVault for rights-cleared training datasets.</p>
  <div class="cta-btns">
    <a href="#" class="btn btn-green" style="padding:12px 28px;font-size:12px;">Start Contributing →</a>
    <a href="#" class="btn" style="background:transparent;border:1px solid #2a3040;color:#5a6070;padding:12px 28px;font-size:12px;">Enterprise Portal →</a>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div>
      <div class="footer-brand">
        <div class="footer-brand-mark">DV</div>
        <span class="footer-brand-name">DataVault</span>
      </div>
      <p class="footer-tagline">The AI data marketplace built on Base. Consent-verified, rights-cleared, on-chain proven.</p>
      <div class="chain-pill" style="border-color:#1a1e25;color:#3a4050;">
        <div class="chain-dot"></div>
        BASE MAINNET
      </div>
    </div>
    <div>
      <div class="footer-col-title">Platform</div>
      <ul class="footer-links">
        <li><a href="#">Dataset Catalog</a></li>
        <li><a href="#">Post a Bounty</a></li>
        <li><a href="#">Enterprise Portal</a></li>
        <li><a href="#">API Docs</a></li>
      </ul>
    </div>
    <div>
      <div class="footer-col-title">Contributors</div>
      <ul class="footer-links">
        <li><a href="#">How to Earn</a></li>
        <li><a href="#">Labeling Tasks</a></li>
        <li><a href="#">Payout Methods</a></li>
        <li><a href="#">Referral Program</a></li>
      </ul>
    </div>
    <div>
      <div class="footer-col-title">Company</div>
      <ul class="footer-links">
        <li><a href="#">About</a></li>
        <li><a href="#">Blog</a></li>
        <li><a href="#">Privacy Policy</a></li>
        <li><a href="#">Terms of Service</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <div class="footer-copy">© 2026 DataVault. All rights reserved.</div>
    <div class="footer-chain">
      <div class="chain-dot"></div>
      Settlements on Base · Powered by USDC
    </div>
  </div>
</footer>

<script>
// Custom cursor
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursorRing');
let mx = 0, my = 0, rx = 0, ry = 0;

document.addEventListener('mousemove', e => {
  mx = e.clientX; my = e.clientY;
  cursor.style.transform = `translate(${mx - 4}px, ${my - 4}px)`;
});

function animateRing() {
  rx += (mx - rx - 18) * 0.12;
  ry += (my - ry - 18) * 0.12;
  ring.style.transform = `translate(${rx}px, ${ry}px)`;
  requestAnimationFrame(animateRing);
}
animateRing();

document.querySelectorAll('a, button, .dtype-card, .stat-block').forEach(el => {
  el.addEventListener('mouseenter', () => ring.classList.add('hover'));
  el.addEventListener('mouseleave', () => ring.classList.remove('hover'));
});

// Scroll reveal
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('visible');
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>
</body>
</html>

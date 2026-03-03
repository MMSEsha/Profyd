<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Profyd — Professional Hiring Platform in Pakistan</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700;900&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --ink: #0a0a0f;
    --cream: #f5f0e8;
    --gold: #c9a84c;
    --gold-light: #e8c96a;
    --forest: #1a3a2e;
    --forest-mid: #24513f;
    --forest-light: #3a7a5e;
    --warm-grey: #8a8275;
    --card-bg: #ffffff;
    --border: #e0d9ce;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--cream);
    color: var(--ink);
    overflow-x: hidden;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.2rem 5%;
    background: rgba(245,240,232,0.92);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
    transition: box-shadow 0.3s;
  }
  nav.scrolled { box-shadow: 0 2px 24px rgba(0,0,0,0.08); }
  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem; font-weight: 900; letter-spacing: -0.02em;
    color: var(--forest);
    text-decoration: none;
  }
  .nav-logo span { color: var(--gold); }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    font-size: 0.88rem; font-weight: 500; letter-spacing: 0.04em;
    text-transform: uppercase; color: var(--ink); text-decoration: none;
    position: relative; padding-bottom: 3px; transition: color 0.2s;
  }
  .nav-links a::after {
    content: ''; position: absolute; bottom: 0; left: 0; right: 0;
    height: 1.5px; background: var(--gold); transform: scaleX(0);
    transform-origin: left; transition: transform 0.3s;
  }
  .nav-links a:hover { color: var(--forest); }
  .nav-links a:hover::after { transform: scaleX(1); }
  .nav-cta {
    background: var(--forest); color: #fff;
    padding: 0.6rem 1.5rem; border-radius: 2px;
    font-size: 0.85rem; font-weight: 600; letter-spacing: 0.05em;
    text-transform: uppercase; text-decoration: none;
    transition: background 0.2s, transform 0.2s;
  }
  .nav-cta:hover { background: var(--forest-mid); transform: translateY(-1px); }
  .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; }
  .hamburger span { width: 24px; height: 2px; background: var(--ink); transition: 0.3s; }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    overflow: hidden;
    position: relative;
  }
  .hero-left {
    background: var(--forest);
    padding: 12rem 5% 5rem 8%;
    display: flex; flex-direction: column; justify-content: center;
    position: relative; overflow: hidden;
  }
  .hero-left::before {
    content: '';
    position: absolute; top: -100px; right: -100px;
    width: 400px; height: 400px;
    border-radius: 50%;
    border: 60px solid rgba(201,168,76,0.12);
    animation: pulse 6s ease-in-out infinite;
  }
  .hero-left::after {
    content: '';
    position: absolute; bottom: -80px; left: -80px;
    width: 280px; height: 280px;
    border-radius: 50%;
    border: 40px solid rgba(255,255,255,0.04);
    animation: pulse 8s ease-in-out infinite reverse;
  }
  @keyframes pulse {
    0%, 100% { transform: scale(1); opacity: 1; }
    50% { transform: scale(1.1); opacity: 0.6; }
  }
  .hero-tag {
    display: inline-block;
    background: rgba(201,168,76,0.18);
    color: var(--gold-light);
    font-size: 0.75rem; font-weight: 600; letter-spacing: 0.12em;
    text-transform: uppercase; padding: 0.4rem 1rem;
    border: 1px solid rgba(201,168,76,0.3);
    border-radius: 2px; margin-bottom: 2rem;
    animation: fadeUp 0.8s ease both;
  }
  .hero-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.8rem, 4.5vw, 4rem);
    font-weight: 900; line-height: 1.1;
    color: #fff; margin-bottom: 1.5rem;
    animation: fadeUp 0.8s 0.15s ease both;
  }
  .hero-title em { font-style: normal; color: var(--gold); }
  .hero-sub {
    font-size: 1.05rem; font-weight: 300; line-height: 1.75;
    color: rgba(255,255,255,0.72); max-width: 420px; margin-bottom: 2.5rem;
    animation: fadeUp 0.8s 0.3s ease both;
  }
  .hero-btns { display: flex; gap: 1rem; flex-wrap: wrap; animation: fadeUp 0.8s 0.45s ease both; }
  .btn-primary {
    background: var(--gold); color: var(--ink);
    padding: 0.9rem 2rem; border-radius: 2px;
    font-weight: 700; font-size: 0.9rem; letter-spacing: 0.05em;
    text-transform: uppercase; text-decoration: none;
    transition: background 0.2s, transform 0.2s, box-shadow 0.2s;
    border: none; cursor: pointer;
  }
  .btn-primary:hover { background: var(--gold-light); transform: translateY(-2px); box-shadow: 0 8px 24px rgba(201,168,76,0.3); }
  .btn-outline {
    background: transparent; color: #fff;
    padding: 0.9rem 2rem; border-radius: 2px;
    font-weight: 600; font-size: 0.9rem; letter-spacing: 0.05em;
    text-transform: uppercase; text-decoration: none;
    border: 1.5px solid rgba(255,255,255,0.35);
    transition: border-color 0.2s, background 0.2s;
  }
  .btn-outline:hover { border-color: #fff; background: rgba(255,255,255,0.08); }

  .hero-right {
    background: var(--cream);
    padding: 12rem 8% 5rem 6%;
    display: flex; flex-direction: column; justify-content: center;
    position: relative;
  }
  .hero-stats {
    display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem;
    margin-bottom: 3rem; animation: fadeUp 0.8s 0.2s ease both;
  }
  .stat-card {
    background: #fff; border: 1px solid var(--border);
    padding: 1.5rem; border-radius: 4px;
    transition: box-shadow 0.3s, transform 0.3s;
  }
  .stat-card:hover { box-shadow: 0 8px 32px rgba(0,0,0,0.08); transform: translateY(-3px); }
  .stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 2.2rem; font-weight: 900; color: var(--forest);
    line-height: 1;
  }
  .stat-label { font-size: 0.82rem; color: var(--warm-grey); margin-top: 0.4rem; font-weight: 500; }
  .hero-promise {
    background: var(--forest);
    padding: 1.8rem 2rem; border-radius: 4px;
    animation: fadeUp 0.8s 0.4s ease both;
  }
  .hero-promise p {
    color: rgba(255,255,255,0.8); font-size: 0.95rem; line-height: 1.7;
    font-weight: 300;
  }
  .hero-promise strong { color: var(--gold-light); }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(28px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* SECTIONS */
  section { padding: 7rem 5%; }
  .section-label {
    display: inline-block; font-size: 0.72rem; font-weight: 700;
    letter-spacing: 0.14em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 0.8rem;
  }
  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 3.5vw, 2.8rem);
    font-weight: 700; line-height: 1.2; color: var(--ink);
    max-width: 560px; margin-bottom: 1.5rem;
  }
  .section-sub {
    font-size: 1rem; color: var(--warm-grey); line-height: 1.8;
    max-width: 560px; margin-bottom: 3rem;
  }

  /* ABOUT */
  #about {
    background: #fff;
    display: grid; grid-template-columns: 1fr 1fr; gap: 6rem;
    align-items: center;
  }
  .about-visual {
    position: relative;
  }
  .about-img-box {
    background: var(--forest);
    width: 100%; aspect-ratio: 4/5;
    border-radius: 4px;
    display: flex; align-items: center; justify-content: center;
    overflow: hidden; position: relative;
  }
  .about-img-box::before {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(201,168,76,0.2) 0%, transparent 60%);
  }
  .about-icon-grid {
    display: grid; grid-template-columns: 1fr 1fr; gap: 2px; padding: 3rem; width: 100%;
  }
  .about-icon-cell {
    aspect-ratio: 1; background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.08);
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    gap: 0.5rem;
    transition: background 0.3s;
  }
  .about-icon-cell:hover { background: rgba(201,168,76,0.15); }
  .about-icon-cell .icon { font-size: 1.8rem; }
  .about-icon-cell .lbl { font-size: 0.7rem; color: rgba(255,255,255,0.6); text-align: center; font-weight: 500; }
  .about-badge {
    position: absolute; bottom: -1.5rem; right: -1.5rem;
    background: var(--gold); color: var(--ink);
    padding: 1.2rem 1.5rem; border-radius: 4px;
    font-family: 'Playfair Display', serif;
    font-size: 1.1rem; font-weight: 700; text-align: center;
    box-shadow: 0 12px 40px rgba(201,168,76,0.4);
  }
  .about-badge span { display: block; font-size: 0.7rem; font-family: 'DM Sans', sans-serif; font-weight: 500; margin-top: 2px; }
  .pillars { display: flex; flex-direction: column; gap: 1rem; margin-top: 2rem; }
  .pillar {
    display: flex; align-items: flex-start; gap: 1rem;
    padding: 1.2rem; border: 1px solid var(--border); border-radius: 4px;
    background: var(--cream); transition: box-shadow 0.3s;
  }
  .pillar:hover { box-shadow: 0 4px 20px rgba(0,0,0,0.07); }
  .pillar-icon { font-size: 1.4rem; flex-shrink: 0; margin-top: 2px; }
  .pillar h4 { font-size: 0.9rem; font-weight: 700; color: var(--forest); margin-bottom: 0.3rem; }
  .pillar p { font-size: 0.84rem; color: var(--warm-grey); line-height: 1.6; }

  /* HIRING */
  #hiring { background: var(--cream); }
  .hiring-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1.5rem;
  }
  .role-card {
    background: #fff; border: 1px solid var(--border); border-radius: 4px;
    padding: 2rem; position: relative; overflow: hidden;
    transition: box-shadow 0.3s, transform 0.3s;
    cursor: pointer;
  }
  .role-card::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px;
    background: var(--gold); transform: scaleX(0); transform-origin: left;
    transition: transform 0.35s;
  }
  .role-card:hover { box-shadow: 0 12px 48px rgba(0,0,0,0.1); transform: translateY(-4px); }
  .role-card:hover::before { transform: scaleX(1); }
  .role-icon { font-size: 2.2rem; margin-bottom: 1rem; }
  .role-title { font-family: 'Playfair Display', serif; font-size: 1.2rem; font-weight: 700; color: var(--forest); margin-bottom: 0.6rem; }
  .role-desc { font-size: 0.88rem; color: var(--warm-grey); line-height: 1.7; margin-bottom: 1.5rem; }
  .role-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }
  .tag {
    background: var(--cream); border: 1px solid var(--border);
    font-size: 0.73rem; font-weight: 600; letter-spacing: 0.03em;
    padding: 0.25rem 0.7rem; border-radius: 100px; color: var(--forest);
  }

  /* PROCESS */
  #process { background: var(--forest); }
  #process .section-title { color: #fff; }
  #process .section-sub { color: rgba(255,255,255,0.65); }
  #process .section-label { color: var(--gold-light); }
  .steps {
    display: grid; grid-template-columns: repeat(5, 1fr);
    gap: 0; position: relative;
  }
  .steps::before {
    content: '';
    position: absolute; top: 2.5rem; left: 10%; right: 10%;
    height: 1px; background: rgba(201,168,76,0.3);
    z-index: 0;
  }
  .step {
    display: flex; flex-direction: column; align-items: center; text-align: center;
    padding: 0 1.5rem; position: relative; z-index: 1;
    transition: transform 0.3s;
  }
  .step:hover { transform: translateY(-6px); }
  .step-num {
    width: 5rem; height: 5rem; border-radius: 50%;
    background: var(--forest-mid); border: 2px solid rgba(201,168,76,0.4);
    display: flex; align-items: center; justify-content: center;
    font-family: 'Playfair Display', serif; font-size: 1.5rem; font-weight: 900;
    color: var(--gold); margin-bottom: 1.5rem;
    transition: background 0.3s, border-color 0.3s;
  }
  .step:hover .step-num { background: var(--gold); color: var(--ink); border-color: var(--gold); }
  .step-title { font-size: 0.88rem; font-weight: 700; color: #fff; margin-bottom: 0.5rem; letter-spacing: 0.02em; }
  .step-desc { font-size: 0.8rem; color: rgba(255,255,255,0.5); line-height: 1.6; }

  /* WHY PROFYD */
  #why { background: #fff; }
  .why-grid {
    display: grid; grid-template-columns: repeat(3, 1fr); gap: 2rem;
  }
  .why-card {
    padding: 2.5rem; border-radius: 4px; border: 1px solid var(--border);
    position: relative; overflow: hidden; transition: box-shadow 0.3s;
  }
  .why-card:hover { box-shadow: 0 12px 48px rgba(0,0,0,0.08); }
  .why-card.featured { background: var(--forest); border-color: var(--forest); }
  .why-card.featured .why-num { color: rgba(201,168,76,0.3); }
  .why-card.featured h3 { color: #fff; }
  .why-card.featured p { color: rgba(255,255,255,0.6); }
  .why-num {
    font-family: 'Playfair Display', serif; font-size: 4rem; font-weight: 900;
    color: rgba(0,0,0,0.05); line-height: 1; margin-bottom: 1rem;
  }
  .why-card h3 { font-family: 'Playfair Display', serif; font-size: 1.15rem; font-weight: 700; color: var(--forest); margin-bottom: 0.7rem; }
  .why-card p { font-size: 0.88rem; color: var(--warm-grey); line-height: 1.75; }
  .why-card .badge {
    display: inline-flex; align-items: center; gap: 0.4rem;
    background: rgba(201,168,76,0.15); color: var(--gold);
    font-size: 0.72rem; font-weight: 700; letter-spacing: 0.08em;
    text-transform: uppercase; padding: 0.3rem 0.8rem; border-radius: 2px;
    margin-bottom: 1rem;
  }

  /* SUBJECTS */
  #subjects { background: var(--cream); }
  .subjects-header { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 3rem; flex-wrap: wrap; gap: 1rem; }
  .subjects-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 1rem;
  }
  .subject-card {
    background: #fff; border: 1px solid var(--border); border-radius: 4px;
    padding: 2rem 1.5rem; text-align: center;
    transition: box-shadow 0.3s, transform 0.3s, background 0.3s;
    cursor: pointer;
  }
  .subject-card:hover { background: var(--forest); box-shadow: 0 12px 32px rgba(26,58,46,0.2); transform: translateY(-4px); }
  .subject-card:hover .subject-icon { transform: scale(1.2); }
  .subject-card:hover .subject-name { color: #fff; }
  .subject-card:hover .subject-level { color: rgba(255,255,255,0.6); }
  .subject-icon { font-size: 2rem; margin-bottom: 0.8rem; display: block; transition: transform 0.3s; }
  .subject-name { font-weight: 700; font-size: 0.9rem; color: var(--forest); margin-bottom: 0.2rem; }
  .subject-level { font-size: 0.75rem; color: var(--warm-grey); }

  /* POLICY BANNER */
  .policy-banner {
    background: var(--gold); padding: 4rem 5%;
    display: flex; align-items: center; justify-content: space-between;
    gap: 2rem; flex-wrap: wrap;
  }
  .policy-text h2 {
    font-family: 'Playfair Display', serif; font-size: 2rem;
    font-weight: 900; color: var(--ink); margin-bottom: 0.5rem;
  }
  .policy-text p { font-size: 0.95rem; color: rgba(10,10,15,0.7); max-width: 520px; line-height: 1.7; }
  .policy-features { display: flex; gap: 2rem; flex-wrap: wrap; }
  .policy-feat { display: flex; align-items: center; gap: 0.6rem; }
  .policy-feat .check { font-size: 1.1rem; }
  .policy-feat span { font-size: 0.88rem; font-weight: 700; color: var(--ink); }

  /* APPLY */
  #apply { background: var(--ink); padding: 8rem 5%; }
  #apply .section-title { color: #fff; }
  #apply .section-sub { color: rgba(255,255,255,0.55); }
  .apply-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: start; }
  .apply-form { display: flex; flex-direction: column; gap: 1.2rem; }
  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
  .form-group { display: flex; flex-direction: column; gap: 0.5rem; }
  .form-group label { font-size: 0.8rem; font-weight: 600; letter-spacing: 0.05em; text-transform: uppercase; color: rgba(255,255,255,0.5); }
  .form-group input,
  .form-group select,
  .form-group textarea {
    background: rgba(255,255,255,0.06);
    border: 1px solid rgba(255,255,255,0.12);
    color: #fff; font-family: 'DM Sans', sans-serif;
    font-size: 0.95rem; padding: 0.85rem 1.1rem; border-radius: 3px;
    outline: none; transition: border-color 0.2s, background 0.2s;
    appearance: none;
  }
  .form-group input::placeholder,
  .form-group textarea::placeholder { color: rgba(255,255,255,0.3); }
  .form-group input:focus,
  .form-group select:focus,
  .form-group textarea:focus {
    border-color: var(--gold); background: rgba(255,255,255,0.1);
  }
  .form-group select option { background: #1a1a1a; }
  .form-group textarea { resize: vertical; min-height: 120px; }
  .apply-info { padding-top: 0.5rem; }
  .apply-info h3 {
    font-family: 'Playfair Display', serif; font-size: 1.5rem;
    font-weight: 700; color: #fff; margin-bottom: 1.5rem;
  }
  .info-list { display: flex; flex-direction: column; gap: 1.2rem; }
  .info-item { display: flex; gap: 1rem; align-items: flex-start; }
  .info-dot {
    width: 8px; height: 8px; border-radius: 50%;
    background: var(--gold); margin-top: 0.45rem; flex-shrink: 0;
  }
  .info-item p { font-size: 0.9rem; color: rgba(255,255,255,0.65); line-height: 1.7; }
  .info-item strong { color: #fff; }

  /* FOOTER */
  footer {
    background: #060609; padding: 4rem 5% 2rem;
    border-top: 1px solid rgba(255,255,255,0.05);
  }
  .footer-grid { display: grid; grid-template-columns: 2fr 1fr 1fr 1fr; gap: 3rem; margin-bottom: 3rem; }
  .footer-brand .logo-f {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem; font-weight: 900; color: #fff; margin-bottom: 1rem; display: block;
  }
  .footer-brand .logo-f span { color: var(--gold); }
  .footer-brand p { font-size: 0.85rem; color: rgba(255,255,255,0.4); line-height: 1.8; max-width: 280px; }
  .footer-col h4 { font-size: 0.78rem; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; color: var(--gold); margin-bottom: 1.2rem; }
  .footer-col ul { list-style: none; display: flex; flex-direction: column; gap: 0.6rem; }
  .footer-col ul a { font-size: 0.85rem; color: rgba(255,255,255,0.45); text-decoration: none; transition: color 0.2s; }
  .footer-col ul a:hover { color: #fff; }
  .footer-bottom {
    border-top: 1px solid rgba(255,255,255,0.07);
    padding-top: 1.5rem; display: flex; justify-content: space-between;
    align-items: center; flex-wrap: wrap; gap: 1rem;
  }
  .footer-bottom p { font-size: 0.8rem; color: rgba(255,255,255,0.25); }
  .footer-links { display: flex; gap: 1.5rem; }
  .footer-links a { font-size: 0.8rem; color: rgba(255,255,255,0.25); text-decoration: none; transition: color 0.2s; }
  .footer-links a:hover { color: rgba(255,255,255,0.6); }

  /* NOTIFY TOAST */
  #toast {
    position: fixed; bottom: 2rem; right: 2rem; z-index: 999;
    background: var(--forest); color: #fff;
    padding: 1rem 1.5rem; border-radius: 4px;
    font-size: 0.9rem; font-weight: 500;
    box-shadow: 0 8px 32px rgba(0,0,0,0.2);
    transform: translateY(120%); opacity: 0;
    transition: all 0.4s cubic-bezier(0.34,1.56,0.64,1);
    display: flex; align-items: center; gap: 0.8rem;
  }
  #toast.show { transform: translateY(0); opacity: 1; }
  #toast .toast-icon { font-size: 1.2rem; }

  /* RESPONSIVE */
  @media (max-width: 1024px) {
    .hero { grid-template-columns: 1fr; min-height: auto; }
    .hero-left { padding: 10rem 5% 4rem; }
    .hero-right { padding: 4rem 5% 6rem; }
    #about { grid-template-columns: 1fr; }
    .about-visual { display: none; }
    .steps { grid-template-columns: repeat(3, 1fr); gap: 2rem; }
    .steps::before { display: none; }
    .why-grid { grid-template-columns: 1fr 1fr; }
    .apply-grid { grid-template-columns: 1fr; }
    .footer-grid { grid-template-columns: 1fr 1fr; }
  }
  @media (max-width: 768px) {
    .nav-links, .nav-cta { display: none; }
    .hamburger { display: flex; }
    .hero-stats { grid-template-columns: 1fr 1fr; }
    .steps { grid-template-columns: 1fr 1fr; }
    .why-grid { grid-template-columns: 1fr; }
    .form-row { grid-template-columns: 1fr; }
    .footer-grid { grid-template-columns: 1fr; }
    .policy-banner { flex-direction: column; }
  }

  /* SCROLL REVEAL */
  .reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }
</style>
</head>
<body>

<!-- NAV -->
<nav id="navbar">
  <a href="#" class="nav-logo">Pro<span>fyd</span></a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#hiring">Roles</a></li>
    <li><a href="#process">Process</a></li>
    <li><a href="#subjects">Subjects</a></li>
    <li><a href="#why">Why Us</a></li>
  </ul>
  <a href="#apply" class="nav-cta">Apply Now</a>
  <div class="hamburger" id="hamburger">
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-left">
    <span class="hero-tag">🇵🇰 Lahore, Pakistan · Est. 2024</span>
    <h1 class="hero-title">
      Build a Career<br>with <em>International</em><br>Exposure
    </h1>
    <p class="hero-sub">
      Profyd connects skilled professionals and educators in Lahore with structured, long-term opportunities serving global markets — no fees, no hidden charges, just merit.
    </p>
    <div class="hero-btns">
      <a href="#hiring" class="btn-primary">Explore Roles</a>
      <a href="#process" class="btn-outline">How It Works</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="hero-stats">
      <div class="stat-card">
        <div class="stat-num">6+</div>
        <div class="stat-label">Countries Served</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">0</div>
        <div class="stat-label">Recruitment Fees</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">8+</div>
        <div class="stat-label">Subject Specialisms</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">100%</div>
        <div class="stat-label">Merit-Based Hiring</div>
      </div>
    </div>
    <div class="hero-promise">
      <p>
        Profyd serves clients in the <strong>UK, US, Australia, Canada, Ireland,</strong> and <strong>New Zealand</strong> — with all operations based out of our professional in-office hub in Lahore.
      </p>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="about-visual">
    <div class="about-img-box">
      <div class="about-icon-grid">
        <div class="about-icon-cell"><span class="icon">📚</span><span class="lbl">Education</span></div>
        <div class="about-icon-cell"><span class="icon">🌍</span><span class="lbl">Global</span></div>
        <div class="about-icon-cell"><span class="icon">💼</span><span class="lbl">Careers</span></div>
        <div class="about-icon-cell"><span class="icon">⭐</span><span class="lbl">Merit</span></div>
      </div>
    </div>
    <div class="about-badge">
      Lahore HQ
      <span>Pakistan's Premier Hiring Platform</span>
    </div>
  </div>
  <div class="about-content reveal">
    <span class="section-label">About Profyd</span>
    <h2 class="section-title">More Than a Job Portal — A Structured Career Ecosystem</h2>
    <p class="section-sub">Profyd is a dedicated recruitment and talent sourcing platform. We focus on quality placements, ethical hiring, and long-term professional development for candidates in Pakistan serving global clients.</p>
    <div class="pillars">
      <div class="pillar">
        <span class="pillar-icon">🎯</span>
        <div>
          <h4>Specialized Focus</h4>
          <p>Not a generic job board — we recruit for structured roles aligned with international tutoring and business support services.</p>
        </div>
      </div>
      <div class="pillar">
        <span class="pillar-icon">🔒</span>
        <div>
          <h4>Zero-Fee Guarantee</h4>
          <p>No registration fees, no placement fees, no hidden charges. Every candidate deserves equal access to opportunity.</p>
        </div>
      </div>
      <div class="pillar">
        <span class="pillar-icon">📈</span>
        <div>
          <h4>Long-Term Growth Paths</h4>
          <p>From Tutor to Academic Coordinator to Training Manager — we invest in your career trajectory.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- POLICY BANNER -->
<div class="policy-banner">
  <div class="policy-text">
    <h2>Zero Recruitment Fees. Always.</h2>
    <p>Profyd strictly prohibits charging candidates at any stage of the recruitment process. Our model is built on trust, transparency, and equal access to opportunity.</p>
  </div>
  <div class="policy-features">
    <div class="policy-feat"><span class="check">✓</span><span>No Registration Fees</span></div>
    <div class="policy-feat"><span class="check">✓</span><span>No Interview Charges</span></div>
    <div class="policy-feat"><span class="check">✓</span><span>No Placement Fees</span></div>
    <div class="policy-feat"><span class="check">✓</span><span>Fully Transparent</span></div>
  </div>
</div>

<!-- HIRING -->
<section id="hiring">
  <div style="text-align:center; margin-bottom:3rem;" class="reveal">
    <span class="section-label">Open Opportunities</span>
    <h2 class="section-title" style="max-width:100%; margin:0 auto 1rem;">Roles We Hire For</h2>
    <p class="section-sub" style="max-width:600px; margin:0 auto;">Two core streams — in-office tutoring for international students, and corporate &amp; technical roles to support global service delivery.</p>
  </div>
  <div class="hiring-grid">
    <div class="role-card reveal" onclick="document.getElementById('apply').scrollIntoView({behavior:'smooth'})">
      <div class="role-icon">🎓</div>
      <div class="role-title">In-Office Tutor</div>
      <div class="role-desc">Teach UK, US, and international curriculum students through online sessions conducted from our Lahore office. Ideal for subject specialists passionate about education.</div>
      <div class="role-tags">
        <span class="tag">Office-Based</span>
        <span class="tag">International Students</span>
        <span class="tag">Lahore</span>
      </div>
    </div>
    <div class="role-card reveal" onclick="document.getElementById('apply').scrollIntoView({behavior:'smooth'})">
      <div class="role-icon">📊</div>
      <div class="role-title">SEO & Digital Marketing</div>
      <div class="role-desc">Drive organic growth and manage content strategy for international markets. Expertise in EEAT, link-building, and keyword research preferred.</div>
      <div class="role-tags">
        <span class="tag">Full-Time</span>
        <span class="tag">Content Strategy</span>
        <span class="tag">SEO</span>
      </div>
    </div>
    <div class="role-card reveal" onclick="document.getElementById('apply').scrollIntoView({behavior:'smooth'})">
      <div class="role-icon">💻</div>
      <div class="role-title">Web Developer</div>
      <div class="role-desc">Build and maintain professional websites using modern tools including Elementor, WordPress, and custom development. Experience with ATS integration is a plus.</div>
      <div class="role-tags">
        <span class="tag">WordPress</span>
        <span class="tag">Frontend</span>
        <span class="tag">UI/UX</span>
      </div>
    </div>
    <div class="role-card reveal" onclick="document.getElementById('apply').scrollIntoView({behavior:'smooth'})">
      <div class="role-icon">🤝</div>
      <div class="role-title">Sales & Customer Support</div>
      <div class="role-desc">Engage with international clients, manage inquiries, and build lasting relationships. Strong communication skills in English are essential.</div>
      <div class="role-tags">
        <span class="tag">B2B & B2C</span>
        <span class="tag">CRM</span>
        <span class="tag">English Required</span>
      </div>
    </div>
    <div class="role-card reveal" onclick="document.getElementById('apply').scrollIntoView({behavior:'smooth'})">
      <div class="role-icon">🎨</div>
      <div class="role-title">Graphic Designer</div>
      <div class="role-desc">Create compelling visual content for digital and print channels. Proficiency in Adobe Suite and familiarity with brand guidelines required.</div>
      <div class="role-tags">
        <span class="tag">Adobe Suite</span>
        <span class="tag">Branding</span>
        <span class="tag">Digital Assets</span>
      </div>
    </div>
    <div class="role-card reveal" onclick="document.getElementById('apply').scrollIntoView({behavior:'smooth'})">
      <div class="role-icon">👥</div>
      <div class="role-title">HR Professional</div>
      <div class="role-desc">Support talent acquisition, onboarding, and employee development. Help maintain Profyd's culture of merit, transparency, and professional growth.</div>
      <div class="role-tags">
        <span class="tag">Talent Acquisition</span>
        <span class="tag">Onboarding</span>
        <span class="tag">HR Ops</span>
      </div>
    </div>
  </div>
</section>

<!-- SUBJECTS -->
<section id="subjects">
  <div class="subjects-header reveal">
    <div>
      <span class="section-label">Tutoring Subjects</span>
      <h2 class="section-title" style="margin-bottom:0;">Subjects We Specialize In</h2>
    </div>
    <a href="#apply" class="btn-primary" style="text-decoration:none;">Apply as Tutor</a>
  </div>
  <div class="subjects-grid">
    <div class="subject-card reveal">
      <span class="subject-icon">➕</span>
      <div class="subject-name">Mathematics</div>
      <div class="subject-level">GCSE · A-Level · SAT</div>
    </div>
    <div class="subject-card reveal">
      <span class="subject-icon">📖</span>
      <div class="subject-name">English</div>
      <div class="subject-level">Literature · Language</div>
    </div>
    <div class="subject-card reveal">
      <span class="subject-icon">⚛️</span>
      <div class="subject-name">Physics</div>
      <div class="subject-level">GCSE · A-Level</div>
    </div>
    <div class="subject-card reveal">
      <span class="subject-icon">🧪</span>
      <div class="subject-name">Chemistry</div>
      <div class="subject-level">GCSE · A-Level · IB</div>
    </div>
    <div class="subject-card reveal">
      <span class="subject-icon">🧬</span>
      <div class="subject-name">Biology</div>
      <div class="subject-level">GCSE · A-Level · AP</div>
    </div>
    <div class="subject-card reveal">
      <span class="subject-icon">💻</span>
      <div class="subject-name">Computer Science</div>
      <div class="subject-level">GCSE · A-Level</div>
    </div>
    <div class="subject-card reveal">
      <span class="subject-icon">📈</span>
      <div class="subject-name">Business Studies</div>
      <div class="subject-level">GCSE · A-Level · IB</div>
    </div>
    <div class="subject-card reveal">
      <span class="subject-icon">🌐</span>
      <div class="subject-name">Other Subjects</div>
      <div class="subject-level">Ask About Availability</div>
    </div>
  </div>
</section>

<!-- PROCESS -->
<section id="process">
  <div style="text-align:center; margin-bottom:4rem;" class="reveal">
    <span class="section-label">Recruitment Process</span>
    <h2 class="section-title" style="max-width:100%; margin:0 auto 1rem; color:#fff;">A Fair & Structured Path to Hire</h2>
    <p class="section-sub" style="max-width:560px; margin:0 auto;">Every candidate goes through the same transparent process — no shortcuts, no favouritism.</p>
  </div>
  <div class="steps">
    <div class="step reveal">
      <div class="step-num">01</div>
      <div class="step-title">Application</div>
      <div class="step-desc">Submit your application via our official website with your qualifications and experience.</div>
    </div>
    <div class="step reveal">
      <div class="step-num">02</div>
      <div class="step-title">Screening</div>
      <div class="step-desc">Our HR team reviews your profile for relevance, qualifications, and role fit.</div>
    </div>
    <div class="step reveal">
      <div class="step-num">03</div>
      <div class="step-title">Assessment</div>
      <div class="step-desc">Complete a subject test or skills evaluation tailored to your applied role.</div>
    </div>
    <div class="step reveal">
      <div class="step-num">04</div>
      <div class="step-title">Interview</div>
      <div class="step-desc">Attend an interview assessing communication, expertise, and cultural alignment.</div>
    </div>
    <div class="step reveal">
      <div class="step-num">05</div>
      <div class="step-title">Offer</div>
      <div class="step-desc">Receive a formal job offer and begin your professional journey with Profyd.</div>
    </div>
  </div>
</section>

<!-- WHY PROFYD -->
<section id="why">
  <div style="text-align:center; margin-bottom:3rem;" class="reveal">
    <span class="section-label">Why Choose Profyd</span>
    <h2 class="section-title" style="max-width:100%; margin:0 auto;">What Sets Us Apart</h2>
  </div>
  <div class="why-grid">
    <div class="why-card reveal">
      <div class="why-num">01</div>
      <div class="badge">🌍 Global Reach</div>
      <h3>International Exposure from Lahore</h3>
      <p>Work with students and clients from the UK, US, Australia, Canada, Ireland, and New Zealand — all from our professional Lahore office.</p>
    </div>
    <div class="why-card featured reveal">
      <div class="why-num">02</div>
      <div class="badge">⭐ Core Value</div>
      <h3>100% Merit-Based Selection</h3>
      <p>We evaluate every candidate purely on skills, qualifications, and performance. No connections required — just your ability to deliver.</p>
    </div>
    <div class="why-card reveal">
      <div class="why-num">03</div>
      <div class="badge">📈 Career Growth</div>
      <h3>Structured Career Advancement</h3>
      <p>Clear growth paths from Tutor to Senior Tutor, Academic Coordinator, Team Lead, and beyond. Performance drives promotion.</p>
    </div>
    <div class="why-card reveal">
      <div class="why-num">04</div>
      <div class="badge">🔒 Ethical Hiring</div>
      <h3>Zero Fees, Maximum Trust</h3>
      <p>Profyd never charges candidates. No registration, interview, processing, or placement fees — ever. Period.</p>
    </div>
    <div class="why-card reveal">
      <div class="why-num">05</div>
      <div class="badge">🏢 Office Culture</div>
      <h3>Professional Work Environment</h3>
      <p>Structured schedules, skill enhancement training, and a performance-based culture that rewards consistency and growth.</p>
    </div>
    <div class="why-card reveal">
      <div class="why-num">06</div>
      <div class="badge">🎯 Specialization</div>
      <h3>Purpose-Built Platform</h3>
      <p>Not a generic job portal — every role at Profyd is aligned with delivering quality international education and business services.</p>
    </div>
  </div>
</section>

<!-- APPLY -->
<section id="apply">
  <div class="apply-grid">
    <div class="reveal">
      <span class="section-label">Join Profyd</span>
      <h2 class="section-title" style="color:#fff;">Apply for a Role Today</h2>
      <p class="section-sub">Submit your application below. Our HR team will review and get back to you within 5 business days. No fees at any stage.</p>
      <div class="apply-form">
        <div class="form-row">
          <div class="form-group">
            <label>First Name</label>
            <input type="text" placeholder="Ahmad"/>
          </div>
          <div class="form-group">
            <label>Last Name</label>
            <input type="text" placeholder="Khan"/>
          </div>
        </div>
        <div class="form-group">
          <label>Email Address</label>
          <input type="email" placeholder="you@email.com"/>
        </div>
        <div class="form-group">
          <label>Phone Number</label>
          <input type="tel" placeholder="+92 300 0000000"/>
        </div>
        <div class="form-group">
          <label>Role Applying For</label>
          <select>
            <option value="" disabled selected>Select a role...</option>
            <option>In-Office Tutor</option>
            <option>SEO Specialist</option>
            <option>Digital Marketing Expert</option>
            <option>Web Developer</option>
            <option>Sales Executive</option>
            <option>Customer Support Representative</option>
            <option>Graphic Designer</option>
            <option>HR Professional</option>
          </select>
        </div>
        <div class="form-group">
          <label>Tell Us About Yourself</label>
          <textarea placeholder="Share your qualifications, relevant experience, and why you want to join Profyd..."></textarea>
        </div>
        <button class="btn-primary" onclick="showToast()" style="width:100%; padding:1.1rem; font-size:1rem;">Submit Application →</button>
      </div>
    </div>
    <div class="apply-info reveal">
      <h3>What Happens Next?</h3>
      <div class="info-list">
        <div class="info-item">
          <div class="info-dot"></div>
          <p><strong>Step 1 — Review:</strong> Our HR team will review your application within 2–3 working days.</p>
        </div>
        <div class="info-item">
          <div class="info-dot"></div>
          <p><strong>Step 2 — Assessment:</strong> Shortlisted candidates will receive a subject or skills test.</p>
        </div>
        <div class="info-item">
          <div class="info-dot"></div>
          <p><strong>Step 3 — Interview:</strong> Selected applicants will be invited for a structured interview.</p>
        </div>
        <div class="info-item">
          <div class="info-dot"></div>
          <p><strong>Step 4 — Offer:</strong> Successful candidates receive a formal offer letter.</p>
        </div>
        <div class="info-item">
          <div class="info-dot"></div>
          <p><strong>Zero Fees:</strong> At no point will you ever be charged for any stage of this process.</p>
        </div>
      </div>
      <div style="margin-top:3rem; padding:2rem; border:1px solid rgba(255,255,255,0.1); border-radius:4px;">
        <p style="font-size:0.85rem; color:rgba(255,255,255,0.5); margin-bottom:0.5rem; font-weight:600; text-transform:uppercase; letter-spacing:0.08em;">Official Website</p>
        <a href="https://profyd.com" target="_blank" style="color:var(--gold); font-size:1.1rem; font-weight:700; text-decoration:none;">profyd.com →</a>
        <p style="font-size:0.82rem; color:rgba(255,255,255,0.35); margin-top:1rem; line-height:1.6;">All applications are processed exclusively through official Profyd channels. Beware of fraudulent third-party listings.</p>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-grid">
    <div class="footer-brand">
      <a href="#" class="logo-f">Pro<span>fyd</span></a>
      <p>Pakistan's premier structured hiring platform connecting skilled professionals in Lahore with international career opportunities. Ethical. Transparent. Merit-first.</p>
    </div>
    <div class="footer-col">
      <h4>Company</h4>
      <ul>
        <li><a href="#about">About Us</a></li>
        <li><a href="#why">Why Profyd</a></li>
        <li><a href="#process">Our Process</a></li>
        <li><a href="https://profyd.com" target="_blank">Official Website</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Opportunities</h4>
      <ul>
        <li><a href="#hiring">Tutor Roles</a></li>
        <li><a href="#hiring">Corporate Roles</a></li>
        <li><a href="#hiring">Tech Roles</a></li>
        <li><a href="#subjects">Subjects</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Markets Served</h4>
      <ul>
        <li><a href="#about">🇬🇧 United Kingdom</a></li>
        <li><a href="#about">🇺🇸 United States</a></li>
        <li><a href="#about">🇦🇺 Australia</a></li>
        <li><a href="#about">🇨🇦 Canada</a></li>
        <li><a href="#about">🇮🇪 Ireland</a></li>
        <li><a href="#about">🇳🇿 New Zealand</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <p>© 2024 Profyd. All rights reserved. Based in Lahore, Pakistan.</p>
    <div class="footer-links">
      <a href="#">Privacy Policy</a>
      <a href="#">Terms of Use</a>
      <a href="https://profyd.com" target="_blank">profyd.com</a>
    </div>
  </div>
</footer>

<!-- TOAST -->
<div id="toast">
  <span class="toast-icon">✅</span>
  Application submitted! We'll be in touch within 5 business days.
</div>

<script>
  // NAV SCROLL EFFECT
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    navbar.classList.toggle('scrolled', window.scrollY > 50);
  });

  // SCROLL REVEAL
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 60);
      }
    });
  }, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // TOAST
  function showToast() {
    const toast = document.getElementById('toast');
    toast.classList.add('show');
    setTimeout(() => toast.classList.remove('show'), 4000);
  }

  // HAMBURGER (mobile)
  document.getElementById('hamburger').addEventListener('click', () => {
    const links = document.querySelector('.nav-links');
    const cta = document.querySelector('.nav-cta');
    if (links) {
      links.style.display = links.style.display === 'flex' ? 'none' : 'flex';
      links.style.flexDirection = 'column';
      links.style.position = 'absolute';
      links.style.top = '70px';
      links.style.left = '0'; links.style.right = '0';
      links.style.background = 'var(--cream)';
      links.style.padding = '1.5rem 5%';
      links.style.borderBottom = '1px solid var(--border)';
      links.style.zIndex = '99';
    }
  });
</script>
</body>
</html>

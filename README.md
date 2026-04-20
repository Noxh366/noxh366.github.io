<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Alfonso Ortiz — Social Media Management</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400;1,700&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
:root{
  --dark:#080d0f;--lblue:#5b9cc4;--blue:#2077c2;--dblue:#0f5f8a;--red:#f02240;
  --white:#ffffff;--offwhite:#f7f9fb;--gray:#f2f5f8;--mgray:#d6dde5;--dg:#888;
  --text:#1a1a1a;--text2:#555;--text3:#888;
}
*{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{background:var(--white);font-family:'DM Sans',sans-serif;color:var(--text);overflow-x:hidden}
 
/* ── NAV ── */
nav{position:fixed;top:0;left:0;right:0;z-index:1000;background:rgba(8,13,15,.96);backdrop-filter:blur(16px);border-bottom:1px solid rgba(255,255,255,.06);padding:0 60px;height:64px;display:flex;align-items:center;justify-content:space-between;transition:all .3s}
.nav-logo{font-family:'Playfair Display',serif;font-size:28px;font-weight:700;color:var(--white);letter-spacing:-1px;text-decoration:none}
.nav-links{display:flex;gap:32px;list-style:none}
.nav-links a{font-size:12px;letter-spacing:1.5px;text-transform:uppercase;color:rgba(255,255,255,.5);text-decoration:none;transition:color .2s;font-weight:400}
.nav-links a:hover{color:var(--white)}
.nav-cta{font-size:11px;letter-spacing:1.5px;text-transform:uppercase;background:var(--blue);color:var(--white);padding:9px 20px;border-radius:4px;text-decoration:none;font-weight:500;transition:background .2s}
.nav-cta:hover{background:var(--dblue)}
.nav-mobile-btn{display:none;background:none;border:none;cursor:pointer;padding:4px}
.ham{display:block;width:22px;height:2px;background:var(--white);margin:5px 0;transition:all .25s}
.mobile-menu{display:none;position:fixed;inset:64px 0 0 0;background:rgba(8,13,15,.98);z-index:999;flex-direction:column;align-items:center;justify-content:center;gap:28px}
.mobile-menu.open{display:flex}
.mobile-menu a{font-size:18px;color:rgba(255,255,255,.7);text-decoration:none;font-weight:300;letter-spacing:1px}
 
/* ── STRIPE ── */
.stripe{display:flex;height:4px}
.stripe span{flex:1}
.s1{background:var(--dark);flex:3!important}.s2{background:var(--lblue)}.s3{background:var(--blue)}.s4{background:var(--dblue)}.s5{background:var(--red)}
 
/* ── HERO ── */
.hero{min-height:100vh;background:var(--dark);display:flex;flex-direction:column;justify-content:flex-end;padding:140px 80px 80px;position:relative;overflow:hidden}
.hero-circles{position:absolute;inset:0;pointer-events:none}
.hero-circle{position:absolute;border-radius:50%;border:1px solid rgba(91,156,196,.07)}
.hero-eyebrow{font-size:10px;letter-spacing:5px;color:var(--red);text-transform:uppercase;font-weight:500;margin-bottom:16px;animation:fadeup .8s .1s both}
.hero-h{font-family:'Playfair Display',serif;font-size:clamp(52px,7vw,96px);font-weight:700;color:var(--white);line-height:1.03;margin-bottom:20px;animation:fadeup .8s .2s both}
.hero-h em{font-style:italic;color:var(--lblue)}
.hero-sub{font-size:18px;color:rgba(255,255,255,.45);font-weight:300;line-height:1.7;max-width:560px;margin-bottom:44px;animation:fadeup .8s .3s both}
.hero-actions{display:flex;gap:14px;align-items:center;flex-wrap:wrap;animation:fadeup .8s .4s both}
.btn-primary{background:var(--blue);color:var(--white);padding:14px 32px;border-radius:4px;font-size:13px;font-weight:500;text-decoration:none;letter-spacing:1px;text-transform:uppercase;transition:background .2s}
.btn-primary:hover{background:var(--dblue)}
.btn-outline{border:1px solid rgba(255,255,255,.2);color:rgba(255,255,255,.7);padding:14px 32px;border-radius:4px;font-size:13px;font-weight:400;text-decoration:none;letter-spacing:1px;text-transform:uppercase;transition:all .2s}
.btn-outline:hover{border-color:var(--white);color:var(--white)}
.hero-scroll{position:absolute;bottom:36px;right:60px;display:flex;flex-direction:column;align-items:center;gap:6px;animation:fadeup .8s .6s both}
.hero-scroll span{font-size:9px;letter-spacing:3px;color:rgba(255,255,255,.2);text-transform:uppercase;writing-mode:vertical-rl}
.scroll-line{width:1px;height:40px;background:linear-gradient(to bottom,rgba(255,255,255,.15),transparent)}
 
/* ── SECTION BASICS ── */
.section{padding:100px 80px}
.section.gray-bg{background:var(--offwhite)}
.section.dark-bg{background:var(--dark)}
.section-label{font-size:9px;letter-spacing:5px;color:var(--red);text-transform:uppercase;font-weight:500;margin-bottom:10px}
.section-title{font-family:'Playfair Display',serif;font-size:clamp(32px,4vw,52px);font-weight:700;color:var(--text);line-height:1.1;margin-bottom:16px}
.section-title.light{color:var(--white)}
.section-sub{font-size:16px;color:var(--text2);font-weight:300;line-height:1.7;max-width:640px;margin-bottom:52px}
.section-sub.light{color:rgba(255,255,255,.45)}
.divider-line{height:2px;background:var(--blue);width:48px;margin-bottom:40px}
 
/* ── SERVICES GRID ── */
.services-intro{display:grid;grid-template-columns:1fr 1fr;gap:80px;align-items:center;margin-bottom:80px}
.svc-intro-text{}
.svc-intro-stats{display:grid;grid-template-columns:1fr 1fr;gap:16px}
.stat-card{background:var(--dark);border-radius:8px;padding:24px;text-align:center}
.stat-num{font-family:'Playfair Display',serif;font-size:42px;font-weight:700;line-height:1;margin-bottom:6px}
.stat-lbl{font-size:11px;color:rgba(255,255,255,.38);letter-spacing:1px;font-weight:300;line-height:1.5}
 
.services-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:var(--mgray);border-radius:12px;overflow:hidden}
.svc-tile{background:var(--white);padding:36px 32px;transition:background .25s}
.svc-tile:hover{background:var(--gray)}
.svc-tile-num{font-family:'Playfair Display',serif;font-size:13px;color:var(--blue);font-weight:700;margin-bottom:14px;display:block}
.svc-tile-icon{width:40px;height:3px;border-radius:2px;margin-bottom:18px}
.svc-tile-t{font-family:'Playfair Display',serif;font-size:20px;font-weight:700;color:var(--text);margin-bottom:10px;line-height:1.2}
.svc-tile-d{font-size:13px;color:var(--text2);line-height:1.7;font-weight:300}
.svc-tile-tags{display:flex;flex-wrap:wrap;gap:5px;margin-top:14px}
.tag{font-size:9px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px;font-weight:500}
 
/* ── PLANS ── */
.plans-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}
.plan-card{border-radius:10px;overflow:hidden;transition:transform .25s}
.plan-card:hover{transform:translateY(-4px)}
.plan-head{background:var(--dark);padding:24px 26px}
.plan-badge{font-size:8px;letter-spacing:3px;text-transform:uppercase;font-weight:500;margin-bottom:7px;display:block}
.plan-name{font-family:'Playfair Display',serif;font-size:24px;font-weight:700;color:var(--white);margin-bottom:4px}
.plan-focus{font-size:12px;color:rgba(255,255,255,.35);font-style:italic}
.plan-price-row{background:var(--dark);padding:12px 26px;border-top:1px solid rgba(255,255,255,.07);display:flex;align-items:baseline;gap:3px}
.plan-price{font-family:'Playfair Display',serif;font-size:34px;font-weight:700;color:var(--white)}
.plan-cur{font-size:13px;color:rgba(255,255,255,.3)}
.plan-per{font-size:11px;color:rgba(255,255,255,.28);margin-left:3px}
.plan-feats{background:var(--gray);padding:20px 26px;display:flex;flex-direction:column;gap:9px}
.plan-feat{font-size:12.5px;color:#333;display:flex;gap:8px;align-items:flex-start;line-height:1.4}
.pf-dot{width:5px;height:5px;border-radius:50%;flex-shrink:0;margin-top:5px}
.pf-lbl{font-weight:500}
.pf-val{color:#666;font-weight:300}
 
/* ── PROCESS ── */
.process-grid{display:grid;grid-template-columns:repeat(6,1fr);gap:0;position:relative}
.process-grid::before{content:'';position:absolute;top:22px;left:11%;right:11%;height:1px;background:var(--mgray);z-index:0}
.process-step{display:flex;flex-direction:column;align-items:center;text-align:center;position:relative;z-index:1}
.ps-num{width:44px;height:44px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-family:'Playfair Display',serif;font-size:15px;font-weight:700;color:var(--white);margin-bottom:14px}
.ps-t{font-size:13px;font-weight:500;color:var(--text);margin-bottom:4px}
.ps-d{font-size:11px;color:var(--text2);font-weight:300;line-height:1.5;padding:0 4px}
 
 
.audit-grid{display:grid;grid-template-columns:1fr 1fr;gap:40px;align-items:center}
.audit-deliverables{display:flex;flex-direction:column;gap:10px}
.audit-item{background:rgba(255,255,255,.04);border-radius:8px;padding:18px 20px;border-left:3px solid var(--blue);display:flex;gap:16px;align-items:flex-start}
.audit-item.red{border-left-color:var(--red)}.audit-item.lblue{border-left-color:var(--lblue)}.audit-item.dblue{border-left-color:var(--dblue)}
.audit-num{font-family:'Playfair Display',serif;font-size:22px;font-weight:700;line-height:1;flex-shrink:0}
.audit-t{font-size:14px;font-weight:500;color:var(--white);margin-bottom:3px}
.audit-d{font-size:12px;color:rgba(255,255,255,.45);line-height:1.55;font-weight:300}
.audit-price-block{background:rgba(255,255,255,.04);border-radius:10px;padding:36px;border:1px solid rgba(255,255,255,.07)}
.audit-price-label{font-size:9px;letter-spacing:4px;text-transform:uppercase;color:var(--lblue);margin-bottom:12px}
.audit-big-price{font-family:'Playfair Display',serif;font-size:56px;font-weight:700;color:var(--white);line-height:1;margin-bottom:4px}
.audit-price-note{font-size:12px;color:rgba(255,255,255,.3);margin-bottom:24px;font-weight:300}
.audit-meta{display:flex;flex-direction:column;gap:8px}
.audit-meta-row{display:flex;gap:10px;align-items:center;font-size:13px;color:rgba(255,255,255,.5);font-weight:300}
.audit-meta-dot{width:5px;height:5px;border-radius:50%;flex-shrink:0}
 
/* ── BRAND SECTION ── */
.brand-grid{display:grid;grid-template-columns:1fr 1fr;gap:60px;align-items:start}
.brand-list{display:flex;flex-direction:column;gap:0}
.brand-item{padding:18px 0;border-bottom:1px solid var(--mgray);display:flex;gap:16px;align-items:flex-start}
.brand-item:last-child{border-bottom:none}
.bi-num{font-family:'Playfair Display',serif;font-size:11px;color:var(--blue);font-weight:700;flex-shrink:0;margin-top:2px}
.bi-t{font-size:15px;font-weight:500;color:var(--text);margin-bottom:4px}
.bi-d{font-size:13px;color:var(--text2);line-height:1.6;font-weight:300}
.brand-cta-box{background:var(--dark);border-radius:12px;padding:36px;position:sticky;top:84px}
.bcb-label{font-size:9px;letter-spacing:4px;text-transform:uppercase;color:var(--lblue);margin-bottom:12px}
.bcb-title{font-family:'Playfair Display',serif;font-size:28px;font-weight:700;color:var(--white);line-height:1.2;margin-bottom:14px}
.bcb-price{font-family:'Playfair Display',serif;font-size:42px;font-weight:700;color:var(--white);margin-bottom:4px}
.bcb-note{font-size:12px;color:rgba(255,255,255,.3);margin-bottom:24px;font-weight:300}
.bcb-items{display:flex;flex-direction:column;gap:6px;margin-bottom:24px}
.bcb-item{display:flex;gap:9px;align-items:flex-start;font-size:13px;color:rgba(255,255,255,.55);font-weight:300;line-height:1.4}
.bcb-dot{width:4px;height:4px;border-radius:50%;flex-shrink:0;margin-top:7px}
 
/* ── DESIGN SECTION ── */
.design-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px}
.design-card{border-radius:8px;overflow:hidden;background:var(--gray)}
.dc-head{padding:20px 20px 14px;border-bottom:1px solid var(--mgray)}
.dc-accent{height:3px;border-radius:2px;margin-bottom:14px}
.dc-t{font-size:16px;font-weight:500;color:var(--text);margin-bottom:4px}
.dc-price{font-family:'Playfair Display',serif;font-size:22px;font-weight:700;color:var(--dark)}
.dc-body{padding:16px 20px}
.dc-items{list-style:none;display:flex;flex-direction:column;gap:6px}
.dc-items li{font-size:12px;color:var(--text2);font-weight:300;padding-left:14px;position:relative;line-height:1.55}
.dc-items li::before{content:'▸';position:absolute;left:0;color:var(--blue);font-size:8px;top:3px}
 
/* ── CTA SECTION ── */
.cta-section{background:var(--dark);text-align:center;padding:120px 80px;position:relative;overflow:hidden}
.cta-circles{position:absolute;inset:0;pointer-events:none}
.cta-circle{position:absolute;border-radius:50%;border:1px solid rgba(91,156,196,.06)}
.cta-tagline{font-family:'Playfair Display',serif;font-size:clamp(36px,5vw,68px);font-weight:700;color:var(--white);line-height:1.1;margin-bottom:18px}
.cta-tagline em{font-style:italic;color:var(--lblue)}
.cta-sub{font-size:17px;color:rgba(255,255,255,.4);font-weight:300;line-height:1.7;max-width:520px;margin:0 auto 44px}
.cta-contacts{display:flex;gap:36px;justify-content:center;flex-wrap:wrap;margin-bottom:48px}
.cta-contact{display:flex;align-items:center;gap:10px;font-size:15px;color:rgba(255,255,255,.65);font-weight:300}
.cta-contact strong{color:var(--white);font-weight:400}
.cc-dot{width:6px;height:6px;border-radius:50%}
 
/* ── FOOTER ── */
footer{background:#040709;padding:40px 80px;display:flex;justify-content:space-between;align-items:center;flex-wrap:gap}
.footer-logo{font-family:'Playfair Display',serif;font-size:22px;font-weight:700;color:var(--white);letter-spacing:-1px}
.footer-tagline{font-size:11px;color:rgba(255,255,255,.2);letter-spacing:2px;margin-top:3px}
.footer-links{display:flex;gap:24px;list-style:none}
.footer-links a{font-size:11px;letter-spacing:1.5px;text-transform:uppercase;color:rgba(255,255,255,.3);text-decoration:none;transition:color .2s}
.footer-links a:hover{color:rgba(255,255,255,.7)}
.footer-legal{font-size:11px;color:rgba(255,255,255,.15)}
 
/* ── ANIMATIONS ── */
@keyframes fadeup{from{opacity:0;transform:translateY(28px)}to{opacity:1;transform:translateY(0)}}
@keyframes fadein{from{opacity:0}to{opacity:1}}
@keyframes slideleft{from{opacity:0;transform:translateX(40px)}to{opacity:1;transform:translateX(0)}}
@keyframes slideright{from{opacity:0;transform:translateX(-40px)}to{opacity:1;transform:translateX(0)}}
@keyframes scaleup{from{opacity:0;transform:scale(.92)}to{opacity:1;transform:scale(1)}}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.5}}
@keyframes scrollbar{0%{transform:translateY(0)}50%{transform:translateY(14px)}100%{transform:translateY(0)}}
@keyframes stripe-slide{from{transform:translateX(-100%)}to{transform:translateX(100%)}}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-12px)}}
@keyframes spin-slow{from{transform:rotate(0deg)}to{transform:rotate(360deg)}}
@keyframes count-in{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:translateY(0)}}
 
/* reveal base — 4 variants */
.reveal{opacity:0;transform:translateY(28px);transition:opacity .7s cubic-bezier(.22,.61,.36,1),transform .7s cubic-bezier(.22,.61,.36,1)}
.reveal.visible{opacity:1;transform:none}
.reveal-left{opacity:0;transform:translateX(-36px);transition:opacity .7s .1s cubic-bezier(.22,.61,.36,1),transform .7s .1s cubic-bezier(.22,.61,.36,1)}
.reveal-left.visible{opacity:1;transform:none}
.reveal-right{opacity:0;transform:translateX(36px);transition:opacity .7s .15s cubic-bezier(.22,.61,.36,1),transform .7s .15s cubic-bezier(.22,.61,.36,1)}
.reveal-right.visible{opacity:1;transform:none}
.reveal-scale{opacity:0;transform:scale(.93);transition:opacity .65s .1s cubic-bezier(.22,.61,.36,1),transform .65s .1s cubic-bezier(.22,.61,.36,1)}
.reveal-scale.visible{opacity:1;transform:scale(1)}
 
/* stagger children */
.stagger > *{opacity:0;transform:translateY(22px);transition:opacity .6s cubic-bezier(.22,.61,.36,1),transform .6s cubic-bezier(.22,.61,.36,1)}
.stagger.visible > *:nth-child(1){opacity:1;transform:none;transition-delay:.05s}
.stagger.visible > *:nth-child(2){opacity:1;transform:none;transition-delay:.15s}
.stagger.visible > *:nth-child(3){opacity:1;transform:none;transition-delay:.25s}
.stagger.visible > *:nth-child(4){opacity:1;transform:none;transition-delay:.35s}
.stagger.visible > *:nth-child(5){opacity:1;transform:none;transition-delay:.45s}
.stagger.visible > *:nth-child(6){opacity:1;transform:none;transition-delay:.55s}
 
/* scroll indicator animate */
.scroll-dot{width:4px;height:4px;border-radius:50%;background:rgba(255,255,255,.4);animation:scrollbar 1.8s ease-in-out infinite}
 
/* stripe shimmer */
.stripe-shimmer{position:relative;overflow:hidden}
.stripe-shimmer::after{content:'';position:absolute;inset:0;background:linear-gradient(90deg,transparent,rgba(255,255,255,.18),transparent);transform:translateX(-100%);animation:stripe-slide 2.2s 1s ease both}
 
/* hero circles float */
.hero-circle:nth-child(1){animation:float 8s ease-in-out infinite}
.hero-circle:nth-child(2){animation:float 11s 2s ease-in-out infinite}
.hero-circle:nth-child(3){animation:float 9s 4s ease-in-out infinite}
 
/* service tile hover */
.svc-tile{transition:background .25s,transform .25s,box-shadow .25s}
.svc-tile:hover{transform:translateY(-4px);box-shadow:0 12px 32px rgba(32,119,194,.1)}
.svc-tile-icon{transition:width .3s}
.svc-tile:hover .svc-tile-icon{width:56px}
 
/* plan card hover */
.plan-card{transition:transform .28s cubic-bezier(.22,.61,.36,1),box-shadow .28s}
.plan-card:hover{transform:translateY(-6px);box-shadow:0 20px 48px rgba(0,0,0,.12)}
 
/* btn hover lift */
.btn-primary{transition:background .2s,transform .18s,box-shadow .18s}
.btn-primary:hover{background:var(--dblue);transform:translateY(-2px);box-shadow:0 8px 24px rgba(32,119,194,.28)}
.btn-primary:active{transform:translateY(0);box-shadow:none}
.btn-outline{transition:all .2s,transform .18s}
.btn-outline:hover{transform:translateY(-2px)}
 
/* nav link underline effect */
.nav-links a{position:relative}
.nav-links a::after{content:'';position:absolute;left:0;bottom:-4px;height:1px;width:0;background:var(--blue);transition:width .25s}
.nav-links a:hover::after{width:100%}
 
/* stat card hover */
.stat-card{transition:transform .25s,background .25s}
.stat-card:hover{transform:translateY(-3px);background:#111a1f}
 
/* audit item hover */
.audit-item{transition:background .22s,transform .22s}
.audit-item:hover{background:rgba(255,255,255,.07);transform:translateX(4px)}
 
/* brand item hover */
.brand-item{transition:background .2s}
.brand-item:hover{background:var(--gray);padding-left:8px;padding-right:8px;border-radius:6px;transition:background .2s,padding .2s}
 
/* design card hover */
.design-card{transition:transform .25s,box-shadow .25s}
.design-card:hover{transform:translateY(-4px);box-shadow:0 14px 36px rgba(0,0,0,.08)}
 
/* process step hover */
.process-step{transition:transform .2s}
.process-step:hover{transform:translateY(-5px)}
.ps-num{transition:transform .2s,box-shadow .2s}
.process-step:hover .ps-num{transform:scale(1.12);box-shadow:0 6px 18px rgba(0,0,0,.2)}
 
/* counter num */
.stat-num{display:inline-block;transition:transform .3s}
.stat-card:hover .stat-num{transform:scale(1.08)}
 
/* section label accent line */
.section-label{position:relative;padding-left:14px}
.section-label::before{content:'';position:absolute;left:0;top:50%;transform:translateY(-50%);width:4px;height:4px;border-radius:50%;background:var(--red)}
 
/* divider line animate */
.divider-line{width:0;transition:width .8s .3s cubic-bezier(.22,.61,.36,1)}
.reveal.visible ~ .divider-line,.divider-line-anim{width:48px}
 
/* ── RESPONSIVE ── */
@media(max-width:1024px){
  .section{padding:80px 40px}
  .hero{padding:120px 40px 60px}
  .services-intro{grid-template-columns:1fr;gap:40px}
  .services-grid{grid-template-columns:1fr 1fr}
  .plans-grid{grid-template-columns:1fr}
  .audit-grid{grid-template-columns:1fr;gap:28px}
  .brand-grid{grid-template-columns:1fr}
  .brand-cta-box{position:static}
  .design-grid{grid-template-columns:1fr 1fr}
  .process-grid{grid-template-columns:repeat(3,1fr);gap:24px}
  .process-grid::before{display:none}
  nav{padding:0 24px}
  .nav-links,.nav-cta{display:none}
  .nav-mobile-btn{display:block}
  footer{flex-direction:column;gap:20px;text-align:center;padding:32px 24px}
  .footer-links{flex-wrap:wrap;justify-content:center;gap:16px}
}
@media(max-width:640px){
  .section{padding:60px 22px}
  .hero{padding:100px 22px 52px}
  .hero-h{font-size:40px}
  .services-grid{grid-template-columns:1fr}
    .videos-grid{grid-template-columns:repeat(2,1fr)}
  .design-grid{grid-template-columns:1fr}
  .process-grid{grid-template-columns:repeat(2,1fr)}
  .cta-section{padding:80px 22px}
    .hero-scroll{display:none}
}
</style>
</head>
<body>
 
<!-- ── NAV ── -->
<nav id="main-nav">
  <a href="#inicio" class="nav-logo">AO</a>
  <ul class="nav-links">
    <li><a href="#servicios">Servicios</a></li>
    <li><a href="#planes">Planes</a></li>
    <li><a href="#marca">Estrategia</a></li>
    <li><a href="#auditoria">Auditorías</a></li>
  </ul>
  <a href="#contacto" class="nav-cta">Cotizar</a>
  <button class="nav-mobile-btn" id="mob-btn" aria-label="Menú">
    <span class="ham"></span><span class="ham"></span><span class="ham"></span>
  </button>
</nav>
<div class="mobile-menu" id="mob-menu">
  <a href="#servicios" class="mob-link">Servicios</a>
  <a href="#planes" class="mob-link">Planes</a>
<a href="#marca" class="mob-link">Estrategia de Marca</a>
  <a href="#auditoria" class="mob-link">Auditorías</a>
  <a href="#contacto" class="mob-link" style="color:var(--lblue)">Contactar</a>
</div>
 
<!-- ── HERO ── -->
<section class="hero" id="inicio">
  <div class="hero-circles">
    <div class="hero-circle" style="width:600px;height:600px;right:-150px;top:-100px"></div>
    <div class="hero-circle" style="width:380px;height:380px;right:-40px;top:-20px;border-color:rgba(32,119,194,.06)"></div>
    <div class="hero-circle" style="width:200px;height:200px;right:90px;top:120px;border-color:rgba(240,34,64,.05)"></div>
  </div>
  <div class="stripe" style="position:absolute;top:0;left:0;right:0;height:4px"><span class="s1"></span><span class="s2"></span><span class="s3"></span><span class="s4"></span><span class="s5"></span></div>
  <div class="hero-eyebrow">Social Media Management & Estrategia Digital</div>
  <h1 class="hero-h">Tu marca merece<br>crecer con <em>estrategia.</em></h1>
  <p class="hero-sub">Gestión de redes, campañas publicitarias, construcción de marca y auditorías digitales — todo con un especialista que conoce tu negocio.</p>
  <div class="hero-actions">
    <a href="#contacto" class="btn-primary">Pide tu cotización</a>
    <a href="#servicios" class="btn-outline">Ver servicios</a>
  </div>
  <div class="hero-scroll">
    <span>Scroll</span>
    <div class="scroll-line"></div>
  </div>
</section>
 
<!-- ── SERVICIOS OVERVIEW ── -->
<section class="section gray-bg" id="servicios">
  <div class="reveal">
    <div class="section-label reveal-left">Lo que hago</div>
    <h2 class="section-title">Servicios que <em style="font-style:italic;font-family:'Playfair Display',serif">impulsan</em> tu marca</h2>
    <div class="divider-line"></div>
  </div>
  <div class="services-intro reveal">
    <div class="svc-intro-text">
      <p style="font-size:16px;color:var(--text2);line-height:1.8;font-weight:300;margin-bottom:20px">No soy una agencia masiva. Soy un especialista de alto enfoque que trabaja directamente contigo para construir y escalar tu presencia digital con estrategia real, ejecución profesional y resultados medibles.</p>
      <p style="font-size:16px;color:var(--text2);line-height:1.8;font-weight:300">Combino visión estratégica, creatividad y análisis de datos en un solo lugar — sin intermediarios, sin demoras y con comunicación directa.</p>
    </div>
    <div class="svc-intro-stats reveal-right">
      <div class="stat-card"><div class="stat-num" style="color:var(--lblue)">1:1</div><div class="stat-lbl">Atención directa sin agencias</div></div>
      <div class="stat-card"><div class="stat-num" style="color:var(--blue)">360°</div><div class="stat-lbl">Visión integral de tu marca digital</div></div>
      <div class="stat-card"><div class="stat-num" style="color:var(--red)">Data</div><div class="stat-lbl">Decisiones basadas en métricas</div></div>
      <div class="stat-card"><div class="stat-num" style="color:var(--lblue)">ROI</div><div class="stat-lbl">Enfoque en retorno de inversión</div></div>
    </div>
  </div>
  <div class="services-grid reveal">
    <div class="svc-tile">
      <span class="svc-tile-num">01</span>
      <div class="svc-tile-icon" style="background:var(--lblue)"></div>
      <div class="svc-tile-t">Gestión de Redes Sociales</div>
      <div class="svc-tile-d">Manejo completo de Instagram, Facebook y TikTok: parrilla, contenido, publicación y comunidad activa.</div>
      <div class="svc-tile-tags"><span class="tag" style="background:#e8f3f9;color:#0a4a6e">Instagram</span><span class="tag" style="background:#e8f3f9;color:#0a4a6e">Facebook</span><span class="tag" style="background:#e8f3f9;color:#0a4a6e">TikTok</span></div>
    </div>
    <div class="svc-tile">
      <span class="svc-tile-num">02</span>
      <div class="svc-tile-icon" style="background:var(--blue)"></div>
      <div class="svc-tile-t">Publicidad Digital & Ads</div>
      <div class="svc-tile-d">Diseño, configuración y optimización diaria de campañas en Meta Ads y Google Ads orientadas a resultados reales.</div>
      <div class="svc-tile-tags"><span class="tag" style="background:#e6f1fb;color:#0c447c">Meta Ads</span><span class="tag" style="background:#e6f1fb;color:#0c447c">Google Ads</span><span class="tag" style="background:#e6f1fb;color:#0c447c">Full Funnel</span></div>
    </div>
    <div class="svc-tile">
      <span class="svc-tile-num">03</span>
      <div class="svc-tile-icon" style="background:var(--dblue)"></div>
      <div class="svc-tile-t">Estrategia de Marca</div>
      <div class="svc-tile-d">Construcción de identidad desde cero: naming, manual de marca, personificación y posicionamiento.</div>
      <div class="svc-tile-tags"><span class="tag" style="background:#e8f1f8;color:#0a3d5e">Naming</span><span class="tag" style="background:#e8f1f8;color:#0a3d5e">Identidad</span><span class="tag" style="background:#e8f1f8;color:#0a3d5e">Branding</span></div>
    </div>
    <div class="svc-tile">
      <span class="svc-tile-num">04</span>
      <div class="svc-tile-icon" style="background:var(--red)"></div>
      <div class="svc-tile-t">Auditorías Digitales</div>
      <div class="svc-tile-d">Diagnóstico a profundidad de tus cuentas de Meta y campañas activas, con dashboards, informe y sesión de consultoría.</div>
      <div class="svc-tile-tags"><span class="tag" style="background:#fdecea;color:#791f1f">Meta Ads</span><span class="tag" style="background:#fdecea;color:#791f1f">Diagnóstico</span></div>
    </div>
    <div class="svc-tile">
      <span class="svc-tile-num">05</span>
      <div class="svc-tile-icon" style="background:var(--dark)"></div>
      <div class="svc-tile-t">Diseño & Creativos</div>
      <div class="svc-tile-d">Identidad visual, logo, brand book, posts, reels y piezas publicitarias que comunican el mensaje correcto.</div>
      <div class="svc-tile-tags"><span class="tag" style="background:#f1efe8;color:#2c2c2a">Logo</span><span class="tag" style="background:#f1efe8;color:#2c2c2a">Brand Book</span><span class="tag" style="background:#f1efe8;color:#2c2c2a">Contenido</span></div>
    </div>
    <div class="svc-tile">
      <span class="svc-tile-num">06</span>
      <div class="svc-tile-icon" style="background:var(--lblue)"></div>
      <div class="svc-tile-t">Consultoría Digital</div>
      <div class="svc-tile-d">Sesiones estratégicas para orientarte en decisiones digitales: presencia, pauta, contenido y posicionamiento.</div>
      <div class="svc-tile-tags"><span class="tag" style="background:#e8f3f9;color:#0a4a6e">Estrategia</span><span class="tag" style="background:#e8f3f9;color:#0a4a6e">Asesoría</span></div>
    </div>
  </div>
</section>
 
<!-- ── PLANES ── -->
<section class="section" id="planes">
  <div class="reveal">
    <div class="section-label reveal-left">Gestión mensual de redes</div>
    <h2 class="section-title">Planes para cada<br>etapa de tu marca</h2>
    <div class="divider-line"></div>
    <p class="section-sub">Elige el nivel que mejor se adapta a tus objetivos. Todos los planes incluyen parrilla de contenido, diseño de posts y gestión de comunidad.</p>
  </div>
  <div class="plans-grid reveal">
    <div class="plan-card">
      <div class="plan-head"><div class="plan-badge" style="color:var(--lblue)">Básico</div><div class="plan-name">Presencia</div><div class="plan-focus">Mantenimiento de marca</div></div>
      <div class="plan-price-row"><div class="plan-cur">$</div><div class="plan-price">8,500</div><div class="plan-per">MXN / mes</div></div>
      <div class="plan-feats">
        <div class="plan-feat"><div class="pf-dot" style="background:var(--lblue)"></div><div><span class="pf-lbl">8 posts estáticos </span><span class="pf-val">(diseño incluido)</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--lblue)"></div><div><span class="pf-lbl">2 reels / mes</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--lblue)"></div><div><span class="pf-lbl">Comunidad </span><span class="pf-val">Lunes a Viernes</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--lblue)"></div><div><span class="pf-lbl">Parrilla mensual</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--mgray)"></div><div><span class="pf-lbl" style="color:#bbb">Ads </span><span class="pf-val" style="color:#ccc">No incluye</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--lblue)"></div><div><span class="pf-lbl">Reporte PDF </span><span class="pf-val">+ reunión mensual 30min</span></div></div>
      </div>
    </div>
    <div class="plan-card" style="box-shadow:0 0 0 2px var(--blue)">
      <div class="plan-head" style="position:relative"><div style="position:absolute;top:12px;right:14px;background:var(--blue);color:#fff;font-size:8px;letter-spacing:2px;text-transform:uppercase;padding:3px 9px;border-radius:20px;font-weight:500">Más popular</div><div class="plan-badge" style="color:var(--blue)">Intermedio</div><div class="plan-name">Crecimiento</div><div class="plan-focus">Captación y alcance</div></div>
      <div class="plan-price-row"><div class="plan-cur">$</div><div class="plan-price">11,500</div><div class="plan-per">MXN / mes</div></div>
      <div class="plan-feats">
        <div class="plan-feat"><div class="pf-dot" style="background:var(--blue)"></div><div><span class="pf-lbl">10 posts estáticos </span><span class="pf-val">(diseño incluido)</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--blue)"></div><div><span class="pf-lbl">4 reels </span><span class="pf-val">(1 por semana)</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--blue)"></div><div><span class="pf-lbl">Comunidad </span><span class="pf-val">Lun – Sábado</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--blue)"></div><div><span class="pf-lbl">Parrilla mensual</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:#1a7a40"></div><div><span class="pf-lbl" style="color:#1a7a40">Ads incluidos </span><span class="pf-val">1 campaña básica</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--blue)"></div><div><span class="pf-lbl">Reporte PDF </span><span class="pf-val">+ reunión quincenal 20min</span></div></div>
      </div>
    </div>
    <div class="plan-card">
      <div class="plan-head"><div class="plan-badge" style="color:var(--red)">Premium</div><div class="plan-name">Dominio</div><div class="plan-focus">Posicionamiento agresivo</div></div>
      <div class="plan-price-row"><div class="plan-cur">$</div><div class="plan-price">17,000</div><div class="plan-per">MXN / mes</div></div>
      <div class="plan-feats">
        <div class="plan-feat"><div class="pf-dot" style="background:var(--red)"></div><div><span class="pf-lbl">12 posts estáticos </span><span class="pf-val">(diseño incluido)</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--red)"></div><div><span class="pf-lbl">8 reels </span><span class="pf-val">(2 por semana)</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--red)"></div><div><span class="pf-lbl">Comunidad </span><span class="pf-val">Lunes a Domingo</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--red)"></div><div><span class="pf-lbl">Parrilla quincenal </span><span class="pf-val">(mayor agilidad)</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:#1a7a40"></div><div><span class="pf-lbl" style="color:#1a7a40">Funnel completo </span><span class="pf-val">Tráfico + remarketing</span></div></div>
        <div class="plan-feat"><div class="pf-dot" style="background:var(--red)"></div><div><span class="pf-lbl">Dashboard </span><span class="pf-val">+ seguimiento semanal 30min</span></div></div>
      </div>
    </div>
  </div>
  <div style="background:var(--gray);border-radius:8px;padding:16px 22px;margin-top:16px;font-size:13px;color:var(--text2);font-weight:300" class="reveal">
    * El presupuesto de anuncios se paga directamente a la plataforma (Meta/Google) y corre por cuenta del cliente. Precios no incluyen IVA.
  </div>
</section>
<!-- ── AUDITORÍA ── -->
<section class="section dark-bg" id="auditoria">
  <div class="reveal">
    <div class="section-label reveal-left" style="color:var(--lblue)">Diagnóstico digital</div>
    <h2 class="section-title light">Auditoría Estratégica<br>de Meta Ads</h2>
    <div class="divider-line"></div>
    <p class="section-sub light">¿Inviertes en publicidad pero no ves resultados claros? Te entrego el diagnóstico completo de tus cuentas con datos reales y recomendaciones accionables.</p>
  </div>
  <div class="audit-grid reveal">
    <div class="audit-deliverables">
      <div class="audit-item"><div class="audit-num" style="color:var(--lblue)">01</div><div><div class="audit-t">Análisis a profundidad</div><div class="audit-d">Revisión exhaustiva de hasta 2 cuentas de Meta: estructura, segmentación, creativos, Pixel y rendimiento histórico.</div></div></div>
      <div class="audit-item dblue"><div class="audit-num" style="color:var(--dblue)">02</div><div><div class="audit-t">4 Dashboards interactivos</div><div class="audit-d">Tableros de visualización con KPIs, tendencias y desglose por campaña, conjunto de anuncios y creativos.</div></div></div>
      <div class="audit-item lblue"><div class="audit-num" style="color:var(--lblue)">03</div><div><div class="audit-t">Documento de diagnóstico</div><div class="audit-d">Informe detallado con hallazgos, estatus de campañas y recomendaciones específicas y generales para optimizar.</div></div></div>
      <div class="audit-item red"><div class="audit-num" style="color:var(--red)">04</div><div><div class="audit-t">Sesión de consultoría 1–2h</div><div class="audit-d">Reunión virtual o presencial para presentar los hallazgos y asesorarte en qué cambios implementar y cómo priorizarlos.</div></div></div>
    </div>
    <div class="audit-price-block reveal-scale">
      <div class="audit-price-label">Inversión total</div>
      <div class="audit-big-price">$5,000</div>
      <div class="audit-price-note">MXN + IVA</div>
      <div class="audit-meta">
        <div class="audit-meta-row"><div class="audit-meta-dot" style="background:var(--blue)"></div>6 días hábiles de entrega</div>
        <div class="audit-meta-row"><div class="audit-meta-dot" style="background:var(--lblue)"></div>50% anticipo · 50% contra entrega</div>
        <div class="audit-meta-row"><div class="audit-meta-dot" style="background:var(--red)"></div>Solo de evaluación — no incluye implementación</div>
        <div class="audit-meta-row"><div class="audit-meta-dot" style="background:var(--mgray)"></div>Toda la información se trata con estricta confidencialidad</div>
      </div>
      <div style="margin-top:24px"><a href="#contacto" class="btn-primary" style="display:inline-block">Solicitar auditoría</a></div>
    </div>
  </div>
</section>
 
<!-- ── ESTRATEGIA MARCA ── -->
<section class="section" id="marca">
  <div class="reveal">
    <div class="section-label reveal-left">Construcción de marca</div>
    <h2 class="section-title">Tu marca, construida<br>desde la estrategia</h2>
    <div class="divider-line"></div>
  </div>
  <div class="brand-grid reveal">
    <div class="brand-list">
      <div class="brand-item"><div class="bi-num">01</div><div><div class="bi-t">Investigación de mercado</div><div class="bi-d">Análisis del sector, oportunidades clave y definición del público objetivo para tu marca o app.</div></div></div>
      <div class="brand-item"><div class="bi-num">02</div><div><div class="bi-t">Benchmarking competitivo</div><div class="bi-d">Análisis de la competencia directa: presencia digital, propuesta de valor, puntos débiles y áreas de oportunidad.</div></div></div>
      <div class="brand-item"><div class="bi-num">03</div><div><div class="bi-t">Naming</div><div class="bi-d">Desarrollo del nombre de tu marca o app: conceptualización, validación de disponibilidad y recomendación estratégica.</div></div></div>
      <div class="brand-item"><div class="bi-num">04</div><div><div class="bi-t">Manual de marca</div><div class="bi-d">Documento maestro de identidad: logotipo, paleta, tipografías, tono de comunicación y normas de uso.</div></div></div>
      <div class="brand-item"><div class="bi-num">05</div><div><div class="bi-t">Personificación de marca</div><div class="bi-d">Arquetipo, personalidad, voz y carácter: cómo habla, cómo se comporta y cómo se relaciona con su audiencia.</div></div></div>
      <div class="brand-item"><div class="bi-num">06</div><div><div class="bi-t">Plan de contenidos</div><div class="bi-d">Estrategia editorial y lineamientos creativos para publicidad. No incluye producción de creativos.</div></div></div>
      <div class="brand-item"><div class="bi-num">07</div><div><div class="bi-t">Creación de redes sociales</div><div class="bi-d">Alta y configuración profesional de perfiles: bios, nomenclatura, foto de perfil y portadas.</div></div></div>
    </div>
    <div class="brand-cta-box reveal-scale">
      <div class="bcb-label">Paquete integral</div>
      <div class="bcb-title">Estrategia de Marca & Lanzamiento Digital</div>
      <div class="bcb-price">$10,000</div>
      <div class="bcb-note" style="color:rgba(255,255,255,.35)">MXN · pago único</div>
      <div class="bcb-items">
        <div class="bcb-item"><div class="bcb-dot" style="background:var(--lblue)"></div>7 entregables estratégicos</div>
        <div class="bcb-item"><div class="bcb-dot" style="background:var(--blue)"></div>Ideal para nuevas marcas, rebrands y apps</div>
        <div class="bcb-item"><div class="bcb-dot" style="background:var(--red)"></div>Pago único al inicio del proyecto</div>
        <div class="bcb-item"><div class="bcb-dot" style="background:var(--mgray)"></div>Tiempos a convenir al inicio</div>
      </div>
      <a href="#contacto" class="btn-primary" style="display:block;text-align:center">Solicitar información</a>
    </div>
  </div>
</section>
 
<!-- ── DISEÑO ── -->
<section class="section gray-bg">
  <div class="reveal">
    <div class="section-label reveal-left">Visual & Creativos</div>
    <h2 class="section-title">Diseño que comunica<br>y convierte</h2>
    <div class="divider-line"></div>
  </div>
  <div class="design-grid reveal">
    <div class="design-card">
      <div class="dc-head"><div class="dc-accent" style="background:var(--dblue)"></div><div class="dc-t">Identidad Visual</div><div class="dc-price">$5,000 <span style="font-size:14px;font-weight:300;color:var(--dg)">MXN</span></div></div>
      <div class="dc-body"><ul class="dc-items"><li>Diseño de logo principal + secundario</li><li>Versiones blanco y negro</li><li>Paleta de colores (HEX y RGB)</li><li>Tipografías primaria y secundaria</li><li>Concepto creativo</li></ul></div>
    </div>
    <div class="design-card">
      <div class="dc-head"><div class="dc-accent" style="background:var(--blue)"></div><div class="dc-t">Brand Book Completo</div><div class="dc-price">$3,500 <span style="font-size:14px;font-weight:300;color:var(--dg)">MXN</span></div></div>
      <div class="dc-body"><ul class="dc-items"><li>Uso correcto del logo</li><li>Área de seguridad y tamaños mínimos</li><li>Usos incorrectos (ejemplos visuales)</li><li>Aplicación de colores y tipografías</li><li>Mockups básicos de aplicación</li></ul></div>
    </div>
    <div class="design-card">
      <div class="dc-head"><div class="dc-accent" style="background:var(--red)"></div><div class="dc-t">Contenido & Piezas</div><div class="dc-price" style="font-size:18px;font-weight:300">Incluido en planes</div></div>
      <div class="dc-body"><ul class="dc-items"><li>Posts estáticos y carruseles</li><li>Reels y videos cortos</li><li>Stories y banners de perfil</li><li>Creativos para Meta Ads y TikTok Ads</li><li>Piezas para Google Display</li></ul></div>
    </div>
  </div>
</section>
 
<!-- ── PROCESO ── -->
<section class="section">
  <div class="reveal">
    <div class="section-label reveal-left">Metodología</div>
    <h2 class="section-title">Cómo trabajamos juntos</h2>
    <div class="divider-line"></div>
    <p class="section-sub">Un proceso claro y sin sorpresas, de principio a fin.</p>
  </div>
  <div class="process-grid reveal">
    <div class="process-step"><div class="ps-num" style="background:var(--lblue)">1</div><div class="ps-t">Briefing</div><div class="ps-d">Conocemos tu marca, objetivos y situación actual.</div></div>
    <div class="process-step"><div class="ps-num" style="background:var(--blue)">2</div><div class="ps-t">Diagnóstico</div><div class="ps-d">Auditamos lo que tienes e identificamos oportunidades.</div></div>
    <div class="process-step"><div class="ps-num" style="background:var(--dblue)">3</div><div class="ps-t">Estrategia</div><div class="ps-d">Diseñamos el plan: qué, cómo y cuándo.</div></div>
    <div class="process-step"><div class="ps-num" style="background:var(--dark)">4</div><div class="ps-t">Producción</div><div class="ps-d">Creamos contenido y estructura de campañas.</div></div>
    <div class="process-step"><div class="ps-num" style="background:var(--red)">5</div><div class="ps-t">Lanzamiento</div><div class="ps-d">Publicamos, activamos y gestionamos la comunidad.</div></div>
    <div class="process-step"><div class="ps-num" style="background:var(--blue)">6</div><div class="ps-t">Optimización</div><div class="ps-d">Medimos, ajustamos y mejoramos constantemente.</div></div>
  </div>
</section>
 
<!-- ── CTA ── -->
<section class="cta-section" id="contacto">
  <div class="cta-circles">
    <div class="cta-circle" style="width:600px;height:600px;left:50%;transform:translateX(-50%);top:-160px"></div>
    <div class="cta-circle" style="width:360px;height:360px;left:50%;transform:translateX(-50%);top:-60px;border-color:rgba(32,119,194,.07)"></div>
  </div>
  <div class="stripe" style="position:absolute;top:0;left:0;right:0;height:4px"><span class="s1"></span><span class="s2"></span><span class="s3"></span><span class="s4"></span><span class="s5"></span></div>
  <div style="position:relative;z-index:1">
    <div style="font-size:9px;letter-spacing:5px;color:var(--red);text-transform:uppercase;font-weight:500;margin-bottom:16px;animation:fadeup .8s both">¿Listo para crecer?</div>
    <div class="cta-tagline">"Tu marca, con<br><em>estrategia.</em>"</div>
    <p class="cta-sub">Da el primer paso hoy. Cuéntame dónde está tu marca y te doy una recomendación honesta sin costo y sin compromiso.</p>
    <div class="cta-contacts">
      <div class="cta-contact"><div class="cc-dot" style="background:var(--blue)"></div><strong>hector_ort_m@outlook.com</strong></div>
      <div class="cta-contact"><div class="cc-dot" style="background:var(--lblue)"></div><strong>993 431 3735</strong></div>
    </div>
    <div style="display:flex;gap:14px;justify-content:center;flex-wrap:wrap">
      <a href="mailto:hector_ort_m@outlook.com" class="btn-primary" style="font-size:13px">Escribir correo</a>
      <a href="https://wa.me/529934313735" class="btn-outline" style="font-size:13px">WhatsApp</a>
    </div>
    <div class="cta-tags" style="margin-top:36px">
      <span class="cta-tag" style="font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:4px 10px;border:1px solid rgba(255,255,255,.1);border-radius:20px;color:rgba(255,255,255,.25)">Redes Sociales</span>
      <span class="cta-tag" style="font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:4px 10px;border:1px solid rgba(255,255,255,.1);border-radius:20px;color:rgba(255,255,255,.25)">Meta Ads</span>
      <span class="cta-tag" style="font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:4px 10px;border:1px solid rgba(255,255,255,.1);border-radius:20px;color:rgba(255,255,255,.25)">Estrategia de Marca</span>
      <span class="cta-tag" style="font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:4px 10px;border:1px solid rgba(255,255,255,.1);border-radius:20px;color:rgba(255,255,255,.25)">Auditorías</span>
      <span class="cta-tag" style="font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:4px 10px;border:1px solid rgba(255,255,255,.1);border-radius:20px;color:rgba(255,255,255,.25)">Diseño</span>
    </div>
  </div>
</section>
 
<!-- ── FOOTER ── -->
<footer>
  <div><div class="footer-logo">AO</div><div class="footer-tagline">Alfonso Ortiz · Social Media Management</div></div>
  <ul class="footer-links">
    <li><a href="#servicios">Servicios</a></li>
    <li><a href="#planes">Planes</a></li>
    <li><a href="#contacto">Contacto</a></li>
  </ul>
  <div class="footer-legal">© 2026 Alfonso Ortiz. Todos los derechos reservados.</div>
</footer>
 
<script>
/* ── NAV scroll effect ── */
const mainNav=document.getElementById('main-nav');
window.addEventListener('scroll',()=>{
  const y=window.scrollY;
  mainNav.style.background=y>60?'rgba(8,13,15,.99)':'rgba(8,13,15,.96)';
  mainNav.style.boxShadow=y>60?'0 2px 24px rgba(0,0,0,.4)':'none';
  /* parallax hero circles */
  document.querySelectorAll('.hero-circle').forEach((c,i)=>{
    c.style.transform=`translateY(${y*(.08+i*.04)}px)`;
  });
});
 
/* ── Mobile menu ── */
const mobBtn=document.getElementById('mob-btn');
const mobMenu=document.getElementById('mob-menu');
mobBtn.addEventListener('click',()=>{
  mobMenu.classList.toggle('open');
  const hams=mobBtn.querySelectorAll('.ham');
  if(mobMenu.classList.contains('open')){
    hams[0].style.transform='rotate(45deg) translate(5px,5px)';
    hams[1].style.opacity='0';
    hams[2].style.transform='rotate(-45deg) translate(5px,-5px)';
  } else {
    hams.forEach(h=>{h.style.transform='';h.style.opacity='';});
  }
});
document.querySelectorAll('.mob-link').forEach(l=>l.addEventListener('click',()=>{
  mobMenu.classList.remove('open');
  mobBtn.querySelectorAll('.ham').forEach(h=>{h.style.transform='';h.style.opacity='';});
}));
 
/* ── Intersection Observer — reveal classes ── */
const revealObs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.classList.add('visible');
      /* animate divider lines inside this block */
      e.target.querySelectorAll('.divider-line').forEach(d=>d.classList.add('divider-line-anim'));
    }
  });
},{threshold:0.12,rootMargin:'0px 0px -40px 0px'});
 
document.querySelectorAll('.reveal,.reveal-left,.reveal-right,.reveal-scale,.stagger').forEach(el=>revealObs.observe(el));
 
/* ── Animated counters on stat cards ── */
const counterObs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(!e.isIntersecting||e.target.dataset.counted) return;
    e.target.dataset.counted='1';
    const el=e.target.querySelector('.stat-num');
    if(!el)return;
    const txt=el.textContent.trim();
    /* only animate pure numbers */
    const num=parseInt(txt.replace(/[^0-9]/g,''));
    if(isNaN(num)||txt.length>4)return;
    let start=0;
    const dur=1400;
    const step=timestamp=>{
      if(!start)start=timestamp;
      const prog=Math.min((timestamp-start)/dur,1);
      const ease=1-Math.pow(1-prog,4);
      el.textContent=Math.round(ease*num).toLocaleString()+(txt.replace(/[0-9]/g,''));
      if(prog<1)requestAnimationFrame(step);
    };
    requestAnimationFrame(step);
  });
},{threshold:0.5});
document.querySelectorAll('.stat-card').forEach(c=>counterObs.observe(c));
 
/* ── Add stagger class to grids ── */
document.querySelectorAll('.services-grid,.plans-grid,.design-grid,.svc-intro-stats,.process-grid').forEach(g=>{
  g.classList.add('stagger');
  revealObs.observe(g);
});
 
/* ── Smooth active nav link highlight ── */
const sections=document.querySelectorAll('section[id]');
const navLinks=document.querySelectorAll('.nav-links a');
const sectionObs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      navLinks.forEach(l=>{
        l.style.color=l.getAttribute('href')==='#'+e.target.id?'#fff':'';
      });
    }
  });
},{threshold:0.4});
sections.forEach(s=>sectionObs.observe(s));
 
/* ── Scroll-triggered stripe shimmer on first load ── */
document.querySelectorAll('.stripe').forEach(s=>s.classList.add('stripe-shimmer'));
 
/* ── Add scroll-dot to hero scroll indicator ── */
const scrollLine=document.querySelector('.scroll-line');
if(scrollLine){
  const dot=document.createElement('div');
  dot.className='scroll-dot';
  scrollLine.parentNode.insertBefore(dot,scrollLine);
}
 
/* ── Plan card tilt on mousemove ── */
document.querySelectorAll('.plan-card').forEach(card=>{
  card.addEventListener('mousemove',e=>{
    const r=card.getBoundingClientRect();
    const x=e.clientX-r.left-r.width/2;
    const y=e.clientY-r.top-r.height/2;
    card.style.transform=`translateY(-6px) rotateX(${(-y/r.height*4).toFixed(1)}deg) rotateY(${(x/r.width*4).toFixed(1)}deg)`;
  });
  card.addEventListener('mouseleave',()=>{
    card.style.transform='';
    card.style.transition='transform .4s ease';
    setTimeout(()=>card.style.transition='',400);
  });
});
 
/* ── Audit item sequential reveal ── */
const auditItems=document.querySelectorAll('.audit-item');
const auditObs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(!e.isIntersecting)return;
    auditItems.forEach((item,i)=>{
      setTimeout(()=>{
        item.style.opacity='1';
        item.style.transform='none';
      },i*120);
    });
    auditObs.disconnect();
  });
},{threshold:0.2});
auditItems.forEach(item=>{
  item.style.opacity='0';
  item.style.transform='translateX(-20px)';
  item.style.transition='opacity .5s ease, transform .5s ease';
});
if(auditItems.length)auditObs.observe(auditItems[0]);
 
/* ── Brand item sequential reveal ── */
const brandItems=document.querySelectorAll('.brand-item');
const brandObs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(!e.isIntersecting)return;
    brandItems.forEach((item,i)=>{
      setTimeout(()=>{
        item.style.opacity='1';
        item.style.transform='none';
      },i*80);
    });
    brandObs.disconnect();
  });
},{threshold:0.1});
brandItems.forEach(item=>{
  item.style.opacity='0';
  item.style.transform='translateY(14px)';
  item.style.transition='opacity .45s ease, transform .45s ease';
});
if(brandItems.length)brandObs.observe(brandItems[0].closest('section'));
</script>
</body>
</html>

<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>Alfonso Ortiz — Social Media Management</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400;1,700&family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js"></script>
<style>
:root{
  --dark:#080d0f;--lblue:#5b9cc4;--blue:#2077c2;--dblue:#0f5f8a;--red:#f02240;
  --white:#fff;--offwhite:#f7f9fb;--gray:#f2f5f8;--mgray:#d6dde5;--dg:#888;
  --text:#0d1117;--text2:#4a5568;
  --nav-h:66px;
}
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
html,body{width:100%;min-width:320px;max-width:100%!important}
#app,main,.page,.book{width:100%!important;max-width:100%!important}
html{scroll-behavior:smooth;font-size:16px}
body{background:var(--white);font-family:'DM Sans',sans-serif;color:var(--text);overflow-x:hidden}


/* ══ STRIPE ══ */
.stripe{display:flex;height:4px}
.stripe span{flex:1}
.s1{background:var(--dark);flex:3!important}.s2{background:var(--lblue)}.s3{background:var(--blue)}.s4{background:var(--dblue)}.s5{background:var(--red)}

/* ══ NAV ══ */
nav{position:fixed;top:0;left:0;right:0;z-index:1000;height:var(--nav-h);background:rgba(8,13,15,.97);backdrop-filter:blur(18px);border-bottom:1px solid rgba(255,255,255,.06);display:flex;align-items:center;padding:0 52px;gap:32px;transition:box-shadow .3s}
nav.scrolled{box-shadow:0 4px 32px rgba(0,0,0,.4)}
.nav-logo{font-family:'Playfair Display',serif;font-size:26px;font-weight:700;color:var(--white);text-decoration:none;letter-spacing:-1px;flex-shrink:0}
.nav-tabs{display:flex;gap:4px;flex:1;justify-content:center}
.nav-tab{background:none;border:none;font-family:'Syne',sans-serif;font-size:11px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:rgba(255,255,255,.4);padding:8px 16px;border-radius:4px;cursor:pointer;transition:all .22s;position:relative}
.nav-tab::after{content:'';position:absolute;bottom:0;left:16px;right:16px;height:2px;background:var(--blue);border-radius:2px;transform:scaleX(0);transition:transform .22s}
.nav-tab:hover{color:rgba(255,255,255,.8)}
.nav-tab.active{color:var(--white)}
.nav-tab.active::after{transform:scaleX(1)}
.nav-right{display:flex;gap:10px;align-items:center;flex-shrink:0}
.lang-toggle{display:flex;background:rgba(255,255,255,.07);border-radius:6px;overflow:hidden;border:1px solid rgba(255,255,255,.1)}
.lang-btn{background:none;border:none;font-family:'Syne',sans-serif;font-size:10px;font-weight:700;letter-spacing:1.5px;color:rgba(255,255,255,.4);padding:6px 12px;cursor:pointer;transition:all .18s;text-transform:uppercase}
.lang-btn.active{background:var(--blue);color:#fff}
.nav-cta{font-family:'Syne',sans-serif;font-size:10px;font-weight:700;letter-spacing:2px;text-transform:uppercase;background:var(--red);color:var(--white);padding:8px 18px;border-radius:4px;text-decoration:none;transition:all .2s}
.nav-cta:hover{background:#c91535;transform:translateY(-1px)}
.mob-btn{display:none;background:none;border:none;cursor:pointer;padding:4px;flex-direction:column;gap:5px}
.ham{display:block;width:22px;height:2px;background:var(--white);transition:all .25s;border-radius:2px}
.mob-menu{display:none;position:fixed;inset:var(--nav-h) 0 0;background:rgba(8,13,15,.99);z-index:999;flex-direction:column;align-items:center;justify-content:center;gap:22px}
.mob-menu.open{display:flex}
.mob-menu button{background:none;border:none;font-family:'Syne',sans-serif;font-size:22px;font-weight:600;color:rgba(255,255,255,.7);cursor:pointer;letter-spacing:2px}

/* ══ PAGES ══ */
.page{display:none;min-height:100vh;padding-top:var(--nav-h)}
.page.active{display:block}

/* ══ HERO ══ */
.hero{min-height:calc(100vh - var(--nav-h));background:var(--dark);display:grid;grid-template-columns:1fr 1fr;align-items:center;padding:80px 80px 60px;gap:60px;position:relative;overflow:hidden}
.hero-canvas{position:absolute;inset:0;opacity:.35}
.hero-left{position:relative;z-index:2}
.hero-eyebrow{font-family:'Syne',sans-serif;font-size:10px;font-weight:700;letter-spacing:5px;color:var(--red);text-transform:uppercase;margin-bottom:18px;display:flex;align-items:center;gap:10px}
.hero-eyebrow::before{content:'';width:28px;height:2px;background:var(--red);display:inline-block}
.hero-h{font-family:'Playfair Display',serif;font-size:clamp(44px,5.5vw,78px);font-weight:700;color:var(--white);line-height:1.04;margin-bottom:22px}
.hero-h em{font-style:italic;color:var(--lblue);display:block}
.hero-sub{font-size:17px;color:rgba(255,255,255,.45);font-weight:300;line-height:1.75;max-width:480px;margin-bottom:40px}
.hero-btns{display:flex;gap:14px;flex-wrap:wrap}
.btn-pri{font-family:'Syne',sans-serif;font-size:11px;font-weight:700;letter-spacing:2px;text-transform:uppercase;background:var(--blue);color:var(--white);padding:14px 28px;border-radius:4px;text-decoration:none;transition:all .22s;border:none;cursor:pointer}
.btn-pri:hover{background:var(--dblue);transform:translateY(-2px);box-shadow:0 10px 28px rgba(32,119,194,.32)}
.btn-sec{font-family:'Syne',sans-serif;font-size:11px;font-weight:600;letter-spacing:2px;text-transform:uppercase;border:1px solid rgba(255,255,255,.2);color:rgba(255,255,255,.7);padding:14px 28px;border-radius:4px;text-decoration:none;transition:all .22s;background:none;cursor:pointer}
.btn-sec:hover{border-color:var(--white);color:var(--white);transform:translateY(-2px)}
.hero-right{position:relative;z-index:2;display:flex;flex-direction:column;gap:14px}
.hero-card{background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.07);border-radius:10px;padding:20px 22px;backdrop-filter:blur(8px);transition:all .25s}
.hero-card:hover{background:rgba(255,255,255,.08);transform:translateX(-4px)}
.hc-num{font-family:'Playfair Display',serif;font-size:11px;color:var(--lblue);font-weight:700;margin-bottom:6px}
.hc-t{font-family:'Syne',sans-serif;font-size:15px;font-weight:700;color:var(--white);margin-bottom:4px}
.hc-d{font-size:13px;color:rgba(255,255,255,.4);font-weight:300;line-height:1.55}
.hero-scroll-hint{position:absolute;bottom:28px;left:80px;display:flex;align-items:center;gap:10px;z-index:2}
.scroll-line{width:40px;height:1px;background:rgba(255,255,255,.2)}
.scroll-text{font-family:'Syne',sans-serif;font-size:9px;letter-spacing:3px;text-transform:uppercase;color:rgba(255,255,255,.2)}

/* ══ SECTION COMMONS ══ */
.section{padding:100px 80px}
.section.dark{background:var(--dark)}
.section.gray{background:var(--offwhite)}
.sec-label{font-family:'Syne',sans-serif;font-size:9px;font-weight:700;letter-spacing:5px;color:var(--red);text-transform:uppercase;margin-bottom:10px;display:flex;align-items:center;gap:10px}
.sec-label::before{content:'';width:20px;height:2px;background:var(--red)}
.sec-title{font-family:'Playfair Display',serif;font-size:clamp(30px,4vw,50px);font-weight:700;color:var(--text);line-height:1.1;margin-bottom:14px}
.sec-title.light{color:var(--white)}
.sec-sub{font-size:16px;color:var(--text2);font-weight:300;line-height:1.75;max-width:580px;margin-bottom:52px}
.sec-sub.light{color:rgba(255,255,255,.45)}
.bar{width:0;height:2px;background:var(--blue);border-radius:2px;margin-bottom:36px;transition:width 1s .2s}
.bar.go{width:48px}

/* ══ SERVICIOS ══ */
.svc-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:2px;background:var(--mgray);border-radius:12px;overflow:hidden}
.svc-tile{background:var(--white);padding:36px 30px;position:relative;overflow:hidden;cursor:default}
.svc-tile::before{content:'';position:absolute;inset:0;background:var(--blue);transform:scaleY(0);transform-origin:bottom;transition:transform .4s cubic-bezier(.22,.61,.36,1);z-index:0}
.svc-tile:hover::before{transform:scaleY(1)}
.svc-tile>*{position:relative;z-index:1;transition:color .3s}
.svc-tile:hover .svc-num,.svc-tile:hover .svc-t,.svc-tile:hover .svc-d{color:rgba(255,255,255,.9)}
.svc-num{font-family:'Playfair Display',serif;font-size:11px;color:var(--blue);font-weight:700;margin-bottom:16px;display:block;transition:color .3s}
.svc-bar{width:32px;height:3px;border-radius:2px;margin-bottom:18px;transition:background .3s}
.svc-tile:hover .svc-bar{background:rgba(255,255,255,.4)!important}
.svc-t{font-family:'Syne',sans-serif;font-size:17px;font-weight:700;color:var(--text);margin-bottom:10px;transition:color .3s}
.svc-d{font-size:13px;color:var(--text2);line-height:1.7;font-weight:300;transition:color .3s}

/* ══ PROCESO ══ */
.process-track{display:grid;grid-template-columns:repeat(6,1fr);position:relative;gap:0}
.process-track::before{content:'';position:absolute;top:22px;left:8%;right:8%;height:1px;background:var(--mgray);z-index:0}
.proc-step{display:flex;flex-direction:column;align-items:center;text-align:center;z-index:1;padding:0 8px}
.proc-n{width:44px;height:44px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-family:'Playfair Display',serif;font-size:15px;font-weight:700;color:var(--white);margin-bottom:14px;transition:transform .25s,box-shadow .25s}
.proc-step:hover .proc-n{transform:scale(1.15);box-shadow:0 8px 22px rgba(0,0,0,.18)}
.proc-t{font-family:'Syne',sans-serif;font-size:12px;font-weight:700;color:var(--text);margin-bottom:4px;letter-spacing:.5px}
.proc-d{font-size:11px;color:var(--text2);font-weight:300;line-height:1.55}

/* ══ TRABAJO / VIDEOS ══ */
.video-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}
.video-card{border-radius:10px;overflow:hidden;position:relative;background:var(--dark);aspect-ratio:9/16;cursor:pointer;min-height:280px}
.video-card:hover img{transform:scale(1.06)}
.video-card video{width:100%;height:100%;object-fit:cover;display:block;transition:transform .5s ease}
.video-card:hover video{transform:scale(1.04)}
.video-overlay{position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.8) 0%,transparent 50%);display:flex;flex-direction:column;justify-content:flex-end;padding:18px 16px;opacity:0;transition:opacity .3s}
.video-card:hover .video-overlay{opacity:1}
.video-play{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:52px;height:52px;border-radius:50%;background:rgba(255,255,255,.15);backdrop-filter:blur(6px);display:flex;align-items:center;justify-content:center;transition:all .25s;border:1px solid rgba(255,255,255,.25)}
.video-card:hover .video-play{background:rgba(32,119,194,.7);border-color:var(--blue);transform:translate(-50%,-50%) scale(1.1)}
.video-play svg{fill:white;width:18px;height:18px;margin-left:2px}
.video-label{font-family:'Syne',sans-serif;font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--lblue)}
.video-type{font-size:12px;color:rgba(255,255,255,.7);font-weight:300;margin-top:3px}
/* video modal */
.modal{position:fixed;inset:0;z-index:2000;background:rgba(0,0,0,.92);display:none;align-items:center;justify-content:center;padding:20px}
.modal.open{display:flex}
.modal-inner{position:relative;width:100%;max-width:460px}
.modal-inner video{width:100%;border-radius:10px;max-height:90vh;object-fit:contain}
.modal-close{position:absolute;top:-40px;right:0;background:none;border:none;color:rgba(255,255,255,.7);font-size:28px;cursor:pointer;line-height:1;transition:color .2s}
.modal-close:hover{color:#fff}

/* ══ MARCA / IDENTIDAD ══ */
.brand-list{display:flex;flex-direction:column}
.brand-item{display:flex;gap:20px;align-items:flex-start;padding:22px 0;border-bottom:1px solid var(--mgray)}
.brand-item:last-child{border-bottom:none}
.bi-n{font-family:'Playfair Display',serif;font-size:13px;font-weight:700;color:var(--blue);flex-shrink:0;min-width:28px;padding-top:2px}
.bi-t{font-family:'Syne',sans-serif;font-size:15px;font-weight:700;color:var(--text);margin-bottom:5px}
.bi-d{font-size:13px;color:var(--text2);line-height:1.65;font-weight:300}

.brand-aside{background:var(--dark);border-radius:12px;padding:36px;position:sticky;top:calc(var(--nav-h) + 20px)}
.ba-label{font-family:'Syne',sans-serif;font-size:9px;letter-spacing:4px;text-transform:uppercase;color:var(--lblue);margin-bottom:12px}
.ba-t{font-family:'Playfair Display',serif;font-size:26px;font-weight:700;color:var(--white);line-height:1.2;margin-bottom:18px}
.ba-items{display:flex;flex-direction:column;gap:9px;margin-bottom:26px}
.ba-item{display:flex;gap:10px;align-items:flex-start;font-size:13px;color:rgba(255,255,255,.5);line-height:1.4;font-weight:300}
.ba-dot{width:4px;height:4px;border-radius:50%;flex-shrink:0;margin-top:7px}

/* ══ AUDITORÍA ══ */
.audit-cards{display:grid;grid-template-columns:repeat(2,1fr);gap:14px;margin-bottom:36px}
.audit-card{background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.07);border-radius:10px;padding:24px;display:flex;gap:18px;transition:all .25s}
.audit-card:hover{background:rgba(255,255,255,.08);transform:translateY(-3px)}
.ac-num{font-family:'Playfair Display',serif;font-size:28px;font-weight:700;line-height:1;flex-shrink:0}
.ac-t{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;color:var(--white);margin-bottom:5px}
.ac-d{font-size:12px;color:rgba(255,255,255,.45);line-height:1.6;font-weight:300}
.audit-meta{display:grid;grid-template-columns:repeat(2,1fr);gap:10px}
.am-item{background:rgba(255,255,255,.04);border-radius:8px;padding:16px 18px}
.am-label{font-family:'Syne',sans-serif;font-size:9px;letter-spacing:2px;text-transform:uppercase;color:var(--lblue);margin-bottom:5px}
.am-val{font-size:13px;color:rgba(255,255,255,.7);font-weight:400}

/* ══ DISEÑO ══ */
.design-cards{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
.dc{background:var(--white);border-radius:10px;overflow:hidden;box-shadow:0 2px 16px rgba(0,0,0,.06);transition:all .25s}
.dc:hover{transform:translateY(-5px);box-shadow:0 14px 40px rgba(0,0,0,.1)}
.dc-bar{height:4px}
.dc-body{padding:24px}
.dc-t{font-family:'Syne',sans-serif;font-size:15px;font-weight:700;color:var(--text);margin-bottom:8px}
.dc-d{font-size:12.5px;color:var(--text2);line-height:1.65;font-weight:300}
.dc-tags{display:flex;flex-wrap:wrap;gap:5px;margin-top:12px}
.dctag{font-size:9px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;font-weight:600}

/* ══ PLANES ══ */
.plans-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}
.plan-card{border-radius:10px;overflow:hidden;transition:transform .28s,box-shadow .28s}
.plan-card:hover{transform:translateY(-6px);box-shadow:0 20px 50px rgba(0,0,0,.12)}
.plan-head{background:var(--dark);padding:24px 26px}
.plan-badge{font-family:'Syne',sans-serif;font-size:8px;letter-spacing:3px;text-transform:uppercase;font-weight:700;margin-bottom:7px;display:block}
.plan-name{font-family:'Playfair Display',serif;font-size:24px;font-weight:700;color:var(--white);margin-bottom:4px}
.plan-focus{font-size:12px;color:rgba(255,255,255,.35);font-style:italic}
.plan-feats{background:var(--gray);padding:20px 26px;display:flex;flex-direction:column;gap:9px}
.plan-feat{font-size:12.5px;color:#333;display:flex;gap:8px;align-items:flex-start;line-height:1.4}
.pf-dot{width:5px;height:5px;border-radius:50%;flex-shrink:0;margin-top:5px}
.pf-lbl{font-weight:500;font-family:'Syne',sans-serif;font-size:12px}
.pf-val{color:#666;font-weight:300}
.plan-cta{background:var(--dark);padding:16px 26px;border-top:1px solid rgba(255,255,255,.05)}

/* ══ CTA FINAL ══ */
.cta-section{background:var(--dark);padding:120px 80px;text-align:center;position:relative;overflow:hidden}
.cta-circles{position:absolute;inset:0;pointer-events:none}
.cta-cir{position:absolute;border-radius:50%;border:1px solid rgba(91,156,196,.06)}
.cta-eyebrow{font-family:'Syne',sans-serif;font-size:9px;letter-spacing:5px;text-transform:uppercase;color:var(--red);font-weight:700;margin-bottom:14px}
.cta-h{font-family:'Playfair Display',serif;font-size:clamp(36px,5vw,64px);font-weight:700;color:var(--white);line-height:1.1;margin-bottom:14px}
.cta-h em{font-style:italic;color:var(--lblue)}
.cta-sub{font-size:17px;color:rgba(255,255,255,.38);font-weight:300;line-height:1.75;max-width:500px;margin:0 auto 40px}
.cta-contacts{display:flex;gap:32px;justify-content:center;flex-wrap:wrap;margin-bottom:40px}
.cta-c{display:flex;align-items:center;gap:9px;font-size:15px;color:rgba(255,255,255,.55)}
.cta-c strong{color:rgba(255,255,255,.85);font-weight:400}
.cta-c a{color:rgba(255,255,255,.85);text-decoration:none;transition:color .2s}
.cta-c a:hover{color:var(--lblue)}
.cc-dot{width:5px;height:5px;border-radius:50%;flex-shrink:0}
.cta-btns{display:flex;gap:12px;justify-content:center;flex-wrap:wrap;margin-bottom:48px}
.btn-meet{font-family:'Syne',sans-serif;font-size:12px;font-weight:700;letter-spacing:2px;text-transform:uppercase;background:var(--red);color:var(--white);padding:16px 36px;border-radius:6px;text-decoration:none;transition:all .22s;display:inline-block}
.btn-meet:hover{background:#c91535;transform:translateY(-3px);box-shadow:0 12px 32px rgba(240,34,64,.32)}
.btn-wa{font-family:'Syne',sans-serif;font-size:12px;font-weight:600;letter-spacing:2px;text-transform:uppercase;border:1px solid rgba(255,255,255,.2);color:rgba(255,255,255,.7);padding:16px 36px;border-radius:6px;text-decoration:none;transition:all .22s;display:inline-block}
.btn-wa:hover{border-color:#fff;color:#fff;transform:translateY(-3px)}
.cta-tags{display:flex;flex-wrap:wrap;gap:7px;justify-content:center}
.ctag{font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:5px 12px;border:1px solid rgba(255,255,255,.09);border-radius:20px;color:rgba(255,255,255,.25);font-family:'Syne',sans-serif}

/* ══ FOOTER ══ */
footer{background:#040709;padding:36px 80px;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:16px;width:100%}
.footer-logo{font-family:'Playfair Display',serif;font-size:22px;font-weight:700;color:var(--white);letter-spacing:-1px}
.footer-sub{font-size:11px;color:rgba(255,255,255,.2);letter-spacing:1.5px;margin-top:3px}
.footer-links{display:flex;gap:22px;list-style:none}
.footer-links a{font-family:'Syne',sans-serif;font-size:10px;letter-spacing:1.5px;text-transform:uppercase;color:rgba(255,255,255,.3);text-decoration:none;transition:color .2s}
.footer-links a:hover{color:rgba(255,255,255,.7)}
.footer-legal{font-size:10px;color:rgba(255,255,255,.14)}
.linkedin-link{display:flex;align-items:center;gap:7px;font-size:11px;color:rgba(255,255,255,.35);text-decoration:none;transition:color .2s}
.linkedin-link:hover{color:var(--lblue)}
.linkedin-link svg{width:14px;height:14px;fill:currentColor}

/* ══ INFO BAND ══ */
.ib{display:flex;border-radius:6px;overflow:hidden;margin-bottom:7px}
.ib-acc{width:4px;flex-shrink:0}
.ib-body{background:var(--gray);flex:1;padding:10px 16px}
.ib-lbl{display:block;font-family:'Syne',sans-serif;font-size:9px;letter-spacing:1.5px;text-transform:uppercase;color:#888;font-weight:600;margin-bottom:2px}
.ib-val{font-size:13px;color:var(--dark);font-weight:400;line-height:1.5}

/* ══ RESPONSIVE ══ */
@media(max-width:1100px){
  .hero{grid-template-columns:1fr;padding:60px 48px 60px}
  .hero-right{display:none}
  .svc-grid{grid-template-columns:1fr 1fr}
  .plans-grid{grid-template-columns:1fr}
  .video-grid{grid-template-columns:repeat(2,1fr)}
  .audit-cards{grid-template-columns:1fr}
  .design-cards{grid-template-columns:1fr 1fr}
  .brand-aside{position:static}
  .section{padding:72px 48px}
  nav{padding:0 24px;gap:16px}
  .nav-tabs{gap:0}
  .nav-tab{font-size:10px;padding:8px 10px}
}
@media(max-width:768px){
  .hero{padding:48px 22px 52px}
  .section{padding:60px 22px}
  .hero-h{font-size:36px}
  .nav-tabs,.nav-cta{display:none}
  .mob-btn{display:flex}
  .svc-grid{grid-template-columns:1fr}
  .video-grid{grid-template-columns:1fr 1fr}
  .audit-meta{grid-template-columns:1fr}
  .design-cards{grid-template-columns:1fr}
  .process-track{grid-template-columns:repeat(2,1fr);gap:20px}
  .process-track::before{display:none}
  footer{flex-direction:column;text-align:center;padding:28px 22px}
  .footer-links{justify-content:center;flex-wrap:wrap}
  .cta-section{padding:72px 22px}
}

/* ══ GSAP / SCROLL ANIMATIONS BASE ══ */
.gs-fade{opacity:0}
.gs-up{opacity:0;transform:translateY(40px)}
.gs-left{opacity:0;transform:translateX(-40px)}
.gs-right{opacity:0;transform:translateX(40px)}
.gs-scale{opacity:0;transform:scale(.9)}
.gs-char{display:inline-block;overflow:hidden}

/* ══ PARTICLE CANVAS ══ */
#hero-canvas{position:absolute;inset:0;pointer-events:none}
</style>
</head>
<body>



<!-- ══ NAV ══ -->
<nav id="main-nav">
  <a href="#" class="nav-logo" data-page="inicio" onclick="navigate('inicio');return false">AO</a>
  <div class="nav-tabs" id="nav-tabs">
    <button class="nav-tab active" data-page="inicio" onclick="navigate('inicio')"><span data-es="Inicio" data-en="Home">Inicio</span></button>
    <button class="nav-tab" data-page="servicios" onclick="navigate('servicios')"><span data-es="Servicios" data-en="Services">Servicios</span></button>
    <button class="nav-tab" data-page="trabajo" onclick="navigate('trabajo')"><span data-es="Trabajo" data-en="Work">Trabajo</span></button>
    <button class="nav-tab" data-page="planes" onclick="navigate('planes')"><span data-es="Planes" data-en="Plans">Planes</span></button>
    <button class="nav-tab" data-page="nosotros" onclick="navigate('nosotros')"><span data-es="Nosotros" data-en="About">Nosotros</span></button>
  </div>
  <div class="nav-right">
    <div class="lang-toggle">
      <button class="lang-btn active" onclick="setLang('es')">ES</button>
      <button class="lang-btn" onclick="setLang('en')">EN</button>
    </div>
    <a href="#" class="nav-cta" onclick="navigate('contacto');return false"><span data-es="Cotizar" data-en="Get Quote">Cotizar</span></a>
  </div>
  <button class="mob-btn" id="mob-btn"><span class="ham"></span><span class="ham"></span><span class="ham"></span></button>
</nav>

<!-- ══ MOBILE MENU ══ -->
<div class="mob-menu" id="mob-menu">
  <button onclick="navigate('inicio');closeMob()"><span data-es="Inicio" data-en="Home">Inicio</span></button>
  <button onclick="navigate('servicios');closeMob()"><span data-es="Servicios" data-en="Services">Servicios</span></button>
  <button onclick="navigate('trabajo');closeMob()"><span data-es="Trabajo" data-en="Work">Trabajo</span></button>
  <button onclick="navigate('planes');closeMob()"><span data-es="Planes" data-en="Plans">Planes</span></button>
  <button onclick="navigate('nosotros');closeMob()"><span data-es="Nosotros" data-en="About">Nosotros</span></button>
  <button onclick="navigate('contacto');closeMob()" style="color:var(--lblue)"><span data-es="Contactar" data-en="Contact">Contactar</span></button>
</div>

<!-- ══════════════════════════════════════
     PAGE: INICIO
══════════════════════════════════════ -->
<div class="page active" id="page-inicio">
  <section class="hero">
    <canvas id="hero-canvas"></canvas>
    <div class="stripe" style="position:absolute;top:0;left:0;right:0;height:4px;z-index:3"><span class="s1"></span><span class="s2"></span><span class="s3"></span><span class="s4"></span><span class="s5"></span></div>
    <div class="hero-left">
      <div class="hero-eyebrow gs-left"><span data-es="Social Media Management & Estrategia Digital" data-en="Social Media Management & Digital Strategy">Social Media Management & Estrategia Digital</span></div>
      <h1 class="hero-h gs-up">
        <span data-es="Tu marca merece" data-en="Your brand deserves">Tu marca merece</span><br>
        <em data-es="crecer con estrategia." data-en="to grow with strategy.">crecer con estrategia.</em>
      </h1>
      <p class="hero-sub gs-up" data-es="Gestión de redes, campañas publicitarias, construcción de marca y auditorías digitales — todo con un especialista que conoce tu negocio." data-en="Social media management, ad campaigns, brand building and digital audits — all with a specialist who knows your business.">Gestión de redes, campañas publicitarias, construcción de marca y auditorías digitales — todo con un especialista que conoce tu negocio.</p>
      <div class="hero-btns gs-up">
        <button class="btn-pri" onclick="navigate('servicios')"><span data-es="Ver Servicios" data-en="See Services">Ver Servicios</span></button>
        <button class="btn-sec" onclick="navigate('trabajo')"><span data-es="Ver Trabajo" data-en="See Work">Ver Trabajo</span></button>
      </div>
    </div>
    <div class="hero-right">
      <div class="hero-card gs-right"><div class="hc-num">01</div><div class="hc-t" data-es="Gestión de Redes" data-en="Social Media">Gestión de Redes</div><div class="hc-d" data-es="Contenido estratégico, comunidad activa y resultados medibles." data-en="Strategic content, active community and measurable results.">Contenido estratégico, comunidad activa y resultados medibles.</div></div>
      <div class="hero-card gs-right"><div class="hc-num">02</div><div class="hc-t" data-es="Publicidad Digital" data-en="Digital Advertising">Publicidad Digital</div><div class="hc-d" data-es="Campañas de Meta Ads y Google Ads orientadas a ROI real." data-en="Meta Ads and Google Ads campaigns focused on real ROI.">Campañas de Meta Ads y Google Ads orientadas a ROI real.</div></div>
      <div class="hero-card gs-right"><div class="hc-num">03</div><div class="hc-t" data-es="Estrategia de Marca" data-en="Brand Strategy">Estrategia de Marca</div><div class="hc-d" data-es="Identidad, posicionamiento y voz de marca desde cero." data-en="Identity, positioning and brand voice from scratch.">Identidad, posicionamiento y voz de marca desde cero.</div></div>
      <div class="hero-card gs-right"><div class="hc-num">04</div><div class="hc-t" data-es="Auditorías Digitales" data-en="Digital Audits">Auditorías Digitales</div><div class="hc-d" data-es="Diagnóstico de cuentas y campañas con recomendaciones accionables." data-en="Account and campaign diagnosis with actionable recommendations.">Diagnóstico de cuentas y campañas con recomendaciones accionables.</div></div>
    </div>
    <div class="hero-scroll-hint">
      <div class="scroll-line"></div>
      <span class="scroll-text" data-es="Scroll" data-en="Scroll">Scroll</span>
    </div>
  </section>

  <!-- Propuesta de valor -->
  <section class="section gray">
    <div class="sec-label gs-left"><span data-es="Por qué elegirme" data-en="Why choose me">Por qué elegirme</span></div>
    <h2 class="sec-title gs-up" data-es="Un especialista, no una agencia." data-en="A specialist, not an agency.">Un especialista, no una agencia.</h2>
    <div class="bar gs-up"></div>
    <div style="display:grid;grid-template-columns:repeat(4,1fr);gap:14px">
      <div class="gs-scale" style="background:var(--dark);border-radius:10px;padding:28px 22px;text-align:center">
        <div style="font-family:'Playfair Display',serif;font-size:38px;font-weight:700;color:var(--lblue);line-height:1;margin-bottom:8px">1:1</div>
        <div style="font-family:'Syne',sans-serif;font-size:10px;letter-spacing:1px;color:rgba(255,255,255,.4)" data-es="Atención directa, sin intermediarios" data-en="Direct attention, no middlemen">Atención directa, sin intermediarios</div>
      </div>
      <div class="gs-scale" style="background:var(--dark);border-radius:10px;padding:28px 22px;text-align:center">
        <div style="font-family:'Playfair Display',serif;font-size:38px;font-weight:700;color:var(--blue);line-height:1;margin-bottom:8px">360°</div>
        <div style="font-family:'Syne',sans-serif;font-size:10px;letter-spacing:1px;color:rgba(255,255,255,.4)" data-es="Visión integral de tu marca digital" data-en="Comprehensive view of your digital brand">Visión integral de tu marca digital</div>
      </div>
      <div class="gs-scale" style="background:var(--dark);border-radius:10px;padding:28px 22px;text-align:center">
        <div style="font-family:'Playfair Display',serif;font-size:38px;font-weight:700;color:var(--red);line-height:1;margin-bottom:8px">ROI</div>
        <div style="font-family:'Syne',sans-serif;font-size:10px;letter-spacing:1px;color:rgba(255,255,255,.4)" data-es="Enfoque en retorno de inversión real" data-en="Focus on real return on investment">Enfoque en retorno de inversión real</div>
      </div>
      <div class="gs-scale" style="background:var(--dark);border-radius:10px;padding:28px 22px;text-align:center">
        <div style="font-family:'Playfair Display',serif;font-size:38px;font-weight:700;color:var(--lblue);line-height:1;margin-bottom:8px">Data</div>
        <div style="font-family:'Syne',sans-serif;font-size:10px;letter-spacing:1px;color:rgba(255,255,255,.4)" data-es="Decisiones basadas en métricas reales" data-en="Decisions based on real metrics">Decisiones basadas en métricas reales</div>
      </div>
    </div>
  </section>

  <!-- CTA rápido -->
  <div style="background:var(--dark);padding:52px 80px;display:flex;align-items:center;justify-content:space-between;gap:24px;flex-wrap:wrap">
    <div>
      <div style="font-family:'Playfair Display',serif;font-size:28px;font-weight:700;color:var(--white)" class="gs-left" data-es='"Tu marca, con estrategia."' data-en='"Your brand, with strategy."'>"Tu marca, con estrategia."</div>
      <div style="font-size:14px;color:rgba(255,255,255,.35);margin-top:5px" class="gs-left" data-es="Alfonso Ortiz · Social Media Management" data-en="Alfonso Ortiz · Social Media Management">Alfonso Ortiz · Social Media Management</div>
    </div>
    <button class="btn-pri gs-right" onclick="navigate('contacto')"><span data-es="Agendar reunión" data-en="Schedule meeting">Agendar reunión</span></button>
  </div>
</div>

<!-- ══════════════════════════════════════
     PAGE: SERVICIOS
══════════════════════════════════════ -->
<div class="page" id="page-servicios">
  <section class="section">
    <div class="sec-label gs-left"><span data-es="Lo que ofrezco" data-en="What I offer">Lo que ofrezco</span></div>
    <h2 class="sec-title gs-up" data-es="Servicios que impulsan tu marca" data-en="Services that drive your brand">Servicios que impulsan tu marca</h2>
    <div class="bar gs-up"></div>
    <div class="svc-grid gs-up">
      <div class="svc-tile"><span class="svc-num">01</span><div class="svc-bar" style="background:var(--lblue)"></div><div class="svc-t" data-es="Gestión de Redes Sociales" data-en="Social Media Management">Gestión de Redes Sociales</div><div class="svc-d" data-es="Manejo completo de Instagram, Facebook y TikTok: parrilla, contenido, publicación y gestión de comunidad activa." data-en="Full management of Instagram, Facebook and TikTok: content calendar, design, publishing and active community management.">Manejo completo de Instagram, Facebook y TikTok: parrilla, contenido, publicación y gestión de comunidad activa.</div></div>
      <div class="svc-tile"><span class="svc-num">02</span><div class="svc-bar" style="background:var(--blue)"></div><div class="svc-t" data-es="Publicidad Digital & Ads" data-en="Digital Advertising & Ads">Publicidad Digital & Ads</div><div class="svc-d" data-es="Diseño, configuración y optimización diaria de campañas en Meta Ads y Google Ads enfocadas en leads, ventas y reconocimiento." data-en="Design, setup and daily optimization of Meta Ads and Google Ads campaigns focused on leads, sales and brand awareness.">Diseño, configuración y optimización diaria de campañas en Meta Ads y Google Ads enfocadas en leads, ventas y reconocimiento.</div></div>
      <div class="svc-tile"><span class="svc-num">03</span><div class="svc-bar" style="background:var(--dblue)"></div><div class="svc-t" data-es="Estrategia de Marca" data-en="Brand Strategy">Estrategia de Marca</div><div class="svc-d" data-es="Construcción de identidad desde cero: naming, manual de marca, personificación y posicionamiento digital." data-en="Brand building from scratch: naming, brand manual, brand personality and digital positioning.">Construcción de identidad desde cero: naming, manual de marca, personificación y posicionamiento digital.</div></div>
      <div class="svc-tile"><span class="svc-num">04</span><div class="svc-bar" style="background:var(--red)"></div><div class="svc-t" data-es="Auditorías Digitales" data-en="Digital Audits">Auditorías Digitales</div><div class="svc-d" data-es="Diagnóstico a profundidad de tus cuentas de Meta y campañas activas, con dashboards, informe y sesión de consultoría." data-en="In-depth diagnosis of your Meta accounts and active campaigns, with dashboards, report and consulting session.">Diagnóstico a profundidad de tus cuentas de Meta y campañas activas, con dashboards, informe y sesión de consultoría.</div></div>
      <div class="svc-tile"><span class="svc-num">05</span><div class="svc-bar" style="background:var(--dark)"></div><div class="svc-t" data-es="Diseño & Creativos" data-en="Design & Creative">Diseño & Creativos</div><div class="svc-d" data-es="Identidad visual, logo, brand book, posts, reels y piezas publicitarias que comunican el mensaje correcto." data-en="Visual identity, logo, brand book, posts, reels and ad creatives that communicate the right message.">Identidad visual, logo, brand book, posts, reels y piezas publicitarias que comunican el mensaje correcto.</div></div>
      <div class="svc-tile"><span class="svc-num">06</span><div class="svc-bar" style="background:var(--lblue)"></div><div class="svc-t" data-es="Consultoría Digital" data-en="Digital Consulting">Consultoría Digital</div><div class="svc-d" data-es="Sesiones estratégicas para orientarte en decisiones de presencia digital, pauta, contenido y posicionamiento." data-en="Strategic sessions to guide your decisions on digital presence, advertising, content and positioning.">Sesiones estratégicas para orientarte en decisiones de presencia digital, pauta, contenido y posicionamiento.</div></div>
    </div>
  </section>

  <!-- Proceso -->
  <section class="section gray">
    <div class="sec-label gs-left"><span data-es="Metodología" data-en="Methodology">Metodología</span></div>
    <h2 class="sec-title gs-up" data-es="Cómo trabajamos juntos" data-en="How we work together">Cómo trabajamos juntos</h2>
    <div class="bar gs-up"></div>
    <div class="process-track">
      <div class="proc-step gs-up"><div class="proc-n" style="background:var(--lblue)">1</div><div class="proc-t" data-es="Briefing" data-en="Briefing">Briefing</div><div class="proc-d" data-es="Conocemos tu marca y objetivos" data-en="We learn about your brand and goals">Conocemos tu marca y objetivos</div></div>
      <div class="proc-step gs-up"><div class="proc-n" style="background:var(--blue)">2</div><div class="proc-t" data-es="Diagnóstico" data-en="Diagnosis">Diagnóstico</div><div class="proc-d" data-es="Auditamos e identificamos oportunidades" data-en="We audit and identify opportunities">Auditamos e identificamos oportunidades</div></div>
      <div class="proc-step gs-up"><div class="proc-n" style="background:var(--dblue)">3</div><div class="proc-t" data-es="Estrategia" data-en="Strategy">Estrategia</div><div class="proc-d" data-es="Diseñamos el plan completo" data-en="We design the complete plan">Diseñamos el plan completo</div></div>
      <div class="proc-step gs-up"><div class="proc-n" style="background:var(--dark)">4</div><div class="proc-t" data-es="Producción" data-en="Production">Producción</div><div class="proc-d" data-es="Contenido y campañas" data-en="Content and campaigns">Contenido y campañas</div></div>
      <div class="proc-step gs-up"><div class="proc-n" style="background:var(--red)">5</div><div class="proc-t" data-es="Lanzamiento" data-en="Launch">Lanzamiento</div><div class="proc-d" data-es="Publicamos y activamos" data-en="We publish and activate">Publicamos y activamos</div></div>
      <div class="proc-step gs-up"><div class="proc-n" style="background:var(--blue)">6</div><div class="proc-t" data-es="Optimización" data-en="Optimization">Optimización</div><div class="proc-d" data-es="Medimos y mejoramos siempre" data-en="We measure and always improve">Medimos y mejoramos siempre</div></div>
    </div>
  </section>
</div>

<!-- ══════════════════════════════════════
     PAGE: TRABAJO
══════════════════════════════════════ -->
<div class="page" id="page-trabajo">
  <section class="section dark">
    <div class="sec-label gs-left" style="color:var(--lblue)"><span data-es="Portafolio de videos" data-en="Video portfolio">Portafolio de videos</span></div>
    <h2 class="sec-title light gs-up" data-es="Trabajo real. Resultados reales." data-en="Real work. Real results.">Trabajo real. Resultados reales.</h2>
    <div class="bar gs-up"></div>
    <p class="sec-sub light gs-up" data-es="Contenido producido para clientes reales — desde reels de marca hasta campañas de alto impacto." data-en="Content produced for real clients — from brand reels to high-impact campaigns.">Contenido producido para clientes reales — desde reels de marca hasta campañas de alto impacto.</p>
    <p class="gs-up" style="font-size:12px;color:rgba(255,255,255,.3);margin-bottom:28px;font-style:italic;margin-top:-28px" data-es="Haz clic en cualquier video para verlo en YouTube." data-en="Click any video to watch it on YouTube.">Haz clic en cualquier video para verlo en YouTube.</p>
    <div class="video-grid" id="video-grid">
      <a class="video-card" href="https://www.youtube.com/shorts/apTKCTMSZJk" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Animación</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/apTKCTMSZJk/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/apTKCTMSZJk/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="AG Solutions">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Animación</div>
          <div class="video-type">AG Solutions</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/lY6kIgfbE44" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Reel</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/lY6kIgfbE44/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/lY6kIgfbE44/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="AG Solutions">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Reel</div>
          <div class="video-type">AG Solutions</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/XPL03eyDVAo" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Reel</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/XPL03eyDVAo/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/XPL03eyDVAo/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="AG Solutions">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Reel</div>
          <div class="video-type">AG Solutions</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/oXox4S_X9FI" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Reel</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/oXox4S_X9FI/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/oXox4S_X9FI/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="AG Solutions">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Reel</div>
          <div class="video-type">AG Solutions</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/ZLIAmCvabeE" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Reel</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/ZLIAmCvabeE/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/ZLIAmCvabeE/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="Campaña">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Reel</div>
          <div class="video-type">Campaña</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/xNsJoU7VeyI" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Testimonio</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/xNsJoU7VeyI/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/xNsJoU7VeyI/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="Testimoniales">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Testimonio</div>
          <div class="video-type">Testimoniales</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/M6dCwALZuAk" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Ad</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/M6dCwALZuAk/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/M6dCwALZuAk/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="Video Campaña">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Ad</div>
          <div class="video-type">Video Campaña</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/diYTP24m2OY" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Ad</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/diYTP24m2OY/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/diYTP24m2OY/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="Video Campaña">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Ad</div>
          <div class="video-type">Video Campaña</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/B-0aUcLjSCQ" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Ad</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/B-0aUcLjSCQ/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/B-0aUcLjSCQ/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="Brandi">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Ad</div>
          <div class="video-type">Brandi</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/3M60MaiU6XY" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Remarketing</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/3M60MaiU6XY/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/3M60MaiU6XY/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="Remarketing">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Remarketing</div>
          <div class="video-type">Remarketing</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/Mjt6la1d9RM" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Ad</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/Mjt6la1d9RM/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/Mjt6la1d9RM/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="Players">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Ad</div>
          <div class="video-type">Players</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/FPagsiK-BVw" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Ad</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/FPagsiK-BVw/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/FPagsiK-BVw/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="Hotel">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Ad</div>
          <div class="video-type">Hotel</div>
        </div>
      </a>
      <a class="video-card" href="https://www.youtube.com/shorts/oN_hGik30vo" target="_blank" rel="noopener" style="cursor:pointer;background:#000;text-decoration:none;display:block">
        <div style="position:absolute;top:10px;left:10px;z-index:2;background:rgba(8,13,15,.82);color:var(--white);font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1.5px;text-transform:uppercase;padding:3px 9px;border-radius:20px">Ad</div>
        <div style="position:absolute;top:10px;right:10px;z-index:2;background:rgba(255,0,0,.85);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:flex;align-items:center;gap:4px">
          <svg width="8" height="8" viewBox="0 0 10 10" fill="white"><path d="M2 1l7 4-7 4V1z"/></svg>YT
        </div>
        <img src="https://img.youtube.com/vi/oN_hGik30vo/maxresdefault.jpg"
          onerror="this.src='https://img.youtube.com/vi/oN_hGik30vo/hqdefault.jpg'"
          style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0;transition:transform .5s ease"
          loading="lazy" alt="Seguridad">
        <div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(8,13,15,.75) 0%,rgba(8,13,15,.1) 60%,transparent 100%)"></div>
        <div class="video-play"><svg viewBox="0 0 18 18"><path d="M5 3l12 6-12 6V3z"/></svg></div>
        <div class="video-overlay">
          <div class="video-label">Ad</div>
          <div class="video-type">Seguridad</div>
        </div>
      </a>
    </div>
  </section>
</div>

<!-- ══════════════════════════════════════
     PAGE: PLANES
══════════════════════════════════════ -->
<div class="page" id="page-planes">
  <section class="section">
    <div class="sec-label gs-left"><span data-es="Gestión mensual" data-en="Monthly management">Gestión mensual</span></div>
    <h2 class="sec-title gs-up" data-es="Planes para cada etapa de tu marca" data-en="Plans for every stage of your brand">Planes para cada etapa de tu marca</h2>
    <div class="bar gs-up"></div>
    <p class="sec-sub gs-up" data-es="Contáctame para recibir una cotización personalizada según tus objetivos y presupuesto." data-en="Contact me to receive a personalized quote based on your goals and budget.">Contáctame para recibir una cotización personalizada según tus objetivos y presupuesto.</p>
    <div class="plans-grid">
      <div class="plan-card gs-up">
        <div class="plan-head"><div class="plan-badge" style="color:var(--lblue)" data-es="Básico" data-en="Basic">Básico</div><div class="plan-name" data-es="Presencia" data-en="Presence">Presencia</div><div class="plan-focus" data-es="Mantenimiento de marca" data-en="Brand maintenance">Mantenimiento de marca</div></div>
        <div class="plan-feats">
          <div class="plan-feat"><div class="pf-dot" style="background:var(--lblue)"></div><div><span class="pf-lbl" data-es="8 posts estáticos" data-en="8 static posts">8 posts estáticos</span></div></div>
          <div class="plan-feat"><div class="pf-dot" style="background:var(--lblue)"></div><div><span class="pf-lbl" data-es="2 reels / mes" data-en="2 reels / month">2 reels / mes</span></div></div>
          <div class="plan-feat"><div class="pf-dot" style="background:var(--lblue)"></div><div><span class="pf-lbl" data-es="Comunidad Lun–Vie" data-en="Community Mon–Fri">Comunidad Lun–Vie</span></div></div>
          <div class="plan-feat"><div class="pf-dot" style="background:var(--lblue)"></div><div><span class="pf-lbl" data-es="Reporte mensual" data-en="Monthly report">Reporte mensual</span></div></div>
        </div>
        <div class="plan-cta"><button class="btn-pri" style="width:100%;text-align:center" onclick="navigate('contacto')"><span data-es="Solicitar info" data-en="Request info">Solicitar info</span></button></div>
      </div>
      <div class="plan-card gs-up" style="box-shadow:0 0 0 2px var(--blue)">
        <div class="plan-head" style="position:relative"><div style="position:absolute;top:12px;right:14px;background:var(--blue);color:#fff;font-family:'Syne',sans-serif;font-size:8px;letter-spacing:2px;text-transform:uppercase;padding:3px 9px;border-radius:20px;font-weight:700" data-es="Más popular" data-en="Most popular">Más popular</div><div class="plan-badge" style="color:var(--blue)" data-es="Intermedio" data-en="Mid">Intermedio</div><div class="plan-name" data-es="Crecimiento" data-en="Growth">Crecimiento</div><div class="plan-focus" data-es="Captación y alcance" data-en="Lead gen & reach">Captación y alcance</div></div>
        <div class="plan-feats">
          <div class="plan-feat"><div class="pf-dot" style="background:var(--blue)"></div><div><span class="pf-lbl" data-es="10 posts estáticos" data-en="10 static posts">10 posts estáticos</span></div></div>
          <div class="plan-feat"><div class="pf-dot" style="background:var(--blue)"></div><div><span class="pf-lbl" data-es="4 reels / mes" data-en="4 reels / month">4 reels / mes</span></div></div>
          <div class="plan-feat"><div class="pf-dot" style="background:var(--blue)"></div><div><span class="pf-lbl" data-es="Comunidad Lun–Sáb" data-en="Community Mon–Sat">Comunidad Lun–Sáb</span></div></div>
          <div class="plan-feat"><div class="pf-dot" style="background:var(--blue)"></div><div><span class="pf-lbl" data-es="Campaña Ads básica" data-en="Basic Ads campaign">Campaña Ads básica</span></div></div>
          <div class="plan-feat"><div class="pf-dot" style="background:var(--blue)"></div><div><span class="pf-lbl" data-es="Reporte quincenal" data-en="Bi-weekly report">Reporte quincenal</span></div></div>
        </div>
        <div class="plan-cta"><button class="btn-pri" style="width:100%;text-align:center" onclick="navigate('contacto')"><span data-es="Solicitar info" data-en="Request info">Solicitar info</span></button></div>
      </div>
      <div class="plan-card gs-up">
        <div class="plan-head"><div class="plan-badge" style="color:var(--red)" data-es="Premium" data-en="Premium">Premium</div><div class="plan-name" data-es="Dominio" data-en="Domination">Dominio</div><div class="plan-focus" data-es="Posicionamiento agresivo" data-en="Aggressive positioning">Posicionamiento agresivo</div></div>
        <div class="plan-feats">
          <div class="plan-feat"><div class="pf-dot" style="background:var(--red)"></div><div><span class="pf-lbl" data-es="12 posts estáticos" data-en="12 static posts">12 posts estáticos</span></div></div>
          <div class="plan-feat"><div class="pf-dot" style="background:var(--red)"></div><div><span class="pf-lbl" data-es="8 reels / mes" data-en="8 reels / month">8 reels / mes</span></div></div>
          <div class="plan-feat"><div class="pf-dot" style="background:var(--red)"></div><div><span class="pf-lbl" data-es="Comunidad Lun–Dom" data-en="Community Mon–Sun">Comunidad Lun–Dom</span></div></div>
          <div class="plan-feat"><div class="pf-dot" style="background:var(--red)"></div><div><span class="pf-lbl" data-es="Funnel Ads completo" data-en="Full Ads funnel">Funnel Ads completo</span></div></div>
          <div class="plan-feat"><div class="pf-dot" style="background:var(--red)"></div><div><span class="pf-lbl" data-es="Dashboard semanal" data-en="Weekly dashboard">Dashboard semanal</span></div></div>
        </div>
        <div class="plan-cta"><button class="btn-pri" style="width:100%;text-align:center" onclick="navigate('contacto')"><span data-es="Solicitar info" data-en="Request info">Solicitar info</span></button></div>
      </div>
    </div>
  </section>

  <!-- Auditoría -->
  <section class="section dark">
    <div class="sec-label gs-left" style="color:var(--lblue)"><span data-es="Diagnóstico digital" data-en="Digital diagnosis">Diagnóstico digital</span></div>
    <h2 class="sec-title light gs-up" data-es="Auditoría Estratégica de Meta Ads" data-en="Strategic Meta Ads Audit">Auditoría Estratégica de Meta Ads</h2>
    <div class="bar gs-up"></div>
    <p class="sec-sub light gs-up" data-es="¿Inviertes en publicidad pero no ves resultados claros? Te entrego un diagnóstico completo con datos reales y recomendaciones accionables." data-en="Are you investing in advertising but not seeing clear results? I deliver a complete diagnosis with real data and actionable recommendations.">¿Inviertes en publicidad pero no ves resultados claros? Te entrego un diagnóstico completo con datos reales y recomendaciones accionables.</p>
    <div class="audit-cards">
      <div class="audit-card gs-scale"><div class="ac-num" style="color:var(--lblue)">01</div><div><div class="ac-t" data-es="Análisis a profundidad" data-en="In-depth analysis">Análisis a profundidad</div><div class="ac-d" data-es="Revisión completa de hasta 2 cuentas de Meta: estructura, segmentación, creativos y rendimiento histórico." data-en="Full review of up to 2 Meta accounts: structure, targeting, creatives and historical performance.">Revisión completa de hasta 2 cuentas de Meta: estructura, segmentación, creativos y rendimiento histórico.</div></div></div>
      <div class="audit-card gs-scale"><div class="ac-num" style="color:var(--blue)">02</div><div><div class="ac-t" data-es="4 Dashboards interactivos" data-en="4 Interactive Dashboards">4 Dashboards interactivos</div><div class="ac-d" data-es="Tableros de visualización con KPIs, tendencias y desglose por campaña y creativos." data-en="Visualization dashboards with KPIs, trends and breakdown by campaign and creatives.">Tableros de visualización con KPIs, tendencias y desglose por campaña y creativos.</div></div></div>
      <div class="audit-card gs-scale"><div class="ac-num" style="color:var(--dblue)">03</div><div><div class="ac-t" data-es="Documento de diagnóstico" data-en="Diagnosis document">Documento de diagnóstico</div><div class="ac-d" data-es="Informe detallado con hallazgos y recomendaciones específicas para optimizar tus campañas." data-en="Detailed report with findings and specific recommendations to optimize your campaigns.">Informe detallado con hallazgos y recomendaciones específicas para optimizar tus campañas.</div></div></div>
      <div class="audit-card gs-scale"><div class="ac-num" style="color:var(--red)">04</div><div><div class="ac-t" data-es="Sesión de consultoría 1–2h" data-en="1–2h consulting session">Sesión de consultoría 1–2h</div><div class="ac-d" data-es="Reunión para explicar hallazgos y asesorarte en qué cambios implementar y cómo priorizarlos." data-en="Meeting to explain findings and advise you on what changes to implement and how to prioritize them.">Reunión para explicar hallazgos y asesorarte en qué cambios implementar y cómo priorizarlos.</div></div></div>
    </div>
    <div class="audit-meta gs-up">
      <div class="am-item"><div class="am-label" data-es="Entrega" data-en="Delivery">Entrega</div><div class="am-val" data-es="6 días hábiles desde recepción de accesos" data-en="6 business days from access receipt">6 días hábiles desde recepción de accesos</div></div>
      <div class="am-item"><div class="am-label" data-es="Pago" data-en="Payment">Pago</div><div class="am-val" data-es="50% anticipo · 50% contra entrega" data-en="50% upfront · 50% on delivery">50% anticipo · 50% contra entrega</div></div>
    </div>
    <div style="margin-top:28px"><button class="btn-pri gs-up" onclick="navigate('contacto')"><span data-es="Solicitar auditoría" data-en="Request audit">Solicitar auditoría</span></button></div>
  </section>

  <!-- Diseño -->
  <section class="section gray">
    <div class="sec-label gs-left"><span data-es="Diseño & Creativos" data-en="Design & Creative">Diseño & Creativos</span></div>
    <h2 class="sec-title gs-up" data-es="Visual que comunica y convierte" data-en="Visual that communicates and converts">Visual que comunica y convierte</h2>
    <div class="bar gs-up"></div>
    <div class="design-cards">
      <div class="dc gs-up"><div class="dc-bar" style="background:var(--dblue)"></div><div class="dc-body"><div class="dc-t" data-es="Identidad Visual" data-en="Visual Identity">Identidad Visual</div><div class="dc-d" data-es="Logo principal y secundario, versiones BN, paleta de colores HEX/RGB, tipografías con guía de uso y concepto creativo." data-en="Primary and secondary logo, BW versions, HEX/RGB color palette, typography with usage guide and creative concept.">Logo principal y secundario, versiones BN, paleta de colores HEX/RGB, tipografías con guía de uso y concepto creativo.</div><div class="dc-tags"><span class="dctag" style="background:#e8f1f8;color:#0a3d5e">Logo</span><span class="dctag" style="background:#e8f1f8;color:#0a3d5e">Paleta</span></div></div></div>
      <div class="dc gs-up"><div class="dc-bar" style="background:var(--blue)"></div><div class="dc-body"><div class="dc-t" data-es="Brand Book Completo" data-en="Complete Brand Book">Brand Book Completo</div><div class="dc-d" data-es="Manual de identidad: uso del logo, área de seguridad, tamaños mínimos, usos incorrectos, aplicación de colores y mockups." data-en="Identity manual: logo usage, safety area, minimum sizes, incorrect uses, color application and mockups.">Manual de identidad: uso del logo, área de seguridad, tamaños mínimos, usos incorrectos, aplicación de colores y mockups.</div><div class="dc-tags"><span class="dctag" style="background:#e6f1fb;color:#0c447c">Manual</span><span class="dctag" style="background:#e6f1fb;color:#0c447c">Mockups</span></div></div></div>
      <div class="dc gs-up"><div class="dc-bar" style="background:var(--red)"></div><div class="dc-body"><div class="dc-t" data-es="Contenido & Ads" data-en="Content & Ads">Contenido & Ads</div><div class="dc-d" data-es="Posts, carruseles, reels, stories, banners y creativos publicitarios para Meta Ads, TikTok Ads y Google Display." data-en="Posts, carousels, reels, stories, banners and ad creatives for Meta Ads, TikTok Ads and Google Display.">Posts, carruseles, reels, stories, banners y creativos publicitarios para Meta Ads, TikTok Ads y Google Display.</div><div class="dc-tags"><span class="dctag" style="background:#fdecea;color:#791f1f">Reels</span><span class="dctag" style="background:#fdecea;color:#791f1f">Ads</span></div></div></div>
    </div>
  </section>
</div>

<!-- ══════════════════════════════════════
     PAGE: NOSOTROS
══════════════════════════════════════ -->
<div class="page" id="page-nosotros">

  <!-- Bio -->
  <section class="section">
    <div class="sec-label gs-left"><span data-es="Quién soy" data-en="Who I am">Quién soy</span></div>
    <h2 class="sec-title gs-up" data-es="El especialista detrás de los resultados." data-en="The specialist behind the results.">El especialista detrás de los resultados.</h2>
    <div class="bar gs-up"></div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:60px;align-items:start">
      <div>
        <p style="font-size:17px;color:var(--text2);line-height:1.85;font-weight:300;margin-bottom:20px" class="gs-left"
          data-es="No soy una agencia masiva. Soy un especialista de alto enfoque que trabaja directamente contigo para construir y escalar tu presencia digital con estrategia real, ejecución profesional y resultados medibles."
          data-en="I'm not a massive agency. I'm a high-focus specialist who works directly with you to build and scale your digital presence with real strategy, professional execution and measurable results.">No soy una agencia masiva. Soy un especialista de alto enfoque que trabaja directamente contigo para construir y escalar tu presencia digital con estrategia real, ejecución profesional y resultados medibles.</p>
        <p style="font-size:17px;color:var(--text2);line-height:1.85;font-weight:300;margin-bottom:36px" class="gs-left"
          data-es="Combino visión estratégica, creatividad y análisis de datos en un solo lugar — sin intermediarios, sin demoras y con comunicación directa."
          data-en="I combine strategic vision, creativity and data analysis in one place — no middlemen, no delays and direct communication.">Combino visión estratégica, creatividad y análisis de datos en un solo lugar — sin intermediarios, sin demoras y con comunicación directa.</p>
        <div class="brand-list gs-up">
          <div class="brand-item">
            <div class="bi-n">01</div>
            <div>
              <div class="bi-t" data-es="Misión" data-en="Mission">Misión</div>
              <div class="bi-d" data-es="Potenciar la presencia digital de marcas y profesionales mediante estrategia, contenido y publicidad que conecten de forma auténtica y generen resultados concretos." data-en="Empower the digital presence of brands and professionals through strategy, content and advertising that connect authentically and generate concrete results.">Potenciar la presencia digital de marcas y profesionales mediante estrategia, contenido y publicidad que conecten de forma auténtica y generen resultados concretos.</div>
            </div>
          </div>
          <div class="brand-item">
            <div class="bi-n">02</div>
            <div>
              <div class="bi-t" data-es="Visión" data-en="Vision">Visión</div>
              <div class="bi-d" data-es="Ser el referente de confianza en gestión de marketing digital para marcas que buscan crecer con estrategia clara, identidad fuerte y comunicación coherente." data-en="To be the trusted reference in digital marketing management for brands seeking to grow with clear strategy, strong identity and coherent communication.">Ser el referente de confianza en gestión de marketing digital para marcas que buscan crecer con estrategia clara, identidad fuerte y comunicación coherente.</div>
            </div>
          </div>
        </div>
      </div>
      <div class="brand-aside gs-right">
        <div class="ba-label" data-es="Tagline" data-en="Tagline">Tagline</div>
        <div class="ba-t" style="font-family:'Playfair Display',serif;font-style:italic;font-size:22px" data-es='"Tu marca, con estrategia."' data-en='"Your brand, with strategy."'>"Tu marca, con estrategia."</div>
        <p style="font-size:13px;color:rgba(255,255,255,.4);line-height:1.7;font-weight:300;margin:16px 0 26px"
          data-es="Este tagline resume todo: no se trata de publicar por publicar. Cada pieza de contenido, cada campaña y cada decisión tiene un propósito estratégico detrás."
          data-en="This tagline says it all: it's not about posting for the sake of posting. Every piece of content, every campaign and every decision has a strategic purpose behind it.">Este tagline resume todo: no se trata de publicar por publicar. Cada pieza de contenido, cada campaña y cada decisión tiene un propósito estratégico detrás.</p>
        <button class="btn-pri" style="width:100%;text-align:center" onclick="navigate('contacto')"><span data-es="Trabajemos juntos" data-en="Let's work together">Trabajemos juntos</span></button>
      </div>
    </div>
  </section>

  <!-- Valores — full section -->
  <section class="section dark">
    <div class="sec-label gs-left" style="color:var(--lblue)"><span data-es="Valores de Marca" data-en="Brand Values">Valores de Marca</span></div>
    <h2 class="sec-title light gs-up" data-es="Lo que guía cada proyecto." data-en="What guides every project.">Lo que guía cada proyecto.</h2>
    <div class="bar gs-up"></div>
    <p class="sec-sub light gs-up"
      data-es="Estos no son valores decorativos — son los principios que determinan cómo trabajo, qué prometo y cómo mido el éxito en cada colaboración."
      data-en="These aren't decorative values — they're the principles that determine how I work, what I promise and how I measure success in every collaboration.">Estos no son valores decorativos — son los principios que determinan cómo trabajo, qué prometo y cómo mido el éxito en cada colaboración.</p>

    <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:2px;background:rgba(255,255,255,.04);border-radius:12px;overflow:hidden" id="valores-grid">

      <!-- Valor 1 -->
      <div class="valor-card gs-scale" style="background:var(--dark);padding:36px 30px;border:1px solid rgba(255,255,255,.06);transition:background .3s,transform .25s;cursor:default" onmouseenter="this.style.background='rgba(91,156,196,.1)'" onmouseleave="this.style.background='var(--dark)'">
        <div style="width:44px;height:44px;border-radius:10px;background:rgba(91,156,196,.15);display:flex;align-items:center;justify-content:center;margin-bottom:18px">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none"><path d="M10 2l2.4 5 5.6.8-4 3.9.9 5.5L10 14.8 5.1 17.2l.9-5.5L2 7.8l5.6-.8L10 2z" stroke="#5b9cc4" stroke-width="1.4" stroke-linejoin="round"/></svg>
        </div>
        <div style="font-family:'Syne',sans-serif;font-size:13px;font-weight:700;color:var(--lblue);letter-spacing:1px;text-transform:uppercase;margin-bottom:10px" data-es="Profesionalismo" data-en="Professionalism">Profesionalismo</div>
        <div style="font-size:14px;font-weight:400;color:var(--white);margin-bottom:8px;font-family:'Playfair Display',serif" data-es="Calidad que no negocia." data-en="Quality that doesn't negotiate.">Calidad que no negocia.</div>
        <div style="font-size:13px;color:rgba(255,255,255,.45);line-height:1.7;font-weight:300" data-es="Cada entregable pasa por un estándar alto antes de salir. El nombre detrás de cada pieza importa, por eso no se entrega nada a medias." data-en="Every deliverable meets a high standard before delivery. The name behind each piece matters, which is why nothing is delivered halfway.">Cada entregable pasa por un estándar alto antes de salir. El nombre detrás de cada pieza importa, por eso no se entrega nada a medias.</div>
      </div>

      <!-- Valor 2 -->
      <div class="valor-card gs-scale" style="background:var(--dark);padding:36px 30px;border:1px solid rgba(255,255,255,.06);transition:background .3s,transform .25s;cursor:default" onmouseenter="this.style.background='rgba(32,119,194,.1)'" onmouseleave="this.style.background='var(--dark)'">
        <div style="width:44px;height:44px;border-radius:10px;background:rgba(32,119,194,.15);display:flex;align-items:center;justify-content:center;margin-bottom:18px">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none"><path d="M3 14l4-4 3 3 4-5 3 3" stroke="#2077c2" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/><circle cx="10" cy="4" r="2" stroke="#2077c2" stroke-width="1.3"/></svg>
        </div>
        <div style="font-family:'Syne',sans-serif;font-size:13px;font-weight:700;color:var(--blue);letter-spacing:1px;text-transform:uppercase;margin-bottom:10px" data-es="Estrategia" data-en="Strategy">Estrategia</div>
        <div style="font-size:14px;font-weight:400;color:var(--white);margin-bottom:8px;font-family:'Playfair Display',serif" data-es="Datos antes que intuición." data-en="Data before intuition.">Datos antes que intuición.</div>
        <div style="font-size:13px;color:rgba(255,255,255,.45);line-height:1.7;font-weight:300" data-es="Ninguna campaña o pieza de contenido nace sin un objetivo claro detrás. Las decisiones se basan en métricas reales, no en tendencias pasajeras." data-en="No campaign or content piece is created without a clear objective behind it. Decisions are based on real metrics, not passing trends.">Ninguna campaña o pieza de contenido nace sin un objetivo claro detrás. Las decisiones se basan en métricas reales, no en tendencias pasajeras.</div>
      </div>

      <!-- Valor 3 -->
      <div class="valor-card gs-scale" style="background:var(--dark);padding:36px 30px;border:1px solid rgba(255,255,255,.06);transition:background .3s,transform .25s;cursor:default" onmouseenter="this.style.background='rgba(15,95,138,.15)'" onmouseleave="this.style.background='var(--dark)'">
        <div style="width:44px;height:44px;border-radius:10px;background:rgba(15,95,138,.2);display:flex;align-items:center;justify-content:center;margin-bottom:18px">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none"><path d="M10 2C5.6 2 2 5.6 2 10s3.6 8 8 8 8-3.6 8-8-3.6-8-8-8z" stroke="#0f5f8a" stroke-width="1.4"/><path d="M10 6v4l3 2" stroke="#0f5f8a" stroke-width="1.4" stroke-linecap="round"/></svg>
        </div>
        <div style="font-family:'Syne',sans-serif;font-size:13px;font-weight:700;color:var(--dblue);letter-spacing:1px;text-transform:uppercase;margin-bottom:10px" data-es="Transparencia" data-en="Transparency">Transparencia</div>
        <div style="font-size:14px;font-weight:400;color:var(--white);margin-bottom:8px;font-family:'Playfair Display',serif" data-es="La verdad, aunque incomode." data-en="The truth, even when it's uncomfortable.">La verdad, aunque incomode.</div>
        <div style="font-size:13px;color:rgba(255,255,255,.45);line-height:1.7;font-weight:300" data-es="Si algo no está funcionando, lo digo. Si hay una mejor forma de invertir el presupuesto, lo propongo. La confianza del cliente vale más que cualquier venta." data-en="If something isn't working, I say so. If there's a better way to invest the budget, I propose it. Client trust is worth more than any sale.">Si algo no está funcionando, lo digo. Si hay una mejor forma de invertir el presupuesto, lo propongo. La confianza del cliente vale más que cualquier venta.</div>
      </div>

      <!-- Valor 4 -->
      <div class="valor-card gs-scale" style="background:var(--dark);padding:36px 30px;border:1px solid rgba(255,255,255,.06);transition:background .3s,transform .25s;cursor:default" onmouseenter="this.style.background='rgba(240,34,64,.08)'" onmouseleave="this.style.background='var(--dark)'">
        <div style="width:44px;height:44px;border-radius:10px;background:rgba(240,34,64,.12);display:flex;align-items:center;justify-content:center;margin-bottom:18px">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none"><path d="M4 10h3l2-5 3 10 2-5h2" stroke="#f02240" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
        </div>
        <div style="font-family:'Syne',sans-serif;font-size:13px;font-weight:700;color:var(--red);letter-spacing:1px;text-transform:uppercase;margin-bottom:10px" data-es="Orientación a Resultados" data-en="Results-Oriented">Orientación a Resultados</div>
        <div style="font-size:14px;font-weight:400;color:var(--white);margin-bottom:8px;font-family:'Playfair Display',serif" data-es="ROI real, no métricas vacías." data-en="Real ROI, not empty metrics.">ROI real, no métricas vacías.</div>
        <div style="font-size:13px;color:rgba(255,255,255,.45);line-height:1.7;font-weight:300" data-es="El éxito no se mide en likes: se mide en leads generados, ventas cerradas, costo por resultado y crecimiento sostenido de la marca." data-en="Success is not measured in likes: it's measured in leads generated, sales closed, cost per result and sustained brand growth.">El éxito no se mide en likes: se mide en leads generados, ventas cerradas, costo por resultado y crecimiento sostenido de la marca.</div>
      </div>

      <!-- Valor 5 -->
      <div class="valor-card gs-scale" style="background:var(--dark);padding:36px 30px;border:1px solid rgba(255,255,255,.06);transition:background .3s,transform .25s;cursor:default" onmouseenter="this.style.background='rgba(91,156,196,.08)'" onmouseleave="this.style.background='var(--dark)'">
        <div style="width:44px;height:44px;border-radius:10px;background:rgba(91,156,196,.1);display:flex;align-items:center;justify-content:center;margin-bottom:18px">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none"><path d="M4 12s1-4 6-4 6 4 6 4" stroke="#5b9cc4" stroke-width="1.4" stroke-linecap="round"/><path d="M10 4v4M7 5.5l1.5 2M13 5.5l-1.5 2" stroke="#5b9cc4" stroke-width="1.3" stroke-linecap="round"/></svg>
        </div>
        <div style="font-family:'Syne',sans-serif;font-size:13px;font-weight:700;color:var(--lblue);letter-spacing:1px;text-transform:uppercase;margin-bottom:10px" data-es="Creatividad con Propósito" data-en="Purpose-Driven Creativity">Creatividad con Propósito</div>
        <div style="font-size:14px;font-weight:400;color:var(--white);margin-bottom:8px;font-family:'Playfair Display',serif" data-es="Estética al servicio del resultado." data-en="Aesthetics in service of results.">Estética al servicio del resultado.</div>
        <div style="font-size:13px;color:rgba(255,255,255,.45);line-height:1.7;font-weight:300" data-es="El contenido no solo tiene que verse bien — tiene que comunicar, conectar y convertir. La creatividad es una herramienta estratégica, no un fin en sí mismo." data-en="Content doesn't just need to look good — it needs to communicate, connect and convert. Creativity is a strategic tool, not an end in itself.">El contenido no solo tiene que verse bien — tiene que comunicar, conectar y convertir. La creatividad es una herramienta estratégica, no un fin en sí mismo.</div>
      </div>

      <!-- Valor 6 -->
      <div class="valor-card gs-scale" style="background:var(--dark);padding:36px 30px;border:1px solid rgba(255,255,255,.06);transition:background .3s,transform .25s;cursor:default" onmouseenter="this.style.background='rgba(32,119,194,.08)'" onmouseleave="this.style.background='var(--dark)'">
        <div style="width:44px;height:44px;border-radius:10px;background:rgba(32,119,194,.12);display:flex;align-items:center;justify-content:center;margin-bottom:18px">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none"><circle cx="10" cy="10" r="7" stroke="#2077c2" stroke-width="1.4"/><path d="M7 10l2 2 4-4" stroke="#2077c2" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/></svg>
        </div>
        <div style="font-family:'Syne',sans-serif;font-size:13px;font-weight:700;color:var(--blue);letter-spacing:1px;text-transform:uppercase;margin-bottom:10px" data-es="Compromiso Real" data-en="Real Commitment">Compromiso Real</div>
        <div style="font-size:14px;font-weight:400;color:var(--white);margin-bottom:8px;font-family:'Playfair Display',serif" data-es="Tu marca, como si fuera la mía." data-en="Your brand, as if it were mine.">Tu marca, como si fuera la mía.</div>
        <div style="font-size:13px;color:rgba(255,255,255,.45);line-height:1.7;font-weight:300" data-es="Me involucro con el negocio del cliente, no solo con sus redes. Entender la industria, los clientes y los objetivos es lo que diferencia el trabajo bueno del trabajo extraordinario." data-en="I get involved with the client's business, not just their social media. Understanding the industry, customers and goals is what separates good work from extraordinary work.">Me involucro con el negocio del cliente, no solo con sus redes. Entender la industria, los clientes y los objetivos es lo que diferencia el trabajo bueno del trabajo extraordinario.</div>
      </div>

    </div>
  </section>

</div>

<!-- ══════════════════════════════════════
     PAGE: CONTACTO
══════════════════════════════════════ -->
<div class="page" id="page-contacto">
  <section class="cta-section">
    <div class="cta-circles">
      <div class="cta-cir" style="width:600px;height:600px;left:50%;top:-150px;transform:translateX(-50%)"></div>
      <div class="cta-cir" style="width:360px;height:360px;left:50%;top:-60px;transform:translateX(-50%);border-color:rgba(32,119,194,.08)"></div>
    </div>
    <div class="stripe" style="position:absolute;top:0;left:0;right:0;height:4px"><span class="s1"></span><span class="s2"></span><span class="s3"></span><span class="s4"></span><span class="s5"></span></div>
    <div style="position:relative;z-index:1">
      <div class="cta-eyebrow gs-up" data-es="¿Listo para crecer?" data-en="Ready to grow?">¿Listo para crecer?</div>
      <div class="cta-h gs-up"><span data-es="Agenda tu reunión" data-en="Schedule your meeting">Agenda tu reunión</span><br><em data-es="hoy mismo." data-en="today.">hoy mismo.</em></div>
      <p class="cta-sub gs-up" data-es="Da el primer paso. Cuéntame dónde está tu marca y te doy una recomendación honesta sin costo y sin compromiso." data-en="Take the first step. Tell me where your brand is and I'll give you an honest recommendation at no cost and no commitment.">Da el primer paso. Cuéntame dónde está tu marca y te doy una recomendación honesta sin costo y sin compromiso.</p>
      <div class="cta-contacts gs-up">
        <div class="cta-c"><div class="cc-dot" style="background:var(--blue)"></div><a href="mailto:hector_ort_m@outlook.com"><strong>hector_ort_m@outlook.com</strong></a></div>
        <div class="cta-c"><div class="cc-dot" style="background:var(--lblue)"></div><a href="https://wa.me/529934313735"><strong>993 431 3735</strong></a></div>
        <div class="cta-c"><div class="cc-dot" style="background:var(--lblue)"></div><a href="https://www.linkedin.com/in/hector-ortiz-849727259/" target="_blank" rel="noopener"><strong>LinkedIn</strong></a></div>
      </div>
      <div class="cta-btns gs-up">
        <a href="https://calendly.com" target="_blank" class="btn-meet"><span data-es="📅 Agendar reunión gratuita" data-en="📅 Schedule free meeting">📅 Agendar reunión gratuita</span></a>
        <a href="https://wa.me/529934313735" target="_blank" class="btn-wa"><span data-es="💬 WhatsApp" data-en="💬 WhatsApp">💬 WhatsApp</span></a>
        <a href="mailto:hector_ort_m@outlook.com" class="btn-wa"><span data-es="✉️ Correo electrónico" data-en="✉️ Email">✉️ Correo electrónico</span></a>
      </div>
      <div class="cta-tags gs-up">
        <span class="ctag" data-es="Redes Sociales" data-en="Social Media">Redes Sociales</span>
        <span class="ctag" data-es="Meta Ads" data-en="Meta Ads">Meta Ads</span>
        <span class="ctag" data-es="Estrategia de Marca" data-en="Brand Strategy">Estrategia de Marca</span>
        <span class="ctag" data-es="Auditorías" data-en="Audits">Auditorías</span>
        <span class="ctag" data-es="Diseño" data-en="Design">Diseño</span>
      </div>
    </div>
  </section>
</div>

<!-- ══ FOOTER (always visible) ══ -->
<footer>
  <div><div class="footer-logo">AO</div><div class="footer-sub">Alfonso Ortiz · Social Media Management</div></div>
  <ul class="footer-links">
    <li><a href="#" onclick="navigate('servicios');return false"><span data-es="Servicios" data-en="Services">Servicios</span></a></li>
    <li><a href="#" onclick="navigate('trabajo');return false"><span data-es="Trabajo" data-en="Work">Trabajo</span></a></li>
    <li><a href="#" onclick="navigate('planes');return false"><span data-es="Planes" data-en="Plans">Planes</span></a></li>
    <li><a href="#" onclick="navigate('contacto');return false"><span data-es="Contacto" data-en="Contact">Contacto</span></a></li>
  </ul>
  <a href="https://www.linkedin.com/in/hector-ortiz-849727259/" target="_blank" rel="noopener" class="linkedin-link">
    <svg viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
    LinkedIn
  </a>
  <div class="footer-legal">© 2026 Alfonso Ortiz. <span data-es="Todos los derechos reservados." data-en="All rights reserved.">Todos los derechos reservados.</span></div>
</footer>

<!-- ══ VIDEO MODAL ══ -->
<div class="modal" id="modal">
  <div class="modal-inner">
    <button class="modal-close" onclick="closeDriveModal()">✕</button>
    <iframe id="modal-iframe" src="" style="width:100%;aspect-ratio:9/16;max-height:88vh;border:none;border-radius:10px" allow="autoplay;fullscreen" allowfullscreen></iframe>
  </div>
</div>

<script>
/* ══ GSAP SETUP ══ */
gsap.registerPlugin(ScrollTrigger);



/* ══ PARTICLE CANVAS (hero) ══ */
function initCanvas(){
  const canvas=document.getElementById('hero-canvas');
  if(!canvas)return;
  const ctx=canvas.getContext('2d');
  let W,H,particles=[];
  function resize(){W=canvas.width=canvas.offsetWidth;H=canvas.height=canvas.offsetHeight}
  resize();
  window.addEventListener('resize',resize);
  const COLS=['#5b9cc4','#2077c2','#0f5f8a','#f02240','rgba(255,255,255,.3)'];
  for(let i=0;i<60;i++){
    particles.push({x:Math.random()*W,y:Math.random()*H,r:Math.random()*1.5+.5,vx:(Math.random()-.5)*.3,vy:(Math.random()-.5)*.3,c:COLS[Math.floor(Math.random()*COLS.length)]});
  }
  function draw(){
    ctx.clearRect(0,0,W,H);
    particles.forEach(p=>{
      ctx.beginPath();ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ctx.fillStyle=p.c;ctx.fill();
      p.x+=p.vx;p.y+=p.vy;
      if(p.x<0)p.x=W;if(p.x>W)p.x=0;
      if(p.y<0)p.y=H;if(p.y>H)p.y=0;
    });
    /* draw connections */
    for(let i=0;i<particles.length;i++){
      for(let j=i+1;j<particles.length;j++){
        const dx=particles[i].x-particles[j].x;
        const dy=particles[i].y-particles[j].y;
        const d=Math.sqrt(dx*dx+dy*dy);
        if(d<100){
          ctx.beginPath();
          ctx.moveTo(particles[i].x,particles[i].y);
          ctx.lineTo(particles[j].x,particles[j].y);
          ctx.strokeStyle=`rgba(91,156,196,${.12*(1-d/100)})`;
          ctx.lineWidth=.5;ctx.stroke();
        }
      }
    }
    requestAnimationFrame(draw);
  }
  draw();
}

/* ══ VIDEOS DATA ══ */
/* ══ YOUTUBE MODAL ══ */
function openYT(embedUrl){
  const modal=document.getElementById('modal');
  const inner=modal.querySelector('.modal-inner');
  inner.innerHTML=`
    <button class="modal-close" onclick="closeYT()" style="position:absolute;top:-40px;right:0;background:none;border:none;color:rgba(255,255,255,.8);font-size:28px;cursor:pointer;line-height:1">✕</button>
    <iframe src="${embedUrl}"
      style="width:min(90vw,460px);aspect-ratio:9/16;max-height:88vh;border:none;border-radius:12px;display:block"
      allow="autoplay;fullscreen;picture-in-picture"
      allowfullscreen>
    </iframe>
  `;
  modal.style.alignItems='center';
  modal.classList.add('open');
  document.body.style.overflow='hidden';
}
function closeYT(){
  const modal=document.getElementById('modal');
  const inner=modal.querySelector('.modal-inner');
  inner.innerHTML=`<button class="modal-close" onclick="closeYT()">✕</button>`;
  modal.classList.remove('open');
  document.body.style.overflow='';
}
function buildVideoGrid(){}
function initFileInput(){}
function initFileInput(){}

/* ══ LANGUAGE ══ */
let lang='es';
function setLang(l){
  lang=l;
  document.querySelectorAll('.lang-btn').forEach(b=>b.classList.toggle('active',b.textContent.toLowerCase()===l));
  document.querySelectorAll('[data-es]').forEach(el=>{
    el.textContent=el.dataset[l]||el.dataset.es;
  });
}

/* ══ NAV / PAGE ROUTING ══ */
let currentPage='inicio';
function navigate(page){
  /* hide all pages */
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-tab').forEach(t=>t.classList.toggle('active',t.dataset.page===page));
  const target=document.getElementById('page-'+page);
  if(target){
    target.classList.add('active');
    window.scrollTo({top:0,behavior:'smooth'});
    currentPage=page;
    /* trigger GSAP for new page */
    setTimeout(()=>{
      initPageAnimations(target);
      if(page==='inicio')initCanvas();
      if(page==='trabajo'){buildVideoGrid();setTimeout(initFileInput,100);}
      ScrollTrigger.refresh();
    },80);
  }
}

/* ══ NAV SCROLL ══ */
window.addEventListener('scroll',()=>{
  document.getElementById('main-nav').classList.toggle('scrolled',window.scrollY>30);
});

/* ══ MOBILE MENU ══ */
const mobBtn=document.getElementById('mob-btn');
const mobMenu=document.getElementById('mob-menu');
mobBtn.addEventListener('click',()=>{
  mobMenu.classList.toggle('open');
  const h=mobBtn.querySelectorAll('.ham');
  if(mobMenu.classList.contains('open')){
    h[0].style.transform='rotate(45deg) translate(5px,5px)';
    h[1].style.opacity='0';h[1].style.transform='scaleX(0)';
    h[2].style.transform='rotate(-45deg) translate(5px,-5px)';
  } else {
    h.forEach(x=>{x.style.transform='';x.style.opacity='';});
  }
});
function closeMob(){
  mobMenu.classList.remove('open');
  mobBtn.querySelectorAll('.ham').forEach(x=>{x.style.transform='';x.style.opacity='';});
}

/* ══ GSAP PAGE ANIMATIONS ══ */
function initPageAnimations(container){
  const els=container.querySelectorAll('.gs-up,.gs-left,.gs-right,.gs-scale,.gs-fade');
  els.forEach(el=>{
    const from={};
    if(el.classList.contains('gs-up')){from.opacity=0;from.y=44}
    else if(el.classList.contains('gs-left')){from.opacity=0;from.x=-40}
    else if(el.classList.contains('gs-right')){from.opacity=0;from.x=40}
    else if(el.classList.contains('gs-scale')){from.opacity=0;from.scale=.88}
    else{from.opacity=0}
    gsap.fromTo(el,from,{
      opacity:1,y:0,x:0,scale:1,
      duration:.8,
      ease:'power3.out',
      scrollTrigger:{trigger:el,start:'top 88%',toggleActions:'play none none none'},
    });
  });

  /* stagger grids */
  container.querySelectorAll('.svc-grid,.plans-grid,.design-cards,.audit-cards').forEach(grid=>{
    gsap.fromTo(grid.children,
      {opacity:0,y:36},
      {opacity:1,y:0,duration:.65,stagger:.1,ease:'power3.out',
        scrollTrigger:{trigger:grid,start:'top 82%'}
      }
    );
  });

  /* proc steps stagger */
  const proc=container.querySelector('.process-track');
  if(proc){
    gsap.fromTo(proc.children,
      {opacity:0,y:28},
      {opacity:1,y:0,duration:.6,stagger:.12,ease:'power2.out',
        scrollTrigger:{trigger:proc,start:'top 85%'}
      }
    );
  }

  /* bar width animate */
  container.querySelectorAll('.bar').forEach(bar=>{
    gsap.fromTo(bar,{width:0},{width:48,duration:1,ease:'power2.out',
      scrollTrigger:{trigger:bar,start:'top 90%'}
    });
  });

  /* hero cards cascade */
  const hCards=container.querySelectorAll('.hero-card');
  if(hCards.length){
    gsap.fromTo(hCards,
      {opacity:0,x:40},
      {opacity:1,x:0,duration:.7,stagger:.12,ease:'power3.out',delay:.3}
    );
  }

  /* parallax sections on scroll */
  container.querySelectorAll('.section').forEach(sec=>{
    gsap.fromTo(sec.querySelector('.sec-title, h2'),
      {backgroundPositionY:'0%'},
      {ease:'none',
        scrollTrigger:{trigger:sec,start:'top bottom',end:'bottom top',scrub:1}
      }
    );
  });

  /* valor cards stagger */
  const valGrid=container.querySelector('#valores-grid');
  if(valGrid){
    gsap.fromTo(valGrid.children,
      {opacity:0,y:40,scale:.93},
      {opacity:1,y:0,scale:1,duration:.7,stagger:.1,ease:'power3.out',
        scrollTrigger:{trigger:valGrid,start:'top 82%'}
      }
    );
  }

  /* svc tile hover color already in CSS, but add subtle rotate on enter */
  container.querySelectorAll('.hero-card').forEach(card=>{
    card.addEventListener('mouseenter',()=>{
      gsap.to(card,{x:-4,duration:.25,ease:'power2.out'});
    });
    card.addEventListener('mouseleave',()=>{
      gsap.to(card,{x:0,duration:.25,ease:'power2.out'});
    });
  });

  /* audit card tilt */
  container.querySelectorAll('.audit-card').forEach(card=>{
    card.addEventListener('mousemove',e=>{
      const r=card.getBoundingClientRect();
      const x=(e.clientX-r.left-r.width/2)/(r.width/2)*6;
      const y=(e.clientY-r.top-r.height/2)/(r.height/2)*-4;
      gsap.to(card,{rotateX:y,rotateY:x,duration:.3,ease:'power1.out',transformPerspective:600});
    });
    card.addEventListener('mouseleave',()=>{
      gsap.to(card,{rotateX:0,rotateY:0,duration:.4,ease:'power2.out'});
    });
  });

  /* plan card magnetic on mouse */
  container.querySelectorAll('.plan-card').forEach(card=>{
    card.addEventListener('mousemove',e=>{
      const r=card.getBoundingClientRect();
      const x=(e.clientX-r.left-r.width/2)/(r.width/2)*5;
      const y=(e.clientY-r.top-r.height/2)/(r.height/2)*-3;
      gsap.to(card,{rotateX:y,rotateY:x,y:-6,duration:.35,ease:'power1.out',transformPerspective:800});
    });
    card.addEventListener('mouseleave',()=>{
      gsap.to(card,{rotateX:0,rotateY:0,y:0,duration:.45,ease:'power2.out'});
    });
  });

  /* text chars split on section title (simple word stagger) */
  container.querySelectorAll('.sec-title,.cta-h').forEach(el=>{
    const words=el.textContent.split(' ');
    if(words.length<12&&el.dataset.split!=='done'){
      el.dataset.split='done';
      const html=words.map(w=>`<span style="display:inline-block">${w}&nbsp;</span>`).join('');
      el.innerHTML=html;
      gsap.fromTo(el.children,
        {opacity:0,y:30},
        {opacity:1,y:0,duration:.65,stagger:.08,ease:'power3.out',
          scrollTrigger:{trigger:el,start:'top 88%'}
        }
      );
    }
  });
}

/* ══ INIT ══ */
initPageAnimations(document.getElementById('page-inicio'));
initCanvas();
</script>
</body>
</html>

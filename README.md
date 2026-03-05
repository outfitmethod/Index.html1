<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Outfit Method</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400&family=Jost:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --cream: #f5f0e8;
    --warm-white: #faf8f4;
    --ink: #1a1a18;
    --mid: #6b6660;
    --light: #c8bfb0;
    --accent: #2c2c2a;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--warm-white);
    color: var(--ink);
    font-family: 'Jost', sans-serif;
    font-weight: 300;
    font-size: 16px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 24px 48px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(250, 248, 244, 0.92);
    backdrop-filter: blur(8px);
    border-bottom: 1px solid rgba(200, 191, 176, 0.3);
  }

  .nav-logo {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 400;
    font-size: 1.2rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--ink);
    text-decoration: none;
  }

  .nav-links {
    display: flex;
    gap: 36px;
    list-style: none;
  }

  .nav-links a {
    font-size: 0.75rem;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--mid);
    text-decoration: none;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--ink); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 120px 48px 80px;
    position: relative;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: -20%;
    right: -10%;
    width: 600px;
    height: 600px;
    background: radial-gradient(circle, rgba(200,191,176,0.2) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-inner {
    max-width: 1100px;
    margin: 0 auto;
    width: 100%;
  }

  .hero-eyebrow {
    font-size: 0.7rem;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: var(--mid);
    margin-bottom: 32px;
    opacity: 0;
    animation: fadeUp 0.8s 0.2s forwards;
  }

  .hero-headline {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(3.2rem, 7vw, 6.5rem);
    line-height: 1.05;
    letter-spacing: -0.01em;
    color: var(--ink);
    margin-bottom: 40px;
    opacity: 0;
    animation: fadeUp 0.8s 0.4s forwards;
  }

  .hero-headline em {
    font-style: italic;
    color: var(--mid);
  }

  .hero-sub {
    max-width: 480px;
    font-size: 1rem;
    color: var(--mid);
    line-height: 1.8;
    margin-bottom: 52px;
    opacity: 0;
    animation: fadeUp 0.8s 0.6s forwards;
  }

  .hero-cta {
    display: inline-block;
    padding: 14px 36px;
    border: 1px solid var(--ink);
    font-family: 'Jost', sans-serif;
    font-size: 0.72rem;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--ink);
    text-decoration: none;
    transition: all 0.25s;
    opacity: 0;
    animation: fadeUp 0.8s 0.8s forwards;
  }

  .hero-cta:hover {
    background: var(--ink);
    color: var(--warm-white);
  }

  .hero-rule {
    position: absolute;
    bottom: 48px;
    left: 48px;
    right: 48px;
    height: 1px;
    background: var(--light);
    opacity: 0;
    animation: fadeIn 1s 1.2s forwards;
  }

  /* SECTION BASE */
  section {
    padding: 100px 48px;
  }

  .section-inner {
    max-width: 1100px;
    margin: 0 auto;
  }

  .section-label {
    font-size: 0.68rem;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: var(--light);
    margin-bottom: 48px;
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .section-label::after {
    content: '';
    display: block;
    height: 1px;
    width: 48px;
    background: var(--light);
  }

  /* PROBLEM */
  .problem {
    background: var(--cream);
  }

  .problem-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: start;
  }

  .problem-headline {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(2rem, 3.5vw, 3rem);
    line-height: 1.2;
    color: var(--ink);
  }

  .problem-headline em {
    font-style: italic;
    color: var(--mid);
  }

  .problem-body {
    color: var(--mid);
    font-size: 0.95rem;
    line-height: 1.9;
  }

  .problem-body p + p {
    margin-top: 20px;
  }

  /* SERVICES */
  .services-headline {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(2rem, 3.5vw, 2.8rem);
    color: var(--ink);
    margin-bottom: 64px;
    max-width: 500px;
    line-height: 1.2;
  }

  .services-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    background: var(--light);
  }

  .service-card {
    background: var(--warm-white);
    padding: 56px 48px;
    position: relative;
    transition: background 0.3s;
  }

  .service-card:hover {
    background: var(--cream);
  }

  .service-number {
    font-family: 'Cormorant Garamond', serif;
    font-size: 0.85rem;
    color: var(--light);
    margin-bottom: 28px;
    letter-spacing: 0.1em;
  }

  .service-name {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 400;
    font-size: 1.7rem;
    color: var(--ink);
    margin-bottom: 16px;
    line-height: 1.2;
  }

  .service-desc {
    font-size: 0.88rem;
    color: var(--mid);
    line-height: 1.8;
    margin-bottom: 32px;
  }

  .service-includes {
    list-style: none;
    margin-bottom: 40px;
  }

  .service-includes li {
    font-size: 0.82rem;
    color: var(--mid);
    padding: 8px 0;
    border-bottom: 1px solid rgba(200,191,176,0.4);
    letter-spacing: 0.02em;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .service-includes li::before {
    content: '—';
    color: var(--light);
    font-size: 0.75rem;
  }

  .service-price {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2rem;
    font-weight: 300;
    color: var(--ink);
  }

  .service-price span {
    font-family: 'Jost', sans-serif;
    font-size: 0.72rem;
    color: var(--mid);
    letter-spacing: 0.1em;
    margin-left: 4px;
    vertical-align: middle;
  }

  /* TESTIMONIAL */
  .testimonial {
    background: var(--ink);
    padding: 100px 48px;
  }

  .testimonial .section-label {
    color: rgba(200,191,176,0.4);
  }

  .testimonial .section-label::after {
    background: rgba(200,191,176,0.4);
  }

  .testimonial-quote {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-weight: 300;
    font-size: clamp(1.6rem, 3vw, 2.4rem);
    color: var(--cream);
    line-height: 1.4;
    max-width: 780px;
    margin-bottom: 40px;
  }

  .testimonial-attr {
    font-size: 0.75rem;
    letter-spacing: 0.16em;
    text-transform: uppercase;
    color: var(--light);
  }

  /* HOW IT WORKS */
  .process {
    background: var(--cream);
  }

  .process-headline {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(2rem, 3.5vw, 2.8rem);
    color: var(--ink);
    margin-bottom: 64px;
    line-height: 1.2;
  }

  .process-steps {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2px;
    background: var(--light);
  }

  .process-step {
    background: var(--cream);
    padding: 40px 36px;
  }

  .step-num {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2.5rem;
    font-weight: 300;
    color: var(--light);
    line-height: 1;
    margin-bottom: 20px;
  }

  .step-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.1rem;
    font-weight: 400;
    color: var(--ink);
    margin-bottom: 12px;
  }

  .step-desc {
    font-size: 0.82rem;
    color: var(--mid);
    line-height: 1.8;
  }

  /* ABOUT */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 80px;
    align-items: start;
  }

  .about-label-col {
    padding-top: 8px;
  }

  .about-headline {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(2rem, 3vw, 2.6rem);
    color: var(--ink);
    margin-bottom: 28px;
    line-height: 1.2;
  }

  .about-body {
    font-size: 0.95rem;
    color: var(--mid);
    line-height: 1.9;
  }

  .about-body p + p {
    margin-top: 20px;
  }

  /* CONTACT */
  .contact {
    background: var(--ink);
    padding: 100px 48px;
  }

  .contact .section-label {
    color: rgba(200,191,176,0.4);
  }

  .contact .section-label::after {
    background: rgba(200,191,176,0.4);
  }

  .contact-inner {
    max-width: 1100px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: start;
  }

  .contact-headline {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(2rem, 3.5vw, 3rem);
    color: var(--cream);
    line-height: 1.15;
    margin-bottom: 24px;
  }

  .contact-sub {
    font-size: 0.88rem;
    color: var(--light);
    line-height: 1.8;
    margin-bottom: 40px;
  }

  .contact-email-link {
    display: inline-block;
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.3rem;
    font-style: italic;
    color: var(--cream);
    text-decoration: none;
    border-bottom: 1px solid rgba(200,191,176,0.4);
    padding-bottom: 4px;
    transition: border-color 0.2s;
  }

  .contact-email-link:hover {
    border-color: var(--cream);
  }

  .contact-details {
    padding-top: 8px;
  }

  .contact-item {
    padding: 24px 0;
    border-bottom: 1px solid rgba(200,191,176,0.15);
  }

  .contact-item-label {
    font-size: 0.68rem;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: rgba(200,191,176,0.5);
    margin-bottom: 8px;
  }

  .contact-item-value {
    font-size: 0.9rem;
    color: var(--light);
    line-height: 1.6;
  }

  /* FOOTER */
  footer {
    padding: 32px 48px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-top: 1px solid rgba(200,191,176,0.2);
    background: var(--ink);
  }

  .footer-logo {
    font-family: 'Cormorant Garamond', serif;
    font-size: 0.95rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: rgba(200,191,176,0.5);
    text-decoration: none;
  }

  .footer-links {
    display: flex;
    gap: 28px;
    list-style: none;
  }

  .footer-links a {
    font-size: 0.72rem;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: rgba(200,191,176,0.4);
    text-decoration: none;
    transition: color 0.2s;
  }

  .footer-links a:hover {
    color: var(--light);
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  /* RESPONSIVE */
  @media (max-width: 768px) {
    nav { padding: 20px 24px; }
    .nav-links { display: none; }
    section { padding: 72px 24px; }
    .hero { padding: 100px 24px 72px; }
    .problem-grid,
    .services-grid,
    .about-grid,
    .contact-inner { grid-template-columns: 1fr; gap: 40px; }
    .process-steps { grid-template-columns: 1fr 1fr; }
    .hero-rule { left: 24px; right: 24px; }
    footer { padding: 24px; flex-direction: column; gap: 16px; text-align: center; }
    .testimonial, .contact { padding: 72px 24px; }
  }

  @media (max-width: 480px) {
    .process-steps { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">Outfit Method</a>
  <ul class="nav-links">
    <li><a href="#services">Services</a></li>
    <li><a href="#process">How it works</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Enquire</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="top">
  <div class="hero-inner">
    <p class="hero-eyebrow">Personal Styling · Virtual · By Appointment</p>
    <h1 class="hero-headline">
      A considered<br>approach to<br><em>dressing well.</em>
    </h1>
    <p class="hero-sub">Outfit Method is a personal styling service built around outfits — not individual pieces. For people who want to dress better without starting over.</p>
    <a href="#contact" class="hero-cta">Start an enquiry</a>
  </div>
  <div class="hero-rule"></div>
</section>

<!-- PROBLEM -->
<section class="problem" id="about-problem">
  <div class="section-inner">
    <p class="section-label">The problem</p>
    <div class="problem-grid">
      <h2 class="problem-headline">Most people don't need <em>more</em> clothes.</h2>
      <div class="problem-body">
        <p>They already own enough. The problem is that very little of it works together. Buying individual items without a clear sense of how they'll be worn leads to wasted money, decision fatigue, and a wardrobe that never quite feels resolved.</p>
        <p>Outfit Method exists to fix that. Rather than focusing on pieces in isolation, everything starts with the outfit — because that's what actually gets worn.</p>
      </div>
    </div>
  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <div class="section-inner">
    <p class="section-label">Services</p>
    <h2 class="services-headline">Two ways to work together.</h2>
    <div class="services-grid">

      <!-- Service 1 -->
      <div class="service-card">
        <p class="service-number">01</p>
        <h3 class="service-name">Personal Outfit Plan</h3>
        <p class="service-desc">A clear, practical plan for everyday dressing. Built around what you already own, with considered additions where needed.</p>
        <ul class="service-includes">
          <li>Style questionnaire</li>
          <li>8–10 complete outfits</li>
          <li>Buying links for additions</li>
          <li>Notes on why each outfit works</li>
          <li>Delivered within 5 working days</li>
        </ul>
        <div class="service-price">£60 <span>one-off</span></div>
      </div>

      <!-- Service 2 -->
      <div class="service-card">
        <p class="service-number">02</p>
        <h3 class="service-name">Capsule Wardrobe Build</h3>
        <p class="service-desc">A considered wardrobe built around outfits, not excess. For those who want to simplify while improving how everything works together.</p>
        <ul class="service-includes">
          <li>Lifestyle and budget intake</li>
          <li>20–25 mix-and-match pieces</li>
          <li>Seasonal focus</li>
          <li>Clear buying guidance</li>
          <li>Delivered within 7 working days</li>
        </ul>
        <div class="service-price">£120 <span>one-off</span></div>
      </div>

    </div>
  </div>
</section>

<!-- TESTIMONIAL -->
<section class="testimonial">
  <div class="section-inner">
    <p class="section-label" style="color:rgba(200,191,176,0.4);">Client feedback</p>
    <blockquote class="testimonial-quote">
      "I had lots of clothes, but I wasn't making the most out of them, and didn't feel like my outfits were polished or well put together."
    </blockquote>
    <p class="testimonial-attr" style="margin-bottom: 64px;">Corey — Personal Outfit Plan</p>

    <blockquote class="testimonial-quote" style="font-size: clamp(1.2rem, 2.2vw, 1.7rem);">
      "The whole process was smooth and I will be paying attention to the detail and following the guidelines in the future."
    </blockquote>
    <p class="testimonial-attr">Manuel — Personal Outfit Plan</p>
  </div>
</section>

<!-- PROCESS -->
<section class="process" id="process">
  <div class="section-inner">
    <p class="section-label">How it works</p>
    <h2 class="process-headline">Simple from start to finish.</h2>
    <div class="process-steps">
      <div class="process-step">
        <div class="step-num">01</div>
        <h3 class="step-title">Get in touch</h3>
        <p class="step-desc">Send an email to begin. No lengthy forms — just a brief message is enough to start.</p>
      </div>
      <div class="process-step">
        <div class="step-num">02</div>
        <h3 class="step-title">Questionnaire</h3>
        <p class="step-desc">I'll send a short questionnaire covering your lifestyle, wardrobe, and what you're looking for.</p>
      </div>
      <div class="process-step">
        <div class="step-num">03</div>
        <h3 class="step-title">Payment & slot</h3>
        <p class="step-desc">Once you're happy to proceed, payment secures your place and work begins.</p>
      </div>
      <div class="process-step">
        <div class="step-num">04</div>
        <h3 class="step-title">Delivery</h3>
        <p class="step-desc">Your plan is delivered by email — clear, practical, and ready to use immediately.</p>
      </div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="section-inner">
    <p class="section-label">About</p>
    <div class="about-grid">
      <div class="about-label-col">
        <h2 class="about-headline">Built around outfits.<br><em>Not excess.</em></h2>
      </div>
      <div>
        <div class="about-body">
          <p>Outfit Method is built around the idea that dressing well should feel repeatable, not effortful. The aim isn't perfection — it's confidence, consistency, and clarity.</p>
          <p>I don't push products or recommend things for the sake of it. Everything is chosen because it earns its place in an outfit. My focus is helping you understand what works, what doesn't, and why — so you can make better decisions long term.</p>
          <p>All services are delivered virtually. A limited number of clients are taken on at any one time.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="contact" id="contact">
  <div class="contact-inner">
    <div>
      <p class="section-label" style="color:rgba(200,191,176,0.4);">Enquiries</p>
      <h2 class="contact-headline">Ready to get started?</h2>
      <p class="contact-sub">Send an email and I'll come back to you within 48 hours with next steps and the questionnaire.</p>
      <a href="/cdn-cgi/l/email-protection#47283233212e332a22332f282307202a262e2b6924282a" class="contact-email-link"><span class="__cf_email__" data-cfemail="620d1716040b160f07160a0d0622050f030b0e4c010d0f">[email&#160;protected]</span></a>
    </div>
    <div class="contact-details">
      <div class="contact-item">
        <p class="contact-item-label">Response time</p>
        <p class="contact-item-value">Within 48 hours</p>
      </div>
      <div class="contact-item">
        <p class="contact-item-label">Delivery</p>
        <p class="contact-item-value">All services delivered virtually by email</p>
      </div>
      <div class="contact-item">
        <p class="contact-item-label">Availability</p>
        <p class="contact-item-value">Limited client spaces taken at any one time</p>
      </div>
      <div class="contact-item">
        <p class="contact-item-label">Instagram</p>
        <p class="contact-item-value"><a href="https://www.instagram.com/outfitmethod" target="_blank" style="color:var(--light);text-decoration:none;">@outfitmethod</a></p>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <a href="#top" class="footer-logo">Outfit Method</a>
  <ul class="footer-links">
    <li><a href="#services">Services</a></li>
# kino-vakars
<!DOCTYPE html>
<html lang="lv">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Brīvdabas Kino Vakars</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=Libre+Baskerville:ital@0;1&family=Oswald:wght@300;400;600&display=swap" rel="stylesheet">
<style>
  :root {
    --midnight: #080c14;
    --deep-blue: #0d1a2e;
    --navy: #112240;
    --gold: #d4a843;
    --amber: #e8c36a;
    --cream: #f5ead6;
    --warm-white: #fdf8ef;
    --red: #c0392b;
    --silver: #a8b8c8;
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--midnight);
    color: var(--cream);
    font-family: 'Libre Baskerville', Georgia, serif;
    overflow-x: hidden;
  }
  .stars-layer {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    z-index: 0;
  }
  .star {
    position: absolute;
    background: #fff;
    border-radius: 50%;
    animation: twinkle var(--dur, 3s) ease-in-out infinite;
    animation-delay: var(--delay, 0s);
  }
  @keyframes twinkle {
    0%, 100% { opacity: 0.2; transform: scale(1); }
    50% { opacity: 1; transform: scale(1.4); }
  }
  nav {
    position: fixed;
    top: 0; width: 100%;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1.2rem 4rem;
    background: linear-gradient(to bottom, rgba(8,12,20,0.95), transparent);
    backdrop-filter: blur(4px);
  }
  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.1rem;
    font-style: italic;
    color: var(--gold);
    letter-spacing: 0.05em;
  }
  .nav-links { display: flex; gap: 2.5rem; list-style: none; }
  .nav-links a {
    font-family: 'Oswald', sans-serif;
    font-weight: 300;
    font-size: 0.8rem;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--silver);
    text-decoration: none;
    transition: color 0.3s;
  }
  .nav-links a:hover { color: var(--gold); }
  #sakums {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 2rem;
    overflow: hidden;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 80%, rgba(212,168,67,0.08) 0%, transparent 70%),
      radial-gradient(ellipse 100% 50% at 50% 110%, rgba(13,26,46,0.9) 0%, transparent 60%),
      linear-gradient(175deg, #040810 0%, #0d1a2e 50%, #080c14 100%);
    z-index: 1;
  }
  .filmstrip {
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 60px;
    display: flex;
    align-items: center;
    z-index: 2;
    opacity: 0.25;
  }
  .filmstrip-inner {
    display: flex;
    gap: 4px;
    padding: 8px 0;
    border-top: 6px solid var(--gold);
    border-bottom: 6px solid var(--gold);
    width: 100%;
  }
  .film-hole {
    min-width: 28px; height: 22px;
    border-radius: 4px;
    background: var(--midnight);
    border: 2px solid var(--gold);
  }
  .hero-content { position: relative; z-index: 3; }
  .hero-eyebrow {
    font-family: 'Oswald', sans-serif;
    font-weight: 300;
    font-size: 0.75rem;
    letter-spacing: 0.4em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1.5rem;
    animation: fadeUp 1s ease both;
  }
  .hero-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(3.5rem, 10vw, 8rem);
    font-weight: 900;
    line-height: 0.9;
    color: var(--warm-white);
    animation: fadeUp 1s 0.2s ease both;
  }
  .hero-title em {
    display: block;
    font-style: italic;
    color: var(--gold);
  }
  .hero-subtitle {
    font-family: 'Libre Baskerville', serif;
    font-style: italic;
    font-size: 1.1rem;
    color: var(--silver);
    margin-top: 1.5rem;
    animation: fadeUp 1s 0.4s ease both;
  }
  .hero-date {
    margin-top: 2.5rem;
    font-family: 'Oswald', sans-serif;
    font-weight: 600;
    font-size: 1.3rem;
    letter-spacing: 0.15em;
    color: var(--amber);
    animation: fadeUp 1s 0.6s ease both;
  }
  .btn-primary {
    display: inline-block;
    margin-top: 2.5rem;
    padding: 1rem 3rem;
    background: var(--gold);
    color: var(--midnight);
    font-family: 'Oswald', sans-serif;
    font-weight: 600;
    font-size: 0.85rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    text-decoration: none;
    border: none;
    cursor: pointer;
    transition: background 0.3s, transform 0.2s;
    animation: fadeUp 1s 0.8s ease both;
  }
  .btn-primary:hover { background: var(--amber); transform: translateY(-2px); }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }
  section { position: relative; z-index: 2; }
  .section-inner {
    max-width: 1100px;
    margin: 0 auto;
    padding: 6rem 2rem;
  }
  .section-label {
    font-family: 'Oswald', sans-serif;
    font-weight: 300;
    font-size: 0.72rem;
    letter-spacing: 0.35em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1rem;
  }
  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 5vw, 3.5rem);
    font-weight: 700;
    line-height: 1.1;
    color: var(--warm-white);
    margin-bottom: 2rem;
  }
  .divider {
    width: 60px; height: 2px;
    background: var(--gold);
    margin: 1.5rem 0 2.5rem;
  }
  #par { background: linear-gradient(180deg, var(--midnight) 0%, var(--deep-blue) 100%); }
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5rem;
    align-items: center;
  }
  .about-text p {
    font-size: 1rem;
    line-height: 1.9;
    color: var(--silver);
    margin-bottom: 1.2rem;
  }
  .about-screen {
    position: relative;
    aspect-ratio: 16/10;
    background: var(--navy);
    border: 3px solid rgba(212,168,67,0.3);
    display: flex; align-items: center; justify-content: center;
    overflow: hidden;
  }
  .screen-glow {
    width: 70%; height: 60%;
    background: radial-gradient(ellipse, rgba(212,168,67,0.15), transparent 70%);
    animation: pulse 3s ease-in-out infinite;
  }
  .screen-icon { font-size: 4rem; position: absolute; }
  @keyframes pulse { 0%,100%{opacity:0.5;} 50%{opacity:1;} }
  .about-screen::before {
    content: '';
    position: absolute; bottom: -2px; left: 0; right: 0;
    height: 4px;
    background: var(--gold);
    opacity: 0.5;
  }
  #programma { background: var(--midnight); }
  .program-card {
    background: linear-gradient(135deg, rgba(17,34,64,0.8), rgba(8,12,20,0.9));
    border: 1px solid rgba(212,168,67,0.2);
    padding: 2.5rem;
    margin-bottom: 1.5rem;
    display: grid;
    grid-template-columns: 80px 1fr auto;
    gap: 2rem;
    align-items: center;
    transition: border-color 0.3s, transform 0.3s;
  }
  .program-card:hover { border-color: var(--gold); transform: translateX(6px); }
  .prog-time {
    font-family: 'Oswald', sans-serif;
    font-size: 1.4rem;
    font-weight: 600;
    color: var(--gold);
    text-align: center;
  }
  .prog-time span { display: block; font-size: 0.65rem; font-weight: 300; letter-spacing: 0.2em; color: var(--silver); margin-top: 0.2rem; }
  .prog-info h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    color: var(--warm-white);
    margin-bottom: 0.4rem;
  }
  .prog-info p { font-size: 0.88rem; color: var(--silver); line-height: 1.6; }
  .prog-badge {
    font-family: 'Oswald', sans-serif;
    font-size: 0.7rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    padding: 0.4rem 1rem;
    border: 1px solid var(--gold);
    color: var(--gold);
    white-space: nowrap;
  }
  #filma { background: linear-gradient(180deg, var(--midnight), var(--deep-blue)); }
  .movie-feature {
    display: grid;
    grid-template-columns: 1fr 1.4fr;
    gap: 4rem;
    align-items: start;
  }
  .movie-poster {
    aspect-ratio: 2/3;
    background: linear-gradient(160deg, #1a2a4a, #0d1a2e);
    border: 2px solid rgba(212,168,67,0.3);
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    gap: 1rem;
    font-size: 5rem;
    position: relative;
    overflow: hidden;
  }
  .movie-poster::after {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(to top, rgba(212,168,67,0.1), transparent);
  }
  .movie-poster-title {
    font-family: 'Playfair Display', serif;
    font-size: 1rem;
    font-style: italic;
    color: var(--gold);
    text-align: center;
    padding: 0 1rem;
    position: relative; z-index: 1;
  }
  .movie-meta { display: flex; gap: 1rem; flex-wrap: wrap; margin-bottom: 1.5rem; }
  .meta-tag {
    font-family: 'Oswald', sans-serif;
    font-size: 0.72rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    padding: 0.35rem 0.9rem;
    background: rgba(212,168,67,0.12);
    color: var(--gold);
    border: 1px solid rgba(212,168,67,0.3);
  }
  .movie-desc p { font-size: 1rem; line-height: 1.85; color: var(--silver); margin-bottom: 1rem; }
  .rating {
    display: inline-flex; align-items: center; gap: 0.5rem;
    font-family: 'Oswald', sans-serif;
    font-size: 1.5rem;
    color: var(--gold);
    margin-top: 1rem;
  }
  .stars-rating { font-size: 1.2rem; letter-spacing: 0.1em; }
  #vieta { background: var(--midnight); }
  .location-grid { display: grid; grid-template-columns: 1.2fr 1fr; gap: 4rem; align-items: start; }
  .map-placeholder {
    aspect-ratio: 4/3;
    background: linear-gradient(135deg, var(--navy), var(--deep-blue));
    border: 2px solid rgba(212,168,67,0.25);
    display: flex; align-items: center; justify-content: center;
    flex-direction: column; gap: 1rem;
    font-size: 3rem;
    color: var(--gold);
    opacity: 0.8;
  }
  .map-placeholder p {
    font-family: 'Oswald', sans-serif;
    font-size: 0.75rem;
    letter-spacing: 0.2em;
    color: var(--silver);
  }
  .location-item {
    display: flex; gap: 1.5rem;
    padding: 1.5rem 0;
    border-bottom: 1px solid rgba(212,168,67,0.1);
    align-items: flex-start;
  }
  .loc-icon { font-size: 1.5rem; min-width: 2rem; margin-top: 0.1rem; }
  .loc-label {
    font-family: 'Oswald', sans-serif;
    font-size: 0.72rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.3rem;
  }
  .loc-value { font-size: 0.95rem; color: var(--cream); line-height: 1.6; }
  #registracija { background: linear-gradient(180deg, var(--deep-blue), var(--midnight)); }
  .reg-center { text-align: center; max-width: 600px; margin: 0 auto; }
  .reg-center .divider { margin: 1.5rem auto 2.5rem; }
  .reg-form { margin-top: 2.5rem; }
  .form-group { margin-bottom: 1.2rem; text-align: left; }
  .form-group label {
    display: block;
    font-family: 'Oswald', sans-serif;
    font-size: 0.72rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.5rem;
  }
  .form-group input,
  .form-group select {
    width: 100%;
    padding: 0.9rem 1.2rem;
    background: rgba(17,34,64,0.8);
    border: 1px solid rgba(212,168,67,0.3);
    color: var(--cream);
    font-family: 'Libre Baskerville', serif;
    font-size: 0.9rem;
    outline: none;
    transition: border-color 0.3s;
  }
  .form-group input:focus,
  .form-group select:focus { border-color: var(--gold); }
  .form-group select option { background: var(--deep-blue); }
  .counter-display {
    display: flex; align-items: center; justify-content: center;
    gap: 2rem; margin: 2rem 0;
  }
  .counter-btn {
    width: 48px; height: 48px;
    background: transparent;
    border: 2px solid var(--gold);
    color: var(--gold);
    font-size: 1.5rem;
    cursor: pointer;
    transition: all 0.2s;
    font-family: 'Oswald', sans-serif;
  }
  .counter-btn:hover { background: var(--gold); color: var(--midnight); }
  .counter-num {
    font-family: 'Playfair Display', serif;
    font-size: 3rem;
    font-weight: 700;
    color: var(--warm-white);
  }
  .counter-label {
    font-family: 'Oswald', sans-serif;
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    color: var(--silver);
    text-transform: uppercase;
  }
  .success-msg {
    display: none;
    padding: 1.5rem;
    background: rgba(212,168,67,0.1);
    border: 1px solid var(--gold);
    color: var(--amber);
    font-family: 'Oswald', sans-serif;
    letter-spacing: 0.1em;
    margin-top: 1.5rem;
  }
  #jautajumi { background: var(--midnight); }
  .faq-item { border-bottom: 1px solid rgba(212,168,67,0.15); }
  .faq-q {
    width: 100%;
    background: none;
    border: none;
    text-align: left;
    padding: 1.5rem 0;
    display: flex; justify-content: space-between; align-items: center;
    cursor: pointer;
    color: var(--cream);
    font-family: 'Playfair Display', serif;
    font-size: 1.05rem;
    gap: 1rem;
  }
  .faq-arrow {
    color: var(--gold);
    font-size: 1.2rem;
    transition: transform 0.3s;
    min-width: 1rem;
  }
  .faq-item.open .faq-arrow { transform: rotate(90deg); }
  .faq-a {
    max-height: 0; overflow: hidden;
    transition: max-height 0.4s ease, padding 0.3s;
    font-size: 0.95rem; line-height: 1.8; color: var(--silver);
    padding-bottom: 0;
  }
  .faq-item.open .faq-a { max-height: 300px; padding-bottom: 1.5rem; }
  #kontakti { background: linear-gradient(180deg, var(--deep-blue), var(--midnight)); }
  .contact-grid { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 2rem; }
  .contact-card {
    background: rgba(17,34,64,0.6);
    border: 1px solid rgba(212,168,67,0.15);
    padding: 2.5rem 2rem;
    text-align: center;
    transition: border-color 0.3s, transform 0.3s;
  }
  .contact-card:hover { border-color: var(--gold); transform: translateY(-4px); }
  .contact-icon { font-size: 2.5rem; margin-bottom: 1rem; }
  .contact-card h3 {
    font-family: 'Oswald', sans-serif;
    font-size: 0.75rem;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.6rem;
  }
  .contact-card p { font-size: 0.95rem; color: var(--silver); line-height: 1.6; }
  .contact-card a { color: var(--amber); text-decoration: none; }
  #autors { background: var(--midnight); }
  .author-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; }
  .author-card {
    padding: 3rem;
    background: rgba(13,26,46,0.6);
    border-left: 3px solid var(--gold);
  }
  .author-card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    color: var(--warm-white);
    margin-bottom: 0.3rem;
  }
  .author-role {
    font-family: 'Oswald', sans-serif;
    font-size: 0.72rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1.2rem;
  }
  .author-card p { font-size: 0.92rem; line-height: 1.8; color: var(--silver); }
  .policy-box {
    padding: 2.5rem 3rem;
    background: rgba(17,34,64,0.5);
    border: 1px solid rgba(212,168,67,0.2);
  }
  .policy-box h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    color: var(--warm-white);
    margin-bottom: 1rem;
  }
  .policy-box p { font-size: 0.88rem; line-height: 1.85; color: var(--silver); margin-bottom: 0.8rem; }
  footer {
    background: #040608;
    padding: 2.5rem 4rem;
    display: flex; justify-content: space-between; align-items: center;
    border-top: 1px solid rgba(212,168,67,0.15);
    position: relative; z-index: 2;
  }
  .footer-logo {
    font-family: 'Playfair Display', serif;
    font-style: italic;
    font-size: 1.1rem;
    color: var(--gold);
  }
  footer p { font-size: 0.8rem; color: rgba(168,184,200,0.5); font-family: 'Oswald', sans-serif; font-weight: 300; letter-spacing: 0.1em; }
  .reveal { opacity: 0; transform: translateY(40px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .reveal.visible { opacity: 1; transform: none; }
  @media (max-width: 768px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { gap: 1.2rem; }
    .about-grid, .movie-feature, .location-grid, .author-grid, .contact-grid { grid-template-columns: 1fr; gap: 2.5rem; }
    .program-card { grid-template-columns: 60px 1fr; }
    .prog-badge { display: none; }
    footer { flex-direction: column; gap: 1rem; text-align: center; }
    .section-inner { padding: 4rem 1.5rem; }
  }
</style>
</head>
<body>

<div class="stars-layer" id="stars"></div>

<nav>
  <div class="nav-logo">✦ Kino Vakars</div>
  <ul class="nav-links">
    <li><a href="#sakums">Sākums</a></li>
    <li><a href="#par">Par</a></li>
    <li><a href="#programma">Programma</a></li>
    <li><a href="#filma">Filma</a></li>
    <li><a href="#vieta">Vieta</a></li>
    <li><a href="#registracija">Reģistrācija</a></li>
    <li><a href="#kontakti">Kontakti</a></li>
  </ul>
</nav>

<section id="sakums">
  <div class="hero-bg"></div>
  <div class="hero-content">
    <div class="hero-eyebrow">Jēkabpils • Vasaras pasākums 2025</div>
    <h1 class="hero-title">
      Brīvdabas<br>
      <em>Kino Vakars</em>
    </h1>
    <p class="hero-subtitle">Filmas zem atvērtām debesīm — kopā ar draugiem</p>
    <div class="hero-date">🎬 &nbsp;Jūnijs 2025 &nbsp;·&nbsp; 21:00 &nbsp;·&nbsp; Pilsētas parks</div>
    <a href="#registracija" class="btn-primary">Pieteikties tagad</a>
  </div>
  <div class="filmstrip">
    <div class="filmstrip-inner" id="filmstrip"></div>
  </div>
</section>

<section id="par">
  <div class="section-inner">
    <div class="about-grid reveal">
      <div class="about-text">
        <div class="section-label">Par pasākumu</div>
        <h2 class="section-title">Maģiska nakts zem zvaigžņotajām debesīm</h2>
        <div class="divider"></div>
        <p>Ielūdzam visu klasi uz neaizmirstamu brīvdabas kino vakaru Jēkabpils pilsētas parkā! Lielais ekrāns, svaigs gaiss un vislabākā kompānija — tas ir viss, kas nepieciešams perfektai vasaras naktij.</p>
        <p>Pasākums sāksies pirms saulrieta ar muzikālu priekšprogrammu, bet galvenais notikums — filmas seanss — iesāksies tieši tumsas iestāšanās brīdī. Katrs apmeklētājs var atnest segu un spilvenu, lai baudītu vakaru pēc iespējas ērtāk.</p>
        <p>Klātbūtnē būs pieejams uzkodu un dzērienu pārdošanas stūrītis — popkorns, karstā šokolāde un citi gardumi.</p>
      </div>
      <div class="about-screen">
        <div class="screen-glow"></div>
        <span class="screen-icon">🎥</span>
      </div>
    </div>
  </div>
</section>

<section id="programma">
  <div class="section-inner">
    <div class="reveal">
      <div class="section-label">Vakara gaita</div>
      <h2 class="section-title">Programma</h2>
      <div class="divider"></div>
    </div>
    <div class="program-card reveal">
      <div class="prog-time">19:00 <span>sākums</span></div>
      <div class="prog-info">
        <h3>Ierašanās un vietu ieņemšana</h3>
        <p>Ierodaties laicīgi, lai izvēlētos labāko vietu! Var atnest segas, spilvenus un pašu gatavotus uzkodus.</p>
      </div>
      <div class="prog-badge">Brīvi</div>
    </div>
    <div class="program-card reveal">
      <div class="prog-time">20:00 <span>muzika</span></div>
      <div class="prog-info">
        <h3>Muzikālā priekšprogramma</h3>
        <p>Dzīvā mūzika un labākās filmskaņu melodijas no skolas ansambļa — sildīsim atmosfēru pirms saulrieta.</p>
      </div>
      <div class="prog-badge">Live</div>
    </div>
    <div class="program-card reveal">
      <div class="prog-time">20:30 <span>ēdiens</span></div>
      <div class="prog-info">
        <h3>Popkorna un uzkodu laiks</h3>
        <p>Uzkodu stūrītis atveras! Popkorns, karstā šokolāde, limonāde un pašmāju cepumi.</p>
      </div>
      <div class="prog-badge">Yum!</div>
    </div>
    <div class="program-card reveal">
      <div class="prog-time">21:00 <span>filma</span></div>
      <div class="prog-info">
        <h3>Filmas seanss sākas</h3>
        <p>Tieši tumsas iestāšanās brīdī — lielais ekrāns iededzas un burvība sākas.</p>
      </div>
      <div class="prog-badge">★ Galvenais</div>
    </div>
    <div class="program-card reveal">
      <div class="prog-time">23:30 <span>beigas</span></div>
      <div class="prog-info">
        <h3>Beigu diskusija un aiziešana</h3>
        <p>Pēc filmas — kopīga apspriešana un neaizmirstamas atmiņas. Neaizmirsti paņemt savas mantas!</p>
      </div>
      <div class="prog-badge">Wrap!</div>
    </div>
  </div>
</section>

<section id="filma">
  <div class="section-inner">
    <div class="section-label reveal">Vakara filma</div>
    <h2 class="section-title reveal">Šīs nakts galvenais varonis</h2>
    <div class="divider reveal"></div>
    <div class="movie-feature reveal">
      <div class="movie-poster">
        🎞️
        <div class="movie-poster-title">Noslēpumainā vasara</div>
      </div>
      <div class="movie-desc">
        <div class="movie-meta">
          <span class="meta-tag">Piedzīvojumi</span>
          <span class="meta-tag">Ģimenei</span>
          <span class="meta-tag">2024</span>
          <span class="meta-tag">112 min</span>
        </div>
        <p>Filma par grupu jaunu draudzēm, kuri vasarā atklāj senas leģendas noslēpumu savā mazajā pilsētā. Piedzīvojumi, draudzība un burvīgi vasaras ainavu kadri — ideāla izvēle brīvdabas seansam.</p>
        <p>Filma ir piemērota visiem vecumiem, ar oriģinālvalodas subtitriem latviešu valodā.</p>
        <p><em>Filmas izvēle tiks precizēta nedēļu pirms pasākuma — sekojiet ziņām!</em></p>
        <div class="rating">
          <div class="stars-rating">★★★★☆</div>
          <span style="font-size:1rem; color: var(--silver); font-family: 'Libre Baskerville', serif;">8.2 / 10</span>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="vieta">
  <div class="section-inner">
    <div class="section-label reveal">Norises vieta</div>
    <h2 class="section-title reveal">Kur mūs atrast?</h2>
    <div class="divider reveal"></div>
    <div class="location-grid reveal">
      <div class="map-placeholder">
        🗺️
        <p>Jēkabpils pilsētas parks</p>
      </div>
      <div class="location-details">
        <div class="location-item">
          <div class="loc-icon">📍</div>
          <div>
            <div class="loc-label">Adrese</div>
            <div class="loc-value">Jēkabpils pilsētas parks<br>Brīvības iela, Jēkabpils</div>
          </div>
        </div>
        <div class="location-item">
          <div class="loc-icon">🗓️</div>
          <div>
            <div class="loc-label">Datums un laiks</div>
            <div class="loc-value">Jūnijs 2025<br>Ieeja no 19:00</div>
          </div>
        </div>
        <div class="location-item">
          <div class="loc-icon">🌧️</div>
          <div>
            <div class="loc-label">Laika apstākļi</div>
            <div class="loc-value">Lietus gadījumā pasākums tiek pārcelts uz nākamo sestdienu. Sekojiet paziņojumiem!</div>
          </div>
        </div>
        <div class="location-item">
          <div class="loc-icon">🚌</div>
          <div>
            <div class="loc-label">Kā nokļūt</div>
            <div class="loc-value">Pilsētas autobuss Nr. 3 un 7<br>Pieturas "Pilsētas parks"</div>
          </div>
        </div>
        <div class="location-item">
          <div class="loc-icon">🎟️</div>
          <div>
            <div class="loc-label">Ieeja</div>
            <div class="loc-value">Brīva ieeja visiem!<br>Uzkodi par maksu</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="registracija">
  <div class="section-inner">
    <div class="reg-center">
      <div class="section-label">Piedalīšanās</div>
      <h2 class="section-title reveal">Pieteikties pasākumam</h2>
      <div class="divider"></div>
      <p style="color: var(--silver); font-size:0.95rem; line-height:1.7;">Pieteikšanās nav obligāta, bet palīdz mums sagatavot pietiekami daudz uzkodu! Aizpildi formu un mēs informēsim par jebkurām izmaiņām.</p>
      <div class="reg-form reveal">
        <div class="form-group">
          <label>Vārds un uzvārds</label>
          <input type="text" id="name" placeholder="Tavs vārds...">
        </div>
        <div class="form-group">
          <label>E-pasta adrese</label>
          <input type="email" id="email" placeholder="tavs@epasts.lv">
        </div>
        <div class="form-group">
          <label>Klase</label>
          <select id="klase">
            <option value="">Izvēlies klasi...</option>
            <option>9.a</option><option>9.b</option>
            <option>10.a</option><option>10.b</option>
            <option>11.a</option><option>11.b</option>
            <option>Cita</option>
          </select>
        </div>
        <div style="margin: 1.5rem 0;">
          <div class="section-label">Cik cilvēku atnāks?</div>
          <div class="counter-display">
            <button class="counter-btn" onclick="changeCount(-1)">−</button>
            <div>
              <div class="counter-num" id="countNum">1</div>
              <div class="counter-label">apmeklētāji</div>
            </div>
            <button class="counter-btn" onclick="changeCount(1)">+</button>
          </div>
        </div>
        <button class="btn-primary" onclick="submitReg()" style="width:100%; text-align:center;">Nosūtīt pieteikumu ✦</button>
        <div class="success-msg" id="successMsg">
          ✓ &nbsp; Paldies! Tava reģistrācija saņemta. Tiksimies parkā!
        </div>
      </div>
    </div>
  </div>
</section>

<section id="jautajumi">
  <div class="section-inner">
    <div class="section-label reveal">Biežāk uzdotie jautājumi</div>
    <h2 class="section-title reveal">Vai ir kādi jautājumi?</h2>
    <div class="divider reveal"></div>
    <div id="faqList" class="reveal">
      <div class="faq-item">
        <button class="faq-q">Ko man ņemt līdzi? <span class="faq-arrow">›</span></button>
        <div class="faq-a">Ieteicams ņemt segu vai pledi, spilvenu ērtai sēdēšanai/gulēšanai uz zāles, kā arī uzkodus. Ja ir paredzēts vēsāks vakars, ņem siltu džemperi!</div>
      </div>
      <div class="faq-item">
        <button class="faq-q">Vai var atnākt arī bez pieteikšanās? <span class="faq-arrow">›</span></button>
        <div class="faq-a">Jā, ieeja ir brīva un pieteikšanās nav obligāta. Tomēr, ja reģistrēsies, varam labāk sagatavoties un informēt tevi par izmaiņām laika apstākļu gadījumā.</div>
      </div>
      <div class="faq-item">
        <button class="faq-q">Ko darīt, ja līs lietus? <span class="faq-arrow">›</span></button>
        <div class="faq-a">Pasākums tiek noturēts jebkurā laikā, izņemot stipru lietu vai pērkona negaisu. Ja pasākums tiek atcelts vai pārcelts, visi reģistrētie apmeklētāji saņems e-pasta paziņojumu.</div>
      </div>
      <div class="faq-item">
        <button class="faq-q">Vai var ņemt līdzi dzīvniekus? <span class="faq-arrow">›</span></button>
        <div class="faq-a">Mājdzīvnieki ir laipni gaidīti, taču lūdzam pārliecināties, ka sunim ir pavada un tas netraucē citiem skatītājiem. Kaķus lūdzam atstāt mājās. 🐕</div>
      </div>
      <div class="faq-item">
        <button class="faq-q">Vai ir maksas parkošana tuvumā? <span class="faq-arrow">›</span></button>
        <div class="faq-a">Pie parka ir bezmaksas autostāvvieta. Iesakām izmantot arī pilsētas autobusu, lai nebūtu jāmeklē vieta automašīnai.</div>
      </div>
    </div>
  </div>
</section>

<section id="kontakti">
  <div class="section-inner">
    <div class="section-label reveal">Saziņa</div>
    <h2 class="section-title reveal">Sazinies ar mums</h2>
    <div class="divider reveal"></div>
    <div class="contact-grid reveal">
      <div class="contact-card">
        <div class="contact-icon">✉️</div>
        <h3>E-pasts</h3>
        <p><a href="mailto:kinopasākums@skola.lv">kinopasākums@skola.lv</a></p>
      </div>
      <div class="contact-card">
        <div class="contact-icon">📱</div>
        <h3>Tālrunis</h3>
        <p>+371 2X XXX XXX<br><span style="font-size:0.8rem; opacity:0.6;">Darba dienās 14:00–18:00</span></p>
      </div>
      <div class="contact-card">
        <div class="contact-icon">📸</div>
        <h3>Sociālie tīkli</h3>
        <p><a href="#">@KinoVakars2025</a><br>Instagram & Facebook</p>
      </div>
    </div>
  </div>
</section>

<section id="autors">
  <div class="section-inner">
    <div class="section-label reveal">Par lapu</div>
    <h2 class="section-title reveal">Autors un vietnes politika</h2>
    <div class="divider reveal"></div>
    <div class="author-grid reveal">
      <div class="author-card">
        <h3>Nick</h3>
        <div class="author-role">Lapas izstrādātājs · 10. klase</div>
        <p>Šo vietni izveidoja 10. klases skolēns Datoriku kā daļu no uzdevuma "Tīmekļa vietnes izveide". Vietne veidota ar mērķi reklamēt klases kopīgo brīvdabas kino vakaru un informēt interesentus par pasākumu.</p>
        <p style="margin-top: 1rem; font-size:0.85rem; color: rgba(168,184,200,0.6);">Izveidots ar Google Sites un HTML · 2025</p>
      </div>
      <div class="policy-box">
        <h3>Vietnes izmantošanas politika</h3>
        <p>Šī vietne ir izveidota izglītojošiem nolūkiem kā daļa no skolas uzdevuma. Visa tajā ievietotā informācija attiecas tikai uz šo pasākumu.</p>
        <p>Apmeklētāji reģistrējoties sniedz savu vārdu un e-pastu tikai pasākuma organizēšanas nolūkos. Dati netiek nodoti trešajām pusēm un tiek dzēsti pēc pasākuma norises.</p>
        <p>Vietnē izmantotie attēli un elementi ir paredzēti tikai nekomerciālai, izglītojošai lietošanai.</p>
        <p>Par vietnes saturu atbild lapas autors. Jautājumu gadījumā raksti uz kontaktformu.</p>
      </div>
    </div>
  </div>
</section>

<footer>
  <div class="footer-logo">✦ Brīvdabas Kino Vakars</div>
  <p>© 2025 · Jēkabpils · Izveidots ar ♥ datoriku stundā</p>
</footer>

<script>
const starsEl = document.getElementById('stars');
for (let i = 0; i < 180; i++) {
  const s = document.createElement('div');
  s.className = 'star';
  const size = Math.random() * 2.5 + 0.5;
  s.style.cssText = `width:${size}px;height:${size}px;top:${Math.random()*100}%;left:${Math.random()*100}%;--dur:${2+Math.random()*4}s;--delay:${Math.random()*5}s;`;
  starsEl.appendChild(s);
}
const fs = document.getElementById('filmstrip');
for (let i = 0; i < 60; i++) {
  const h = document.createElement('div');
  h.className = 'film-hole';
  fs.appendChild(h);
}
let count = 1;
function changeCount(d) {
  count = Math.max(1, Math.min(20, count + d));
  document.getElementById('countNum').textContent = count;
}
function submitReg() {
  const name = document.getElementById('name').value.trim();
  const email = document.getElementById('email').value.trim();
  if (!name || !email) { alert('Lūdzu aizpildi vārdu un e-pastu!'); return; }
  document.getElementById('successMsg').style.display = 'block';
  document.getElementById('name').value = '';
  document.getElementById('email').value = '';
  document.getElementById('klase').value = '';
  count = 1; document.getElementById('countNum').textContent = '1';
}
document.querySelectorAll('.faq-q').forEach(btn => {
  btn.addEventListener('click', () => {
    const item = btn.parentElement;
    const wasOpen = item.classList.contains('open');
    document.querySelectorAll('.faq-item').forEach(i => i.classList.remove('open'));
    if (!wasOpen) item.classList.add('open');
  });
});
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); } });
}, { threshold: 0.12 });
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>
</body>
</html>

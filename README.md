# ARMA-
boutique arme automatique et sémi automatique et équipements de protection destiné à la vente 
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>MAISON ÉLITE — Boutique</title>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Montserrat:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --cream: #F5F0E8;
      --dark: #1A1713;
      --gold: #B8965A;
      --gold-light: #D4AF78;
      --mid: #6B6459;
      --white: #FDFBF7;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'Montserrat', sans-serif;
      background: var(--cream);
      color: var(--dark);
      overflow-x: hidden;
    }

    /* ── NAV ── */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1.5rem 4rem;
      background: rgba(245,240,232,0.92);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(184,150,90,0.2);
      animation: fadeDown 0.8s ease both;
    }
    @keyframes fadeDown { from { opacity:0; transform:translateY(-20px); } to { opacity:1; transform:translateY(0); } }

    .nav-logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.6rem;
      font-weight: 300;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--dark);
      text-decoration: none;
    }
    .nav-logo span { color: var(--gold); }

    .nav-links { display: flex; gap: 2.5rem; list-style: none; }
    .nav-links a {
      font-size: 0.7rem; letter-spacing: 0.18em; text-transform: uppercase;
      color: var(--mid); text-decoration: none; transition: color 0.3s;
    }
    .nav-links a:hover { color: var(--gold); }

    .nav-actions { display: flex; gap: 1.5rem; align-items: center; }
    .cart-btn {
      font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase;
      background: var(--dark); color: var(--cream);
      border: none; padding: 0.65rem 1.4rem; cursor: pointer;
      transition: background 0.3s;
    }
    .cart-btn:hover { background: var(--gold); }

    /* ── HERO ── */
    .hero {
      min-height: 100vh;
      display: grid; grid-template-columns: 1fr 1fr;
      padding-top: 80px;
      animation: fadeIn 1s ease 0.3s both;
    }
    @keyframes fadeIn { from { opacity:0; } to { opacity:1; } }

    .hero-text {
      display: flex; flex-direction: column; justify-content: center;
      padding: 6rem 4rem 6rem 6rem;
    }
    .hero-eyebrow {
      font-size: 0.65rem; letter-spacing: 0.3em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 1.5rem;
    }
    .hero-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(3rem, 5vw, 5rem);
      font-weight: 300; line-height: 1.05;
      color: var(--dark); margin-bottom: 1.5rem;
    }
    .hero-title em { font-style: italic; color: var(--gold); }
    .hero-sub {
      font-size: 0.8rem; color: var(--mid); line-height: 1.8;
      max-width: 400px; margin-bottom: 3rem;
      font-weight: 300; letter-spacing: 0.04em;
    }
    .hero-cta {
      display: inline-flex; gap: 1.2rem; align-items: center;
    }
    .btn-primary {
      font-size: 0.7rem; letter-spacing: 0.18em; text-transform: uppercase;
      background: var(--dark); color: var(--cream);
      border: none; padding: 1rem 2.5rem; cursor: pointer;
      text-decoration: none; transition: all 0.3s;
    }
    .btn-primary:hover { background: var(--gold); }
    .btn-ghost {
      font-size: 0.7rem; letter-spacing: 0.18em; text-transform: uppercase;
      border: 1px solid var(--gold); color: var(--gold);
      padding: 1rem 2rem; cursor: pointer;
      text-decoration: none; transition: all 0.3s;
    }
    .btn-ghost:hover { background: var(--gold); color: var(--white); }

    .hero-image {
      position: relative; overflow: hidden;
      background: var(--dark);
    }
    .hero-image::before {
      content: '';
      position: absolute; inset: 0;
      background: linear-gradient(135deg, #2a2420 0%, #1a1713 50%, #3d3028 100%);
    }
    .hero-image-inner {
      position: relative; height: 100%;
      display: flex; align-items: center; justify-content: center;
    }
    .hero-decor {
      width: 280px; height: 380px;
      border: 1px solid rgba(184,150,90,0.3);
      position: relative;
    }
    .hero-decor::before {
      content: '';
      position: absolute; inset: 12px;
      border: 1px solid rgba(184,150,90,0.15);
    }
    .hero-decor-text {
      position: absolute; inset: 0;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center; gap: 1rem;
    }
    .hero-decor-text span {
      font-family: 'Cormorant Garamond', serif;
      font-size: 5rem; color: rgba(184,150,90,0.15);
      font-style: italic; line-height: 1;
    }
    .hero-decor-label {
      font-size: 0.6rem; letter-spacing: 0.3em; text-transform: uppercase;
      color: rgba(184,150,90,0.5);
    }
    .hero-badge {
      position: absolute; bottom: 3rem; right: 3rem;
      width: 90px; height: 90px;
      border-radius: 50%; border: 1px solid rgba(184,150,90,0.4);
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      animation: spin 20s linear infinite;
    }
    @keyframes spin { to { transform: rotate(360deg); } }
    .hero-badge span {
      font-size: 0.5rem; letter-spacing: 0.2em;
      text-transform: uppercase; color: var(--gold-light);
      text-align: center; line-height: 1.6;
    }

    /* ── STRIP ── */
    .strip {
      background: var(--dark); padding: 1rem 0;
      overflow: hidden; white-space: nowrap;
    }
    .strip-inner {
      display: inline-flex; gap: 4rem;
      animation: marquee 18s linear infinite;
    }
    @keyframes marquee { to { transform: translateX(-50%); } }
    .strip-item {
      font-size: 0.6rem; letter-spacing: 0.25em; text-transform: uppercase;
      color: rgba(184,150,90,0.7); display: flex; align-items: center; gap: 1rem;
    }
    .strip-item::after { content: '◆'; color: var(--gold); font-size: 0.4rem; }

    /* ── SECTION TITLE ── */
    .section-header { text-align: center; padding: 5rem 2rem 3rem; }
    .section-eyebrow {
      font-size: 0.6rem; letter-spacing: 0.35em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 1rem; display: block;
    }
    .section-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 4vw, 3.5rem);
      font-weight: 300; color: var(--dark); line-height: 1.1;
    }
    .section-title em { font-style: italic; color: var(--gold); }

    /* ── PRODUCTS ── */
    .products { padding: 2rem 4rem 6rem; }
    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 2rem;
    }
    .product-card {
      background: var(--white);
      border: 1px solid rgba(184,150,90,0.12);
      overflow: hidden;
      transition: transform 0.4s ease, box-shadow 0.4s ease;
      cursor: pointer;
      animation: cardIn 0.6s ease both;
    }
    .product-card:nth-child(1) { animation-delay: 0.1s; }
    .product-card:nth-child(2) { animation-delay: 0.2s; }
    .product-card:nth-child(3) { animation-delay: 0.3s; }
    .product-card:nth-child(4) { animation-delay: 0.4s; }
    .product-card:nth-child(5) { animation-delay: 0.5s; }
    .product-card:nth-child(6) { animation-delay: 0.6s; }
    @keyframes cardIn { from { opacity:0; transform:translateY(24px); } to { opacity:1; transform:translateY(0); } }

    .product-card:hover { transform: translateY(-6px); box-shadow: 0 20px 50px rgba(26,23,19,0.12); }

    .product-image {
      height: 300px; background: var(--dark);
      position: relative; overflow: hidden;
      display: flex; align-items: center; justify-content: center;
    }
    .product-image-bg {
      position: absolute; inset: 0;
    }
    .product-tag {
      position: absolute; top: 1.2rem; left: 1.2rem;
      font-size: 0.55rem; letter-spacing: 0.2em; text-transform: uppercase;
      background: var(--gold); color: var(--white);
      padding: 0.3rem 0.7rem;
    }
    .product-emoji {
      font-size: 4rem; position: relative; z-index: 1;
      filter: drop-shadow(0 8px 24px rgba(0,0,0,0.4));
      transition: transform 0.4s ease;
    }
    .product-card:hover .product-emoji { transform: scale(1.1); }

    .product-info { padding: 1.5rem; }
    .product-cat {
      font-size: 0.55rem; letter-spacing: 0.2em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 0.5rem; display: block;
    }
    .product-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.25rem; font-weight: 400;
      color: var(--dark); margin-bottom: 0.5rem; line-height: 1.2;
    }
    .product-desc {
      font-size: 0.72rem; color: var(--mid);
      line-height: 1.6; margin-bottom: 1.2rem; font-weight: 300;
    }
    .product-footer { display: flex; align-items: center; justify-content: space-between; }
    .product-price {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.4rem; font-weight: 300; color: var(--dark);
    }
    .product-price span { font-size: 0.8rem; color: var(--gold); margin-left: 0.3rem; }
    .add-btn {
      font-size: 0.6rem; letter-spacing: 0.15em; text-transform: uppercase;
      background: var(--dark); color: var(--cream);
      border: none; padding: 0.6rem 1.2rem; cursor: pointer;
      transition: background 0.3s;
    }
    .add-btn:hover { background: var(--gold); }

    /* ── FEATURES ── */
    .features {
      background: var(--dark); padding: 5rem 4rem;
      display: grid; grid-template-columns: repeat(3, 1fr); gap: 3rem;
    }
    .feature { text-align: center; }
    .feature-icon {
      font-size: 1.8rem; margin-bottom: 1.2rem; display: block;
    }
    .feature-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.2rem; font-weight: 300; color: var(--cream);
      margin-bottom: 0.7rem;
    }
    .feature-text {
      font-size: 0.72rem; color: rgba(184,150,90,0.6);
      line-height: 1.7; font-weight: 300; letter-spacing: 0.03em;
    }

    /* ── NEWSLETTER ── */
    .newsletter {
      padding: 6rem 4rem; text-align: center;
      background: linear-gradient(180deg, var(--cream) 0%, #EDE6D6 100%);
    }
    .newsletter-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 3.5vw, 3rem); font-weight: 300;
      color: var(--dark); margin-bottom: 0.8rem;
    }
    .newsletter-sub {
      font-size: 0.75rem; color: var(--mid); margin-bottom: 2.5rem;
      letter-spacing: 0.04em; font-weight: 300;
    }
    .newsletter-form { display: flex; gap: 0; justify-content: center; max-width: 480px; margin: 0 auto; }
    .newsletter-form input {
      flex: 1; padding: 1rem 1.5rem;
      border: 1px solid rgba(184,150,90,0.4); border-right: none;
      background: var(--white); font-family: 'Montserrat', sans-serif;
      font-size: 0.75rem; color: var(--dark); outline: none;
    }
    .newsletter-form input::placeholder { color: var(--mid); }
    .newsletter-form button {
      font-size: 0.65rem; letter-spacing: 0.18em; text-transform: uppercase;
      background: var(--gold); color: var(--white);
      border: none; padding: 1rem 1.8rem; cursor: pointer;
      transition: background 0.3s; font-family: 'Montserrat', sans-serif;
    }
    .newsletter-form button:hover { background: var(--dark); }

    /* ── FOOTER ── */
    footer {
      background: var(--dark); padding: 4rem 4rem 2rem;
    }
    .footer-top {
      display: grid; grid-template-columns: 2fr 1fr 1fr 1fr;
      gap: 3rem; margin-bottom: 3rem;
      border-bottom: 1px solid rgba(184,150,90,0.15);
      padding-bottom: 3rem;
    }
    .footer-brand { }
    .footer-logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.5rem; font-weight: 300; letter-spacing: 0.2em;
      text-transform: uppercase; color: var(--cream); margin-bottom: 1rem; display: block;
    }
    .footer-logo span { color: var(--gold); }
    .footer-desc {
      font-size: 0.7rem; color: rgba(184,150,90,0.5);
      line-height: 1.8; font-weight: 300;
    }
    .footer-col h4 {
      font-size: 0.6rem; letter-spacing: 0.25em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 1.2rem;
    }
    .footer-col ul { list-style: none; }
    .footer-col ul li { margin-bottom: 0.6rem; }
    .footer-col ul li a {
      font-size: 0.7rem; color: rgba(245,240,232,0.4);
      text-decoration: none; transition: color 0.3s; font-weight: 300;
    }
    .footer-col ul li a:hover { color: var(--gold-light); }
    .footer-bottom {
      display: flex; justify-content: space-between; align-items: center;
    }
    .footer-copy {
      font-size: 0.6rem; color: rgba(184,150,90,0.3);
      letter-spacing: 0.1em;
    }
    .footer-socials { display: flex; gap: 1rem; }
    .footer-socials a {
      font-size: 0.6rem; letter-spacing: 0.15em; text-transform: uppercase;
      color: rgba(184,150,90,0.4); text-decoration: none; transition: color 0.3s;
    }
    .footer-socials a:hover { color: var(--gold); }

    /* ── TOAST ── */
    .toast {
      position: fixed; bottom: 2rem; right: 2rem; z-index: 999;
      background: var(--dark); color: var(--cream);
      padding: 1rem 1.5rem; font-size: 0.7rem; letter-spacing: 0.08em;
      border-left: 3px solid var(--gold);
      transform: translateX(120%); transition: transform 0.4s ease;
      pointer-events: none;
    }
    .toast.show { transform: translateX(0); }

    @media (max-width: 900px) {
      nav { padding: 1.2rem 2rem; }
      .nav-links { display: none; }
      .hero { grid-template-columns: 1fr; }
      .hero-image { height: 300px; }
      .hero-text { padding: 3rem 2rem; }
      .products { padding: 2rem; }
      .features { grid-template-columns: 1fr; gap: 2rem; }
      .footer-top { grid-template-columns: 1fr 1fr; }
    }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">Maison <span>Élite</span></a>
  <ul class="nav-links">
    <li><a href="#produits">Boutique</a></li>
    <li><a href="#about">À propos</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <div class="nav-actions">
    <button class="cart-btn">🛍 Panier (0)</button>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-text">
    <p class="hero-eyebrow">✦ Nouvelle Collection 2026</p>
    <h1 class="hero-title">L'Art du<br/><em>Raffinement</em><br/>Absolu</h1>
    <p class="hero-sub">Chaque produit est sélectionné avec soin pour vous offrir une expérience d'achat unique — alliant qualité exceptionnelle et élégance intemporelle.</p>
    <div class="hero-cta">
      <a href="#produits" class="btn-primary">Découvrir la boutique</a>
      <a href="#about" class="btn-ghost">Notre histoire</a>
    </div>
  </div>
  <div class="hero-image">
    <div class="hero-image-inner">
      <div class="hero-decor">
        <div class="hero-decor-text">
          <span>M</span>
          <p class="hero-decor-label">Maison Élite — Since 2024</p>
        </div>
      </div>
      <div class="hero-badge">
        <span>Premium · Quality · Élite ·</span>
      </div>
    </div>
  </div>
</section>

<!-- STRIP -->
<div class="strip">
  <div class="strip-inner">
    <span class="strip-item">Livraison gratuite dès 80€</span>
    <span class="strip-item">Retours sous 30 jours</span>
    <span class="strip-item">Paiement sécurisé</span>
    <span class="strip-item">Service client premium</span>
    <span class="strip-item">Qualité garantie</span>
    <span class="strip-item">Livraison gratuite dès 80€</span>
    <span class="strip-item">Retours sous 30 jours</span>
    <span class="strip-item">Paiement sécurisé</span>
    <span class="strip-item">Service client premium</span>
    <span class="strip-item">Qualité garantie</span>
  </div>
</div>

<!-- PRODUCTS -->
<section id="produits">
  <div class="section-header">
    <span class="section-eyebrow">✦ Sélection exclusive</span>
    <h2 class="section-title">Nos <em>Bestsellers</em></h2>
  </div>
  <div class="products">
    <div class="products-grid" id="productsGrid"></div>
  </div>
</section>

<!-- FEATURES -->
<section class="features" id="about">
  <div class="feature">
    <span class="feature-icon">✦</span>
    <h3 class="feature-title">Qualité Supérieure</h3>
    <p class="feature-text">Chaque produit est rigoureusement sélectionné pour garantir les plus hauts standards de qualité et durabilité.</p>
  </div>
  <div class="feature">
    <span class="feature-icon">◈</span>
    <h3 class="feature-title">Livraison Rapide</h3>
    <p class="feature-text">Expédition sous 24h. Livraison offerte dès 80€ d'achat partout en France métropolitaine.</p>
  </div>
  <div class="feature">
    <span class="feature-icon">❖</span>
    <h3 class="feature-title">Satisfaction Garantie</h3>
    <p class="feature-text">Retours gratuits sous 30 jours. Votre satisfaction est notre priorité absolue.</p>
  </div>
</section>

<!-- NEWSLETTER -->
<section class="newsletter" id="contact">
  <h2 class="newsletter-title">Restez dans l'exclusivité</h2>
  <p class="newsletter-sub">Inscrivez-vous pour recevoir nos offres privées et nouveautés en avant-première.</p>
  <div class="newsletter-form">
    <input type="email" placeholder="Votre adresse email" />
    <button onclick="handleNewsletter()">S'inscrire</button>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div class="footer-brand">
      <span class="footer-logo">Maison <span>Élite</span></span>
      <p class="footer-desc">Une boutique dédiée à l'excellence et au raffinement. Des produits soigneusement sélectionnés pour les esprits exigeants.</p>
    </div>
    <div class="footer-col">
      <h4>Boutique</h4>
      <ul>
        <li><a href="#">Nouveautés</a></li>
        <li><a href="#">Bestsellers</a></li>
        <li><a href="#">Promotions</a></li>
        <li><a href="#">Collections</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Service</h4>
      <ul>
        <li><a href="#">Mon compte</a></li>
        <li><a href="#">Suivi commande</a></li>
        <li><a href="#">Retours</a></li>
        <li><a href="#">FAQ</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Légal</h4>
      <ul>
        <li><a href="#">Mentions légales</a></li>
        <li><a href="#">CGV</a></li>
        <li><a href="#">Confidentialité</a></li>
        <li><a href="#">Cookies</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <p class="footer-copy">© 2026 Maison Élite. Tous droits réservés.</p>
    <div class="footer-socials">
      <a href="#">Instagram</a>
      <a href="#">Pinterest</a>
      <a href="#">TikTok</a>
    </div>
  </div>
</footer>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
  const products = [
    { name: "Collection Prestige", cat: "Exclusivité", price: "129", tag: "Nouveau", emoji: "🏆", desc: "Notre pièce emblématique, conçue pour ceux qui ne font aucun compromis sur la qualité.", bg: "linear-gradient(135deg,#1e1a15,#2d2720)" },
    { name: "Édition Signature", cat: "Premium", price: "89", tag: "Bestseller", emoji: "✨", desc: "Un classique intemporel revisité avec les matériaux les plus nobles du marché.", bg: "linear-gradient(135deg,#1a1e1d,#1d2d2a)" },
    { name: "Série Artisan", cat: "Artisanal", price: "149", tag: null, emoji: "🎨", desc: "Fabriqué à la main par des artisans passionnés pour une finition irréprochable.", bg: "linear-gradient(135deg,#1e1a1d,#2a1e28)" },
    { name: "Box Découverte", cat: "Coffret", price: "59", tag: "Promo", emoji: "🎁", desc: "Le cadeau idéal : une sélection de nos produits phares dans un écrin luxueux.", bg: "linear-gradient(135deg,#1a1c1e,#1e2530)" },
    { name: "Formule Elite", cat: "Pack", price: "199", tag: "Exclusif", emoji: "👑", desc: "Notre offre la plus complète, réservée aux membres de notre programme VIP.", bg: "linear-gradient(135deg,#1e1d1a,#302a1a)" },
    { name: "Édition Limitée", cat: "Collector", price: "249", tag: "Rare", emoji: "💎", desc: "Seulement 100 exemplaires disponibles. Une rareté pour les collectionneurs avisés.", bg: "linear-gradient(135deg,#1a1e1a,#1e2e20)" },
  ];

  let cartCount = 0;

  function renderProducts() {
    const grid = document.getElementById('productsGrid');
    grid.innerHTML = products.map((p, i) => `
      <div class="product-card">
        <div class="product-image" style="background:${p.bg}">
          ${p.tag ? `<span class="product-tag">${p.tag}</span>` : ''}
          <span class="product-emoji">${p.emoji}</span>
        </div>
        <div class="product-info">
          <span class="product-cat">${p.cat}</span>
          <h3 class="product-name">${p.name}</h3>
          <p class="product-desc">${p.desc}</p>
          <div class="product-footer">
            <div class="product-price">${p.price}€ <span>TTC</span></div>
            <button class="add-btn" onclick="addToCart('${p.name}')">+ Ajouter</button>
          </div>
        </div>
      </div>
    `).join('');
  }

  function addToCart(name) {
    cartCount++;
    document.querySelector('.cart-btn').textContent = `🛍 Panier (${cartCount})`;
    showToast(`"${name}" ajouté au panier`);
  }

  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.classList.add('show');
    setTimeout(() => t.classList.remove('show'), 2800);
  }

  function handleNewsletter() {
    const input = document.querySelector('.newsletter-form input');
    if (input.value.includes('@')) {
      showToast('Inscription confirmée ! Merci 🎉');
      input.value = '';
    } else {
      showToast('Veuillez entrer un email valide.');
    }
  }

  renderProducts();
</script>
</body>
</html>

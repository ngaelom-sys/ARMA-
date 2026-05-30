# ARMADIE — Firearms & Tactical Equipment Store

Boutique en ligne spécialisée dans la vente d'armes automatiques, semi-automatiques et équipements de protection tactique.

---

<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>ARMADIE — Firearms Store</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --navy: #001f3f;
      --cream: #E8D7C3;
      --gold: #D4AF78;
      --dark: #0a0e27;
      --red: #C41E3A;
      --white: #FFFFFF;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'Roboto', sans-serif;
      background: var(--dark);
      color: var(--cream);
      overflow-x: hidden;
    }

    /* ── NAV ── */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1.5rem 4rem;
      background: rgba(0, 31, 63, 0.95);
      backdrop-filter: blur(12px);
      border-bottom: 2px solid var(--gold);
      animation: fadeDown 0.8s ease both;
    }
    @keyframes fadeDown { from { opacity:0; transform:translateY(-20px); } to { opacity:1; transform:translateY(0); } }

    .nav-logo {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.4rem;
      font-weight: 700;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--gold);
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 0.8rem;
    }
    .nav-logo-img {
      width: 40px;
      height: 40px;
      background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="50" cy="50" r="45" fill="%23E8D7C3"/><circle cx="50" cy="50" r="40" fill="%23001f3f"/><path d="M30,50 L70,50 M50,30 L50,70" stroke="%23D4AF78" stroke-width="2"/><circle cx="50" cy="50" r="8" fill="%23D4AF78"/></svg>') center/contain no-repeat;
    }

    .nav-links { display: flex; gap: 2.5rem; list-style: none; }
    .nav-links a {
      font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase;
      color: var(--cream); text-decoration: none; transition: color 0.3s;
      font-weight: 500;
    }
    .nav-links a:hover { color: var(--gold); }

    .nav-actions { display: flex; gap: 1.5rem; align-items: center; }
    .cart-btn {
      font-size: 0.7rem; letter-spacing: 0.12em; text-transform: uppercase;
      background: var(--red); color: var(--white);
      border: none; padding: 0.65rem 1.4rem; cursor: pointer;
      transition: background 0.3s; font-weight: 600;
    }
    .cart-btn:hover { background: var(--gold); color: var(--dark); }

    /* ── CART MODAL ── */
    .cart-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(0, 0, 0, 0.8);
      z-index: 200;
      animation: fadeIn 0.3s ease;
    }
    .cart-modal.active { display: flex; }
    .cart-modal-content {
      background: var(--navy);
      border: 2px solid var(--gold);
      border-radius: 8px;
      width: 90%;
      max-width: 600px;
      max-height: 80vh;
      overflow-y: auto;
      padding: 2rem;
      margin: auto;
      box-shadow: 0 0 50px rgba(212,175,120,0.3);
    }
    .cart-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 2rem;
      border-bottom: 1px solid rgba(212,175,120,0.3);
      padding-bottom: 1rem;
    }
    .cart-header h2 {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.5rem;
      color: var(--gold);
      letter-spacing: 0.05em;
    }
    .cart-close {
      background: none;
      border: none;
      color: var(--gold);
      font-size: 1.8rem;
      cursor: pointer;
      transition: color 0.3s;
    }
    .cart-close:hover { color: var(--red); }
    .cart-items {
      margin-bottom: 2rem;
    }
    .cart-item {
      display: grid;
      grid-template-columns: 1fr auto auto;
      gap: 1rem;
      padding: 1rem;
      background: rgba(212,175,120,0.05);
      border-left: 3px solid var(--red);
      margin-bottom: 1rem;
      align-items: center;
    }
    .cart-item-info h3 {
      font-family: 'Orbitron', sans-serif;
      color: var(--cream);
      margin-bottom: 0.3rem;
      font-size: 0.95rem;
    }
    .cart-item-price {
      color: var(--red);
      font-weight: 600;
      font-size: 1.1rem;
    }
    .cart-item-remove {
      background: var(--red);
      color: var(--white);
      border: none;
      padding: 0.4rem 0.8rem;
      cursor: pointer;
      font-size: 0.65rem;
      font-weight: 600;
      transition: background 0.3s;
    }
    .cart-item-remove:hover { background: var(--gold); color: var(--dark); }
    .cart-empty {
      text-align: center;
      padding: 2rem;
      color: #B8A599;
      font-style: italic;
    }
    .cart-summary {
      background: rgba(212,175,120,0.1);
      padding: 1.5rem;
      border: 1px solid rgba(212,175,120,0.3);
      margin-bottom: 2rem;
      border-radius: 4px;
    }
    .cart-total {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-family: 'Orbitron', sans-serif;
      font-size: 1.3rem;
      font-weight: 700;
      color: var(--red);
      margin-bottom: 1rem;
    }
    .cart-crypto-note {
      background: rgba(196, 30, 58, 0.2);
      padding: 1rem;
      border-left: 3px solid var(--red);
      margin-bottom: 1.5rem;
      font-size: 0.8rem;
      color: #B8A599;
      border-radius: 4px;
    }
    .crypto-methods {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem;
      margin-bottom: 2rem;
    }
    .crypto-btn {
      padding: 1rem;
      border: 2px solid var(--gold);
      background: rgba(212,175,120,0.05);
      color: var(--cream);
      cursor: pointer;
      font-family: 'Orbitron', sans-serif;
      font-weight: 600;
      text-transform: uppercase;
      font-size: 0.7rem;
      letter-spacing: 0.1em;
      transition: all 0.3s;
      border-radius: 4px;
    }
    .crypto-btn:hover {
      background: var(--gold);
      color: var(--dark);
      border-color: var(--red);
    }
    .checkout-btn {
      width: 100%;
      padding: 1.2rem;
      background: var(--red);
      color: var(--white);
      border: none;
      font-family: 'Orbitron', sans-serif;
      font-weight: 700;
      font-size: 0.8rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      cursor: pointer;
      transition: all 0.3s;
      border-radius: 4px;
    }
    .checkout-btn:hover {
      background: var(--gold);
      color: var(--dark);
    }
    .checkout-btn:disabled {
      background: #6B6459;
      cursor: not-allowed;
      opacity: 0.6;
    }

    /* ── HERO ── */
    .hero {
      min-height: 100vh;
      display: grid; grid-template-columns: 1fr 1fr;
      padding-top: 80px;
      background: linear-gradient(135deg, var(--dark) 0%, var(--navy) 100%);
      animation: fadeIn 1s ease 0.3s both;
    }
    @keyframes fadeIn { from { opacity:0; } to { opacity:1; } }

    .hero-text {
      display: flex; flex-direction: column; justify-content: center;
      padding: 6rem 4rem 6rem 6rem;
    }
    .hero-eyebrow {
      font-size: 0.65rem; letter-spacing: 0.25em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 1.5rem; font-weight: 700;
    }
    .hero-title {
      font-family: 'Orbitron', sans-serif;
      font-size: clamp(3rem, 5vw, 5rem);
      font-weight: 700; line-height: 1.05;
      color: var(--cream); margin-bottom: 1.5rem;
      letter-spacing: 0.05em;
    }
    .hero-title em { font-style: italic; color: var(--red); }
    .hero-sub {
      font-size: 0.85rem; color: #B8A599; line-height: 1.8;
      max-width: 450px; margin-bottom: 3rem;
      font-weight: 300; letter-spacing: 0.03em;
    }
    .hero-cta {
      display: inline-flex; gap: 1.2rem; align-items: center;
    }
    .btn-primary {
      font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase;
      background: var(--red); color: var(--white);
      border: 2px solid var(--red); padding: 1rem 2.5rem; cursor: pointer;
      text-decoration: none; transition: all 0.3s; font-weight: 600;
    }
    .btn-primary:hover { background: transparent; color: var(--red); }
    .btn-ghost {
      font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase;
      border: 2px solid var(--gold); color: var(--gold);
      padding: 1rem 2rem; cursor: pointer;
      text-decoration: none; transition: all 0.3s; font-weight: 600;
    }
    .btn-ghost:hover { background: var(--gold); color: var(--dark); }

    .hero-image {
      position: relative; overflow: hidden;
      background: var(--navy);
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .hero-image::before {
      content: '';
      position: absolute; inset: 0;
      background: radial-gradient(circle at center, rgba(212,175,120,0.1) 0%, transparent 70%);
    }
    .hero-logo-large {
      position: relative; z-index: 2;
      text-align: center;
    }
    .hero-logo-img {
      width: 300px;
      height: 300px;
      margin-bottom: 2rem;
      filter: drop-shadow(0 0 30px rgba(212,175,120,0.3));
    }
    .hero-badge {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.1rem;
      color: var(--gold);
      letter-spacing: 0.2em;
      text-transform: uppercase;
      font-weight: 700;
    }

    /* ── STRIP ── */
    .strip {
      background: var(--red); padding: 1.2rem 0;
      overflow: hidden; white-space: nowrap;
    }
    .strip-inner {
      display: inline-flex; gap: 4rem;
      animation: marquee 18s linear infinite;
    }
    @keyframes marquee { to { transform: translateX(-50%); } }
    .strip-item {
      font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase;
      color: var(--white); display: flex; align-items: center; gap: 1rem;
      font-weight: 600;
    }
    .strip-item::after { content: '◆'; color: var(--gold); font-size: 0.5rem; }

    /* ── SECTION TITLE ── */
    .section-header { text-align: center; padding: 5rem 2rem 3rem; }
    .section-eyebrow {
      font-size: 0.65rem; letter-spacing: 0.25em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 1rem; display: block; font-weight: 700;
    }
    .section-title {
      font-family: 'Orbitron', sans-serif;
      font-size: clamp(2rem, 4vw, 3.5rem);
      font-weight: 700; color: var(--cream); line-height: 1.1;
      letter-spacing: 0.04em;
    }
    .section-title em { font-style: italic; color: var(--red); }

    /* ── PRODUCTS ── */
    .products { padding: 2rem 4rem 6rem; }
    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 2.5rem;
    }
    .product-card {
      background: var(--navy);
      border: 2px solid var(--gold);
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

    .product-card:hover { transform: translateY(-8px); box-shadow: 0 20px 60px rgba(212,175,120,0.25); border-color: var(--red); }

    .product-image {
      height: 300px; background: linear-gradient(135deg, var(--navy) 0%, #0d1428 100%);
      position: relative; overflow: hidden;
      display: flex; align-items: center; justify-content: center;
    }
    .product-tag {
      position: absolute; top: 1.2rem; left: 1.2rem;
      font-size: 0.6rem; letter-spacing: 0.18em; text-transform: uppercase;
      background: var(--red); color: var(--white);
      padding: 0.4rem 0.8rem; font-weight: 700;
    }
    .product-emoji {
      font-size: 4.5rem; position: relative; z-index: 1;
      filter: drop-shadow(0 8px 24px rgba(0,0,0,0.6));
      transition: transform 0.4s ease;
    }
    .product-card:hover .product-emoji { transform: scale(1.15) rotate(-5deg); }

    .product-info { padding: 1.5rem; }
    .product-cat {
      font-size: 0.6rem; letter-spacing: 0.18em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 0.6rem; display: block; font-weight: 700;
    }
    .product-name {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.15rem; font-weight: 600;
      color: var(--cream); margin-bottom: 0.6rem; line-height: 1.2;
      letter-spacing: 0.02em;
    }
    .product-desc {
      font-size: 0.75rem; color: #B8A599;
      line-height: 1.6; margin-bottom: 1.2rem; font-weight: 300;
    }
    .product-footer { display: flex; align-items: center; justify-content: space-between; }
    .product-price {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.35rem; font-weight: 700; color: var(--red);
    }
    .product-price span { font-size: 0.75rem; color: var(--gold); margin-left: 0.3rem; }
    .add-btn {
      font-size: 0.65rem; letter-spacing: 0.12em; text-transform: uppercase;
      background: var(--red); color: var(--white);
      border: none; padding: 0.65rem 1.2rem; cursor: pointer;
      transition: background 0.3s; font-weight: 600;
    }
    .add-btn:hover { background: var(--gold); color: var(--dark); }

    /* ── FEATURES ── */
    .features {
      background: var(--navy); padding: 5rem 4rem;
      display: grid; grid-template-columns: repeat(3, 1fr); gap: 3rem;
      border-top: 2px solid var(--gold);
    }
    .feature { text-align: center; }
    .feature-icon {
      font-size: 2.2rem; margin-bottom: 1.2rem; display: block;
    }
    .feature-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.1rem; font-weight: 600; color: var(--gold);
      margin-bottom: 0.7rem;
      letter-spacing: 0.05em;
    }
    .feature-text {
      font-size: 0.75rem; color: #B8A599;
      line-height: 1.7; font-weight: 300; letter-spacing: 0.02em;
    }

    /* ── NEWSLETTER ── */
    .newsletter {
      padding: 6rem 4rem; text-align: center;
      background: linear-gradient(180deg, var(--navy) 0%, var(--dark) 100%);
      border-top: 2px solid var(--gold);
    }
    .newsletter-title {
      font-family: 'Orbitron', sans-serif;
      font-size: clamp(2rem, 3.5vw, 3rem); font-weight: 700;
      color: var(--cream); margin-bottom: 0.8rem;
      letter-spacing: 0.05em;
    }
    .newsletter-sub {
      font-size: 0.8rem; color: #B8A599; margin-bottom: 2.5rem;
      letter-spacing: 0.03em; font-weight: 300;
    }
    .newsletter-form { display: flex; gap: 0; justify-content: center; max-width: 500px; margin: 0 auto; }
    .newsletter-form input {
      flex: 1; padding: 1rem 1.5rem;
      border: 2px solid var(--gold); border-right: none;
      background: var(--dark); font-family: 'Roboto', sans-serif;
      font-size: 0.8rem; color: var(--cream); outline: none;
    }
    .newsletter-form input::placeholder { color: #6B6459; }
    .newsletter-form button {
      font-size: 0.65rem; letter-spacing: 0.15em; text-transform: uppercase;
      background: var(--red); color: var(--white);
      border: 2px solid var(--red); padding: 1rem 2rem; cursor: pointer;
      transition: all 0.3s; font-family: 'Orbitron', sans-serif; font-weight: 700;
    }
    .newsletter-form button:hover { background: transparent; color: var(--red); border-color: var(--red); }

    /* ── FOOTER ── */
    footer {
      background: var(--dark); padding: 4rem 4rem 2rem;
      border-top: 2px solid var(--red);
    }
    .footer-top {
      display: grid; grid-template-columns: 2fr 1fr 1fr 1fr;
      gap: 3rem; margin-bottom: 3rem;
      border-bottom: 1px solid rgba(212,175,120,0.2);
      padding-bottom: 3rem;
    }
    .footer-logo {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.3rem; font-weight: 700; letter-spacing: 0.1em;
      text-transform: uppercase; color: var(--gold); margin-bottom: 1rem; display: block;
    }
    .footer-desc {
      font-size: 0.75rem; color: #B8A599;
      line-height: 1.8; font-weight: 300;
    }
    .footer-col h4 {
      font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 1.2rem; font-weight: 700;
    }
    .footer-col ul { list-style: none; }
    .footer-col ul li { margin-bottom: 0.6rem; }
    .footer-col ul li a {
      font-size: 0.75rem; color: #B8A599;
      text-decoration: none; transition: color 0.3s; font-weight: 300;
    }
    .footer-col ul li a:hover { color: var(--gold); }
    .footer-bottom {
      display: flex; justify-content: space-between; align-items: center;
    }
    .footer-copy {
      font-size: 0.65rem; color: #6B6459;
      letter-spacing: 0.08em;
    }
    .footer-socials { display: flex; gap: 1.5rem; }
    .footer-socials a {
      font-size: 0.65rem; letter-spacing: 0.12em; text-transform: uppercase;
      color: #6B6459; text-decoration: none; transition: color 0.3s; font-weight: 600;
    }
    .footer-socials a:hover { color: var(--gold); }

    /* ── TOAST ── */
    .toast {
      position: fixed; bottom: 2rem; right: 2rem; z-index: 999;
      background: var(--red); color: var(--white);
      padding: 1rem 1.5rem; font-size: 0.75rem; letter-spacing: 0.08em;
      border-left: 4px solid var(--gold);
      transform: translateX(120%); transition: transform 0.4s ease;
      pointer-events: none; font-weight: 600;
    }
    .toast.show { transform: translateX(0); }

    @media (max-width: 900px) {
      nav { padding: 1.2rem 2rem; }
      .nav-links { display: none; }
      .hero { grid-template-columns: 1fr; }
      .hero-image { height: 400px; }
      .hero-text { padding: 3rem 2rem; }
      .products { padding: 2rem; }
      .features { grid-template-columns: 1fr; gap: 2rem; }
      .footer-top { grid-template-columns: 1fr 1fr; }
      .cart-modal-content { width: 95%; padding: 1.5rem; }
      .crypto-methods { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">
    <span class="nav-logo-img"></span>
    ARMADIE
  </a>
  <ul class="nav-links">
    <li><a href="#produits">Catalogue</a></li>
    <li><a href="#about">À propos</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <div class="nav-actions">
    <button class="cart-btn" onclick="openCart()">🛍 Panier (<span id="cartCount">0</span>)</button>
  </div>
</nav>

<!-- CART MODAL -->
<div class="cart-modal" id="cartModal">
  <div class="cart-modal-content">
    <div class="cart-header">
      <h2>Mon Panier</h2>
      <button class="cart-close" onclick="closeCart()">✕</button>
    </div>
    
    <div class="cart-items" id="cartItems">
      <div class="cart-empty">Votre panier est vide</div>
    </div>

    <div class="cart-summary" id="cartSummary" style="display: none;">
      <div class="cart-total">
        <span>Total:</span>
        <span id="cartTotal">0€</span>
      </div>
      
      <div class="cart-crypto-note">
        <strong>⚠️ Paiement en Crypto uniquement</strong><br>
        Sélectionnez votre méthode de paiement en cryptomonnaie pour procéder au checkout.
      </div>

      <div class="crypto-methods">
        <button class="crypto-btn" onclick="selectCrypto('BTC')">₿ Bitcoin</button>
        <button class="crypto-btn" onclick="selectCrypto('ETH')">Ξ Ethereum</button>
        <button class="crypto-btn" onclick="selectCrypto('USDT')">◆ USDT</button>
        <button class="crypto-btn" onclick="selectCrypto('XMR')">ⓧ Monero</button>
      </div>

      <button class="checkout-btn" id="checkoutBtn" onclick="checkout()" disabled>Procéder au Paiement Crypto</button>
    </div>
  </div>
</div>

<!-- HERO -->
<section class="hero">
  <div class="hero-text">
    <p class="hero-eyebrow">★ Spécialiste En Armement ★</p>
    <h1 class="hero-title">Équipement Tactique<br/><em>Professionnel</em></h1>
    <p class="hero-sub">ARMADIE vous propose une sélection rigoureuse d'armes à feu automatiques et semi-automatiques, d'équipements de protection haut de gamme et d'accessoires tactiques destinés aux professionnels et collectionneurs avertis.</p>
    <div class="hero-cta">
      <a href="#produits" class="btn-primary">Voir le catalogue</a>
      <a href="#about" class="btn-ghost">En savoir plus</a>
    </div>
  </div>
  <div class="hero-image">
    <div class="hero-logo-large">
      <div class="hero-logo-img" style="background: url('data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 500 500%22><defs><style>.skull {fill:none;stroke:%23D4AF78;stroke-width:3;stroke-linecap:round;stroke-linejoin:round;} .accent {fill:%23D4AF78;}</style></defs><circle cx=%22250%22 cy=%22250%22 r=%22240%22 class=%22skull%22/><circle cx=%22180%22 cy=%22200%22 r=%2245%22 class=%22skull%22/><circle cx=%22320%22 cy=%22200%22 r=%2245%22 class=%22skull%22/><rect x=%22220%22 y=%22240%22 width=%2260%22 height=%2240%22 class=%22skull%22/><line x1=%22100%22 y1=%22280%22 x2=%22160%22 y2=%22320%22 class=%22skull%22/><line x1=%22400%22 y1=%22280%22 x2=%22340%22 y2=%22320%22 class=%22skull%22/><line x1=%22180%22 y1=%22380%22 x2=%22320%22 y2=%22380%22 class=%22skull%22/><text x=%22250%22 y=%22450%22 font-family=%22Arial, sans-serif%22 font-size=%2260%22 font-weight=%22bold%22 text-anchor=%22middle%22 fill=%22%23D4AF78%22>ARMADIE</text></svg>') center/contain no-repeat;"></div>
      <p class="hero-badge">Firearms Store</p>
    </div>
  </div>
</section>

<!-- STRIP -->
<div class="strip">
  <div class="strip-inner">
    <span class="strip-item">✓ Paiement Crypto</span>
    <span class="strip-item">✓ Livraison sécurisée</span>
    <span class="strip-item">✓ Contrôles légaux</span>
    <span class="strip-item">✓ Authentification réquise</span>
    <span class="strip-item">✓ Garantie produit</span>
    <span class="strip-item">✓ Paiement Crypto</span>
    <span class="strip-item">✓ Livraison sécurisée</span>
    <span class="strip-item">✓ Contrôles légaux</span>
    <span class="strip-item">✓ Authentification réquise</span>
    <span class="strip-item">✓ Garantie produit</span>
  </div>
</div>

<!-- PRODUCTS -->
<section id="produits">
  <div class="section-header">
    <span class="section-eyebrow">★ Sélection Premium ★</span>
    <h2 class="section-title">Nos <em>Bestsellers</em></h2>
  </div>
  <div class="products">
    <div class="products-grid" id="productsGrid"></div>
  </div>
</section>

<!-- FEATURES -->
<section class="features" id="about">
  <div class="feature">
    <span class="feature-icon">🛡️</span>
    <h3 class="feature-title">Qualité Certifiée</h3>
    <p class="feature-text">Tous nos produits respectent les normes internationales et sont certifiés conformes aux standards militaires et professionnels.</p>
  </div>
  <div class="feature">
    <span class="feature-icon">🚚</span>
    <h3 class="feature-title">Expédition Sécurisée</h3>
    <p class="feature-text">Transport spécialisé avec assurance complète. Signature obligatoire à la réception. Traçabilité totale du colis.</p>
  </div>
  <div class="feature">
    <span class="feature-icon">⚖️</span>
    <h3 class="feature-title">Conformité Légale</h3>
    <p class="feature-text">Vente strictement réservée aux personnes autorisées. Vérification des permis et autorisations légales requises.</p>
  </div>
</section>

<!-- NEWSLETTER -->
<section class="newsletter" id="contact">
  <h2 class="newsletter-title">Restez Informé</h2>
  <p class="newsletter-sub">Inscrivez-vous pour recevoir nos mises à jour de stock et offres exclusives.</p>
  <div class="newsletter-form">
    <input type="email" placeholder="Votre adresse email" />
    <button onclick="handleNewsletter()">S'inscrire</button>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div class="footer-brand">
      <span class="footer-logo">ARMADIE</span>
      <p class="footer-desc">Spécialiste en équipements tactiques et armement professionnel. Vente aux personnes autorisées uniquement.</p>
    </div>
    <div class="footer-col">
      <h4>Catalogue</h4>
      <ul>
        <li><a href="#">Armes à Feu</a></li>
        <li><a href="#">Protection</a></li>
        <li><a href="#">Accessoires</a></li>
        <li><a href="#">Munitions</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Service</h4>
      <ul>
        <li><a href="#">Mon compte</a></li>
        <li><a href="#">Suivi commande</a></li>
        <li><a href="#">Support</a></li>
        <li><a href="#">FAQ</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Légal</h4>
      <ul>
        <li><a href="#">Mentions légales</a></li>
        <li><a href="#">CGV</a></li>
        <li><a href="#">Confidentialité</a></li>
        <li><a href="#">Conformité</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <p class="footer-copy">© 2026 ARMADIE. Tous droits réservés. Vente réservée aux personnes autorisées. Paiement en crypto uniquement.</p>
    <div class="footer-socials">
      <a href="#">Instagram</a>
      <a href="#">YouTube</a>
      <a href="#">Contact</a>
    </div>
  </div>
</footer>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
  const products = [
    { name: "AR-15 Tactical", cat: "Armes Semi-Auto", price: 1299, tag: "Bestseller", emoji: "🔫", desc: "Carabine de précision semi-automatique, certifiée pour usage professionnel et compétition.", bg: "linear-gradient(135deg, #001f3f 0%, #0d1428 100%)" },
    { name: "Kevlar Protection", cat: "Protection", price: 899, tag: "Premium", emoji: "🛡️", desc: "Gilet pare-balles niveau III+, certification militaire, confort optimal.", bg: "linear-gradient(135deg, #001f3f 0%, #0d1428 100%)" },
    { name: "Accessoires Tac.", cat: "Accessoires", price: 299, tag: null, emoji: "⚙️", desc: "Kit complet de montage rails, viseurs et accessoires tactiques professionnels.", bg: "linear-gradient(135deg, #001f3f 0%, #0d1428 100%)" },
    { name: "Munitions 5.56", cat: "Munitions", price: 149, tag: "Stock", emoji: "💣", desc: "Boîte de 1000 munitions 5.56 NATO, qualité militaire, précision garantie.", bg: "linear-gradient(135deg, #001f3f 0%, #0d1428 100%)" },
    { name: "Casque Balistique", cat: "Protection", price: 599, tag: "Nouveau", emoji: "🪖", desc: "Casque balistique NIJ Level III, poids optimisé pour usage prolongé.", bg: "linear-gradient(135deg, #001f3f 0%, #0d1428 100%)" },
    { name: "Pack Opérateur", cat: "Bundle", price: 2499, tag: "Exclusif", emoji: "👮", desc: "Pack complet pour opérateur professionnel : arme, protection, accessoires.", bg: "linear-gradient(135deg, #001f3f 0%, #0d1428 100%)" },
  ];

  let cart = [];
  let selectedCrypto = null;

  function renderProducts() {
    const grid = document.getElementById('productsGrid');
    grid.innerHTML = products.map((p) => `
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
            <button class="add-btn" onclick="addToCart('${p.name}', ${p.price})">+ Ajouter</button>
          </div>
        </div>
      </div>
    `).join('');
  }

  function addToCart(name, price) {
    cart.push({ name, price, id: Date.now() });
    updateCartUI();
    showToast(`"${name}" ajouté au panier`);
  }

  function removeFromCart(id) {
    cart = cart.filter(item => item.id !== id);
    updateCartUI();
    showToast('Produit retiré du panier');
  }

  function updateCartUI() {
    document.getElementById('cartCount').textContent = cart.length;
    
    const cartItemsDiv = document.getElementById('cartItems');
    const cartSummaryDiv = document.getElementById('cartSummary');
    
    if (cart.length === 0) {
      cartItemsDiv.innerHTML = '<div class="cart-empty">Votre panier est vide</div>';
      cartSummaryDiv.style.display = 'none';
      return;
    }

    cartItemsDiv.innerHTML = cart.map((item) => `
      <div class="cart-item">
        <div class="cart-item-info">
          <h3>${item.name}</h3>
          <div class="cart-item-price">${item.price}€</div>
        </div>
        <button class="cart-item-remove" onclick="removeFromCart(${item.id})">Retirer</button>
      </div>
    `).join('');

    const total = cart.reduce((sum, item) => sum + item.price, 0);
    document.getElementById('cartTotal').textContent = total + '€';
    cartSummaryDiv.style.display = 'block';
  }

  function openCart() {
    document.getElementById('cartModal').classList.add('active');
  }

  function closeCart() {
    document.getElementById('cartModal').classList.remove('active');
    selectedCrypto = null;
    document.getElementById('checkoutBtn').disabled = true;
  }

  function selectCrypto(crypto) {
    selectedCrypto = crypto;
    document.getElementById('checkoutBtn').disabled = false;
    showToast(`Méthode sélectionnée: ${crypto}`);
  }

  function checkout() {
    if (!selectedCrypto || cart.length === 0) {
      showToast('Veuillez sélectionner une méthode de paiement');
      return;
    }
    
    const total = cart.reduce((sum, item) => sum + item.price, 0);
    showToast(`Paiement de ${total}€ en ${selectedCrypto} - Redirection vers wallet...`);
    
    // Simulation - dans une vraie app, redirection vers payment gateway
    setTimeout(() => {
      cart = [];
      updateCartUI();
      closeCart();
      showToast('Transaction initié - Vérification en cours ✓');
    }, 2000);
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

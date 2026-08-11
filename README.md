<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sorbito de Amor – Ordenar</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;1,400&family=Cormorant+Garamond:wght@300;400;500&family=Montserrat:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --cream: #f5ede0;
    --cream-dark: #ecdcc8;
    --brown: #6b3f2a;
    --brown-light: #9b6b4a;
    --gold: #c8922a;
    --gold-light: #e8b45a;
    --text-dark: #2c1a0e;
    --text-mid: #5a3820;
    --white: #fffdf9;
    --shadow: rgba(107,63,42,0.15);
  }

  * { margin:0; padding:0; box-sizing:border-box; }

  body {
    background: var(--cream);
    font-family: 'Montserrat', sans-serif;
    color: var(--text-dark);
    min-height: 100vh;
  }

  /* ── TEXTURE OVERLAY ── */
  body::before {
    content:'';
    position:fixed; inset:0;
    background-image:
      radial-gradient(ellipse 600px 400px at 10% 20%, rgba(200,146,42,0.08) 0%, transparent 70%),
      radial-gradient(ellipse 500px 350px at 90% 80%, rgba(107,63,42,0.07) 0%, transparent 70%);
    pointer-events:none; z-index:0;
  }

  /* ── HEADER ── */
  header {
    background: var(--brown);
    padding: 0;
    position: sticky; top:0; z-index:100;
    box-shadow: 0 4px 20px rgba(0,0,0,0.25);
  }
  .header-inner {
    max-width:1200px; margin:0 auto;
    display:flex; align-items:center; justify-content:space-between;
    padding: 14px 24px;
  }
  .logo-area { display:flex; align-items:center; gap:14px; }
  .logo-icon {
    width:48px; height:48px;
    background: var(--gold);
    border-radius:50%;
    display:flex; align-items:center; justify-content:center;
    font-size:22px;
  }
  .logo-text h1 {
    font-family:'Playfair Display', serif;
    font-size:1.5rem; color:var(--cream);
    line-height:1;
  }
  .logo-text span {
    font-family:'Cormorant Garamond', serif;
    font-size:0.85rem; color:var(--gold-light);
    letter-spacing:3px; text-transform:uppercase;
  }

  .cart-btn {
    background: var(--gold);
    border:none; border-radius:30px;
    padding:10px 20px;
    color:var(--white); font-family:'Montserrat',sans-serif;
    font-weight:500; font-size:0.85rem;
    cursor:pointer; display:flex; align-items:center; gap:8px;
    transition: background .2s, transform .1s;
    position:relative;
  }
  .cart-btn:hover { background:var(--gold-light); transform:scale(1.03); }
  .cart-count {
    background: var(--brown);
    color:white; border-radius:50%;
    width:22px; height:22px; font-size:0.75rem;
    display:flex; align-items:center; justify-content:center;
    font-weight:700;
  }

  /* ── HERO ── */
  .hero {
    background: linear-gradient(135deg, var(--brown) 0%, #3d1f0e 100%);
    padding: 48px 24px 40px;
    text-align:center;
    position:relative; overflow:hidden;
  }
  .hero::before {
    content:'☕';
    position:absolute; font-size:220px; opacity:0.04;
    top:-30px; right:-20px; transform:rotate(15deg);
  }
  .hero h2 {
    font-family:'Playfair Display', serif;
    font-size:2.2rem; color:var(--cream);
    margin-bottom:8px;
  }
  .hero p { color:var(--gold-light); font-size:0.9rem; letter-spacing:1px; }

  /* ── LAYOUT ── */
  .page-wrap {
    max-width:1200px; margin:0 auto;
    display:grid;
    grid-template-columns: 1fr 340px;
    gap:28px;
    padding:28px 20px 60px;
    position:relative; z-index:1;
  }

  /* ── CATEGORY TABS ── */
  .tabs {
    display:flex; gap:8px; flex-wrap:wrap;
    margin-bottom:20px;
  }
  .tab {
    padding:8px 18px; border-radius:20px;
    border:2px solid var(--brown-light);
    background:transparent;
    color:var(--brown); font-family:'Montserrat',sans-serif;
    font-size:0.78rem; font-weight:500; letter-spacing:.5px;
    cursor:pointer; transition: all .2s;
    text-transform:uppercase;
  }
  .tab.active, .tab:hover {
    background:var(--brown); color:var(--cream); border-color:var(--brown);
  }

  /* ── MENU SECTION ── */
  .menu-section { display:none; }
  .menu-section.active { display:block; }

  .section-title {
    font-family:'Playfair Display', serif;
    font-size:1.6rem; color:var(--brown);
    margin-bottom:6px;
    display:flex; align-items:center; gap:12px;
  }
  .section-title::after {
    content:''; flex:1; height:1px;
    background:linear-gradient(to right, var(--brown-light), transparent);
  }
  .section-subtitle {
    font-size:0.75rem; color:var(--brown-light);
    letter-spacing:2px; text-transform:uppercase; margin-bottom:18px;
  }

  /* ── ITEM CARDS ── */
  .items-grid {
    display:grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap:14px; margin-bottom:32px;
  }
  .item-card {
    background:var(--white);
    border-radius:16px;
    padding:18px;
    box-shadow: 0 2px 12px var(--shadow);
    transition: transform .2s, box-shadow .2s;
    position:relative; overflow:hidden;
  }
  .item-card::before {
    content:''; position:absolute;
    top:0; left:0; right:0; height:3px;
    background:linear-gradient(to right, var(--gold), var(--brown-light));
  }
  .item-card:hover { transform:translateY(-3px); box-shadow:0 8px 24px var(--shadow); }

  .item-name {
    font-family:'Playfair Display', serif;
    font-size:1rem; color:var(--text-dark);
    margin-bottom:4px;
  }
  .item-desc {
    font-size:0.72rem; color:var(--brown-light);
    margin-bottom:10px; line-height:1.5;
    font-style:italic;
  }
  .item-bottom {
    display:flex; align-items:center; justify-content:space-between;
    margin-top:auto;
  }

  /* Size selector */
  .size-price {
    display:flex; gap:6px; flex-wrap:wrap;
  }
  .size-btn {
    padding:4px 10px; border-radius:12px;
    border:1.5px solid var(--cream-dark);
    background:var(--cream); font-size:0.72rem;
    cursor:pointer; font-family:'Montserrat',sans-serif;
    font-weight:500; color:var(--text-mid);
    transition:all .15s;
    display:flex; flex-direction:column; align-items:center; gap:1px;
  }
  .size-btn span.size-label { font-size:0.62rem; color:var(--brown-light); }
  .size-btn.selected { background:var(--gold); border-color:var(--gold); color:var(--white); }
  .size-btn.selected span.size-label { color:rgba(255,255,255,0.8); }

  /* Single price */
  .item-price {
    font-family:'Playfair Display', serif;
    font-size:1.15rem; color:var(--gold);
    font-weight:600;
  }

  .add-btn {
    background:var(--brown);
    border:none; border-radius:50%;
    width:34px; height:34px;
    color:var(--cream); font-size:1.3rem;
    cursor:pointer; display:flex; align-items:center; justify-content:center;
    transition:background .2s, transform .1s;
    flex-shrink:0;
  }
  .add-btn:hover { background:var(--gold); transform:scale(1.1); }

  .add-row { display:flex; align-items:center; gap:8px; }

  /* ── EXTRAS NOTE ── */
  .extras-note {
    background:var(--cream-dark);
    border-left: 3px solid var(--gold);
    border-radius:0 8px 8px 0;
    padding:10px 16px; margin-bottom:24px;
    font-size:0.75rem; color:var(--text-mid); line-height:1.6;
  }

  /* ── CART PANEL ── */
  .cart-panel {
    background:var(--white);
    border-radius:20px;
    padding:24px;
    box-shadow:0 4px 20px var(--shadow);
    position:sticky; top:80px; align-self:start;
    max-height: calc(100vh - 100px);
    overflow-y: auto;
  }
  .cart-panel h3 {
    font-family:'Playfair Display', serif;
    font-size:1.3rem; color:var(--brown);
    margin-bottom:16px;
    display:flex; align-items:center; gap:8px;
  }

  .cart-empty {
    text-align:center; padding:40px 20px;
    color:var(--brown-light); font-size:0.85rem; line-height:2;
  }
  .cart-empty .emoji { font-size:2.5rem; display:block; margin-bottom:8px; }

  .cart-items { margin-bottom:16px; }
  .cart-item {
    display:flex; justify-content:space-between; align-items:flex-start;
    padding:10px 0; border-bottom:1px solid var(--cream-dark);
    gap:8px;
  }
  .cart-item:last-child { border-bottom:none; }
  .cart-item-info { flex:1; }
  .cart-item-name {
    font-size:0.82rem; font-weight:500; color:var(--text-dark);
    line-height:1.3;
  }
  .cart-item-sub {
    font-size:0.72rem; color:var(--brown-light); margin-top:2px;
  }
  .cart-item-right { display:flex; align-items:center; gap:6px; flex-shrink:0; }
  .cart-item-price {
    font-family:'Playfair Display', serif;
    font-size:0.92rem; color:var(--gold); font-weight:600;
  }
  .qty-ctrl {
    display:flex; align-items:center; gap:4px;
  }
  .qty-btn {
    width:22px; height:22px; border-radius:50%;
    border:1.5px solid var(--cream-dark);
    background:var(--cream); font-size:0.85rem;
    cursor:pointer; display:flex; align-items:center; justify-content:center;
    transition:all .15s; color:var(--brown);
  }
  .qty-btn:hover { background:var(--brown); color:white; border-color:var(--brown); }
  .qty-num { font-size:0.82rem; font-weight:600; min-width:16px; text-align:center; }

  .cart-divider { height:1px; background:var(--cream-dark); margin:12px 0; }
  .cart-total {
    display:flex; justify-content:space-between; align-items:center;
    margin-bottom:18px;
  }
  .cart-total span:first-child { font-weight:500; font-size:0.88rem; }
  .cart-total span:last-child {
    font-family:'Playfair Display', serif;
    font-size:1.4rem; color:var(--brown); font-weight:600;
  }

  /* Notes */
  .notes-label { font-size:0.75rem; color:var(--brown-light); margin-bottom:6px; font-weight:500; }
  .notes-input {
    width:100%; border:1.5px solid var(--cream-dark);
    border-radius:10px; padding:8px 12px;
    font-family:'Montserrat',sans-serif; font-size:0.78rem;
    color:var(--text-dark); background:var(--cream);
    resize:none; margin-bottom:14px;
    transition:border-color .2s;
  }
  .notes-input:focus { outline:none; border-color:var(--gold); }

  /* Name */
  .name-input {
    width:100%; border:1.5px solid var(--cream-dark);
    border-radius:10px; padding:10px 14px;
    font-family:'Montserrat',sans-serif; font-size:0.82rem;
    color:var(--text-dark); background:var(--cream);
    margin-bottom:12px; transition:border-color .2s;
  }
  .name-input:focus { outline:none; border-color:var(--gold); }

  .checkout-btn {
    width:100%; padding:14px;
    background:linear-gradient(135deg, var(--brown) 0%, #3d1f0e 100%);
    color:var(--cream); border:none; border-radius:12px;
    font-family:'Playfair Display', serif;
    font-size:1.05rem; cursor:pointer;
    transition: opacity .2s, transform .1s;
    letter-spacing:.5px;
  }
  .checkout-btn:hover { opacity:.9; transform:scale(1.01); }
  .checkout-btn:disabled { opacity:.4; cursor:not-allowed; transform:none; }

  .payment-icons {
    display:flex; justify-content:center; gap:10px;
    margin-top:12px; flex-wrap:wrap;
  }
  .payment-icon {
    background:var(--cream); border:1px solid var(--cream-dark);
    border-radius:6px; padding:4px 10px;
    font-size:0.7rem; color:var(--brown-light); font-weight:500;
  }

  /* ── MODAL ── */
  .modal-overlay {
    display:none; position:fixed; inset:0;
    background:rgba(0,0,0,0.6); z-index:1000;
    align-items:center; justify-content:center; padding:20px;
  }
  .modal-overlay.open { display:flex; }
  .modal {
    background:var(--white); border-radius:20px;
    padding:32px; max-width:460px; width:100%;
    box-shadow:0 20px 60px rgba(0,0,0,0.3);
    animation: popIn .25s ease;
  }
  @keyframes popIn {
    from { transform:scale(.85); opacity:0; }
    to { transform:scale(1); opacity:1; }
  }
  .modal h3 {
    font-family:'Playfair Display', serif;
    font-size:1.4rem; color:var(--brown); margin-bottom:8px;
  }
  .modal p { font-size:0.85rem; color:var(--text-mid); margin-bottom:20px; line-height:1.6; }
  .modal-total {
    background:var(--cream); border-radius:12px; padding:16px;
    margin-bottom:20px; text-align:center;
  }
  .modal-total .amount {
    font-family:'Playfair Display', serif;
    font-size:2rem; color:var(--gold); font-weight:600;
  }
  .modal-total .label { font-size:0.78rem; color:var(--brown-light); }

  .pay-options { display:flex; flex-direction:column; gap:10px; margin-bottom:16px; }
  .pay-option {
    padding:14px 18px; border-radius:12px;
    border:2px solid var(--cream-dark);
    background:var(--cream); cursor:pointer;
    display:flex; align-items:center; gap:12px;
    font-family:'Montserrat',sans-serif; font-size:0.85rem;
    font-weight:500; color:var(--text-dark);
    transition:all .2s;
  }
  .pay-option:hover, .pay-option.selected {
    border-color:var(--gold); background:rgba(200,146,42,0.05);
  }
  .pay-icon { font-size:1.4rem; }
  .pay-desc { font-size:0.72rem; color:var(--brown-light); font-weight:400; }

  .modal-actions { display:flex; gap:10px; }
  .btn-cancel {
    flex:1; padding:12px; border-radius:10px;
    border:2px solid var(--cream-dark); background:transparent;
    color:var(--brown-light); font-family:'Montserrat',sans-serif;
    font-size:0.85rem; cursor:pointer; transition:all .2s;
  }
  .btn-cancel:hover { border-color:var(--brown-light); }
  .btn-confirm {
    flex:2; padding:12px; border-radius:10px;
    background:var(--gold); border:none;
    color:white; font-family:'Montserrat',sans-serif;
    font-size:0.85rem; font-weight:600; cursor:pointer;
    transition:all .2s;
  }
  .btn-confirm:hover { background:var(--gold-light); }

  /* ── SUCCESS ── */
  .success-modal {
    text-align:center;
  }
  .success-modal .check {
    font-size:4rem; margin-bottom:12px; display:block;
    animation: bounceIn .5s ease;
  }
  @keyframes bounceIn {
    0% { transform:scale(0); } 60% { transform:scale(1.2); } 100% { transform:scale(1); }
  }
  .success-modal h3 { margin-bottom:8px; }
  .order-num {
    background:var(--cream); border-radius:10px; padding:12px;
    font-family:'Playfair Display', serif;
    font-size:1.5rem; color:var(--brown);
    margin:12px 0; letter-spacing:2px;
  }
  .btn-new-order {
    width:100%; padding:14px; margin-top:16px;
    background:var(--brown); color:var(--cream);
    border:none; border-radius:12px;
    font-family:'Montserrat',sans-serif; font-size:0.9rem;
    cursor:pointer; transition:opacity .2s;
  }
  .btn-new-order:hover { opacity:.85; }

  /* ── RESPONSIVE ── */
  @media (max-width:768px) {
    /* Header mobile */
    .header-inner { padding:10px 16px; }
    .logo-icon { width:40px; height:40px; font-size:18px; }
    .logo-text h1 { font-size:1.2rem; }
    .logo-text span { font-size:0.7rem; letter-spacing:2px; }
    .cart-btn { padding:8px 16px; font-size:0.8rem; }
    .cart-count { width:20px; height:20px; font-size:0.7rem; }
    
    /* Hero mobile */
    .hero { padding:32px 16px 28px; }
    .hero h2 { font-size:1.6rem; }
    .hero p { font-size:0.8rem; }
    
    /* Page layout mobile */
    .page-wrap { 
      grid-template-columns:1fr; 
      gap:0;
      padding:20px 16px 120px;
    }
    
    /* Tabs mobile */
    .tabs { 
      gap:6px; 
      overflow-x:auto;
      -webkit-overflow-scrolling: touch;
      scrollbar-width: none;
      padding-bottom:8px;
    }
    .tabs::-webkit-scrollbar { display:none; }
    .tab { 
      padding:6px 14px; 
      font-size:0.7rem; 
      white-space:nowrap;
      flex-shrink:0;
    }
    
    /* Menu sections mobile */
    .section-title { font-size:1.3rem; }
    .section-subtitle { font-size:0.7rem; }
    .extras-note { font-size:0.7rem; padding:8px 12px; }
    
    /* Item cards mobile */
    .items-grid { 
      grid-template-columns: 1fr;
      gap:12px; 
    }
    .item-card { padding:14px; }
    .item-name { font-size:0.95rem; }
    .item-desc { font-size:0.68rem; }
    .size-btn { padding:3px 8px; font-size:0.68rem; }
    .size-btn span.size-label { font-size:0.58rem; }
    .item-price { font-size:1rem; }
    .add-btn { width:30px; height:30px; font-size:1.1rem; }
    
    /* Cart panel mobile - floating bottom */
    .cart-panel { 
      position:fixed; 
      bottom:0; 
      left:0; 
      right:0;
      border-radius:20px 20px 0 0; 
      max-height:70vh;
      transform:translateY(calc(100% - 60px));
      transition:transform .3s ease;
      z-index:50;
      box-shadow: 0 -4px 20px rgba(0,0,0,0.2);
    }
    .cart-panel.open { transform:translateY(0); }
    .cart-toggle-bar {
      display:flex; 
      justify-content:space-between; 
      align-items:center;
      cursor:pointer; 
      margin-bottom:0;
      padding-bottom:12px;
      border-bottom:1px solid var(--cream-dark);
    }
    .cart-toggle-bar h3 { margin-bottom:0; font-size:1.1rem; }
    .cart-toggle-bar .toggle-icon { 
      font-size:1.2rem; 
      transition:transform .3s;
    }
    .cart-panel.open .toggle-icon { transform:rotate(180deg); }
    .cart-body { margin-top:16px; }
    
    /* Cart items mobile */
    .cart-item { padding:8px 0; }
    .cart-item-name { font-size:0.78rem; }
    .cart-item-sub { font-size:0.68rem; }
    .cart-item-price { font-size:0.85rem; }
    .qty-btn { width:20px; height:20px; font-size:0.8rem; }
    .qty-num { font-size:0.78rem; }
    .cart-total span:first-child { font-size:0.85rem; }
    .cart-total span:last-child { font-size:1.2rem; }
    .name-input { padding:8px 12px; font-size:0.8rem; }
    .notes-input { padding:6px 10px; font-size:0.75rem; }
    .checkout-btn { padding:12px; font-size:0.95rem; }
    .payment-icons { gap:6px; margin-top:10px; }
    .payment-icon { padding:3px 8px; font-size:0.65rem; }
    
    /* Modal mobile */
    .modal-overlay { padding:12px; align-items:flex-end; }
    .modal { 
      padding:24px 20px; 
      max-width:100%;
      max-height:85vh;
      overflow-y:auto;
    }
    .modal h3 { font-size:1.2rem; }
    .modal p { font-size:0.8rem; }
    .modal-total { padding:12px; }
    .modal-total .amount { font-size:1.6rem; }
    .modal-total .label { font-size:0.72rem; }
    .pay-option { padding:12px 14px; font-size:0.8rem; }
    .pay-icon { font-size:1.2rem; }
    .pay-desc { font-size:0.68rem; }
    .btn-cancel, .btn-confirm { padding:10px; font-size:0.8rem; }
    
    /* Success modal mobile */
    .success-modal .check { font-size:3rem; }
    .order-num { font-size:1.2rem; padding:10px; }
    
    /* Footer mobile */
    footer { padding:32px 20px 24px !important; }
    footer > div > div:first-child { 
      flex-direction:column !important; 
      align-items:flex-start !important;
      gap:24px !important;
    }
    footer > div > div:first-child > div:last-child {
      flex-direction:column !important;
      gap:24px !important;
      width:100%;
    }
  }
  
  @media (min-width:769px) {
    .cart-toggle-bar { pointer-events:none; }
    .cart-toggle-bar .toggle-icon { display:none; }
    
    /* Desktop optimizations */
    .items-grid { 
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    }
    
    /* Hover effects only on desktop */
    .item-card:hover { 
      transform:translateY(-4px); 
      box-shadow:0 12px 32px var(--shadow); 
    }
    .tab:hover {
      background:var(--brown); 
      color:var(--cream);
    }
  }
  
  /* Tablet adjustments */
  @media (min-width:769px) and (max-width:1024px) {
    .page-wrap { 
      grid-template-columns: 1fr 300px;
      gap:24px;
      padding:24px 20px 40px;
    }
    .items-grid { 
      grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    }
  }
  
  /* Large desktop */
  @media (min-width:1400px) {
    .page-wrap { 
      max-width:1400px;
      grid-template-columns: 1fr 380px;
    }
    .items-grid { 
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    }
  }
  
  /* Small phones */
  @media (max-width:375px) {
    .hero h2 { font-size:1.4rem; }
    .section-title { font-size:1.2rem; }
    .modal { padding:20px 16px; }
  }

</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="header-inner">
    <div class="logo-area">
      <div class="logo-icon">☕</div>
      <div class="logo-text">
        <h1>Sorbito de Amor</h1>
        <span>coffee shop · desde 2002</span>
      </div>
    </div>
    <button class="cart-btn" onclick="toggleCart()">
      🛒 Mi orden
      <div class="cart-count" id="cartCount">0</div>
    </button>
  </div>
</header>

<!-- HERO -->
<div class="hero">
  <h2>Haz tu pedido</h2>
  <p>Desde 2002 — Saltillo, México</p>
</div>

<!-- MAIN -->
<div class="page-wrap">

  <!-- LEFT: MENU -->
  <div>
    <!-- TABS -->
    <div class="tabs" id="tabs">
      <button class="tab active" onclick="showCat('espresso')">Espresso</button>
      <button class="tab" onclick="showCat('calientes')">Calientes</button>
      <button class="tab" onclick="showCat('chocolates')">Chocolates</button>
      <button class="tab" onclick="showCat('chai')">Chai</button>
      <button class="tab" onclick="showCat('frio')">Frío & Frappe</button>
      <button class="tab" onclick="showCat('tes')">Tés Naturales</button>
      <button class="tab" onclick="showCat('cold')">Cold Brew</button>
      <button class="tab" onclick="showCat('extraccion')">Extracción</button>
      <button class="tab" onclick="showCat('food')">Croissant & Bagel</button>
      <button class="tab" onclick="showCat('ciabatta')">Ciabattas & Panini</button>
      <button class="tab" onclick="showCat('smoothies')">Smoothies & Sodas</button>
      <button class="tab" onclick="showCat('postres')">Postres</button>
    </div>

    <!-- ESPRESSO -->
    <div class="menu-section active" id="cat-espresso">
      <div class="section-title">Espresso</div>
      <div class="section-subtitle">Shots puros de café</div>
      <div class="items-grid" id="grid-espresso"></div>
    </div>

    <!-- CALIENTES -->
    <div class="menu-section" id="cat-calientes">
      <div class="section-title">Bebidas Calientes</div>
      <div class="section-subtitle">ch · m · g</div>
      <div class="extras-note">
        ☕ Shot espresso +$20 &nbsp;|&nbsp; Crema batida +$15 &nbsp;|&nbsp; Deslactosada/light +$10
      </div>
      <div class="items-grid" id="grid-calientes"></div>
    </div>

    <!-- CHOCOLATES -->
    <div class="menu-section" id="cat-chocolates">
      <div class="section-title">Chocolates</div>
      <div class="section-subtitle">ch · m · g</div>
      <div class="extras-note">
        ☕ Shot espresso +$20 &nbsp;|&nbsp; Crema batida +$15 &nbsp;|&nbsp; Deslactosada/light +$10
      </div>
      <div class="items-grid" id="grid-chocolates"></div>
    </div>

    <!-- CHAI -->
    <div class="menu-section" id="cat-chai">
      <div class="section-title">Chai</div>
      <div class="section-subtitle">ch · m · g</div>
      <div class="extras-note">Verde · Spiced · Vainilla · Sugar Free (+$5)</div>
      <div class="items-grid" id="grid-chai"></div>
    </div>

    <!-- FRÍO Y FRAPPE -->
    <div class="menu-section" id="cat-frio">
      <div class="section-title">Frío y Frappe</div>
      <div class="section-subtitle">ch · m · g</div>
      <div class="extras-note">Leche Avena, Almendra o Coco +$20 &nbsp;|&nbsp; Sabor Esencia +$10</div>
      <div class="items-grid" id="grid-frio"></div>
    </div>

    <!-- TÉS -->
    <div class="menu-section" id="cat-tes">
      <div class="section-title">Tés Naturales</div>
      <div class="section-subtitle">Pregunta por nuestra variedad</div>
      <div class="extras-note">Leche Avena, Almendra o Coco +$20 &nbsp;|&nbsp; Sabor Esencia +$10</div>
      <div class="items-grid" id="grid-tes"></div>
    </div>

    <!-- COLD BREW -->
    <div class="menu-section" id="cat-cold">
      <div class="section-title">Cold Brew</div>
      <div class="section-subtitle">ch · m · g</div>
      <div class="extras-note">Leche Avena, Almendra o Coco +$20 &nbsp;|&nbsp; Sabor Esencia +$10</div>
      <div class="items-grid" id="grid-cold"></div>
    </div>

    <!-- EXTRACCIÓN -->
    <div class="menu-section" id="cat-extraccion">
      <div class="section-title">Métodos de Extracción</div>
      <div class="section-subtitle">Otros métodos para un café excepcional</div>
      <div class="items-grid" id="grid-extraccion"></div>
    </div>

    <!-- FOOD: CROISSANT -->
    <div class="menu-section" id="cat-food">
      <div class="section-title">Croissant & Bagel</div>
      <div class="section-subtitle">Elige tu pan de preferencia</div>
      <div class="items-grid" id="grid-food"></div>
    </div>

    <!-- CIABATTA & PANINI -->
    <div class="menu-section" id="cat-ciabatta">
      <div class="section-title">Ciabattas & Panini</div>
      <div class="section-subtitle">Sándwiches artesanales</div>
      <div class="items-grid" id="grid-ciabatta"></div>
    </div>

    <!-- SMOOTHIES -->
    <div class="menu-section" id="cat-smoothies">
      <div class="section-title">Smoothies & Italian Sodas</div>
      <div class="section-subtitle">ch · m · g</div>
      <div class="items-grid" id="grid-smoothies"></div>
    </div>

    <!-- POSTRES -->
    <div class="menu-section" id="cat-postres">
      <div class="section-title">Postres</div>
      <div class="section-subtitle">El toque dulce perfecto</div>
      <div class="items-grid" id="grid-postres"></div>
    </div>
  </div>

  <!-- RIGHT: CART -->
  <div class="cart-panel" id="cartPanel">
    <div class="cart-toggle-bar" onclick="toggleCartMobile()">
      <h3>🛒 Mi Orden</h3>
      <span class="toggle-icon">▲</span>
    </div>
    <div class="cart-body">
      <div id="cartEmpty" class="cart-empty">
        <span class="emoji">☕</span>
        Tu orden está vacía.<br>¡Elige algo del menú!
      </div>
      <div class="cart-items" id="cartItems"></div>
      <div id="cartFooter" style="display:none">
        <div class="cart-divider"></div>
        <div class="cart-total">
          <span>Total</span>
          <span id="cartTotal">$0</span>
        </div>
        <label class="notes-label">Nombre para tu orden</label>
        <input class="name-input" id="clientName" placeholder="Tu nombre..." />
        <label class="notes-label">Notas especiales (opcional)</label>
        <textarea class="notes-input" id="orderNotes" rows="2" placeholder="Sin azúcar, leche de almendra..."></textarea>
        <button class="checkout-btn" onclick="openCheckout()">Pagar pedido →</button>
        <div class="payment-icons">
          <span class="payment-icon">💳 Tarjeta</span>
          <span class="payment-icon">📱 Transferencia</span>
          <span class="payment-icon">💵 Efectivo</span>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer style="
  background: var(--brown);
  color: var(--cream);
  padding: 40px 24px 32px;
  margin-top: 0;
  position: relative; z-index:1;
">
  <div style="max-width:1200px; margin:0 auto;">
    <div style="
      display:flex; flex-wrap:wrap; gap:32px;
      justify-content:space-between; align-items:flex-start;
      margin-bottom:28px;
    ">
      <!-- Brand -->
      <div>
        <div style="font-family:'Playfair Display',serif; font-size:1.4rem; margin-bottom:4px;">Sorbito de Amor</div>
        <div style="font-size:0.72rem; color:var(--gold-light); letter-spacing:3px; text-transform:uppercase;">Coffee Shop · Desde 2002</div>
      </div>

      <!-- Contact links -->
      <div style="display:flex; flex-wrap:wrap; gap:40px;">

        <!-- Ubicación -->
        <div>
          <div style="font-size:0.7rem; font-weight:600; letter-spacing:2px; text-transform:uppercase; color:var(--gold-light); margin-bottom:10px;">Ubicación</div>
          <a href="https://maps.google.com/?q=Blvd.+Pedro+Figueroa+966-2,+Saltillo,+Mexico" target="_blank"
            style="display:flex; align-items:flex-start; gap:8px; color:var(--cream); text-decoration:none; font-size:0.82rem; line-height:1.5; transition:color .2s;"
            onmouseover="this.style.color='var(--gold-light)'" onmouseout="this.style.color='var(--cream)'">
            <span style="font-size:1rem; flex-shrink:0; margin-top:1px;">📍</span>
            <span>Blvd. Pedro Figueroa 966-2<br>Saltillo, México, C.P. 25256</span>
          </a>
        </div>

        <!-- Contacto -->
        <div>
          <div style="font-size:0.7rem; font-weight:600; letter-spacing:2px; text-transform:uppercase; color:var(--gold-light); margin-bottom:10px;">Contacto</div>
          <div style="display:flex; flex-direction:column; gap:10px;">
            <a href="tel:8444851285"
              style="display:flex; align-items:center; gap:8px; color:var(--cream); text-decoration:none; font-size:0.82rem; transition:color .2s;"
              onmouseover="this.style.color='var(--gold-light)'" onmouseout="this.style.color='var(--cream)'">
              <span>📞</span> 844 485 1285
            </a>
            <a href="mailto:comentarios@sorbitodeamor.com"
              style="display:flex; align-items:center; gap:8px; color:var(--cream); text-decoration:none; font-size:0.82rem; transition:color .2s;"
              onmouseover="this.style.color='var(--gold-light)'" onmouseout="this.style.color='var(--cream)'">
              <span>✉️</span> comentarios@sorbitodeamor.com
            </a>
            <a href="https://m.me/SorbitodeAmor" target="_blank"
              style="display:flex; align-items:center; gap:8px; color:var(--cream); text-decoration:none; font-size:0.82rem; transition:color .2s;"
              onmouseover="this.style.color='var(--gold-light)'" onmouseout="this.style.color='var(--cream)'">
              <span>💬</span> Sorbito de Amor (Messenger)
            </a>
          </div>
        </div>

        <!-- Web & Redes -->
        <div>
          <div style="font-size:0.7rem; font-weight:600; letter-spacing:2px; text-transform:uppercase; color:var(--gold-light); margin-bottom:10px;">Encuéntranos</div>
          <div style="display:flex; flex-direction:column; gap:10px;">
            <a href="https://venenitocafe.com" target="_blank"
              style="display:flex; align-items:center; gap:8px; color:var(--cream); text-decoration:none; font-size:0.82rem; transition:color .2s;"
              onmouseover="this.style.color='var(--gold-light)'" onmouseout="this.style.color='var(--cream)'">
              <span>🔗</span> venenitocafe.com
            </a>
            <a href="https://facebook.com/SorbitodeAmor" target="_blank"
              style="display:flex; align-items:center; gap:8px; color:var(--cream); text-decoration:none; font-size:0.82rem; transition:color .2s;"
              onmouseover="this.style.color='var(--gold-light)'" onmouseout="this.style.color='var(--cream)'">
              <span>📘</span> Facebook
            </a>
            <a href="https://instagram.com/SorbitodeAmor" target="_blank"
              style="display:flex; align-items:center; gap:8px; color:var(--cream); text-decoration:none; font-size:0.82rem; transition:color .2s;"
              onmouseover="this.style.color='var(--gold-light)'" onmouseout="this.style.color='var(--cream)'">
              <span>📷</span> Instagram
            </a>
          </div>
        </div>
      </div>
    </div>

    <div style="border-top:1px solid rgba(255,255,255,0.12); padding-top:18px; text-align:center; font-size:0.72rem; color:rgba(245,237,224,0.45);">
      © 2024 Sorbito de Amor Coffee Shop · Saltillo, Coahuila
    </div>
  </div>
</footer>

<!-- CHECKOUT MODAL -->
<div class="modal-overlay" id="checkoutModal">
  <div class="modal">
    <h3>Confirmar pedido</h3>
    <p id="modalOrderSummary">Revisa tu pedido antes de pagar.</p>
    <div class="modal-total">
      <div class="label">Total a pagar</div>
      <div class="amount" id="modalTotal">$0</div>
    </div>
    <div id="paymentBrick_container"></div>
    <div class="pay-options">
      <div class="pay-option selected" id="pay-cash" onclick="selectPay('cash')">
        <span class="pay-icon">💵</span>
        <div>
          <div>Efectivo en caja</div>
          <div class="pay-desc">Paga al recoger tu pedido</div>
        </div>
      </div>
      <div class="pay-option" id="pay-card" onclick="selectPay('card')">
        <span class="pay-icon">💳</span>
        <div>
          <div>Tarjeta (crédito/débito)</div>
          <div class="pay-desc">Terminal en caja — Visa, MC, AMEX</div>
        </div>
      </div>
      <div class="pay-option" id="pay-transfer" onclick="selectPay('transfer')">
        <span class="pay-icon">📱</span>
        <div>
          <div>Transferencia / CoDi</div>
          <div class="pay-desc">CLABE: 012820001234567890</div>
        </div>
      </div>
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" onclick="closeCheckout()">Cancelar</button>
      <button class="btn-confirm" onclick="confirmOrder()">Confirmar pedido ✓</button>
    </div>
  </div>
</div>

<!-- SUCCESS MODAL -->
<div class="modal-overlay" id="successModal">
  <div class="modal success-modal">
    <span class="check">✅</span>
    <h3>¡Pedido recibido!</h3>
    <p>Prepara tu pago. En breve tu pedido estará listo. ¡Gracias por venir a Sorbito de Amor!</p>
    <div class="order-num" id="orderNumber">#0000</div>
    <p style="font-size:0.78rem; color:var(--brown-light);">Muestra este número en caja</p>
    <button class="btn-new-order" onclick="newOrder()">Hacer otro pedido</button>
  </div>
</div>

<script>
// ═══════════════════════════════════════
// MENU DATA
// ═══════════════════════════════════════
const menu = {
  espresso: [
    { name:'Espresso',   price:57,  single:true },
    { name:'Doppio',     price:63,  single:true },
    { name:'Tagliato',   price:67,  single:true },
    { name:'Macchiato',  price:67,  single:true },
    { name:'Con Panna',  price:67,  single:true },
    { name:'Affogato',   price:84,  single:true, desc:'Espresso sobre helado' },
    { name:'Bombon',     price:74,  single:true },
  ],
  calientes: [
    { name:'Espresso Americano', sizes:{ch:61,m:66,g:71} },
    { name:'Sorbito del Día',    sizes:{ch:54,m:59,g:64} },
    { name:'Cappuccino',         sizes:{ch:79,m:84,g:89} },
    { name:'Mochaccino',         sizes:{ch:83,m:88,g:94} },
    { name:'Caramel Latte',      sizes:{ch:83,m:88,g:94} },
    { name:'White Mocha',        sizes:{ch:84,m:89,g:94} },
    { name:'Cajeta Latte',       sizes:{ch:84,m:89,g:94} },
    { name:'Caffé Latte',        sizes:{ch:79,m:84,g:89} },
    { name:'Paradisso Latte',    sizes:{ch:84,m:89,g:94} },
    { name:'Creme Brulé Latte',  sizes:{ch:86,m:91,g:96} },
    { name:'Buona Notte Latte',  sizes:{ch:84,m:89,g:94} },
    { name:'Malva Mocha',        sizes:{ch:84,m:89,g:94} },
    { name:'Cinnamon Roll Latte',sizes:{ch:84,m:89,g:94} },
    { name:'Matcha Tea',         sizes:{ch:94,m:99,g:104} },
  ],
  chocolates: [
    { name:'Chocolate Caliente', sizes:{ch:74,m:79,g:84} },
    { name:'Crema de Luna',      sizes:{ch:84,m:89,g:94} },
    { name:'Rafaello',           sizes:{ch:86,m:91,g:96} },
  ],
  chai: [
    { name:'Chai Caliente', sizes:{ch:94,m:99,g:104}, desc:'Verde · Spiced · Vainilla · Sugar Free (+$5)' },
  ],
  frio: [
    { name:'Frappuccino',           sizes:{ch:85,m:90,g:100} },
    { name:'Mocha Frappe',          sizes:{ch:90,m:95,g:100} },
    { name:'Caramel Latte Frappe',  sizes:{ch:90,m:95,g:100} },
    { name:'White Mocha Frappe',    sizes:{ch:90,m:95,g:100} },
    { name:'Frappuccino Cajeta',    sizes:{ch:90,m:95,g:100} },
    { name:'Mocha Oreo',            sizes:{ch:90,m:95,g:100} },
    { name:'Malva Mocha Frappe',    sizes:{ch:94,m:99,g:104} },
    { name:'Crema de Luna Frappe',  sizes:{ch:90,m:95,g:100} },
    { name:'Rafaello Frappe',       sizes:{ch:92,m:97,g:102} },
    { name:'Java Chip',             sizes:{ch:90,m:95,g:100} },
    { name:'Matcha Green Tea',      sizes:{ch:95,m:100,g:105} },
    { name:'White Chocolate Frozen',sizes:{ch:90,m:95,g:100} },
    { name:'Chai Tea Frappe',       sizes:{ch:100,m:105,g:109}, desc:'Verde · Spiced · Vainilla · Sugar Free (+$5)' },
  ],
  tes: [
    { name:'Té Natural Caliente', sizes:{ch:69,m:74,g:79}, desc:'Pregunta por nuestra variedad de sabores' },
    { name:'Té Natural Frío',     sizes:{ch:74,m:79,g:84}, desc:'Pregunta por nuestra variedad de sabores' },
    { name:'Té Natural Frappe',   sizes:{ch:77,m:82,g:87}, desc:'Pregunta por nuestra variedad de sabores' },
  ],
  cold: [
    { name:'Cold Brew (natural o mineral)', sizes:{ch:75,m:80,g:85} },
    { name:'Vanilla Cream Cold Brew',       sizes:{ch:85,m:90,g:95} },
    { name:'Marshmallow Delight',           sizes:{ch:85,m:90,g:95} },
    { name:'Chillin Lavender',              sizes:{ch:85,m:90,g:95} },
    { name:'Coconut Love',                  sizes:{ch:85,m:90,g:95} },
  ],
  extraccion: [
    { name:'CHEMEX',       price:99, single:true, desc:'Taza limpia y cuerpo ligero' },
    { name:'AEROPRESS',    price:99, single:true, desc:'Taza limpia, cuerpo parecido al espresso' },
    { name:'DRIPPER V60',  price:99, single:true, desc:'Taza limpia con cuerpo moderado y sabor marcado' },
    { name:'FRENCH PRESS', price:99, single:true, desc:'Taza con cuerpo y alto contenido de aceites' },
  ],
  food: [
    { name:'Filadelfia',     price:95,  single:true, desc:'Tu pan de preferencia con queso Filadelfia' },
    { name:'Tradicional',    price:115, single:true, desc:'Pechuga de pavo ahumada y queso chihuahua' },
    { name:'Sorbito de Amor',price:125, single:true, desc:'Pechuga de pavo ahumada, mozarela, pimiento verde, tomate y champiñones (opcional)' },
    { name:'Pepino',         price:130, single:true, desc:'Pechuga de pavo ahumada, mozarela, pepino, lechuga y pimiento rojo' },
    { name:'Atún',           price:130, single:true, desc:'Atún, lechuga y pimiento rojo' },
    { name:'Salmón',         price:150, single:true, desc:'Salmón ahumado, filadelfia, pepino, cebolla morada' },
    { name:'Manzana',        price:100, single:true, desc:'Filadelfia, mermelada de manzana y canela' },
    { name:'Nutella',        price:109, single:true, desc:'Filadelfia y Nutella' },
  ],
  ciabatta: [
    { name:'Ciabatta Sorbito',  price:140, single:true, desc:'Jamón de pierna, mozarela, salami y tomate' },
    { name:'Ciabatta Atún',     price:130, single:true, desc:'Atún, lechuga y pimiento rojo' },
    { name:'Panini Ajo y Perejil',     price:125, single:true, desc:'Pechuga de pavo ahumada, mozarela y verduras' },
    { name:'Panini Mostaza con Queso', price:125, single:true, desc:'Jamón de pierna, queso chihuahua y verduras' },
  ],
  smoothies: [
    { name:'Smoothie', sizes:{ch:83,m:88,g:93}, desc:'Mango · Fresa · Piña Colada · Blueberry' },
    { name:'Italian Soda', sizes:{ch:70,m:75,g:80}, desc:'Menta · Kiwi · Raspberry · Coco · Blueberry y más' },
  ],
  postres: [
    { name:'Pasteles',             price:100, single:true, desc:'Pregunta por nuestra variedad (desde $100)' },
    { name:'Galletas',             price:60,  single:true, desc:'Chocochip · Arándano-nuez · Macadamia y chocolate blanco · Cacahuate · Pistache (desde $60)' },
    { name:'Brownie con Nieve',    price:95,  single:true },
    { name:'Empanadas',            price:40,  single:true, desc:'Piña · Cajeta · Chabacano' },
  ],
};

const sizeLabel = { ch:'Chico', m:'Mediano', g:'Grande' };

// ═══════════════════════════════════════
// RENDER MENU
// ═══════════════════════════════════════
function renderMenus() {
  for (const [cat, items] of Object.entries(menu)) {
    const grid = document.getElementById('grid-' + cat);
    if (!grid) continue;
    grid.innerHTML = '';
    items.forEach((item, idx) => {
      const card = document.createElement('div');
      card.className = 'item-card';

      let priceHTML = '';
      let selectedSize = null;

      if (item.single) {
        priceHTML = `<span class="item-price">$${item.price}</span>`;
      } else {
        const sizeKeys = Object.keys(item.sizes);
        selectedSize = sizeKeys[0];
        const btns = sizeKeys.map((s, i) =>
          `<button class="size-btn ${i===0?'selected':''}"
            data-cat="${cat}" data-idx="${idx}" data-size="${s}"
            onclick="selectSize(this,'${cat}',${idx},'${s}')">
            <span class="size-label">${sizeLabel[s]}</span>
            $${item.sizes[s]}
          </button>`
        ).join('');
        priceHTML = `<div class="size-price">${btns}</div>`;
      }

      card.innerHTML = `
        <div class="item-name">${item.name}</div>
        ${item.desc ? `<div class="item-desc">${item.desc}</div>` : ''}
        <div class="item-bottom">
          ${priceHTML}
          <div class="add-row">
            <button class="add-btn"
              data-cat="${cat}" data-idx="${idx}"
              onclick="addToCart('${cat}',${idx},this)">+</button>
          </div>
        </div>
      `;
      grid.appendChild(card);
    });
  }
}

function selectSize(btn, cat, idx, size) {
  const card = btn.closest('.item-card');
  card.querySelectorAll('.size-btn').forEach(b => b.classList.remove('selected'));
  btn.classList.add('selected');
  btn.dataset.selectedSize = size;
}

// ═══════════════════════════════════════
// CART STATE
// ═══════════════════════════════════════
let cart = [];

function addToCart(cat, idx, btn) {
  const item = menu[cat][idx];
  let label = item.name, price = item.price, size = null;

  if (!item.single) {
    const card = btn.closest('.item-card');
    const selBtn = card.querySelector('.size-btn.selected');
    size = selBtn ? selBtn.dataset.size : Object.keys(item.sizes)[0];
    price = item.sizes[size];
    label = item.name;
  }

  const key = cat + '-' + idx + (size ? '-' + size : '');
  const existing = cart.find(c => c.key === key);
  if (existing) {
    existing.qty++;
  } else {
    cart.push({ key, name:label, size:size ? sizeLabel[size] : null, price, qty:1 });
  }

  // Bounce animation
  btn.style.transform = 'scale(1.4)';
  setTimeout(() => btn.style.transform = '', 200);

  renderCart();
}

function changeQty(key, delta) {
  const idx = cart.findIndex(c => c.key === key);
  if (idx === -1) return;
  cart[idx].qty += delta;
  if (cart[idx].qty <= 0) cart.splice(idx, 1);
  renderCart();
}

function renderCart() {
  const count = cart.reduce((s, c) => s + c.qty, 0);
  const total = cart.reduce((s, c) => s + c.price * c.qty, 0);

  document.getElementById('cartCount').textContent = count;

  const emptyEl = document.getElementById('cartEmpty');
  const footerEl = document.getElementById('cartFooter');
  const itemsEl = document.getElementById('cartItems');

  if (cart.length === 0) {
    emptyEl.style.display = 'block';
    footerEl.style.display = 'none';
    itemsEl.innerHTML = '';
    return;
  }

  emptyEl.style.display = 'none';
  footerEl.style.display = 'block';

  itemsEl.innerHTML = cart.map(c => `
    <div class="cart-item">
      <div class="cart-item-info">
        <div class="cart-item-name">${c.name}</div>
        ${c.size ? `<div class="cart-item-sub">${c.size}</div>` : ''}
      </div>
      <div class="cart-item-right">
        <div class="qty-ctrl">
          <button class="qty-btn" onclick="changeQty('${c.key}',-1)">−</button>
          <span class="qty-num">${c.qty}</span>
          <button class="qty-btn" onclick="changeQty('${c.key}',1)">+</button>
        </div>
        <div class="cart-item-price">$${c.price * c.qty}</div>
      </div>
    </div>
  `).join('');

  document.getElementById('cartTotal').textContent = '$' + total;
}

// ═══════════════════════════════════════
// CATEGORY TABS
// ═══════════════════════════════════════
function showCat(cat) {
  document.querySelectorAll('.menu-section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  document.getElementById('cat-' + cat).classList.add('active');
  event.target.classList.add('active');
}

// ═══════════════════════════════════════
// CART TOGGLE (mobile)
// ═══════════════════════════════════════
function toggleCart() {
  const panel = document.getElementById('cartPanel');
  panel.classList.toggle('open');
}
function toggleCartMobile() {
  if (window.innerWidth <= 768) {
    document.getElementById('cartPanel').classList.toggle('open');
  }
}

// ═══════════════════════════════════════
// CHECKOUT
// ═══════════════════════════════════════
let selectedPay = 'cash';

function selectPay(method) {
  selectedPay = method;
  ['cash','card','transfer'].forEach(m => {
    document.getElementById('pay-' + m).classList.toggle('selected', m === method);
  });
}

function openCheckout() {
  if (cart.length === 0) return;
  const name = document.getElementById('clientName').value.trim();
  const total = cart.reduce((s, c) => s + c.price * c.qty, 0);
  const summary = (name ? `Pedido de <strong>${name}</strong><br><br>` : '') +
    cart.map(c => `${c.qty}× ${c.name}${c.size ? ' ('+c.size+')' : ''} — $${c.price * c.qty}`).join('<br>');

  document.getElementById('modalOrderSummary').innerHTML = summary;
  document.getElementById('modalTotal').textContent = '$' + total;
  document.getElementById('checkoutModal').classList.add('open');
}

function closeCheckout() {
  document.getElementById('checkoutModal').classList.remove('open');
}

async function confirmOrder() {
  if (cart.length === 0) return;
  
  const mp = new MercadoPago("APP_USR-87258bb7-c2d0-4a5d-a05e-dae843f8f322");
  const bricksBuilder = mp.bricks();
  const total = cart.reduce((s, c) => s + c.price * c.qty, 0);
  
  document.getElementById("paymentBrick_container").innerHTML = "";
  
  await bricksBuilder.create("cardPayment", "paymentBrick_container", {
    initialization: {
      amount: total
    },
    callbacks: {
      onSubmit: async (formData) => {
        try {
          const clientName = document.getElementById('clientName').value.trim();
          const clientNotes = document.getElementById('orderNotes').value.trim();
          
          const res = await fetch("https://sorbito-de-amor.onrender.com/api/pagar", {
            method: "POST",
            headers: {
              "Content-Type": "application/json"
            },
            body: JSON.stringify({
              token: formData.token,
              payment_method_id: formData.payment_method_id,
              transaction_amount: total,
              installments: formData.installments,
              description: "Pedido Sorbito de Amor",
              payer: {
                email: formData.payer?.email || "cliente@sorbitodeamor.com"
              },
              order_items: cart,
              customer_name: clientName,
              customer_notes: clientNotes
            })
          });
          
          const data = await res.json();
          
          if (data.status === "approved") {
            const orderNum = data.order_number || '#' + String(Math.floor(Math.random() * 9000) + 1000);
            document.getElementById('orderNumber').textContent = orderNum;
            document.getElementById('checkoutModal').classList.remove('open');
            document.getElementById('successModal').classList.add('open');
          } else {
            alert("Pago rechazado ❌\n" + (data.message || "Por favor intenta con otra tarjeta"));
          }
        } catch (error) {
          console.error(error);
          alert("Error en el pago. Por favor intenta de nuevo o contacta a soporte.");
        }
      },
      onError: (error) => console.error(error)
    }
  });
}

function newOrder() {
  cart = [];
  renderCart();
  document.getElementById('clientName').value = '';
  document.getElementById('orderNotes').value = '';
  document.getElementById('successModal').classList.remove('open');
}

// ═══════════════════════════════════════
// INIT
// ═══════════════════════════════════════
renderMenus();
renderCart();
</script>
<script src="https://sdk.mercadopago.com/js/v2"></script>
</body>
</html>
# ALMORA
<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>ALMORA — Harina de Almendra</title>
<meta name="description" content="ALMORA - Harina de almendra artesanal. Recetas, preguntas y carrito de compras." />

<style>
  :root{
    --green-dark:#203f33;
    --green-mid:#385341;
    --accent:#d6a772;
    --cream:#f5f1e8;
    --card-bg:#ffffff;
    --muted:#7a6f63;
    --glass: rgba(255,255,255,0.6);
  }

  /* reset ligero */
  *{box-sizing:border-box;margin:0;padding:0}
  html,body{height:100%}
  body{
    font-family: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    background: linear-gradient(180deg, #eef3ec 0%, var(--cream) 100%);
    color:var(--green-dark);
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
    line-height:1.45;
  }

  /* header */
  header{
    position:sticky;
    top:0;
    background:var(--cream);
    border-bottom:1px solid rgba(32,63,51,0.06);
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:20px;
    padding:14px 20px;
    z-index:80;
  }
  .brand{display:flex;align-items:center;gap:12px}
  .brand img{
    width:64px;height:64px;object-fit:contain;border-radius:8px;
    transform:translateY(-6px);
    animation:logoFloat 1100ms ease both;
  }
  @keyframes logoFloat{
    from{opacity:0; transform: translateY(-20px) scale(.95)}
    to{opacity:1; transform: translateY(0) scale(1)}
  }
  .brand h1{font-size:20px;letter-spacing:1px;margin-bottom:2px}
  .brand p{font-size:12px;color:var(--muted);margin-top:2px}

  nav{display:flex;gap:12px;align-items:center}
  nav a{color:var(--green-mid);text-decoration:none;font-weight:600;padding:8px 10px;border-radius:8px}
  nav a:hover{background:rgba(32,63,51,0.06)}

  /* main hero */
  .hero{
    display:grid;
    grid-template-columns: 1fr 420px;
    gap:28px;
    align-items:center;
    padding:36px 20px 28px;
  }
  .hero-left{
    padding:28px;
    background: linear-gradient(180deg, rgba(59,86,69,0.92) 0%, rgba(45,71,58,0.95) 100%);
    color:white;border-radius:14px;box-shadow:0 10px 30px rgba(15,23,21,0.15);
    position:relative; overflow:hidden;
    transform:translateY(0);
    animation:fadeUp .9s ease both;
  }
  @keyframes fadeUp{from{opacity:0; transform:translateY(18px)} to{opacity:1; transform:translateY(0)}}
  .hero-left h2{font-family: Georgia, serif; font-size:36px; margin-bottom:10px}
  .hero-left p{color:rgba(255,255,255,0.9); margin-bottom:18px}
  .hero-cta{display:flex;gap:12px;align-items:center}
  .btn{
    background:var(--accent); color:white; padding:12px 18px; border-radius:10px; text-decoration:none; font-weight:700;
    box-shadow: 0 8px 18px rgba(214,167,114,0.18); border:0; cursor:pointer;
    transition: transform .18s ease, box-shadow .18s ease;
  }
  .btn:hover{transform:translateY(-3px); box-shadow: 0 14px 30px rgba(214,167,114,0.22)}

  .hero-right{
    background:var(--card-bg); border-radius:12px; padding:18px;
    box-shadow: 0 8px 24px rgba(22,33,26,0.06);
    display:flex;flex-direction:column;align-items:center;justify-content:center;
    animation:fadeIn .9s .15s both;
  }
  @keyframes fadeIn{from{opacity:0} to{opacity:1}}
  .hero-right img{width:260px;height:auto;display:block}

  /* featured / grid */
  .section{padding:36px 20px}
  .cards{display:grid;gap:18px;grid-template-columns:repeat(auto-fit,minmax(220px,1fr))}

  .product{
    background:var(--card-bg);padding:16px;border-radius:12px;
    box-shadow:0 6px 20px rgba(20,30,24,0.06); transition: transform .18s ease, box-shadow .18s ease;
    display:flex;flex-direction:column;gap:10px;
  }
  .product:hover{transform:translateY(-6px);box-shadow:0 14px 30px rgba(24,40,30,0.09)}
  .product img{width:100%;height:180px;object-fit:cover;border-radius:8px}
  .priceRow{display:flex;justify-content:space-between;align-items:center;margin-top:auto}
  .price{font-weight:800;color:var(--green-mid)}

  /* carrito */
  .cartBtn{background:transparent;border:2px solid var(--green-mid);padding:8px 12px;border-radius:10px;cursor:pointer}
  .cart-panel{
    position:fixed;right:18px;top:84px;width:360px;max-width:calc(100% - 36px);background:white;border-radius:12px;
    box-shadow:0 18px 40px rgba(20,30,22,0.18);overflow:hidden;transform:translateX(22px);opacity:0;
    transition:transform .28s ease,opacity .28s ease; z-index:140;
  }
  .cart-panel.open{transform:translateX(0);opacity:1}
  .cart-header{padding:14px 16px;border-bottom:1px solid #f1efe8;display:flex;justify-content:space-between;align-items:center}
  .cart-items{max-height:360px;overflow:auto;padding:12px}
  .cart-item{display:flex;gap:12px;align-items:center;padding:8px;border-radius:8px}
  .cart-item img{width:64px;height:56px;object-fit:cover;border-radius:8px}
  .qty{display:flex;gap:6px;align-items:center}
  .qty button{padding:6px 8px;border-radius:6px;border:1px solid #e6e0d6;background:transparent;cursor:pointer}

  .cart-footer{padding:12px;border-top:1px solid #f1efe8;display:flex;justify-content:space-between;align-items:center}

  /* FAQ */
  .faq{max-width:900px;margin:0 auto;text-align:left}
  .faq-item{background:var(--card-bg);padding:14px;border-radius:10px;margin-bottom:10px;cursor:pointer;box-shadow:0 6px 16px rgba(18,28,22,0.04)}
  .faq-item h4{margin-bottom:6px}
  .faq-item p{display:none;color:var(--muted)}

  /* Comentarios */
  .comentarios{display:flex;flex-direction:column;gap:12px;max-width:900px;margin:12px auto 0;text-align:left}
  .coment{background:var(--card-bg);padding:12px;border-radius:10px;box-shadow:0 6px 16px rgba(18,28,22,0.04)}

  /* animaciones suaves */
  .fadeUp{animation:fadeUp .6s ease both}
  .slideLeft{animation:slideLeft .6s ease both}
  @keyframes slideLeft{from{opacity:0;transform:translateX(12px)}to{opacity:1;transform:translateX(0)}}

  /* responsive */
  @media(max-width:980px){
    .hero{grid-template-columns:1fr}
    .hero-right{order:-1;margin-bottom:12px}
    nav a{display:none}
  }
  @media(max-width:520px){
    .brand img{width:52px;height:52px}
    .hero-left h2{font-size:26px}
  }
</style>
</head>
<body>

<header>
  <div class="brand">
    <!-- Pon aquí tu logo tal cual: guarda el archivo como 'almora-logo.png' -->
    <img src="almora-logo.png" alt="ALMORA Logo" id="brandLogo">
    <div>
      <h1>ALMORA</h1>
      <p>Harina de almendra • Artesanal</p>
    </div>
  </div>

  <nav aria-label="Navegación principal">
    <a href="#productos">Productos</a>
    <a href="#recetas">Recetas</a>
    <a href="#comentarios">Comentarios</a>
    <a href="#faq">Dudas</a>
  </nav>

  <div style="display:flex;align-items:center;gap:10px">
    <button class="cartBtn" id="openCartBtn" aria-haspopup="dialog">🛒 Carrito <span id="cartCount" style="margin-left:8px;font-weight:700">0</span></button>
  </div>
</header>

<!-- HERO -->
<section class="hero" aria-label="Hero">
  <div class="hero-left">
    <h2>Descubre la pureza de la harina de almendra</h2>
    <p>Natural, deliciosa y perfecta para tus recetas: galletas, pan y mucho más. Inspirado en un estilo artesanal y premium.</p>
    <div class="hero-cta">
      <button class="btn" onclick="document.getElementById('productos').scrollIntoView({behavior:'smooth'})">Ver productos</button>
      <a class="btn" style="background:transparent;color:white;border:2px solid rgba(255,255,255,0.14);padding:10px 16px;border-radius:8px;text-decoration:none" href="#recetas">Ver recetas</a>
    </div>
  </div>

  <div class="hero-right">
    <!-- imagen hero: reemplaza por tu imagen real (hero.jpg) -->
    <img src="hero.jpg" alt="Almendras y producto ALMORA">
    <p style="font-size:13px;color:var(--muted);margin-top:8px">Artesanal • Sin gluten • Calidad premium</p>
  </div>
</section>

<!-- PRODUCTOS -->
<section class="section" id="productos">
  <h2 style="text-align:center">Nuestros Productos</h2>
  <div class="cards" id="productList" style="margin-top:18px">

    <!-- Productos (se llenan dinámicamente por JS) -->

  </div>
</section>

<!-- RECETAS -->
<section class="section" id="recetas">
  <h2 style="text-align:center">Recetas Semanales</h2>
  <div class="cards" style="margin-top:18px">
    <article class="product slideLeft">
      <h3>Galletas de Almendra</h3>
      <p class="muted">Rinde 12 galletas — fáciles y crujientes.</p>
      <ul style="margin-top:8px">
        <li>1 taza de harina de almendra ALMORA</li>
        <li>1 huevo</li>
        <li>3 cucharadas de miel</li>
      </ul>
      <div style="margin-top:10px" class="priceRow">
        <small class="muted">Tiempo 20 min</small>
        <span class="price">Fácil</span>
      </div>
    </article>

    <article class="product slideLeft">
      <h3>Hotcakes de Almendra</h3>
      <p class="muted">Espesos y esponjosos, perfectos para el desayuno.</p>
      <div style="margin-top:10px" class="priceRow">
        <small class="muted">Tiempo 15 min</small>
        <span class="price">Fácil</span>
      </div>
    </article>

    <article class="product slideLeft">
      <h3>Pan Keto de Almendra</h3>
      <p class="muted">Bajo en carbohidratos, ideal para dietas saludables.</p>
      <div style="margin-top:10px" class="priceRow">
        <small class="muted">Tiempo 50 min</small>
        <span class="price">Intermedio</span>
      </div>
    </article>
  </div>
</section>

<!-- COMENTARIOS -->
<section class="section" id="comentarios">
  <h2 style="text-align:center">Comentarios</h2>

  <div class="comentarios" id="reviews">
    <!-- reviews cargadas por JS -->
  </div>

  <div style="max-width:720px;margin:20px auto;">
    <h4>Deja tu comentario</h4>
    <form id="reviewForm">
      <input type="text" id="reviewName" placeholder="Tu nombre" required style="padding:10px;border-radius:8px;border:1px solid #e8e2d7;width:100%;margin-bottom:10px">
      <textarea id="reviewText" placeholder="Tu comentario..." required style="padding:10px;border-radius:8px;border:1px solid #e8e2d7;width:100%;height:100px"></textarea>
      <div style="display:flex;gap:8px;justify-content:flex-end">
        <button class="btn" type="submit">Enviar comentario</button>
      </div>
    </form>
  </div>
</section>

<!-- FAQ -->
<section class="section" id="faq">
  <h2 style="text-align:center">Preguntas frecuentes</h2>
  <div class="faq" style="margin-top:18px">
    <div class="faq-item" onclick="toggleFAQ(this)">
      <h4>¿Es libre de gluten?</h4>
      <p>Sí, nuestra harina de almendra no contiene gluten y es apta para personas con sensibilidad.</p>
    </div>
    <div class="faq-item" onclick="toggleFAQ(this)">
      <h4>¿Puedo usarla en panadería tradicional?</h4>
      <p>Sí, aunque para masas largas se recomienda mezclar con otras harinas o usar recetas adaptadas.</p>
    </div>
    <div class="faq-item" onclick="toggleFAQ(this)">
      <h4>¿Cómo conservo el producto?</h4>
      <p>Guarda en un lugar fresco y seco. En refrigeración dura más tiempo y se mantiene fresca.</p>
    </div>
  </div>
</section>

<!-- CART PANEL -->
<div id="cartPanel" class="cart-panel" aria-hidden="true" role="dialog" aria-label="Carrito de compras">
  <div class="cart-header">
    <strong>Tu carrito</strong>
    <button onclick="toggleCart()" aria-label="Cerrar carrito" style="background:transparent;border:0;cursor:pointer;font-size:18px">✕</button>
  </div>
  <div class="cart-items" id="cartItems">
    <!-- items -->
  </div>
  <div class="cart-footer">
    <div>
      <div style="font-size:13px;color:var(--muted)">Total</div>
      <div style="font-weight:800" id="cartTotal">$0.00</div>
    </div>
    <div>
      <button class="btn" onclick="checkout()">Pagar</button>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer style="margin-top:36px;padding:26px 20px;text-align:center;background:linear-gradient(180deg,var(--green-dark),var(--green-mid));color:white">
  <div style="display:flex;align-items:center;justify-content:center;gap:12px;margin-bottom:8px">
    <img src="almora-logo.png" alt="ALMORA logo" style="width:46px;height:46px;object-fit:contain;border-radius:6px">
    <div style="text-align:left">
      <div style="font-weight:700">ALMORA</div>
      <div style="font-size:13px;color:rgba(255,255,255,0.85)">Harina de almendra • Calidad artesanal</div>
    </div>
  </div>
  <div style="font-size:13px;color:rgba(255,255,255,0.85)">© <span id="year"></span> ALMORA • Hecho con amor</div>
</footer>

<script>
/* ====== Datos de producto (puedes cambiarlos) ====== */
const PRODUCTS = [
  {
    id: 'almora-1',
    title: 'Harina de Almendra ALMORA 500g',
    price: 8.90,
    img: 'paquete1.jpg',
    desc: 'Harina 100% almendra, ideal para repostería y cocina saludable.'
  },
  {
    id: 'almora-2',
    title: 'Harina Fina Premium 1kg',
    price: 15.50,
    img: 'paquete2.jpg',
    desc: 'Textura extra fina para postres gourmet.'
  },
  {
    id: 'almora-3',
    title: 'Mix para Galletas ALMORA',
    price: 6.25,
    img: 'paquete3.jpg',
    desc: 'Mezcla lista para preparar galletas en minutos.'
  }
];

/* ====== Render de productos ====== */
const productList = document.getElementById('productList');
function renderProducts(){
  PRODUCTS.forEach(p=>{
    const el = document.createElement('article');
    el.className = 'product fadeUp';
    el.innerHTML = `
      <img loading="lazy" src="${p.img}" alt="${p.title}">
      <h3>${p.title}</h3>
      <p style="color:var(--muted)">${p.desc}</p>
      <div class="priceRow">
        <div style="display:flex;gap:8px;align-items:center">
          <div style="font-weight:700;color:var(--green-mid)">$${p.price.toFixed(2)}</div>
        </div>
        <div>
          <button class="btn" onclick="addToCart('${p.id}')">Añadir</button>
        </div>
      </div>
    `;
    productList.appendChild(el);
  });
}
renderProducts();

/* ====== Carrito (local) ====== */
let CART = []; // {id, qty}
const cartPanel = document.getElementById('cartPanel');
const cartItemsEl = document.getElementById('cartItems');
const cartCountEl = document.getElementById('cartCount');
const cartTotalEl = document.getElementById('cartTotal');
const openCartBtn = document.getElementById('openCartBtn');

function saveCart(){ localStorage.setItem('almora_cart', JSON.stringify(CART)); }
function loadCart(){ const raw = localStorage.getItem('almora_cart'); if(raw) CART = JSON.parse(raw); else CART = []; updateCartUI(); }
loadCart();

function findProduct(id){ return PRODUCTS.find(p => p.id === id); }

function addToCart(id){
  const item = CART.find(i=>i.id===id);
  if(item) item.qty++;
  else CART.push({id, qty:1});
  saveCart();
  updateCartUI();
  // animación pequeña
  openCartBtn.animate([{transform:'scale(1)'},{transform:'scale(1.06)'},{transform:'scale(1)'}],{duration:260});
}

function removeFromCart(id){
  CART = CART.filter(i=>i.id!==id);
  saveCart();
  updateCartUI();
}

function changeQty(id, delta){
  const item = CART.find(i=>i.id===id);
  if(!item) return;
  item.qty += delta;
  if(item.qty < 1) removeFromCart(id);
  saveCart();
  updateCartUI();
}

function cartTotal(){
  let t = 0;
  CART.forEach(i=>{
    const p = findProduct(i.id);
    if(p) t += p.price * i.qty;
  });
  return t;
}

function updateCartUI(){
  // contador
  const totalCount = CART.reduce((s,i)=>s+i.qty,0);
  cartCountEl.textContent = totalCount;

  // items
  cartItemsEl.innerHTML = '';
  if(CART.length === 0){
    cartItemsEl.innerHTML = '<div style="padding:18px;color:var(--muted)">Tu carrito está vacío.</div>';
  } else {
    CART.forEach(i=>{
      const p = findProduct(i.id);
      const itemEl = document.createElement('div');
      itemEl.className = 'cart-item';
      itemEl.innerHTML = `
        <img src="${p.img}" alt="${p.title}">
        <div style="flex:1">
          <div style="font-weight:700">${p.title}</div>
          <div style="color:var(--muted);font-size:13px">$${p.price.toFixed(2)} x ${i.qty} = <strong>$${(p.price*i.qty).toFixed(2)}</strong></div>
          <div style="margin-top:8px" class="qty">
            <button onclick="changeQty('${i.id}', -1)" aria-label="Disminuir">−</button>
            <div style="padding:6px;border-radius:6px;border:1px solid #f1efe8;background:#fff">${i.qty}</div>
            <button onclick="changeQty('${i.id}', 1)" aria-label="Aumentar">+</button>
            <button style="margin-left:12px;background:transparent;border:0;color:#c24;cursor:pointer" onclick="removeFromCart('${i.id}')">Eliminar</button>
          </div>
        </div>
      `;
      cartItemsEl.appendChild(itemEl);
    });
  }
  cartTotalEl.textContent = '$' + cartTotal().toFixed(2);
}

/* ====== Toggle carrito ====== */
function toggleCart(){
  const open = cartPanel.classList.toggle('open');
  cartPanel.setAttribute('aria-hidden', (!open).toString());
}
openCartBtn.addEventListener('click', ()=>{ toggleCart(); updateCartUI(); });

/* ====== Checkout (simulado) ====== */
function checkout(){
  if(CART.length === 0){
    alert('Tu carrito está vacío.');
    return;
  }
  // simulamos proceso rapido
  const total = cartTotal().toFixed(2);
  if(confirm('Pagar $' + total + ' — Simular pago?')){
    // limpiar carrito
    CART = [];
    saveCart();
    updateCartUI();
    alert('¡Gracias! Pago simulado completado.');
    toggleCart();
  }
}

/* ====== FAQ toggle ====== */
function toggleFAQ(el){
  const p = el.querySelector('p');
  if(!p) return;
  p.style.display = p.style.display === 'block' ? 'none' : 'block';
}

/* ====== Comentarios locales (simulado) ====== */
const reviewsEl = document.getElementById('reviews');
const reviewForm = document.getElementById('reviewForm');
function loadReviews(){
  const data = localStorage.getItem('almora_reviews');
  let arr = data ? JSON.parse(data) : [
    {name:'Sofía R.', text:'La mejor harina de almendra que he probado.'},
    {name:'Daniel M.', text:'Perfecta para mis recetas keto. 10/10.'}
  ];
  reviewsEl.innerHTML = '';
  arr.forEach(r=>{
    const d = document.createElement('div');
    d.className = 'coment';
    d.innerHTML = `<strong>${r.name}</strong><p style="color:var(--muted);margin-top:6px">${r.text}</p>`;
    reviewsEl.appendChild(d);
  });
}
loadReviews();
reviewForm.addEventListener('submit', (e)=>{
  e.preventDefault();
  const name = document.getElementById('reviewName').value.trim();
  const txt = document.getElementById('reviewText').value.trim();
  if(!name || !txt) return alert('Completa tu nombre y comentario.');
  const data = localStorage.getItem('almora_reviews');
  const arr = data ? JSON.parse(data) : [];
  arr.unshift({name, text:txt});
  localStorage.setItem('almora_reviews', JSON.stringify(arr));
  reviewForm.reset();
  loadReviews();
});

/* ====== Inicialización final ====== */
document.getElementById('year').textContent = new Date().getFullYear();

/* mejora: arrastrar logo animado pequeño al entrar (solo estética) */
document.getElementById('brandLogo').addEventListener('mouseenter', (e)=>{
  e.currentTarget.animate([{transform:'translateY(0)'},{transform:'translateY(-6px)'},{transform:'translateY(0)'}],{duration:480});
});

</script>
</body>
</html>

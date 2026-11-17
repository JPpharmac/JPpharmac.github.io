<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Your Shop</title>
<meta name="description" content="Your shop description goes here.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Instrument+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --paper:#F2F5F4; --surface:#FFFFFF; --ink:#18282D; --muted:#5B6B6F;
  --line:#D3DBD9; --accent:#0E6B6B; --accent-ink:#FFFFFF;
  --font:"Instrument Sans",system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;
}
@media (prefers-color-scheme:dark){
  :root{--paper:#101A1D;--surface:#172429;--ink:#E6EEEC;--muted:#98AAAD;--line:#2A3A3F;--accent:#4FC3BD;--accent-ink:#0B1517}
}
*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{margin:0;background:var(--paper);color:var(--ink);font:400 1rem/1.55 var(--font)}
a{color:inherit}
button{font:inherit;cursor:pointer}
:focus-visible{outline:3px solid var(--accent);outline-offset:2px}
.wrap{max-width:1080px;margin:0 auto;padding:0 20px}

header{border-bottom:1px solid var(--line);background:var(--paper);position:sticky;top:0;z-index:5}
header .wrap{display:flex;align-items:center;gap:24px;height:64px}
.brand{font-weight:700;font-size:1.2rem;letter-spacing:-.01em;text-decoration:none;margin-right:auto}
nav{display:flex;gap:20px}
nav a{text-decoration:none;color:var(--muted);font-weight:500}
nav a:hover{color:var(--ink)}
.cart-btn{border:1px solid var(--ink);background:transparent;color:var(--ink);padding:8px 14px;border-radius:6px;font-weight:600}
.cart-btn:hover{background:var(--ink);color:var(--paper)}

.hero{padding:72px 0 48px}
.hero h1{font-size:clamp(2.2rem,6vw,4rem);line-height:1.04;letter-spacing:-.03em;margin:0 0 16px;max-width:14ch}
.hero p{color:var(--muted);max-width:46ch;margin:0 0 24px;font-size:1.1rem}
.btn{display:inline-block;background:var(--accent);color:var(--accent-ink);border:0;padding:12px 20px;border-radius:6px;font-weight:600;text-decoration:none}
.btn:hover{filter:brightness(1.08)}

section{padding:40px 0}
h2{font-size:1.5rem;letter-spacing:-.02em;margin:0 0 24px}
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(230px,1fr));gap:24px}
.card{background:var(--surface);border:1px solid var(--line);border-radius:8px;overflow:hidden;display:flex;flex-direction:column}
.thumb{aspect-ratio:4/3;display:grid;place-items:center;font-size:3rem;font-weight:700;color:var(--accent-ink);background:var(--accent)}
.card-body{padding:16px;display:flex;flex-direction:column;gap:6px;flex:1}
.card h3{margin:0;font-size:1.05rem}
.card p{margin:0;color:var(--muted);font-size:.95rem;flex:1}
.price{font-weight:700}
.card .btn{width:100%;margin-top:10px}

.about p{max-width:60ch;color:var(--muted)}
footer{border-top:1px solid var(--line);padding:28px 0;color:var(--muted);font-size:.95rem}

/* Cart drawer */
.scrim{position:fixed;inset:0;background:rgba(0,0,0,.4);opacity:0;pointer-events:none;transition:opacity .2s;z-index:9}
.drawer{position:fixed;top:0;right:0;bottom:0;width:min(400px,100%);background:var(--surface);border-left:1px solid var(--line);transform:translateX(100%);transition:transform .25s;z-index:10;display:flex;flex-direction:column}
body.cart-open .scrim{opacity:1;pointer-events:auto}
body.cart-open .drawer{transform:none}
.drawer-head{display:flex;justify-content:space-between;align-items:center;padding:16px 20px;border-bottom:1px solid var(--line)}
.drawer-head h2{margin:0;font-size:1.2rem}
.icon-btn{background:none;border:0;color:var(--ink);font-size:1.5rem;line-height:1;padding:4px 8px}
.items{flex:1;overflow:auto;padding:8px 20px}
.empty{color:var(--muted);padding:24px 0}
.item{display:flex;justify-content:space-between;gap:12px;padding:12px 0;border-bottom:1px solid var(--line)}
.item small{display:block;color:var(--muted)}
.qty{display:flex;align-items:center;gap:8px;margin-top:6px}
.qty button{width:28px;height:28px;border:1px solid var(--line);background:var(--paper);color:var(--ink);border-radius:4px}
.remove{background:none;border:0;color:var(--muted);text-decoration:underline;padding:0;font-size:.9rem}
.drawer-foot{padding:16px 20px;border-top:1px solid var(--line)}
.total{display:flex;justify-content:space-between;font-weight:700;margin-bottom:12px}
.drawer-foot .btn{width:100%}
.note{color:var(--muted);font-size:.9rem;margin:10px 0 0;min-height:1.4em}

@media (prefers-reduced-motion:reduce){*{transition:none!important;scroll-behavior:auto!important}}
@media (max-width:560px){nav{display:none}.hero{padding-top:48px}}
</style>
</head>
<body>

<header>
  <div class="wrap">
    <a class="brand" href="#top">Your Shop</a>
    <nav aria-label="Main">
      <a href="#products">Products</a>
      <a href="#about">About</a>
      <a href="#contact">Contact</a>
    </nav>
    <button class="cart-btn" id="open-cart" aria-label="Open cart">Cart (<span id="cart-count">0</span>)</button>
  </div>
</header>

<main id="top">
  <div class="wrap hero">
    <h1>Headline about what you sell</h1>
    <p>One sentence on who the products are for and why they’re worth buying.</p>
    <a class="btn" href="#products">Shop products</a>
  </div>

  <section id="products">
    <div class="wrap">
      <h2>Products</h2>
      <div class="grid" id="product-grid"></div>
    </div>
  </section>

  <section id="about" class="about">
    <div class="wrap">
      <h2>About</h2>
      <p>Tell customers who you are, where the products come from, and how orders are shipped.</p>
    </div>
  </section>
</main>

<footer id="contact">
  <div class="wrap">
    <p>Questions? Email <a href="mailto:you@example.com">you@example.com</a></p>
    <p>© <span id="year"></span> Your Shop</p>
  </div>
</footer>

<div class="scrim" id="scrim"></div>
<aside class="drawer" id="drawer" aria-label="Cart" aria-hidden="true">
  <div class="drawer-head">
    <h2>Your cart</h2>
    <button class="icon-btn" id="close-cart" aria-label="Close cart">&times;</button>
  </div>
  <div class="items" id="cart-items"></div>
  <div class="drawer-foot">
    <div class="total"><span>Total</span><span id="cart-total">$0.00</span></div>
    <button class="btn" id="checkout">Check out</button>
    <p class="note" id="note" role="status"></p>
  </div>
</aside>

<script>
/* ===== EDIT HERE: your products =====
   price is in dollars. Add as many as you like.
   Later you can add an image (e.g. image: "img/mug.jpg")
   and a payment link (e.g. buyUrl: "https://buy.stripe.com/...") */
const PRODUCTS = [
  { id: "p1", name: "Product one",   description: "Short description of this product.", price: 24 },
  { id: "p2", name: "Product two",   description: "Short description of this product.", price: 38 },
  { id: "p3", name: "Product three", description: "Short description of this product.", price: 15 },
  { id: "p4", name: "Product four",  description: "Short description of this product.", price: 62 }
];
const CURRENCY = "USD";
/* ===================================== */

const money = n => new Intl.NumberFormat(undefined, { style: "currency", currency: CURRENCY }).format(n);
const $ = id => document.getElementById(id);
let cart = {};

try { cart = JSON.parse(localStorage.getItem("cart") || "{}"); } catch (e) { cart = {}; }
const save = () => { try { localStorage.setItem("cart", JSON.stringify(cart)); } catch (e) {} };

function renderProducts() {
  $("product-grid").innerHTML = PRODUCTS.map(p => `
    <article class="card">
      ${p.image
        ? `<img class="thumb" src="${p.image}" alt="${p.name}">`
        : `<div class="thumb" aria-hidden="true">${p.name.charAt(0)}</div>`}
      <div class="card-body">
        <h3>${p.name}</h3>
        <p>${p.description}</p>
        <span class="price">${money(p.price)}</span>
        <button class="btn" data-add="${p.id}">Add to cart</button>
      </div>
    </article>`).join("");
}

function renderCart() {
  const lines = Object.entries(cart)
    .map(([id, qty]) => ({ p: PRODUCTS.find(x => x.id === id), qty }))
    .filter(l => l.p);
  const count = lines.reduce((s, l) => s + l.qty, 0);
  const total = lines.reduce((s, l) => s + l.qty * l.p.price, 0);
  $("cart-count").textContent = count;
  $("cart-total").textContent = money(total);
  $("checkout").disabled = count === 0;
  $("cart-items").innerHTML = lines.length
    ? lines.map(({ p, qty }) => `
      <div class="item">
        <div>
          <strong>${p.name}</strong>
          <small>${money(p.price)} each</small>
          <div class="qty">
            <button data-dec="${p.id}" aria-label="Decrease quantity of ${p.name}">&minus;</button>
            <span>${qty}</span>
            <button data-inc="${p.id}" aria-label="Increase quantity of ${p.name}">+</button>
          </div>
        </div>
        <div style="text-align:right">
          <div>${money(p.price * qty)}</div>
          <button class="remove" data-remove="${p.id}">Remove</button>
        </div>
      </div>`).join("")
    : `<p class="empty">Your cart is empty. Add a product to get started.</p>`;
}

function change(id, delta) {
  cart[id] = (cart[id] || 0) + delta;
  if (cart[id] <= 0) delete cart[id];
  save(); renderCart();
}

function setOpen(open) {
  document.body.classList.toggle("cart-open", open);
  $("drawer").setAttribute("aria-hidden", String(!open));
  if (open) $("close-cart").focus(); else $("open-cart").focus();
}

document.addEventListener("click", e => {
  const t = e.target;
  if (t.dataset.add) { change(t.dataset.add, 1); setOpen(true); }
  if (t.dataset.inc) change(t.dataset.inc, 1);
  if (t.dataset.dec) change(t.dataset.dec, -1);
  if (t.dataset.remove) { delete cart[t.dataset.remove]; save(); renderCart(); }
});
$("open-cart").onclick = () => setOpen(true);
$("close-cart").onclick = () => setOpen(false);
$("scrim").onclick = () => setOpen(false);
document.addEventListener("keydown", e => { if (e.key === "Escape") setOpen(false); });

/* Checkout is a placeholder. Connect a payment provider here later
   (e.g. Stripe Payment Links or Checkout). */
$("checkout").onclick = () => {
  $("note").textContent = "Checkout isn’t connected yet. Payments will be added here.";
};

$("year").textContent = new Date().getFullYear();
renderProducts();
renderCart();
</script>
</body>
</html>

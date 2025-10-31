# https://onlyfans.com/
<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>GlowFans — Plateforme créateurs</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <header class="top">
    <div class="brand">GlowFans</div>
    <nav class="top-nav">
      <a href="index.html">Accueil</a>
      <a href="explore.html">Explorer</a>
      <a href="#" id="openAuth">Se connecter</a>
    </nav>
  </header>

  <main class="landing">
    <section class="hero">
      <div class="hero-txt">
        <h1>Abonne-toi à tes créateurs favoris</h1>
        <p>Publie du contenu, crée des abonnements, échange avec ta communauté.</p>
        <div class="cta-row">
          <a class="btn btn-primary" href="app.html">Accéder à l’app</a>
          <a class="btn btn-ghost" href="explore.html">Explorer les créateurs</a>
        </div>
      </div>
      <div class="hero-card">
        <div class="card">
          <div class="card-head">
            <div class="avatar"></div>
            <div>
              <div class="name">Mila Studio</div>
              <div class="sub">@mila • Créatrice</div>
            </div>
            <button class="btn btn-mini">S’abonner</button>
          </div>
          <div class="card-media skel"></div>
          <div class="card-actions">
            <button>❤️ 1,2k</button>
            <button>💬 183</button>
            <button>↗️ Partager</button>
          </div>
        </div>
      </div>
    </section>

    <section class="features">
      <div class="feat">
        <h3>Abonnements</h3>
        <p>Crée des niveaux d’accès et monétise ton audience.</p>
      </div>
      <div class="feat">
        <h3>Messagerie</h3>
        <p>Échange en privé avec tes abonnés fidèles.</p>
      </div>
      <div class="feat">
        <h3>Analytique</h3>
        <p>Suis tes revenus et ta croissance en temps réel.</p>
      </div>
    </section>
  </main>

  <div class="modal" id="authModal" hidden>
    <div class="modal-body">
      <h2>Connexion</h2>
      <input id="email" type="email" placeholder="Email" />
      <input id="password" type="password" placeholder="Mot de passe" />
      <button class="btn btn-primary" id="loginBtn">Se connecter</button>
      <button class="btn btn-ghost" id="closeAuth">Fermer</button>
      <small class="muted">Démo statique — aucune donnée réelle n’est envoyée.</small>
    </div>
  </div>

  <footer class="foot">
    © 2025 GlowFans — Démo UI. Aucun lien avec des marques tierces.
  </footer>

  <script src="app.js"></script>
</body>
</html>
<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Explorer — GlowFans</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
<header class="top">
  <div class="brand">GlowFans</div>
  <nav class="top-nav">
    <a href="index.html">Accueil</a>
    <a class="active" href="explore.html">Explorer</a>
    <a href="app.html">App</a>
  </nav>
</header>

<main class="explore">
  <h1>Découvrir des créateurs</h1>
  <div id="grid" class="grid"></div>
</main>

<footer class="foot">© 2025 GlowFans</footer>
<script src="app.js"></script>
</body>
</html>
<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>App — GlowFans</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body class="app-shell">
  <aside class="sidebar">
    <div class="brand big">GlowFans</div>
    <nav class="side-links">
      <a class="active" href="app.html">Fil</a>
      <a href="#">Messages</a>
      <a href="#">Abonnements</a>
      <a href="#">Statistiques</a>
      <a href="#">Paramètres</a>
    </nav>
    <div class="side-foot">
      <button id="logoutBtn" class="btn btn-ghost">Déconnexion</button>
    </div>
  </aside>

  <main class="feed">
    <div class="composer card">
      <textarea placeholder="Publier une mise à jour… (démo)"></textarea>
      <div class="right">
        <button class="btn btn-ghost">📎 Média</button>
        <button class="btn btn-primary">Publier</button>
      </div>
    </div>

    <div id="feed"></div>
  </main>

  <section class="rightbar">
    <div class="card price-card">
      <h3>Ton abonnement</h3>
      <div class="price"><span id="currency">€</span><span id="price">9.99</span> / mois</div>
      <button class="btn btn-primary">S’abonner</button>
      <small class="muted">Démo — configure dans <code>data.json</code>.</small>
    </div>
    <div class="card">
      <h3>Créateurs populaires</h3>
      <ul id="popular"></ul>
    </div>
  </section>

  <script src="app.js"></script>
</body>
</html>
:root{
  --bg:#0b0d10;          /* fond app */
  --bg-soft:#f7f9fb;     /* fond landing */
  --card:#ffffff;
  --ink:#141619;
  --ink-2:#5b6672;
  --accent:#27bcd4;      /* bleu-vert distinct (pas le bleu OF) */
  --stroke:#e6ebf0;
  --radius:14px;
}
*{box-sizing:border-box}
html,body{margin:0;padding:0;font-family:Inter,Segoe UI,system-ui,Arial,sans-serif;color:var(--ink);}

/* header */
.top{position:sticky;top:0;z-index:10;background:#fff;border-bottom:1px solid var(--stroke);
     display:flex;align-items:center;justify-content:space-between;padding:12px 20px}
.brand{font-weight:800;letter-spacing:.2px}
.brand.big{font-size:22px}
.top-nav a{margin:0 8px;text-decoration:none;color:var(--ink-2)}
.top-nav a.active,.top-nav a:hover{color:var(--ink)}

/* landing */
.landing{background:linear-gradient(180deg,var(--bg-soft),#fff)}
.hero{max-width:1100px;margin:40px auto;display:grid;grid-template-columns:1.2fr .8fr;gap:28px;align-items:center;padding:0 16px}
.hero h1{font-size:44px;margin:0 0 10px}
.hero p{color:var(--ink-2);margin:0 0 16px}
.cta-row{display:flex;gap:12px}
.btn{border:1px solid var(--stroke);padding:10px 16px;border-radius:999px;background:#fff;cursor:pointer}
.btn:hover{transform:translateY(-1px)}
.btn-primary{background:var(--accent);color:#fff;border-color:transparent}
.btn-ghost{background:#fff}
.btn-mini{padding:6px 10px}

.card{background:var(--card);border:1px solid var(--stroke);border-radius:var(--radius);overflow:hidden}
.card-head{display:flex;gap:12px;align-items:center;padding:12px;border-bottom:1px solid var(--stroke)}
.card-media{height:220px;background:#eef3f6}
.skel{background:linear-gradient(90deg,#eef3f6,#f7fafc,#eef3f6);animation:sh 1.8s infinite}
@keyframes sh{0%{background-position:-200px 0}100%{background-position:200px 0}}
.avatar{width:38px;height:38px;border-radius:50%;background:#cde7ee}
.name{font-weight:700}
.sub{font-size:12px;color:var(--ink-2)}
.card-actions{display:flex;gap:8px;padding:10px;border-top:1px solid var(--stroke)}
.features{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;max-width:1100px;margin:10px auto 80px;padding:0 16px}
.feat{background:#fff;border:1px solid var(--stroke);border-radius:12px;padding:16px}
.foot{padding:28px;text-align:center;color:var(--ink-2);border-top:1px solid var(--stroke);background:#fff;margin-top:40px}

/* modal */
.modal{position:fixed;inset:0;display:grid;place-items:center;background:rgba(10,13,16,.45);backdrop-filter:blur(2px)}
.modal-body{background:#fff;border:1px solid var(--stroke);border-radius:16px;padding:20px;min-width:320px;display:flex;flex-direction:column;gap:10px}
.modal[hidden]{display:none}
input{padding:10px 12px;border:1px solid var(--stroke);border-radius:10px}
.muted{color:var(--ink-2);font-size:12px}

/* explore */
.explore{max-width:1100px;margin:24px auto;padding:0 16px}
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:16px}
.creator{background:#fff;border:1px solid var(--stroke);border-radius:14px;overflow:hidden}
.creator .cover{height:120px;background:#eaf5f7}
.creator .meta{display:flex;gap:10px;align-items:center;padding:12px}
.creator .meta .avatar{width:44px;height:44px;background:#cde7ee}

/* app shell */
.app-shell{background:var(--bg);display:grid;grid-template-columns:260px minmax(0,1fr) 360px;gap:18px}
.sidebar{position:sticky;top:0;height:100vh;background:#0f1216;color:#c9d2db;padding:18px;border-right:1px solid #13181e}
.side-links{display:flex;flex-direction:column;gap:8px;margin-top:12px}
.side-links a{color:#c9d2db;text-decoration:none;padding:10px 12px;border-radius:8px}
.side-links a:hover,.side-links a.active{background:#141a20;color:#fff}
.side-foot{position:absolute;bottom:16px;left:18px;right:18px}

.feed{padding:22px 0 32px}
.feed .card{margin:0 12px 16px;border-radius:16px}
.composer{display:flex;flex-direction:column;gap:10px;padding:12px}
.composer textarea{min-height:80px;border:1px dashed var(--stroke);border-radius:12px;padding:10px;resize:vertical}

.rightbar{position:sticky;top:0;height:100vh;padding:22px 18px 32px;border-left:1px solid #13181e;background:#0f1216;color:#c9d2db}
.rightbar .card{background:#11161c;border:1px solid #1a2028;color:#e9f1f7}
.price-card .price{font-size:26px;font-weight:800;margin:10px 0}

/* post card */
.post .card-head{background:#fff}
.post .media{height:320px;background:#e5f3f6}
.post .body{padding:12px}
.post .actions{display:flex;gap:10px;padding:10px;border-top:1px solid var(--stroke);background:#fff}

/* responsive */
@media (max-width:1100px){
  .app-shell{grid-template-columns:70px 1fr}
  .rightbar{display:none}
  .brand.big{display:none}
  .side-links a{padding:10px;text-align:center}
}
@media (max-width:860px){
  .hero{grid-template-columns:1fr}
  .features{grid-template-columns:1fr}
}
{
  "currency": "€",
  "price": 9.99,
  "popular": [
    {"name": "Mila Studio", "handle": "@mila"},
    {"name": "Kai Motion", "handle": "@kaim"},
    {"name": "Lia Art", "handle": "@lia"}
  ],
  "creators": [
    {"name":"Mila Studio","handle":"@mila"},
    {"name":"Kai Motion","handle":"@kaim"},
    {"name":"Zoe Craft","handle":"@zoe"},
    {"name":"Lia Art","handle":"@lia"},
    {"name":"Rex Fit","handle":"@rex"}
  ],
  "posts": [
    {"author":"Mila Studio","handle":"@mila","likes":1200,"comments":183,"text":"Nouveau set photo 💡"},
    {"author":"Kai Motion","handle":"@kaim","likes":830,"comments":92,"text":"Making-of du clip 🎬"},
    {"author":"Zoe Craft","handle":"@zoe","likes":510,"comments":41,"text":"Atelier croquis ✏️"}
  ]
}
// Modal auth (landing)
const openAuth = document.getElementById('openAuth');
const authModal = document.getElementById('authModal');
const closeAuth = document.getElementById('closeAuth');
if (openAuth && authModal) {
  openAuth.addEventListener('click', (e)=>{ e.preventDefault(); authModal.hidden = false; });
}
if (closeAuth && authModal) {
  closeAuth.addEventListener('click', ()=> authModal.hidden = true);
}

// Fake login
const loginBtn = document.getElementById('loginBtn');
if (loginBtn) {
  loginBtn.addEventListener('click', ()=>{
    const email = document.getElementById('email').value.trim();
    if (!email) return alert('Entre un email (démo).');
    localStorage.setItem('gf_user', email);
    alert('Connecté (démo). Va sur “App”.');
    authModal.hidden = true;
  });
}

// Logout sur app
const logoutBtn = document.getElementById('logoutBtn');
if (logoutBtn) {
  logoutBtn.addEventListener('click', ()=>{
    localStorage.removeItem('gf_user');
    location.href = 'index.html';
  });
}

// Charge data.json et peuple l'UI
async function loadData(){
  try{
    const res = await fetch('data.json', {cache:'no-store'});
    const data = await res.json();

    // prix
    const priceEl = document.getElementById('price');
    const curEl = document.getElementById('currency');
    if (priceEl && curEl){ priceEl.textContent = data.price; curEl.textContent = data.currency; }

    // populaires (rightbar)
    const ul = document.getElementById('popular');
    if (ul && data.popular){
      ul.innerHTML = data.popular.map(p=>`<li>${p.name} <span class="muted">${p.handle}</span></li>`).join('');
    }

    // explore grid
    const grid = document.getElementById('grid');
    if (grid && data.creators){
      grid.innerHTML = data.creators.map(c=>`
        <div class="creator">
          <div class="cover"></div>
          <div class="meta">
            <div class="avatar"></div>
            <div style="flex:1">
              <div class="name">${c.name}</div>
              <div class="sub">${c.handle}</div>
            </div>
            <button class="btn btn-primary btn-mini">S’abonner</button>
          </div>
        </div>
      `).join('');
    }

    // feed posts
    const feed = document.getElementById('feed');
    if (feed && data.posts){
      feed.innerHTML = data.posts.map(p=>`
        <article class="card post">
          <div class="card-head">
            <div class="avatar"></div>
            <div style="flex:1">
              <div class="name">${p.author}</div>
              <div class="sub">${p.handle}</div>
            </div>
            <button class="btn btn-mini">S’abonner</button>
          </div>
          <div class="media"></div>
          <div class="body">${p.text}</div>
          <div class="actions">
            <button>❤️ ${p.likes}</button>
            <button>💬 ${p.comments}</button>
            <button>🔒 Contenu réservé</button>
          </div>
        </article>
      `).join('');
    }

  }catch(e){
    console.error(e);
  }
}
loadData();

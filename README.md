# https://onlyfans.com/
<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>CreatorHub — Dashboard Démo</title>

  <style>
    :root{
      --bg:#f4f6f8;
      --card:#ffffff;
      --accent:#0069d9;
      --muted:#6b7280;
      --radius:12px;
      --txt:#111827;
    }
    *{box-sizing:border-box}
    body{margin:0;font-family:Inter,system-ui,Arial;color:var(--txt);background:var(--bg)}
    .app-shell{display:grid;grid-template-columns:220px 1fr 320px;gap:18px;min-height:100vh;padding:18px}
    .sidebar{background:linear-gradient(180deg,#0f1724,#071227);color:#fff;padding:18px;border-radius:12px;display:flex;flex-direction:column;justify-content:space-between}
    .brand{font-weight:800;font-size:20px;margin-bottom:12px}
    .nav a{display:block;padding:10px;border-radius:8px;color:rgba(255,255,255,0.85);text-decoration:none;margin-bottom:6px}
    .nav a.active, .nav a:hover{background:rgba(255,255,255,0.06)}
    .side-foot{margin-top:14px}
    .btn{padding:8px 12px;border-radius:8px;border:1px solid rgba(0,0,0,0.06);background:#fff;cursor:pointer}
    .btn-ghost{background:transparent;color:#fff;border:1px solid rgba(255,255,255,0.08)}
    .btn-primary{background:var(--accent);color:#fff;border:0}
    .main{padding:6px}
    .main-header{display:flex;justify-content:space-between;align-items:center;gap:12px;margin-bottom:18px}
    .card{background:var(--card);padding:14px;border-radius:var(--radius);box-shadow:0 6px 18px rgba(16,24,40,0.06)}
    .balance-card{min-width:220px;text-align:center}
    .balance-label{font-size:13px;color:var(--muted)}
    .balance-amount{font-size:28px;font-weight:800;margin-top:8px}
    .muted{color:var(--muted);font-size:13px}
    .content .card{min-height:360px}
    #feed .post{padding:12px;border-bottom:1px solid #f2f4f6}
    #feed .post:last-child{border-bottom:none}
    .rightbar{padding:0}
    .rightbar .card{position:sticky;top:18px}
    .modal{position:fixed;inset:0;display:grid;place-items:center;background:rgba(2,6,23,0.45);z-index:50}
    .modal-body{width:360px}
    input[type="text"], input[type="password"], input[type="number"]{width:100%;padding:10px;border-radius:10px;border:1px solid #e6eef6;margin-top:8px}
    @media (max-width:980px){
      .app-shell{grid-template-columns:1fr;padding:12px}
      .rightbar{display:none}
    }
  </style>
</head>

<body>
  <div class="app-shell">
    <aside class="sidebar">
      <div>
        <div class="brand">CreatorHub</div>
        <nav class="nav">
          <a class="active" href="#">Dashboard</a>
          <a href="#">Messages</a>
          <a href="#">Abonnements</a>
          <a href="#">Paramètres</a>
        </nav>
      </div>
      <div class="side-foot">
        <button id="openAdmin" class="btn">Ouvrir l'admin</button>
      </div>
    </aside>

    <main class="main">
      <header class="main-header">
        <div class="welcome">
          <h2>Bonjour, Créateur</h2>
          <p class="muted">Voici un aperçu de ton compte</p>
        </div>
        <div class="account">
          <div class="balance-card card">
            <div class="balance-label">Solde disponible</div>
            <div class="balance-amount"><span id="currency">€</span><span id="balance">0.00</span></div>
            <div class="balance-actions">
              <button id="withdrawBtn" class="btn btn-ghost">Retirer</button>
            </div>
          </div>
        </div>
      </header>

      <section class="content">
        <div class="card">
          <h3>Fil d'activité</h3>
          <div id="feed"></div>
        </div>
      </section>
    </main>

    <aside class="rightbar">
      <div class="card">
        <h4>Statistiques rapides</h4>
        <ul>
          <li>Abonnés : <strong id="subs">1 234</strong></li>
          <li>Revenus ce mois : <strong id="rev">2 450€</strong></li>
        </ul>
      </div>
    </aside>
  </div>

  <!-- Admin modal -->
  <div id="adminModal" class="modal" hidden>
    <div class="modal-body card">
      <h3>Panneau Admin (démo)</h3>
      <label>Mot de passe admin :</label>
      <input id="adminPwd" type="password" placeholder="mot de passe" />
      <button id="authBtn" class="btn">Se connecter</button>

      <div id="adminPanel" hidden>
        <label>Modifier le solde (ex: 2499.99)</label>
        <input id="newBalance" type="number" step="0.01" />
        <div style="display:flex;gap:8px;margin-top:8px">
          <button id="saveBalance" class="btn btn-primary">Enregistrer</button>
          <button id="resetBtn" class="btn btn-ghost">Reset (0)</button>
        </div>
        <p class="muted">Changement stocké localement (localStorage).</p>
      </div>

      <div style="margin-top:12px">
        <button id="closeAdmin" class="btn btn-ghost">Fermer</button>
      </div>
    </div>
  </div>

  <script>
    const DEFAULT_BALANCE = 0.00;
    const ADMIN_PWD = "admin123";

    function formatMoney(n){
      return Number(n).toLocaleString('fr-FR',{minimumFractionDigits:2,maximumFractionDigits:2});
    }
    function getBalance(){
      const raw = localStorage.getItem('ch_balance');
      if(raw===null)return DEFAULT_BALANCE;
      const num=parseFloat(raw);
      return isNaN(num)?DEFAULT_BALANCE:num;
    }
    function setBalance(val){
      const num=Number(val)||0;
      localStorage.setItem('ch_balance',String(num));
      renderBalance();
    }
    function renderBalance(){
      const bal=getBalance();
      const el=document.getElementById('balance');
      if(el)el.textContent=formatMoney(bal);
    }
    function renderFeed(){
      const feed=document.getElementById('feed');
      const posts=[
        {author:'Mila Studio',text:'Nouveau set photo publié',time:'2h'},
        {author:'Kai Motion',text:'Coulisses du clip',time:'8h'},
        {author:'Zoe Craft',text:'Atelier croquis jeudi',time:'1j'}
      ];
      if(!feed)return;
      feed.innerHTML=posts.map(p=>`
        <div class="post">
          <div style="display:flex;justify-content:space-between">
            <div><strong>${p.author}</strong> <span class="muted">· ${p.time}</span></div>
          </div>
          <div style="margin-top:8px">${p.text}</div>
        </div>
      `).join('');
    }

    const adminModal=document.getElementById('adminModal');
    const openAdmin=document.getElementById('openAdmin');
    const closeAdmin=document.getElementById('closeAdmin');
    const authBtn=document.getElementById('authBtn');
    const adminPanel=document.getElementById('adminPanel');
    const adminPwd=document.getElementById('adminPwd');
    const saveBalance=document.getElementById('saveBalance');
    const newBalance=document.getElementById('newBalance');
    const resetBtn=document.getElementById('resetBtn');

    if(openAdmin)openAdmin.addEventListener('click',()=>adminModal.hidden=false);
    if(closeAdmin)closeAdmin.addEventListener('click',()=>adminModal.hidden=true);
    if(authBtn){
      authBtn.addEventListener('click',()=>{
        const val=(adminPwd.value||'').trim();
        if(val===ADMIN_PWD){
          adminPanel.hidden=false;
          adminPwd.parentElement.style.display='none';
          authBtn.style.display='none';
        }else alert('Mot de passe incorrect (démo).');
      });
    }
    if(saveBalance){
      saveBalance.addEventListener('click',()=>{
        const v=parseFloat(newBalance.value);
        if(isNaN(v)){alert('Entre un nombre.');return;}
        setBalance(v);
        alert('Solde mis à jour.');
      });
    }
    if(resetBtn){
      resetBtn.addEventListener('click',()=>{
        setBalance(0);
        alert('Solde remis à 0.');
      });
    }

    renderBalance();
    renderFeed();
  </script>
</body>
</html>

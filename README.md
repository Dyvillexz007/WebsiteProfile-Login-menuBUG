Dyvillexz X Codex
<html lang="id">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Website BEHIND Profile Login</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#0b0b0b;
    --panel:#111214;
    --muted:#9a9a9a;
    --white:#f5f5f5;
    --accent:#d9d9d9;
    --card:#161616;
    --glass: rgba(255,255,255,0.03);
  }
  *{box-sizing:border-box}
  html,body{height:100%}
  body{
    margin:0;
    font-family:Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    background:var(--bg);
    color:var(--white);
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
  }

  /* Header */
  .site-header{
    height:64px;
    display:flex;
    align-items:center;
    justify-content:space-between;
    padding:12px 20px;
    background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
    border-bottom:1px solid rgba(255,255,255,0.03);
    position:sticky;
    top:0;
    z-index:30;
  }
  .brand{display:flex;align-items:center;gap:12px}
  .logo{
    width:40px;height:40px;border-radius:50%;background:#0e0e0e;display:flex;align-items:center;justify-content:center;
    font-weight:800;color:var(--white);box-shadow:0 2px 6px rgba(0,0,0,0.6)
  }
  .hamburger{width:36px;height:36px;border-radius:6px;background:transparent;border:1px solid rgba(255,255,255,0.05);display:flex;align-items:center;justify-content:center;cursor:pointer}
  .hamburger:after{content:'≡';font-size:20px;opacity:0.9}

  /* Container */
  .container{max-width:1100px;margin:28px auto;padding:0 18px;display:block;gap:28px}

  /* Profile card */
  .profile{
    background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent);
    padding:22px;
    border-radius:10px;
    display:flex;
    gap:20px;
    align-items:center;
    border:1px solid rgba(255,255,255,0.03);
  }
  .avatar{
    width:90px;height:90px;border-radius:50%;background:#222;overflow:hidden;flex:0 0 90px;border:3px solid rgba(255,255,255,0.03)
  }
  .avatar img{width:100%;height:100%;object-fit:cover}
  .profile-info{flex:1}
  .profile-info h1{font-size:22px;margin:0 0 6px 0}
  .handle{color:var(--muted);margin-bottom:8px}
  .stats{display:flex;gap:28px;color:var(--muted);font-size:14px}
  .stats .num{font-weight:700;color:var(--white);display:block}

  /* Banner with video */
  .banner-wrap{
    margin-top:18px;
    position:relative;
    height:320px;
    border-radius:10px;
    overflow:hidden;
    background:#0e0e0e;
    border:1px solid rgba(255,255,255,0.03);
  }
  .banner-video{
    position:absolute;inset:0;width:100%;height:100%;object-fit:cover;
    filter:grayscale(20%) contrast(0.9) brightness(0.6);
  }
  .banner-overlay{
    position:absolute;inset:0;
    background:linear-gradient(180deg, rgba(0,0,0,0.15), rgba(0,0,0,0.45));
    display:flex;
    align-items:center;
    justify-content:center;
    padding:20px;
  }
  .banner-title{
    text-align:center;
    z-index:3;
  }
  .banner-title h2{
    margin:0;
    font-size:64px;
    letter-spacing:6px;
    font-weight:800;
    color:var(--white);
    text-transform:uppercase;
  }
  .banner-title p{margin-top:10px;color:var(--muted);font-size:13px}

  /* Login card */
  .login-section{margin-top:26px;display:flex;justify-content:center}
  .login-card{
    width:420px;
    background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent);
    border-radius:12px;
    padding:26px;
    border:1px solid rgba(255,255,255,0.03);
    box-shadow:0 6px 18px rgba(0,0,0,0.6);
  }
  .login-card h3{margin:0 0 12px 0;font-weight:700}
  .input{width:100%;padding:12px 14px;border-radius:8px;background:var(--card);border:1px solid rgba(255,255,255,0.03);color:var(--white);margin-bottom:12px}
  .btn{
    width:100%;
    padding:12px 14px;border-radius:10px;border:0;background:var(--accent);color:#0b0b0b;font-weight:700;cursor:pointer
  }
  .small{font-size:13px;color:var(--muted);margin-top:10px;text-align:center}

  @media (max-width:700px){
    .banner-title h2{font-size:40px}
    .profile{flex-direction:row;gap:14px;padding:16px}
    .avatar{width:72px;height:72px;flex:0 0 72px}
    .container{padding:0 14px}
    .banner-wrap{height:220px}
    .login-card{width:100%}
  }

  /* Popup menu */
  .menu-popup {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.6);
    backdrop-filter: blur(10px);
    justify-content: center;
    align-items: center;
    z-index: 999;
    animation: fadeIn 0.25s ease;
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  .menu-content {
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 18px;
    padding: 28px 34px;
    text-align: center;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
    width: 280px;
    animation: popUp 0.3s ease;
  }
  @keyframes popUp {
    from { transform: scale(0.9); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
  }

  .menu-content a {
    display: block;
    text-decoration: none;
    color: #fff;
    padding: 10px 0;
    font-size: 16px;
    font-weight: 600;
    border-radius: 8px;
    transition: all 0.2s ease;
  }
  .menu-content a:hover {
    background: rgba(255, 255, 255, 0.1);
  }

  .typing {
    border-right: 2px solid #fff;
    white-space: nowrap;
    overflow: hidden;
    width: 0;
    animation: typing 2s steps(20, end) forwards;
  }
  @keyframes typing {
    from { width: 0 }
    to { width: 100% }
  }
</style>
</head>
<body>
<header class="site-header">
  <div class="brand">
    <div class="logo">🌐</div>
    <div style="line-height:1">
      <div style="font-weight:700">DyvillexzDev</div>
      <div style="font-size:12px;color:var(--muted)">Website_Profile Login V3</div>
    </div>
  </div>
  <div style="display:flex;align-items:center;gap:12px">
    <div style="color:var(--muted);font-size:13px">Menu</div>
    <div class="hamburger" title="Menu"></div>
  </div>
</header>

<!-- Musik otomatis halaman awal -->
<audio id="bg-music" autoplay loop>
  <source src="https://c.termai.cc/a36/nU9EEY.mp3" type="audio/mpeg">
</audio>
<!-- Tombol kontrol musik -->
<div id="music-controls" style="position: fixed; bottom: 20px; right: 20px; z-index: 1000;">
  <button id="mute-btn" style="font-size: 24px; margin-right: 10px;">│▶️│</button>
</div>
<script>
  const audio = document.getElementById('bg-music');
  const muteBtn = document.getElementById('mute-btn');
  // Fitur mute/unmute
  muteBtn.addEventListener('click', function() {
    if (audio.volume > 0) {
      audio.volume = 0;
      muteBtn.textContent = '🔴OFF';
    } else {
      audio.volume = 1;
      muteBtn.textContent = '🔵ON';
    }
  });
</script>

<main class="container" id="mainPage">
  <section class="profile">
    <div class="avatar">
<img src="https://c.termai.cc/i14/n7l.jpg" alt="Foto 1" class="gambar">
    </div>
    <div class="profile-info">
      <script>
document.querySelectorAll('.gambar').forEach(img => {
  img.addEventListener('click', () => {
    const view = document.createElement('div');
    view.style.position = 'fixed';
    view.style.top = 0;
    view.style.left = 0;
    view.style.width = '100%';
    view.style.height = '100%';
    view.style.background = 'rgba(0,0,0,0.8)';
    view.style.display = 'flex';
    view.style.justifyContent = 'center';
    view.style.alignItems = 'center';
    view.style.zIndex = 9999;
    view.innerHTML = `<img src="${img.src}" style="max-width:90%; max-height:90%; border-radius:10px;">`;
    view.addEventListener('click', () => view.remove());
    document.body.appendChild(view);
  });
});
</script>
      <h1>Demox_</h1>
      <div class="handle">@dyonezerofokun</div>
      <div class="stats">
        <div><span class="num">20</span>mengikuti</div>
        <div><span class="num">57,2 rb</span>pengikut</div>
        <div><span class="num">270,7 rb</span>Suka</div>
      </div>
    </div>
  </section>

  <section class="banner-wrap">
    <video class="banner-video" id="bgVideo" autoplay muted loop playsinline preload="auto">
      <source src="https://c.termai.cc/v2/Qx9Xhlg.mp4" type="video/mp4">
    </video>
    <div class="banner-overlay">
      <div class="banner-title">
        <p>TO THE ONE WHO LEFT IT ALL</p>
        <h2>BEHIND</h2>
        <p>THEY WOULD ALL BEAR WITNESS TO THE BARE FLESH OF THE ONE WHO IS FREE</p>
      </div>
    </div>
  </section>

  <section class="login-section">
    <div class="login-card">
      <h3>Login</h3>
      <label>Nama Pengguna / Email</label>
      <input class="input" type="text" placeholder="Masukan Email/telepon">
      <label>Kata Sandi</label>
      <input class="input" type="password" placeholder="********">
      <button class="btn">Masuk</button>
      <div class="small">hubungi Developer Untuk mendapatkan akses Login —│ Dyvillexz ⧼🔰⧽</div>
    </div>
  </section>
</main>

<!-- Popup Menu -->
<div id="menuPopup" class="menu-popup">
  <div class="menu-content">
    <h3 id="popupTitle" class="typing">Opsi Menu By Demox_ ✔️</h3>
    <a href="https://github.com/Dyvillexz007" target="_blank">🎭 Developer</a>
    <a href="https://cdn.yupra.my.id/yp/l22hmjj5.html">🔰 Owner</a>
    <a href="https://wa.me/qr/" target="_blank">👤 WhatsApp</a>
    <a href=""></a>
     <h3 id="popupTitle" class="">Folow me  🖤</h3>
         <a href="https://www.tiktok.com/@dyvoidzeroone" target="_blank">Tiktok</a>
         <a href="https://www.youtube.com/@Dyvillexz" target="_blank">Youtobe</a>
         <a href="https://www.instagram.com/tauf1q_ferdi4ns_syhaputra" target="_blank">instagram</a>
        
    
  </div>
</div>

<audio id="menuSound" src="https://cdn.pixabay.com/audio/2022/03/15/audio_1b5b63b8a8.mp3"></audio>

<script>
document.addEventListener('click', function() {
  const audio = document.getElementById('bg-music');
  if (audio.paused) audio.play();
});

const popup = document.getElementById('menuPopup');
const button = document.querySelector('.hamburger');
const sound = document.getElementById('menuSound');
const popupTitle = document.getElementById('popupTitle');

button.addEventListener('click', () => {
  popup.style.display = 'flex';
  popupTitle.classList.remove('typing');
  void popupTitle.offsetWidth;
  popupTitle.classList.add('typing');
  sound.currentTime = 0;
  sound.play();
});
popup.addEventListener('click', (e) => {
  if (e.target === popup) popup.style.display = 'none';
});
</script>

<!-- ===== CEK LOGIN DENGAN VALIDASI KOSONG ===== -->
<script>
document.querySelector('.btn').addEventListener('click', function() {
  const emailInput = document.querySelectorAll('.input')[0].value.trim();
  const passwordInput = document.querySelectorAll('.input')[1].value.trim();
  const validEmail = "demox007@gmail.com";
  const validPassword = "1234567";
  let err = document.querySelector('.error-login');
  if (!err) {
    err = document.createElement('div');
    err.className = 'error-login';
    err.style.color = 'red';
    err.style.marginTop = '10px';
    err.style.textAlign = 'center';
    document.querySelector('.login-card').appendChild(err);
  }
  if (emailInput === "" || passwordInput === "") {
    err.textContent = "Masukan email/nomor dan sandi terlebih dahulu!";
    return;
  }
  if (emailInput !== validEmail || passwordInput !== validPassword) {
    err.textContent = "Email atau kata sandi salah!";
    return;
  }

  // ✅ TAMPILKAN HALAMAN DASHBOARD
  document.getElementById("mainPage").style.display = "none";
  document.getElementById("halamanLain").style.display = "flex";
});

// Fungsi logout / kembali ke login
function keluar(){
  document.getElementById("halamanLain").style.display = "none";
  document.getElementById("mainPage").style.display = "block";
}
</script>
<!-- ================= HALAMAN DASHBOARD ================= -->
<div id="halamanLain" style="display:none;flex-direction:column;align-items:center;justify-content:center;height:100vh;text-align:center;padding:20px;background:#101010;color:#eee;">

  <div class="container" style="width:100%;max-width:980px;display:flex;flex-direction:column;gap:20px;">

    <!-- FORM -->
    <div class="card" style="background:#1a1a1a;border-radius:14px;padding:20px;box-shadow:0 0 15px rgba(255,0,0,0.2);border:1px solid rgba(255,0,0,0.3);">
      <h1>DEMOX X BUG </h1>
      <p class="lead" style="color:#999;">🔰🔴🟡🔵🔰</p>

      <label>Masukkan nomor target</label>
      <input id="phone" type="text" placeholder="628****" style="width:100%;padding:10px;border-radius:10px;border:1px solid rgba(255,255,255,0.1);background:transparent;color:inherit;margin-top:6px;font-size:14px;" />

      <label>Pilih menu BUG</label>
      <select id="menuSelect" style="width:100%;padding:10px;border-radius:10px;border:1px solid rgba(255,255,255,0.1);background:transparent;color:inherit;margin-top:6px;font-size:14px;">
        <option value="Menu">pilih menu bug</option>
        <option value="fclose">fclose</option>
        <option value="forceclose">forceclose</option>
        <option value="fc-invis">fc-invis</option>
        <option value="delaymaker">delaymaker</option>
        <option value="delayinvis">delayinvis</option>
        <option value="delayip">delayip</option>
      </select>

      <label>Jumlah Bug yg mau di kirim</label>
      <input id="ownerName" type="text" placeholder="10" value="10" style="width:100%;padding:10px;border-radius:10px;border:1px solid rgba(255,255,255,0.1);background:transparent;color:inherit;margin-top:6px;font-size:14px;" />

      <label>Catatan untuk target</label>
      <textarea id="notes" rows="3" placeholder="Projeck ini masi dalam pengembangan tahap awal kemungkinan bayak kesalahan atau permasalahan tidak di ketahui oleh karena itu gunakan secara bijak" style="width:100%;padding:10px;border-radius:10px;border:1px solid rgba(255,255,255,0.1);background:transparent;color:inherit;margin-top:6px;font-size:14px;"></textarea>

      <div class="row" style="display:flex;gap:10px;margin-top:12px;">
        <button class="primary" id="simulateBtn" style="background:#ff3b3b;padding:10px 16px;border-radius:10px;border:none;color:#fff;font-weight:700;cursor:pointer;box-shadow:0 0 12px #ff3b3b;">Kirim</button>
        <button class="ghost" id="resetBtn" style="background:transparent;border:1px solid rgba(255,0,0,0.3);padding:10px 14px;border-radius:10px;color:#999;cursor:pointer;">Hentikan</button>
      </div>
    </div>

    <!-- PREVIEW -->
    <div class="card" style="background:#1a1a1a;border-radius:14px;padding:20px;box-shadow:0 0 15px rgba(255,0,0,0.2);border:1px solid rgba(255,0,0,0.3);">
      <div class="preview" style="padding:15px;border-radius:12px;background:rgba(255,0,0,0.05);min-height:180px;display:flex;flex-direction:column;gap:12px;align-items:center;justify-content:center;box-shadow:0 0 15px rgba(255,0,0,0.3);">
        <div class="video-wrap" title="Profile Video" style="width:120px;height:120px;border-radius:999px;overflow:hidden;border:5px solid rgba(255,0,0,0.4);display:flex;align-items:center;justify-content:center;box-shadow:0 0 20px rgba(255,0,0,0.6);">
          <video id="profileVideo" autoplay muted loop playsinline style="width:150%;height:150%;object-fit:cover;transform:translateX(-0%);">
            <source src="https://o.uguu.se/wFKVhDgO.mp4" type="video/mp4" />
          </video>
        </div>

        <div class="meta" style="display:flex;flex-direction:column;align-items:center;gap:5px;">
          <div class="owner" id="ownerPreview" style="font-weight:700;font-size:16px;">Demox_</div>
          <div class="tag" id="phonePreview" style="font-size:12px;color:#999;">Online</div>
        </div>

        <div class="menu-list" style="display:flex;flex-direction:column;gap:8px;margin-top:10px;">
          <div class="menu-item" style="display:flex;align-items:center;justify-content:space-between;padding:10px;border-radius:8px;background:rgba(255,0,0,0.05);cursor:pointer;border:1px solid rgba(255,0,0,0.2);"><div></div><div class="tag">Developer🎭</div></div>
          <div class="" style="display:flex;align-items:center;justify-content:space-between;padding:10px;border-radius:8px;background:rgba(255,0,0,0.05);border:1px solid rgba(255,0,0,0.2);"><div><span id="m2name"></span></div><div class="tag"></div></div>
          <div class="menu-item" style="display:flex;align-items:center;justify-content:space-between;padding:10px;border-radius:8px;background:rgba(255,0,0,0.05);border:1px solid rgba(255,0,0,0.2);"><div></div><div class="tag"></div></div>
        </div>

        <div class="result" id="resultBox" style="padding:12px;border-radius:10px;margin-top:12px;background:rgba(255,0,0,0.03);min-height:120px;color:#fdd;">
          Hasil! bug berasil terkirim di sini 
        </div>

        <footer style="margin-top:10px;font-size:12px;color:#999;">Sistem UI • Developer • By Demox X Dyvillexz</footer>
      </div>
    </div>

  </div>
</div>

<script>
const phoneInp = document.getElementById('phone');
const ownerInp = document.getElementById('ownerName');
const menuSel = document.getElementById('menuSelect');
const simulateBtn = document.getElementById('simulateBtn');
const resetBtn = document.getElementById('resetBtn');
const ownerPreview = document.getElementById('ownerPreview');
const phonePreview = document.getElementById('phonePreview');
const resultBox = document.getElementById('resultBox');
const m2name = document.getElementById('m2name');

function normalizePhone(s){
  if(!s) return '';
  s = s.trim().replace(/\s+/g,'').replace(/[^\d]/g,'');
  if(s.startsWith('0')) s='62'+s.slice(1);
  return s;
}

function showResult(lines){
  resultBox.innerHTML = '';
  lines.forEach(l=>{
    const d=document.createElement('div');
    d.textContent=l;
    resultBox.appendChild(d);
  });
}

function sleep(ms){return new Promise(r=>setTimeout(r,ms));}

simulateBtn.addEventListener('click', async()=>{
  const phone=normalizePhone(phoneInp.value);
  const owner=ownerInp.value||'—';
  const menu=menuSel.value;
  ownerPreview.textContent=owner;
  phonePreview.textContent=phone?('+'.concat(phone)):'Belum diisi';
  m2name.textContent=owner;

  if(!phone){showResult(['ERROR: Nomor tidak valid']);return;}

  showResult(['Tunggu sebentar.....']);
  await sleep(500);
  showResult([`Nomor: +${phone}`, 'menggirim BUG...']);
  await sleep(500);

  if(menu==='profileVideo'){
    showResult(['Mode: Profile Video Bergerak (Demo)','Preview video aktif','Nama Owner: '+owner]);
  } else if(menu==='displayName'){
    showResult(['Mode: Ubah Nama Owner','Nama baru ditampilkan: '+owner]);
  } else if(menu==='statusSpoof'){
    showResult(['Mode: Status Simulasi','Status mockup: "Sedang sibuk — private"']);
  } else {
    showResult(['Mode: memproses....','Bug berasil Terkirim']);
  }
});

resetBtn.addEventListener('click', ()=>{
  phoneInp.value='';
  ownerInp.value='Dyvillexz';
  menuSel.value='profileVideo';
  ownerPreview.textContent='Dyvillexz';
  phonePreview.textContent='+62 — belum diisi';
  m2name.textContent='Dyvillexz';
  resultBox.innerHTML='Siap. Masukkan nomor dan pilih menu.';
});
</script>

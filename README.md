<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>MinikPanel | Anaokulu Yönetim Paneli</title>

<style>
:root{
  --bg:#fff8ef;
  --bg2:#f7efe4;
  --card:#ffffff;
  --text:#243044;
  --muted:#6b7280;
  --line:#eadfce;
  --orange:#ff9f43;
  --blue:#4dabf7;
  --green:#51cf66;
  --purple:#9775fa;
  --pink:#f06595;
  --red:#ef4444;
  --yellow:#ffd43b;
  --dark:#1f2937;
  --shadow:0 14px 35px rgba(36,48,68,.12);
}
*{margin:0;padding:0;box-sizing:border-box}
body{
  font-family:Segoe UI,Arial,sans-serif;
  background:var(--bg);
  color:var(--text);
}
button,input,select,textarea{font-family:inherit}
button{border:0;cursor:pointer;font-weight:800}
img{width:100%;display:block}

.app{
  display:grid;
  grid-template-columns:280px 1fr;
  min-height:100vh;
}

.sidebar{
  background:linear-gradient(180deg,#fff,#fff5e7);
  border-right:1px solid var(--line);
  padding:18px;
  position:sticky;
  top:0;
  height:100vh;
  overflow:auto;
}

.logo{
  display:flex;
  align-items:center;
  gap:10px;
  font-size:23px;
  font-weight:900;
  margin-bottom:20px;
}
.logo-icon{
  width:42px;height:42px;
  border-radius:15px;
  display:grid;place-items:center;
  background:linear-gradient(135deg,var(--orange),var(--pink));
  color:white;
}
.logo span{color:var(--orange)}

.nav-btn{
  width:100%;
  display:flex;
  align-items:center;
  gap:10px;
  padding:13px 14px;
  border-radius:15px;
  margin-bottom:8px;
  background:transparent;
  color:var(--text);
  text-align:left;
}
.nav-btn:hover,.nav-btn.active{
  background:linear-gradient(90deg,rgba(255,159,67,.18),rgba(77,171,247,.14));
  color:#c05621;
}

.main{padding:18px;max-width:1250px;width:100%;margin:auto}

.topbar{
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:12px;
  margin-bottom:18px;
}
.mobile-menu{
  display:none;
  padding:10px 14px;
  border-radius:12px;
  background:var(--orange);
  color:white;
}
.demo-badge{
  background:#fff;
  border:1px solid var(--line);
  padding:10px 14px;
  border-radius:999px;
  color:var(--muted);
  font-size:14px;
}
.demo-badge b{color:var(--orange)}

.hero{
  background:
  linear-gradient(90deg,rgba(36,48,68,.85),rgba(36,48,68,.35)),
  url("https://images.unsplash.com/photo-1588072432836-e10032774350?auto=format&fit=crop&w=1500&q=80");
  background-size:cover;
  background-position:center;
  border-radius:28px;
  padding:42px;
  color:white;
  box-shadow:var(--shadow);
  margin-bottom:20px;
}
.hero h1{font-size:clamp(30px,5vw,54px);max-width:720px;line-height:1.06}
.hero p{max-width:640px;color:#fff4e6;line-height:1.7;margin-top:15px}
.hero-actions{display:flex;gap:10px;flex-wrap:wrap;margin-top:20px}

.btn{
  padding:11px 15px;
  border-radius:13px;
  color:white;
}
.btn-orange{background:var(--orange)}
.btn-blue{background:var(--blue)}
.btn-green{background:var(--green);color:#123}
.btn-purple{background:var(--purple)}
.btn-red{background:var(--red)}
.btn-dark{background:var(--dark)}

.page-title{margin-bottom:16px}
.page-title h1{font-size:30px}
.page-title p{color:var(--muted);margin-top:5px}

.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(210px,1fr));gap:15px}
.card,.panel,.stat{
  background:var(--card);
  border:1px solid var(--line);
  border-radius:22px;
  padding:18px;
  box-shadow:var(--shadow);
}
.stat{position:relative;overflow:hidden}
.stat:before{
  content:"";
  position:absolute;
  right:-25px;top:-25px;
  width:85px;height:85px;
  border-radius:50%;
  background:linear-gradient(135deg,var(--orange),var(--pink));
  opacity:.16;
}
.stat h2{font-size:28px;color:var(--orange)}
.stat p{color:var(--muted);margin-top:5px}

.card h3,.panel h3{margin-bottom:8px}
.meta{color:var(--muted);line-height:1.6;font-size:14px}

.card-top{
  display:flex;
  justify-content:space-between;
  align-items:flex-start;
  gap:10px;
}
.status{
  display:inline-block;
  padding:6px 10px;
  border-radius:999px;
  color:white;
  font-size:12px;
  font-weight:900;
  white-space:nowrap;
}
.s-green{background:var(--green);color:#123}
.s-blue{background:var(--blue)}
.s-orange{background:var(--orange)}
.s-purple{background:var(--purple)}
.s-red{background:var(--red)}
.s-pink{background:var(--pink)}

.actions{display:flex;gap:8px;flex-wrap:wrap;margin-top:14px}
.smallbtn{
  padding:8px 11px;
  border-radius:11px;
  color:white;
  font-size:13px;
}

.notice{
  background:#fff7e6;
  border:1px solid #ffd8a8;
  color:#9a5b00;
  padding:13px 15px;
  border-radius:18px;
  margin-bottom:16px;
  font-size:14px;
}

.search-row{
  display:flex;
  gap:10px;
  margin-bottom:14px;
}
.search-row input{
  width:100%;
  padding:13px;
  border:1px solid var(--line);
  border-radius:14px;
  outline:none;
}

.two{display:grid;grid-template-columns:1.2fr .8fr;gap:16px}
.table{width:100%;border-collapse:collapse}
.table th,.table td{
  text-align:left;
  padding:12px;
  border-bottom:1px solid var(--line);
  font-size:14px;
}
.table th{color:var(--muted)}

.bar-wrap{margin:14px 0}
.bar-label{display:flex;justify-content:space-between;margin-bottom:6px;font-size:14px}
.bar-bg{height:24px;background:#f1e7d9;border-radius:999px;overflow:hidden}
.bar{
  height:100%;
  line-height:24px;
  color:white;
  padding-left:10px;
  font-size:12px;
  background:linear-gradient(90deg,var(--orange),var(--pink),var(--purple));
}

.timeline{display:grid;gap:10px}
.time-item{
  background:#fff8ef;
  border:1px solid var(--line);
  padding:13px;
  border-radius:16px;
  display:flex;
  justify-content:space-between;
  gap:10px;
}

.gallery{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:12px;
}
.gallery img{
  height:190px;
  object-fit:cover;
  border-radius:18px;
  border:1px solid var(--line);
  box-shadow:var(--shadow);
}

.modal{
  display:none;
  position:fixed;
  inset:0;
  background:rgba(31,41,55,.55);
  z-index:300;
  padding:20px;
}
.modal.active{
  display:flex;
  align-items:center;
  justify-content:center;
}
.modal-box{
  width:100%;
  max-width:460px;
  background:white;
  border-radius:24px;
  padding:20px;
  box-shadow:0 20px 60px rgba(0,0,0,.25);
}
.modal-box input,.modal-box textarea{
  width:100%;
  padding:12px;
  border:1px solid var(--line);
  border-radius:14px;
  margin:8px 0 12px;
}
.toast{
  display:none;
  position:fixed;
  left:50%;
  bottom:22px;
  transform:translateX(-50%);
  background:var(--dark);
  color:white;
  padding:13px 18px;
  border-radius:14px;
  z-index:400;
}
.footer-note{text-align:center;color:var(--muted);font-size:13px;margin:25px 0}

@media(max-width:900px){
  .app{grid-template-columns:1fr}
  .sidebar{
    display:none;
    position:fixed;
    z-index:200;
    width:280px;
    left:0;top:0;
  }
  .sidebar.active{display:block}
  .mobile-menu{display:block}
  .two{grid-template-columns:1fr}
  .gallery{grid-template-columns:1fr 1fr}
  .hero{padding:28px}
}
@media(max-width:560px){
  .gallery{grid-template-columns:1fr}
  .search-row{flex-direction:column}
}
</style>
</head>

<body>

<div class="app">

<aside id="sidebar" class="sidebar">
  <div class="logo"><div class="logo-icon">🎒</div>Minik<span>Panel</span></div>

  <button class="nav-btn active" onclick="navigate('dashboard',this)">📊 Dashboard</button>
  <button class="nav-btn" onclick="navigate('students',this)">👧 Öğrenciler</button>
  <button class="nav-btn" onclick="navigate('classes',this)">🏫 Sınıflar</button>
  <button class="nav-btn" onclick="navigate('attendance',this)">📅 Devamsızlık</button>
  <button class="nav-btn" onclick="navigate('payments',this)">💳 Ödemeler</button>
  <button class="nav-btn" onclick="navigate('parents',this)">👨‍👩‍👧 Veliler</button>
  <button class="nav-btn" onclick="navigate('branches',this)">🏢 Şubeler</button>
  <button class="nav-btn" onclick="navigate('daily',this)">🌞 Günlük Akış</button>
  <button class="nav-btn" onclick="navigate('meals',this)">🍲 Yemek Listesi</button>
  <button class="nav-btn" onclick="navigate('reports',this)">📈 Raporlar</button>
  <button class="nav-btn" onclick="navigate('announcements',this)">📢 Duyurular</button>
  <button class="nav-btn" onclick="navigate('gallery',this)">🖼️ Galeri</button>
</aside>

<main class="main">
  <div class="topbar">
    <button class="mobile-menu" onclick="toggleMenu()">☰ Menü</button>
    <div class="demo-badge"><b>Demo Mod:</b> Düzenleme ve silme işlemleri kalıcı değildir.</div>
  </div>

  <div id="content"></div>
</main>

</div>

<div id="modal" class="modal">
  <div class="modal-box">
    <h2>Kaydı Düzenle</h2>
    <div class="notice">Demo modundasınız. Bu değişiklik sayfa yenilenince veya farklı bölüme geçince geri alınır.</div>
    <label>Başlık</label>
    <input id="editTitle">
    <label>Açıklama</label>
    <textarea id="editText" rows="4"></textarea>
    <div class="actions">
      <button class="smallbtn btn-green" onclick="saveEdit()">Kaydet</button>
      <button class="smallbtn btn-dark" onclick="closeModal()">Kapat</button>
    </div>
  </div>
</div>

<div id="toast" class="toast"></div>

<script>
const originalData={
students:[
{title:"Defne Yılmaz",text:"5 yaş • Minik Kalpler Sınıfı • Veli: Ayşe Yılmaz • Aidat: Ödendi",status:"Aktif",s:"s-green"},
{title:"Efe Kaya",text:"4 yaş • Neşeli Bulutlar Sınıfı • Veli: Murat Kaya • Aidat: Bekliyor",status:"Bekliyor",s:"s-orange"},
{title:"Zeynep Demir",text:"6 yaş • Güneş Çocukları Sınıfı • Veli: Elif Demir • Aidat: Ödendi",status:"Aktif",s:"s-green"},
{title:"Aras Çelik",text:"5 yaş • Yıldızlar Sınıfı • Veli: Hasan Çelik • Aidat: Gecikmiş",status:"Gecikmiş",s:"s-red"},
{title:"Ela Aydın",text:"3 yaş • Papatyalar Sınıfı • Veli: Fatma Aydın • Aidat: Ödendi",status:"Yeni",s:"s-blue"},
{title:"Mina Koç",text:"4 yaş • Bal Arıları Sınıfı • Veli: Selin Koç • Aidat: Bekliyor",status:"Takip",s:"s-purple"}
],
classes:[
{title:"Minik Kalpler Sınıfı",text:"Kapasite: 18 • Mevcut: 15 • Öğretmen: Nur Öğretmen • Doluluk: %83",status:"Uygun",s:"s-green"},
{title:"Neşeli Bulutlar Sınıfı",text:"Kapasite: 16 • Mevcut: 16 • Öğretmen: Elif Öğretmen • Doluluk: %100",status:"Dolu",s:"s-red"},
{title:"Güneş Çocukları Sınıfı",text:"Kapasite: 20 • Mevcut: 17 • Öğretmen: Derya Öğretmen • Doluluk: %85",status:"Uygun",s:"s-green"},
{title:"Yıldızlar Sınıfı",text:"Kapasite: 18 • Mevcut: 14 • Öğretmen: Merve Öğretmen • Doluluk: %78",status:"Uygun",s:"s-blue"},
{title:"Papatyalar Sınıfı",text:"Kapasite: 14 • Mevcut: 12 • Öğretmen: Sema Öğretmen • Doluluk: %86",status:"Uygun",s:"s-purple"},
{title:"Bal Arıları Sınıfı",text:"Kapasite: 16 • Mevcut: 13 • Öğretmen: Aslı Öğretmen • Doluluk: %81",status:"Uygun",s:"s-orange"}
],
attendance:[
{title:"Bugünkü Devamsızlık",text:"11 öğrenci gelmedi • 4 öğrenci geç geldi • 2 izinli kayıt var",status:"Güncel",s:"s-blue"},
{title:"Defne Yılmaz",text:"Bugün geldi • Giriş saati: 08:42 • Teslim alan: Anne",status:"Geldi",s:"s-green"},
{title:"Aras Çelik",text:"Bugün gelmedi • Veli bilgilendirildi • Sebep: Hastalık",status:"Gelmedi",s:"s-red"},
{title:"Mina Koç",text:"Geç geldi • Giriş saati: 10:15 • Not: Servis gecikmesi",status:"Geç",s:"s-orange"}
],
payments:[
{title:"Haziran Aidat Özeti",text:"Toplam tahakkuk: ₺426.000 • Tahsil edilen: ₺352.000 • Bekleyen: ₺74.000",status:"Aylık",s:"s-blue"},
{title:"Defne Yılmaz",text:"Haziran aidatı ödendi • Tutar: ₺8.500 • Ödeme: Havale",status:"Ödendi",s:"s-green"},
{title:"Efe Kaya",text:"Haziran aidatı bekliyor • Tutar: ₺8.500 • Hatırlatma gönderildi",status:"Bekliyor",s:"s-orange"},
{title:"Aras Çelik",text:"Mayıs + Haziran gecikmiş • Toplam: ₺17.000",status:"Gecikmiş",s:"s-red"},
{title:"Mina Koç",text:"Servis ücreti bekliyor • Tutar: ₺2.750",status:"Takip",s:"s-purple"}
],
parents:[
{title:"Ayşe Yılmaz",text:"Öğrenci: Defne Yılmaz • Tel: 0555 100 10 10 • Bildirim: Açık",status:"Aktif",s:"s-green"},
{title:"Murat Kaya",text:"Öğrenci: Efe Kaya • Tel: 0555 200 20 20 • Aidat hatırlatması gönderildi",status:"Takip",s:"s-orange"},
{title:"Elif Demir",text:"Öğrenci: Zeynep Demir • Tel: 0555 300 30 30 • Acil kişi: Baba",status:"Aktif",s:"s-blue"},
{title:"Hasan Çelik",text:"Öğrenci: Aras Çelik • Tel: 0555 400 40 40 • Devamsızlık bildirildi",status:"Bilgilendi",s:"s-purple"}
],
branches:[
{title:"Merkez Şube",text:"68 öğrenci • 4 sınıf • Sorumlu: Derya Hanım • Doluluk: %88",status:"Aktif",s:"s-green"},
{title:"Sahil Şube",text:"34 öğrenci • 2 sınıf • Sorumlu: Merve Hanım • Doluluk: %76",status:"Aktif",s:"s-blue"},
{title:"Bahçe Şube",text:"24 öğrenci • 2 sınıf • Sorumlu: Sema Hanım • Doluluk: %80",status:"Aktif",s:"s-purple"}
],
announcements:[
{title:"Veli Toplantısı",text:"Cuma günü saat 17:30’da sınıf öğretmenleriyle dönem değerlendirme toplantısı yapılacaktır.",status:"Yeni",s:"s-blue"},
{title:"Fotoğraf Günü",text:"Çarşamba günü sınıf fotoğraf çekimi yapılacaktır. Öğrencilerin okul formasıyla gelmesi rica olunur.",status:"Planlandı",s:"s-purple"},
{title:"Gezi Duyurusu",text:"Minik Kalpler ve Güneş Çocukları sınıfları için doğa etkinliği planlanmıştır.",status:"Etkinlik",s:"s-green"},
{title:"Aidat Hatırlatması",text:"Haziran dönemi bekleyen ödemeler için otomatik hatırlatma mesajları gönderilmiştir.",status:"Ödeme",s:"s-orange"}
]
};

let data=JSON.parse(JSON.stringify(originalData));
let currentPage="dashboard";
let editTarget=null;

function toggleMenu(){
  document.getElementById("sidebar").classList.toggle("active");
}

function toast(msg){
  const t=document.getElementById("toast");
  t.textContent=msg;
  t.style.display="block";
  setTimeout(()=>t.style.display="none",2800);
}

function resetData(){
  data=JSON.parse(JSON.stringify(originalData));
}

function title(h,p){
  return `<div class="page-title"><h1>${h}</h1><p>${p}</p></div>`;
}

function stat(n,t){
  return `<div class="stat"><h2>${n}</h2><p>${t}</p></div>`;
}

function card(item,type,i){
  return `
  <div class="card">
    <div class="card-top">
      <div>
        <h3>${item.title}</h3>
        <p class="meta">${item.text}</p>
      </div>
      <span class="status ${item.s}">${item.status}</span>
    </div>
    <div class="actions">
      <button class="smallbtn btn-blue" onclick="openEdit('${type}',${i})">Düzenle</button>
      <button class="smallbtn btn-red" onclick="deleteItem('${type}',${i})">Sil</button>
      <button class="smallbtn btn-purple" onclick="toast('Detay ekranı demo olarak gösterildi.')">Detay</button>
    </div>
  </div>`;
}

function list(type){
  return `<div class="notice">Demo modundasınız. Düzenleme ve silme işlemleri geçici olarak görünür; sayfa yenilenince veya farklı bölüme geçince tüm veriler ilk haline döner.</div>
  <div class="search-row"><input placeholder="Bu bölümde ara..." oninput="filterCards(this.value)"><button class="btn btn-dark" onclick="navigate(currentPage)">Verileri Yenile</button></div>
  <div class="grid">${data[type].map((x,i)=>card(x,type,i)).join("")}</div>`;
}

function navigate(page,btn){
  resetData();
  currentPage=page;
  document.getElementById("sidebar").classList.remove("active");
  document.querySelectorAll(".nav-btn").forEach(b=>b.classList.remove("active"));
  if(btn) btn.classList.add("active");

  const c=document.getElementById("content");

  if(page==="dashboard"){
    c.innerHTML=`
    <section class="hero">
      <h1>Anaokulu ve Kurs Merkezleri İçin Akıllı Yönetim Paneli</h1>
      <p>MinikPanel; öğrenci kayıtları, sınıf doluluk takibi, devamsızlık, aidat, veli iletişimi, şube yönetimi ve raporlama ekranlarını tek panelde toplayan kapsamlı demo arayüzüdür.</p>
      <div class="hero-actions">
        <button class="btn btn-orange" onclick="navigate('students')">Öğrencileri İncele</button>
        <button class="btn btn-blue" onclick="navigate('reports')">Raporları Gör</button>
      </div>
    </section>

    <div class="grid">
      ${stat("126","Toplam Öğrenci")}
      ${stat("8","Aktif Sınıf")}
      ${stat("11","Bugünkü Devamsızlık")}
      ${stat("18","Bekleyen Ödeme")}
      ${stat("%84","Doluluk Oranı")}
      ${stat("3","Aktif Şube")}
    </div>
    <br>
    <div class="two">
      <div class="panel">
        <h3>Bugünkü Özet</h3><br>
        <table class="table">
          <tr><th>İşlem</th><th>Durum</th></tr>
          <tr><td>Güneş Çocukları sınıfında sanat etkinliği</td><td><span class="status s-green">Tamamlandı</span></td></tr>
          <tr><td>Aras Çelik için devamsızlık bildirimi</td><td><span class="status s-orange">Gönderildi</span></td></tr>
          <tr><td>Haziran aidat hatırlatmaları</td><td><span class="status s-blue">Aktif</span></td></tr>
          <tr><td>Cuma veli toplantısı duyurusu</td><td><span class="status s-purple">Planlandı</span></td></tr>
        </table>
      </div>
      <div class="panel">
        <h3>Bugünkü Yemek</h3><br>
        <p class="meta">Kahvaltı: Peynirli tost, zeytin, süt</p>
        <p class="meta">Öğle: Sebze çorbası, köfte, pilav</p>
        <p class="meta">İkindi: Muz, ev kurabiyesi</p>
        <br>
        <h3>Yaklaşan Etkinlik</h3>
        <p class="meta">Çarşamba: Fotoğraf günü</p>
      </div>
    </div>
    <p class="footer-note">Bu çalışma portföy/demo amaçlıdır. Tüm veriler kurgusaldır.</p>`;
  }

  if(page==="students") c.innerHTML=title("Öğrenciler","Öğrenci kayıtları, veli bilgileri ve ödeme durumları.")+list("students");
  if(page==="classes") c.innerHTML=title("Sınıflar","Anaokulu sınıfları, kapasite ve doluluk takibi.")+list("classes");
  if(page==="attendance") c.innerHTML=title("Devamsızlık","Günlük yoklama, geç gelenler ve veli bilgilendirmeleri.")+list("attendance");
  if(page==="payments") c.innerHTML=title("Ödemeler","Aidat, servis ücreti ve tahsilat takip ekranı.")+list("payments");
  if(page==="parents") c.innerHTML=title("Veliler","Veli iletişim bilgileri ve bildirim durumları.")+list("parents");
  if(page==="branches") c.innerHTML=title("Şubeler","Çoklu şube desteği ve şube bazlı doluluk bilgileri.")+list("branches");
  if(page==="announcements") c.innerHTML=title("Duyurular","Velilere gönderilecek duyuru ve bilgilendirmeler.")+list("announcements");

  if(page==="daily"){
    c.innerHTML=title("Günlük Akış","Anaokulu günlük program akışı.")+
    `<div class="panel">
      <div class="timeline">
        ${time("08:00 - 09:00","Karşılama ve serbest oyun")}
        ${time("09:00 - 09:30","Kahvaltı")}
        ${time("09:45 - 10:30","Sanat etkinliği")}
        ${time("10:45 - 11:30","Bahçe ve oyun saati")}
        ${time("12:00 - 12:45","Öğle yemeği")}
        ${time("13:00 - 14:30","Uyku / dinlenme")}
        ${time("15:00 - 15:30","İkindi kahvaltısı")}
        ${time("16:00 - 17:30","Veli teslim ve çıkış")}
      </div>
    </div>`;
  }

  if(page==="meals"){
    c.innerHTML=title("Yemek Listesi","Haftalık kahvaltı, öğle ve ikindi menüsü.")+
    `<div class="grid">
      ${meal("Pazartesi","Peynirli tost","Sebze çorbası, köfte, pilav","Muz ve süt")}
      ${meal("Salı","Omlet, zeytin","Tavuklu makarna, yoğurt","Ev keki")}
      ${meal("Çarşamba","Simit, peynir","Mercimek çorbası, bulgur pilavı","Elma")}
      ${meal("Perşembe","Menemen","Kuru fasulye, pirinç pilavı","Kurabiye")}
      ${meal("Cuma","Bal, tereyağı, süt","Tarhana çorbası, sebzeli makarna","Meyve tabağı")}
    </div>`;
  }

  if(page==="reports"){
    c.innerHTML=title("Raporlar","Sınıf doluluk, ödeme, devamsızlık ve şube raporları.")+
    `<div class="grid">
      ${stat("₺352.000","Bu Ay Tahsilat")}
      ${stat("₺74.000","Bekleyen Ödeme")}
      ${stat("%84","Ortalama Doluluk")}
      ${stat("31","Aylık Devamsızlık")}
    </div><br>
    <div class="two">
      <div class="panel">
        <h3>Sınıf Doluluk Grafiği</h3>
        ${bar("Minik Kalpler",83)}
        ${bar("Neşeli Bulutlar",100)}
        ${bar("Güneş Çocukları",85)}
        ${bar("Yıldızlar",78)}
        ${bar("Papatyalar",86)}
      </div>
      <div class="panel">
        <h3>Ödeme Durumu</h3>
        ${bar("Ödendi",72)}
        ${bar("Bekliyor",18)}
        ${bar("Gecikmiş",10)}
        <br>
        <h3>Şube Dağılımı</h3>
        ${bar("Merkez Şube",54)}
        ${bar("Sahil Şube",27)}
        ${bar("Bahçe Şube",19)}
      </div>
    </div>`;
  }

  if(page==="gallery"){
    c.innerHTML=title("Galeri","Anaokulu ortamı için temsili görseller.")+
    `<div class="gallery">
      <img src="https://images.unsplash.com/photo-1588072432836-e10032774350?auto=format&fit=crop&w=900&q=80">
      <img src="https://images.unsplash.com/photo-1503676260728-1c00da094a0b?auto=format&fit=crop&w=900&q=80">
      <img src="https://images.unsplash.com/photo-1516627145497-ae6968895b74?auto=format&fit=crop&w=900&q=80">
      <img src="https://images.unsplash.com/photo-1596464716127-f2a82984de30?auto=format&fit=crop&w=900&q=80">
      <img src="https://images.unsplash.com/photo-1544717305-2782549b5136?auto=format&fit=crop&w=900&q=80">
      <img src="https://images.unsplash.com/photo-1519389950473-47ba0277781c?auto=format&fit=crop&w=900&q=80">
      <img src="https://images.unsplash.com/photo-1577896851231-70ef18881754?auto=format&fit=crop&w=900&q=80">
      <img src="https://images.unsplash.com/photo-1587654780291-39c9404d746b?auto=format&fit=crop&w=900&q=80">
    </div>`;
  }
}

function time(a,b){
  return `<div class="time-item"><b>${a}</b><span class="meta">${b}</span></div>`;
}

function meal(day,b,l,s){
  return `<div class="card"><h3>${day}</h3><p class="meta"><b>Kahvaltı:</b> ${b}</p><p class="meta"><b>Öğle:</b> ${l}</p><p class="meta"><b>İkindi:</b> ${s}</p></div>`;
}

function bar(label,w){
  return `<div class="bar-wrap"><div class="bar-label"><span>${label}</span><b>%${w}</b></div><div class="bar-bg"><div class="bar" style="width:${w}%">%${w}</div></div></div>`;
}

function filterCards(q){
  q=q.toLowerCase();
  document.querySelectorAll(".card").forEach(x=>{
    x.style.display=x.innerText.toLowerCase().includes(q) ? "block" : "none";
  });
}

function openEdit(type,i){
  editTarget={type,i};
  document.getElementById("editTitle").value=data[type][i].title;
  document.getElementById("editText").value=data[type][i].text;
  document.getElementById("modal").classList.add("active");
}

function saveEdit(){
  if(!editTarget)return;
  data[editTarget.type][editTarget.i].title=document.getElementById("editTitle").value;
  data[editTarget.type][editTarget.i].text=document.getElementById("editText").value;
  closeModal();
  renderCurrent();
  toast("Kayıt geçici olarak güncellendi.");
}

function deleteItem(type,i){
  if(!confirm("Bu kayıt demo olarak silinsin mi? Sayfa yenilenince veya bölüm değişince geri gelir."))return;
  data[type].splice(i,1);
  renderCurrent(false);
  toast("Kayıt geçici olarak silindi.");
}

function closeModal(){
  document.getElementById("modal").classList.remove("active");
}

function renderCurrent(reset=false){
  const page=currentPage;
  const fakeBtn=[...document.querySelectorAll(".nav-btn")].find(b=>b.classList.contains("active"));
  if(reset) resetData();
  const temp=JSON.parse(JSON.stringify(data));
  navigate(page,fakeBtn);
  data=temp;
}

navigate("dashboard");
</script>

</body>
</html>

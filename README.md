[index.html](https://github.com/user-attachments/files/33335243/index.html)
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Platform Ujian Ekonomi v2.0 - Google Sheets</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@500&display=swap');

:root {
  --bg:    #080e1a;
  --bg2:   #0d1520;
  --card:  #111c2e;
  --card2: #162236;
  --pri:   #3d8ef0;
  --pri2:  #5ba3ff;
  --glow:  rgba(61,142,240,.18);
  --on:    #ffffff;
  --bd:    #1e2f47;
  --bd2:   #243649;
  --mut:   #5a7a9f;
  --fg:    #d8e8f8;
  --fg2:   #a8c4e0;
  --sel:   #132240;
  --warn:  #f05252;
  --warn2: #ff8a80;
  --ok:    #34c48a;
  --grad:  linear-gradient(135deg,#1a3560 0%,#0d1f3c 100%);
  box-sizing: border-box;
  padding-top: env(safe-area-inset-top,0px);
  padding-bottom: env(safe-area-inset-bottom,0px);
}

*{box-sizing:border-box;margin:0;padding:0}

html{
  scroll-padding-top: env(safe-area-inset-top,0px);
  height:100%;
}

body{
  min-height:100%;
  background: var(--bg);
  background-image:
    radial-gradient(ellipse 80% 40% at 50% -10%, rgba(61,142,240,.12) 0%, transparent 70%),
    radial-gradient(ellipse 40% 30% at 90% 80%, rgba(61,80,200,.08) 0%, transparent 60%);
  color: var(--fg);
  font: 400 15px/1.6 'Inter', system-ui, -apple-system, sans-serif;
  -webkit-font-smoothing: antialiased;
}

[hidden]{display:none!important}

.w{
  max-width: 780px;
  margin: 0 auto;
  padding: 20px 16px 60px;
}

.card{
  background: var(--card);
  border: 1px solid var(--bd);
  border-radius: 16px;
  padding: 28px 28px;
  position: relative;
  overflow: hidden;
}
.card::before{
  content:'';
  position:absolute;inset:0;
  background: linear-gradient(135deg,rgba(61,142,240,.04) 0%,transparent 60%);
  pointer-events:none;
}

.brand{
  display:flex;align-items:center;gap:10px;
  margin-bottom:28px;
}
.brand-dot{
  width:8px;height:8px;border-radius:50%;
  background:var(--pri);
  box-shadow:0 0 10px var(--pri);
}
.brand-name{
  font:600 .78rem/1 'JetBrains Mono',monospace;
  letter-spacing:.12em;
  color:var(--pri2);
  text-transform:uppercase;
}

h1{
  font: 700 1.75rem/1.15 'Inter',sans-serif;
  color: var(--on);
  margin-bottom: 6px;
  letter-spacing:-.02em;
}

.subtitle{
  color: var(--mut);
  font-size:.9rem;
  margin-bottom:24px;
  line-height:1.5;
}

.pills{
  display:flex;gap:8px;flex-wrap:wrap;
  margin-bottom:28px;
}
.pill{
  display:flex;align-items:center;gap:8px;
  background:var(--card2);
  border:1px solid var(--bd);
  border-radius:100px;
  padding:7px 14px;
}
.pill b{
  font:600 1rem/1 'JetBrains Mono',monospace;
  color:var(--pri2);
}
.pill span{font-size:.8rem;color:var(--mut);}

.field{margin-bottom:16px;}
.field label{
  display:block;
  font:600 .8rem/1 'Inter',sans-serif;
  color:var(--fg2);
  letter-spacing:.04em;
  margin-bottom:7px;
  text-transform:uppercase;
}
.field input{
  width:100%;
  padding:12px 14px;
  font:400 .95rem/1 'Inter',sans-serif;
  color:var(--fg);
  background:var(--bg2);
  border:1px solid var(--bd);
  border-radius:10px;
  transition:border-color .15s,box-shadow .15s;
  outline:none;
}
.field input::placeholder{color:var(--mut);}
.field input:focus{
  border-color:var(--pri);
  box-shadow:0 0 0 3px var(--glow);
}

.err{
  color:var(--warn2);
  font-size:.85rem;
  min-height:1.3em;
  margin-bottom:14px;
}

button{
  font:500 .9rem/1 'Inter',sans-serif;
  cursor:pointer;
  border-radius:10px;
  border:1px solid var(--bd);
  background:var(--card2);
  color:var(--fg);
  padding:11px 18px;
  transition:all .15s;
}
button:hover{border-color:var(--bd2);background:var(--card);}

.btn-pri{
  background:var(--pri);
  color:#fff;
  border-color:var(--pri);
  font-weight:600;
  box-shadow:0 0 20px var(--glow);
}
.btn-pri:hover{
  background:var(--pri2);
  border-color:var(--pri2);
  box-shadow:0 0 28px rgba(61,142,240,.3);
}
button:focus-visible{
  outline:2px solid var(--pri);
  outline-offset:2px;
}

.top{
  position:sticky;
  top:env(safe-area-inset-top,0px);
  z-index:10;
  background:rgba(8,14,26,.85);
  backdrop-filter:blur(12px);
  -webkit-backdrop-filter:blur(12px);
  border-bottom:1px solid var(--bd);
  padding:12px 16px;
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:12px;
  margin:0 -16px;
}
.top-left b{
  font:600 .95rem/1 'Inter',sans-serif;
  color:var(--on);
}
.top-left .prog-text{
  font-size:.78rem;
  color:var(--mut);
  margin-top:3px;
}
#tm{
  font:700 1.3rem/1 'JetBrains Mono',monospace;
  color:var(--pri2);
  background:var(--card);
  border:1px solid var(--bd);
  border-radius:8px;
  padding:6px 14px;
  letter-spacing:.04em;
  transition:color .3s;
  white-space:nowrap;
}
#tm.lo{
  color:var(--warn2);
  border-color:rgba(240,82,82,.3);
  background:rgba(240,82,82,.08);
}

.progress-wrap{
  height:3px;
  background:var(--bd);
  border-radius:2px;
  margin:10px 0 0;
  overflow:hidden;
}
#pbar{
  height:100%;
  background:linear-gradient(90deg,var(--pri) 0%,var(--pri2) 100%);
  border-radius:2px;
  transition:width .3s ease;
  width:0%;
}

.q-card{
  margin-top:14px;
}
.q-tag{
  font:500 .75rem/1 'JetBrains Mono',monospace;
  color:var(--mut);
  letter-spacing:.05em;
  margin-bottom:14px;
}
.q-text{
  font:400 1.05rem/1.65 'Inter',sans-serif;
  color:var(--on);
  margin-bottom:20px;
}

.opt{
  display:flex;
  gap:12px;
  width:100%;
  text-align:left;
  margin:7px 0;
  padding:13px 16px;
  align-items:flex-start;
  border-radius:12px;
  border:1px solid var(--bd);
  background:var(--bg2);
  transition:all .15s;
  color:var(--fg);
  cursor:pointer;
}
.opt:hover{
  border-color:var(--bd2);
  background:var(--card2);
}
.opt-letter{
  font-style:normal;
  font:600 .82rem/1 'JetBrains Mono',monospace;
  min-width:28px;height:28px;
  border-radius:7px;
  border:1px solid var(--bd);
  display:grid;place-items:center;
  color:var(--mut);
  flex-shrink:0;
  transition:all .15s;
  background:var(--card);
}
.opt.on{
  background:var(--sel);
  border-color:var(--pri);
}
.opt.on .opt-letter{
  background:var(--pri);
  color:#fff;
  border-color:var(--pri);
  box-shadow:0 0 8px var(--glow);
}

.nav{
  display:flex;
  justify-content:space-between;
  gap:8px;
  margin-top:18px;
  flex-wrap:wrap;
}

#grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(40px,1fr));
  gap:5px;
  margin-top:16px;
}
#grid button{
  padding:9px 0;
  font:600 .8rem/1 'JetBrains Mono',monospace;
  border-radius:8px;
  color:var(--mut);
}
#grid .ans{
  background:var(--sel);
  border-color:var(--pri);
  color:var(--pri2);
}
#grid .cur{
  outline:2px solid var(--pri);
  outline-offset:2px;
}

.explanation{
  padding:14px 16px;
  border-radius:12px;
  margin-top:14px;
  border-left:4px solid;
  font-size:.9rem;
  line-height:1.6;
}
.explanation.correct{
  background:rgba(52,196,138,.1);
  border-left-color:var(--ok);
  color:var(--ok);
}
.explanation.wrong{
  background:rgba(240,82,82,.1);
  border-left-color:var(--warn);
  color:var(--warn2);
}
.explanation b{
  display:block;
  margin-bottom:8px;
  font-weight:600;
}

.score-ring-wrap{
  display:flex;
  justify-content:center;
  margin:20px 0 24px;
}
.score-ring{
  position:relative;
  width:140px;height:140px;
}
.score-ring svg{
  transform:rotate(-90deg);
}
.score-ring-num{
  position:absolute;
  inset:0;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
}
.score-big{
  font:700 2.5rem/1 'JetBrains Mono',monospace;
  color:var(--on);
}
.score-label{
  font:500 .72rem/1 'Inter',sans-serif;
  color:var(--mut);
  margin-top:3px;
}

.result-meta{
  font-size:.88rem;
  color:var(--mut);
  text-align:center;
  margin-bottom:20px;
}

table{
  width:100%;
  border-collapse:collapse;
  margin-top:12px;
  font-size:.88rem;
}
th{
  padding:9px 10px;
  background:var(--bg2);
  color:var(--fg2);
  font:600 .75rem/1 'Inter',sans-serif;
  text-align:left;
  letter-spacing:.04em;
  border-bottom:1px solid var(--bd);
  text-transform:uppercase;
}
td{
  padding:9px 10px;
  border-bottom:1px solid var(--bd);
  color:var(--fg);
}

.rv{
  border:1px solid var(--bd);
  border-radius:12px;
  padding:16px;
  margin:10px 0;
  background:var(--bg2);
}
.rv.g{border-left:4px solid var(--ok);}
.rv.b{border-left:4px solid var(--warn);}
.rv-tag{
  font:500 .75rem/1 'JetBrains Mono',monospace;
  color:var(--mut);
  margin-bottom:10px;
  letter-spacing:.04em;
}
.rv .q-text{font-size:.95rem;margin-bottom:12px;}
.ro{
  display:flex;gap:10px;
  padding:7px 10px;
  border-radius:8px;
  margin:3px 0;
  font-size:.88rem;
  color:var(--fg2);
}
.ro i{
  font-style:normal;
  font:600 .8rem/1 'JetBrains Mono',monospace;
  min-width:22px;color:var(--mut);
}
.ro.k{background:rgba(52,196,138,.1);color:var(--ok);border:1px solid rgba(52,196,138,.2);}
.ro.k i{color:var(--ok);}
.ro.w{color:var(--warn2);}
.ro.w i{color:var(--warn2);}
.pb{
  margin-top:10px;
  padding:10px 12px;
  background:var(--card2);
  border-radius:8px;
  font-size:.85rem;
  color:var(--fg2);
  line-height:1.6;
  border-left:3px solid var(--pri);
}
.pb b{color:var(--pri2);}

.mut{color:var(--mut);}
.mt16{margin-top:16px;}
.note{
  font-size:.8rem;
  color:var(--mut);
  line-height:1.6;
  margin-top:16px;
  padding:12px 14px;
  background:var(--bg2);
  border-radius:10px;
  border:1px solid var(--bd);
}

.status-badge{
  display:inline-flex;
  align-items:center;
  gap:6px;
  padding:6px 12px;
  border-radius:8px;
  font-size:.8rem;
  font-weight:600;
  margin-top:12px;
}
.status-badge.sending{
  background:rgba(61,142,240,.1);
  color:var(--pri2);
  border:1px solid rgba(61,142,240,.3);
}
.status-badge.success{
  background:rgba(52,196,138,.1);
  color:var(--ok);
  border:1px solid rgba(52,196,138,.3);
}
.status-badge.error{
  background:rgba(240,82,82,.1);
  color:var(--warn2);
  border:1px solid rgba(240,82,82,.3);
}

@media(max-width:500px){
  .card{padding:20px 16px;}
  h1{font-size:1.4rem;}
  .pills{gap:6px;}
}
</style>
</head>
<body>
<div class="w">

<!-- SECTION 0: Start -->
<section id="s0" class="card">
  <div class="brand">
    <div class="brand-dot"></div>
    <div class="brand-name">CZHI Project 2.0</div>
  </div>
  <h1>Latihan Soal Ekonomi</h1>
  <p class="subtitle">Kelas X · Google Sheets Integration · Real-time Data Sync · Penjelasan Instan</p>
  <div class="pills">
    <div class="pill"><b>30</b><span>soal acak</span></div>
    <div class="pill"><b>120</b><span>menit</span></div>
    <div class="pill"><b>☁️</b><span>data otomatis ke sheets</span></div>
  </div>
  
  <div class="field">
    <label for="nm">Nama lengkap</label>
    <input id="nm" autocomplete="off" placeholder="Masukkan nama lengkap" autofocus>
  </div>
  <div class="field">
    <label for="kl">Kelas</label>
    <input id="kl" placeholder="Contoh: X-6" autocomplete="off">
  </div>
  
  <p class="err" id="err"></p>
  <button class="btn-pri" id="go" style="width:100%;padding:14px;">Mulai Ujian</button>
  
  <p class="note">Web ini dirancang untuk memberikan latihan soal ekonomi sebelum menghadapi ulangan ekonomi yang sesungguhnya, enjoy!</p>
</section>

<!-- SECTION 1: Quiz -->
<section id="s1" hidden>
  <div class="top">
    <div class="top-left">
      <b id="who"></b>
      <div class="prog-text" id="prog"></div>
      <div class="progress-wrap" style="width:180px;max-width:50vw;">
        <div id="pbar"></div>
      </div>
    </div>
    <div id="tm">120:00</div>
  </div>

  <div class="card q-card">
    <div class="q-tag" id="qt"></div>
    <div class="q-text" id="qq"></div>
    <div id="ops"></div>
    <div id="expl"></div>
    <div class="nav">
      <button id="pv">← Sebelumnya</button>
      <button id="nx" class="btn-pri">Berikutnya →</button>
    </div>
  </div>

  <div id="grid"></div>

  <div class="nav mt16">
    <span></span>
    <button id="fin" style="border-color:var(--warn);color:var(--warn2);">Kumpulkan Jawaban</button>
  </div>
</section>

<!-- SECTION 2: Results -->
<section id="s2" class="card" hidden>
  <div class="brand">
    <div class="brand-dot" style="background:var(--ok);box-shadow:0 0 10px var(--ok);"></div>
    <div class="brand-name" style="color:var(--ok);">Ujian Selesai</div>
  </div>
  
  <div class="mut" id="rwho" style="margin-bottom:4px;font-size:.9rem;"></div>

  <div class="score-ring-wrap">
    <div class="score-ring">
      <svg width="140" height="140" viewBox="0 0 140 140">
        <circle cx="70" cy="70" r="58" fill="none" stroke="var(--bd)" stroke-width="10"/>
        <circle id="score-arc" cx="70" cy="70" r="58" fill="none"
          stroke="var(--pri)" stroke-width="10"
          stroke-linecap="round"
          stroke-dasharray="364.4"
          stroke-dashoffset="364.4"
          style="transition:stroke-dashoffset 1s ease"/>
      </svg>
      <div class="score-ring-num">
        <div class="score-big" id="sc">—</div>
        <div class="score-label">/ 100</div>
      </div>
    </div>
  </div>

  <div class="result-meta" id="rd"></div>
  <div id="sent" class="mut" style="font-size:.85rem;text-align:center;margin-bottom:12px;"></div>
  
  <div id="sync-status"></div>

  <table id="rt"></table>
  <div id="rv" style="margin-top:20px;"></div>

  <div class="mt16">
    <button id="again" style="width:100%;">Kembali ke Halaman Awal</button>
  </div>
</section>

</div>

<script>
// ============================================
// DATA SOAL EKONOMI (84 soal total)
// ============================================
var M=["Kegiatan Ekonomi","Biaya Produksi","Perilaku Produsen","Hukum Produk Marginal","Kurva PPC","Produksi","Distribusi"];

var D=[[0,0,"Kegiatan manusia untuk memenuhi kebutuhan sehari-hari melalui menghasilkan, menyalurkan, dan menggunakan barang atau jasa disebut ....","kegiatan sosial","kegiatan ekonomi","kegiatan budaya","kegiatan politik",1],[0,0,"Tiga kegiatan pokok dalam siklus kegiatan ekonomi adalah ....","produksi, promosi, dan konsumsi","produksi, distribusi, dan investasi","distribusi, konsumsi, dan tabungan","produksi, distribusi, dan konsumsi",3],[0,0,"Petani menghasilkan beras dari sawahnya. Kegiatan tersebut termasuk ....","produksi","distribusi","konsumsi","investasi",0],[0,0,"Faktor produksi berupa kemampuan mengatur faktor produksi lainnya dan mengambil keputusan disebut ....","sumber daya alam","tenaga kerja","kewirausahaan","modal",2],[0,1,"Urutan saluran distribusi tidak langsung yang benar adalah ....","produsen → pengecer → grosir → konsumen","produsen → grosir → pengecer → konsumen","grosir → produsen → pengecer → konsumen","produsen → konsumen → grosir → pengecer",1],[0,1,"Pernyataan yang paling tepat tentang fungsi distribusi adalah ....","membuat produk tersedia pada waktu, tempat, dan jumlah yang dibutuhkan","mengubah bahan mentah menjadi barang jadi","menghabiskan barang sebanyak-banyaknya","menambah jumlah faktor produksi",0],[0,1,"Menurut materi, tujuan utama konsumsi adalah ....","menghabiskan barang sebanyak mungkin","menambah laba produsen","mengumpulkan barang sebanyak mungkin","memperoleh manfaat untuk memenuhi kebutuhan",3],[0,1,"Pabrik mengolah bahan menjadi sepatu, sepatu dikirim ke toko, lalu siswa memakainya untuk bersekolah. Urutan kegiatan ekonomi yang benar adalah ....","konsumsi, produksi, distribusi","distribusi, produksi, konsumsi","produksi, distribusi, konsumsi","produksi, konsumsi, distribusi",2],[0,2,"Pabrik sepatu mampu memproduksi banyak sepatu dan siswa di sebuah daerah sangat membutuhkannya, tetapi toko di daerah itu selalu kehabisan stok. Tahap yang paling mungkin bermasalah adalah ....","produksi","distribusi","konsumsi","kewirausahaan",1],[0,2,"Ana membeli sebuah blender untuk dipakai terus-menerus dalam usaha jus miliknya. Bagi usaha tersebut, blender termasuk faktor produksi ....","modal","sumber daya alam","tenaga kerja","kewirausahaan",0],[0,2,"Berikut ini yang bukan faktor yang memengaruhi konsumsi adalah ....","pendapatan","harga","selera","jumlah mesin di pabrik",3],[0,2,"Konsumsi memenuhi kebutuhan sekaligus memunculkan kebutuhan baru. Hal ini menunjukkan bahwa ....","kegiatan ekonomi berhenti setelah konsumsi","produksi tidak lagi diperlukan","kegiatan ekonomi membentuk siklus yang terus berlanjut","distribusi tidak memiliki peran",2],[1,0,"Biaya yang jumlahnya tidak berubah dalam jangka pendek meskipun jumlah produksi berubah disebut ....","biaya tetap","biaya variabel","biaya marginal","biaya rata-rata",0],[1,0,"Contoh biaya variabel adalah ....","sewa tempat","penyusutan mesin","bahan baku","gaji manajer tetap",2],[1,0,"Rumus biaya total (TC) adalah ....","TC = FC − VC","TC = FC + VC","TC = FC × VC","TC = FC ÷ VC",1],[1,0,"Biaya rata-rata (AC) dihitung dengan rumus ....","AC = TC × Q","AC = TC − Q","AC = FC ÷ VC","AC = TC ÷ Q",3],[1,1,"Sebuah usaha memiliki biaya tetap Rp1.500.000 dan biaya variabel Rp2.500.000 untuk menghasilkan 800 unit. Biaya rata-rata per unit adalah ....","Rp3.125","Rp4.000","Rp5.000","Rp5.500",2],[1,1,"Ketika produksi naik 100 unit, biaya total naik sebesar Rp600.000. Biaya marginal (MC) per unit tambahan adalah ....","Rp6.000","Rp60.000","Rp600","Rp100.000",0],[1,1,"Biaya tetap per unit turun ketika jumlah produksi bertambah karena ....","biaya tetap total ikut turun","biaya tetap tersebar ke lebih banyak unit","biaya variabel menjadi nol","harga jual otomatis naik",1],[1,1,"Sebuah usaha memiliki FC = Rp60 dan pada Q = 3 biaya variabelnya Rp45 (dalam ribuan rupiah). Biaya rata-rata (AC) pada Q = 3 adalah ....","Rp15","Rp20","Rp30","Rp35",3],[1,2,"Sebuah usaha memiliki FC = 60. Pada Q = 4 nilai VC = 55, dan pada Q = 5 nilai VC = 75. Biaya marginal (MC) dari Q = 4 ke Q = 5 adalah ....","20","27","35","115",0],[1,2,"Dengan FC = 60, TC pada Q = 4, Q = 5, dan Q = 6 berturut-turut adalah 115, 135, dan 180. Kesimpulan yang tepat tentang biaya marginal adalah ....","MC turun dari 45 menjadi 20","MC tetap 20 pada setiap unit tambahan","MC naik dari 20 menjadi 45, sehingga setiap unit tambahan makin mahal","MC selalu sama dengan AC",2],[1,2,"Usaha dengan FC Rp1.200.000 memiliki TC Rp1.800.000 pada Q = 100 dan TC Rp2.200.000 pada Q = 200. Biaya marginal dari Q = 100 ke Q = 200 adalah ....","Rp2.200","Rp11.000","Rp18.000","Rp4.000",3],[1,2,"Pernyataan yang benar tentang biaya produksi adalah ....","biaya variabel per unit selalu tetap pada semua tingkat output","biaya tetap total tidak berubah dalam kisaran kapasitas tertentu, tetapi biaya tetap per unit turun ketika output naik","biaya total selalu turun ketika output naik","pada output nol, biaya total juga nol",1],[2,0,"Produksi adalah kegiatan ....","menjual barang kepada konsumen","menyalurkan barang ke pengecer","memproses input menjadi output","menyimpan barang di gudang",2],[2,0,"Pada usaha kedai jus, buah, tenaga kerja, dan blender disebut ....","output","input","laba","titik impas",1],[2,0,"Penerimaan total (TR) dihitung dengan rumus ....","harga jual × jumlah terjual","harga jual + jumlah terjual","biaya total − laba","biaya tetap + biaya variabel",0],[2,0,"Laba dihitung dengan rumus ....","TR + TC","TC − TR","TR × TC","TR − TC",3],[2,1,"Titik impas (BEP) terjadi ketika ....","penerimaan total lebih besar daripada biaya total","penerimaan total sama dengan biaya total","penerimaan total lebih kecil daripada biaya total","biaya total sama dengan nol",1],[2,1,"Pada fungsi produksi Q = F(K, L, R, T), huruf L menunjukkan ....","modal","bahan baku","tenaga kerja","teknologi",2],[2,1,"Seorang produsen memilih memakai mesin atau tenaga manusia untuk membuat produknya. Keputusan tersebut menjawab pertanyaan ....","berapa yang diproduksi","untuk siapa produk ditawarkan","berapa dan untuk siapa","bagaimana cara memproduksi",3],[2,1,"Sebuah kedai menjual 50 gelas minuman dengan harga Rp10.000 per gelas. Penerimaan total kedai tersebut adalah ....","Rp500.000","Rp60.000","Rp5.000","Rp10.050",0],[2,2,"Kedai jus menjual 200 gelas dengan harga Rp12.000 per gelas. Biaya total usaha tersebut Rp2.000.000. Laba yang diperoleh adalah ....","Rp2.400.000","Rp2.000.000","Rp400.000","rugi Rp400.000",2],[2,2,"Sebuah usaha menjual 100 unit dengan harga Rp8.000 per unit, sedangkan biaya total produksinya Rp1.000.000. Kondisi usaha tersebut adalah ....","laba Rp200.000","rugi Rp200.000","tepat di titik impas","laba Rp800.000",1],[2,2,"Sebelum memutuskan menambah produksi, produsen sebaiknya membandingkan ....","tambahan penerimaan dengan tambahan biaya","harga pesaing saja","jumlah pegawai dengan jumlah pelanggan","biaya tetap dengan biaya variabel saja",0],[2,2,"Sebuah usaha memiliki penerimaan total Rp3.000.000 dan biaya total Rp3.500.000. Jika biaya tidak berubah, agar usaha mencapai titik impas, penerimaan total harus ....","turun Rp500.000","tetap Rp3.000.000","naik menjadi Rp6.500.000","naik Rp500.000 sehingga sama dengan biaya total",3],[3,0,"Produk marginal (MP) adalah ....","seluruh output yang dihasilkan","output rata-rata per unit input","biaya per unit output","tambahan output akibat tambahan satu unit input variabel",3],[3,0,"Produk total (TP) adalah ....","jumlah seluruh output yang dihasilkan","tambahan output dari satu input","output rata-rata per input","biaya total produksi",0],[3,0,"Produk rata-rata (AP) dihitung dengan rumus ....","AP = TP × L","AP = TP − L","AP = TP ÷ L","AP = L ÷ TP",2],[3,0,"Contoh input tetap dalam jangka pendek adalah ....","tenaga kerja","ukuran dapur","bahan baku","jumlah juru masak",1],[3,1,"Pada produksi dengan TP: L = 3 menghasilkan 36 dan L = 4 menghasilkan 45, produk marginal (MP) pada L = 4 adalah ....","9","11,25","45","12",0],[3,1,"Diketahui TP: L = 0 → 0; L = 1 → 10; L = 2 → 24; L = 3 → 36. Produk marginal tertinggi terjadi pada penambahan tenaga kerja ke ....","1","3","4","2",3],[3,1,"Jika TP pada L = 5 adalah 51, produk rata-rata (AP) pada L = 5 adalah ....","6","51","10,2","9",2],[3,1,"Pernyataan yang sesuai dengan hukum produk marginal yang makin menurun adalah ....","produk total selalu turun ketika input ditambah","jika satu input variabel terus ditambah sementara input lain tetap, tambahan output pada akhirnya makin kecil","produk marginal selalu bernilai negatif","produk rata-rata selalu naik",1],[3,2,"Diketahui TP: L = 1 → 10; L = 2 → 24; L = 3 → 36; L = 4 → 45. Produk marginal mulai menurun pada penambahan tenaga kerja ke ....","1","2","4","3",3],[3,2,"Diketahui TP: L = 6 → 54 dan L = 7 → 50. Produk marginal bernilai negatif pada penambahan tenaga kerja ke ....","7","6","5","4",0],[3,2,"Ciri fase 'marginal menurun' adalah ....","MP negatif dan TP turun","MP masih positif, tetapi makin kecil, dan TP masih naik","MP bertambah karena pembagian kerja","TP berhenti dan tidak berubah sama sekali",1],[3,2,"Pada tabel produksi, L = 3 memiliki AP = 12 dan MP = 12, sedangkan L = 4 memiliki MP = 9 dan AP = 11,25. Kesimpulan yang tepat adalah ....","ketika MP berada di bawah AP, AP naik","AP selalu sama dengan MP","ketika MP lebih kecil daripada AP, AP menurun","ketika MP di atas AP, AP selalu turun",2],[4,0,"Kurva PPC menunjukkan ....","hubungan harga dan jumlah permintaan","batas maksimal kombinasi output dua barang yang dapat dihasilkan suatu perekonomian","biaya total produksi suatu perusahaan","laba maksimum produsen",1],[4,0,"Produksi suatu perekonomian memiliki batas karena ....","konsumen tidak mau membeli","harga barang terlalu tinggi","sumber daya terbatas (kelangkaan)","terlalu banyak distributor",2],[4,0,"Titik yang berada tepat pada kurva PPC menunjukkan ....","produksi efisien dan optimal","banyak sumber daya menganggur","kombinasi yang tidak mungkin dicapai","terjadinya penurunan kapasitas produksi",0],[4,0,"Titik yang berada di luar kurva PPC menunjukkan ....","produksi efisien","adanya pengangguran","biaya produksi nol","kombinasi yang tidak mungkin dicapai dengan sumber daya dan teknologi saat ini",3],[4,1,"Titik yang berada di dalam kurva PPC menunjukkan bahwa ....","kombinasi tersebut mustahil dicapai","ada sumber daya yang menganggur atau belum digunakan secara efisien","produksi sudah optimal","terjadi pertumbuhan ekonomi",1],[4,1,"Kurva PPC bergeser ke kanan (keluar) menandakan ....","kemunduran ekonomi akibat bencana","berkurangnya sumber daya akibat perang","pertumbuhan ekonomi karena faktor produksi atau teknologi meningkat","kelangkaan sudah hilang",2],[4,1,"Rumus biaya peluang pada kurva PPC adalah ....","jumlah barang yang dikorbankan ÷ jumlah barang yang diperoleh","jumlah barang yang diperoleh ÷ jumlah barang yang dikorbankan","jumlah barang yang dikorbankan × jumlah barang yang diperoleh","jumlah barang yang dikorbankan + jumlah barang yang diperoleh",0],[4,1,"Pada PPC padi dan kain, titik A (100 ton padi, 0 bal kain) dan titik B (90 ton padi, 20 bal kain). Biaya peluang untuk menambah 1 bal kain dari A ke B adalah ... ton padi.","2","10","20","0,5",3],[4,2,"Pada PPC padi dan kain, titik C (70 ton padi, 40 bal kain) dan titik D (40 ton padi, 60 bal kain). Biaya peluang untuk menambah 1 bal kain dari C ke D adalah ... ton padi.","0,5","1,0","1,5","2,0",2],[4,2,"Dari titik A sampai E, setiap tambahan 20 bal kain mengorbankan padi berturut-turut 10, 20, 30, dan 40 ton. Pola ini menunjukkan bahwa ....","biaya peluang tetap, sehingga kurva berupa garis lurus","biaya peluang makin meningkat, sehingga kurva PPC melengkung cekung (ke luar)","biaya peluang makin menurun","tidak ada biaya peluang dalam produksi",1],[4,2,"Kurva PPC melalui titik (padi, kain): (100, 0), (90, 20), (70, 40), (40, 60), (0, 80). Titik F (40 ton padi, 30 bal kain) dan titik G (80 ton padi, 60 bal kain) berturut-turut berada ....","di dalam kurva (belum efisien) dan di luar kurva (belum dapat dicapai)","di luar kurva dan di dalam kurva","tepat pada kurva dan di luar kurva","keduanya di dalam kurva",0],[4,2,"Perang menghancurkan sebagian besar mesin dan lahan produktif sebuah negara, sehingga kombinasi produksi pada titik C (70 ton padi, 40 bal kain) tidak mungkin lagi dicapai. Perubahan yang terjadi pada PPC adalah ....","bergeser ke kanan, titik C berada di dalam kurva baru","tetap, titik C tetap efisien","bergeser ke kiri, titik C tepat pada kurva baru","bergeser ke kiri, titik C berada di luar kurva baru",3],[5,0,"Kegiatan manusia menghasilkan barang atau jasa untuk memenuhi kebutuhan manusia disebut ....","distribusi","konsumsi","produksi","investasi",2],[5,0,"Berikut ini yang termasuk barang konsumsi adalah ....","makanan dan minuman","spatula","pisau dapur","mesin pabrik",0],[5,0,"Faktor-faktor produksi terdiri atas ....","alam, tenaga kerja, modal, dan distribusi","alam, modal, konsumsi, dan keahlian","tenaga kerja, grosir, modal, dan keahlian","alam, tenaga kerja, modal, dan keahlian",3],[5,0,"Hutan, hewan, air, dan sinar matahari termasuk sumber daya alam yang ....","tidak dapat diperbarui","dapat diperbarui","dibuat manusia","bernilai modal",1],[5,1,"Faktor produksi asli (utama) adalah ....","alam dan tenaga kerja","modal dan keahlian","alam dan modal","tenaga kerja dan keahlian",0],[5,1,"Perbankan, pengangkutan, dan pergudangan termasuk ....","barang konsumsi","barang modal","jasa langsung","jasa tidak langsung",3],[5,1,"Sebuah usaha katering memakai spatula dan pisau untuk mengolah makanan. Spatula dan pisau tersebut termasuk ....","barang konsumsi","barang modal","jasa langsung","sumber daya alam",1],[5,1,"Pernyataan yang sesuai dengan pengertian produksi menurut materi adalah ....","produksi hanya berarti menciptakan barang baru","produksi hanya berupa kegiatan jasa","produksi dapat berupa mengubah bentuk, mengubah sifat, atau menambah nilai guna barang","produksi hanya dilakukan oleh perusahaan besar",2],[5,2,"Sebuah pabrik roti memproduksi roti untuk dijual. Pernyataan yang tepat tentang tujuan produksi dari sudut pandang produsen dan konsumen adalah ....","keduanya bertujuan menambah laba","produsen menyediakan benda pemuas kebutuhan, konsumen meningkatkan keuntungan","keduanya bertujuan menghabiskan sumber daya","produsen meningkatkan keuntungan dan menjaga kesinambungan perusahaan, konsumen memperoleh benda pemuas kebutuhan",3],[5,2,"Pak Budi membuat kursi dari kayu jati, memakai gergaji dan mesin bubut, dibantu 3 karyawan, dan ia sendiri yang mengatur seluruh proses. Kayu jati, gergaji dan mesin bubut, karyawan, serta Pak Budi berturut-turut termasuk faktor produksi ....","modal, alam, tenaga kerja, keahlian","alam, tenaga kerja, modal, keahlian","alam, modal, tenaga kerja, keahlian","tenaga kerja, alam, keahlian, modal",2],[5,2,"Seorang akuntan bekerja menggunakan pikiran, rasa, dan karsa, sedangkan seorang kuli panggul bekerja menggunakan kekuatan fisik. Penggolongan tenaga kerja menurut sifat kerjanya secara berurutan adalah ....","rohani dan jasmani","jasmani dan rohani","keduanya rohani","keduanya jasmani",0],[5,2,"Pernyataan yang tepat tentang karakteristik faktor produksi alam adalah ....","jumlahnya tidak terbatas sehingga tidak pernah langka","tersedia secara alami, tetapi jumlahnya terbatas, kualitas dan lokasinya berbeda, serta pemanfaatannya memerlukan biaya ekstraksi","seluruhnya dapat diperbarui","dibuat manusia melalui proses produksi",1],[6,0,"Distribusi adalah kegiatan ....","mengubah bahan menjadi barang jadi","menyampaikan barang atau jasa dari produsen ke tangan konsumen yang membutuhkan","menggunakan barang untuk memenuhi kebutuhan","menghitung biaya produksi suatu usaha",1],[6,0,"Fungsi distribusi yang berkaitan dengan memindahkan barang dari satu tempat ke tempat lain adalah ....","penyimpanan","penjualan dan pembelian","pengemasan dan standarisasi","pengangkutan (transportasi)",3],[6,0,"Penyaluran barang tanpa perantara dengan alur produsen → konsumen disebut distribusi ....","langsung","tak langsung","semi langsung","bertingkat",0],[6,0,"Pedagang yang membeli dan menjual barang dalam jumlah besar disebut ....","pengecer","agen","grosir","komisioner",2],[6,1,"Badan atau perusahaan yang membeli barang dari luar negeri untuk dijual di dalam negeri disebut ....","eksportir","pengecer","importir","makelar",2],[6,1,"Perantara yang menjual atau membeli barang atas nama orang lain disebut ....","agen","makelar","komisioner","grosir",1],[6,1,"Saluran distribusi tak langsung satu tingkat, yang sesuai untuk barang mahal, adalah ....","produsen → konsumen","produsen → agen → pedagang besar → pengecer → konsumen","produsen → pedagang besar → pengecer → konsumen","produsen → pengecer → konsumen",3],[6,1,"Kegiatan distribusi berupa menyimpan barang di tempat khusus sebelum disalurkan atau dijual disebut ....","penggudangan","pembelian","pembungkusan","pengangkutan",0],[6,2,"Susu kemasan dikirim dari pabrik ke pedagang besar, lalu ke warung, kemudian dibeli oleh siswa. Jenis distribusi tersebut adalah ....","tak langsung dua tingkat","langsung","tak langsung tiga tingkat","semi langsung",0],[6,2,"Alur produsen → agen tunggal → agen → subagen → grosir → pengecer → konsumen akhir termasuk mata rantai distribusi yang ....","pendek","agak pendek","sangat panjang","panjang",2],[6,2,"Perbedaan mata rantai distribusi sangat panjang dan panjang adalah ....","yang sangat panjang tidak memakai grosir","yang sangat panjang memakai agen tunggal sebelum agen, sedangkan yang panjang tidak","yang panjang memakai agen tunggal","keduanya tidak memakai pengecer",1],[6,2,"Seorang pengrajin tas menjual produknya melalui akun media sosial dan mengirimkannya langsung ke pembeli lewat jasa kurir. Jenis saluran distribusi yang digunakan adalah ....","tak langsung satu tingkat","tak langsung tiga tingkat","semi langsung","langsung (produsen → konsumen)",3]];

// Convert data
D = D.map(function(r) {
  return [r[0], r[1], r[2], [r[3], r[4], r[5], r[6]], r[7]];
});

// Penjelasan untuk setiap soal
var E=["Kegiatan ekonomi adalah kegiatan manusia memenuhi kebutuhan lewat produksi, distribusi, dan konsumsi.","Tiga kegiatan pokok ekonomi: produksi (menghasilkan), distribusi (menyalurkan), konsumsi (menggunakan).","Petani yang menghasilkan beras sedang melakukan produksi, yaitu menghasilkan barang.","Kewirausahaan adalah kemampuan mengatur faktor produksi lain dan mengambil keputusan.","Saluran tidak langsung berurutan: produsen, grosir, pengecer, konsumen.","Distribusi membuat produk tersedia pada waktu, tempat, dan jumlah yang dibutuhkan.","Tujuan konsumsi adalah memperoleh manfaat untuk memenuhi kebutuhan, bukan sekadar menghabiskan barang.","Pabrik (produksi), pengiriman ke toko (distribusi), siswa memakai sepatu (konsumsi).","Produk sudah ada dan dibutuhkan, tetapi tidak sampai ke toko, jadi masalahnya ada pada distribusi.","Alat yang membantu proses produksi, seperti blender, termasuk modal.","Konsumsi dipengaruhi pendapatan, harga, selera, kebutuhan, dan lingkungan. Jumlah mesin pabrik terkait produksi.","Konsumsi memunculkan kebutuhan baru, sehingga produksi, distribusi, dan konsumsi berputar sebagai siklus.","Biaya tetap (FC) tidak berubah dalam jangka pendek meski output berubah.","Bahan baku bertambah mengikuti output, jadi termasuk biaya variabel.","Biaya total sama dengan biaya tetap ditambah biaya variabel: TC = FC + VC.","Biaya rata-rata adalah biaya total dibagi jumlah output: AC = TC ÷ Q.","TC = 1.500.000 + 2.500.000 = 4.000.000. AC = 4.000.000 ÷ 800 = Rp5.000.","MC = ΔTC ÷ ΔQ = 600.000 ÷ 100 = Rp6.000 per unit tambahan.","FC total tetap, tetapi dibagi ke lebih banyak unit sehingga FC per unit turun.","TC = 60 + 45 = 105. AC = 105 ÷ 3 = 35.","TC pada Q = 4 adalah 60 + 55 = 115, pada Q = 5 adalah 60 + 75 = 135. MC = 135 − 115 = 20.","MC Q4 ke Q5 = 20, sedangkan Q5 ke Q6 = 180 − 135 = 45. MC naik, jadi tambahan unit makin mahal.","MC = (2.200.000 − 1.800.000) ÷ (200 − 100) = 400.000 ÷ 100 = Rp4.000.","FC total tetap dalam kapasitas tertentu, tetapi FC per unit turun saat output naik. Pernyataan lain keliru: VC per unit dapat berubah, TC tidak turun saat Q naik, dan pada Q = 0 biaya total sama dengan FC.","Produksi adalah kegiatan memproses input menjadi output.","Faktor yang dipakai dalam proses produksi (buah, tenaga kerja, blender) disebut input.","TR = harga jual × jumlah terjual.","Laba = TR − TC.","Titik impas (BEP) terjadi saat TR = TC, sehingga usaha tidak laba dan tidak rugi.","Dalam Q = F(K, L, R, T): K modal, L tenaga kerja, R bahan baku, T teknologi.","Memilih cara membuat produk (mesin atau tenaga manusia) menjawab keputusan 'bagaimana'.","TR = 50 × Rp10.000 = Rp500.000.","TR = 200 × 12.000 = 2.400.000. Laba = 2.400.000 − 2.000.000 = Rp400.000.","TR = 100 × 8.000 = 800.000, lebih kecil dari TC 1.000.000, sehingga rugi Rp200.000.","Sebelum menambah produksi, bandingkan tambahan penerimaan dengan tambahan biaya.","TC − TR = 3.500.000 − 3.000.000 = 500.000. TR harus naik 500.000 agar TR = TC (BEP).","Produk marginal adalah tambahan output akibat tambahan satu unit input variabel.","Produk total adalah jumlah seluruh output yang dihasilkan.","Produk rata-rata adalah produk total dibagi jumlah input: AP = TP ÷ L.","Ukuran dapur adalah input tetap dalam jangka pendek. Tenaga kerja dan bahan baku adalah input variabel.","MP = TP(L=4) − TP(L=3) = 45 − 36 = 9.","MP: L1 = 10, L2 = 24 − 10 = 14, L3 = 36 − 24 = 12. MP tertinggi pada L = 2.","AP = TP ÷ L = 51 ÷ 5 = 10,2.","Hukum ini menyatakan bahwa bila satu input variabel terus ditambah sementara input lain tetap, tambahan output akhirnya makin kecil.","MP: L1 = 10, L2 = 14, L3 = 12, L4 = 9. MP mulai menurun pada L = 3 karena 12 lebih kecil dari 14.","MP pada L = 7 adalah 50 − 54 = −4, jadi MP negatif mulai pada L = 7.","Fase marginal menurun: MP masih positif tetapi makin kecil, sehingga TP masih naik.","Jika MP lebih kecil dari AP maka AP menurun. Pada L = 4, MP 9 lebih kecil dari AP 12 sehingga AP turun menjadi 11,25.","Kurva PPC menunjukkan batas maksimal kombinasi output dua barang yang dapat dihasilkan perekonomian.","Produksi terbatas karena sumber daya terbatas (kelangkaan).","Titik pada kurva PPC menunjukkan produksi yang efisien dan optimal.","Titik di luar kurva tidak mungkin dicapai dengan sumber daya dan teknologi saat ini.","Titik di dalam kurva berarti ada sumber daya menganggur atau belum efisien.","Pergeseran kurva ke kanan menandakan pertumbuhan ekonomi karena faktor produksi atau teknologi meningkat.","Biaya peluang = jumlah barang yang dikorbankan ÷ jumlah barang yang diperoleh.","Padi yang dikorbankan 100 − 90 = 10 ton untuk 20 bal kain. 10 ÷ 20 = 0,5 ton padi per bal kain.","Padi yang dikorbankan 70 − 40 = 30 ton untuk 20 bal kain. 30 ÷ 20 = 1,5 ton padi per bal kain.","Pengorbanan makin besar (10, 20, 30, 40) menunjukkan biaya peluang meningkat, sehingga kurva melengkung cekung ke luar.","Pada 30 bal kain padi maksimum sekitar 80 ton, jadi F (40) di dalam kurva. Pada 60 bal kain padi maksimum 40 ton, jadi G (80) di luar kurva.","Kapasitas produksi turun sehingga PPC bergeser ke kiri. Titik C yang dulu efisien kini melampaui kemampuan produksi, jadi berada di luar kurva baru.","Produksi adalah kegiatan manusia menghasilkan barang atau jasa untuk memenuhi kebutuhan.","Makanan dan minuman siap dikonsumsi manusia, jadi termasuk barang konsumsi. Spatula dan pisau termasuk barang modal.","Faktor produksi: alam, tenaga kerja, modal, dan keahlian (sumber daya pengusaha).","Hutan, hewan, air, dan sinar matahari termasuk sumber daya alam yang dapat diperbarui.","Alam dan tenaga kerja disebut faktor produksi asli. Modal dan keahlian adalah faktor produksi turunan.","Jasa yang tidak langsung memenuhi kebutuhan manusia disebut jasa tidak langsung. Guru, dokter, dan sirkus adalah jasa langsung.","Alat yang dipakai untuk menghasilkan barang lain (makanan) adalah barang modal.","Produksi tidak selalu menciptakan barang baru, tetapi bisa juga mengubah bentuk, mengubah sifat, atau menambah nilai guna.","Bagi produsen, tujuannya meningkatkan keuntungan dan menjaga kesinambungan perusahaan. Bagi konsumen, tujuannya tersedianya benda pemuas kebutuhan.","Kayu jati = faktor alam; gergaji dan mesin = modal; karyawan = tenaga kerja; Pak Budi yang mengatur proses = keahlian (pengusaha).","Tenaga kerja rohani memakai pikiran, rasa, dan karsa. Tenaga kerja jasmani memakai kekuatan fisik.","Karakteristik utama: tersedia alami, jumlah terbatas dan dapat langka, kualitas dan lokasi geografis berbeda, dan butuh biaya ekstraksi.","Distribusi adalah kegiatan menyampaikan barang atau jasa dari produsen ke konsumen yang membutuhkan.","Pengangkutan atau transportasi memindahkan barang antartempat.","Distribusi langsung menyalurkan barang tanpa perantara.","Grosir membeli dan menjual barang dalam jumlah besar. Pengecer menjual satuan.","Importir membeli barang dari luar negeri untuk dijual di dalam negeri. Eksportir menjual barang dalam negeri ke luar negeri.","Makelar menjual atau membeli atas nama orang lain. Komisioner menguasai atau memiliki barangnya.","Satu tingkat memakai satu perantara: produsen → pengecer → konsumen.","Penggudangan adalah menyimpan barang di gudang sebelum disalurkan.","Pabrik → pedagang besar → pengecer (warung) → konsumen adalah distribusi tak langsung dua tingkat, umumnya untuk barang harian.","Alur dengan agen tunggal, agen, subagen, grosir, dan pengecer termasuk mata rantai sangat panjang.","Sangat panjang: produsen → agen tunggal → agen → subagen → grosir → pengecer. Panjang: produsen → agen → subagen → grosir → pengecer (tanpa agen tunggal).","Tidak ada perantara pedagang antara produsen dan konsumen, jadi distribusi langsung. Kurir hanya jasa pengangkutan."];

// ============================================
// KONFIGURASI
// ============================================
var NQ = 30;
var DUR = 7200000;  // 120 menit
var KEY = "czhi-eko-v2-sheets";

// GOOGLE APPS SCRIPT DEPLOYMENT URL
// (Harus di-set setelah deploy script di Google Sheets)
var GOOGLE_APPS_SCRIPT_URL = "https://script.google.com/macros/s/AKfycbyoyLkg_qTcn1nwCl5vn57_ZttHSyiI97mnlAxxrJYGhL4W_A6zavyTklqrU15Euo8/exec";

// ============================================
// VARIABEL GLOBAL
// ============================================
var $ = function(i) { return document.getElementById(i); };
var st = null;
var tm = null;
var cf = 0;

// ============================================
// FUNGSI UTILITY
// ============================================
function shuffle(a) {
  a = a.slice();
  for (var i = a.length - 1; i > 0; i--) {
    var j = Math.floor(Math.random() * (i + 1));
    var t = a[i];
    a[i] = a[j];
    a[j] = t;
  }
  return a;
}

function saveLoacalStorage() {
  try { localStorage.setItem(KEY, JSON.stringify(st)); } catch(e) {}
}

function loadLocalStorage() {
  try { return JSON.parse(localStorage.getItem(KEY)); } catch(e) { return null; }
}

function show(id) {
  ["s0", "s1", "s2"].forEach(function(x) {
    $(x).hidden = (x !== id);
  });
  window.scrollTo(0, 0);
}

function escape_html(x) {
  x = String(x == null ? "" : x);
  return x.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;");
}

// ============================================
// GOOGLE SHEETS INTEGRATION
// ============================================
async function saveToGoogleSheets(record) {
  try {
    // Siapkan jawaban (B=Benar, S=Salah, -=Kosong)
    var jawaban = "";
    for (var i = 1; i <= 84; i++) {
      var ans = record.det[i];
      if (ans === 1) jawaban += "B";
      else if (ans === 0) jawaban += "S";
      else jawaban += "-";
    }
    
    // Data untuk dikirim
    var payload = {
      nama: record.nama,
      kelas: record.kelas,
      nilai: record.nilai,
      benar: record.benar,
      salah: record.salah,
      kosong: record.kosong,
      alasan: record.alasan,
      waktu: record.waktu,
      jawaban: jawaban
    };
    
    // Tampilkan status sedang mengirim
    showSyncStatus("sending");
    
    // Kirim ke Google Apps Script
    var response = await fetch(GOOGLE_APPS_SCRIPT_URL, {
      method: "POST",
      mode: "no-cors",
      cache: "no-cache",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify(payload)
    });
    
    // Tampilkan status berhasil
    showSyncStatus("success");
    
  } catch(e) {
    console.error("Error:", e);
    showSyncStatus("error");
  }
}

function showSyncStatus(status) {
  var statusDiv = $("sync-status");
  
  if (status === "sending") {
    statusDiv.innerHTML = '<div class="status-badge sending">⏳ Mengirim data ke Google Sheets...</div>';
  } else if (status === "success") {
    statusDiv.innerHTML = '<div class="status-badge success">✓ Data berhasil tersimpan di Google Sheets!</div>';
  } else if (status === "error") {
    statusDiv.innerHTML = '<div class="status-badge error">⚠ Error: Periksa koneksi internet Anda</div>';
  }
}

// ============================================
// MULAI UJIAN
// ============================================
function start() {
  var n = $("nm").value.trim();
  var k = $("kl").value.trim();
  
  if (!n || !k) {
    $("err").textContent = "Nama dan kelas wajib diisi.";
    return;
  }
  
  var pick = [];
  for (var m = 0; m < 7; m++) {
    var got = [];
    for (var l = 0; l < 3; l++) {
      var ids = [];
      D.forEach(function(q, i) {
        if (q[0] === m && q[1] === l) ids.push(i);
      });
      got.push(shuffle(ids)[0]);
    }
    var rest = [];
    D.forEach(function(q, i) {
      if (q[0] === m && got.indexOf(i) < 0) rest.push(i);
    });
    got.push(shuffle(rest)[0]);
    pick = pick.concat(got);
  }
  
  var left = [];
  D.forEach(function(q, i) {
    if (pick.indexOf(i) < 0) left.push(i);
  });
  pick = pick.concat(shuffle(left).slice(0, 2));
  
  st = {
    n: n,
    k: k,
    it: shuffle(pick).map(function(i) {
      return { i: i, o: shuffle([0, 1, 2, 3]) };
    }),
    a: Array(NQ).fill(-1),
    c: 0,
    end: Date.now() + DUR,
    done: false,
    why: null
  };
  
  saveLoacalStorage();
  run();
}

// ============================================
// JALANKAN UJIAN
// ============================================
function run() {
  show("s1");
  $("who").textContent = st.n + " · " + st.k;
  render();
  tick();
  clearInterval(tm);
  tm = setInterval(tick, 500);
}

// ============================================
// TIMER
// ============================================
function tick() {
  var r = Math.max(0, st.end - Date.now());
  var s = Math.ceil(r / 1000);
  var t = $("tm");
  
  t.textContent = String(Math.floor(s / 60)).padStart(2, "0") + ":" + String(s % 60).padStart(2, "0");
  t.className = s <= 300 ? "lo" : "";
  
  if (r <= 0) finish(true);
}

// ============================================
// RENDER SOAL
// ============================================
function render() {
  var c = st.c;
  var it = st.it[c];
  var q = D[it.i];
  
  $("qt").textContent = "Soal " + (c + 1) + " dari " + NQ + " · " + M[q[0]] + " · " + ["Mudah", "Sedang", "Sulit"][q[1]];
  $("qq").textContent = q[2];
  
  var h = "";
  it.o.forEach(function(oi, p) {
    h += '<button class="opt ' + (st.a[c] === p ? "on" : "") + '" data-p="' + p + '"><i class="opt-letter">' + "ABCD"[p] + '</i><span></span></button>';
  });
  $("ops").innerHTML = h;
  
  var sp = $("ops").querySelectorAll("span");
  it.o.forEach(function(oi, p) {
    sp[p].textContent = q[3][oi];
  });
  
  var expl = $("expl");
  if (st.a[c] >= 0) {
    var isCorrect = it.o[st.a[c]] === D[it.i][4];
    var explanation = E[it.i];
    var explClass = isCorrect ? "correct" : "wrong";
    var explTitle = isCorrect ? "✓ Jawaban Benar! (+3,33 poin)" : "✗ Jawaban Salah";
    
    expl.innerHTML = '<div class="explanation ' + explClass + '"><b>' + explTitle + '</b>' + escape_html(explanation) + '</div>';
  } else {
    expl.innerHTML = "";
  }
  
  $("pv").disabled = c === 0;
  $("nx").disabled = c === NQ - 1;
  
  var n = st.a.filter(function(x) { return x >= 0; }).length;
  $("prog").textContent = "Terjawab " + n + " dari " + NQ;
  $("pbar").style.width = (n / NQ * 100) + "%";
  
  var g = "";
  for (var i = 0; i < NQ; i++)
    g += '<button data-g="' + i + '" class="' + (st.a[i] >= 0 ? "ans " : "") + (i === c ? "cur" : "") + '" aria-label="Soal ' + (i + 1) + '">' + (i + 1) + '</button>';
  $("grid").innerHTML = g;
}

// ============================================
// EVENT LISTENER
// ============================================
$("ops").addEventListener("click", function(e) {
  var b = e.target.closest(".opt");
  if (!b) return;
  st.a[st.c] = +b.dataset.p;
  saveLoacalStorage();
  render();
});

$("grid").addEventListener("click", function(e) {
  var b = e.target.closest("button");
  if (!b) return;
  st.c = +b.dataset.g;
  saveLoacalStorage();
  render();
});

$("pv").onclick = function() {
  if (st.c > 0) {
    st.c--;
    saveLoacalStorage();
    render();
  }
};

$("nx").onclick = function() {
  if (st.c < NQ - 1) {
    st.c++;
    saveLoacalStorage();
    render();
  }
};

$("go").onclick = start;

$("fin").onclick = function() {
  var k = st.a.filter(function(x) { return x < 0; }).length;
  
  if (!cf) {
    cf = 1;
    $("fin").textContent = (k ? k + " soal belum dijawab. " : "") + "Klik lagi untuk mengumpulkan";
    setTimeout(function() {
      cf = 0;
      $("fin").textContent = "Kumpulkan Jawaban";
    }, 5000);
    return;
  }
  
  finish(false);
};

// ============================================
// SELESAI UJIAN
// ============================================
function finish(auto) {
  clearInterval(tm);
  
  var ok = 0;
  var pm = [0, 0, 0, 0, 0, 0, 0];
  var tt = [0, 0, 0, 0, 0, 0, 0];
  
  st.it.forEach(function(it, i) {
    var q = D[it.i];
    var a = st.a[i];
    tt[q[0]]++;
    
    if (a >= 0 && it.o[a] === q[4]) {
      ok++;
      pm[q[0]]++;
    }
  });
  
  if (auto && !st.why) st.why = "time";
  
  st.done = true;
  st.score = Math.round((ok / NQ) * 100);
  st.correct = ok;
  
  saveLoacalStorage();
  
  $("rwho").textContent = st.n + " · Kelas " + st.k;
  $("sc").textContent = st.score;
  
  setTimeout(function() {
    var arc = document.getElementById("score-arc");
    if (arc) {
      var circ = 364.4;
      arc.style.strokeDashoffset = String(circ - (circ * st.score / 100));
      var color = st.score >= 75 ? "#34c48a" : st.score >= 50 ? "#3d8ef0" : "#f05252";
      arc.setAttribute("stroke", color);
    }
  }, 200);
  
  $("rd").textContent = "Benar " + ok + " dari " + NQ + " soal (Skor: " + st.score + "/100)" + (st.why === "time" ? " (waktu habis)" : st.why === "leave" ? " (halaman ditinggalkan)" : ".");
  
  var t = "<tr><th>Materi</th><th>Benar</th></tr>";
  for (var m = 0; m < 7; m++)
    t += "<tr><td>" + M[m] + "</td><td>" + pm[m] + " / " + tt[m] + "</td></tr>";
  $("rt").innerHTML = t;
  
  review();
  show("s2");
  
  // Siapkan record untuk Google Sheets
  var rec = {
    nama: st.n,
    kelas: st.k,
    nilai: st.score,
    benar: ok,
    salah: NQ - ok - st.a.filter(function(x) { return x < 0; }).length,
    kosong: st.a.filter(function(x) { return x < 0; }).length,
    alasan: st.why === "time" ? "waktu habis" : st.why === "leave" ? "pindah tab" : "selesai",
    waktu: new Date().toISOString(),
    det: {}
  };
  
  st.it.forEach(function(it, i) {
    var a = st.a[i];
    var no = i + 1;
    if (a < 0) {
      rec.det[no] = -1;
    } else {
      rec.det[no] = (it.o[a] === D[it.i][4]) ? 1 : 0;
    }
  });
  
  // Kirim ke Google Sheets
  saveToGoogleSheets(rec);
}

$("again").onclick = function() {
  try { localStorage.removeItem(KEY); } catch(e) {}
  location.reload();
};

// ============================================
// REVIEW JAWABAN
// ============================================
function review() {
  var h = '<h2 style="font:600 1rem/1 Inter,sans-serif;color:var(--fg);margin-bottom:14px;">Jawaban & Pembahasan</h2>';
  
  st.it.forEach(function(it, i) {
    var q = D[it.i];
    var a = st.a[i];
    var kp = it.o.indexOf(q[4]);
    var good = a === kp;
    
    h += '<div class="rv ' + (good ? "g" : "b") + '"><div class="rv-tag">Soal ' + (i + 1) + " · " + M[q[0]] + " · " + ["Mudah", "Sedang", "Sulit"][q[1]] + " · " + (good ? "✓ Benar" : a < 0 ? "— Tidak dijawab" : "✗ Salah") + '</div><div class="q-text">' + escape_html(q[2]) + "</div>";
    
    it.o.forEach(function(oi, pp) {
      var c = pp === kp ? " k" : (pp === a ? " w" : "");
      h += '<div class="ro' + c + '"><i>' + "ABCD"[pp] + '</i><span>' + escape_html(q[3][oi]) + (pp === kp ? " — kunci" : (pp === a && pp !== kp ? " — jawabanmu" : "")) + '</span></div>';
    });
    
    h += '<div class="pb"><b>Pembahasan:</b> ' + escape_html(E[it.i]) + '</div></div>';
  });
  
  $("rv").innerHTML = h;
}

// ============================================
// LOAD STATE
// ============================================
var p = loadLocalStorage();
if (p && p.it && p.it.length === NQ) {
  st = p;
  if (st.done) {
    finish(false);
  } else if (st.end <= Date.now()) {
    finish(true);
  } else {
    run();
  }
}
</script>
</body>
</html>

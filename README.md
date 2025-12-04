<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>SMPN 1 SINDANG</title>

<style>
:root{
  --maroon:#7a0b10;
  --gold:#d4af37;
  --bg:#000;
  --card:#fff;
}
*{box-sizing:border-box;margin:0;padding:0;}
body{font-family:Arial,sans-serif;color:#fff;scroll-behavior:smooth;}

/* VIDEO BACKGROUND HD */
#bgVideo{
  position: fixed;
  top:0; left:0;
  width:100%;
  height:100%;
  object-fit: cover;
  z-index: -2;
  filter: brightness(0.85) contrast(1.1) saturate(1.2);
  transition: filter 0.5s;
}
body::before{
  content:"";
  position: fixed;
  inset:0;
  background: rgba(0,0,0,0.15); /* overlay lebih tipis */
  z-index: -1;
}

/* HEADER */
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 20px;
  background: rgba(0,0,0,0.5);
  backdrop-filter: blur(6px);
  border-bottom: 1px solid #333;
  position: sticky;
  top: 0;
  z-index: 100;
  box-shadow: 0 2px 12px rgba(0,0,0,0.4);
}
header img { width:60px; border-radius:8px; border:2px solid var(--gold);}
header .header-text { display:flex; flex-direction:column; margin-left:10px;}
header h1 { margin:0; font-size:1.1rem; color: var(--gold); text-shadow:0 0 6px rgba(0,0,0,0.7);}
header p { margin:0; font-size:0.8rem; color:#fff; text-shadow:0 0 4px rgba(0,0,0,0.7);}
nav { display:flex; gap:8px; flex-wrap:nowrap;}
nav a {
  padding:5px 12px; font-size:0.85rem; background:rgba(17,17,17,0.7);
  color:#fff; text-decoration:none; border-radius:6px; font-weight:600;
  border:1px solid var(--gold); transition:0.25s; box-shadow:0 0 6px rgba(212,175,55,0.5);
}
nav a:hover { background:var(--gold); color:#000; transform:translateY(-2px); box-shadow:0 0 12px rgba(212,175,55,0.9);}
nav a.active { background:var(--gold); color:#000; box-shadow:0 0 14px rgba(212,175,55,1);}

/* CONTAINER & SECTION */
.container{max-width:1200px;margin:auto;padding:20px;}
section{
  background: rgba(0,0,0,0.55);
  padding:22px;
  border-radius:14px;
  margin-bottom:20px;
  border:1px solid #444;
  box-shadow:0 4px 12px rgba(0,0,0,0.5);
}
h2{
  margin:0 0 12px;
  color:var(--gold);
  border-left:6px solid var(--gold);
  padding-left:10px;
  text-shadow:0 0 6px rgba(0,0,0,0.5);
}
.lead{font-size:1rem;color:#f9f9f9;margin-bottom:10px; text-shadow:0 0 3px rgba(0,0,0,0.5);}
/* Kepala Sekolah */
.kepsek-container {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-bottom: 40px;
}

.kepsek-card {
  text-align: center;
}

.kepsek-img img {
  width: 220px;
  height: 280px;
  object-fit: cover;
  border-radius: 15px;
  border: 3px solid #fff;
  box-shadow: 0 0 15px #fff;
}

.kepsek-info h3 {
  margin-top: 10px;
  font-size: 1.5rem;
  font-weight: bold;
}

.kepsek-info p {
  margin-top: -5px;
  font-size: 1rem;
  opacity: 0.8;
}


/* GURU GRID */
.guru-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(180px,1fr)); gap:18px; margin-top:12px;}
.guru-card { background:#222; border-radius:12px; overflow:hidden; border:2px solid #555; text-align:center; transition:transform 0.3s, box-shadow 0.3s;}
.guru-card:hover { transform: translateY(-6px) scale(1.03); box-shadow:0 10px 26px rgba(212,175,55,0.6);}
.guru-img { width:100%; padding-top:100%; position:relative; overflow:hidden; background:#111;}
.guru-img img { position:absolute; top:0; left:0; width:100%; height:100%; object-fit:cover; border-bottom:2px solid #555; transition:0.3s, filter 0.3s, transform 0.3s; box-shadow:0 0 14px rgba(212,175,55,0.6);}
.guru-img img:hover { filter: brightness(1.2); transform: scale(1.05); box-shadow:0 0 24px rgba(212,175,55,1);}
.guru-info { padding:12px; background:linear-gradient(180deg, rgba(255,248,235,0.05), rgba(255,248,220,0.02));}
.guru-info h3 { margin:0; color: var(--gold); font-size:1rem; text-shadow:0 0 3px rgba(0,0,0,0.5);}
.guru-info p { margin:4px 0 0; color:#fff; font-size:0.88rem; text-shadow:0 0 2px rgba(0,0,0,0.4);}

/* ESKUL & GALERI SCROLL */
.eskul-scroll, .gallery-scroll { display:flex; gap:12px; overflow-x:auto; padding-bottom:8px; scroll-snap-type:x mandatory;}
.eskul-card, .gallery-card { flex:0 0 auto; width:180px; border-radius:12px; overflow:hidden; background:#222; scroll-snap-align:start; text-align:center; transition:transform 0.3s, box-shadow 0.3s;}
.eskul-card img, .gallery-card img { width:100%; aspect-ratio:9/16; object-fit:cover; display:block; border-bottom:2px solid #555; box-shadow:0 0 14px rgba(212,175,55,0.6); transition:0.3s, filter 0.3s, transform 0.3s;}
.eskul-card:hover, .gallery-card:hover { transform:scale(1.06); box-shadow:0 0 24px rgba(212,175,55,0.8);}
.eskul-card:hover img, .gallery-card:hover img { filter:brightness(1.2); transform:scale(1.05); box-shadow:0 0 20px rgba(212,175,55,1);}
.eskul-card p { margin:6px 0 8px; color:#fff; font-weight:600;}
.eskul-scroll::-webkit-scrollbar, .gallery-scroll::-webkit-scrollbar { height:6px;}
.eskul-scroll::-webkit-scrollbar-thumb, .gallery-scroll::-webkit-scrollbar-thumb { background: rgba(212,175,55,0.7); border-radius:3px;}
.eskul-scroll::-webkit-scrollbar-track, .gallery-scroll::-webkit-scrollbar-track { background: rgba(0,0,0,0.2);}
.gallery-scroll {
  display: flex;
  gap: 15px;
  overflow-x: auto;
  padding: 10px;
  scroll-behavior: smooth;
}

#galeri {
  padding: 40px 20px;
  text-align: center;
}

.gallery-container {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 25px;
}

.gallery-row {
  display: flex;
  justify-content: center;
  gap: 15px;
  flex-wrap: wrap;
}

.gallery-card {
  width: 180px;
  height: 250px;
  overflow: hidden;
  border-radius: 10px;
  border: 2px solid #fff;
  box-shadow: 0 0 10px #fff;
}

.gallery-card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

#video {
  padding: 40px 20px;
  text-align: center;
}

.video-grid {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 25px;
  margin-top: 20px;
}

.video-item {
  background: rgba(255, 255, 255, 0.1);
  padding: 10px;
  border-radius: 12px;
  box-shadow: 0 0 10px #fff;
  backdrop-filter: blur(4px);
}

.video-item video {
  width: 100%;
  height: 180px;
  border-radius: 10px;
  object-fit: cover;
}

.video-item p {
  margin-top: 8px;
  font-size: 0.9rem;
}

/* FASILITAS */
.fasilitas-grid{ display:grid; grid-template-columns:repeat(auto-fit,minmax(240px,1fr)); gap:16px; margin-top:12px;}
.fasilitas-box{ background:#222; border:2px solid #555; border-radius:14px; padding:12px; text-align:center; transition:.3s;}
.fasilitas-box:hover{ transform:translateY(-6px) scale(1.03); box-shadow:0 10px 26px rgba(212,175,55,0.6);}
.fasilitas-box img{ width:100%; height:160px; object-fit:cover; border-radius:10px; margin-bottom:8px; box-shadow:0 0 14px rgba(212,175,55,0.6); transition:0.3s, filter 0.3s, transform 0.3s;}
.fasilitas-box:hover img{ filter:brightness(1.2); transform:scale(1.05); box-shadow:0 0 20px rgba(212,175,55,1);}

/* FORM */
form input, form textarea { width:100%; padding:10px; margin:6px 0; background:#000; border:1px solid #555; color:#fff; border-radius:8px;}
button{ padding:10px 18px; background:var(--gold); border:none; border-radius:10px; font-weight:700; margin-top:5px; cursor:pointer;}
#musicBtn{position:fixed; bottom:20px; right:20px; padding:14px 20px; border-radius:50px; background:var(--gold); color:#111; font-weight:800; border:3px solid #111; cursor:pointer; z-index:200;}
</style>
</head>
<body>

<!-- VIDEO BACKGROUND -->
<video autoplay muted loop id="bgVideo">
  <source src="VN20251012_064140.mp4" type="video/mp4">
  Browser Anda tidak mendukung video.
</video>

<!-- MUSIK -->
<audio id="bgMusic" autoplay loop>
  <source src="DJ MASHUP X MELODY TANTE CULIK AKU DONG V7 BY KHARIS SOPAN FT NESS FX VIRAL FYP TIKTOK MENGKANEE!!.mp3" type="audio/mpeg">
</audio>
<button id="musicBtn">MUSIK ON/OFF</button>

<header>
  <div style="display:flex; align-items:center;">
    <img src="logo nesasin.png" alt="Logo SMPN 1 Sindang">
    <div class="header-text">
      <h1>SMPN 1 SINDANG</h1>
      <p>BERAKSI</p>
    </div>
  </div>

  <nav>
    <a href="#profil" class="active">Profil</a>
    <a href="#guru">Guru</a>
    <a href="#fasilitas">Fasilitas</a>
    <a href="#eskul">Eskul</a>
    <a href="#galeri">Galeri</a>
    <a href="#kontak">Kontak</a>
  </nav>
</header>

<div class="container">

<!-- PROFIL -->
<section id="profil">
  <h2>Profil Sekolah</h2>
  <p class="lead">
    SMPN 1 Sindang Beraksi adalah wujud semangat sekolah dalam menciptakan lingkungan belajar yang aktif, kreatif, dan inspiratif. Setiap guru dan siswa berperan aktif dalam berbagai kegiatan akademik maupun ekstrakurikuler, mulai dari olahraga, seni, hingga inovasi teknologi. Dengan moto “Beraksi”, sekolah ini mendorong seluruh warga sekolah untuk berinisiatif, berkreasi, dan berkontribusi nyata bagi prestasi, karakter, dan kemajuan masyarakat. SMPN 1 Sindang bukan hanya tempat belajar, tetapi juga laboratorium aksi nyata untuk membentuk generasi unggul.
  </p>

  <!-- VISI -->
  <h3 style="margin-top:25px;">Visi</h3>
  <p class="lead">
    “Terwujudnya peserta didik yang berkarakter, berprestasi, berkompetensi, dan berakhlak mulia melalui lingkungan pendidikan yang aman, nyaman, dan berdaya saing.”
  </p>

  <!-- MISI -->
  <h3 style="margin-top:20px;">Misi</h3>
  <ul class="lead" style="text-align:left; max-width:800px; margin:0 auto; line-height:1.6;">
    <li>Menciptakan suasana belajar yang aktif, kreatif, inovatif, dan menyenangkan.</li>
    <li>Mengembangkan potensi akademik maupun non-akademik siswa secara optimal.</li>
    <li>Menanamkan nilai karakter, kedisiplinan, dan budaya beraksi di lingkungan sekolah.</li>
    <li>Meningkatkan kompetensi guru dan kualitas proses pembelajaran secara berkelanjutan.</li>
    <li>Memperkuat kerja sama antara sekolah, keluarga, dan masyarakat.</li>
  </ul>
</section>


<!-- GURU -->
<section id="guru">
  <h2>Data Guru</h2>
  <p class="lead">Berikut adalah daftar guru SMPN 1 Sindang.</p>

  <!-- Kepala Sekolah di Tengah -->
  <div class="kepsek-container">
    <div class="kepsek-card">
      <div class="kepsek-img">
        <img src="logo nesasin.png" alt="Kepala Sekolah">
      </div>
      <div class="kepsek-info">
        <h3>Nama Kepala Sekolah</h3>
        <p>Kepala Sekolah</p>
      </div>
    </div>
  </div>

  <!-- GRID GURU -->
  <div class="guru-grid">

    <div class="guru-card"><div class="guru-img"><img src="EKA.JPG" alt="EKA"></div><div class="guru-info"><h3>EKA</h3><p>Guru</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="ASEP.JPG" alt="ASEP"></div><div class="guru-info"><h3>Asep</h3><p>Guru</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="DEDEN (1).JPG" alt="DEDEN"></div><div class="guru-info"><h3>Deden</h3><p>Guru</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="ARIF.JPG" alt="ARIF"></div><div class="guru-info"><h3>Arif</h3><p>Guru</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="DEDEN (2).jpg" alt="NUNUY"></div><div class="guru-info"><h3>Nunuy</h3><p>Guru</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="SUSI.JPG" alt="SUSI"></div><div class="guru-info"><h3>SUSI SUSILAWATI S.Pd</h3><p>GURU B. INDONESIA</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="YOYO.jpg" alt="YOYO"></div><div class="guru-info"><h3>YOYO ROHAYA S.Pd</h3><p>GURU IPS</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="DEDE.JPG" alt="DEDE"></div><div class="guru-info"><h3>DEDE SUMIATI S.Pd</h3><p>GURU IPA</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="DEDEN (2).jpg" alt="NUNUY"></div><div class="guru-info"><h3>NUNUY RATNAWULAN.S.Pd.,M.P </h3><p>GURU MATEMATIKA</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="GURU (1).JPG" alt="SUSI"></div><div class="guru-info"><h3>NYAI FAHIYATUL S.Pd.I</h3><p>GURU INFORMATIKA</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="GURU (2).JPG" alt="YOYO"></div><div class="guru-info"><h3>YOYO ROHAYA S.Pd</h3><p>Guru</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="GURU (3).JPG" alt="DEDE"></div><div class="guru-info"><h3>DEDE SUMIATI S.Pd</h3><p>Guru</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="tu (1).JPG" alt="Neni"></div><div class="guru-info"><h3>Neni</h3><p>Guru</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="tu (2).JPG" alt="Yoyo"></div><div class="guru-info"><h3>Yoyo</h3><p>Guru</p></div></div>
    <div class="guru-card"><div class="guru-img"><img src="tu (3).JPG" alt="Dede"></div><div class="guru-info"><h3>Dede</h3><p>Guru</p></div></div>

  </div>
</section>


<!-- FASILITAS -->
<section id="fasilitas">
  <h2>Fasilitas Sekolah</h2>
  <div class="fasilitas-grid">
    <div class="fasilitas-box"><img src="LAPANG.jpeg" alt="Lapangan"><p>Lapangan</p></div>
    <div class="fasilitas-box"><img src="PMR R (1).jpeg" alt="RUANG PMR"><p>Ruang PMR</p></div>
    <div class="fasilitas-box"><img src="GAZEBO.jpeg" alt="GAZEBO"><p>Gazebo</p></div>
    <div class="fasilitas-box"><img src="GADA.jpeg" alt="GADA"><p>Gada</p></div>
    <div class="fasilitas-box"><img src="TU RUANG.jpeg" alt=""><p>RUANG TU</p></div>
        <div class="fasilitas-box"><img src="WC SISWA.jpeg" alt="Lapangan"><p>WC SISWA</p></div>
    <div class="fasilitas-box"><img src="IPA.jpeg" alt="RUANG PMR"><p>LAB IPA</p></div>
    <div class="fasilitas-box"><img src="MUSOLA.jpeg" alt="GAZEBO"><p>MUSOLA</p></div>
    <div class="fasilitas-box"><img src="GADA.jpeg" alt="GADA"><p>Gada</p></div>
    <div class="fasilitas-box"><img src="TU RUANG.jpeg" alt=""><p>RUANG TU</p></div>
  </div>
</section>

<!-- ESKUL -->
<section id="eskul">
  <h2>Ekstrakurikuler</h2>
  <div class="eskul-scroll">
    <div class="eskul-card"><img src="zaskia.jpeg" alt="Pramuka"><p>Pramuka</p></div>
    <div class="eskul-card"><img src="model 1 (2).jpeg" alt="Volley"><p>VOLLEY</p></div>
    <div class="eskul-card"><img src="model 1 (1).jpeg" alt="Garuda"><p>Garuda</p></div>
    <div class="eskul-card"><img src="model 1 (3).jpeg" alt="OSIS"><p>OSIS</p></div>
    <div class="eskul-card"><img src="model 1 (4).jpeg" alt="PMR"><p>PMR</p></div>
    <div class="eskul-card"><img src="adinda.jpeg" alt="PRAMUKA"><p>pramuka</p></div>
    <div class="eskul-card"><img src="pramuka dp 1 (1).jpeg" alt="Pramuka"><p>Pramuka</p></div>
    <div class="eskul-card"><img src="pramuka dp 1 (2).jpeg" alt="PRAMUKA"><p>PRAMUKA</p></div>
    <div class="eskul-card"><img src="pramuka dp 1 (3).jpeg" alt="Garuda"><p>Garuda</p></div>
    <div class="eskul-card"><img src="model 1 (3).jpeg" alt="OSIS"><p>OSIS</p></div>
    <div class="eskul-card"><img src="model 1 (4).jpeg" alt="PMR"><p>PMR</p></div>
    <div class="eskul-card"><img src="adinda.jpeg" alt="PRAMUKA"><p>pramuka</p></div>
  </div>
</section>
<section id="eskul">
  <h2>Ekstrakurikuler</h2>
  <div class="eskul-scroll">
 
    <div class="eskul-card"><img src="pramuka dp 1 (1).jpeg" alt="Pramuka"><p>PRAMUKA</p></div>
    <div class="eskul-card"><img src="pramuka dp 1 (2).jpeg" alt="PRAMUKA"><p>PRAMUKA</p></div>
    <div class="eskul-card"><img src="pramuka dp 1 (3).jpeg" alt="Garuda"><p>PRAMUKA</p></div>
    <div class="eskul-card"><img src="pramuka dp 4 (1).jpeg" alt="OSIS"><p>PRAMUKA</p></div>
    <div class="eskul-card"><img src="pramuka dp 4 (2).jpeg" alt="PMR"><p>PRAMUKA</p></div>
    <div class="eskul-card"><img src="pramuka dp 4 (3).jpeg" alt="PRAMUKA"><p>PRAMUKA</p></div>
  </div>
</section>

<!-- GALERI -->
<section id="galeri">
  <h2>Galeri Kegiatan</h2>
  <p class="lead">Dokumentasi berbagai kegiatan SMPN 1 Sindang.</p>

  <div class="gallery-container">

    <!-- Baris 1 -->
    <div class="gallery-row">
      <div class="gallery-card"><img src="barisan guru (2).jpeg" alt="Upacara Bendera"></div>
      <div class="gallery-card"><img src="barisan guru (3).jpeg" alt="Kegiatan Pramuka"></div>
      <div class="gallery-card"><img src="barisan guru (4).jpeg" alt="Lomba Seni"></div>
      <div class="gallery-card"><img src="barisan guru (5).jpeg" alt="Kegiatan Eskul"></div>
      <div class="gallery-card"><img src="barisan guru (6).jpeg" alt="Belajar di Kelas"></div>
    </div>

    <!-- Baris 2 -->
    <div class="gallery-row">
      <div class="gallery-card"><img src="LADIS PRAMUKA.jpeg" alt="Upacara Bendera"></div>
      <div class="gallery-card"><img src="GALERI PRAMUKA.jpeg" alt="Kegiatan Pramuka"></div>
      <div class="gallery-card"><img src="pramuka 1 (2).jpeg" alt="Lomba Seni"></div>
      <div class="gallery-card"><img src="E PRAMUKA.jpeg" alt="Kegiatan Eskul"></div>
      <div class="gallery-card"><img src="nesasin.4.jpeg" alt="Belajar di Kelas"></div>
    </div>

    <!-- Baris 3 -->
    <div class="gallery-row">
      <div class="gallery-card"><img src="hguru (1).jpeg" alt="Upacara Bendera"></div>
      <div class="gallery-card"><img src="hguru (2).jpeg" alt="Kegiatan Pramuka"></div>
      <div class="gallery-card"><img src="hguru (3).jpeg" alt="Lomba Seni"></div>
      <div class="gallery-card"><img src="hguru (4).jpeg" alt="Kegiatan Eskul"></div>
      <div class="gallery-card"><img src="hguru (5).jpeg" alt="Belajar di Kelas"></div>
    </div>
    <div class="gallery-row">
      <div class="gallery-card"><img src="hguru (6).jpeg" alt="Upacara Bendera"></div>
      <div class="gallery-card"><img src="barisan guru (7).jpeg" alt="Kegiatan Pramuka"></div>
      <div class="gallery-card"><img src="barisan guru (8).jpeg" alt="Lomba Seni"></div>
      <div class="gallery-card"><img src="barisan guru (9).jpeg" alt="Kegiatan Eskul"></div>
      <div class="gallery-card"><img src="sifa.jpeg" alt="Belajar di Kelas"></div>
    </div>
  </div>
</section>

  <section id="video-selection">
    <h2>Video NESASIN</h2>
    <div class="media-container">
      <!-- 20 Video dengan keterangan -->
   <!-- VIDEO -->
<section id="video">
  <h2>Video Kegiatan</h2>
  <p class="lead">Dokumentasi berbagai aktivitas SMPN 1 Sindang.</p>

  <div class="video-grid">

      <div class="video-item"><video controls src="VN20240912_020700.mp4"></video><p>Keterangan: Video Profil</p></div>
      <div class="video-item"><video controls src="muter.mp4"></video><p>Keterangan: koreo</p></div>
      <div class="video-item"><video controls src="muter 2.mp4"></video><p>Keterangan: koreo</p></div>
      <div class="video-item"><video controls src="video koreo.mp4"></video><p>koreo huruf</p></div>
      <div class="video-item"><video controls src="sayaciptaan.mp4"></video><p>ai</p></div>
      <div class="video-item"><video controls src="robot 3.mp4"></video><p>random</p></div>
      <div class="video-item"><video controls src="video7.mp4"></video><p>Keterangan: Ujian Sekolah</p></div>
      <div class="video-item"><video controls src="video8.mp4"></video><p>Keterangan: Upacara Bendera</p></div>
      <div class="video-item"><video controls src="video9.mp4"></video><p>Keterangan: Kegiatan Seni</p></div>
      <div class="video-item"><video controls src="video10.mp4"></video><p>Keterangan: Kegiatan Olahraga</p></div>
      <div class="video-item"><video controls src="video11.mp4"></video><p>Keterangan: Kegiatan Prakarya</p></div>
      <div class="video-item"><video controls src="video12.mp4"></video><p>Keterangan: Laboratorium</p></div>
      <div class="video-item"><video controls src="video13.mp4"></video><p>Keterangan: Ekstrakurikuler PMR</p></div>
      <div class="video-item"><video controls src="video14.mp4"></video><p>Keterangan: English Club</p></div>
      <div class="video-item"><video controls src="video15.mp4"></video><p>Keterangan: Ekstrakurikuler Robotik</p></div>
      <div class="video-item"><video controls src="video16.mp4"></video><p>Keterangan: Kegiatan Lapangan</p></div>
      <div class="video-item"><video controls src="video17.mp4"></video><p>Keterangan: Seni Tari</p></div>
      <div class="video-item"><video controls src="video18.mp4"></video><p>Keterangan: Musik dan Paduan Suara</p></div>
      <div class="video-item"><video controls src="video19.mp4"></video><p>Keterangan: Kegiatan Ekstrakurikuler Lain</p></div>
      <div class="video-item"><video controls src="video20.mp4"></video><p>Keterangan: Penutupan Kegiatan Sekolah</p></div>

  </div>
</section>


<!-- KONTAK -->
<section id="kontak">
  <h2>Kontak</h2>
  <form>
    <input type="text" placeholder="Nama" required>
    <input type="email" placeholder="Email" required>
    <textarea placeholder="Pesan" rows="4" required></textarea>
    <button type="submit">Kirim</button>
  </form>
</section>
  <!-- Formulir -->
  <section id="formulir">
    <h2>Download Formulir Pramuka Garuda</h2>
    <a href="Dokumen_Formulir.docx" download class="download-btn">Download Formulir</a>
  </section>

</div>

<footer style="text-align:center;padding:18px;color:#fff;background:linear-gradient(90deg,var(--maroon),#a21b22); box-shadow:0 -2px 12px rgba(0,0,0,0.5);">
  &copy; 2025 SMPN 1 SINDANG • “Berprestasi – Berbudaya – Berkarakter”
</footer>

<script>
// Smooth scroll + active nav highlight
const sections=document.querySelectorAll('section');
const navLinks=document.querySelectorAll('nav a');
window.addEventListener('scroll',()=>{
  let current="";
  sections.forEach(s=>{
    const top=s.offsetTop-100;
    if(scrollY>=top) current=s.getAttribute('id');
  });
  navLinks.forEach(a=>a.classList.remove('active'));
  document.querySelector('nav a[href="#'+current+'"]')?.classList.add('active');
});

// Musik ON/OFF
const music=document.getElementById('bgMusic');
const musicBtn=document.getElementById('musicBtn');
musicBtn.addEventListener('click',()=>{
  if(music.paused){music.play(); musicBtn.textContent="MUSIK ON";}
  else{music.pause(); musicBtn.textContent="MUSIK OFF";}
});
</script>

</body>
</html>

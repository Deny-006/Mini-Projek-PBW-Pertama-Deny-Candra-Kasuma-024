# 🎨 Website Portofolio – Deny Candra Kasuma

Project ini merupakan website portfolio statis yang dibuat menggunakan HTML, CSS, Bootstrap 5, dan Vue JS (CDN). Website ini memiliki beberapa section utama yaitu:

- Home (Hero Section)
- About Me (Professional Skills)
- Certificates (Selected Projects)

Website dirancang menggunakan struktur dasar HTML yang benar serta styling terpisah pada file style.css. Bootstrap digunakan untuk membantu layouting dan responsive design, sedangkan Vue JS digunakan untuk interpolation ({{ }}), data(), dan mounting aplikasi ke #app.

# 📂 Struktur Repository

- File index.html berisi struktur website dan script Vue JS.
- File style.css berisi seluruh styling tampilan.
- Folder images berisi gambar profil yang digunakan pada Hero Section.

# 🖼️ Dokumentasi Tampilan Website

# 🖥️ Penjelasan Setiap Section / Fitur
### 1. Navbar

Navbar dibuat menggunakan Bootstrap 5 dengan posisi fixed-top agar selalu berada di atas saat halaman di-scroll.

Potongan Kode:

<nav class="navbar navbar-expand-lg navbar-dark fixed-top custom-nav">
  <div class="container">
    <a class="navbar-brand fw-bold logo-text" href="#home">{{ name }}</a>

    <button class="navbar-toggler" data-bs-toggle="collapse" data-bs-target="#nav">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="nav">
      <ul class="navbar-nav ms-auto">
        <li class="nav-item"><a class="nav-link" href="#home">Home</a></li>
        <li class="nav-item"><a class="nav-link" href="#about">About</a></li>
        <li class="nav-item"><a class="nav-link" href="#works">Works</a></li>
      </ul>
    </div>
  </div>
</nav>

Penjelasan:

- navbar-expand-lg → membuat navbar responsive.
- fixed-top → navbar tetap di atas.
- {{ name }} → menggunakan interpolation Vue JS untuk menampilkan nama secara dinamis.

### 2. Home (Hero Section)

Hero section berisi perkenalan singkat, nama, role, deskripsi, tombol portfolio, dan gambar profil.

Potongan Kode:

<section id="home" class="hero">
  <div class="container">
    <div class="row align-items-center">

      <div class="col-md-6">
        <h5 class="small-text">Hello, I'm</h5>
        <h1 class="main-name">{{ name }}</h1>
        <h4 class="role-text">{{ role }}</h4>

        <p class="hero-desc mt-4">
          {{ about }}
        </p>

        <a href="#works" class="btn btn-custom mt-3">View Portfolio</a>
      </div>

      <div class="col-md-6 text-center">
        <img src="images/Deny Candra Kasuma.jpg" class="hero-img">
      </div>

    </div>
  </div>
</section>
Penjelasan:

- Menggunakan Grid System Bootstrap (row, col-md-6).
- Data diambil dari Vue:

```javascript
data() {
  return {
    name: "Deny Candra Kasuma",
    role: "Digital Designer | Illustrator | Photographer",
    about: "Saya adalah Digital Designer..."
  }
}
```

- Minimal 1 gambar terpenuhi melalui <img class="hero-img">.
- CSS pada .hero menggunakan min-height: 100vh agar tampil full screen.

### 3. About Me (Professional Skills)

Section ini menampilkan daftar kemampuan dalam bentuk progress bar.

Potongan Kode:

<section id="about" class="section">
  <div class="container">
    <h2 class="section-title text-center">Professional Skills</h2>

    <div v-for="skill in skills" class="mb-4">
      <div class="d-flex justify-content-between">
        <span>{{ skill.name }}</span>
        <span>{{ skill.level }}%</span>
      </div>
      <div class="progress">
        <div class="progress-bar"
             :style="{width: skill.level + '%'}"></div>
      </div>
    </div>
  </div>
</section>

Penjelasan:

- v-for="skill in skills" → menampilkan data skill secara berulang.
- :style="{width: skill.level + '%'}" → mengatur lebar progress bar secara dinamis.

Data skills:

```javascript
skills: [
  { name: "Poster Design", level: 90 },
  { name: "Digital Illustration", level: 85 },
  { name: "Photography", level: 80 },
  { name: "Adobe Photoshop", level: 88 },
  { name: "Adobe Illustrator", level: 84 }
]
```

Progress bar menggunakan komponen Bootstrap dan dikustomisasi melalui style.css.

### 4. Certificates (Selected Projects)

Pada kode yang digunakan, bagian Certificates direpresentasikan oleh section Works yang menampilkan daftar project dalam bentuk card.

Potongan Kode:

<section id="works" class="section-dark">
  <div class="container">
    <h2 class="section-title text-center mb-5">Selected Projects</h2>

    <div class="row">
      <div class="col-md-4 mb-4"
           v-for="work in works"
           :key="work.title">

        <div class="work-card p-4">
          <h5>{{ work.title }}</h5>
          <small>{{ work.category }}</small>
        </div>

      </div>
    </div>
  </div>
</section>

Penjelasan:

- Menggunakan v-for untuk menampilkan daftar project.
- Grid Bootstrap (col-md-4) membuat layout 3 kolom pada layar besar.
- Hover effect dibuat menggunakan CSS:

```javascript
.work-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 15px 30px rgba(124,58,237,0.3);
}
```

Data works:

```javascript
works: [
  { title: "Modern Event Poster", category: "Poster Design" },
  { title: "Digital Illustration Art", category: "Illustration" },
  { title: "Creative Portrait Photography", category: "Photography" }
]
```

# 🎨 Styling (CSS)

Semua styling berada di file style.css. Website menggunakan dark theme dengan warna ungu sebagai accent color.

Contoh styling utama:

```javascript
body {
  font-family: 'Poppins', sans-serif;
  background: radial-gradient(circle at top left, #1a1a2e, #0d0d15 60%);
  color: #ffffff;
}

.btn-custom {
  background: linear-gradient(45deg,#7c3aed,#c084fc);
  border-radius: 30px;
}
```

CSS mengatur:
- Background gradient
- Navbar glass effect
- Button custom
- Progress bar gradient
- Card hover animation
- Responsive spacing

# 🛠️ Teknologi yang Digunakan

Project ini menggunakan:

- HTML5 → Struktur dasar website
- CSS3 → Styling tampilan
- Bootstrap 5 → Grid system, navbar, progress bar, responsive design
- Vue JS 3 (CDN) → Interpolation {{ }}, data(), v-for, dan mount('#app')

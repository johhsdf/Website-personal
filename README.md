<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Toko Safiyya Naila</title>
  <style>
    :root {
      --primary: #BEE3F8;
      --accent: #FFD8A8;
      --light-bg: #F9FAFB;
      --dark-bg: #1F2937;
      --dark-text: #F3F4F6;
      --light-text: #111827;
    }
    body {
      font-family: 'Poppins', sans-serif;
      background-color: var(--light-bg);
      color: var(--light-text);
      transition: background 0.3s, color 0.3s;
    }
    body.dark {
      background-color: var(--dark-bg);
      color: var(--dark-text);
    }
    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1rem 2rem;
      background: var(--primary);
      border-radius: 0 0 20px 20px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }
    .logo {
      font-weight: bold;
      font-size: 1.5rem;
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }
    .logo::before {
      content: '🍚🥚';
    }
    .controls button {
      margin-left: 10px;
      padding: 0.5rem 1rem;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      background: var(--accent);
      transition: transform 0.3s;
    }
    .controls button:hover {
      transform: scale(1.05);
    }
    section {
      padding: 3rem 2rem;
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 1s ease, transform 1s ease;
    }
    section.visible {
      opacity: 1;
      transform: translateY(0);
    }
    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 1.5rem;
    }
    .product {
      background: white;
      border-radius: 12px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      padding: 1rem;
      text-align: center;
      transition: transform 0.3s;
    }
    body.dark .product {
      background: #374151;
    }
    .product:hover {
      transform: translateY(-5px);
    }
    .btn {
      background: var(--accent);
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 6px;
      cursor: pointer;
      transition: background 0.3s;
    }
    .btn:hover {
      background: #ffc98b;
    }
    footer {
      text-align: center;
      padding: 1rem;
      background: var(--primary);
      border-radius: 20px 20px 0 0;
    }
  </style>
</head>
<body>
  <header>
    <div class="logo">Safiyya Naila</div>
    <div class="controls">
      <button id="themeToggle">🌙/☀️</button>
      <button id="langToggle">EN/ID</button>
    </div>
  </header>

  <section id="hero">
    <h1>Selamat Datang di Toko Safiyya Naila</h1>
    <p>Menyediakan bahan pokok berkualitas: beras dan telur segar setiap hari!</p>
    <button class="btn" onclick="scrollToProducts()">Belanja Sekarang</button>
  </section>

  <section id="products">
    <h2>Produk Kami</h2>
    <div class="products">
      <div class="product">
        <h3>Beras Premium</h3>
        <p>Stok: <span id="riceStock">50</span> kg</p>
        <button class="btn" onclick="addToCart('Beras Premium')">Tambah ke Keranjang</button>
      </div>
      <div class="product">
        <h3>Telur Ayam Kampung</h3>
        <p>Stok: <span id="eggStock">120</span> butir</p>
        <button class="btn" onclick="addToCart('Telur Ayam Kampung')">Tambah ke Keranjang</button>
      </div>
    </div>
  </section>

  <section id="about">
    <h2>Tentang Kami</h2>
    <p>Toko Safiyya Naila berkomitmen menyediakan bahan pokok segar dengan harga terjangkau untuk masyarakat <b>Makassar</b> dan sekitarnya.</p>
  </section>

  <section id="contact">
    <h2>Kontak Kami</h2>
    <p>Hubungi kami di <b>Makassar</b> melalui WhatsApp untuk pemesanan:</p>
    <a href="https://wa.me/6281234567890" class="btn">Pesan Sekarang</a>
    <p style="margin-top:10px;">📍 <i>Lokasi: Makassar, Sulawesi Selatan</i></p>
  </section>

  <footer>
    <p>© 2025 Safiyya Naila. Semua Hak Dilindungi.</p>
  </footer>

  <script>
    // Tema gelap/terang
    document.getElementById('themeToggle').addEventListener('click', () => {
      document.body.classList.toggle('dark');
    });

    // Scroll animasi
    const sections = document.querySelectorAll('section');
    window.addEventListener('scroll', () => {
      sections.forEach(sec => {
        const rect = sec.getBoundingClientRect();
        if(rect.top < window.innerHeight - 100) {
          sec.classList.add('visible');
        }
      });
    });

    // Scroll ke produk
    function scrollToProducts() {
      document.getElementById('products').scrollIntoView({ behavior: 'smooth' });
    }

    // Bahasa
    let isEnglish = false;
    document.getElementById('langToggle').addEventListener('click', () => {
      isEnglish = !isEnglish;
      document.querySelector('h1').textContent = isEnglish ? 'Welcome to Safiyya Naila Store' : 'Selamat Datang di Toko Safiyya Naila';
      document.querySelector('#hero p').textContent = isEnglish ? 'We provide premium rice and fresh eggs every day!' : 'Menyediakan bahan pokok berkualitas: beras dan telur segar setiap hari!';
      document.querySelector('#products h2').textContent = isEnglish ? 'Our Products' : 'Produk Kami';
      document.querySelector('#about h2').textContent = isEnglish ? 'About Us' : 'Tentang Kami';
      document.querySelector('#about p').innerHTML = isEnglish 
        ? 'Safiyya Naila is committed to providing fresh essentials at affordable prices for the people of <b>Makassar</b> and beyond.' 
        : 'Toko Safiyya Naila berkomitmen menyediakan bahan pokok segar dengan harga terjangkau untuk masyarakat <b>Makassar</b> dan sekitarnya.';
      document.querySelector('#contact h2').textContent = isEnglish ? 'Contact Us' : 'Kontak Kami';
      document.querySelector('#contact p').innerHTML = isEnglish 
        ? 'Contact us in <b>Makassar</b> via WhatsApp to order:' 
        : 'Hubungi kami di <b>Makassar</b> melalui WhatsApp untuk pemesanan:';
    });

    // Keranjang sederhana
    const cart = [];
    function addToCart(item) {
      cart.push(item);
      alert(item + (isEnglish ? ' added to cart!' : ' ditambahkan ke keranjang!'));
    }
  </script>
</body>
</html>

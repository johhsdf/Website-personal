<!DOCTYPE html>
<html lang="id" data-theme="light">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Safiyya Naila - Toko Beras & Telur</title>
    <style>
        :root {
            --primary-color: #2E7D32;
            --bg-color: #FFFFFF;
            --text-color: #333333;
        }
        
        [data-theme="dark"] {
            --primary-color: #4CAF50;
            --bg-color: #121212;
            --text-color: #E0E0E0;
        }
        
        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            transition: all 0.3s ease;
        }
    </style>
</head>
<body>
    <header>
        <button id="themeToggle">🌙 Dark Mode</button>
        <button id="languageToggle">🇮🇩 ID</button>
    </header>
    
    <script>
        // Implementasi dark mode dan multi-bahasa
        const translations = {
            "welcome": {
                "id": "Selamat Datang di Safiyya Naila",
                "en": "Welcome to Safiyya Naila"
            }
        };
    </script>
</body>
</html>      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
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

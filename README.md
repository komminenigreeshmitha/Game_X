<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>GameX - Play Without Limits</title>
  <style>
    /* ===== Global Styles ===== */
    * {margin:0; padding:0; box-sizing:border-box; font-family:'Poppins',sans-serif;}
    body {
      background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
      color: #fff;
      scroll-behavior: smooth;
      overflow-x: hidden;
    }
    a { text-decoration: none; color: inherit; }

    /* ===== Animated Background Glow ===== */
    body::before {
      content:"";
      position:fixed;
      width:200%;
      height:200%;
      background: radial-gradient(circle at center, rgba(255,0,255,0.2), transparent 70%),
                  radial-gradient(circle at 30% 70%, rgba(0,255,255,0.15), transparent 70%),
                  radial-gradient(circle at 70% 30%, rgba(255,255,0,0.2), transparent 70%);
      animation: moveBg 20s linear infinite;
      z-index:-1;
    }
    @keyframes moveBg {
      0% {transform: translate(0,0);}
      50% {transform: translate(-200px,-100px);}
      100% {transform: translate(0,0);}
    }

    /* ===== Navbar ===== */
    nav {
      position: fixed; top:0; left:0; width:100%;
      display:flex; justify-content:space-between; align-items:center;
      padding:15px 50px; z-index:1000;
      background: rgba(20,20,50,0.6);
      backdrop-filter: blur(10px);
    }
    .logo {
      font-size:28px; font-weight:700; color:#0ff; text-shadow:0 0 15px #0ff;
    }
    nav ul { display:flex; list-style:none; }
    nav ul li { margin:0 15px; }
    nav ul li a {
      font-weight:500; transition:0.3s; color:#fff;
    }
    nav ul li a:hover { color:#ff0; text-shadow:0 0 8px #ff0; }
    .btn {
      background: linear-gradient(45deg, #ff00cc, #3333ff);
      padding:10px 20px; border-radius:30px;
      color:#fff; font-weight:600;
      transition:0.3s; box-shadow:0 0 12px #ff00cc;
    }
    .btn:hover { transform:scale(1.1); box-shadow:0 0 25px #00f; }

    /* ===== Hero ===== */
    .hero {
      height:100vh; display:flex; flex-direction:column;
      justify-content:center; align-items:center; text-align:center;
      padding:120px 20px 50px;
      position: relative;
      overflow:hidden;
    }
    .hero::after {
      content:""; position:absolute; inset:0;
      background: rgba(0,0,0,0.6);
    }
    .hero-content { position:relative; z-index:1; animation: fadeIn 2s ease-out; }
    .hero h1 {
      font-size:60px; color:#0ff; text-shadow:0 0 15px #0ff;
      margin-bottom:20px; animation: glow 2s infinite alternate;
    }
    .hero p {
      font-size:20px; max-width:700px; margin:0 auto 30px;
      color:#ddd;
    }
    @keyframes glow {
      from {text-shadow:0 0 15px #0ff;}
      to {text-shadow:0 0 25px #f0f;}
    }
    @keyframes fadeIn {
      from {opacity:0; transform:translateY(50px);}
      to {opacity:1; transform:translateY(0);}
    }

    /* ===== Features ===== */
    .features {
      padding:100px 50px; text-align:center;
      background: rgba(255,255,255,0.05);
    }
    .features h2 {
      font-size:40px; margin-bottom:50px; color:#ff0;
      text-shadow:0 0 10px #ff0;
    }
    .feature-grid {
      display:grid; grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
      gap:30px;
    }
    .feature {
      background: rgba(255,255,255,0.08);
      border-radius:15px; padding:30px;
      transition:0.4s; box-shadow:0 0 10px rgba(0,255,255,0.3);
    }
    .feature:hover {
      transform:translateY(-10px) rotate3d(1,1,0,10deg);
      box-shadow:0 0 30px rgba(255,0,255,0.8);
    }
    .feature img { width:60px; margin-bottom:15px; }

    /* ===== Showcase ===== */
    .showcase {
      padding:100px 50px; text-align:center;
    }
    .showcase h2 {
      font-size:40px; margin-bottom:40px; color:#0ff;
      text-shadow:0 0 10px #0ff;
    }
    .games {
      display:grid; grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
      gap:30px;
    }
    .game-card {
      position:relative; overflow:hidden; border-radius:20px;
      box-shadow:0 0 15px rgba(0,0,0,0.5);
      transition: transform 0.3s;
      cursor:pointer;
    }
    .game-card img { width:100%; display:block; transition:0.5s; }
    .game-card:hover img { transform:scale(1.1) rotate(1deg); }
    .game-info {
      position:absolute; bottom:0; left:0; right:0;
      background:linear-gradient(to top,rgba(0,0,0,0.9),transparent);
      padding:20px; text-align:left;
      transform:translateY(100%);
      transition:0.4s;
    }
    .game-card:hover .game-info { transform:translateY(0); }
    .game-info h3 { color:#fff; margin-bottom:5px; }
    .game-info p { color:#ccc; font-size:14px; }

    /* ===== Footer ===== */
    footer {
      background:#111; color:#aaa; padding:50px 20px;
      text-align:center;
    }
    footer .socials a {
      margin:0 10px; font-size:20px; color:#0ff; transition:0.3s;
    }
    footer .socials a:hover { color:#ff0; text-shadow:0 0 10px #ff0; }

    /* Responsive */
    @media(max-width:768px) {
      nav { padding:15px 20px; }
      .hero h1 { font-size:40px; }
      .features h2, .showcase h2 { font-size:30px; }
    }
  </style>
</head>
<body>

  <!-- Navbar -->
  <nav>
    <div class="logo">GameX</div>
    <ul>
      <li><a href="#features">Features</a></li>
      <li><a href="#showcase">Games</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <a href="#download" class="btn">Download App</a>
  </nav>

  <!-- Hero -->
  <section class="hero">
    <div class="hero-content">
      <h1>Play Without Limits</h1>
      <p>The ultimate gaming app with stunning graphics, thrilling challenges, and endless fun.</p>
      <a href="#showcase" class="btn">Explore Games</a>
    </div>
  </section>

  <!-- Features -->
  <section id="features" class="features">
    <h2>Why Choose GameX?</h2>
    <div class="feature-grid">
      <div class="feature">
        <img src="https://img.icons8.com/ios-filled/100/00ffff/controller.png"/>
        <h3>Immersive Gameplay</h3>
        <p>Experience next-level gaming with smooth controls and realistic graphics.</p>
      </div>
      <div class="feature">
        <img src="https://img.icons8.com/ios-filled/100/ff00ff/online.png"/>
        <h3>Multiplayer</h3>
        <p>Challenge your friends or team up with gamers worldwide.</p>
      </div>
      <div class="feature">
        <img src="https://img.icons8.com/ios-filled/100/ffff00/rocket.png"/>
        <h3>Fast & Optimized</h3>
        <p>Lightning speed performance across all devices.</p>
      </div>
    </div>
  </section>

  <!-- Showcase -->
  <section id="showcase" class="showcase">
    <h2>Top Games</h2>
    <div class="games">
      <div class="game-card">
        <img src="https://cdn.cloudflare.steamstatic.com/steam/apps/570/header.jpg" alt="Dota 2">
        <div class="game-info">
          <h3>Dota 2</h3>
          <p>Epic 5v5 MOBA battles with strategy and teamwork.</p>
        </div>
      </div>
      <div class="game-card">
        <img src="https://cdn.cloudflare.steamstatic.com/steam/apps/730/header.jpg" alt="CS:GO">
        <div class="game-info">
          <h3>CS:GO</h3>
          <p>Legendary FPS action. Compete globally with friends.</p>
        </div>
      </div>
      <div class="game-card">
        <img src="https://cdn.cloudflare.steamstatic.com/steam/apps/271590/header.jpg" alt="GTA V">
        <div class="game-info">
          <h3>GTA V</h3>
          <p>Open-world adventure in Los Santos. Create your legacy.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer id="contact">
    <h3>GameX</h3>
    <p>Level up your gaming experience. Join the revolution.</p>
    <div class="socials">
      <a href="#">🌐</a>
      <a href="#">🐦</a>
      <a href="#">🎮</a>
    </div>
    <p style="margin-top:20px;font-size:14px;">© 2025 GameX. All rights reserved.</p>
  </footer>

  <!-- JavaScript Animations -->
  <script>
    // Fade-in on scroll
    const elements = document.querySelectorAll('.feature, .game-card');
    const observer = new IntersectionObserver(entries => {
      entries.forEach(entry => {
        if(entry.isIntersecting){
          entry.target.style.opacity = 1;
          entry.target.style.transform = "translateY(0)";
        }
      });
    }, {threshold:0.2});
    elements.forEach(el => {
      el.style.opacity=0; el.style.transform="translateY(50px)";
      observer.observe(el);
    });
  </script>

</body>
</html>

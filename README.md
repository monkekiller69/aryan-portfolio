<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Aryan Khurana | Environment Artist</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 25%, #a1c4fd 50%, #c2e9fb 75%, #d4fc79 100%);
      background-attachment: fixed;
      background-size: 400% 400%;
      animation: gradientShift 30s ease infinite;
      color: #222;
      overflow-x: hidden;
    }

    @keyframes gradientShift {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    canvas#starfield {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
      background: transparent;
    }

    header, footer {
      background-color: #111;
      color: #fff;
      padding: 1rem 2rem;
      text-align: center;
    }
    nav {
      display: flex;
      justify-content: center;
      gap: 2rem;
      margin: 1rem 0;
    }
    nav a {
      color: #444;
      text-decoration: none;
      font-weight: bold;
    }
    .container {
      max-width: 960px;
      margin: auto;
      padding: 2rem;
      background-color: rgba(255, 255, 255, 0.95);
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05);
      border-radius: 12px;
    }
    h2 {
      border-bottom: 2px solid #ccc;
      padding-bottom: 0.5rem;
    }
    .project {
      margin-bottom: 2rem;
    }
    .project img, .project video {
      width: 100%;
      border-radius: 8px;
      margin-top: 1rem;
    }
    .contact {
      line-height: 1.6;
    }
    a.button {
      display: inline-block;
      margin-top: 0.5rem;
      padding: 0.5rem 1rem;
      background-color: #111;
      color: #fff;
      text-decoration: none;
      border-radius: 4px;
    }
  </style>
</head>
<body>
  <canvas id="starfield"></canvas>

  <header>
    <h1>Aryan Khurana</h1>
    <p>Game Environment Artist & Unreal Designer</p>
  </header>

  <nav>
    <a href="#about">About</a>
    <a href="#projects">Projects</a>
    <a href="#contact">Contact</a>
  </nav>

  <div class="container">
    <section id="about">
      <h2>About Me</h2>
      <p>
        I am a proficient designer with a strong focus on outcomes. My creativity drives me to think independently and generate unique ideas. With broad knowledge not only in technology but also in real-world dynamics, I excel in leadership roles and project management. Being a good listener enables me to absorb diverse perspectives. My core passion lies in building immersive, detailed environments using Unreal Engine.
      </p>
    </section>

    <section id="projects">
      <h2>Projects</h2>

      <div class="project">
        <h3>Drug Awareness Museum</h3>
        <p>
          An interactive Unreal Engine project showcasing a museum where an NPC guides users through informative displays about commonly abused drugs. This experience was developed to raise awareness among youth about the harmful effects of drugs, using a self-created Blueprint automation system for the NPC's behavior.
        </p>
        <img src="images/drug-museum.jpg" alt="Drug Awareness Screenshot" />
        <video controls>
          <source src="videos/drug-museum.mp4" type="video/mp4" />
          Your browser does not support the video tag.
        </video>
      </div>

      <div class="project">
        <h3>Snow Jungle Exploration</h3>
        <p>
          A snow-themed jungle environment built for exploration, featuring a mountainous region and hidden rewards. This experience emphasizes environmental storytelling, foliage detail, and optimized path design for immersive player interaction.
        </p>
        <img src="images/snow-jungle.jpg" alt="Snow Jungle Screenshot" />
        <video controls>
          <source src="videos/snow-jungle.mp4" type="video/mp4" />
          Your browser does not support the video tag.
        </video>
      </div>

      <div class="project">
        <h3>Choke Point PvP Map</h3>
        <p>
          A competitive multiplayer map designed from scratch, with attention to game balance and strategic chokepoints. It features a fully custom skybox created using 29a.ch to enhance visual immersion and ambiance, making it ideal for PvP gameplay scenarios.
        </p>
        <img src="images/choke-point.jpg" alt="Choke Point Map Screenshot" />
        <video controls>
          <source src="videos/choke-point.mp4" type="video/mp4" />
          Your browser does not support the video tag.
        </video>
      </div>
    </section>

    <section id="contact">
      <h2>Contact</h2>
      <p class="contact">
        Email: <a href="mailto:awesomekanha@gmail.com">awesomekanha@gmail.com</a><br />
        LinkedIn: <a href="https://www.linkedin.com/in/aryankhurana3" target="_blank">linkedin.com/in/aryankhurana3</a><br />
        Behance: <a href="https://www.behance.net/aryankhurana3" target="_blank">behance.net/aryankhurana3</a>
      </p>
    </section>
  </div>

  <footer>
    <p>© 2025 Aryan Khurana. All rights reserved.</p>
  </footer>

  <script>
    const canvas = document.getElementById('starfield');
    const ctx = canvas.getContext('2d');
    let stars = [];

    function resize() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }

    function createStars() {
      stars = [];
      for (let i = 0; i < 150; i++) {
        stars.push({
          x: Math.random() * canvas.width,
          y: Math.random() * canvas.height,
          radius: Math.random() * 1.5,
          speed: Math.random() * 0.2 + 0.05
        });
      }
    }

    function animateStars(scrollY = 0) {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      stars.forEach(star => {
        star.y += star.speed + scrollY * 0.001;
        if (star.y > canvas.height) star.y = 0;
        ctx.beginPath();
        ctx.arc(star.x, star.y, star.radius, 0, 2 * Math.PI);
        ctx.fillStyle = '#fff';
        ctx.fill();
      });
      requestAnimationFrame(() => animateStars(window.scrollY));
    }

    window.addEventListener('resize', () => {
      resize();
      createStars();
    });

    resize();
    createStars();
    animateStars();
  </script>
</body>
</html>

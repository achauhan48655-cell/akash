<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Akash — Portfolio</title>

<!-- Google Font -->
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;800&display=swap" rel="stylesheet">

<style>
  :root{
    --bg1: #9b9f9e; /* glacier light */
    --bg2: #197a6b; /* glacier deep */
    --accent: #000000;
    --glass: rgba(255,255,255,0.06);
    --glass-2: rgba(255,255,255,0.09);
    --text: #ffb0b0;
    --muted: rgba(232,255,247,0.75);
    --shadow: 0 10px 30px rgba(5,20,20,0.45);
    --card-shadow: 0 8px 28px rgba(6,18,20,0.5);
    --glass-border: rgba(255,255,255,0.06);
    font-family: 'Poppins', system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
  }

  /* Full page reset */
  *{box-sizing:border-box}
  html,body{height:100%}
  body{
    margin:0;
    min-height:100%;
    color:var(--text);
    background: linear-gradient(120deg,var(--bg1), var(--bg2));
    overflow-x:hidden;
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
  }

  /* Animated glacier gradient */
  .bg-anim{
    position:fixed;
    inset:0;
    z-index:-2;
    background: linear-gradient(120deg, #aef6df 0%, #80f2c8 25%, #2fb99c 50%, #197a6b 75%);
    background-size: 400% 400%;
    animation: glacierShift 18s linear infinite;
    filter: contrast(1.02) saturate(1.05);
  }
  @keyframes glacierShift{
    0%{background-position:0% 50%}
    50%{background-position:100% 50%}
    100%{background-position:0% 50%}
  }

  /* subtle radial overlay for depth */
  .vignette{
    position:fixed; inset:0; pointer-events:none;
    background: radial-gradient(circle at 10% 10%, rgba(255,255,255,0.02), transparent 10%),
                radial-gradient(circle at 90% 90%, rgba(0,0,0,0.06), transparent 20%);
    z-index:-1;
  }

  /* Layout */
  header{
    display:flex;
    gap:20px;
    align-items:center;
    justify-content:space-between;
    padding:22px 28px;
    position:sticky; top:0;
    backdrop-filter: blur(8px) saturate(1.1);
    background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    border-bottom: 1px solid rgba(255,255,255,0.04);
    z-index:10;
    box-shadow: var(--shadow);
  }

  .brand{
    display:flex; gap:14px; align-items:center;
    text-decoration:none; color:var(--text);
  }
  .logo{
    width:54px; height:54px; border-radius:12px;
    display:grid; place-items:center; font-weight:800; font-size:18px;
    background: linear-gradient(135deg, rgba(255,255,255,0.06), rgba(255,255,255,0.02));
    box-shadow: var(--card-shadow);
    border:1px solid var(--glass-border);
  }

  nav ul{list-style:none; margin:0; padding:0; display:flex; gap:14px; align-items:center}
  nav a{
    color:var(--muted);
    text-decoration:none;
    font-weight:600;
    padding:8px 12px;
    border-radius:8px;
    transition:all .18s ease;
    box-shadow: 0 6px 18px rgba(5,20,20,0.28);
    background: linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
    border:1px solid rgba(255,255,255,0.03);
  }
  nav a:hover, nav a:focus{ color:var(--text); transform:translateY(-3px); box-shadow: 0 14px 30px rgba(6,20,18,0.35) }

  main{
    padding:48px 6vw;
    max-width:1100px;
    margin:20px auto;
  }

  /* Hero */
  .hero{
    display:flex;
    gap:28px;
    align-items:center;
    justify-content:space-between;
    margin-bottom:36px;
    padding:36px;
    border-radius:18px;
    box-shadow: var(--card-shadow);
    background: linear-gradient(135deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02));
    border:1px solid rgba(255,255,255,0.04);
  }
  .hero-left{
    flex:1 1 60%;
    min-width: 250px;
  }
  .eyebrow{
    display:inline-block;
    padding:6px 12px;
    background: rgba(0,0,0,0.12);
    color:var(--text);
    border-radius:999px;
    font-weight:600;
    margin-bottom:18px;
    box-shadow: 0 6px 16px rgba(3,12,12,0.25);
  }
  h1{
    font-size: clamp(30px, 5vw, 54px);
    margin:6px 0 8px;
    line-height:1.02;
    letter-spacing:-0.6px;
    text-shadow: 0 6px 18px rgba(4,12,12,0.55);
  }
  .role{
    color:var(--muted);
    font-weight:500;
    margin-bottom:18px;
  }
  .cta-row{display:flex; gap:12px; align-items:center;}
  .btn{
    padding:12px 18px;
    border-radius:12px;
    font-weight:700;
    cursor:pointer;
    border: none;
    outline: none;
    transition:all .18s ease;
    box-shadow: 0 10px 30px rgba(2,12,12,0.4);
    background: linear-gradient(90deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02));
    color:var(--text);
  }
  .btn-primary{
    background: linear-gradient(90deg, rgba(255,255,255,0.06), rgba(255,255,255,0.02));
    border:1px solid rgba(255,255,255,0.06);
  }
  .btn-ghost{
    background:transparent;
    border:1px dashed rgba(255,255,255,0.06);
  }
  .btn:hover{transform:translateY(-4px); box-shadow: 0 20px 40px rgba(6,20,18,0.5)}

  /* Hero right visual */
  .visual{
    width:240px; height:240px; border-radius:18px;
    display:grid; place-items:center;
    background: linear-gradient(135deg, rgba(255,255,255,0.03), rgba(255,255,255,0.01));
    border:1px solid rgba(255,255,255,0.04);
    box-shadow: var(--card-shadow);
  }
  .visual .name{
    text-align:center;
    font-weight:800;
    font-size:22px;
    color:var(--text);
    letter-spacing:0.6px;
  }
  .visual .sub{color:var(--muted); margin-top:6px; font-weight:600; font-size:13px}

  /* Sections */
  section{ margin:28px 0; padding:22px; border-radius:14px; background:var(--glass); border:1px solid var(--glass-border); box-shadow: var(--card-shadow); }
  section h2{ margin:6px 0 12px; font-size:20px }
  .grid{ display:grid; grid-template-columns: repeat(auto-fit,minmax(220px,1fr)); gap:18px; align-items:start; }

  .card{
    padding:16px; border-radius:12px;
    background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    border:1px solid rgba(255,255,255,0.03);
    box-shadow: 0 8px 22px rgba(6,18,18,0.35);
  }
  .card h3{ margin:8px 0; font-size:16px }
  .muted { color:var(--muted); font-size:14px }

  /* contact form */
  .contact-grid{ display:grid; grid-template-columns:1fr 320px; gap:18px; }
  form input, form textarea{
    width:100%; padding:12px; border-radius:10px; margin-bottom:10px;
    background: rgba(0,0,0,0.06); border:1px solid rgba(255,255,255,0.03); color:var(--text);
    outline:none; font-size:14px;
    box-shadow: 0 6px 16px rgba(0,0,0,0.25);
  }
  form button{ width:100%; padding:12px; border-radius:10px; font-weight:700; cursor:pointer; }

  footer{ text-align:center; padding:28px 12px; color:var(--muted); font-size:13px; }

  /* snow canvas on top of background but behind content */
  #snow-canvas{
    position:fixed; inset:0; z-index:-1; pointer-events:none;
    mix-blend-mode: screen;
  }

  /* responsive tweaks */
  @media (max-width:880px){
    .hero{ flex-direction:column; align-items:flex-start }
    .visual{ width:160px; height:160px; align-self:center }
    .contact-grid{ grid-template-columns:1fr; }
    nav ul{ display:none } /* small screens: keep simpler (could add hamburger later) */
  }

  /* small utility */
  .pill{ display:inline-block; padding:6px 10px; border-radius:999px; background: rgba(255,255,255,0.03); font-weight:700 }
</style>
</head>
<body>
  <div class="bg-anim" aria-hidden="true"></div>
  <div class="vignette" aria-hidden="true"></div>

  <canvas id="snow-canvas" aria-hidden="true"></canvas>

  <header>
    <a class="brand" href="#home" aria-label="Go to home">
      <div class="logo" aria-hidden="true">AK</div>
      <div style="line-height:1;">
        <div style="font-weight:800">Akash</div>
        <div style="font-size:12px;color:var(--muted);margin-top:3px">Portfolio</div>
      </div>
    </a>

    <nav aria-label="Main navigation">
      <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#projects">Projects</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main id="home">
    <section class="hero" role="region" aria-labelledby="hero-title">
      <div class="hero-left">
        <div class="eyebrow">Hello, I'm</div>
        <h1 id="hero-title">Akash — Digital Creator & Developer</h1>
        <div class="role">Designing modern interfaces, subtle animations, and interactive web experiences.</div>

        <div class="cta-row" style="margin-top:18px">
          <button class="btn btn-primary" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Hire / Contact</button>
          <a class="btn btn-ghost" href="#projects">See Projects</a>
        </div>
      </div>

      <div class="visual" aria-hidden="true">
        <div class="name">AKASH</div>
        <div class="sub">Glacier • Snow • Green</div>
      </div>
    </section>

    <section id="about" aria-labelledby="about-title">
      <h2 id="about-title">About</h2>
      <div class="grid">
        <div class="card">
          <h3>Who I am</h3>
          <p class="muted">I’m Akash — a front-end developer and designer who loves clean interfaces, subtle motion, and a glacier-green aesthetic. I make interactive websites and small web apps with HTML, CSS, and JavaScript.</p>
        </div>

        <div class="card">
          <h3>Skills</h3>
          <p class="muted">HTML • CSS • JavaScript • Animations • Responsive design • Accessibility-conscious UI</p>
        </div>

        <div class="card">
          <h3>Approach</h3>
          <p class="muted">Design-first development: start with structure, refine visuals, add motion with purpose, and ensure performance.</p>
        </div>
      </div>
    </section>

    <section id="projects" aria-labelledby="projects-title">
      <h2 id="projects-title">Projects</h2>
      <div class="grid">
        <article class="card" aria-labelledby="p1">
          <h3 id="p1">Glacier Weather UI</h3>
          <p class="muted">A clean weather UI with animated gradient background and snow overlay. Built with pure JS and CSS.</p>
        </article>

        <article class="card" aria-labelledby="p2">
          <h3 id="p2">Interactive Portfolio</h3>
          <p class="muted">Single-file portfolio with subtle glassmorphism and animations — made for speed and presentation.</p>
        </article>

        <article class="card" aria-labelledby="p3">
          <h3 id="p3">3D Card Animations</h3>
          <p class="muted">Cards with 3D tilt, depth shadows, and CSS transforms for a tactile experience.</p>
        </article>
      </div>
    </section>

    <section id="contact" aria-labelledby="contact-title">
      <h2 id="contact-title">Contact</h2>

      <div class="contact-grid" role="form" aria-label="Contact form and info">
        <div>
          <form id="contactForm" onsubmit="submitContact(event)" autocomplete="off">
            <input type="text" id="name" name="name" placeholder="Your name" required />
            <input type="email" id="email" name="email" placeholder="Your email" required />
            <textarea id="message" name="message" rows="5" placeholder="Message..." required></textarea>
            <button class="btn btn-primary" type="submit">Send Message</button>
          </form>
          <div id="formStatus" style="margin-top:12px;color:var(--muted);"></div>
        </div>

        <aside class="card" style="display:flex;flex-direction:column;gap:8px;align-items:flex-start">
          <div><strong>Akash</strong></div>
          <div class="muted">Frontend Developer & Designer</div>
          <div style="margin-top:8px">
            <div class="pill">Email</div>
            <div style="margin-top:6px" class="muted">akash@example.com</div>
          </div>
          <div style="margin-top:10px">
            <div class="pill">Location</div>
            <div class="muted" style="margin-top:6px">India</div>
          </div>
        </aside>
      </div>
    </section>

    <footer>
      <div>© <span id="year"></span> Akash — Crafted with glacier green & falling snow.</div>
    </footer>
  </main>

<script>
  // set copyright year
  document.getElementById('year').textContent = new Date().getFullYear();

  // contact form (demo-only; won't actually send)
  function submitContact(e){
    e.preventDefault();
    const name = document.getElementById('name').value.trim();
    const email = document.getElementById('email').value.trim();
    const message = document.getElementById('message').value.trim();
    const status = document.getElementById('formStatus');

    if(!name || !email || !message){
      status.textContent = 'Please fill all fields.';
      return;
    }

    // Simulate send + reset
    status.textContent = 'Sending message...';
    setTimeout(() => {
      status.textContent = 'Thanks, ' + (name.split(' ')[0] || name) + '! Your message has been received (demo).';
      document.getElementById('contactForm').reset();
    }, 900);
  }

  /* Snow effect using canvas - lightweight particle system */
  (function(){
    const canvas = document.getElementById('snow-canvas');
    const ctx = canvas.getContext('2d');
    let width = canvas.width = window.innerWidth;
    let height = canvas.height = window.innerHeight;
    const flakes = [];
    const flakeCount = Math.min(160, Math.floor((width * height) / 6000)); // scale with screen

    function rand(min,max){ return Math.random()*(max-min)+min; }

    for(let i=0;i<flakeCount;i++){
      flakes.push({
        x: rand(0,width),
        y: rand(0,height),
        r: rand(1.2,4.4),
        d: rand(0.5,2.2),
        vx: rand(-0.25,0.45),
        vy: rand(0.2,1.0),
        a: rand(0,Math.PI*2),
        swing: rand(10,40)
      });
    }

    function resize(){
      width = canvas.width = window.innerWidth;
      height = canvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resize, {passive:true});

    let t = 0;
    function draw(){
      ctx.clearRect(0,0,width,height);
      // subtle glow / blend
      ctx.fillStyle = 'rgba(255,255,255,0.02)';
      ctx.fillRect(0,0,width,height);

      for(let i=0;i<flakes.length;i++){
        const f = flakes[i];
        // oscillate horizontally for natural fall
        f.a += 0.01 * f.d;
        f.x += Math.sin(f.a) * 0.6 + f.vx;
        f.y += f.vy * f.d;

        // wrap
        if(f.x > width + 20) f.x = -20;
        if(f.x < -20) f.x = width + 20;
        if(f.y > height + 20){
          f.y = -10;
          f.x = rand(0,width);
        }

        // draw with radial gradient for soft flakes
        const g = ctx.createRadialGradient(f.x, f.y, 0, f.x, f.y, f.r*3);
        g.addColorStop(0, 'rgba(255,255,255,0.95)');
        g.addColorStop(0.3, 'rgba(255,255,255,0.6)');
        g.addColorStop(1, 'rgba(255,255,255,0)');
        ctx.beginPath();
        ctx.fillStyle = g;
        ctx.arc(f.x, f.y, f.r*2.2, 0, Math.PI*2);
        ctx.fill();
      }

      t += 0.01;
      requestAnimationFrame(draw);
    }

    // reduce animation on hidden tabs to save CPU
    document.addEventListener('visibilitychange', function(){
      if(document.hidden){
        // nothing to do: requestAnimationFrame will naturally throttle
      }
    });

    draw();
  })();

  // small keyboard nav: number keys go to sections
  document.addEventListener('keydown', function(e){
    if(e.key === '1') location.hash = '#home';
    if(e.key === '2') location.hash = '#about';
    if(e.key === '3') location.hash = '#projects';
    if(e.key === '4') location.hash = '#contact';
  });
</script>
</body>
</html>

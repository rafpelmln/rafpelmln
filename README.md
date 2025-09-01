<!doctype html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Rafpelmln — Profile</title>
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--accent:#06b6d4;--muted:#94a3b8}
    *{box-sizing:border-box}
    body{margin:0;font-family:Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;color:#e6eef6;background:linear-gradient(180deg,#071127 0%, #0f1724 100%);-webkit-font-smoothing:antialiased}
    .wrap{max-width:980px;margin:40px auto;padding:24px}
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));border-radius:14px;padding:26px;display:grid;grid-template-columns:120px 1fr;gap:20px;align-items:center;box-shadow:0 8px 30px rgba(2,6,23,0.6)}
    .avatar{width:120px;height:120px;border-radius:14px;overflow:hidden;border:3px solid rgba(255,255,255,0.04)}
    .avatar img{width:100%;height:100%;object-fit:cover;display:block}
    h1{margin:0 0 6px 0;font-size:20px}
    p.lead{margin:0;color:var(--muted)}

    /* typing */
    .type-wrap{margin-top:8px;font-family:monospace;color:var(--accent);height:28px;overflow:hidden}
    .cursor{display:inline-block;width:10px;background:var(--accent);margin-left:6px;animation:blink 1s steps(2) infinite}
    @keyframes blink{50%{opacity:0}}

    /* skills */
    .skills{display:flex;flex-wrap:wrap;gap:10px;margin-top:18px}
    .skill{padding:8px 12px;border-radius:999px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03);font-weight:600;font-size:13px}

    /* skill bars */
    .bars{margin-top:18px}
    .bar{margin-bottom:10px}
    .bar .meta{display:flex;justify-content:space-between;font-size:13px;color:var(--muted)}
    .bar .track{height:10px;background:rgba(255,255,255,0.04);border-radius:999px;margin-top:6px;overflow:hidden}
    .bar .fill{height:100%;width:0%;background:linear-gradient(90deg,var(--accent),#7c3aed);border-radius:999px;transition:width 1s ease}

    /* footer */
    .links{display:flex;gap:12px;margin-top:14px}
    .btn{padding:8px 12px;border-radius:10px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03);text-decoration:none;color:#e6eef6;font-weight:600}

    /* responsive */
    @media (max-width:640px){.card{grid-template-columns:1fr;padding:18px}.avatar{margin:0 auto}}

    /* subtle entrance */
    .card{transform:translateY(12px);opacity:0;animation:in 600ms forwards}
    @keyframes in{to{transform:none;opacity:1}}
  </style>
</head>
<body>
  <main class="wrap">
    <section class="card">
      <div class="avatar">
        <img src="https://github.com/Rafpelmln.png" alt="avatar" />
      </div>
      <div>
        <h1>Halo — Aing Maneh 👋 <small style="color:var(--muted);font-weight:600">(Rafpelmln)</small></h1>
        <p class="lead">Web Developer & Student — fokus ke Laravel & frontend modern. Bikin aplikasi yang rapi, performa oke, dan UI asik.</p>

        <div class="type-wrap" aria-hidden="true"><span id="type"></span><span class="cursor"></span></div>

        <div class="skills" aria-hidden="false">
          <div class="skill">Laravel</div>
          <div class="skill">JavaScript</div>
          <div class="skill">HTML</div>
          <div class="skill">CSS</div>
          <div class="skill">Tailwind</div>
          <div class="skill">React.js</div>
          <div class="skill">Next.js</div>
        </div>

        <div class="bars" aria-hidden="true">
          <div class="bar"><div class="meta"><span>Laravel</span><span>90%</span></div><div class="track"><div class="fill" data-width="90"></div></div></div>
          <div class="bar"><div class="meta"><span>JavaScript</span><span>85%</span></div><div class="track"><div class="fill" data-width="85"></div></div></div>
          <div class="bar"><div class="meta"><span>HTML & CSS</span><span>92%</span></div><div class="track"><div class="fill" data-width="92"></div></div></div>
          <div class="bar"><div class="meta"><span>Tailwind</span><span>80%</span></div><div class="track"><div class="fill" data-width="80"></div></div></div>
          <div class="bar"><div class="meta"><span>React / Next</span><span>78%</span></div><div class="track"><div class="fill" data-width="78"></div></div></div>
        </div>

        <div class="links">
          <a class="btn" href="https://github.com/Rafpelmln" target="_blank" rel="noopener">GitHub</a>
          <a class="btn" href="#" onclick="alert('Tambahin link portfolio di sini ya')">Portfolio</a>
        </div>
      </div>
    </section>

    <section style="margin-top:18px;color:var(--muted);font-size:14px">Tips: simpen file ini sebagai <code>profile.html</code> atau <code>index.html</code>. Bisa buka langsung di browser.</section>
  </main>

  <script>
    // typing effect
    const texts = ['Web Developer', 'Laravel • React • Next.js', 'Build with clean code & UX'];
    const el = document.getElementById('type');
    let i = 0, j = 0, forward = true;
    function type(){
      const t = texts[i];
      if(forward){
        el.textContent = t.slice(0, ++j);
        if(j === t.length){forward=false; setTimeout(type,900); return}
      } else {
        el.textContent = t.slice(0, --j);
        if(j === 0){forward=true; i=(i+1)%texts.length}
      }
      setTimeout(type, forward?80:40);
    }
    type();

    // animate skill bars after load
    window.addEventListener('load', ()=>{
      document.querySelectorAll('.fill').forEach(f=>{
        const w = f.getAttribute('data-width')||70;
        setTimeout(()=>f.style.width = w + '%', 200);
      });
    });
  </script>
</body>
</html>

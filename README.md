<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Birds of the World — A Colorful Guide</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&family=Poppins:wght@600;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg: linear-gradient(135deg,#f0f8ff 0%, #f7fff7 100%);
      --card: #ffffff;
      --accent1: #ff6b6b;
      --accent2: #6bffd6;
      --accent3: #6b9bff;
      --glass: rgba(255,255,255,0.65);
      --shadow: 0 8px 30px rgba(36, 37, 58, 0.12);
      --radius: 18px;
      --maxw: 1100px;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      font-family: 'Inter', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
      margin:0; background:var(--bg); color:#102a43; -webkit-font-smoothing:antialiased;
    }

    /* Container */
    .wrap{max-width:var(--maxw); margin:32px auto; padding:24px}

    /* Header */
    header{
      display:flex; align-items:center; gap:18px; justify-content:space-between; margin-bottom:22px;
    }
    .brand{display:flex; align-items:center; gap:12px}
    .logo{
      width:56px; height:56px; border-radius:12px; background:linear-gradient(135deg,var(--accent1),var(--accent3));
      display:grid; place-items:center; color:white; font-weight:800; font-family:'Poppins'; box-shadow:var(--shadow);
    }
    h1{margin:0; font-size:20px}
    p.lead{margin:0; opacity:0.85; font-size:13px}

    /* Search area */
    .controls{display:flex; gap:12px; align-items:center}
    .search{display:flex; align-items:center; gap:8px; background:var(--glass); padding:8px 12px; border-radius:999px; box-shadow:var(--shadow)}
    .search input{border:0; outline:0; background:transparent; width:220px}
    .select, .btn{padding:8px 12px; border-radius:10px; border:0; background:white; box-shadow:var(--shadow); cursor:pointer}
    .btn.primary{background:linear-gradient(90deg,var(--accent3),var(--accent2)); color:white; font-weight:600}

    /* Hero */
    .hero{
      display:flex; gap:24px; align-items:center; padding:28px; border-radius:22px; background:linear-gradient(90deg, rgba(107,155,255,0.12), rgba(255,107,107,0.06));
      box-shadow:var(--shadow); margin-bottom:20px; overflow:hidden;
    }
    .hero-left{flex:1}
    .hero-right{width:320px; display:grid; gap:10px}
    .hero h2{font-family:'Poppins'; margin:0 0 8px 0; font-size:26px}
    .hero p{margin:0; opacity:0.85}
    .tagline{display:inline-block; margin-top:12px; padding:6px 10px; background:rgba(255,255,255,0.8); border-radius:999px; font-weight:600}

    /* Grid of cards */
    .grid{display:grid; grid-template-columns:repeat(auto-fit,minmax(240px,1fr)); gap:18px}
    .card{background:var(--card); border-radius:16px; overflow:hidden; box-shadow:var(--shadow); transition:transform .28s ease, box-shadow .28s ease; cursor:pointer}
    .card:hover{transform:translateY(-8px); box-shadow:0 20px 50px rgba(36,37,58,0.16)}
    .card .media{height:160px; background-size:cover; background-position:center}
    .card .body{padding:12px}
    .species{display:flex; align-items:center; justify-content:space-between}
    .species h3{margin:0; font-size:16px}
    .meta{font-size:13px; opacity:0.8}
    .tags{margin-top:8px; display:flex; gap:8px; flex-wrap:wrap}
    .tag{padding:6px 8px; border-radius:999px; background:linear-gradient(90deg, rgba(107,155,255,0.12), rgba(107,255,214,0.06)); font-weight:600; font-size:12px}

    /* Modal */
    .modal-backdrop{position:fixed; inset:0; background:rgba(6,7,11,0.35); display:none; place-items:center; z-index:60}
    .modal{width:min(920px,96%); background:linear-gradient(180deg,#ffffff, #fbfdff); border-radius:16px; padding:18px; display:grid; grid-template-columns:1fr 320px; gap:16px}
    .modal .m-media{height:320px; background-size:cover; background-position:center; border-radius:12px}
    .close{border:0; background:transparent; font-size:20px; cursor:pointer}

    /* footer */
    footer{margin-top:20px; text-align:center; font-size:13px; opacity:0.8}

    /* Responsive tweaks */
    @media (max-width:760px){
      .hero{flex-direction:column}
      .modal{grid-template-columns:1fr}
      .hero-right{width:100%}
      .search input{width:120px}
    }

    /* little decorative birds */
    .bird-deco{position:absolute; right:32px; top:18px; width:120px; opacity:0.12; transform:rotate(-10deg)}
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="brand">
        <div class="logo">B</div>
        <div>
          <h1>Birds of the World</h1>
          <p class="lead">Discover species, habitats & fun facts — bright, friendly and easy to explore</p>
        </div>
      </div>
      <div class="controls">
        <div class="search" role="search">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" aria-hidden><path d="M21 21l-4.35-4.35" stroke="#102a43" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
          <input id="q" placeholder="Search species (e.g. Kingfisher)" />
        </div>
        <select id="filter" class="select">
          <option value="all">All habitats</option>
          <option value="forest">Forest</option>
          <option value="wetlands">Wetlands</option>
          <option value="grassland">Grassland</option>
          <option value="urban">Urban</option>
        </select>
        <button id="reset" class="btn">Reset</button>
      </div>
    </header>

    <section class="hero">
      <div class="hero-left">
        <h2>Explore colorful bird species — photos, range & facts</h2>
        <p>From tiny hummingbirds to majestic eagles — learn where they live, what they eat, and why they matter.</p>
        <div class="tagline">Curated picks • Family-friendly • Offline capable</div>
      </div>
      <div class="hero-right">
        <img class="bird-deco" src="https://images.unsplash.com/photo-1518972559570-9c6c0a0f9e2b?q=80&w=800&auto=format&fit=crop&crop=entropy&s=6a6e6b2f" alt="decorative bird"/>
        <div style="background:linear-gradient(90deg,#fff,#f8fafe); padding:12px; border-radius:12px; box-shadow:var(--shadow)">
          <strong>Featured</strong>
          <p style="margin:6px 0 0 0; font-size:13px; opacity:0.85">Indian Peafowl — a symbol of beauty and biodiversity in open forests & farmland.</p>
        </div>
        <div style="background:linear-gradient(90deg,#fff,#fff7f9); padding:12px; border-radius:12px; box-shadow:var(--shadow)">
          <strong>Quick Tip</strong>
          <p style="margin:6px 0 0 0; font-size:13px; opacity:0.85">Use the search to find species and click any card to read more.</p>
        </div>
      </div>
    </section>

    <main>
      <div id="grid" class="grid" aria-live="polite"></div>
    </main>

    <footer>
      <p>&copy; 2025 Birds of the World — Built with ❤️ for bird lovers</p>
    </footer>
  </div>

  <!-- Modal -->
  <div id="backdrop" class="modal-backdrop" role="dialog" aria-modal="true">
    <div class="modal" role="document">
      <div>
        <div id="m-media" class="m-media"></div>
        <h3 id="m-name" style="margin-top:12px"></h3>
        <p id="m-scientific" style="margin:6px 0 0 0; font-style:italic; opacity:0.85"></p>
        <p id="m-desc" style="margin-top:10px; line-height:1.5"></p>
      </div>
      <aside style="padding:8px;">
        <div style="display:flex; justify-content:space-between; align-items:center">
          <strong>Details</strong>
          <button class="close" id="closeBtn">✕</button>
        </div>
        <ul id="m-list" style="margin-top:10px; padding-left:18px"></ul>
        <div style="margin-top:14px">
          <small>Source: Example data for demo only</small>
        </div>
      </aside>
    </div>
  </div>

  <script>
    // --- sample bird dataset ---
    const birds = [
      {
        id:1, name:'Indian Peafowl', scientific:'Pavo cristatus', habitat:'grassland', diet:'Omnivore', range:'South Asia', img:'https://images.unsplash.com/photo-1528251736479-6c2a3d1a7b6c?q=80&w=1200&auto=format&fit=crop&crop=entropy&s=48cfa8b0a6b5d2d4', desc:'A large and colorful pheasant known for its iridescent tail (train) displayed during courtship.'
      },
      {id:2, name:'Common Kingfisher', scientific:'Alcedo atthis', habitat:'wetlands', diet:'Fish & insects', range:'Eurasia', img:'https://images.unsplash.com/photo-1501706362039-c6e8097e27b0?q=80&w=1200&auto=format&fit=crop&crop=entropy&s=8d6f6b1752f3cc11', desc:'A small bright-blue bird that hunts by diving into water from perches.'},
      {id:3, name:'Bald Eagle', scientific:'Haliaeetus leucocephalus', habitat:'forest', diet:'Carnivore (fish)', range:'North America', img:'https://images.unsplash.com/photo-1547149607-0a6f1b3b4cfd?q=80&w=1200&auto=format&fit=crop&crop=entropy&s=9ef3f3b4f2a8bd7c', desc:'A large raptor symbol of the United States; powerful flyer and fish hunter.'},
      {id:4, name:'Greater Flamingo', scientific:'Phoenicopterus roseus', habitat:'wetlands', diet:'Filter-feeder (algae) ', range:'Africa, S. Europe, S. Asia', img:'https://images.unsplash.com/photo-1523301343968-17a72ca0327b?q=80&w=1200&auto=format&fit=crop&crop=entropy&s=7e8f6a2c0b6eae3a', desc:'Tall wading birds with pink feathers; feed by filtering water through their bills.'},
      {id:5, name:'Ruby-throated Hummingbird', scientific:'Archilochus colubris', habitat:'forest', diet:'Nectar & insects', range:'Americas', img:'https://images.unsplash.com/photo-1511174511562-5f7f18b872c9?q=80&w=1200&auto=format&fit=crop&crop=entropy&s=2d7a5f9b9d4b5f9a', desc:'Tiny, agile birds that hover while feeding from flowers; rapid wingbeat.'},
      {id:6, name:'Barn Owl', scientific:'Tyto alba', habitat:'urban', diet:'Small mammals', range:'Worldwide', img:'https://images.unsplash.com/photo-1526481280698-2a6a6eb0d4b3?q=80&w=1200&auto=format&fit=crop&crop=entropy&s=1f7b64cc4c2b3b2d', desc:'Nocturnal owls with heart-shaped faces and silent flight that hunt rodents.'}
    ];

    const grid = document.getElementById('grid');
    const q = document.getElementById('q');
    const filter = document.getElementById('filter');
    const reset = document.getElementById('reset');

    function render(list){
      grid.innerHTML = '';
      if(list.length === 0){ grid.innerHTML = '<p style="grid-column:1/-1; padding:18px; border-radius:12px; background:white; box-shadow:var(--shadow)">No birds matched your search.</p>'; return }
      list.forEach(b => {
        const el = document.createElement('article'); el.className='card'; el.tabIndex=0;
        el.innerHTML = `
          <div class="media" style="background-image:url('${b.img}')" aria-hidden></div>
          <div class="body">
            <div class="species">
              <h3>${b.name}</h3>
              <div class="meta">${b.range}</div>
            </div>
            <p class="meta">${b.scientific}</p>
            <div class="tags">
              <span class="tag">${b.habitat}</span>
              <span class="tag">${b.diet}</span>
            </div>
          </div>
        `;
        el.addEventListener('click', ()=> openModal(b));
        el.addEventListener('keyup', (ev)=> { if(ev.key === 'Enter') openModal(b) });
        grid.appendChild(el);
      })
    }

    function openModal(b){
      document.getElementById('m-media').style.backgroundImage = `url(${b.img})`;
      document.getElementById('m-name').textContent = b.name;
      document.getElementById('m-scientific').textContent = b.scientific;
      document.getElementById('m-desc').textContent = b.desc;
      const list = document.getElementById('m-list');
      list.innerHTML = `
        <li><strong>Habitat:</strong> ${b.habitat}</li>
        <li><strong>Diet:</strong> ${b.diet}</li>
        <li><strong>Range:</strong> ${b.range}</li>
      `;
      document.getElementById('backdrop').style.display = 'grid';
    }

    document.getElementById('closeBtn').addEventListener('click', ()=> document.getElementById('backdrop').style.display='none');
    document.getElementById('backdrop').addEventListener('click', (ev)=>{ if(ev.target.id === 'backdrop') ev.currentTarget.style.display='none' });

    // --- search & filter logic ---
    function applyFilters(){
      const term = q.value.trim().toLowerCase();
      const habitat = filter.value;
      let out = birds.filter(b => {
        const matchQ = b.name.toLowerCase().includes(term) || b.scientific.toLowerCase().includes(term) || b.range.toLowerCase().includes(term);
        const matchHab = (habitat === 'all') || (b.habitat === habitat);
        return matchQ && matchHab;
      });
      render(out);
    }

    q.addEventListener('input', applyFilters);
    filter.addEventListener('change', applyFilters);
    reset.addEventListener('click', ()=>{ q.value=''; filter.value='all'; applyFilters(); });

    // initial
    render(birds);
  </script>
</body>
</html>


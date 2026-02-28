<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ARCHI-PRO AI | Shavkat Edition</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/pannellum@2.5.6/build/pannellum.js"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/pannellum@2.5.6/build/pannellum.css"/>

    <style>
        :root { --accent: #d4af37; --dark: #0a0a0b; --card: #161618; --text: #e0e0e0; }
        * { margin:0; padding:0; box-sizing:border-box; font-family: 'Inter', sans-serif; }
        body { background: var(--dark); color: var(--text); overflow-x: hidden; }

        /* Header & Navigation */
        header { padding: 25px 5%; display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid rgba(212, 175, 55, 0.2); position: sticky; top:0; background: rgba(10,10,11,0.9); z-index: 1000; backdrop-filter: blur(10px); }
        .logo { font-size: 24px; font-weight: 800; letter-spacing: 2px; }
        .logo span { color: var(--accent); }

        /* AI Controller Panel */
        .ai-panel { padding: 40px 5%; background: radial-gradient(circle at top, #1c1c1f, #0a0a0b); text-align: center; }
        .control-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; max-width: 1200px; margin: 30px auto; background: var(--card); padding: 30px; border-radius: 20px; border: 1px solid rgba(255,255,255,0.05); }
        
        .input-group { text-align: left; }
        label { display: block; margin-bottom: 10px; font-size: 12px; color: var(--accent); text-transform: uppercase; letter-spacing: 1px; }
        input, select { width: 100%; background: #222; border: 1px solid #333; color: white; padding: 15px; border-radius: 12px; transition: 0.3s; }
        input:focus { border-color: var(--accent); }

        /* Project Cards */
        .project-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(380px, 1fr)); gap: 30px; padding: 50px 5%; }
        .p-card { background: var(--card); border-radius: 24px; overflow: hidden; border: 1px solid rgba(255,255,255,0.03); transition: 0.5s cubic-bezier(0.4, 0, 0.2, 1); position: relative; }
        .p-card:hover { transform: translateY(-15px); border-color: var(--accent); box-shadow: 0 20px 40px rgba(0,0,0,0.5); }
        .p-img { width: 100%; height: 280px; object-fit: cover; transition: 0.5s; }
        .p-card:hover .p-img { scale: 1.05; }
        .p-content { padding: 25px; }
        .p-price { position: absolute; top: 20px; right: 20px; background: var(--accent); color: #000; padding: 8px 15px; border-radius: 30px; font-weight: 800; }

        /* Modal 3D Walkthrough */
        #walkthrough-modal { display:none; position:fixed; inset:0; background: #000; z-index: 2000; }
        #viewer { width: 100%; height: 100vh; }
        .close-walk { position: absolute; top: 30px; right: 30px; font-size: 40px; color: var(--accent); cursor: pointer; z-index: 2100; }
        
        /* Stats Table in Modal */
        .info-panel { position: absolute; bottom: 40px; left: 40px; background: rgba(0,0,0,0.8); padding: 30px; border-radius: 20px; border-left: 5px solid var(--accent); max-width: 400px; backdrop-filter: blur(10px); }

        /* Kitchen Style Badges */
        .style-badge { display: inline-block; padding: 4px 10px; border: 1px solid var(--accent); border-radius: 5px; font-size: 10px; margin-right: 5px; color: var(--accent); }

        .btn-action { background: var(--accent); color: #000; border: none; padding: 15px 30px; border-radius: 12px; font-weight: 700; cursor: pointer; width: 100%; margin-top: 15px; text-transform: uppercase; transition: 0.3s; }
        .btn-action:hover { letter-spacing: 1px; opacity: 0.9; }

        @media (max-width: 768px) { .project-grid { grid-template-columns: 1fr; } }
    </style>
</head>
<body>

    <div id="walkthrough-modal">
        <span class="close-walk" onclick="closeTour()">&times;</span>
        <div id="viewer"></div>
        <div class="info-panel">
            <h2 id="m-title">Loyiha Detallari</h2>
            <p id="m-desc" style="margin: 10px 0; font-size: 14px; color: #aaa;"></p>
            <div id="m-stats" style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 15px;"></div>
            <button class="btn-action" onclick="alert('PDF Yuklanmoqda...')"><i class="fa fa-file-pdf"></i> Loyihani PDF Yuklash</button>
        </div>
    </div>

    <header>
        <div class="logo">ARCHI<span>PRO.AI</span></div>
        <div style="font-size: 14px;"><i class="fa fa-heart"></i> Saqlanganlar (0)</div>
    </header>

    <section class="ai-panel">
        <h1 style="font-size: 42px; margin-bottom: 10px;" data-aos="fade-up">Orzungizdagi Uyni <span style="color:var(--accent)">AI</span> Bilan Toping</h1>
        <p style="color: #666; margin-bottom: 20px;">Budjetingizni kiriting va virtual sayohatni boshlang</p>
        
        <div class="control-grid" data-aos="zoom-in">
            <div class="input-group">
                <label>Sizning Budjetingiz ($)</label>
                <input type="number" id="budgetInput" value="75000" oninput="liveFilter()">
            </div>
            <div class="input-group">
                <label>Xonalar Soni</label>
                <select id="roomSelect" onchange="liveFilter()">
                    <option value="all">Hammasi</option>
                    <option value="2">2 xona</option>
                    <option value="3">3 xona</option>
                    <option value="4">4+ xona</option>
                </select>
            </div>
            <div class="input-group">
                <label>Maydon (m²)</label>
                <input type="number" id="areaInput" value="120" oninput="liveFilter()">
            </div>
        </div>
    </section>

    <div class="project-grid" id="mainGrid"></div>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        AOS.init();

        const projects = [
            {
                id: 1, name: "Luxury Loft Concept", price: 120000, rooms: 4, area: 250, 
                mat: "Beton/Shisha", style: "Minimalist", 
                img: "https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=800",
                kitchen: "Modern-Island", panorama: "https://pannellum.org/images/alma.jpg",
                specs: { kitchen: "25 m²", bath: "12 m²", height: "3.5m", doors: "2.4m" }
            },
            {
                id: 2, name: "Classic Family Villa", price: 65000, rooms: 3, area: 140, 
                mat: "Pishgan g'isht", style: "Classic", 
                img: "https://images.unsplash.com/photo-1583608205776-bfd35f0d9f83?w=800",
                kitchen: "Classic-U", panorama: "https://pannellum.org/images/jure.jpg",
                specs: { kitchen: "18 m²", bath: "8 m²", height: "3.2m", doors: "2.1m" }
            },
            {
                id: 3, name: "Eco Smart House", price: 45000, rooms: 2, area: 90, 
                mat: "Gazobeton", style: "Modern", 
                img: "https://images.unsplash.com/photo-1512917774080-9991f1c4c750?w=800",
                kitchen: "Minimal-Open", panorama: "https://pannellum.org/images/cerro-toco-0.jpg",
                specs: { kitchen: "12 m²", bath: "6 m²", height: "3.0m", doors: "2.1m" }
            }
        ];

        function liveFilter() {
            const bud = document.getElementById('budgetInput').value;
            const rom = document.getElementById('roomSelect').value;
            const area = document.getElementById('areaInput').value;
            
            const filtered = projects.filter(p => {
                return p.price <= bud && (rom === 'all' || p.rooms == rom);
            });
            render(filtered);
        }

        function render(data) {
            const grid = document.getElementById('mainGrid');
            grid.innerHTML = '';
            data.forEach(p => {
                grid.innerHTML += `
                    <div class="p-card" data-aos="fade-up">
                        <div class="p-price">$${p.price.toLocaleString()}</div>
                        <img src="${p.img}" class="p-img">
                        <div class="p-content">
                            <div class="style-badge">${p.style}</div>
                            <div class="style-badge">Oshxona: ${p.kitchen}</div>
                            <h2 style="margin:10px 0;">${p.name}</h2>
                            <p style="font-size:13px; color:#777;"><i class="fa fa-expand"></i> ${p.area} m² | <i class="fa fa-bed"></i> ${p.rooms} Xona</p>
                            <div style="margin-top:15px; border-top:1px solid #333; padding-top:15px;">
                                <p style="font-size:12px; color:var(--accent);">Material: ${p.mat}</p>
                                <button class="btn-action" onclick="openTour(${p.id})"><i class="fa fa-street-view"></i> Ichiga Kirish (3D WALK)</button>
                            </div>
                        </div>
                    </div>
                `;
            });
        }

        function openTour(id) {
            const p = projects.find(x => x.id === id);
            document.getElementById('walkthrough-modal').style.display = 'block';
            document.getElementById('m-title').innerText = p.name;
            document.getElementById('m-desc').innerText = `${p.style} uslubidagi professional loyiha. Har bir detal AI tomonidan optimallashtirilgan.`;
            
            const stats = document.getElementById('m-stats');
            stats.innerHTML = `
                <div style="background:#222; padding:10px; border-radius:10px">Oshxona: ${p.specs.kitchen}</div>
                <div style="background:#222; padding:10px; border-radius:10px">Vanna: ${p.specs.bath}</div>
                <div style="background:#222; padding:10px; border-radius:10px">Shift: ${p.specs.height}</div>
                <div style="background:#222; padding:10px; border-radius:10px">Eshik: ${p.specs.doors}</div>
            `;

            pannellum.viewer('viewer', {
                "type": "panorama",
                "panorama": p.panorama,
                "autoLoad": true,
                "title": p.name
            });
        }

        function closeTour() {
            document.getElementById('walkthrough-modal').style.display = 'none';
        }

        window.onload = liveFilter;
    </script>
</body>
</html>

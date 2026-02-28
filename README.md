<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SHAVKAT AI-ARCHITECT v3.0 | Professional</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root { --gold: #d4af37; --dark: #0a0a0a; --gray: #1a1a1a; }
        * { margin:0; padding:0; box-sizing:border-box; font-family: 'Poppins', sans-serif; }
        body { background: var(--dark); color: white; overflow-x: hidden; }

        /* Navigation */
        nav { padding: 20px 5%; border-bottom: 1px solid var(--gold); display: flex; justify-content: space-between; }
        .logo span { color: var(--gold); }

        /* AI Filter */
        .ai-header { padding: 40px 5%; background: linear-gradient(45deg, #0a0a0a, #1a1a1a); text-align: center; }
        .filter-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 15px; max-width: 1000px; margin: 20px auto; }
        input, select { background: #222; border: 1px solid #444; color: white; padding: 12px; border-radius: 8px; outline: none; }
        .btn-gen { background: var(--gold); color: black; border: none; padding: 15px 30px; border-radius: 8px; font-weight: bold; cursor: pointer; width: 100%; }

        /* Catalog */
        .catalog { display: grid; grid-template-columns: repeat(auto-fit, minmax(350px, 1fr)); gap: 30px; padding: 40px 5%; }
        .card { background: var(--gray); border-radius: 15px; overflow: hidden; border: 1px solid #333; transition: 0.4s; }
        .card:hover { border-color: var(--gold); transform: translateY(-5px); }
        .card img { width: 100%; height: 230px; object-fit: cover; }
        .card-body { padding: 20px; }

        /* FULL PROJECT MODAL (Uyni ichiga kirish) */
        #project-modal { display:none; position:fixed; inset:0; background: rgba(0,0,0,0.98); z-index: 10000; overflow-y: auto; padding: 20px; }
        .modal-content { max-width: 1100px; margin: 0 auto; background: #111; border-radius: 20px; border: 1px solid var(--gold); padding: 30px; }
        .close-btn { float: right; font-size: 30px; color: var(--gold); cursor: pointer; }
        .inner-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; margin-top: 20px; }
        .blueprint { background: #fff; padding: 20px; border-radius: 10px; color: black; }
        .specs-table { width: 100%; margin-top: 15px; border-collapse: collapse; }
        .specs-table td { padding: 10px; border-bottom: 1px solid #333; }
    </style>
</head>
<body>

    <nav>
        <h2 class="logo">SHAVKAT <span>VIP-AI</span></h2>
        <div><i class="fa fa-user-shield"></i> Premium Rejim</div>
    </nav>

    <section class="ai-header">
        <h1>Aqlli Arxitektor Tizimi</h1>
        <p>Byudjet va xohishingizni kiriting, AI cheksiz variantlar chiqaradi</p>
        <div class="filter-grid">
            <input type="number" id="f-price" placeholder="Maksimal pul ($)">
            <select id="f-rooms">
                <option value="3">3 xonali</option>
                <option value="5">5 xonali</option>
                <option value="8">8+ xonali</option>
            </select>
            <select id="f-mat">
                <option value="G'isht">Pishgan g'isht</option>
                <option value="Loy">Milliy (Loy/Somon)</option>
                <option value="Beton">Monolit Beton</option>
            </select>
            <button class="btn-gen" onclick="generateHouses()">YANGI LOYIHALAR</button>
        </div>
    </section>

    <div class="catalog" id="catalog"></div>

    <div id="project-modal">
        <div class="modal-content">
            <span class="close-btn" onclick="closeProject()">&times;</span>
            <h2 id="m-title" style="color: var(--gold);">Loyiha Tafsilotlari</h2>
            <div class="inner-grid">
                <div>
                    <img id="m-img" src="" style="width:100%; border-radius:15px; height: 350px; object-fit: cover;">
                    <div style="margin-top:20px; padding:20px; background:#222; border-radius:10px;">
                        <h3><i class="fa fa-street-view"></i> 360° Virtual Tur</h3>
                        <p style="color:#888;">Xonalararo sayohat yuklanmoqda...</p>
                        <div style="height:150px; background:#000; margin-top:10px; border-radius:10px; display:flex; align-items:center; justify-content:center;">
                             <span style="color:var(--gold)">[ 360 VIEW ACTIVE ]</span>
                        </div>
                    </div>
                </div>
                <div>
                    <h3>Texnik Parametrlar (0-dan hamma narsasi)</h3>
                    <table class="specs-table">
                        <tr><td>Umumiy maydon:</td><td id="m-area" style="text-align:right; font-weight:bold;">-</td></tr>
                        <tr><td>Xonalar soni:</td><td id="m-rooms" style="text-align:right; font-weight:bold;">-</td></tr>
                        <tr><td>Eshik balandligi:</td><td style="text-align:right; font-weight:bold;">2.20 m</td></tr>
                        <tr><td>Deraza turi:</td><td style="text-align:right; font-weight:bold;">Panorama (Vakuum)</td></tr>
                        <tr><td>Oshxona kvadrati:</td><td style="text-align:right; font-weight:bold;">18 m²</td></tr>
                        <tr><td>Hammoм / Vanna:</td><td style="text-align:right; font-weight:bold;">7.5 m²</td></tr>
                        <tr><td>Shift balandligi:</td><td style="text-align:right; font-weight:bold;">3.40 m</td></tr>
                        <tr><td>Material:</td><td id="m-mat" style="text-align:right; font-weight:bold; color:var(--gold);">-</td></tr>
                    </table>
                    <button class="btn-gen" style="margin-top:20px;"><i class="fa fa-download"></i> PDF SMETANI YUKLASH</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        const images = [
            "https://images.unsplash.com/photo-1613490493576-7fde63acd811?w=600",
            "https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=600",
            "https://images.unsplash.com/photo-1512917774080-9991f1c4c750?w=600",
            "https://images.unsplash.com/photo-1583608205776-bfd35f0d9f83?w=600"
        ];

        function generateHouses() {
            const catalog = document.getElementById('catalog');
            const rooms = document.getElementById('f-rooms').value;
            const mat = document.getElementById('f-mat').value;
            const price = document.getElementById('f-price').value || "45,000";

            catalog.innerHTML = ''; // Tozalash
            
            for(let i=0; i<9; i++) {
                const id = Math.floor(Math.random() * 9000) + 1000;
                const img = images[Math.floor(Math.random() * images.length)];
                const area = Math.floor(Math.random() * 300) + 80;

                catalog.innerHTML += `
                    <div class="card">
                        <img src="${img}">
                        <div class="card-body">
                            <div style="display:flex; justify-content:space-between; color:var(--gold);">
                                <b>VIP-${id}</b> <b>$${price}</b>
                            </div>
                            <h3 style="margin:10px 0;">Elite ${mat} Design</h3>
                            <p style="color:#888; font-size:14px;">Xonalar: ${rooms} | Maydon: ${area} m²</p>
                            <button class="btn-gen" style="margin-top:15px;" onclick="openProject('${img}', '${mat}', '${area}', '${rooms}')">
                                <i class="fa fa-door-open"></i> ICHIGA KIRISH
                            </button>
                        </div>
                    </div>
                `;
            }
        }

        function openProject(img, mat, area, rooms) {
            document.getElementById('m-img').src = img;
            document.getElementById('m-mat').innerText = mat;
            document.getElementById('m-area').innerText = area + " m²";
            document.getElementById('m-rooms').innerText = rooms + " ta";
            document.getElementById('project-modal').style.display = 'block';
            document.body.style.overflow = 'hidden'; // Skrollni to'xtatish
        }

        function closeProject() {
            document.getElementById('project-modal').style.display = 'none';
            document.body.style.overflow = 'auto';
        }

        window.onload = generateHouses;
    </script>
</body>
</html>

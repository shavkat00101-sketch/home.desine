<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SHAVKAT VIP AI-ARCHITECT</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root { --gold: #c5a059; --dark: #0f0f0f; --glass: rgba(255,255,255,0.1); }
        * { margin:0; padding:0; box-sizing:border-box; font-family: 'Poppins', sans-serif; }
        body { background: #050505; color: white; overflow-x: hidden; }

        /* VIP Header */
        header { padding: 20px 5%; background: var(--dark); border-bottom: 1px solid var(--gold); display: flex; justify-content: space-between; align-items: center; position: sticky; top: 0; z-index: 100; }
        .vip-badge { background: var(--gold); color: black; padding: 2px 10px; border-radius: 5px; font-size: 12px; font-weight: bold; }

        /* AI Input Box */
        .ai-panel { padding: 40px 5%; text-align: center; background: linear-gradient(to bottom, #1a1a1a, #050505); }
        .ai-input-wrapper { max-width: 800px; margin: 0 auto; background: var(--glass); padding: 30px; border-radius: 25px; border: 1px solid rgba(197, 160, 89, 0.3); backdrop-filter: blur(10px); }
        
        input, select { background: #222; border: 1px solid #444; color: white; padding: 15px; border-radius: 12px; width: 100%; margin-bottom: 15px; outline: none; }
        .btn-vip { background: var(--gold); color: black; border: none; padding: 15px 30px; border-radius: 50px; font-weight: bold; cursor: pointer; transition: 0.3s; width: 100%; font-size: 18px; }
        .btn-vip:hover { transform: scale(1.02); box-shadow: 0 0 20px var(--gold); }

        /* Infinite Grid */
        .house-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(350px, 1fr)); gap: 30px; padding: 50px 5%; }
        .vip-card { background: #1a1a1a; border-radius: 20px; border: 1px solid #333; overflow: hidden; transition: 0.5s; }
        .vip-card:hover { border-color: var(--gold); }
        .vip-card img { width: 100%; height: 250px; object-fit: cover; filter: grayscale(30%); transition: 0.5s; }
        .vip-card:hover img { filter: grayscale(0%); transform: scale(1.05); }
        .card-content { padding: 25px; }

        /* Floating AI Chat */
        #ai-chat { position: fixed; bottom: 20px; right: 20px; background: var(--gold); width: 60px; height: 60px; border-radius: 50%; display: flex; align-items: center; justify-content: center; cursor: pointer; font-size: 25px; color: black; box-shadow: 0 5px 15px rgba(0,0,0,0.5); z-index: 1000; }

        .loading-spinner { display: none; margin: 20px auto; width: 50px; height: 50px; border: 5px solid #333; border-top-color: var(--gold); border-radius: 50%; animation: spin 1s infinite linear; }
        @keyframes spin { to { transform: rotate(360deg); } }
    </style>
</head>
<body>

    <header>
        <div class="logo"><h2>SHAVKAT <span class="vip-badge">VIP AI</span></h2></div>
        <div id="status"><i class="fa fa-circle" style="color: #00ff00; font-size: 10px;"></i> AI Tizimi Faol</div>
    </header>

    <section class="ai-panel">
        <h1 style="font-size: 35px; margin-bottom: 20px;">AI Arxitektor: <span style="color: var(--gold);">Cheksiz Imkoniyatlar</span></h1>
        <div class="ai-input-wrapper">
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px;">
                <input type="number" id="budget" placeholder="Byudjetingiz ($)">
                <input type="number" id="sqm" placeholder="Maydon (m2)">
            </div>
            <select id="style">
                <option value="Modern">Zamonaviy (High-Tech)</option>
                <option value="Classic">Klassik</option>
                <option value="Loft">Loft / Minimalizm</option>
                <option value="National">Milliy (Loy / G'isht)</option>
            </select>
            <button class="btn-vip" onclick="generateVIP()">YANGI VIP LOYIHALAR GENERATSIYA QILISH</button>
        </div>
    </section>

    <div class="loading-spinner" id="loader"></div>

    <div class="house-grid" id="catalog">
        </div>

    <div id="ai-chat" onclick="alert('AI Maslahatchi: Men sizga loyiha tanlashda yordam beraman!')">
        <i class="fa fa-robot"></i>
    </div>

    <script>
        // AI Generator mantiqi
        const houseStyles = {
            Modern: ["https://images.unsplash.com/photo-1613490493576-7fde63acd811?w=600", "https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=600"],
            Classic: ["https://images.unsplash.com/photo-1583608205776-bfd35f0d9f83?w=600", "https://images.unsplash.com/photo-1600596542815-ffad4c1539a9?w=600"],
            Loft: ["https://images.unsplash.com/photo-1512917774080-9991f1c4c750?w=600", "https://images.unsplash.com/photo-1576941089067-2de3c901e126?w=600"],
            National: ["https://images.unsplash.com/photo-1595815771614-ade9d652a65d?w=600", "https://images.unsplash.com/photo-1449156001437-3a1661acda22?w=600"]
        };

        function generateVIP() {
            const loader = document.getElementById('loader');
            const catalog = document.getElementById('catalog');
            const style = document.getElementById('style').value;
            const budget = document.getElementById('budget').value || "50,000";
            
            loader.style.display = 'block';
            
            setTimeout(() => {
                loader.style.display = 'none';
                // Cheksiz generatsiya: Har safar 6 ta yangi loyiha qo'shadi
                for(let i=0; i<6; i++) {
                    const randomImg = houseStyles[style][Math.floor(Math.random() * houseStyles[style].length)];
                    const randomID = Math.floor(Math.random() * 9000) + 1000;
                    
                    catalog.innerHTML += `
                        <div class="vip-card">
                            <img src="${randomImg}" alt="House">
                            <div class="card-content">
                                <div style="display:flex; justify-content:space-between; margin-bottom:10px;">
                                    <span style="color:var(--gold); font-weight:bold;">LOYIHA VIP-${randomID}</span>
                                    <span>$${budget}</span>
                                </div>
                                <h3>VIP ${style} Concept</h3>
                                <p style="font-size:13px; color:#888; margin:10px 0;">Eshik: 2.1m | Deraza: Panorama | Ichki qism: To'liq 3D</p>
                                <button class="btn-vip" style="font-size:14px; padding:10px;" onclick="window.open('https://shavkat00101-sketch.github.io/home.desine/')">ICHIGA KIRISH (VR)</button>
                            </div>
                        </div>
                    `;
                }
            }, 1000);
        }

        // Dastlabki yuklash
        window.onload = generateVIP;
    </script>
</body>
</html>

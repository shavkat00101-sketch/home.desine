<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Architect | Aqlli Uy Loyihalari</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <style>
        :root { --p: #2c3e50; --a: #e67e22; --l: #f4f7f6; --d: #1a1a1a; }
        * { margin:0; padding:0; box-sizing:border-box; font-family: 'Segoe UI', sans-serif; }
        body { background: var(--l); color: var(--d); transition: 0.5s; }
        
        /* Navigation */
        nav { background: rgba(44, 62, 80, 0.9); backdrop-filter: blur(10px); padding: 15px 5%; color: white; display: flex; justify-content: space-between; align-items: center; position: sticky; top: 0; z-index: 1000; }
        .logo { font-size: 20px; font-weight: bold; letter-spacing: 1px; }
        .logo span { color: var(--a); }

        /* AI Section */
        .ai-engine { padding: 60px 10%; background: linear-gradient(135deg, #2c3e50, #4ca1af); color: white; text-align: center; }
        .builder-box { background: white; padding: 30px; border-radius: 20px; color: var(--d); max-width: 500px; margin: 30px auto; box-shadow: 0 15px 40px rgba(0,0,0,0.2); }
        input, select { width: 100%; padding: 12px; margin: 10px 0; border-radius: 10px; border: 1px solid #ddd; outline: none; }
        .btn-ai { background: var(--a); color: white; border: none; padding: 15px; width: 100%; border-radius: 10px; font-weight: bold; cursor: pointer; transition: 0.3s; }
        .btn-ai:hover { background: #d35400; transform: scale(1.02); }

        /* Results */
        #result-area { display: none; margin-top: 30px; padding: 20px; background: #fff; border-radius: 15px; color: var(--d); animation: slideUp 0.5s; }
        @keyframes slideUp { from {transform: translateY(50px); opacity: 0;} to {transform: translateY(0); opacity: 1;} }

        /* Stats */
        .stats { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 15px; margin-top: 20px; }
        .stat-card { background: #f9f9f9; padding: 15px; border-radius: 10px; border-bottom: 3px solid var(--a); }

        footer { background: var(--d); color: #777; padding: 30px; text-align: center; font-size: 14px; }
    </style>
</head>
<body>

    <nav>
        <div class="logo">AI<span>ARCHITECT</span></div>
        <i class="fa fa-bars"></i>
    </nav>

    <section class="ai-engine">
        <h1 data-aos="fade-down">Orzungizdagi uyni hisoblang</h1>
        <p>Ma'lumotlarni kiriting, AI sizga loyiha va xarajatlarni chiqarib beradi</p>
        
        <div class="builder-box" data-aos="zoom-in">
            <input type="number" id="area" placeholder="Uy maydoni (masalan: 120) m²">
            <select id="rooms">
                <option value="3">3 xonali uy</option>
                <option value="4">4 xonali uy</option>
                <option value="5">5+ xonali uy</option>
            </select>
            <select id="material">
                <option value="pishgan">Pishgan g'isht</option>
                <option value="xom">Xom g'isht / Blok</option>
            </select>
            <button class="btn-ai" onclick="calculateAI()">LOYIHANI GENERATSIYA QILISH</button>

            <div id="result-area">
                <h3 id="res-title">Sizning loyihangiz tayyor!</h3>
                <div class="stats">
                    <div class="stat-card"><h5>G'isht</h5><p id="bricks">-</p></div>
                    <div class="stat-card"><h5>Sement</h5><p id="cement">-</p></div>
                    <div class="stat-card"><h5>Taxminiy xarajat</h5><p id="cost">-</p></div>
                </div>
                <img id="res-img" src="" style="width:100%; border-radius:10px; margin-top:20px; display:none;">
                <p style="margin-top:15px; font-size:13px; color:#666;">*Hisob-kitoblar taxminiy hisoblangan</p>
            </div>
        </div>
    </section>

    <footer id="contact">
        <p>&copy; 2026 AI Architect Platform. Barcha huquqlar himoyalangan.</p>
        <div style="margin-top:10px;">
            <i class="fab fa-telegram"></i> @arxitektor_ai
        </div>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        AOS.init();

        function calculateAI() {
            let area = document.getElementById('area').value;
            let mat = document.getElementById('material').value;
            let resArea = document.getElementById('result-area');
            
            if(!area || area < 20) {
                alert("Iltimos, maydonni to'g'ri kiriting!");
                return;
            }

            // AI Mantiqi (Algoritm)
            let brickCount = area * 450; 
            let cementCount = Math.floor(area * 0.8);
            let totalCost = area * (mat === 'pishgan' ? 350 : 250);

            document.getElementById('bricks').innerText = brickCount.toLocaleString() + " dona";
            document.getElementById('cement').innerText = cementCount + " qop";
            document.getElementById('cost').innerText = "$" + totalCost.toLocaleString();
            
            // Loyiha rasmini tanlash
            let img = document.getElementById('res-img');
            img.style.display = "block";
            img.src = area > 150 
                ? "https://images.unsplash.com/photo-1613490493576-7fde63acd811?w=600" 
                : "https://images.unsplash.com/photo-1580587771525-78b9dba3b914?w=600";

            resArea.style.display = "block";
            resArea.scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>

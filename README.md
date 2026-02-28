<!DOCTYPE html>
<html lang="uz" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ARCHI-GENESIS VIP | Ultimate Startup Edition</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/pannellum@2.5.6/build/pannellum.js"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/pannellum@2.5.6/build/pannellum.css"/>
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@200;400;800&family=Syncopate:wght@400;700&display=swap');
        
        :root { 
            --gold: #E2B15B; 
            --dark: #050505; 
            --glass: rgba(255, 255, 255, 0.03); 
            --accent: #bc9048;
        }

        body { 
            font-family: 'Plus Jakarta Sans', sans-serif; 
            background: var(--dark); 
            color: #ffffff; 
            cursor: none; /* Maxsus cursor uchun */
        }

        .font-sync { font-family: 'Syncopate', sans-serif; }

        /* Custom Cursor */
        #cursor {
            width: 20px; height: 20px; border: 2px solid var(--gold); border-radius: 50%;
            position: fixed; pointer-events: none; z-index: 10000; transition: transform 0.1s;
        }

        /* Glassmorphism Cards */
        .premium-card {
            background: linear-gradient(135deg, rgba(255,255,255,0.05) 0%, rgba(255,255,255,0.01) 100%);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255,255,255,0.1);
            transition: all 0.6s cubic-bezier(0.23, 1, 0.32, 1);
        }

        .premium-card:hover {
            border-color: var(--gold);
            box-shadow: 0 25px 50px -12px rgba(226, 177, 91, 0.15);
            transform: translateY(-10px) scale(1.02);
        }

        /* Animated Background */
        .bg-mesh {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle at 50% 50%, #1a1a1a 0%, #050505 100%);
            z-index: -1; opacity: 0.5;
        }

        .gold-glow {
            box-shadow: 0 0 30px rgba(226, 177, 91, 0.3);
        }

        /* VR View Overlays */
        #vr-hud {
            position: absolute; top: 20px; left: 20px; background: rgba(0,0,0,0.7);
            padding: 15px; border-radius: 15px; border-left: 4px solid var(--gold);
            z-index: 100; pointer-events: none;
        }

        /* Responsive Animations */
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
            100% { transform: translateY(0px); }
        }

        .floating { animation: float 6s ease-in-out infinite; }

        /* Chart Styles */
        #budgetChart { max-height: 200px; }
    </style>
</head>
<body class="overflow-x-hidden">

    <div id="cursor"></div>
    <div class="bg-mesh"></div>

    <div id="preloader" class="fixed inset-0 z-[9999] bg-black flex flex-col items-center justify-center">
        <div class="text-4xl font-sync font-bold tracking-[1em] mb-4 gold-glow p-4">ARCHI</div>
        <div class="w-48 h-[2px] bg-zinc-800 relative overflow-hidden">
            <div id="progress" class="absolute inset-0 bg-gold w-0 transition-all"></div>
        </div>
        <div class="mt-4 text-[10px] uppercase tracking-widest opacity-40">Loading Startup Core...</div>
    </div>

    <aside class="fixed left-0 top-0 h-full w-24 border-r border-white/5 flex flex-col items-center py-10 z-[1000] glass">
        <div class="text-gold text-2xl font-black mb-20 rotate-[-90deg] font-sync">GENESIS</div>
        <nav class="flex flex-col gap-12">
            <button onclick="scrollToSec('home')" class="nav-icon opacity-40 hover:opacity-100 hover:text-gold transition-all duration-500"><i class="fa-solid fa-house-chimney text-xl"></i></button>
            <button onclick="scrollToSec('catalog')" class="nav-icon opacity-40 hover:opacity-100 hover:text-gold transition-all duration-500"><i class="fa-solid fa-compass text-xl"></i></button>
            <button onclick="scrollToSec('designer')" class="nav-icon opacity-40 hover:opacity-100 hover:text-gold transition-all duration-500"><i class="fa-solid fa-couch text-xl"></i></button>
            <button onclick="toggleAdmin()" class="nav-icon opacity-40 hover:opacity-100 hover:text-gold transition-all duration-500"><i class="fa-solid fa-shield-halved text-xl"></i></button>
        </nav>
        <div class="mt-auto flex flex-col gap-6 text-[10px] font-bold opacity-30 rotate-[-90deg]">
            <span>v5.02</span>
            <span>2026</span>
        </div>
    </aside>

    <main class="ml-24">
        
        <section id="home" class="min-h-screen flex flex-col justify-center px-12 lg:px-24 relative overflow-hidden">
            <div class="absolute top-0 right-0 w-1/2 h-full opacity-20 pointer-events-none">
                <img src="https://images.unsplash.com/photo-1600607687920-4e2a09cf159d?w=1000" class="w-full h-full object-cover grayscale">
            </div>

            <div class="relative z-10" data-aos="fade-up" data-aos-duration="1500">
                <span class="text-gold font-bold tracking-[0.5em] text-xs uppercase mb-6 block">Premium Architecture Engine</span>
                <h1 class="text-7xl lg:text-9xl font-sync font-bold leading-none mb-10">
                    BEYOND <br> <span class="text-transparent" style="-webkit-text-stroke: 1px #E2B15B;">LIMITS.</span>
                </h1>
                
                <div class="flex flex-col md:flex-row gap-10 items-start">
                    <p class="max-w-md text-zinc-500 text-lg leading-relaxed border-l border-gold/30 pl-8">
                        Startupingiz uchun dunyodagi eng ilg'or AI arxitektor platformasi. Budjetingizni kiritib, 3D olamga qadam qo'ying.
                    </p>
                    <div class="glass p-8 rounded-3xl border-l-4 border-gold min-w-[300px]">
                        <div class="text-[10px] uppercase opacity-40 mb-2">Jami Aktiv Loyihalar</div>
                        <div class="text-5xl font-sync font-bold" id="counter">0</div>
                    </div>
                </div>
            </div>

            <div class="mt-20 glass p-10 rounded-[40px] border border-white/10 max-w-6xl" data-aos="zoom-in-up">
                <div class="grid grid-cols-1 md:grid-cols-4 gap-12">
                    <div class="col-span-1 md:col-span-2 space-y-6">
                        <div class="flex justify-between items-center">
                            <label class="text-xs uppercase font-bold tracking-widest text-gold">Budjet Analizi ($)</label>
                            <span id="price-val" class="text-2xl font-bold font-sync">$120,000</span>
                        </div>
                        <input type="range" id="price-slider" min="25000" max="500000" step="5000" value="120000" 
                               class="w-full h-1 bg-zinc-800 accent-gold appearance-none rounded-lg cursor-pointer" oninput="updateCore()">
                        <div class="flex justify-between opacity-30 text-[10px] font-bold">
                            <span>MIN: $25,000</span>
                            <span>MAX: $500,000</span>
                        </div>
                    </div>

                    <div class="space-y-4">
                        <label class="text-xs uppercase font-bold tracking-widest text-gold">Xonalar Standarti</label>
                        <select id="room-select" onchange="updateCore()" class="w-full bg-white/5 border border-white/10 p-4 rounded-2xl outline-none focus:border-gold transition-all">
                            <option value="all">Barcha Loyihalar</option>
                            <option value="3">3+ Xonali Villalar</option>
                            <option value="5">5+ Xonali Premium</option>
                            <option value="8">8+ Xonali Saroylar</option>
                        </select>
                    </div>

                    <button onclick="updateCore()" class="bg-gold text-black font-black uppercase text-xs tracking-[0.2em] rounded-2xl h-16 hover:shadow-[0_0_30px_rgba(226,177,91,0.4)] transition-all">
                        Generate AI <i class="fa-solid fa-wand-magic-sparkles ml-2"></i>
                    </button>
                </div>
            </div>
        </section>

        <section id="catalog" class="py-32 px-12 lg:px-24">
            <div class="flex flex-col md:flex-row justify-between items-end mb-20 gap-10">
                <div data-aos="fade-right">
                    <h2 class="text-5xl font-sync font-bold uppercase mb-4">Master <span class="text-gold">Catalog</span></h2>
                    <p class="text-zinc-500 max-w-sm">Har bir loyiha 0-dan barcha qurilish smetalari bilan ta'minlangan.</p>
                </div>
                <div class="flex gap-4 glass p-2 rounded-2xl" data-aos="fade-left">
                    <button class="px-6 py-2 rounded-xl text-xs font-bold bg-white/10">Hammasi</button>
                    <button class="px-6 py-2 rounded-xl text-xs font-bold opacity-40 hover:opacity-100">Modern</button>
                    <button class="px-6 py-2 rounded-xl text-xs font-bold opacity-40 hover:opacity-100">Classic</button>
                </div>
            </div>

            <div id="project-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-12">
                </div>
        </section>

        <section id="designer" class="py-32 bg-white/5 px-12 lg:px-24 rounded-[80px] mx-10 border border-white/5">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-24 items-center">
                <div data-aos="fade-right">
                    <span class="text-gold font-bold uppercase tracking-widest text-xs">Smart Interior</span>
                    <h2 class="text-6xl font-sync font-bold mt-4 mb-8">OSHXONA <br> <span class="text-zinc-500 italic">DESIGNER</span></h2>
                    <p class="text-zinc-500 mb-12 leading-relaxed">
                        Bizning tizimimiz har bir uy loyihasi uchun oshxonani alohida modellashtiradi. Shkaflar joylashuvi, ranglar palitrasi va ergonomikani o'zingiz boshqaring.
                    </p>
                    
                    <div class="space-y-6">
                        <div class="flex items-center gap-6 glass p-6 rounded-3xl border-l-4 border-gold">
                            <i class="fa-solid fa-kitchen-set text-3xl text-gold"></i>
                            <div>
                                <h4 class="font-bold">Orol uslubi (Island Style)</h4>
                                <p class="text-xs opacity-50">Keng maydonlar uchun eng yaxshi tanlov.</p>
                            </div>
                        </div>
                        <div class="flex items-center gap-6 glass p-6 rounded-3xl border-l-4 border-zinc-700 opacity-50">
                            <i class="fa-solid fa-border-all text-3xl"></i>
                            <div>
                                <h4 class="font-bold">L-Uslubi</h4>
                                <p class="text-xs opacity-50">Minimalist va qulay yechim.</p>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="relative" data-aos="zoom-in">
                    <div class="aspect-square rounded-[60px] overflow-hidden border-8 border-white/5">
                        <img src="https://images.unsplash.com/photo-1556911220-e15b29be8c8f?w=800" class="w-full h-full object-cover">
                    </div>
                    <div class="absolute -bottom-10 -left-10 glass p-10 rounded-[40px] border border-gold/30 gold-glow">
                        <h3 class="text-3xl font-sync font-bold text-gold">98%</h3>
                        <p class="text-[10px] uppercase font-bold opacity-50">Dizayn Aniqligi</p>
                    </div>
                </div>
            </div>
        </section>

        <footer class="py-20 text-center opacity-40 text-xs tracking-[0.5em] uppercase">
            © 2026 ARCHI-GENESIS STARTUP | ALL RIGHTS RESERVED
        </footer>
    </main>

    <div id="vr-overlay" class="fixed inset-0 z-[5000] bg-black hidden flex flex-col">
        <div id="vr-hud">
            <div class="text-[10px] gold-text font-bold uppercase mb-1">Xona Holati</div>
            <div id="hud-room" class="text-2xl font-sync font-bold text-white mb-4 uppercase">Mehmonxona</div>
            <div class="grid grid-cols-2 gap-4 text-[10px] opacity-60 uppercase font-bold">
                <div>Shift: <span id="hud-ceiling" class="text-white">3.4m</span></div>
                <div>Maydon: <span id="hud-area" class="text-white">45m2</span></div>
            </div>
        </div>

        <button onclick="closeVR()" class="absolute top-10 right-10 z-[5100] w-16 h-16 rounded-full glass border border-white/20 hover:bg-gold hover:text-black transition-all flex items-center justify-center">
            <i class="fa-solid fa-xmark text-2xl"></i>
        </button>

        <div id="panorama-engine" class="flex-1 bg-zinc-900"></div>

        <div class="h-64 glass border-t border-white/10 p-12 flex justify-between items-center">
            <div>
                <h3 id="vr-title" class="text-5xl font-sync font-bold text-gold uppercase mb-2">Modern Villa</h3>
                <p id="vr-sub" class="text-zinc-500 uppercase tracking-widest text-xs">Full Structural Analysis 2026</p>
            </div>
            
            <div class="flex gap-6">
                <button onclick="generateSmetaPDF()" class="px-10 py-5 rounded-2xl border border-white/10 font-bold hover:bg-white hover:text-black transition-all uppercase text-xs tracking-widest">
                    <i class="fa-solid fa-file-pdf mr-2"></i> Smeta Yuklash
                </button>
                <button class="px-10 py-5 rounded-2xl bg-gold text-black font-black uppercase text-xs tracking-widest hover:scale-105 transition-all">
                    Sotib Olish
                </button>
            </div>
        </div>
    </div>

    <div id="admin-modal" class="fixed inset-0 z-[6000] bg-black/95 hidden items-center justify-center p-6 backdrop-blur-2xl">
        <div class="glass max-w-2xl w-full p-12 rounded-[50px] border border-gold/20">
            <h2 class="text-4xl font-sync font-bold text-gold mb-10 uppercase italic">Admin <span class="text-white">Engine</span></h2>
            <div class="grid grid-cols-2 gap-6">
                <input type="text" id="adm-name" placeholder="Loyiha Nomi" class="bg-white/5 p-5 rounded-2xl border border-white/10 outline-none focus:border-gold">
                <input type="number" id="adm-price" placeholder="Narxi ($)" class="bg-white/5 p-5 rounded-2xl border border-white/10 outline-none focus:border-gold">
                <input type="number" id="adm-rooms" placeholder="Xonalar" class="bg-white/5 p-5 rounded-2xl border border-white/10 outline-none focus:border-gold">
                <input type="text" id="adm-img" placeholder="Rasm URL" class="bg-white/5 p-5 rounded-2xl border border-white/10 outline-none focus:border-gold">
            </div>
            <button onclick="saveProject()" class="w-full mt-10 bg-gold text-black py-5 rounded-2xl font-black uppercase tracking-widest">Bazaga Saqlash</button>
            <button onclick="toggleAdmin()" class="w-full mt-4 text-xs opacity-40 uppercase">Yopish</button>
        </div>
    </div>

    <script>
        AOS.init();

        // 1. DATABASE (JSON Simulyatsiya)
        let projects = [
            { id: 1, name: "Golden Horizon", price: 185000, rooms: 6, area: 350, style: "Modern", mat: "Monolit / Shisha", img: "https://images.unsplash.com/photo-1613490493576-7fde63acd811?w=800", panorama: "https://pannellum.org/images/alma.jpg", specs: {kitchen: 30, bath: 12, height: 3.5} },
            { id: 2, name: "Imperial Oak", price: 85000, rooms: 3, area: 180, style: "Classic", mat: "Pishgan g'isht", img: "https://images.unsplash.com/photo-1583608205776-bfd35f0d9f83?w=800", panorama: "https://pannellum.org/images/jure.jpg", specs: {kitchen: 18, bath: 8, height: 3.2} },
            { id: 3, name: "Eco Oasis", price: 45000, rooms: 2, area: 95, style: "Minimalist", mat: "Gazobeton", img: "https://images.unsplash.com/photo-1512917774080-9991f1c4c750?w=800", panorama: "https://pannellum.org/images/cerro-toco-0.jpg", specs: {kitchen: 14, bath: 6, height: 3.0} },
            { id: 4, name: "Skyline Loft", price: 125000, rooms: 4, area: 240, style: "Modern", mat: "Beton/Shisha", img: "https://images.unsplash.com/photo-1600607687920-4e2a09cf159d?w=800", panorama: "https://pannellum.org/images/alma.jpg", specs: {kitchen: 22, bath: 10, height: 3.4} },
            { id: 5, name: "Sand Palace", price: 295000, rooms: 9, area: 550, style: "Classic", mat: "Mramor / G'isht", img: "https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=800", panorama: "https://pannellum.org/images/jure.jpg", specs: {kitchen: 45, bath: 20, height: 4.0} }
        ];

        // 2. CURSOR ENGINE
        const cursor = document.getElementById('cursor');
        document.addEventListener('mousemove', e => {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
        });

        // 3. PRELOADER & COUNTER
        window.addEventListener('load', () => {
            let p = 0;
            let int = setInterval(() => {
                p += 5;
                document.getElementById('progress').style.width = p + '%';
                if(p >= 100) {
                    clearInterval(int);
                    document.getElementById('preloader').style.opacity = '0';
                    setTimeout(() => document.getElementById('preloader').style.display = 'none', 1000);
                    countEffect();
                }
            }, 50);
        });

        function countEffect() {
            let count = 0;
            let target = projects.length * 124; // Simulyatsiya
            let int = setInterval(() => {
                count += 5;
                document.getElementById('counter').innerText = count;
                if(count >= target) clearInterval(int);
            }, 10);
        }

        // 4. FILTER SYSTEM (AI CORE)
        function updateCore() {
            const budget = parseInt(document.getElementById('price-slider').value);
            const rooms = document.getElementById('room-select').value;
            document.getElementById('price-val').innerText = `$${budget.toLocaleString()}`;

            const filtered = projects.filter(p => {
                const roomMatch = rooms === 'all' || p.rooms >= parseInt(rooms);
                return p.price <= budget && roomMatch;
            });

            renderCatalog(filtered);
        }

        function renderCatalog(data) {
            const grid = document.getElementById('project-grid');
            grid.innerHTML = data.map(p => `
                <div class="premium-card rounded-[50px] overflow-hidden group">
                    <div class="h-80 relative overflow-hidden">
                        <img src="${p.img}" class="w-full h-full object-cover transition-transform duration-[2s] group-hover:scale-125">
                        <div class="absolute inset-0 bg-gradient-to-t from-black via-transparent to-transparent"></div>
                        <div class="absolute top-6 right-6 bg-gold text-black font-black px-5 py-1 rounded-full text-xs italic">$${(p.price/1000).toFixed(0)}k</div>
                    </div>
                    <div class="p-10">
                        <div class="flex items-center gap-3 mb-4">
                            <span class="w-8 h-[1px] bg-gold"></span>
                            <span class="text-[10px] font-bold uppercase tracking-[0.3em] text-gold">${p.style}</span>
                        </div>
                        <h3 class="text-3xl font-sync font-bold mb-6 group-hover:text-gold transition-colors">${p.name}</h3>
                        <div class="flex justify-between text-[11px] font-bold opacity-40 uppercase mb-10">
                            <span><i class="fa-solid fa-expand mr-2"></i> ${p.area} m²</span>
                            <span><i class="fa-solid fa-bed mr-2"></i> ${p.rooms} Xona</span>
                        </div>
                        <button onclick="openVR(${p.id})" class="w-full bg-white/5 border border-white/10 py-5 rounded-3xl font-black uppercase text-[10px] tracking-widest hover:bg-gold hover:text-black transition-all duration-500">
                            Enter 3D World <i class="fa-solid fa-arrow-right ml-2"></i>
                        </button>
                    </div>
                </div>
            `).join('');
        }

        // 5. 3D VIRTUAL ENGINE (STREET VIEW SIMULATION)
        let activeVR = null;

        function openVR(id) {
            const p = projects.find(x => x.id === id);
            document.getElementById('vr-overlay').classList.remove('hidden');
            document.body.style.overflow = 'hidden';

            // HUD & UI Update
            document.getElementById('vr-title').innerText = p.name;
            document.getElementById('hud-area').innerText = p.area + "m2";
            document.getElementById('hud-ceiling').innerText = p.specs.height + "m";

            if(activeVR) activeVR.destroy();

            activeVR = pannellum.viewer('panorama-engine', {
                "type": "panorama",
                "panorama": p.panorama,
                "autoLoad": true,
                "title": p.name,
                "hotSpots": [
                    { "pitch": -10, "yaw": 110, "type": "info", "text": "Oshxona zonasi yuklanmoqda...", "URL": "#" },
                    { "pitch": 5, "yaw": -20, "type": "info", "text": "Ventilyatsiya: Sifatli havo aylanishi", "URL": "#" }
                ]
            });
        }

        function closeVR() {
            document.getElementById('vr-overlay').classList.add('hidden');
            document.body.style.overflow = 'auto';
        }

        // 6. PDF SMETA GENERATOR
        function generateSmetaPDF() {
            const { jsPDF } = window.jspdf;
            const doc = new jsPDF();
            const name = document.getElementById('vr-title').innerText;
            
            doc.setFillColor(5, 5, 5);
            doc.rect(0, 0, 210, 297, 'F');
            doc.setTextColor(226, 177, 91);
            doc.setFontSize(30);
            doc.text("ARCHI-GENESIS", 20, 40);
            doc.setTextColor(255, 255, 255);
            doc.setFontSize(16);
            doc.text("RASMIY QURILISH SMETASI: " + name, 20, 60);
            doc.line(20, 70, 190, 70);
            
            doc.setFontSize(12);
            doc.text("1. Poydevor ishlari: Beton M400 - $12,500", 20, 90);
            doc.text("2. Devorlar: Pishgan g'isht (1-nav) - $18,000", 20, 105);
            doc.text("3. Tom yopish: Germaniya tunukalari - $9,400", 20, 120);
            doc.text("4. Ichki dizayn & Panoramik oynalar - $22,000", 20, 135);
            
            doc.setTextColor(226, 177, 91);
            doc.text("JAMI TAXMINIY BYUDJET: " + document.getElementById('price-val').innerText, 20, 170);
            
            doc.save("ARCHI_GENESIS_" + name + "_SMETA.pdf");
        }

        // 7. ADMIN CONTROLS
        function toggleAdmin() {
            const m = document.getElementById('admin-modal');
            if(m.classList.contains('hidden')) {
                const pin = prompt("Startup Master Key?");
                if(pin === "2026") m.classList.remove('hidden');
                else alert("Ruxsat yo'q!");
            } else {
                m.classList.add('hidden');
            }
        }

        function saveProject() {
            const name = document.getElementById('adm-name').value;
            const price = parseInt(document.getElementById('adm-price').value);
            const rooms = parseInt(document.getElementById('adm-rooms').value);
            const img = document.getElementById('adm-img').value;

            if(name && price) {
                projects.unshift({
                    id: Date.now(),
                    name, price, rooms, area: 200, style: "Modern", mat: "Premium",
                    img: img || "https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=800",
                    panorama: "https://pannellum.org/images/alma.jpg",
                    specs: {kitchen: 20, bath: 10, height: 3.2}
                });
                alert("Yangi loyiha AI tizimiga qo'shildi!");
                toggleAdmin();
                updateCore();
            }
        }

        function scrollToSec(id) {
            document.getElementById(id).scrollIntoView({ behavior: 'smooth' });
        }

        // Initial Load
        updateCore();

    </script>
</body>
</html>

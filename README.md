<!DOCTYPE html>
<html lang="uz" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ARCHI-GENIUS VIP | AI Architecture Startup</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/pannellum@2.5.6/build/pannellum.js"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/pannellum@2.5.6/build/pannellum.css"/>
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;500;700&family=Outfit:wght@200;400;900&display=swap');
        
        :root { --gold: #C5A059; --dark: #080808; --card: #121212; }
        body { font-family: 'Outfit', sans-serif; background-color: var(--dark); color: #f0f0f0; }
        .font-header { font-family: 'Space+Grotesk', sans-serif; }
        
        /* Custom UI Elements */
        .gold-gradient { background: linear-gradient(135deg, #C5A059 0%, #F1D38E 50%, #B38642 100%); }
        .glass { background: rgba(255, 255, 255, 0.02); backdrop-filter: blur(15px); border: 1px solid rgba(255, 255, 255, 0.05); }
        .gold-border { border-color: var(--gold); }
        .text-gold { color: var(--gold); }

        /* Scrollbar */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: var(--dark); }
        ::-webkit-scrollbar-thumb { background: var(--gold); border-radius: 10px; }

        /* 3D Viewer Customization */
        #panorama-view { width: 100%; height: 100%; background: #000; }
        .pnlm-load-box { background: rgba(0,0,0,0.8) !important; color: var(--gold) !important; border: 1px solid var(--gold) !important; }
        
        /* Animations */
        .hover-gold:hover { color: var(--gold); text-shadow: 0 0 10px rgba(197, 160, 89, 0.5); transition: 0.3s; }
        .card-anim { transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275); }
        .card-anim:hover { transform: translateY(-15px) scale(1.02); }
    </style>
</head>
<body class="overflow-x-hidden">

    <div id="auth-overlay" class="fixed inset-0 z-[2000] bg-black flex items-center justify-center">
        <div class="glass p-12 rounded-[40px] text-center max-w-md w-full border-t-4 border-yellow-600">
            <h2 class="text-4xl font-header font-black mb-4 uppercase tracking-tighter">STARTUP <span class="text-gold">ACCESS</span></h2>
            <p class="text-zinc-500 mb-8">Professional arxitektura tizimiga kirish uchun ma'lumotlaringizni kiriting.</p>
            <input type="text" id="user-name" placeholder="Ismingiz" class="w-full bg-zinc-900/50 p-4 rounded-2xl mb-4 border border-zinc-800 focus:border-yellow-600 outline-none">
            <input type="tel" id="user-tel" placeholder="Telefon raqamingiz" class="w-full bg-zinc-900/50 p-4 rounded-2xl mb-8 border border-zinc-800 focus:border-yellow-600 outline-none">
            <button onclick="initApp()" class="w-full gold-gradient text-black font-black py-5 rounded-2xl uppercase tracking-widest hover:scale-95 transition">Tizimni Yoqish</button>
        </div>
    </div>

    <nav class="fixed left-0 top-0 h-full w-20 glass flex flex-col items-center py-10 gap-10 z-[1000] hidden md:flex">
        <div class="text-gold text-3xl font-black italic">A</div>
        <div class="flex flex-col gap-8 opacity-40">
            <a href="#home" class="hover-gold text-xl"><i class="fa fa-home"></i></a>
            <a href="#projects" class="hover-gold text-xl"><i class="fa fa-th-large"></i></a>
            <a href="#admin" class="hover-gold text-xl" onclick="toggleAdmin()"><i class="fa fa-cog"></i></a>
        </div>
        <div class="mt-auto opacity-20 text-xs rotate-90 whitespace-nowrap">VERSION 4.2 VIP</div>
    </nav>

    <header class="fixed top-0 right-0 left-0 md:left-20 z-[900] py-6 px-10 flex justify-between items-center glass border-b-0">
        <div class="font-header font-bold text-xl uppercase tracking-[0.3em]">Archi<span class="text-gold">Genius</span></div>
        <div class="flex items-center gap-8">
            <div id="current-user" class="text-xs uppercase opacity-60 hidden sm:block"></div>
            <button class="bg-white/5 border border-white/10 px-6 py-2 rounded-full text-xs font-bold hover:bg-white/10 transition">BOG'LANISH</button>
        </div>
    </header>

    <div class="md:ml-20 pt-32 px-6 lg:px-20 min-h-screen">
        
        <section id="home" class="mb-20">
            <div class="max-w-4xl" data-aos="fade-right">
                <h1 class="text-6xl md:text-8xl font-black font-header leading-[0.9] mb-8">
                    KELAJAK <span class="text-gold">UYINI</span> <br> BUGUN QURING.
                </h1>
                <p class="text-zinc-500 text-lg md:text-xl max-w-xl border-l-2 border-yellow-600 pl-6 mb-12">
                    Startup platformamiz orqali budjetingizni kiritib, professional loyihalarni 3D formatda o'rganing.
                </p>
            </div>

            <div class="glass p-10 rounded-[50px] border border-white/5 shadow-2xl relative z-10" data-aos="fade-up">
                <div class="grid grid-cols-1 md:grid-cols-4 gap-10 items-center">
                    <div class="space-y-4">
                        <label class="text-[10px] uppercase font-bold text-gold tracking-widest">Maksimal Budjet ($)</label>
                        <input type="range" id="filter-price" min="20000" max="300000" step="5000" value="150000" 
                               class="w-full h-1 bg-zinc-800 accent-yellow-600 appearance-none rounded-lg cursor-pointer" oninput="liveRefresh()">
                        <div class="flex justify-between font-black text-2xl">
                            <span>$20k</span>
                            <span id="price-display" class="text-gold">$150,000</span>
                        </div>
                    </div>
                    
                    <div class="space-y-4">
                        <label class="text-[10px] uppercase font-bold text-gold tracking-widest">Xonalar Soni</label>
                        <div class="flex gap-2">
                            <button class="room-btn active bg-yellow-600 text-black px-4 py-2 rounded-lg font-bold" onclick="setRoom('all', this)">ALL</button>
                            <button class="room-btn bg-zinc-900 px-4 py-2 rounded-lg font-bold" onclick="setRoom(2, this)">2+</button>
                            <button class="room-btn bg-zinc-900 px-4 py-2 rounded-lg font-bold" onclick="setRoom(4, this)">4+</button>
                            <button class="room-btn bg-zinc-900 px-4 py-2 rounded-lg font-bold" onclick="setRoom(6, this)">6+</button>
                        </div>
                    </div>

                    <div class="space-y-4">
                        <label class="text-[10px] uppercase font-bold text-gold tracking-widest">Maydon (m²)</label>
                        <input type="number" id="filter-area" value="120" class="w-full bg-transparent border-b-2 border-zinc-800 p-2 text-2xl font-black outline-none focus:border-gold" oninput="liveRefresh()">
                    </div>

                    <button onclick="liveRefresh()" class="gold-gradient text-black h-20 rounded-3xl font-black text-lg uppercase shadow-2xl shadow-yellow-900/20 hover:scale-105 transition">
                        Qidirish <i class="fa fa-bolt ml-2"></i>
                    </button>
                </div>
            </div>
        </section>

        <section id="projects" class="py-20">
            <div class="flex justify-between items-end mb-16">
                <div>
                    <h2 class="text-4xl font-header font-black uppercase">Loyihalar <span class="text-zinc-600">Katalogi</span></h2>
                    <div class="h-1 w-20 gold-gradient mt-4"></div>
                </div>
                <div class="text-xs opacity-40 uppercase tracking-widest">Jami: <span id="project-count">0</span> Loyiha</div>
            </div>

            <div id="catalog-container" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-12">
                </div>
        </section>

    </div>

    <div id="walkthrough-panel" class="fixed inset-0 z-[5000] bg-black hidden flex flex-col md:flex-row">
        <button onclick="exitWalkthrough()" class="absolute top-10 right-10 z-[5100] bg-white/10 p-5 rounded-full backdrop-blur-xl border border-white/20 hover:bg-gold hover:text-black transition duration-500">
            <i class="fa fa-times text-2xl"></i>
        </button>

        <div class="flex-[3] relative">
            <div id="panorama-view"></div>
            <div class="absolute bottom-10 left-1/2 -translate-x-1/2 flex gap-4">
                <button class="px-6 py-3 glass rounded-full text-xs font-bold uppercase tracking-widest" onclick="changeScene('living')">Mehmonxona</button>
                <button class="px-6 py-3 glass rounded-full text-xs font-bold uppercase tracking-widest" onclick="changeScene('kitchen')">Oshxona</button>
            </div>
        </div>

        <div class="flex-1 glass border-l border-white/10 p-12 overflow-y-auto">
            <h2 id="view-title" class="text-5xl font-header font-black text-gold mb-4 uppercase leading-none">Modern Villa</h2>
            <div id="view-style" class="text-xs uppercase border border-gold px-3 py-1 rounded inline-block mb-10 tracking-widest text-gold font-bold">Luxe Minimalist</div>
            
            <p id="view-desc" class="text-zinc-500 leading-relaxed mb-10">
                Ushbu loyiha zamonaviy texnologiyalar va milliy arxitektura elementlarini o'zida mujassam etgan. Maxsus dizayn oshxonasi va keng yotoqxonalari bilan ajralib turadi.
            </p>

            <div class="space-y-6 mb-12">
                <div class="flex justify-between border-b border-white/5 pb-4 text-sm">
                    <span class="opacity-40 uppercase">Narxi</span>
                    <span id="view-price" class="font-bold text-xl">$120,000</span>
                </div>
                <div class="flex justify-between border-b border-white/5 pb-4 text-sm">
                    <span class="opacity-40 uppercase">Oshxona Maydoni</span>
                    <span id="view-kitchen" class="font-bold">24 m²</span>
                </div>
                <div class="flex justify-between border-b border-white/5 pb-4 text-sm">
                    <span class="opacity-40 uppercase">Shift Balandligi</span>
                    <span id="view-ceiling" class="font-bold">3.4 m</span>
                </div>
                <div class="flex justify-between border-b border-white/5 pb-4 text-sm">
                    <span class="opacity-40 uppercase">Materiallar</span>
                    <span id="view-mat" class="font-bold text-gold uppercase">Pishgan g'isht</span>
                </div>
            </div>

            <div class="grid grid-cols-2 gap-4">
                <button onclick="downloadSmeta()" class="bg-zinc-900 border border-zinc-700 py-5 rounded-2xl font-bold uppercase text-[10px] tracking-widest hover:bg-white hover:text-black transition">Smetani Yuklash</button>
                <button onclick="alert('Loyiha menejeri bilan bog'lanish yuborildi!')" class="gold-gradient text-black py-5 rounded-2xl font-black uppercase text-[10px] tracking-widest">Sotib Olish</button>
            </div>
        </div>
    </div>

    <div id="admin-panel" class="fixed inset-0 z-[6000] bg-black/95 hidden flex items-center justify-center p-6 backdrop-blur-3xl">
        <div class="glass w-full max-w-4xl p-12 rounded-[50px] relative border border-white/10 overflow-y-auto max-h-[90vh]">
            <button onclick="toggleAdmin()" class="absolute top-10 right-10 text-4xl opacity-40 hover:opacity-100">&times;</button>
            <h2 class="text-4xl font-header font-black gold-text mb-10 uppercase tracking-tighter italic">Admin <span class="text-white">Studio</span></h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="space-y-2">
                    <label class="text-[10px] uppercase font-bold opacity-40">Loyiha Nomi</label>
                    <input type="text" id="admin-name" class="w-full bg-zinc-900 p-4 rounded-xl border border-zinc-800 outline-none focus:border-gold">
                </div>
                <div class="space-y-2">
                    <label class="text-[10px] uppercase font-bold opacity-40">Budjet ($)</label>
                    <input type="number" id="admin-price" class="w-full bg-zinc-900 p-4 rounded-xl border border-zinc-800 outline-none focus:border-gold">
                </div>
                <div class="space-y-2">
                    <label class="text-[10px] uppercase font-bold opacity-40">Xonalar Soni</label>
                    <input type="number" id="admin-rooms" class="w-full bg-zinc-900 p-4 rounded-xl border border-zinc-800 outline-none focus:border-gold">
                </div>
                <div class="space-y-2">
                    <label class="text-[10px] uppercase font-bold opacity-40">Maydon (m2)</label>
                    <input type="number" id="admin-area" class="w-full bg-zinc-900 p-4 rounded-xl border border-zinc-800 outline-none focus:border-gold">
                </div>
                <div class="space-y-2">
                    <label class="text-[10px] uppercase font-bold opacity-40">Style & Material</label>
                    <select id="admin-style" class="w-full bg-zinc-900 p-4 rounded-xl border border-zinc-800 outline-none focus:border-gold text-white">
                        <option>Modern / High-Tech</option>
                        <option>Classic / Imperial</option>
                        <option>National / Eco</option>
                        <option>Minimalist / Loft</option>
                    </select>
                </div>
                <div class="space-y-2">
                    <label class="text-[10px] uppercase font-bold opacity-40">Rasm URL</label>
                    <input type="text" id="admin-img" class="w-full bg-zinc-900 p-4 rounded-xl border border-zinc-800 outline-none focus:border-gold" placeholder="https://unsplash.com/...">
                </div>
            </div>
            
            <button onclick="saveNewProject()" class="w-full gold-gradient text-black py-6 rounded-3xl font-black uppercase tracking-widest mt-12 shadow-2xl shadow-yellow-600/20">Loyihani Tasdiqlash va Bazaga Qo'shish</button>
        </div>
    </div>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        AOS.init();

        // 1. DATABASE & CONFIG
        let currentRoomFilter = 'all';
        let projects = [
            { id: 1, name: "Registan View Villa", price: 185000, rooms: 6, area: 320, mat: "Pishgan g'isht", style: "National / Eco", img: "https://images.unsplash.com/photo-1613490493576-7fde63acd811?w=800", panorama: "https://pannellum.org/images/alma.jpg", specs: {kitchen: 28, bath: 12, ceiling: 3.5, doors: 2.3} },
            { id: 2, name: "Obsidian Heights", price: 245000, rooms: 8, area: 450, mat: "Beton / Shisha", style: "Modern / High-Tech", img: "https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=800", panorama: "https://pannellum.org/images/cerro-toco-0.jpg", specs: {kitchen: 35, bath: 15, ceiling: 4.0, doors: 2.5} },
            { id: 3, name: "Neo Minimal House", price: 42000, rooms: 2, area: 95, mat: "Gazobeton", style: "Minimalist / Loft", img: "https://images.unsplash.com/photo-1512917774080-9991f1c4c750?w=800", panorama: "https://pannellum.org/images/jure.jpg", specs: {kitchen: 14, bath: 6, ceiling: 3.0, doors: 2.1} },
            { id: 4, name: "Heritage Classic", price: 78000, rooms: 4, area: 180, mat: "Pishgan g'isht", style: "Classic / Imperial", img: "https://images.unsplash.com/photo-1583608205776-bfd35f0d9f83?w=800", panorama: "https://pannellum.org/images/alma.jpg", specs: {kitchen: 20, bath: 10, ceiling: 3.3, doors: 2.2} },
            { id: 5, name: "Glass River House", price: 135000, rooms: 5, area: 260, mat: "Monolit", style: "Modern / High-Tech", img: "https://images.unsplash.com/photo-1600607687920-4e2a09cf159d?w=800", panorama: "https://pannellum.org/images/cerro-toco-0.jpg", specs: {kitchen: 24, bath: 12, ceiling: 3.4, doors: 2.4} }
        ];

        // 2. AUTH & INIT
        function initApp() {
            const name = document.getElementById('user-name').value;
            if(!name) { alert("Ismingizni kiriting!"); return; }
            document.getElementById('auth-overlay').classList.add('opacity-0', 'pointer-events-none', 'duration-700');
            document.getElementById('current-user').innerText = `USER: ${name}`;
            setTimeout(() => { document.getElementById('auth-overlay').style.display = 'none'; }, 700);
            liveRefresh();
        }

        // 3. FILTERING ENGINE
        function setRoom(val, el) {
            currentRoomFilter = val;
            document.querySelectorAll('.room-btn').forEach(b => b.classList.remove('active', 'bg-yellow-600', 'text-black'));
            document.querySelectorAll('.room-btn').forEach(b => b.classList.add('bg-zinc-900'));
            el.classList.add('active', 'bg-yellow-600', 'text-black');
            el.classList.remove('bg-zinc-900');
            liveRefresh();
        }

        function liveRefresh() {
            const budget = parseInt(document.getElementById('filter-price').value);
            const area = parseInt(document.getElementById('filter-area').value);
            document.getElementById('price-display').innerText = `$${budget.toLocaleString()}`;

            const filtered = projects.filter(p => {
                const roomMatch = currentRoomFilter === 'all' || p.rooms >= currentRoomFilter;
                return p.price <= budget && p.area >= area && roomMatch;
            });

            renderGrid(filtered);
            document.getElementById('project-count').innerText = filtered.length;
        }

        function renderGrid(data) {
            const container = document.getElementById('catalog-container');
            container.innerHTML = data.map(p => `
                <div class="p-card card-anim glass rounded-[40px] overflow-hidden relative group">
                    <div class="absolute top-6 left-6 z-20 bg-black/60 backdrop-blur-md border border-white/10 px-4 py-1 rounded-full text-[10px] font-bold tracking-widest text-gold uppercase">
                        ${p.style}
                    </div>
                    <div class="h-80 relative overflow-hidden">
                        <img src="${p.img}" class="w-full h-full object-cover transition duration-1000 group-hover:scale-125">
                        <div class="absolute inset-0 bg-gradient-to-t from-black via-transparent to-transparent opacity-80"></div>
                    </div>
                    <div class="p-10 relative">
                        <div class="flex justify-between items-start mb-6">
                            <h3 class="text-3xl font-header font-black leading-tight">${p.name}</h3>
                            <div class="text-right">
                                <span class="text-gold font-black text-2xl leading-none">$${(p.price/1000).toFixed(0)}k</span>
                                <p class="text-[10px] opacity-40 uppercase">Taxminiy</p>
                            </div>
                        </div>
                        <div class="flex gap-6 text-[11px] font-bold opacity-50 uppercase tracking-widest mb-10">
                            <span><i class="fa fa-expand text-gold mr-2"></i>${p.area} m2</span>
                            <span><i class="fa fa-bed text-gold mr-2"></i>${p.rooms} Xona</span>
                        </div>
                        <button onclick="enterWalkthrough(${p.id})" class="w-full bg-white text-black font-black py-5 rounded-2xl flex justify-between px-8 hover:bg-gold transition duration-500">
                            <span>ICHIGA KIRISH</span>
                            <i class="fa fa-arrow-right"></i>
                        </button>
                    </div>
                </div>
            `).join('');
        }

        // 4. 3D VIRTUAL WALKTHROUGH ENGINE
        let activeViewer = null;

        function enterWalkthrough(id) {
            const p = projects.find(x => x.id === id);
            const panel = document.getElementById('walkthrough-panel');
            panel.classList.remove('hidden');
            document.body.style.overflow = 'hidden';

            // UI Data
            document.getElementById('view-title').innerText = p.name;
            document.getElementById('view-price').innerText = `$${p.price.toLocaleString()}`;
            document.getElementById('view-style').innerText = p.style;
            document.getElementById('view-mat').innerText = p.mat;
            document.getElementById('view-kitchen').innerText = p.specs.kitchen + " m²";
            document.getElementById('view-ceiling').innerText = p.specs.ceiling + " m";

            // Init Pannellum
            if(activeViewer) activeViewer.destroy();
            activeViewer = pannellum.viewer('panorama-view', {
                "type": "panorama",
                "panorama": p.panorama,
                "autoLoad": true,
                "title": p.name,
                "hotSpots": [
                    { "pitch": -10, "yaw": 110, "type": "info", "text": "Oshxona zonasi: " + p.specs.kitchen + " m2" },
                    { "pitch": 10, "yaw": -20, "type": "info", "text": "Ventilyatsiya va shift: " + p.specs.ceiling + " m" },
                    { "pitch": -20, "yaw": -170, "type": "scene", "text": "Yotoqxonaga o'tish", "sceneId": "next" }
                ]
            });
        }

        function exitWalkthrough() {
            document.getElementById('walkthrough-panel').classList.add('hidden');
            document.body.style.overflow = 'auto';
        }

        // 5. PDF EXPORT LOGIC
        function downloadSmeta() {
            const { jsPDF } = window.jspdf;
            const doc = new jsPDF();
            const name = document.getElementById('view-title').innerText;
            const price = document.getElementById('view-price').innerText;
            
            doc.setFontSize(22);
            doc.text("ARXITEKTURA LOYIHASI: " + name, 20, 30);
            doc.setFontSize(14);
            doc.text("Taxminiy xarajatlar smetasi (Market Price 2026)", 20, 45);
            doc.line(20, 50, 190, 50);
            
            doc.text("Umumiy narx: " + price, 20, 65);
            doc.text("Material: " + document.getElementById('view-mat').innerText, 20, 75);
            doc.text("Tavsif: Ushbu loyiha barcha standartlarga mos ravishda AI tomonidan yaratildi.", 20, 85);
            
            doc.setFontSize(10);
            doc.text("Hujjat SHAVKAT ARCHI-GENIUS platformasi orqali generatsiya qilindi.", 20, 280);
            
            doc.save(name + "_smeta.pdf");
        }

        // 6. ADMIN DASHBOARD CRUD
        function toggleAdmin() {
            const modal = document.getElementById('admin-panel');
            if(modal.classList.contains('hidden')) {
                const pin = prompt("Admin PIN-kodini kiriting (Test uchun: 2026):");
                if(pin === "2026") modal.classList.remove('hidden');
                else alert("Xato kod!");
            } else {
                modal.classList.add('hidden');
            }
        }

        function saveNewProject() {
            const n = document.getElementById('admin-name').value;
            const p = parseInt(document.getElementById('admin-price').value);
            const r = parseInt(document.getElementById('admin-rooms').value);
            const a = parseInt(document.getElementById('admin-area').value);
            const s = document.getElementById('admin-style').value;
            const i = document.getElementById('admin-img').value;

            if(!n || !p) { alert("Ma'lumotlar to'liq emas!"); return; }

            projects.unshift({
                id: Date.now(),
                name: n, price: p, rooms: r, area: a, style: s,
                img: i || "https://images.unsplash.com/photo-1613490493576-7fde63acd811?w=800",
                mat: "Monolit / G'isht",
                panorama: "https://pannellum.org/images/alma.jpg",
                specs: {kitchen: 20, bath: 10, ceiling: 3.2, doors: 2.2}
            });

            alert("Loyiha Startup bazasiga muvaffaqiyatli qo'shildi!");
            toggleAdmin();
            liveRefresh();
        }

    </script>
</body>
</html>

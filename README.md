<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ARCHI-SYSTEMS v1.0 | Enterprise Architecture Platform</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/pannellum@2.5.6/build/pannellum.js"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/pannellum@2.5.6/build/pannellum.css"/>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>

    <style>
        :root { --primary: #b89150; --bg: #0a0a0c; --card: #151518; --text: #e2e2e7; }
        body { background-color: var(--bg); color: var(--text); font-family: 'Inter', sans-serif; overflow-x: hidden; }
        
        /* 3D Viewport Styling */
        #panorama-container { width: 100%; height: 100%; border-radius: 20px; overflow: hidden; }
        .pnlm-ui { border-radius: 20px; }
        
        /* Custom UI Elements */
        .glass-nav { background: rgba(10, 10, 12, 0.85); backdrop-filter: blur(20px); border-bottom: 1px solid rgba(184, 145, 80, 0.2); }
        .sidebar { border-right: 1px solid rgba(255, 255, 255, 0.05); }
        .btn-gold { background: linear-gradient(135deg, #b89150 0%, #d4af37 100%); color: #000; font-weight: 800; transition: 0.4s; }
        .btn-gold:hover { transform: scale(1.02); box-shadow: 0 0 25px rgba(184, 145, 80, 0.4); }
        
        /* Animations */
        @keyframes fadeIn { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }
        .animate-fade { animation: fadeIn 0.8s ease-out forwards; }
        
        /* Admin Table */
        table { width: 100%; border-collapse: collapse; }
        th, td { padding: 15px; text-align: left; border-bottom: 1px solid rgba(255, 255, 255, 0.05); }
    </style>
</head>
<body>

<div class="flex min-h-screen">

    <aside class="sidebar w-20 lg:w-64 fixed h-full flex flex-col items-center lg:items-start py-8 px-6 glass-nav z-[100]">
        <div class="text-primary font-black text-2xl mb-12 flex items-center gap-3">
            <i class="fa-solid fa-cube"></i> <span class="hidden lg:block">ARCHI.AI</span>
        </div>
        
        <nav class="flex flex-col gap-8 w-full">
            <a href="#" onclick="showSection('explorer')" class="flex items-center gap-4 text-primary hover:text-white transition group">
                <i class="fa-solid fa-compass text-xl"></i> <span class="hidden lg:block">Platforma</span>
            </a>
            <a href="#" onclick="showSection('admin')" class="flex items-center gap-4 opacity-40 hover:opacity-100 transition group">
                <i class="fa-solid fa-database text-xl"></i> <span class="hidden lg:block">Admin Panel</span>
            </a>
            <a href="#" class="flex items-center gap-4 opacity-40 hover:opacity-100 transition group">
                <i class="fa-solid fa-chart-line text-xl"></i> <span class="hidden lg:block">Analitika</span>
            </a>
        </nav>

        <div class="mt-auto text-[10px] opacity-20 uppercase font-bold tracking-widest hidden lg:block">
            System Status: Online<br>Database: Connected
        </div>
    </aside>

    <main class="ml-20 lg:ml-64 flex-1 p-6 lg:p-12">
        
        <section id="explorer-section" class="animate-fade">
            <div class="flex flex-col lg:flex-row justify-between items-start gap-10 mb-12">
                <div>
                    <h1 class="text-4xl lg:text-5xl font-black mb-4">LOYIHA <span class="text-primary">DVIGATELI</span></h1>
                    <p class="text-zinc-500 max-w-lg italic">Startup darajasidagi real-time filtratsiya va 3D vizualizatsiya tizimi.</p>
                </div>
                
                <div class="bg-[#151518] p-8 rounded-[30px] border border-white/5 w-full lg:w-[600px] shadow-2xl">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                        <div>
                            <label class="text-[10px] uppercase font-bold text-primary mb-3 block tracking-widest">Sizning Budjetingiz ($)</label>
                            <input type="number" id="input-budget" value="150000" oninput="runEngine()" class="w-full bg-black border border-zinc-800 p-4 rounded-xl focus:border-primary outline-none text-xl font-bold">
                        </div>
                        <div>
                            <label class="text-[10px] uppercase font-bold text-primary mb-3 block tracking-widest">Xonalar Soni</label>
                            <select id="input-rooms" onchange="runEngine()" class="w-full bg-black border border-zinc-800 p-4 rounded-xl focus:border-primary outline-none">
                                <option value="all">Barchasi</option>
                                <option value="2">2 Xonali</option>
                                <option value="4">4 Xonali</option>
                                <option value="6">6+ Xonali</option>
                            </select>
                        </div>
                        <div class="md:col-span-2">
                            <label class="text-[10px] uppercase font-bold text-primary mb-3 block tracking-widest">Minimal Maydon (m²)</label>
                            <input type="range" id="input-area" min="50" max="500" value="120" oninput="runEngine()" class="w-full h-1 bg-zinc-800 accent-primary appearance-none rounded-lg cursor-pointer">
                            <div class="flex justify-between mt-2 text-xs font-bold"><span id="area-val">120</span> m²</div>
                        </div>
                    </div>
                </div>
            </div>

            <div id="project-container" class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-10">
                </div>
        </section>

        <section id="admin-section" class="hidden animate-fade">
            <div class="flex justify-between items-center mb-10">
                <h2 class="text-3xl font-black uppercase tracking-tighter">Ma'lumotlar Bazasi <span class="text-primary">Boshqaruvi</span></h2>
                <button onclick="openCreateModal()" class="btn-gold px-8 py-3 rounded-xl text-xs uppercase"><i class="fa fa-plus mr-2"></i> Loyiha Qo'shish</button>
            </div>

            <div class="bg-[#151518] rounded-[30px] overflow-hidden border border-white/5">
                <table id="admin-table">
                    <thead>
                        <tr class="bg-black/40 text-[10px] uppercase tracking-widest text-primary">
                            <th>ID</th>
                            <th>Loyiha Nomi</th>
                            <th>Narx ($)</th>
                            <th>Xona</th>
                            <th>Maydon</th>
                            <th>Amallar</th>
                        </tr>
                    </thead>
                    <tbody id="admin-body">
                        </tbody>
                </table>
            </div>
        </section>
    </main>
</div>

<div id="vr-modal" class="fixed inset-0 z-[5000] bg-black hidden flex flex-col md:flex-row">
    <div class="flex-[2] relative">
        <div id="panorama-container"></div>
        <button onclick="closeVR()" class="absolute top-8 right-8 z-[5100] bg-black/50 p-4 rounded-full border border-white/20 hover:bg-primary transition">
            <i class="fa fa-times text-2xl text-white"></i>
        </button>
        <div class="absolute bottom-10 left-1/2 -translate-x-1/2 flex gap-4 z-[5100]">
            <button onclick="changeScene('living')" class="px-6 py-2 bg-black/80 rounded-full text-xs font-bold border border-primary hover:bg-primary hover:text-black transition">MEHMONXONA</button>
            <button onclick="changeScene('kitchen')" class="px-6 py-2 bg-black/80 rounded-full text-xs font-bold border border-primary hover:bg-primary hover:text-black transition">OSHXONA</button>
        </div>
    </div>
    <div class="flex-1 bg-zinc-900/50 backdrop-blur-3xl p-10 border-l border-white/5 flex flex-col overflow-y-auto">
        <h2 id="vr-title" class="text-4xl font-black text-primary mb-4">LOYIHA NOMI</h2>
        <div id="vr-style" class="text-xs font-bold opacity-40 uppercase tracking-widest mb-10 border border-white/10 px-3 py-1 inline-block rounded">MODERN DESIGN</div>
        
        <div class="grid grid-cols-2 gap-4 mb-10">
            <div class="bg-black/40 p-5 rounded-2xl border border-white/5">
                <div class="text-[10px] opacity-40 mb-1">Narxi</div>
                <div id="vr-price" class="text-xl font-bold">$150,000</div>
            </div>
            <div class="bg-black/40 p-5 rounded-2xl border border-white/5">
                <div class="text-[10px] opacity-40 mb-1">Maydon</div>
                <div id="vr-area" class="text-xl font-bold">120 m²</div>
            </div>
        </div>

        <div class="space-y-6 mb-12 flex-1">
            <h4 class="text-xs font-bold uppercase tracking-widest text-primary">Texnik Sifati:</h4>
            <ul id="vr-specs" class="space-y-4 text-sm opacity-80 italic">
                </ul>
        </div>

        <button onclick="generatePDF()" class="w-full btn-gold py-5 rounded-2xl uppercase tracking-widest text-xs">Smetani PDF Yuklash</button>
    </div>
</div>

<script>
    // 1. DATABASE (Simulated Object-Relational Model)
    let DB_HOUSES = [
        { id: 101, name: "Skyline Residence", price: 185000, rooms: 6, area: 320, style: "Modern Luxury", material: "Monolit / Shisha", kitchen: "Island Design", panorama: "https://pannellum.org/images/alma.jpg", specs: ["3.5m Shift", "Energo-tejamkor tizim", "Panoramik oynalar"] },
        { id: 102, name: "Eco Minimalist", price: 42000, rooms: 2, area: 85, style: "Minimalism", material: "Gazobeton", kitchen: "Compact L-Shape", panorama: "https://pannellum.org/images/jure.jpg", specs: ["Tabiiy havo aylanishi", "Akustik izolyatsiya", "Yashil tom imkoniyati"] },
        { id: 103, name: "Imperial Villa", price: 295000, rooms: 8, area: 450, style: "Classic Imperial", material: "Pishgan g'isht", kitchen: "Royal Suite", panorama: "https://pannellum.org/images/cerro-toco-0.jpg", specs: ["Mramor qoplamalar", "Smart Home tizimi", "Maxsus xavfsizlik zonasi"] },
        { id: 104, name: "Family Comfort", price: 75000, rooms: 4, area: 160, style: "Neo-Classic", material: "G'isht", kitchen: "Open Space", panorama: "https://pannellum.org/images/alma.jpg", specs: ["Bolalar maydonchasi", "Avtonom isitish", "Keng balkonlar"] }
    ];

    // 2. BACKEND LOGIC (Calculation & Filter Engine)
    function runEngine() {
        const budget = parseFloat(document.getElementById('input-budget').value) || 0;
        const rooms = document.getElementById('input-rooms').value;
        const area = document.getElementById('input-area').value;
        document.getElementById('area-val').innerText = area;

        // Filtering Algoritmi
        const filteredResults = DB_HOUSES.filter(house => {
            const priceMatch = house.price <= budget;
            const roomMatch = rooms === 'all' || house.rooms >= parseInt(rooms);
            const areaMatch = house.area >= parseInt(area);
            return priceMatch && roomMatch && areaMatch;
        });

        renderExplorer(filteredResults);
        renderAdmin(); // Admin panelni ham yangilab turamiz
    }

    // 3. FRONTEND RENDERER (Clean Code Architecture)
    function renderExplorer(data) {
        const container = document.getElementById('project-container');
        container.innerHTML = data.length ? "" : "<div class='col-span-3 text-center opacity-20 py-20'>Budjetingizga mos loyiha topilmadi...</div>";
        
        data.forEach(house => {
            container.innerHTML += `
                <div class="bg-[#151518] rounded-[40px] overflow-hidden border border-white/5 group hover:border-primary transition duration-500 shadow-xl">
                    <div class="h-64 relative overflow-hidden">
                        <img src="https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=600" class="w-full h-full object-cover group-hover:scale-110 transition duration-700">
                        <div class="absolute top-6 right-6 bg-primary text-black font-black px-4 py-1 rounded-full text-xs italic">$${house.price.toLocaleString()}</div>
                    </div>
                    <div class="p-8">
                        <h3 class="text-2xl font-black mb-3">${house.name}</h3>
                        <div class="flex gap-6 text-[10px] font-bold opacity-40 uppercase tracking-widest mb-8">
                            <span><i class="fa fa-bed mr-2 text-primary"></i>${house.rooms} Xona</span>
                            <span><i class="fa fa-expand mr-2 text-primary"></i>${house.area} m²</span>
                        </div>
                        <button onclick="initVR(${house.id})" class="w-full py-4 rounded-2xl bg-white/5 border border-white/10 hover:bg-primary hover:text-black font-black transition-all duration-300 uppercase text-[10px] tracking-widest">
                            3D VR WALKTHROUGH <i class="fa fa-arrow-right ml-2"></i>
                        </button>
                    </div>
                </div>
            `;
        });
    }

    // 4. 3D STREET VIEW ENGINE (Pannellum Integration)
    let viewerInstance = null;
    let currentActiveHouse = null;

    function initVR(id) {
        currentActiveHouse = DB_HOUSES.find(h => h.id === id);
        const modal = document.getElementById('vr-modal');
        modal.classList.remove('hidden');
        document.body.style.overflow = 'hidden';

        document.getElementById('vr-title').innerText = currentActiveHouse.name;
        document.getElementById('vr-price').innerText = `$${currentActiveHouse.price.toLocaleString()}`;
        document.getElementById('vr-area').innerText = `${currentActiveHouse.area} m²`;
        
        const specsList = document.getElementById('vr-specs');
        specsList.innerHTML = currentActiveHouse.specs.map(s => `<li><i class="fa fa-check text-primary mr-3"></i>${s}</li>`).join('');

        // VR Dvigatelini yoqish
        if(viewerInstance) viewerInstance.destroy();
        viewerInstance = pannellum.viewer('panorama-container', {
            "type": "panorama",
            "panorama": currentActiveHouse.panorama,
            "autoLoad": true,
            "autoRotate": -2,
            "title": currentActiveHouse.name,
            "author": "Archi AI Systems",
            "hotSpots": [
                { "pitch": -10, "yaw": 110, "type": "info", "text": "Oshxona maydoni: 25m2" },
                { "pitch": 10, "yaw": -20, "type": "info", "text": "Ventilyatsiya: Sifatli" }
            ]
        });
    }

    function changeScene(type) {
        // Startup uchun xonalardan xonaga o'tish simulyatsiyasi
        const panos = {
            living: "https://pannellum.org/images/alma.jpg",
            kitchen: "https://pannellum.org/images/jure.jpg"
        };
        viewerInstance.setPanorama(panos[type]);
        Swal.fire({ title: 'Xona almashmoqda...', timer: 1000, showConfirmButton: false, background: '#151518', color: '#fff' });
    }

    function closeVR() {
        document.getElementById('vr-modal').classList.add('hidden');
        document.body.style.overflow = 'auto';
    }

    // 5. ADMIN PANEL (CRUD Operations & State Management)
    function renderAdmin() {
        const body = document.getElementById('admin-body');
        body.innerHTML = DB_HOUSES.map(h => `
            <tr>
                <td class="opacity-30">#${h.id}</td>
                <td class="font-bold">${h.name}</td>
                <td class="text-primary font-black">$${h.price.toLocaleString()}</td>
                <td>${h.rooms}</td>
                <td>${h.area} m²</td>
                <td>
                    <div class="flex gap-4">
                        <button onclick="deleteHouse(${h.id})" class="text-red-500 hover:text-red-400 transition"><i class="fa fa-trash"></i></button>
                        <button class="opacity-20"><i class="fa fa-edit"></i></button>
                    </div>
                </td>
            </tr>
        `).join('');
    }

    function deleteHouse(id) {
        Swal.fire({
            title: 'Haqiqatdan o\'chirmoqchimisiz?',
            text: "Ushbu loyiha bazadan butunlay yo'qoladi!",
            icon: 'warning',
            showCancelButton: true,
            confirmButtonColor: '#b89150',
            cancelButtonColor: '#d33',
            confirmButtonText: 'Ha, o\'chirilsin!'
        }).then((result) => {
            if (result.isConfirmed) {
                DB_HOUSES = DB_HOUSES.filter(h => h.id !== id);
                runEngine();
                Swal.fire('O\'chirildi!', 'Loyiha o\'chirildi.', 'success');
            }
        });
    }

    function openCreateModal() {
        // Backendga ma'lumot yuborish simulyatsiyasi
        Swal.fire({
            title: 'Yangi Loyiha Qo\'shish',
            html: `
                <input id="swal-name" class="swal2-input bg-zinc-900" placeholder="Loyiha nomi">
                <input id="swal-price" type="number" class="swal2-input bg-zinc-900" placeholder="Narxi ($)">
            `,
            focusConfirm: false,
            confirmButtonText: 'Saqlash',
            preConfirm: () => {
                const name = document.getElementById('swal-name').value;
                const price = document.getElementById('swal-price').value;
                if (!name || !price) { Swal.showValidationMessage(`Iltimos to'ldiring`); }
                return { name, price };
            }
        }).then((result) => {
            if (result.value) {
                const newHouse = {
                    id: Date.now(),
                    name: result.value.name,
                    price: parseInt(result.value.price),
                    rooms: 4, area: 150, style: "Custom", material: "G'isht",
                    panorama: "https://pannellum.org/images/alma.jpg",
                    specs: ["Yangi loyiha", "Standart smeta"]
                };
                DB_HOUSES.push(newHouse);
                runEngine();
            }
        });
    }

    // 6. UTILITIES (PDF Generation)
    function generatePDF() {
        const { jsPDF } = window.jspdf;
        const doc = new jsPDF();
        doc.setFontSize(22);
        doc.text("RASMIY QURILISH SMETASI", 20, 30);
        doc.setFontSize(14);
        doc.text(`Loyiha: ${currentActiveHouse.name}`, 20, 50);
        doc.text(`Umumiy Narx: $${currentActiveHouse.price.toLocaleString()}`, 20, 60);
        doc.text(`Maydon: ${currentActiveHouse.area} m2`, 20, 70);
        doc.line(20, 80, 190, 80);
        doc.text("Materiallar va Ishchi kuchi:", 20, 95);
        doc.text("- Devorlar: $12,000", 25, 105);
        doc.text("- Tom yopish: $8,000", 25, 115);
        doc.text("- Ichki dizayn: $15,000", 25, 125);
        doc.save(`${currentActiveHouse.name}_Smeta.pdf`);
    }

    function showSection(id) {
        document.getElementById('explorer-section').classList.add('hidden');
        document.getElementById('admin-section').classList.add('hidden');
        document.getElementById(id + '-section').classList.remove('hidden');
    }

    // INITIAL LAUNCH
    window.onload = runEngine;
</script>

</body>
</html>

<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Modern House Projects | Professional Uy Loyihalari</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <style>
        :root {
            --primary: #2c3e50;
            --accent: #e67e22;
            --light: #f8f9fa;
            --dark: #1a1a1a;
            --glass: rgba(255, 255, 255, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background-color: #fff;
            color: var(--dark);
            overflow-x: hidden;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 20px 50px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .logo {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .logo span { color: var(--accent); }

        .nav-links {
            display: flex;
            list-style: none;
        }

        .nav-links li { margin-left: 30px; }

        .nav-links a {
            text-decoration: none;
            color: var(--primary);
            font-weight: 500;
            transition: 0.3s;
        }

        .nav-links a:hover { color: var(--accent); }

        /* Hero Section */
        .hero {
            height: 100vh;
            background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), 
                        url('https://images.unsplash.com/photo-1600585154340-be6161a56a0c?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
            padding: 0 20px;
        }

        .hero h1 {
            font-size: 4rem;
            margin-bottom: 20px;
            text-transform: uppercase;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 600px;
            margin-bottom: 30px;
        }

        .btn-main {
            padding: 15px 40px;
            background: var(--accent);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            transition: 0.4s;
            border: 2px solid transparent;
        }

        .btn-main:hover {
            background: transparent;
            border-color: white;
            transform: scale(1.1);
        }

        /* Projects Section */
        .projects {
            padding: 100px 10%;
            background: var(--light);
        }

        .section-title {
            text-align: center;
            margin-bottom: 60px;
        }

        .section-title h2 {
            font-size: 2.5rem;
            color: var(--primary);
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .project-card {
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            transition: 0.5s;
            position: relative;
        }

        .project-card:hover {
            transform: translateY(-15px);
        }

        .project-img {
            height: 250px;
            overflow: hidden;
        }

        .project-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: 0.5s;
        }

        .project-card:hover .project-img img {
            transform: scale(1.1);
        }

        .project-info {
            padding: 25px;
        }

        .project-info h3 {
            margin-bottom: 15px;
            color: var(--primary);
        }

        .specs {
            display: flex;
            justify-content: space-between;
            color: #777;
            font-size: 0.9rem;
            border-top: 1px solid #eee;
            padding-top: 15px;
        }

        .specs i {
            color: var(--accent);
            margin-right: 5px;
        }

        /* Contact Section */
        .contact {
            padding: 80px 10%;
            background: var(--primary);
            color: white;
            text-align: center;
        }

        .contact-icon {
            font-size: 3rem;
            margin-bottom: 20px;
            color: var(--accent);
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {transform: translateY(0);}
            40% {transform: translateY(-20px);}
            60% {transform: translateY(-10px);}
        }

        footer {
            padding: 20px;
            text-align: center;
            background: #111;
            color: #666;
            font-size: 0.8rem;
        }

        /* Mobile Styles */
        @media (max-width: 768px) {
            .hero h1 { font-size: 2.5rem; }
            nav { padding: 15px 20px; }
            .nav-links { display: none; }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">URBAN<span>ARCH</span></div>
        <ul class="nav-links">
            <li><a href="#">Bosh sahifa</a></li>
            <li><a href="#projects">Loyihalar</a></li>
            <li><a href="#">Xizmatlar</a></li>
            <li><a href="#contact">Aloqa</a></li>
        </ul>
    </nav>

    <section class="hero">
        <h1 data-aos="fade-up">Kelajak Uyingizni Tanlang</h1>
        <p data-aos="fade-up" data-aos-delay="200">Bizning loyihalarimiz - bu shunchaki chizmalar emas, bu sizning shinam hayotingiz poydevoridir.</p>
        <a href="#projects" class="btn-main" data-aos="zoom-in" data-aos-delay="400">Loyihalarni Ko'rish</a>
    </section>

    <section class="projects" id="projects">
        <div class="section-title" data-aos="fade-down">
            <h2>Eksklyuziv Loyihalar</h2>
            <p>Eng ko'p tanlanadigan zamonaviy uy loyihalari</p>
        </div>

        <div class="grid">
            <div class="project-card" data-aos="fade-up">
                <div class="project-img">
                    <img src="https://images.unsplash.com/photo-1580587771525-78b9dba3b914?auto=format&fit=crop&w=600&q=80" alt="Loyiha 1">
                </div>
                <div class="project-info">
                    <h3>Modern Villa "Crystal"</h3>
                    <p>Minimalistik uslubda yaratilgan keng va yorug' uy.</p>
                    <div class="specs">
                        <span><i class="fa fa-expand"></i> 250 m²</span>
                        <span><i class="fa fa-bed"></i> 4 Xona</span>
                        <span><i class="fa fa-car"></i> 2 Garaj</span>
                    </div>
                </div>
            </div>

            <div class="project-card" data-aos="fade-up" data-aos-delay="100">
                <div class="project-img">
                    <img src="https://images.unsplash.com/photo-1518780664697-55e3ad937233?auto=format&fit=crop&w=600&q=80" alt="Loyiha 2">
                </div>
                <div class="project-info">
                    <h3>Eco House "Green"</h3>
                    <p>Tabiat bilan uyg'unlikda quriladigan energiya tejamkor uy.</p>
                    <div class="specs">
                        <span><i class="fa fa-expand"></i> 180 m²</span>
                        <span><i class="fa fa-bed"></i> 3 Xona</span>
                        <span><i class="fa fa-leaf"></i> Eco-friendly</span>
                    </div>
                </div>
            </div>

            <div class="project-card" data-aos="fade-up" data-aos-delay="200">
                <div class="project-img">
                    <img src="https://images.unsplash.com/photo-1600596542815-ffad4c1539a9?auto=format&fit=crop&w=600&q=80" alt="Loyiha 3">
                </div>
                <div class="project-info">
                    <h3>Classic Mansion</h3>
                    <p>Hashamat va klassikani sevuvchilar uchun maxsus loyiha.</p>
                    <div class="specs">
                        <span><i class="fa fa-expand"></i> 420 m²</span>
                        <span><i class="fa fa-bed"></i> 6 Xona</span>
                        <span><i class="fa fa-swimming-pool"></i> Basseyn</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="contact" id="contact">
        <i class="fa fa-envelope-open contact-icon"></i>
        <h2 data-aos="zoom-in">O'z loyihangizni buyurtma qiling</h2>
        <p style="margin: 20px 0;">Mutaxassislarimiz sizga bepul maslahat berishadi</p>
        <a href="tel:+998901234567" class="btn-main" style="background: white; color: var(--primary);">Qo'ng'iroq qilish</a>
    </section>

    <footer>
        &copy; 2026 URBANARCH Projects. Barcha huquqlar himoyalangan.
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        // Init AOS Animation
        AOS.init({
            duration: 1000,
            once: true
        });

        // Sticky Navbar Effect
        window.addEventListener('scroll', function() {
            const nav = document.querySelector('nav');
            if (window.scrollY > 50) {
                nav.style.padding = '10px 50px';
                nav.style.background = '#fff';
            } else {
                nav.style.padding = '20px 50px';
                nav.style.background = 'rgba(255, 255, 255, 0.95)';
            }
        });
    </script>
</body>
</html>

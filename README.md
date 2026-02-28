<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shavkat Najmitdinov | Portfolio</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <style>
        /* CSS Dizayn */
        :root {
            --primary-color: #00d2ff;
            --secondary-color: #3a7bd5;
            --bg-dark: #0f0c29;
            --text-white: #ffffff;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background: var(--bg-dark);
            color: var(--text-white);
            overflow-x: hidden;
        }

        /* Navigatsiya */
        nav {
            display: flex;
            justify-content: space-around;
            align-items: center;
            height: 80px;
            background: rgba(15, 12, 41, 0.9);
            position: fixed;
            width: 100%;
            z-index: 1000;
            backdrop-filter: blur(10px);
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            letter-spacing: 2px;
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 0 10%;
            flex-wrap: wrap;
            padding-top: 80px;
        }

        .hero-text {
            flex: 1;
            min-width: 300px;
            animation: fadeInLeft 1.5s ease;
        }

        .hero-text h1 {
            font-size: 3.5rem;
            margin-bottom: 10px;
        }

        .hero-text span {
            color: var(--primary-color);
        }

        .hero-image {
            flex: 1;
            display: flex;
            justify-content: center;
            min-width: 300px;
            animation: fadeInRight 1.5s ease;
        }

        .img-box {
            width: 350px;
            height: 450px;
            border-radius: 20px;
            overflow: hidden;
            border: 5px solid var(--primary-color);
            box-shadow: 0 0 20px var(--primary-color);
            transition: transform 0.5s;
        }

        .img-box:hover {
            transform: scale(1.05);
        }

        .img-box img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        /* Ikonkalar Animatsiyasi */
        .social-icons {
            margin-top: 30px;
        }

        .social-icons i {
            font-size: 2rem;
            margin-right: 20px;
            cursor: pointer;
            transition: 0.3s;
            color: var(--text-white);
        }

        .social-icons i:hover {
            color: var(--primary-color);
            transform: translateY(-10px) rotate(360deg);
        }

        /* Tugma */
        .btn {
            display: inline-block;
            margin-top: 20px;
            padding: 12px 30px;
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            color: white;
            text-decoration: none;
            border-radius: 25px;
            font-weight: 600;
            transition: 0.3s;
        }

        .btn:hover {
            box-shadow: 0 0 15px var(--primary-color);
            transform: scale(1.1);
        }

        /* Animatsiyalar */
        @keyframes fadeInLeft {
            from { opacity: 0; transform: translateX(-100px); }
            to { opacity: 1; transform: translateX(0); }
        }

        @keyframes fadeInRight {
            from { opacity: 0; transform: translateX(100px); }
            to { opacity: 1; transform: translateX(0); }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero-text h1 { font-size: 2.5rem; }
            .hero { text-align: center; }
            .img-box { width: 280px; height: 350px; margin-top: 30px; }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">SHAW_PORTFOLIO</div>
    </nav>

    <section class="hero">
        <div class="hero-text">
            <h3>Assalomu alaykum!</h3>
            <h1>Men <span>Najmitdinov Shavkat</span></h1>
            <p>Full-Stack Dasturchi va Dizayner. Men zamonaviy va interaktiv veb-saytlar yarataman.</p>
            
            <div class="social-icons">
                <i class="fab fa-telegram"></i>
                <i class="fab fa-instagram"></i>
                <i class="fab fa-github"></i>
                <i class="fab fa-linkedin"></i>
            </div>

            <a href="#" class="btn">Bog'lanish</a>
        </div>

        <div class="hero-image">
            <div class="img-box">
                <img src="3168.jpg" alt="Najmitdinov Shavkat">
            </div>
        </div>
    </section>

    <script>
        // Oddiy JavaScript animatsiya effekti
        document.addEventListener('mousemove', (e) => {
            const img = document.querySelector('.img-box');
            let xAxis = (window.innerWidth / 2 - e.pageX) / 25;
            let yAxis = (window.innerHeight / 2 - e.pageY) / 25;
            img.style.transform = `rotateY(${xAxis}deg) rotateX(${yAxis}deg)`;
        });
    </script>

</body>
</html>

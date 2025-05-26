<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Design Services - Ramirez Ventures</title>

  <!-- Fonts & Icons -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

  <style>
    :root {
      --primary: #0096FF;
      --secondary: #FF33CC;
      --accent: #FFFF00;
      --dark: #1a1a1a;
      --light: #ffffff;
      --text-light: #f0f0f0;
      --card-bg: rgba(30, 30, 30, 0.9);
      --transition: 0.3s ease-in-out;
      --shadow-sm: 0 2px 4px rgba(0, 0, 0, 0.2);
      --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.3);
      --shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.4);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html {
      font-size: 16px;
      scroll-behavior: smooth;
      scroll-padding-top: 5rem;
    }

    body {
      font-family: 'Inter', sans-serif;
      color: var(--text-light);
      min-height: 100vh;
      line-height: 1.6;
      display: flex;
      flex-direction: column;
      position: relative;
    }

    /* Logo Only */
    .logo-container {
      position: fixed;
      top: 15px;
      left: 20px;
      z-index: 1001;
    }

    .logo {
      height: 40px;
      width: auto;
    }

    /* Main Content Wrapper */
    .content {
      flex: 1;
      z-index: 2;
      position: relative;
    }

    /* Fullscreen Background Slideshow */
    .background-carousel {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 1;
      overflow: hidden;
      pointer-events: none;
    }
    
    .background-carousel img {
      position: absolute;
      width: 100%;
      height: 100%;
      object-fit: cover;
      opacity: -1;
      transition: opacity 1s ease-in-out;
      pointer-events: none;
    }

    .background-carousel img.active {
      opacity: 1;
    }

    /* Optional dark overlay for readability */
    .overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0.75), rgba(0, 0, 0, 0.85));
      z-index: -1;
      pointer-events: none;
    }

    .container {
      max-width: 1200px;
      width: 100%;
      margin: 0 auto;
      padding: 0 1rem;
      flex-grow: 1;
    }

    /* Hero Title Section */
    .hero-title {
      text-align: center;
      padding: 6rem 1rem 2rem;
      max-width: 1200px;
      margin: 0 auto;
      animation: fadeInDown 1s ease forwards;
    }

    .hero-title h2 {
      font-size: clamp(2rem, 6vw, 4rem);
      font-weight: 800;
      margin-bottom: 1rem;
      background: linear-gradient(to right, #00FFFF, #00BFFF);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      text-shadow: 0 2px 6px rgba(0, 0, 0, 0.6);
    }

    .hero-title p {
      font-size: clamp(1rem, 2vw, 1.25rem);
      max-width: 60ch;
      margin: 1.5rem auto 0;
      color: var(--text-light);
    }

    @keyframes fadeInDown {
      from {
        opacity: 0;
        transform: translateY(-20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    main {
      padding-block: 2rem;
      flex: 1;
    }

    /* Services Grid */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 1.5rem;
      list-style-type: none;
      margin: 2rem 0;
      padding: 0;
      position: relative;
      z-index: 10;
    }

    .service-item {
      transition: transform var(--transition);
    }

    .service-item:hover {
      transform: translateY(-5px);
    }

    .service-btn {
      display: flex;
      align-items: center;
      justify-content: center;
      text-decoration: none;
      color: var(--light);
      font-weight: 600;
      background: rgba(0, 0, 0, 0.8);
      padding: 1.5rem 1rem;
      border-radius: 10px;
      text-align: center;
      height: 100%;
      transition: all var(--transition);
      box-shadow: var(--shadow-md);
      border-left: 3px solid transparent;
      position: relative;
      overflow: hidden;
      z-index: 1;
      text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
    }

    .service-btn::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 0%;
      height: 100%;
      background: linear-gradient(135deg, rgba(0, 150, 255, 0.9), rgba(255, 51, 204, 0.9));
      transition: width var(--transition);
      z-index: -1;
      opacity: 0.9;
    }

    .service-btn:hover {
      color: white;
      border-left: 3px solid var(--accent);
      box-shadow: var(--shadow-md);
    }

    .service-btn:hover::before {
      width: 100%;
    }

    /* Back Button */
    .back-btn {
      display: inline-flex;
      align-items: center;
      margin-top: 2rem;
      padding: 0.75rem 1.5rem;
      background: black;
      color: var(--light);
      text-decoration: none;
      border-radius: 30px;
      font-weight: 500;
      transition: all var(--transition);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }

    .back-btn i {
      margin-right: 0.5rem;
    }

    .back-btn:hover {
      background: rgba(31, 25, 25, 0.2);
      transform: translateX(-5px);
    }

    /* Design Services Description */
    .design-intro {
      background: rgba(0, 0, 0, 0.85);
      padding: 2rem;
      border-radius: 1rem;
      margin-bottom: 2rem;
      box-shadow: var(--shadow-lg);
      border-left: 4px solid var(--primary);
      max-width: 800px;
      margin-left: auto;
      margin-right: auto;
      position: relative;
      z-index: 10;
    }

    footer {
      background: linear-gradient(180deg, rgba(0, 0, 0, 0.8), rgba(0, 0, 0, 0.95));
      color: var(--text-light);
      padding: 3rem 1rem;
      margin-top: auto;
      position: relative;
      z-index: 2;
    }

    .footer-content {
      max-width: 1200px;
      margin: 0 auto;
      text-align: center;
    }

    .social-icons {
      display: flex;
      justify-content: center;
      gap: 1.5rem;
      margin-top: 1.5rem;
    }

    .social-icons a {
      color: var(--text-light);
      font-size: 1.5rem;
      transition: transform var(--transition), color var(--transition);
      width: 3rem;
      height: 3rem;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      background: rgba(255, 255, 255, 0.1);
    }

    .social-icons a:hover {
      color: var(--accent);
      transform: translateY(-3px);
      background: rgba(255, 255, 255, 0.2);
    }

    @media (max-width: 768px) {
      .services-grid {
        grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      }
    }

    @media (max-width: 480px) {
      .container {
        padding: 1.5rem;
      }
      
      .services-grid {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>

<body data-page="design-services">
  <!-- Only Logo (Replaces Header) -->
  <div class="logo-container">
    <img src="/images/Ramirez logo.png" alt="Ramirez Ventures Logo" class="logo">
  </div>

  <!-- Fullscreen Background Carousel -->
  <div class="background-carousel" id="backgroundCarousel">
    <img src="/images/MOVIE WALLPAPER.jpg" alt="Design Background 1" class="active">
    <img src="/images/Ramirez logo.png" alt="Design Background 2">
    <img src="/images/web wallpaper.jpg" alt="Design Background 3">
  </div>

  <!-- Overlay for readability -->
  <div class="overlay"></div>

  <!-- Main Content Wrapper -->
  <div class="content" id="content">
    <!-- Hero Title Section -->
    <section class="hero-title">
      <h2>DESIGN SERVICES</h2>
      <p>
        Elevating brands through innovative, cutting-edge design solutions tailored to your vision and business goals.
      </p>
    </section>

    <!-- Main Page Content -->
    <main>
      <div class="container">
        <div class="design-intro">
          <p>At Ramirez Ventures, we understand that exceptional design is the cornerstone of effective branding and marketing. Our team of talented designers combines creativity with strategic thinking to deliver designs that not only look stunning but also drive results for your business.</p>
        </div>
        
        <ol class="services-grid">
          <li class="service-item">
            <a href="/logo-design" class="service-btn">Logo Design</a>
          </li>
          <li class="service-item">
            <a href="/flyer-design" class="service-btn">Flyer Design</a>
          </li>
          <li class="service-item">
            <a href="/web-design" class="service-btn">Web Design</a>
          </li>
          <li class="service-item">
            <a href="/package-design" class="service-btn">Package Design</a>
          </li>
          <li class="service-item">
            <a href="/product-design" class="service-btn">Product Design</a>
          </li>
          <li class="service-item">
            <a href="/product-label-design" class="service-btn">Product Label Design</a>
          </li>
          <li class="service-item">
            <a href="/business-card-design" class="service-btn">Business Card Design</a>
          </li>
          <li class="service-item">
            <a href="/banners-design" class="service-btn">Banners Design</a>
          </li>
          <li class="service-item">
            <a href="/3d-signage" class="service-btn">3D Signage</a>
          </li>
          <li class="service-item">
            <a href="/letterhead-design" class="service-btn">Letterhead Design</a>
          </li>
          <li class="service-item">
            <a href="/brochure-design" class="service-btn">Brochure Design</a>
          </li>
        </ol>
        
        <a href="/" class="back-btn"><i class="fas fa-arrow-left"></i> Back to Home</a>
      </div>
    </main>

    <!-- Footer -->
    <footer>
      <div class="footer-content">
        <p>&copy; 2025 Ramirez Ventures. All rights reserved.</p>
        <div class="social-icons">
          <a href="#" aria-label="LinkedIn"><i class="fab fa-linkedin-in"></i></a>
          <a href="#" aria-label="Twitter"><i class="fab fa-twitter"></i></a>
          <a href="#" aria-label="GitHub"><i class="fab fa-github"></i></a>
        </div>
      </div>
    </footer>
  </div>

  <script>
    // Background Carousel functionality
    const slides = document.querySelectorAll('.background-carousel img');
    let currentSlide = 0;

    function showNextSlide() {
      slides[currentSlide].classList.remove('active');
      currentSlide = (currentSlide + 1) % slides.length;
      slides[currentSlide].classList.add('active');
    }

    setInterval(showNextSlide, 5000); // Change every 5 seconds
  </script>
</body>
</html># website

# starguide.travel
Code for starguide.travel astrology website
[app.js](https://github.com/user-attachments/files/26605117/app.js)
/**
 * AstroCartography Application
 * Calculates and displays planetary lines based on birth data
 */
[styles.css](https://github.com/user-attachments/files/26605125/styles.css)/* ============================================
   ASTROCARTOGRAPHY - COSMIC THEME
   Dark mystical aesthetic with gold accents
   ============================================ */

/* CSS Variables */
:root {
    /* Primary Colors */
    --color-deep-purple: #1a0a2e;
    --color-midnight: #0d0221;
    --color-cosmic-blue: #16213e;
    --color-indigo: #2d1b4e;
    
    /* Gold Accents */
    --color-gold: #f4d03f;
    --color-gold-light: #f9e79f;
    --color-gold-dark: #b7950b;
    --color-sun-gold: #ffd700;
    
    /* Planetary Colors */
    --color-sun: #ff9500;
    --color-moon: #c0c0c0;
    --color-venus: #e91e63;
    --color-mars: #ff5252;
    --color-jupiter: #9c27b0;
    --color-saturn: #795548;
    
    /* Gradient Backgrounds */
    --gradient-primary: linear-gradient(135deg, var(--color-midnight) 0%, var(--color-deep-purple) 50%, var(--color-cosmic-blue) 100%);
    --gradient-gold: linear-gradient(135deg, var(--color-gold) 0%, var(--color-sun-gold) 50%, var(--color-gold-light) 100%);
    --gradient-glass: linear-gradient(135deg, rgba(255,255,255,0.1) 0%, rgba(255,255,255,0.05) 100%);
    
    /* Typography */
    --font-heading: 'Cinzel', serif;
    --font-body: 'Playfair Display', serif;
    
    /* Spacing */
    --space-xs: 0.5rem;
    --space-sm: 1rem;
    --space-md: 2rem;
    --space-lg: 4rem;
    --space-xl: 6rem;
    
    /* Transitions */
    --transition-fast: 0.2s ease;
    --transition-medium: 0.4s ease;
    --transition-slow: 0.6s ease;
    
    /* Shadows */
    --shadow-glow: 0 0 20px rgba(244, 208, 63, 0.3);
    --shadow-card: 0 8px 32px rgba(0, 0, 0, 0.3);
}

/* Reset & Base Styles */
*, *::before, *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
}

body {
    font-family: var(--font-body);
    background: var(--gradient-primary);
    color: #ffffff;
    line-height: 1.6;
    overflow-x: hidden;
    min-height: 100vh;
}

/* Starfield Canvas Background */
#starfield {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    pointer-events: none;
}

/* Container */
.container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 var(--space-sm);
}

/* ============================================
   NAVIGATION
   ============================================ */
.header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 100;
    background: rgba(13, 2, 33, 0.9);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid rgba(244, 208, 63, 0.2);
}

.nav {
    max-width: 1280px;
    margin: 0 auto;
    padding: var(--space-sm);
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    display: flex;
    align-items: center;
    gap: var(--space-xs);
    font-family: var(--font-heading);
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--color-gold);
    text-decoration: none;
}

.logo i {
    animation: twinkle 2s ease-in-out infinite;
}

@keyframes twinkle {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.6; transform: scale(1.1); }
}

.nav-links {
    display: flex;
    list-style: none;
    gap: var(--space-md);
}

.nav-links a {
    color: rgba(255, 255, 255, 0.8);
    text-decoration: none;
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.5rem 1rem;
    border-radius: 8px;
    transition: all var(--transition-fast);
    font-size: 0.95rem;
}

.nav-links a:hover {
    color: var(--color-gold);
    background: rgba(244, 208, 63, 0.1);
}

/* ============================================
   HERO SECTION
   ============================================ */
.hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    padding: var(--space-lg) var(--space-sm);
    background: 
        radial-gradient(ellipse at 20% 80%, rgba(156, 39, 176, 0.3) 0%, transparent 50%),
        radial-gradient(ellipse at 80% 20%, rgba(244, 208, 63, 0.2) 0%, transparent 50%);
}

.hero-content {
    text-align: center;
    max-width: 800px;
    z-index: 2;
}

.hero-icon {
    font-size: 4rem;
    color: var(--color-gold);
    margin-bottom: var(--space-sm);
    animation: float 3s ease-in-out infinite;
}

@keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-15px); }
}

.hero-title {
    font-family: var(--font-heading);
    font-size: clamp(2rem, 6vw, 4rem);
    font-weight: 700;
    line-height: 1.2;
    margin-bottom: var(--space-sm);
}

.title-accent {
    display: block;
    background: var(--gradient-gold);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.hero-subtitle {
    font-size: 1.25rem;
    color: rgba(255, 255, 255, 0.8);
    margin-bottom: var(--space-md);
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
}

.hero-cta {
    display: inline-flex;
    align-items: center;
    gap: 0.75rem;
    padding: 1rem 2.5rem;
    background: var(--gradient-gold);
    color: var(--color-midnight);
    text-decoration: none;
    border-radius: 50px;
    font-family: var(--font-heading);
    font-weight: 600;
    font-size: 1.1rem;
    transition: all var(--transition-medium);
    box-shadow: var(--shadow-glow);
}

.hero-cta:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 30px rgba(244, 208, 63, 0.5);
}

.zodiac-wheel {
    position: absolute;
    right: 10%;
    top: 50%;
    transform: translateY(-50%);
    font-size: 200px;
    color: rgba(244, 208, 63, 0.05);
    animation: rotate-slow 60s linear infinite;
}

@keyframes rotate-slow {
    from { transform: translateY(-50%) rotate(0deg); }
    to { transform: translateY(-50%) rotate(360deg); }
}

/* ============================================
   SECTION HEADER
   ============================================ */
.section-header {
    text-align: center;
    margin-bottom: var(--space-md);
}

.section-header i {
    font-size: 2.5rem;
    color: var(--color-gold);
    margin-bottom: var(--space-xs);
}

.section-header h2 {
    font-family: var(--font-heading);
    font-size: 2.5rem;
    margin-bottom: var(--space-xs);
    background: var(--gradient-gold);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.section-header p {
    color: rgba(255, 255, 255, 0.7);
    font-size: 1.1rem;
}

/* ============================================
   INPUT SECTION
   ============================================ */
.input-section {
    padding: var(--space-xl) var(--space-sm);
    position: relative;
}

.form-card {
    max-width: 600px;
    margin: 0 auto var(--space-md);
    border-radius: 24px;
    padding: var(--space-md);
}

.birth-form {
    display: flex;
    flex-direction: column;
    gap: var(--space-sm);
}

.form-group {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

.form-group label {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-weight: 500;
    color: rgba(255, 255, 255, 0.9);
}

.form-group label i {
    color: var(--color-gold);
    width: 20px;
}

.form-group input {
    padding: 1rem 1.25rem;
    border: 2px solid rgba(244, 208, 63, 0.2);
    border-radius: 12px;
    background: rgba(0, 0, 0, 0.3);
    color: #fff;
    font-family: var(--font-body);
    font-size: 1rem;
    transition: all var(--transition-fast);
}

.form-group input:focus {
    outline: none;
    border-color: var(--color-gold);
    box-shadow: 0 0 15px rgba(244, 208, 63, 0.2);
}

.form-group input::placeholder {
    color: rgba(255, 255, 255, 0.4);
}

.submit-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.75rem;
    padding: 1.25rem;
    background: var(--gradient-gold);
    color: var(--color-midnight);
    border: none;
    border-radius: 12px;
    font-family: var(--font-heading);
    font-size: 1.1rem;
    font-weight: 700;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    transition: all var(--transition-fast);
    margin-top: var(--space-xs);
}

.submit-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(244, 208, 63, 0.4);
}

.btn-shine {
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
    animation: shine 3s infinite;
}

@keyframes shine {
    0% { left: -100%; }
    50% { left: 100%; }
    100% { left: 100%; }
}

/* Legend Card */
.legend-card {
    max-width: 900px;
    margin: 0 auto;
    border-radius: 24px;
    padding: var(--space-md);
}

.legend-card h3 {
    font-family: var(--font-heading);
    text-align: center;
    margin-bottom: var(--space-sm);
    color: var(--color-gold);
}

.legend-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: var(--space-sm);
}

.legend-item {
    display: flex;
    align-items: center;
    gap: var(--space-sm);
    padding: var(--space-sm);
    background: rgba(255, 255, 255, 0.05);
    border-radius: 12px;
    transition: all var(--transition-fast);
}

.legend-item:hover {
    background: rgba(255, 255, 255, 0.1);
    transform: translateX(5px);
}

.legend-dot {
    width: 16px;
    height: 16px;
    border-radius: 50%;
    flex-shrink: 0;
    box-shadow: 0 0 10px currentColor;
}

.legend-item.sun .legend-dot { background: var(--color-sun); color: var(--color-sun); }
.legend-item.moon .legend-dot { background: var(--color-moon); color: var(--color-moon); }
.legend-item.venus .legend-dot { background: var(--color-venus); color: var(--color-venus); }
.legend-item.mars .legend-dot { background: var(--color-mars); color: var(--color-mars); }
.legend-item.jupiter .legend-dot { background: var(--color-jupiter); color: var(--color-jupiter); }
.legend-item.saturn .legend-dot { background: var(--color-saturn); color: var(--color-saturn); }

.legend-item strong {
    display: block;
    color: #fff;
    font-size: 1.1rem;
}

.legend-item span {
    color: rgba(255, 255, 255, 0.6);
    font-size: 0.9rem;
}

/* ============================================
   MAP SECTION
   ============================================ */
.map-section {
    padding: var(--space-xl) var(--space-sm);
    background: rgba(0, 0, 0, 0.2);
}

.results-container {
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: var(--space-md);
    max-width: 1400px;
    margin: 0 auto;
}

.map-wrapper {
    position: relative;
    border-radius: 20px;
    overflow: hidden;
    box-shadow: var(--shadow-card);
}

.map-container {
    height: 600px;
    width: 100%;
    background: #1a1a2e;
    border-radius: 20px;
}

.map-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background: rgba(13, 2, 33, 0.9);
    backdrop-filter: blur(5px);
    opacity: 0;
    visibility: hidden;
    transition: all var(--transition-medium);
}

.map-overlay.active {
    opacity: 1;
    visibility: visible;
}

.loading-spinner {
    width: 60px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: var(--space-sm);
}

.loading-spinner i {
    font-size: 3rem;
    color: var(--color-gold);
    animation: spin 1s linear infinite;
}

@keyframes spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
}

.map-overlay p {
    color: rgba(255, 255, 255, 0.8);
    font-size: 1.2rem;
}

/* Interpretation Panel */
.interpretation-panel {
    border-radius: 20px;
    padding: var(--space-md);
    max-height: 600px;
    overflow-y: auto;
}

.interpretation-panel::-webkit-scrollbar {
    width: 8px;
}

.interpretation-panel::-webkit-scrollbar-track {
    background: rgba(0, 0, 0, 0.2);
    border-radius: 4px;
}

.interpretation-panel::-webkit-scrollbar-thumb {
    background: rgba(244, 208, 63, 0.5);
    border-radius: 4px;
}

.panel-header {
    display: flex;
    align-items: center;
    gap: var(--space-xs);
    padding-bottom: var(--space-sm);
    border-bottom: 1px solid rgba(244, 208, 63, 0.2);
    margin-bottom: var(--space-sm);
}

.panel-header i {
    font-size: 1.5rem;
    color: var(--color-gold);
}

.panel-header h3 {
    font-family: var(--font-heading);
    font-size: 1.3rem;
    color: var(--color-gold);
}

.empty-state {
    text-align: center;
    padding: var(--space-md);
    color: rgba(255, 255, 255, 0.5);
}

.empty-state i {
    font-size: 3rem;
    margin-bottom: var(--space-sm);
    color: var(--color-gold);
    opacity: 0.5;
}

/* Interpretation Cards */
.interpretation-card {
    background: rgba(255, 255, 255, 0.05);
    border-radius: 12px;
    padding: var(--space-sm);
    margin-bottom: var(--space-sm);
    border-left: 3px solid;
    transition: all var(--transition-fast);
}

.interpretation-card:hover {
    background: rgba(255, 255, 255, 0.1);
    transform: translateX(5px);
}

.interpretation-card.sun { border-color: var(--color-sun); }
.interpretation-card.moon { border-color: var(--color-moon); }
.interpretation-card.venus { border-color: var(--color-venus); }
.interpretation-card.mars { border-color: var(--color-mars); }
.interpretation-card.jupiter { border-color: var(--color-jupiter); }
.interpretation-card.saturn { border-color: var(--color-saturn); }
.interpretation-card.crossing { border-color: var(--color-gold); }

.card-header {
    display: flex;
    align-items: center;
    gap: var(--space-xs);
    margin-bottom: 0.5rem;
}

.card-header i {
    font-size: 1.2rem;
}

.interpretation-card.sun .card-header i { color: var(--color-sun); }
.interpretation-card.moon .card-header i { color: var(--color-moon); }
.interpretation-card.venus .card-header i { color: var(--color-venus); }
.interpretation-card.mars .card-header i { color: var(--color-mars); }
.interpretation-card.jupiter .card-header i { color: var(--color-jupiter); }
.interpretation-card.saturn .card-header i { color: var(--color-saturn); }
.interpretation-card.crossing .card-header i { color: var(--color-gold); }

.card-header h4 {
    font-family: var(--font-heading);
    font-size: 1.1rem;
}

.interpretation-card p {
    font-size: 0.95rem;
    line-height: 1.7;
    color: rgba(255, 255, 255, 0.8);
}

.location-tag {
    display: inline-block;
    margin-top: 0.5rem;
    padding: 0.3rem 0.8rem;
    background: rgba(244, 208, 63, 0.2);
    border-radius: 20px;
    font-size: 0.85rem;
    color: var(--color-gold);
}

/* ============================================
   ABOUT SECTION
   ============================================ */
.about-section {
    padding: var(--space-xl) var(--space-sm);
}

.about-content {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: var(--space-md);
    max-width: 1200px;
    margin: 0 auto;
}

.about-card {
    padding: var(--space-md);
    border-radius: 20px;
    text-align: center;
    transition: all var(--transition-medium);
}

.about-card:hover {
    transform: translateY(-10px);
    box-shadow: var(--shadow-glow);
}

.about-card i {
    font-size: 3rem;
    margin-bottom: var(--space-sm);
}

.about-card:nth-child(1) i { color: var(--color-sun); }
.about-card:nth-child(2) i { color: var(--color-moon); }
.about-card:nth-child(3) i { color: var(--color-venus); }
.about-card:nth-child(4) i { color: var(--color-mars); }

.about-card h3 {
    font-family: var(--font-heading);
    font-size: 1.4rem;
    margin-bottom: var(--space-xs);
    color: var(--color-gold);
}

.about-card p {
    color: rgba(255, 255, 255, 0.7);
    line-height: 1.7;
}

/* ============================================
   FOOTER
   ============================================ */
.footer {
    padding: var(--space-md) var(--space-sm);
    background: rgba(0, 0, 0, 0.4);
    border-top: 1px solid rgba(244, 208, 63, 0.1);
}

.footer-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: var(--space-sm);
    margin-bottom: var(--space-sm);
}

.footer-brand {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-family: var(--font-heading);
    font-size: 1.5rem;
    color: var(--color-gold);
}

.footer-brand p {
    font-family: var(--font-body);
    font-size: 0.9rem;
    color: rgba(255, 255, 255, 0.5);
    margin: 0;
    margin-left: var(--space-sm);
}

.footer-links {
    display: flex;
    gap: var(--space-md);
}

.footer-links a {
    color: rgba(255, 255, 255, 0.7);
    text-decoration: none;
    display: flex;
    align-items: center;
    gap: 0.5rem;
    transition: color var(--transition-fast);
}

.footer-links a:hover {
    color: var(--color-gold);
}

.footer-bottom {
    text-align: center;
    padding-top: var(--space-sm);
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    color: rgba(255, 255, 255, 0.5);
    font-size: 0.9rem;
}

/* ============================================
   UTILITY CLASSES
   ============================================ */
.glass {
    background: var(--gradient-glass);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.1);
}

/* Leaflet Custom Styles */
.leaflet-container {
    font-family: var(--font-body);
    background: #0d0221;
}

.leaflet-popup-content-wrapper {
    background: rgba(26, 10, 46, 0.95);
    border-radius: 12px;
    color: #fff;
    border: 1px solid rgba(244, 208, 63, 0.3);
}

.leaflet-popup-tip {
    background: rgba(26, 10, 46, 0.95);
}

/* ============================================
   RESPONSIVE DESIGN
   ============================================ */
@media (max-width: 1024px) {
    .results-container {
        grid-template-columns: 1fr;
    }
    
    .interpretation-panel {
        max-height: 400px;
    }
}

@media (max-width: 768px) {
    .nav-links {
        gap: 0.5rem;
    }
    
    .nav-links a {
        padding: 0.4rem 0.8rem;
        font-size: 0.9rem;
    }
    
    .nav-links a span {
        display: none;
    }
    
    .hero-title {
        font-size: 2rem;
    }
    
    .section-header h2 {
        font-size: 1.8rem;
    }
    
    .zodiac-wheel {
        display: none;
    }
    
    .legend-grid {
        grid-template-columns: 1fr;
    }
    
    .about-content {
        grid-template-columns: 1fr;
    }
    
    .footer-content {
        flex-direction: column;
        text-align: center;
    }
    
    .footer-brand {
        flex-direction: column;
    }
    
    .footer-brand p {
        margin: 0;
    }
}

@media (max-width: 480px) {
    .hero-cta {
        padding: 0.875rem 1.5rem;
        font-size: 1rem;
    }
    
    .submit-btn {
        padding: 1rem;
        font-size: 1rem;
    }
    
    .form-card,
    .legend-card {
        padding: var(--space-sm);
    }
    
    .interpretation-panel {
        padding: var(--space-sm);
    }
}


// ============================================
// STARFIELD ANIMATION
// ============================================[index.html](https://github.com/user-attachments/files/26605121/index.html)<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AstroCartography - Your Cosmic Map</title>
    
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700&family=Playfair+Display:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
    
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Leaflet CSS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    
    <!-- Custom CSS -->
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Star Background Canvas -->
    <canvas id="starfield"></canvas>
    
    <!-- Header Navigation -->
    <header class="header">
        <nav class="nav">
            <div class="logo">
                <i class="fas fa-star"></i>
                <span>AstroCarto</span>
            </div>
            <ul class="nav-links">
                <li><a href="#chart"><i class="fas fa-moon"></i> Chart</a></li>
                <li><a href="#map"><i class="fas fa-globe-americas"></i> Map</a></li>
                <li><a href="#about"><i class="fas fa-star"></i> About</a></li>
            </ul>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <div class="hero-icon">
                <i class="fas fa-globe"></i>
            </div>
            <h1 class="hero-title">Discover Your<span class="title-accent">Cosmic Geography</span></h1>
            <p class="hero-subtitle">
                Uncover where the planets align to unlock your full potential.<br>
                Your destiny is written in the stars—and mapped on Earth.
            </p>
            <a href="#chart" class="hero-cta">
                <i class="fas fa-compass"></i>
                Begin Your Journey
            </a>
        </div>
        <div class="zodiac-wheel" aria-hidden="true">
            <i class="fas fa-sun"></i>
        </div>
    </section>

    <!-- Input Section -->
    <section id="chart" class="input-section">
        <div class="container">
            <div class="section-header">
                <i class="fas fa-calendar-alt"></i>
                <h2>Enter Your Birth Details</h2>
                <p>Provide accurate information for precise astrocartography calculations</p>
            </div>
            
            <div class="form-card glass">
                <form id="birthForm" class="birth-form">
                    <!-- Name Input -->
                    <div class="form-group">
                        <label for="name">
                            <i class="fas fa-user"></i>
                            Your Name
                        </label>
                        <input type="text" id="name" name="name" placeholder="Enter your name" required>
                    </div>
                    
                    <!-- Date Input -->
                    <div class="form-group">
                        <label for="birthDate">
                            <i class="fas fa-calendar"></i>
                            Birth Date
                        </label>
                        <input type="date" id="birthDate" name="birthDate" required>
                    </div>
                    
                    <!-- Time Input -->
                    <div class="form-group">
                        <label for="birthTime">
                            <i class="fas fa-clock"></i>
                            Birth Time
                        </label>
                        <input type="time" id="birthTime" name="birthTime" required>
                    </div>
                    
                    <!-- Birth Location -->
                    <div class="form-group">
                        <label for="birthLocation">
                            <i class="fas fa-map-marker-alt"></i>
                            Birth City
                        </label>
                        <input type="text" id="birthLocation" name="birthLocation" 
                               placeholder="e.g., New York, USA" required>
                    </div>
                    
                    <!-- Submit Button -->
                    <button type="submit" class="submit-btn">
                        <i class="fas fa-magic"></i>
                        Generate Your Cosmic Map
                        <div class="btn-shine"></div>
                    </button>
                </form>
            </div>
            
            <!-- Planetary Legend -->
            <div class="legend-card glass">
                <h3><i class="fas fa-key"></i> Planetary Line Meanings</h3>
                <div class="legend-grid">
                    <div class="legend-item sun">
                        <span class="legend-dot"></span>
                        <div>
                            <strong>Sun</strong>
                            <span>Self-expression & vitality</span>
                        </div>
                    </div>
                    <div class="legend-item moon">
                        <span class="legend-dot"></span>
                        <div>
                            <strong>Moon</strong>
                            <span>Home & emotional security</span>
                        </div>
                    </div>
                    <div class="legend-item venus">
                        <span class="legend-dot"></span>
                        <div>
                            <strong>Venus</strong>
                            <span>Love & relationships</span>
                        </div>
                    </div>
                    <div class="legend-item mars">
                        <span class="legend-dot"></span>
                        <div>
                            <strong>Mars</strong>
                            <span>Ambition & drive</span>
                        </div>
                    </div>
                    <div class="legend-item jupiter">
                        <span class="legend-dot"></span>
                        <div>
                            <strong>Jupiter</strong>
                            <span>Expansion & fortune</span>
                        </div>
                    </div>
                    <div class="legend-item saturn">
                        <span class="legend-dot"></span>
                        <div>
                            <strong>Saturn</strong>
                            <span>Lifelong challenges</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Map Results Section -->
    <section id="map" class="map-section">
        <div class="container">
            <div class="section-header">
                <i class="fas fa-globe-americas"></i>
                <h2>Your Astrocartography Map</h2>
                <p>Explore where planetary lines intersect your world</p>
            </div>
            
            <div class="results-container">
                <div class="map-wrapper">
                    <div id="aMap" class="map-container"></div>
                    <div class="map-overlay loading" id="mapLoading">
                        <div class="loading-spinner">
                            <i class="fas fa-star"></i>
                        </div>
                        <p>Calculating cosmic alignments...</p>
                    </div>
                </div>
                
                <div class="interpretation-panel glass" id="interpretationPanel">
                    <div class="panel-header">
                        <i class="fas fa-scroll"></i>
                        <h3>Celestial Interpretations</h3>
                    </div>
                    <div class="panel-content" id="panelContent">
                        <div class="empty-state">
                            <i class="fas fa-star"></i>
                            <p>Complete the form above to receive your personalized astrocartography reading.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="about-section">
        <div class="container">
            <div class="section-header">
                <i class="fas fa-info-circle"></i>
                <h2>About Astrocartography</h2>
            </div>
            <div class="about-content">
                <div class="about-card glass">
                    <i class="fas fa-sun"></i>
                    <h3>Your Sun Line</h3>
                    <p>Where your authentic self shines brightest. These locations amplify confidence and leadership.</p>
                </div>
                <div class="about-card glass">
                    <i class="fas fa-moon"></i>
                    <h3>Lunar Comfort</h3>
                    <p>Your Moon line brings emotional fulfillment and a sense of belonging and home.</p>
                </div>
                <div class="about-card glass">
                    <i class="fas fa-heart"></i>
                    <h3>Venus' Blessing</h3>
                    <p>Find love, beauty, and harmony where Venus lines grace your map—perfect for romance.</p>
                </div>
                <div class="about-card glass">
                    <i class="fas fa-fire"></i>
                    <h3>Mars Energy</h3>
                    <p>Mars locations ignite passion and drive but can also bring conflict—channel wisely.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <div class="footer-content">
                <div class="footer-brand">
                    <i class="fas fa-star"></i>
                    <span>AstroCarto</span>
                    <p>Mapping your destiny among the stars</p>
                </div>
                <div class="footer-links">
                    <a href="#"><i class="fas fa-question-circle"></i> FAQ</a>
                    <a href="#"><i class="fas fa-shield-alt"></i> Privacy</a>
                    <a href="#"><i class="fas fa-envelope"></i> Contact</a>
                </div>
            </div>
            <div class="footer-bottom">
                <p>© 2024 AstroCartography. The stars guide us all.</p>
            </div>
        </div>
    </footer>

    <!-- Leaflet JS -->
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
    
    <!-- Custom JS -->
    <script src="app.js"></script>
</body>
</html>


const initStarfield = () => {
    const canvas = document.getElementById('starfield');
    if (!canvas) return;
    
    const ctx = canvas.getContext('2d');
    let stars = [];
    let width, height;

    const resize = () => {
        width = canvas.width = window.innerWidth;
        height = canvas.height = window.innerHeight;
    };

    class Star {
        constructor() {
            this.reset();
        }

        reset() {
            this.x = Math.random() * width;
            this.y = Math.random() * height;
            this.size = Math.random() * 2 + 0.5;
            this.speedX = (Math.random() - 0.5) * 0.3;
            this.speedY = (Math.random() - 0.5) * 0.3;
            this.brightness = Math.random();
            this.twinkleSpeed = Math.random() * 0.02 + 0.005;
        }

        update() {
            this.x += this.speedX;
            this.y += this.speedY;
            this.brightness += this.twinkleSpeed;
            
            if (this.brightness > 1 || this.brightness < 0.3) {
                this.twinkleSpeed = -this.twinkleSpeed;
            }

            if (this.x < 0 || this.x > width || this.y < 0 || this.y > height) {
                this.reset();
            }
        }

        draw() {
            ctx.beginPath();
            ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
            ctx.fillStyle = `rgba(255, 255, 255, ${this.brightness})`;
            ctx.fill();

            // Star glow
            ctx.shadowBlur = this.size * 2;
            ctx.shadowColor = 'rgba(255, 255, 255, 0.5)';
            ctx.fill();
            ctx.shadowBlur = 0;
        }
    }

    const initStars = () => {
        stars = [];
        for (let i = 0; i < 150; i++) {
            stars.push(new Star());
        }
    };

    const animate = () => {
        ctx.clearRect(0, 0, width, height);
        stars.forEach(star => {
            star.update();
            star.draw();
        });
        requestAnimationFrame(animate);
    };

    resize();
    initStars();
    animate();

    window.addEventListener('resize', () => {
        resize();
        initStars();
    });
};

// ============================================
// PLANETARY DATA & MEANINGS
// ============================================
const PLANETARY_DATA = {
    sun: {
        name: 'Sun',
        color: '#ff9500',
        icon: 'fa-sun',
        meaning: 'Self-expression, confidence, vitality, and authentic identity',
        influence: 'Your authentic self shines brightest here. These locations amplify confidence, leadership abilities, and personal expression. Perfect for career advancement and public recognition.',
        locations: ['Paris, France', 'Rome, Italy', 'New York, USA', 'Tokyo, Japan']
    },
    moon: {
        name: 'Moon',
        color: '#c0c0c0',
        icon: 'fa-moon',
        meaning: 'Home, emotional security, intuition, and nurturing',
        influence: 'Your Moon line brings emotional fulfillment and a deep sense of belonging. These locations nurture your soul and provide comfort. Ideal for settling down and family life.',
        locations: ['Lisbon, Portugal', 'San Francisco, USA', 'Sydney, Australia', 'Amsterdam, Netherlands']
    },
    venus: {
        name: 'Venus',
        color: '#e91e63',
        icon: 'fa-heart',
        meaning: 'Love, beauty, pleasure, harmony, and relationships',
        influence: 'Venus lines bring love, beauty, and artistic inspiration. These locations enhance romantic opportunities and creative expression. Perfect for relationships and artistic pursuits.',
        locations: ['Venice, Italy', 'Rio de Janeiro, Brazil', 'Barcelona, Spain', 'Vienna, Austria']
    },
    mars: {
        name: 'Mars',
        color: '#ff5252',
        icon: 'fa-fire',
        meaning: 'Ambition, drive, passion, energy, and assertiveness',
        influence: 'Mars locations ignite passion and competitive drive. These energies can fuel great achievements but may also bring conflict. Use wisely for sports, business competition, and bold initiatives.',
        locations: ['Berlin, Germany', 'Dubai, UAE', 'Moscow, Russia', 'Chicago, USA']
    },
    jupiter: {
        name: 'Jupiter',
        color: '#9c27b0',
        icon: 'fa-star',
        meaning: 'Expansion, luck, growth, prosperity, and wisdom',
        influence: 'Jupiter brings abundance and good fortune. These locations expand your horizons and attract opportunities. Excellent for education, travel, business growth, and finding mentors.',
        locations: ['London, UK', 'Singapore', 'Vancouver, Canada', 'Melbourne, Australia']
    },
    saturn: {
        name: 'Saturn',
        color: '#795548',
        icon: 'fa-mountain',
        meaning: 'Lifelong challenges, discipline, responsibility, and maturity',
        influence: 'Saturn lines bring serious lessons and tests of endurance. While challenging, these locations teach invaluable life lessons. Good for serious study, long-term planning, and building lasting structures.',
        locations: ['Stockholm, Sweden', 'Seoul, South Korea', 'Toronto, Canada', 'Zurich, Switzerland']
    }
};

// ============================================
// GEOLOCATION DATA (Mock major cities)
// ============================================
const CITY_COORDINATES = {
    'new york': [40.7128, -74.0060],
    'london': [51.5074, -0.1278],
    'paris': [48.8566, 2.3522],
    'tokyo': [35.6762, 139.6503],
    'berlin': [52.5200, 13.4050],
    'rome': [41.9028, 12.4964],
    'sydney': [-33.8688, 151.2093],
    'barcelona': [41.3851, 2.1734],
    'dubai': [25.2048, 55.2708],
    'singapore': [1.3521, 103.8198],
    'los angeles': [34.0522, -118.2437],
    'san francisco': [37.7749, -122.4194],
    'chicago': [41.8781, -87.6298],
    'miami': [25.7617, -80.1918],
    'boston': [42.3601, -71.0589],
    'seattle': [47.6062, -122.3321],
    'vancouver': [49.2827, -123.1207],
    'toronto': [43.6532, -79.3832],
    'mexico city': [19.4326, -99.1332],
    'rio de janeiro': [-22.9068, -43.1729],
    'buenos aires': [-34.6037, -58.3816],
    'cairo': [30.0444, 31.2357],
    'cape town': [-33.9249, 18.4241],
    'moscow': [55.7558, 37.6173],
    'mumbai': [19.0760, 72.8777],
    'bangkok': [13.7563, 100.5018],
    'shanghai': [31.2304, 121.4737],
    'beijing': [39.9042, 116.4074],
    'seoul': [37.5665, 126.9780],
    'hong kong': [22.3193, 114.1694],
    'amsterdam': [52.3676, 4.9041],
    'vienna': [48.2082, 16.3738],
    'lisbon': [38.7223, -9.1393],
    'madrid': [40.4168, -3.7038],
    'zurich': [47.3769, 8.5417],
    'stockholm': [59.3293, 18.0686],
    'melbourne': [-37.8136, 144.9631],
    'venice': [45.4408, 12.3155]
};

// ============================================
// MAP FUNCTIONALITY
// ============================================
let map = null;
let planetLines = [];

const initializeMap = () => {
    if (map) return map;

    map = L.map('aMap', {
        center: [20, 0],
        zoom: 2,
        minZoom: 2,
        worldCopyJump: true,
        attributionControl: true
    });

    // Dark theme tiles
    L.tileLayer('https://{s}.basemaps.cartocdn.com/dark_all/{z}/{x}/{y}{r}.png', {
        attribution: '&copy; OpenStreetMap contributors &copy; CARTO',
        subdomains: 'abcd',
        maxZoom: 19
    }).addTo(map);

    return map;
};

// Hash string to number for deterministic calculations
const hashString = (str) => {
    let hash = 0;
    for (let i = 0; i < str.length; i++) {
        const char = str.charCodeAt(i);
        hash = ((hash << 5) - hash) + char;
        hash = hash & hash;
    }
    return Math.abs(hash);
};

// Generate planet lines based on birth data
const generatePlanetLines = (birthDate, birthTime, birthLocation) => {
    const planets = ['sun', 'moon', 'venus', 'mars', 'jupiter', 'saturn'];
    const lines = [];
    const hash = hashString(birthDate + birthTime + birthLocation);
    
    // Find birth city coordinates or use default
    let birthLat = 40.7128, birthLng = -74.0060;
    const cityKey = Object.keys(CITY_COORDINATES).find(
        city => birthLocation.toLowerCase().includes(city)
    );
    if (cityKey) {
        [birthLat, birthLng] = CITY_COORDINATES[cityKey];
    }

    planets.forEach((planet, index) => {
        // Deterministic pseudo-random angles based on hash
        const baseAngle = (hash + index * 60) % 360;
        const variation = ((hash >> (index + 1)) % 30) - 15;
        const angle = baseAngle + variation;
        
        // Calculate line endpoints based on azimuth angle
        const radians = (angle * Math.PI) / 180;
        const distance = 150; // Roughly 15,000 km at this projection scale
        
        // Generate great circle approximation points
        const numPoints = 50;
        const points = [];
        
        for (let i = 0; i <= numPoints; i++) {
            const t = (i / numPoints) * 2 - 1; // -1 to 1
            const lat = birthLat + Math.sin(radians) * distance * t;
            const lng = birthLng + Math.cos(radians) * distance * t * 
                       Math.cos(birthLat * Math.PI / 180);
            
            points.push([lat, lng]);
        }
        
        lines.push({
            planet,
            points,
            angle,
            birthCoords: [birthLat, birthLng]
        });
    });

    return lines;
};

// Render lines on map
const renderPlanetLines = (lines) => {
    // Clear existing lines
    planetLines.forEach(line => map.removeLayer(line));
    planetLines = [];

    lines.forEach(lineData => {
        const planetInfo = PLANETARY_DATA[lineData.planet];
        
        // Create polyline with glow effect
        const mainLine = L.polyline(lineData.points, {
            color: planetInfo.color,
            weight: 3,
            opacity: 0.8,
            dashArray: '10, 5',
            lineCap: 'round'
        }).addTo(map);

        // Add glow effect
        const glowLine = L.polyline(lineData.points, {
            color: planetInfo.color,
            weight: 8,
            opacity: 0.2,
            lineCap: 'round'
        }).addTo(map);

        // Add hover popup
        mainLine.bindPopup(`
            <div style="text-align: center; padding: 10px;">
                <i class="fas ${planetInfo.icon}" style="color: ${planetInfo.color}; font-size: 24px;"></i>
                <h3 style="margin: 5px 0; color: ${planetInfo.color};">${planetInfo.name} Line</h3>
                <p style="margin: 0; font-size: 14px;">${planetInfo.meaning}</p>
            </div>
        `);

        planetLines.push(mainLine, glowLine);
    });

    // Add birth location marker
    if (lines.length > 0) {
        const birthCoords = lines[0].birthCoords;
        const birthMarker = L.circleMarker(birthCoords, {
            radius: 12,
            fillColor: '#f4d03f',
            color: '#fff',
            weight: 3,
            opacity: 1,
            fillOpacity: 1
        }).addTo(map);
        
        birthMarker.bindPopup('
            <div style="text-align: center;">
                <i class="fas fa-star" style="color: #f4d03f;"></i>
                <strong>Birth Location</strong>
            </div>
        ');
        
        planetLines.push(birthMarker);
    }
};

// Calculate line crossings and generate interpretations
const calculateCrossings = (lines, birthData) => {
    const interpretations = [];
    const planetsCrossed = new Set();
    
    // Generate interpretations for each planet line
    lines.forEach(line => {
        const planet = line.planet;
        const data = PLANETARY_DATA[planet];
        
        // Pick a relevant location from this planet's list
        const hash = hashString(birthData.name + planet);
        const locationIndex = hash % data.locations.length;
        const location = data.locations[locationIndex];
        
        interpretations.push({
            type: planet,
            title: `${data.name} Line`,
            description: data.influence,
            location: location,
            icon: data.icon,
            color: data.color
        });
        
        planetsCrossed.add(planet);
    });

    // Add special crossing interpretations
    if (planetsCrossed.has('venus') && planetsCrossed.has('jupiter')) {
        interpretations.push({
            type: 'crossing',
            title: 'Venus-Jupiter Crossing ✨',
            description: 'A rare celestial blessing! The combination of Venus (love and beauty) with Jupiter (expansion and luck) creates powerful energies for romance, creative success, and social harmony. This is an excellent location for weddings, artistic collaborations, and finding your soulmate.',
            location: interpretations.find(i => i.type === 'venus')?.location || 'Tropical paradise',
            icon: 'fa-gem',
            color: '#f4d03f'
        });
    }

    if (planetsCrossed.has('sun') && planetsCrossed.has('mars')) {
        interpretations.push({
            type: 'crossing',
            title: 'Sun-Mars Conjunction 🔥',
            description: 'Powerful energies combine here! The Sun (self-expression) meeting Mars (action and drive) creates a dynamic environment for leadership, athletic achievement, and courageous endeavors. You will feel unstoppable here, but watch for impulsive decisions.',
            location: interpretations.find(i => i.type === 'mars')?.location || 'Dynamic city',
            icon: 'fa-bolt',
            color: '#ff5252'
        });
    }

    if (planetsCrossed.has('moon') && planetsCrossed.has('saturn')) {
        interpretations.push({
            type: 'crossing',
            title: 'Moon-Saturn Challenge 🌑',
            description: 'Emotional maturity is required here. The Moon (feelings and security) in relationship with Saturn (discipline and limitation) teaches emotional resilience. While initially challenging, this location can help you develop deep emotional wisdom and lasting foundations.',
            location: interpretations.find(i => i.type === 'saturn')?.location || 'Historic place',
            icon: 'fa-balance-scale',
            color: '#795548'
        });
    }

    return interpretations;
};

// Render interpretations panel
const renderInterpretations = (interpretations, userName) => {
    const panel = document.getElementById('panelContent');
    
    const html = `
        <div class="interpretation-header" style="margin-bottom: 1rem;">
            <p style="color: rgba(255,255,255,0.8); font-style: italic;">
                Welcome, ${userName}! Based on your cosmic chart, here are your planetary alignments:
            </p>
        </div>
        ${interpretations.map(interp => `
            <div class="interpretation-card ${interp.type}">
                <div class="card-header">
                    <i class="fas ${interp.icon}" style="color: ${interp.color};"></i>
                    <h4>${interp.title}</h4>
                </div>
                <p>${interp.description}</p>
                <span class="location-tag">
                    <i class="fas fa-map-marker-alt" style="margin-right: 0.3rem;"></i>
                    ${interp.location}
                </span>
            </div>
        `).join('')}
    `;
    
    panel.innerHTML = html;
};

// Show loading state
const showLoading = () => {
    document.getElementById('mapLoading').classList.add('active');
};

const hideLoading = () => {
    document.getElementById('mapLoading').classList.remove('active');
};

// Main calculation function
const calculateAstrocartography = (formData) => {
    showLoading();
    
    return new Promise((resolve) => {
        setTimeout(() => {
            // Generate planet lines
            const lines = generatePlanetLines(
                formData.birthDate,
                formData.birthTime,
                formData.birthLocation
            );
            
            // Render on map
            renderPlanetLines(lines);
            
            // Calculate and show interpretations
            const interpretations = calculateCrossings(lines, formData);
            renderInterpretations(interpretations, formData.name);
            
            hideLoading();
            
            // Zoom to show all lines
            if (lines.length > 0) {
                const group = L.featureGroup(planetLines);
                map.fitBounds(group.getBounds().pad(0.2));
            }
            
            resolve({ lines, interpretations });
        }, 1500); // Simulate calculation time
    });
};

// ============================================
// FORM HANDLING
// ============================================
const initForm = () => {
    const form = document.getElementById('birthForm');
    if (!form) return;

    form.addEventListener('submit', async (e) => {
        e.preventDefault();
        
        const formData = {
            name: form.querySelector('#name').value,
            birthDate: form.querySelector('#birthDate').value,
            birthTime: form.querySelector('#birthTime').value,
            birthLocation: form.querySelector('#birthLocation').value
        };

        // Basic validation
        if (!formData.name || !formData.birthDate || !formData.birthTime || !formData.birthLocation) {
            alert('Please fill in all fields to generate your cosmic map.');
            return;
        }

        // Scroll to map section
        document.getElementById('map').scrollIntoView({ behavior: 'smooth' });

        // Calculate and display results
        await calculateAstrocartography(formData);
    });
};

// ============================================
// SMOOTH SCROLL
// ============================================
const initSmoothScroll = () => {
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
        anchor.addEventListener('click', function (e) {
            e.preventDefault();
            const target = document.querySelector(this.getAttribute('href'));
            if (target) {
                target.scrollIntoView({
                    behavior: 'smooth',
                    block: 'start'
                });
            }
        });
    });
};

// ============================================
// NAVIGATION
// ============================================
const initNavigation = () => {
    const header = document.querySelector('.header');
    let lastScroll = 0;

    window.addEventListener('scroll', () => {
        const currentScroll = window.pageYOffset;
        
        if (currentScroll > 100) {
            header.style.background = 'rgba(13, 2, 33, 0.95)';
        } else {
            header.style.background = 'rgba(13, 2, 33, 0.9)';
        }
        
        lastScroll = currentScroll;
    });
};

// ============================================
// INITIALIZATION
// ============================================
document.addEventListener('DOMContentLoaded', () => {
    initStarfield();
    initializeMap();
    initForm();
    initSmoothScroll();
    initNavigation();
});

// Reveal animations on scroll
const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
};

const revealObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.style.opacity = '1';
            entry.target.style.transform = 'translateY(0)';
        }
    });
}, observerOptions);

// Apply reveal animation to cards
document.addEventListener('DOMContentLoaded', () => {
    document.querySelectorAll('.about-card, .form-card, .legend-card').forEach(el => {
        el.style.opacity = '0';
        el.style.transform = 'translateY(30px)';
        el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
        revealObserver.observe(el);
    });
});

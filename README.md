# Opulent-Decor-and-Events-
Client  form
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Opulent Decor & Events | Luxury Event Decoration</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=Lato:wght@300;400;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --gold: #D4AF37;
            --gold-light: #F4E8C1;
            --dark: #0a0a0a;
            --darker: #050505;
            --white: #ffffff;
            --rose-gold: #B76E79;
            --bronze: #CD7F32;
            --red: #DC143C;
        }

        body {
            font-family: 'Lato', sans-serif;
            background-color: var(--darker);
            color: var(--white);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Live Wallpaper Canvas */
        #liveWallpaper {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
        }

        /* Navigation */
        nav {
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            background: rgba(5, 5, 5, 0.9);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(212, 175, 55, 0.2);
            padding: 0.8rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all 0.3s;
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 0.8rem;
        }

        .logo-img {
            height: 45px;
            width: auto;
            filter: drop-shadow(0 0 10px rgba(212, 175, 55, 0.5));
            animation: pulseLogo 2s ease-in-out infinite;
        }

        @keyframes pulseLogo {
            0%, 100% { filter: drop-shadow(0 0 10px rgba(212, 175, 55, 0.5)); }
            50% { filter: drop-shadow(0 0 20px rgba(212, 175, 55, 0.8)); }
        }

        .logo-text {
            font-family: 'Playfair Display', serif;
            font-size: 1.1rem;
            font-weight: 700;
            color: var(--gold);
            letter-spacing: 2px;
        }

        .nav-links {
            display: flex;
            gap: 2.5rem;
            list-style: none;
        }

        .nav-links a {
            color: var(--white);
            text-decoration: none;
            font-weight: 300;
            letter-spacing: 1.5px;
            font-size: 0.9rem;
            text-transform: uppercase;
            transition: all 0.3s;
            position: relative;
            padding: 0.5rem 0;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--gold), var(--rose-gold));
            transition: width 0.3s;
        }

        .nav-links a:hover::after,
        .nav-links a.active::after {
            width: 100%;
        }

        .nav-links a:hover,
        .nav-links a.active {
            color: var(--gold);
        }

        /* Mobile Menu */
        .mobile-menu-btn {
            display: none;
            flex-direction: column;
            gap: 5px;
            cursor: pointer;
            z-index: 1001;
        }

        .mobile-menu-btn span {
            width: 30px;
            height: 2px;
            background: var(--gold);
            transition: all 0.3s;
        }

        /* Page Container */
        .page {
            display: none;
            min-height: 100vh;
            padding-top: 80px;
            animation: fadeIn 0.6s ease;
        }

        .page.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* HOME PAGE */
        .home-page {
            padding-top: 0;
        }

        .hero-cinematic {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero-cinematic::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: radial-gradient(ellipse at center, transparent 0%, rgba(5,5,5,0.8) 100%);
            z-index: 1;
        }

        .hero-content {
            position: relative;
            z-index: 2;
            max-width: 900px;
            padding: 2rem;
        }

        .hero-logo-large {
            width: 280px;
            height: auto;
            margin-bottom: 2rem;
            filter: drop-shadow(0 0 30px rgba(212, 175, 55, 0.6));
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0) scale(1); }
            50% { transform: translateY(-20px) scale(1.02); }
        }

        .hero-title {
            font-family: 'Playfair Display', serif;
            font-size: 4.5rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            background: linear-gradient(135deg, var(--gold) 0%, var(--rose-gold) 50%, var(--gold) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: 4px;
            animation: shimmer 3s linear infinite;
            background-size: 200% auto;
        }

        @keyframes shimmer {
            0% { background-position: -200% center; }
            100% { background-position: 200% center; }
        }

        .hero-slogan {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            color: var(--red);
            margin-bottom: 1.5rem;
            letter-spacing: 6px;
            text-transform: lowercase;
        }

        .hero-tagline {
            font-size: 1.3rem;
            color: rgba(255,255,255,0.8);
            margin-bottom: 3rem;
            font-weight: 300;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        .hero-cta {
            display: inline-flex;
            align-items: center;
            gap: 1rem;
            padding: 1.2rem 3rem;
            background: linear-gradient(135deg, var(--gold), var(--rose-gold));
            color: var(--dark);
            text-decoration: none;
            font-weight: 700;
            letter-spacing: 2px;
            border-radius: 50px;
            transition: all 0.4s;
            box-shadow: 0 10px 40px rgba(212, 175, 55, 0.4);
            font-size: 1.1rem;
            border: 2px solid transparent;
        }

        .hero-cta:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 60px rgba(212, 175, 55, 0.6);
            border-color: var(--gold-light);
        }

        .scroll-indicator {
            position: absolute;
            bottom: 40px;
            left: 50%;
            transform: translateX(-50%);
            animation: bounce 2s infinite;
            z-index: 2;
        }

        .scroll-indicator svg {
            width: 30px;
            height: 30px;
            fill: var(--gold);
        }

        @keyframes bounce {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(-10px); }
        }

        /* Pricing Preview Section on Home */
        .pricing-preview {
            padding: 6rem 5%;
            background: linear-gradient(180deg, transparent 0%, rgba(10,10,10,0.95) 100%);
        }

        .pricing-cards {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 2rem;
            max-width: 1200px;
            margin: 3rem auto 0;
        }

        .pricing-card {
            background: rgba(255,255,255,0.03);
            border: 1px solid rgba(212,175,55,0.2);
            border-radius: 20px;
            padding: 2.5rem 2rem;
            text-align: center;
            transition: all 0.4s;
            backdrop-filter: blur(10px);
            position: relative;
            overflow: hidden;
        }

        .pricing-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--gold), var(--rose-gold));
            opacity: 0;
            transition: opacity 0.3s;
        }

        .pricing-card:hover::before {
            opacity: 1;
        }

        .pricing-card:hover {
            transform: translateY(-10px);
            border-color: var(--gold);
            box-shadow: 0 20px 40px rgba(212,175,55,0.2);
        }

        .pricing-card.featured {
            border-color: var(--gold);
            transform: scale(1.05);
        }

        .pricing-card.featured::before {
            opacity: 1;
        }

        .pricing-tier {
            font-family: 'Playfair Display', serif;
            font-size: 1.5rem;
            color: var(--gold-light);
            margin-bottom: 0.5rem;
        }

        .pricing-card.featured .pricing-tier {
            color: var(--gold);
        }

        .pricing-amount {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--white);
            margin-bottom: 0.5rem;
        }

        .pricing-amount span {
            font-size: 0.9rem;
            color: rgba(255,255,255,0.6);
            display: block;
            font-weight: 400;
        }

        .pricing-desc {
            color: rgba(255,255,255,0.7);
            font-size: 0.9rem;
            margin-bottom: 1.5rem;
        }

        .view-details-btn {
            display: inline-block;
            padding: 0.8rem 1.5rem;
            background: transparent;
            border: 1px solid var(--gold);
            color: var(--gold);
            text-decoration: none;
            border-radius: 25px;
            font-size: 0.9rem;
            transition: all 0.3s;
        }

        .view-details-btn:hover {
            background: var(--gold);
            color: var(--dark);
        }

        /* ABOUT PAGE */
        .about-page {
            background: linear-gradient(135deg, rgba(10,10,10,0.95), rgba(5,5,5,0.98));
        }

        .about-hero {
            min-height: 60vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 4rem 2rem;
            position: relative;
        }

        .about-hero-content h1 {
            font-family: 'Playfair Display', serif;
            font-size: 4rem;
            color: var(--gold);
            margin-bottom: 1rem;
        }

        .about-hero-content p {
            font-size: 1.3rem;
            color: rgba(255,255,255,0.8);
            max-width: 700px;
        }

        .about-content-split {
            display: grid;
            grid-template-columns: 1fr 1fr;
            min-height: 80vh;
        }

        .about-image-side {
            background: linear-gradient(135deg, rgba(212,175,55,0.1), rgba(183,110,121,0.1));
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 4rem;
            position: relative;
            overflow: hidden;
        }

        .about-image-side::before {
            content: '';
            position: absolute;
            width: 300px;
            height: 300px;
            border: 2px solid var(--gold);
            border-radius: 50%;
            animation: rotate 20s linear infinite;
            opacity: 0.3;
        }

        .about-logo-large {
            width: 250px;
            filter: drop-shadow(0 0 40px rgba(212,175,55,0.5));
            z-index: 2;
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .about-text-side {
            padding: 4rem;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .about-text-side h2 {
            font-family: 'Playfair Display', serif;
            font-size: 2.5rem;
            color: var(--gold);
            margin-bottom: 2rem;
        }

        .about-text-side p {
            color: rgba(255,255,255,0.85);
            font-size: 1.1rem;
            line-height: 1.9;
            margin-bottom: 1.5rem;
        }

        .stats-row {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 2rem;
            margin-top: 3rem;
            padding-top: 3rem;
            border-top: 1px solid rgba(212,175,55,0.2);
        }

        .stat-item {
            text-align: center;
        }

        .stat-number {
            font-family: 'Playfair Display', serif;
            font-size: 3rem;
            color: var(--gold);
            display: block;
        }

        .stat-label {
            color: rgba(255,255,255,0.7);
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        /* SERVICES PAGE with VISIBLE PRICES */
        .services-page {
            background: var(--dark);
        }

        .services-hero {
            text-align: center;
            padding: 5rem 2rem;
        }

        .services-hero h1 {
            font-family: 'Playfair Display', serif;
            font-size: 4rem;
            color: var(--gold);
            margin-bottom: 1rem;
        }

        .services-hero p {
            color: rgba(255,255,255,0.8);
            font-size: 1.2rem;
            max-width: 600px;
            margin: 0 auto;
        }

        /* Full Pricing Table Section */
        .pricing-table-section {
            padding: 4rem 5%;
            max-width: 1400px;
            margin: 0 auto;
        }

        .pricing-table-header {
            text-align: center;
            margin-bottom: 3rem;
        }

        .pricing-table-header h2 {
            font-family: 'Playfair Display', serif;
            font-size: 2.5rem;
            color: var(--gold);
            margin-bottom: 1rem;
        }

        .pricing-table-header p {
            color: rgba(255,255,255,0.7);
        }

        .event-pricing-card {
            background: rgba(255,255,255,0.02);
            border: 1px solid rgba(212,175,55,0.15);
            border-radius: 20px;
            margin-bottom: 2rem;
            overflow: hidden;
        }

        .event-header {
            background: linear-gradient(135deg, rgba(212,175,55,0.1), rgba(183,110,121,0.1));
            padding: 1.5rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
            transition: all 0.3s;
        }

        .event-header:hover {
            background: linear-gradient(135deg, rgba(212,175,55,0.2), rgba(183,110,121,0.2));
        }

        .event-title {
            font-family: 'Playfair Display', serif;
            font-size: 1.5rem;
            color: var(--gold-light);
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .event-icon {
            font-size: 2rem;
        }

        .toggle-icon {
            font-size: 1.5rem;
            color: var(--gold);
            transition: transform 0.3s;
        }

        .event-pricing-card.expanded .toggle-icon {
            transform: rotate(180deg);
        }

        .pricing-details {
            display: none;
            padding: 2rem;
        }

        .event-pricing-card.expanded .pricing-details {
            display: block;
            animation: slideDown 0.3s ease;
        }

        @keyframes slideDown {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .class-section {
            margin-bottom: 2rem;
        }

        .class-section:last-child {
            margin-bottom: 0;
        }

        .class-title {
            font-size: 1.1rem;
            color: var(--gold);
            margin-bottom: 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 1px solid rgba(212,175,55,0.2);
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .package-row {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            gap: 1.5rem;
        }

        .package-item {
            background: rgba(0,0,0,0.3);
            border: 1px solid rgba(212,175,55,0.1);
            border-radius: 12px;
            padding: 1.5rem;
            text-align: center;
            transition: all 0.3s;
        }

        .package-item:hover {
            border-color: var(--gold);
            transform: translateY(-3px);
        }

        .package-name {
            font-family: 'Playfair Display', serif;
            font-size: 1.1rem;
            margin-bottom: 0.5rem;
            text-transform: uppercase;
        }

        .package-item.basic .package-name { color: var(--bronze); }
        .package-item.standard .package-name { color: var(--gold); }
        .package-item.premium .package-name { color: var(--rose-gold); }

        .package-price-display {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--white);
            margin-bottom: 0.5rem;
        }

        .package-price-display span {
            font-size: 0.8rem;
            color: rgba(255,255,255,0.6);
            display: block;
        }

        .book-now-btn {
            display: inline-block;
            margin-top: 1rem;
            padding: 0.6rem 1.2rem;
            background: var(--gold);
            color: var(--dark);
            text-decoration: none;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 700;
            transition: all 0.3s;
        }

        .book-now-btn:hover {
            background: var(--rose-gold);
            transform: scale(1.05);
        }

        /* Service Cards with Prices */
        .services-grid-with-prices {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 2rem;
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 2rem 4rem;
        }

        .service-price-card {
            background: rgba(255,255,255,0.02);
            border: 1px solid rgba(212,175,55,0.15);
            border-radius: 20px;
            overflow: hidden;
            transition: all 0.4s;
        }

        .service-price-card:hover {
            border-color: var(--gold);
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(212,175,55,0.15);
        }

        .service-price-header {
            background: linear-gradient(135deg, rgba(212,175,55,0.1), rgba(183,110,121,0.1));
            padding: 2rem;
            text-align: center;
        }

        .service-price-icon {
            font-size: 3.5rem;
            margin-bottom: 1rem;
        }

        .service-price-header h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            color: var(--gold-light);
        }

        .service-price-body {
            padding: 2rem;
        }

        .starting-price {
            text-align: center;
            margin-bottom: 1.5rem;
            padding-bottom: 1.5rem;
            border-bottom: 1px solid rgba(212,175,55,0.1);
        }

        .starting-price-label {
            color: rgba(255,255,255,0.6);
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 0.5rem;
        }

        .starting-price-amount {
            font-family: 'Playfair Display', serif;
            font-size: 2.2rem;
            color: var(--gold);
        }

        .price-range {
            display: flex;
            justify-content: space-between;
            margin-bottom: 1.5rem;
            font-size: 0.9rem;
        }

        .price-range-item {
            text-align: center;
        }

        .price-range-label {
            color: rgba(255,255,255,0.5);
            font-size: 0.75rem;
            text-transform: uppercase;
            margin-bottom: 0.3rem;
        }

        .price-range-value {
            color: var(--white);
            font-weight: 600;
        }

        .service-cta {
            display: block;
            width: 100%;
            padding: 1rem;
            background: linear-gradient(135deg, var(--gold), var(--rose-gold));
            color: var(--dark);
            text-align: center;
            text-decoration: none;
            font-weight: 700;
            border-radius: 10px;
            transition: all 0.3s;
        }

        .service-cta:hover {
            transform: scale(1.02);
            box-shadow: 0 10px 30px rgba(212,175,55,0.3);
        }

        /* BOOK PAGE */
        .book-page {
            background: linear-gradient(180deg, var(--darker) 0%, var(--dark) 100%);
            min-height: 100vh;
            padding: 2rem 5% 6rem;
        }

        .book-header {
            text-align: center;
            padding: 3rem 0;
        }

        .book-header h1 {
            font-family: 'Playfair Display', serif;
            font-size: 3.5rem;
            color: var(--gold);
            margin-bottom: 1rem;
        }

        .book-header p {
            color: rgba(255,255,255,0.7);
            font-size: 1.1rem;
        }

        .booking-container {
            max-width: 1000px;
            margin: 0 auto;
            background: rgba(255,255,255,0.02);
            border: 1px solid rgba(212,175,55,0.2);
            border-radius: 30px;
            padding: 3rem;
            backdrop-filter: blur(20px);
        }

        .form-progress {
            display: flex;
            justify-content: space-between;
            margin-bottom: 3rem;
            position: relative;
        }

        .form-progress::before {
            content: '';
            position: absolute;
            top: 20px;
            left: 10%;
            right: 10%;
            height: 2px;
            background: rgba(212,175,55,0.2);
            z-index: 0;
        }

        .progress-step {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.5rem;
            z-index: 1;
        }

        .step-circle {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--dark);
            border: 2px solid rgba(212,175,55,0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            color: var(--gold);
            transition: all 0.3s;
        }

        .progress-step.active .step-circle {
            background: var(--gold);
            color: var(--dark);
            border-color: var(--gold);
            box-shadow: 0 0 20px rgba(212,175,55,0.5);
        }

        .step-label {
            font-size: 0.8rem;
            color: rgba(255,255,255,0.6);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .form-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
        }

        .form-group {
            position: relative;
        }

        .form-group.full-width {
            grid-column: 1 / -1;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: var(--gold-light);
            font-weight: 400;
            letter-spacing: 1px;
            font-size: 0.85rem;
            text-transform: uppercase;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 1rem 1.2rem;
            background: rgba(0,0,0,0.3);
            border: 1px solid rgba(212,175,55,0.2);
            border-radius: 10px;
            color: var(--white);
            font-family: 'Lato', sans-serif;
            transition: all 0.3s;
            font-size: 1rem;
        }

        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--gold);
            box-shadow: 0 0 15px rgba(212,175,55,0.2);
            background: rgba(0,0,0,0.5);
        }

        /* Color Palette Grid */
        .palette-section {
            grid-column: 1 / -1;
            background: rgba(0,0,0,0.2);
            border-radius: 15px;
            padding: 2rem;
            margin: 1rem 0;
        }

        .palette-header {
            text-align: center;
            margin-bottom: 1.5rem;
        }

        .palette-header h3 {
            font-family: 'Playfair Display', serif;
            color: var(--gold);
            font-size: 1.5rem;
        }

        .palette-categories {
            display: flex;
            justify-content: center;
            gap: 0.5rem;
            margin-bottom: 1.5rem;
            flex-wrap: wrap;
        }

        .palette-cat-btn {
            padding: 0.5rem 1rem;
            background: transparent;
            border: 1px solid rgba(212,175,55,0.3);
            color: var(--white);
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.8rem;
            transition: all 0.3s;
        }

        .palette-cat-btn:hover,
        .palette-cat-btn.active {
            background: var(--gold);
            color: var(--dark);
            border-color: var(--gold);
        }

        .palette-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1rem;
        }

        .palette-option {
            cursor: pointer;
            border-radius: 10px;
            overflow: hidden;
            border: 2px solid transparent;
            transition: all 0.3s;
        }

        .palette-option:hover {
            transform: translateY(-5px);
        }

        .palette-option.selected {
            border-color: var(--gold);
            box-shadow: 0 0 20px rgba(212,175,55,0.3);
        }

        .palette-colors {
            display: flex;
            height: 60px;
        }

        .palette-color-block {
            flex: 1;
        }

        .palette-name {
            padding: 0.5rem;
            text-align: center;
            font-size: 0.8rem;
            background: rgba(0,0,0,0.5);
            color: var(--white);
        }

        /* Package Selection */
        .package-section {
            grid-column: 1 / -1;
            margin: 1rem 0;
        }

        .package-tabs {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .package-tab {
            padding: 0.8rem 1.5rem;
            background: transparent;
            border: 1px solid rgba(212,175,55,0.3);
            color: var(--white);
            border-radius: 25px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
        }

        .package-tab.active {
            background: linear-gradient(135deg, var(--gold), var(--rose-gold));
            color: var(--dark);
            border-color: transparent;
        }

        .package-cards {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 1.5rem;
        }

        .package-card {
            background: rgba(0,0,0,0.3);
            border: 2px solid rgba(212,175,55,0.2);
            border-radius: 15px;
            padding: 2rem;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            position: relative;
        }

        .package-card:hover {
            transform: translateY(-5px);
            border-color: rgba(212,175,55,0.5);
        }

        .package-card.selected {
            border-color: var(--gold);
            background: rgba(212,175,55,0.1);
        }

        .package-card.selected::before {
            content: '✓';
            position: absolute;
            top: -10px;
            right: -10px;
            width: 30px;
            height: 30px;
            background: var(--gold);
            color: var(--dark);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
        }

        .package-tier-name {
            font-family: 'Playfair Display', serif;
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .package-card[data-tier="basic"] .package-tier-name { color: var(--bronze); }
        .package-card[data-tier="standard"] .package-tier-name { color: var(--gold); }
        .package-card[data-tier="premium"] .package-tier-name { color: var(--rose-gold); }

        .package-price {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 1rem;
        }

        .submit-btn {
            width: 100%;
            padding: 1.3rem;
            margin-top: 2rem;
            background: linear-gradient(135deg, var(--gold), var(--rose-gold));
            border: none;
            border-radius: 12px;
            color: var(--dark);
            font-weight: 700;
            font-size: 1.1rem;
            letter-spacing: 2px;
            cursor: pointer;
            transition: all 0.3s;
            text-transform: uppercase;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.8rem;
        }

        .submit-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(212,175,55,0.4);
        }

        /* Footer */
        footer {
            background: var(--darker);
            padding: 3rem 5%;
            text-align: center;
            border-top: 1px solid rgba(212,175,55,0.2);
        }

        .footer-logo {
            width: 80px;
            margin-bottom: 1rem;
        }

        .footer-slogan {
            color: var(--red);
            font-family: 'Playfair Display', serif;
            letter-spacing: 4px;
            margin-bottom: 1.5rem;
        }

        .footer-contact {
            display: flex;
            justify-content: center;
            gap: 3rem;
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .footer-contact span {
            color: rgba(255,255,255,0.7);
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        /* WhatsApp Float */
        .whatsapp-float {
            position: fixed;
            bottom: 30px;
            right: 30px;
            z-index: 999;
            animation: pulseWhatsApp 2s infinite;
        }

        @keyframes pulseWhatsApp {
            0%, 100% { box-shadow: 0 0 0 0 rgba(37,211,102,0.7); }
            50% { box-shadow: 0 0 0 20px rgba(37,211,102,0); }
        }

        .whatsapp-btn {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            background: #25D366;
            color: white;
            padding: 1rem 1.5rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 700;
            box-shadow: 0 10px 30px rgba(37,211,102,0.4);
            transition: all 0.3s;
        }

        .whatsapp-btn:hover {
            transform: scale(1.05);
        }

        /* MOBILE RESPONSIVE */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
                position: absolute;
                top: 100%;
                left: 0;
                right: 0;
                background: rgba(5,5,5,0.98);
                flex-direction: column;
                padding: 2rem;
                gap: 1.5rem;
                border-bottom: 1px solid rgba(212,175,55,0.2);
            }

            .nav-links.active {
                display: flex;
            }

            .mobile-menu-btn {
                display: flex;
            }

            .hero-logo-large {
                width: 180px;
            }

            .hero-title {
                font-size: 2.5rem;
            }

            .hero-slogan {
                font-size: 1.2rem;
                letter-spacing: 3px;
            }

            .pricing-cards {
                grid-template-columns: 1fr;
            }

            .pricing-card.featured {
                transform: none;
            }

            .about-content-split {
                grid-template-columns: 1fr;
            }

            .about-image-side {
                min-height: 300px;
                order: -1;
            }

            .about-text-side {
                padding: 2rem;
            }

            .stats-row {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }

            .services-grid-with-prices {
                grid-template-columns: 1fr;
            }

            .package-row {
                grid-template-columns: 1fr;
            }

            .booking-container {
                padding: 1.5rem;
                border-radius: 20px;
            }

            .form-grid {
                grid-template-columns: 1fr;
            }

            .palette-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .package-cards {
                grid-template-columns: 1fr;
            }

            .package-tabs {
                flex-direction: column;
                align-items: center;
            }

            .section-header h2,
            .about-hero-content h1,
            .services-hero h1,
            .book-header h1 {
                font-size: 2.2rem;
            }

            .footer-contact {
                flex-direction: column;
                gap: 1rem;
            }

            .whatsapp-float {
                bottom: 20px;
                right: 20px;
            }

            .whatsapp-btn span {
                display: none;
            }
        }

        /* Desktop Enhancements */
        @media (min-width: 1200px) {
            .services-grid-with-prices {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body>

    <!-- Live Wallpaper Canvas -->
    <canvas id="liveWallpaper"></canvas>

    <!-- Navigation -->
    <nav>
        <div class="logo-container">
            <img src="/mnt/kimi/upload/opulent.png" alt="Opulent Decor" class="logo-img">
            <span class="logo-text">OPULENT DECOR</span>
        </div>
        <ul class="nav-links" id="navLinks">
            <li><a href="#" class="active" onclick="showPage('home')">Home</a></li>
            <li><a href="#" onclick="showPage('about')">About</a></li>
            <li><a href="#" onclick="showPage('services')">Services</a></li>
            <li><a href="#" onclick="showPage('book')">Book Now</a></li>
        </ul>
        <div class="mobile-menu-btn" onclick="toggleMobileMenu()">
            <span></span>
            <span></span>
            <span></span>
        </div>
    </nav>

    <!-- HOME PAGE -->
    <div class="page home-page active" id="home">
        <section class="hero-cinematic">
            <div class="hero-content">
                <img src="/mnt/kimi/upload/opulent.png" alt="Opulent Decor & Events" class="hero-logo-large">
                <h1 class="hero-title">OPULENT DECOR</h1>
                <p class="hero-slogan">Luxury . style . perfection</p>
                <p class="hero-tagline">Transforming your special moments into extraordinary memories with bespoke event decoration and styling</p>
                <a href="#" class="hero-cta" onclick="showPage('book')">Book Your Event →</a>
            </div>
            <div class="scroll-indicator">
                <svg viewBox="0 0 24 24"><path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"/></svg>
            </div>
        </section>

        <!-- Pricing Preview on Home -->
        <section class="pricing-preview">
            <div class="section-header">
                <h2>Transparent Pricing</h2>
                <p>Clear, upfront pricing for every budget. No hidden fees.</p>
            </div>
            <div class="pricing-cards">
                <div class="pricing-card">
                    <div class="pricing-tier">Basic Class</div>
                    <div class="pricing-amount">
                        UGX 300K
                        <span>Starting from</span>
                    </div>
                    <div class="pricing-desc">Perfect for intimate gatherings and simple celebrations</div>
                    <a href="#" class="view-details-btn" onclick="showPage('services')">View Details</a>
                </div>
                <div class="pricing-card featured">
                    <div class="pricing-tier">Middle Class</div>
                    <div class="pricing-amount">
                        UGX 2M
                        <span>Starting from</span>
                    </div>
                    <div class="pricing-desc">Enhanced decor with premium touches for special occasions</div>
                    <a href="#" class="view-details-btn" onclick="showPage('services')">View Details</a>
                </div>
                <div class="pricing-card">
                    <div class="pricing-tier">First Class</div>
                    <div class="pricing-amount">
                        UGX 4M
                        <span>Starting from</span>
                    </div>
                    <div class="pricing-desc">Luxury experience with exquisite details and full service</div>
                    <a href="#" class="view-details-btn" onclick="showPage('services')">View Details</a>
                </div>
            </div>
        </section>
    </div>

    <!-- ABOUT PAGE -->
    <div class="page about-page" id="about">
        <section class="about-hero">
            <div class="about-hero-content">
                <h1>Our Story</h1>
                <p>Crafting moments of magic through the art of luxury event design</p>
            </div>
        </section>

        <div class="about-content-split">
            <div class="about-image-side">
                <img src="/mnt/kimi/upload/opulent.png" alt="Opulent Decor" class="about-logo-large">
            </div>
            <div class="about-text-side">
                <h2>Elegance Redefined</h2>
                <p>At Opulent Decor & Events, we believe every celebration deserves to be nothing short of spectacular. With an eye for detail and a passion for luxury, we specialize in creating breathtaking environments that reflect your unique style and vision.</p>
                <p>From intimate gatherings to grand celebrations, our team of dedicated designers works tirelessly to ensure every element — from color palettes to floral arrangements — harmonizes perfectly to create an atmosphere of pure elegance.</p>
                <p>We don't just decorate venues; we craft experiences that linger in memories long after the last guest has departed. Your dream event is our masterpiece.</p>
                
                <div class="stats-row">
                    <div class="stat-item">
                        <span class="stat-number">500+</span>
                        <span class="stat-label">Events Decorated</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number">10+</span>
                        <span class="stat-label">Years Experience</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number">100%</span>
                        <span class="stat-label">Client Satisfaction</span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- SERVICES PAGE with VISIBLE PRICES -->
    <div class="page services-page" id="services">
        <section class="services-hero">
            <h1>Our Services & Prices</h1>
            <p>Transparent pricing for every celebration. Choose your package with confidence.</p>
        </section>

        <!-- Service Cards with Visible Prices -->
        <div class="services-grid-with-prices">
            <!-- Wedding -->
            <div class="service-price-card">
                <div class="service-price-header">
                    <div class="service-price-icon">💒</div>
                    <h3>Wedding Decoration</h3>
                </div>
                <div class="service-price-body">
                    <div class="starting-price">
                        <div class="starting-price-label">Starting from</div>
                        <div class="starting-price-amount">UGX 3,000,000</div>
                    </div>
                    <div class="price-range">
                        <div class="price-range-item">
                            <div class="price-range-label">Basic</div>
                            <div class="price-range-value">3M - 10M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">Middle</div>
                            <div class="price-range-value">5M - 10M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">First</div>
                            <div class="price-range-value">10M - 100M</div>
                        </div>
                    </div>
                    <a href="#" class="service-cta" onclick="selectService('wedding')">Book Wedding Package</a>
                </div>
            </div>

            <!-- Introduction -->
            <div class="service-price-card">
                <div class="service-price-header">
                    <div class="service-price-icon">🎊</div>
                    <h3>Introduction (Kwanjula)</h3>
                </div>
                <div class="service-price-body">
                    <div class="starting-price">
                        <div class="starting-price-label">Starting from</div>
                        <div class="starting-price-amount">UGX 2,500,000</div>
                    </div>
                    <div class="price-range">
                        <div class="price-range-item">
                            <div class="price-range-label">Basic</div>
                            <div class="price-range-value">2.5M - 5M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">Middle</div>
                            <div class="price-range-value">5M - 10M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">First</div>
                            <div class="price-range-value">10M - 50M</div>
                        </div>
                    </div>
                    <a href="#" class="service-cta" onclick="selectService('introduction')">Book Introduction</a>
                </div>
            </div>

            <!-- Kukyala -->
            <div class="service-price-card">
                <div class="service-price-header">
                    <div class="service-price-icon">💍</div>
                    <h3>Kukyala Decor</h3>
                </div>
                <div class="service-price-body">
                    <div class="starting-price">
                        <div class="starting-price-label">Starting from</div>
                        <div class="starting-price-amount">UGX 500,000</div>
                    </div>
                    <div class="price-range">
                        <div class="price-range-item">
                            <div class="price-range-label">Basic</div>
                            <div class="price-range-value">500K - 2M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">Middle</div>
                            <div class="price-range-value">2M - 4M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">First</div>
                            <div class="price-range-value">4M - 10M</div>
                        </div>
                    </div>
                    <a href="#" class="service-cta" onclick="selectService('kukyala')">Book Kukyala</a>
                </div>
            </div>

            <!-- Birthday -->
            <div class="service-price-card">
                <div class="service-price-header">
                    <div class="service-price-icon">🎂</div>
                    <h3>Birthday Parties</h3>
                </div>
                <div class="service-price-body">
                    <div class="starting-price">
                        <div class="starting-price-label">Starting from</div>
                        <div class="starting-price-amount">UGX 500,000</div>
                    </div>
                    <div class="price-range">
                        <div class="price-range-item">
                            <div class="price-range-label">Basic</div>
                            <div class="price-range-value">500K - 2M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">Middle</div>
                            <div class="price-range-value">2M - 4M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">First</div>
                            <div class="price-range-value">4M - 10M</div>
                        </div>
                    </div>
                    <a href="#" class="service-cta" onclick="selectService('birthday')">Book Birthday</a>
                </div>
            </div>

            <!-- Bridal Shower -->
            <div class="service-price-card">
                <div class="service-price-header">
                    <div class="service-price-icon">👰</div>
                    <h3>Bridal Shower</h3>
                </div>
                <div class="service-price-body">
                    <div class="starting-price">
                        <div class="starting-price-label">Starting from</div>
                        <div class="starting-price-amount">UGX 300,000</div>
                    </div>
                    <div class="price-range">
                        <div class="price-range-item">
                            <div class="price-range-label">Basic</div>
                            <div class="price-range-value">300K - 1M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">Middle</div>
                            <div class="price-range-value">1M - 2.5M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">First</div>
                            <div class="price-range-value">3M - 5M</div>
                        </div>
                    </div>
                    <a href="#" class="service-cta" onclick="selectService('bridal-shower')">Book Bridal Shower</a>
                </div>
            </div>

            <!-- Baby Shower -->
            <div class="service-price-card">
                <div class="service-price-header">
                    <div class="service-price-icon">🍼</div>
                    <h3>Baby Shower</h3>
                </div>
                <div class="service-price-body">
                    <div class="starting-price">
                        <div class="starting-price-label">Starting from</div>
                        <div class="starting-price-amount">UGX 300,000</div>
                    </div>
                    <div class="price-range">
                        <div class="price-range-item">
                            <div class="price-range-label">Basic</div>
                            <div class="price-range-value">300K - 1M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">Middle</div>
                            <div class="price-range-value">1M - 2.5M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">First</div>
                            <div class="price-range-value">3M - 5M</div>
                        </div>
                    </div>
                    <a href="#" class="service-cta" onclick="selectService('baby-shower')">Book Baby Shower</a>
                </div>
            </div>

            <!-- Kuhingira -->
            <div class="service-price-card">
                <div class="service-price-header">
                    <div class="service-price-icon">🏡</div>
                    <h3>Kuhingira</h3>
                </div>
                <div class="service-price-body">
                    <div class="starting-price">
                        <div class="starting-price-label">Starting from</div>
                        <div class="starting-price-amount">UGX 300,000</div>
                    </div>
                    <div class="price-range">
                        <div class="price-range-item">
                            <div class="price-range-label">Basic</div>
                            <div class="price-range-value">300K - 1M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">Middle</div>
                            <div class="price-range-value">1M - 2.5M</div>
                        </div>
                        <div class="price-range-item">
                            <div class="price-range-label">First</div>
                            <div class="price-range-value">3M - 5M</div>
                        </div>
                    </div>
                    <a href="#" class="service-cta" onclick="selectService('kuhingira')">Book Kuhingira</a>
                </div>
            </div>
        </div>

        <!-- Detailed Pricing Table -->
        <div class="pricing-table-section">
            <div class="pricing-table-header">
                <h2>Complete Price List</h2>
                <p>Click on any service to see detailed pricing by package tier</p>
            </div>

            <!-- Wedding Pricing -->
            <div class="event-pricing-card expanded">
                <div class="event-header" onclick="togglePricing(this)">
                    <div class="event-title">
                        <span class="event-icon">💒</span>
                        Wedding Decoration
                    </div>
                    <span class="toggle-icon">▼</span>
                </div>
                <div class="pricing-details">
                    <div class="class-section">
                        <div class="class-title">Basic Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 3,000,000<span>Essential package</span></div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('wedding', 'basic', 'basic', 3000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 5,000,000<span>Popular choice</span></div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('wedding', 'basic', 'standard', 5000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 10,000,000<span>All inclusive</span></div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('wedding', 'basic', 'premium', 10000000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">Middle Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 5,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('wedding', 'middle', 'basic', 5000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 7,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('wedding', 'middle', 'standard', 7000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 10,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('wedding', 'middle', 'premium', 10000000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">First Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 10,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('wedding', 'first', 'basic', 10000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 35,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('wedding', 'first', 'standard', 35000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 100,000,000<span>Luxury ultimate</span></div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('wedding', 'first', 'premium', 100000000)">Select</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Introduction Pricing -->
            <div class="event-pricing-card">
                <div class="event-header" onclick="togglePricing(this)">
                    <div class="event-title">
                        <span class="event-icon">🎊</span>
                        Introduction (Kwanjula)
                    </div>
                    <span class="toggle-icon">▼</span>
                </div>
                <div class="pricing-details">
                    <div class="class-section">
                        <div class="class-title">Basic Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 2,500,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('introduction', 'basic', 'basic', 2500000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 3,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('introduction', 'basic', 'standard', 3000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 5,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('introduction', 'basic', 'premium', 5000000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">Middle Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 5,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('introduction', 'middle', 'basic', 5000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 6,500,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('introduction', 'middle', 'standard', 6500000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 10,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('introduction', 'middle', 'premium', 10000000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">First Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 10,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('introduction', 'first', 'basic', 10000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 15,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('introduction', 'first', 'standard', 15000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 50,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('introduction', 'first', 'premium', 50000000)">Select</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Kukyala Pricing -->
            <div class="event-pricing-card">
                <div class="event-header" onclick="togglePricing(this)">
                    <div class="event-title">
                        <span class="event-icon">💍</span>
                        Kukyala
                    </div>
                    <span class="toggle-icon">▼</span>
                </div>
                <div class="pricing-details">
                    <div class="class-section">
                        <div class="class-title">Basic Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 500,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kukyala', 'basic', 'basic', 500000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 1,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kukyala', 'basic', 'standard', 1000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 2,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kukyala', 'basic', 'premium', 2000000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">Middle Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 2,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kukyala', 'middle', 'basic', 2000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 3,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kukyala', 'middle', 'standard', 3000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 4,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kukyala', 'middle', 'premium', 4000000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">First Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 4,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kukyala', 'first', 'basic', 4000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 6,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kukyala', 'first', 'standard', 6000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 10,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kukyala', 'first', 'premium', 10000000)">Select</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Birthday Pricing -->
            <div class="event-pricing-card">
                <div class="event-header" onclick="togglePricing(this)">
                    <div class="event-title">
                        <span class="event-icon">🎂</span>
                        Birthday Parties
                    </div>
                    <span class="toggle-icon">▼</span>
                </div>
                <div class="pricing-details">
                    <div class="class-section">
                        <div class="class-title">Basic Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 500,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('birthday', 'basic', 'basic', 500000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 1,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('birthday', 'basic', 'standard', 1000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 2,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('birthday', 'basic', 'premium', 2000000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">Middle Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 2,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('birthday', 'middle', 'basic', 2000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 3,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('birthday', 'middle', 'standard', 3000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 4,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('birthday', 'middle', 'premium', 4000000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">First Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 4,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('birthday', 'first', 'basic', 4000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 6,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('birthday', 'first', 'standard', 6000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 10,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('birthday', 'first', 'premium', 10000000)">Select</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Bridal Shower Pricing -->
            <div class="event-pricing-card">
                <div class="event-header" onclick="togglePricing(this)">
                    <div class="event-title">
                        <span class="event-icon">👰</span>
                        Bridal Shower
                    </div>
                    <span class="toggle-icon">▼</span>
                </div>
                <div class="pricing-details">
                    <div class="class-section">
                        <div class="class-title">Basic Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 300,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('bridal-shower', 'basic', 'basic', 300000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 500,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('bridal-shower', 'basic', 'standard', 500000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 1,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('bridal-shower', 'basic', 'premium', 1000000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">Middle Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 1,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('bridal-shower', 'middle', 'basic', 1000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 2,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('bridal-shower', 'middle', 'standard', 2000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 2,500,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('bridal-shower', 'middle', 'premium', 2500000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">First Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 3,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('bridal-shower', 'first', 'basic', 3000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 3,700,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('bridal-shower', 'first', 'standard', 3700000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 5,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('bridal-shower', 'first', 'premium', 5000000)">Select</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Baby Shower Pricing -->
            <div class="event-pricing-card">
                <div class="event-header" onclick="togglePricing(this)">
                    <div class="event-title">
                        <span class="event-icon">🍼</span>
                        Baby Shower
                    </div>
                    <span class="toggle-icon">▼</span>
                </div>
                <div class="pricing-details">
                    <div class="class-section">
                        <div class="class-title">Basic Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 300,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('baby-shower', 'basic', 'basic', 300000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 500,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('baby-shower', 'basic', 'standard', 500000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 1,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('baby-shower', 'basic', 'premium', 1000000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">Middle Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 1,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('baby-shower', 'middle', 'basic', 1000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 2,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('baby-shower', 'middle', 'standard', 2000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 2,500,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('baby-shower', 'middle', 'premium', 2500000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">First Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 3,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('baby-shower', 'first', 'basic', 3000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 3,700,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('baby-shower', 'first', 'standard', 3700000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 5,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('baby-shower', 'first', 'premium', 5000000)">Select</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Kuhingira Pricing -->
            <div class="event-pricing-card">
                <div class="event-header" onclick="togglePricing(this)">
                    <div class="event-title">
                        <span class="event-icon">🏡</span>
                        Kuhingira
                    </div>
                    <span class="toggle-icon">▼</span>
                </div>
                <div class="pricing-details">
                    <div class="class-section">
                        <div class="class-title">Basic Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 300,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kuhingira', 'basic', 'basic', 300000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 500,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kuhingira', 'basic', 'standard', 500000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 1,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kuhingira', 'basic', 'premium', 1000000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">Middle Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 1,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kuhingira', 'middle', 'basic', 1000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 2,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kuhingira', 'middle', 'standard', 2000000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 2,500,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kuhingira', 'middle', 'premium', 2500000)">Select</a>
                            </div>
                        </div>
                    </div>
                    <div class="class-section">
                        <div class="class-title">First Class</div>
                        <div class="package-row">
                            <div class="package-item basic">
                                <div class="package-name">Basic</div>
                                <div class="package-price-display">UGX 3,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kuhingira', 'first', 'basic', 3000000)">Select</a>
                            </div>
                            <div class="package-item standard">
                                <div class="package-name">Standard</div>
                                <div class="package-price-display">UGX 3,700,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kuhingira', 'first', 'standard', 3700000)">Select</a>
                            </div>
                            <div class="package-item premium">
                                <div class="package-name">Premium</div>
                                <div class="package-price-display">UGX 5,000,000</div>
                                <a href="#" class="book-now-btn" onclick="bookPackage('kuhingira', 'first', 'premium', 5000000)">Select</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- BOOK PAGE -->
    <div class="page book-page" id="book">
        <div class="book-header">
            <h1>Book Your Event</h1>
            <p>Fill in the details below and we'll create magic for your special day</p>
        </div>

        <div class="booking-container">
            <div class="form-progress">
                <div class="progress-step active">
                    <div class="step-circle">1</div>
                    <span class="step-label">Details</span>
                </div>
                <div class="progress-step">
                    <div class="step-circle">2</div>
                    <span class="step-label">Theme</span>
                </div>
                <div class="progress-step">
                    <div class="step-circle">3</div>
                    <span class="step-label">Package</span>
                </div>
                <div class="progress-step">
                    <div class="step-circle">4</div>
                    <span class="step-label">Confirm</span>
                </div>
            </div>

            <form id="bookingForm" onsubmit="submitToWhatsApp(event)">
                <div class="form-grid">
                    <div class="form-group">
                        <label>Full Name *</label>
                        <input type="text" name="fullname" required placeholder="Your full name">
                    </div>
                    <div class="form-group">
                        <label>Phone Number *</label>
                        <input type="tel" name="phone" required placeholder="07XX XXX XXX">
                    </div>
                    <div class="form-group">
                        <label>Email Address *</label>
                        <input type="email" name="email" required placeholder="your@email.com">
                    </div>
                    <div class="form-group">
                        <label>Event Type *</label>
                        <select name="eventType" id="eventTypeSelect" required onchange="updatePackages()">
                            <option value="">Select Event Type</option>
                            <option value="wedding">Wedding</option>
                            <option value="introduction">Introduction (Kwanjula)</option>
                            <option value="kukyala">Kukyala</option>
                            <option value="birthday">Birthday Party</option>
                            <option value="bridal-shower">Bridal Shower</option>
                            <option value="baby-shower">Baby Shower</option>
                            <option value="kuhingira">Kuhingira</option>
                            <option value="other">Other</option>
                        </select>
                    </div>

                    <!-- Color Palette Section -->
                    <div class="palette-section">
                        <div class="palette-header">
                            <h3>Choose Your Color Theme</h3>
                        </div>
                        <div class="palette-categories">
                            <button type="button" class="palette-cat-btn active" onclick="showPaletteCat('classic')">Classic</button>
                            <button type="button" class="palette-cat-btn" onclick="showPaletteCat('romantic')">Romantic</button>
                            <button type="button" class="palette-cat-btn" onclick="showPaletteCat('modern')">Modern</button>
                            <button type="button" class="palette-cat-btn" onclick="showPaletteCat('earthy')">Earthy</button>
                        </div>
                        <div class="palette-grid" id="paletteGrid">
                            <!-- Populated by JS -->
                        </div>
                        <input type="hidden" name="selectedTheme" id="selectedTheme">
                        <input type="hidden" name="themeColors" id="themeColors">
                    </div>

                    <!-- Package Selection with Visible Prices -->
                    <div class="package-section" id="packageSection" style="display: none;">
                        <div class="package-tabs">
                            <button type="button" class="package-tab active" onclick="setPackageClass('basic')">Basic Class</button>
                            <button type="button" class="package-tab" onclick="setPackageClass('middle')">Middle Class</button>
                            <button type="button" class="package-tab" onclick="setPackageClass('first')">First Class</button>
                        </div>
                        <div class="package-cards" id="packageCards">
                            <!-- Populated by JS with prices -->
                        </div>
                        <input type="hidden" name="selectedClass" id="selectedClass" value="basic">
                        <input type="hidden" name="selectedPackage" id="selectedPackage">
                        <input type="hidden" name="packagePrice" id="packagePrice">
                    </div>

                    <div class="form-group">
                        <label>Event Date *</label>
                        <input type="date" name="eventDate" required>
                    </div>
                    <div class="form-group">
                        <label>Event Time *</label>
                        <input type="time" name="eventTime" required>
                    </div>
                    <div class="form-group">
                        <label>Venue Type *</label>
                        <select name="venueType" required>
                            <option value="">Select Venue Type</option>
                            <option value="garden">Garden/Outdoor</option>
                            <option value="hall">Reception Hall</option>
                            <option value="hotel">Hotel Ballroom</option>
                            <option value="home">Private Residence</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>Number of Guests *</label>
                        <input type="number" name="guestCount" min="1" required placeholder="Estimated guests">
                    </div>
                    <div class="form-group full-width">
                        <label>Venue Name & Address *</label>
                        <input type="text" name="venueAddress" required placeholder="Venue name, district, full address with landmarks...">
                    </div>
                    <div class="form-group full-width">
                        <label>Additional Details</label>
                        <textarea name="details" rows="4" placeholder="Tell us more about your vision, specific requirements, or special requests..."></textarea>
                    </div>
                </div>

                <button type="submit" class="submit-btn">
                    <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
                    Send to WhatsApp
                </button>
            </form>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <img src="/mnt/kimi/upload/opulent.png" alt="Opulent Decor" class="footer-logo">
        <p class="footer-slogan">Luxury . style . perfection</p>
        <div class="footer-contact">
            <span>📞 0747378298</span>
            <span>📱 0751215607</span>
            <span>✉️ opulentdecor@gmail.com</span>
        </div>
        <p style="color: rgba(255,255,255,0.4); font-size: 0.9rem;">&copy; 2026 Opulent Decor & Events. All rights reserved.</p>
    </footer>

    <!-- WhatsApp Float -->
    <div class="whatsapp-float">
        <a href="https://wa.me/256751215607" class="whatsapp-btn" target="_blank">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
            <span>Chat Now</span>
        </a>
    </div>

    <script>
        // Live Wallpaper Animation
        const canvas = document.getElementById('liveWallpaper');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        class Particle {
            constructor() {
                this.reset();
            }

            reset() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 2 + 0.5;
                this.speedX = (Math.random() - 0.5) * 0.5;
                this.speedY = (Math.random() - 0.5) * 0.5;
                this.opacity = Math.random() * 0.5 + 0.1;
                this.color = Math.random() > 0.5 ? '#D4AF37' : '#B76E79';
            }

            update() {
                this.x += this.speedX;
                this.y += this.speedY;

                if (this.x < 0 || this.x > canvas.width || this.y < 0 || this.y > canvas.height) {
                    this.reset();
                }
            }

            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.globalAlpha = this.opacity;
                ctx.fill();
                ctx.globalAlpha = 1;
            }
        }

        function initParticles() {
            particles = [];
            const particleCount = window.innerWidth < 768 ? 30 : 60;
            for (let i = 0; i < particleCount; i++) {
                particles.push(new Particle());
            }
        }

        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            const gradient = ctx.createRadialGradient(
                canvas.width / 2, canvas.height / 2, 0,
                canvas.width / 2, canvas.height / 2, canvas.width
            );
            gradient.addColorStop(0, '#0a0a0a');
            gradient.addColorStop(1, '#050505');
            ctx.fillStyle = gradient;
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            particles.forEach(particle => {
                particle.update();
                particle.draw();
            });

            particles.forEach((a, i) => {
                particles.slice(i + 1).forEach(b => {
                    const dx = a.x - b.x;
                    const dy = a.y - b.y;
                    const distance = Math.sqrt(dx * dx + dy * dy);

                    if (distance < 100) {
                        ctx.beginPath();
                        ctx.strokeStyle = '#D4AF37';
                        ctx.globalAlpha = 0.1 * (1 - distance / 100);
                        ctx.lineWidth = 0.5;
                        ctx.moveTo(a.x, a.y);
                        ctx.lineTo(b.x, b.y);
                        ctx.stroke();
                        ctx.globalAlpha = 1;
                    }
                });
            });

            requestAnimationFrame(animateParticles);
        }

        window.addEventListener('resize', () => {
            resizeCanvas();
            initParticles();
        });

        resizeCanvas();
        initParticles();
        animateParticles();

        // Page Navigation
        function showPage(pageName) {
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            
            document.getElementById(pageName).classList.add('active');
            
            document.querySelectorAll('.nav-links a').forEach(link => {
                link.classList.remove('active');
            });
            event.target.classList.add('active');
            
            document.getElementById('navLinks').classList.remove('active');
            
            window.scrollTo(0, 0);
        }

        function toggleMobileMenu() {
            document.getElementById('navLinks').classList.toggle('active');
        }

        // Pricing Toggle
        function togglePricing(header) {
            const card = header.parentElement;
            card.classList.toggle('expanded');
        }

        // Book Package from Services Page
        function bookPackage(eventType, classType, tier, price) {
            showPage('book');
            document.getElementById('eventTypeSelect').value = eventType;
            updatePackages();
            
            // Set class
            document.querySelectorAll('.package-tab').forEach(tab => tab.classList.remove('active'));
            document.querySelectorAll('.package-tab').forEach(tab => {
                if (tab.textContent.toLowerCase().includes(classType)) {
                    tab.classList.add('active');
                }
            });
            document.getElementById('selectedClass').value = classType;
            renderPackages();
            
            // Select package
            setTimeout(() => {
                document.querySelectorAll('.package-card').forEach(card => {
                    if (card.dataset.tier === tier) {
                        card.click();
                    }
                });
            }, 100);
            
            document.getElementById('packagePrice').value = price;
            
            return false;
        }

        function selectService(serviceType) {
            showPage('book');
            document.getElementById('eventTypeSelect').value = serviceType;
            updatePackages();
            return false;
        }

        // Palette Data
        const palettes = {
            classic: [
                { name: 'Royal Gold', colors: ['#D4AF37', '#FFFFFF', '#1a1a1a', '#F4E8C1'] },
                { name: 'Classic White', colors: ['#FFFFFF', '#F5F5F5', '#D4AF37', '#E8E8E8'] },
                { name: 'Black Tie', colors: ['#000000', '#FFFFFF', '#D4AF37', '#333333'] },
                { name: 'Champagne', colors: ['#F7E7CE', '#D4AF37', '#FFFFFF', '#C9B99A'] }
            ],
            romantic: [
                { name: 'Blush Pink', colors: ['#F8C8DC', '#FFB6C1', '#FFFFFF', '#D4AF37'] },
                { name: 'Rose Gold', colors: ['#B76E79', '#F4C2C2', '#FFFFFF', '#D4AF37'] },
                { name: 'Dusty Rose', colors: ['#DCAE96', '#C9A9A6', '#F5F5F5', '#8B6F47'] },
                { name: 'Lavender', colors: ['#E6E6FA', '#D8BFD8', '#FFFFFF', '#9370DB'] }
            ],
            modern: [
                { name: 'Navy Gold', colors: ['#000080', '#D4AF37', '#FFFFFF', '#1a1a1a'] },
                { name: 'Emerald', colors: ['#50C878', '#FFFFFF', '#1a1a1a', '#D4AF37'] },
                { name: 'Slate', colors: ['#708090', '#D3D3D3', '#FFFFFF', '#D4AF37'] },
                { name: 'Burgundy', colors: ['#800020', '#FFFFFF', '#D4AF37', '#4a0404'] }
            ],
            earthy: [
                { name: 'Sage', colors: ['#9DC183', '#F5F5DC', '#8B7355', '#FFFFFF'] },
                { name: 'Terracotta', colors: ['#E2725B', '#F4A460', '#FFF8DC', '#8B4513'] },
                { name: 'Forest', colors: ['#228B22', '#8FBC8F', '#F5F5DC', '#8B4513'] },
                { name: 'Harvest', colors: ['#DAA520', '#F4A460', '#8B4513', '#FFFFFF'] }
            ]
        };

        function showPaletteCat(category) {
            document.querySelectorAll('.palette-cat-btn').forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');
            
            const grid = document.getElementById('paletteGrid');
            grid.innerHTML = '';
            
            palettes[category].forEach(palette => {
                const div = document.createElement('div');
                div.className = 'palette-option';
                div.onclick = () => selectPalette(palette.name, palette.colors, div);
                div.innerHTML = `
                    <div class="palette-colors">
                        ${palette.colors.map(c => `<div class="palette-color-block" style="background: ${c}"></div>`).join('')}
                    </div>
                    <div class="palette-name">${palette.name}</div>
                `;
                grid.appendChild(div);
            });
        }

        function selectPalette(name, colors, element) {
            document.querySelectorAll('.palette-option').forEach(el => el.classList.remove('selected'));
            element.classList.add('selected');
            document.getElementById('selectedTheme').value = name;
            document.getElementById('themeColors').value = colors.join(', ');
        }

        showPaletteCat('classic');

        // Pricing Data
        const pricingData = {
            wedding: {
                basic: { basic: 3000000, standard: 5000000, premium: 10000000 },
                middle: { basic: 5000000, standard: 7000000, premium: 10000000 },
                first: { basic: 10000000, standard: 35000000, premium: 100000000 }
            },
            introduction: {
                basic: { basic: 2500000, standard: 3000000, premium: 5000000 },
                middle: { basic: 5000000, standard: 6500000, premium: 10000000 },
                first: { basic: 10000000, standard: 15000000, premium: 50000000 }
            },
            kukyala: {
                basic: { basic: 500000, standard: 1000000, premium: 2000000 },
                middle: { basic: 2000000, standard: 3000000, premium: 4000000 },
                first: { basic: 4000000, standard: 6000000, premium: 10000000 }
            },
            birthday: {
                basic: { basic: 500000, standard: 1000000, premium: 2000000 },
                middle: { basic: 2000000, standard: 3000000, premium: 4000000 },
                first: { basic: 4000000, standard: 6000000, premium: 10000000 }
            },
            'bridal-shower': {
                basic: { basic: 300000, standard: 500000, premium: 1000000 },
                middle: { basic: 1000000, standard: 2000000, premium: 2500000 },
                first: { basic: 3000000, standard: 3700000, premium: 5000000 }
            },
            'baby-shower': {
                basic: { basic: 300000, standard: 500000, premium: 1000000 },
                middle: { basic: 1000000, standard: 2000000, premium: 2500000 },
                first: { basic: 3000000, standard: 3700000, premium: 5000000 }
            },
            kuhingira: {
                basic: { basic: 300000, standard: 500000, premium: 1000000 },
                middle: { basic: 1000000, standard: 2000000, premium: 2500000 },
                first: { basic: 3000000, standard: 3700000, premium: 5000000 }
            }
        };

        function updatePackages() {
            const eventType = document.getElementById('eventTypeSelect').value;
            const section = document.getElementById('packageSection');
            
            if (!eventType || eventType === 'other') {
                section.style.display = 'none';
                return;
            }
            
            section.style.display = 'block';
            renderPackages();
        }

        function setPackageClass(classType) {
            document.querySelectorAll('.package-tab').forEach(tab => tab.classList.remove('active'));
            event.target.classList.add('active');
            document.getElementById('selectedClass').value = classType;
            renderPackages();
        }

        function renderPackages() {
            const eventType = document.getElementById('eventTypeSelect').value;
            const classType = document.getElementById('selectedClass').value;
            
            if (!eventType || !pricingData[eventType]) return;
            
            const prices = pricingData[eventType][classType];
            const container = document.getElementById('packageCards');
            container.innerHTML = '';
            
            const features = {
                basic: ['Essential setup', 'Standard florals', 'Basic lighting'],
                standard: ['Enhanced setup', 'Premium florals', 'Advanced lighting', 'Coordinator'],
                premium: ['Luxury setup', 'Exquisite florals', 'Premium effects', 'Design team', 'Priority support']
            };
            
            Object.entries(prices).forEach(([tier, price]) => {
                const card = document.createElement('div');
                card.className = 'package-card';
                card.dataset.tier = tier;
                card.onclick = () => selectPackage(tier, price, card);
                
                const formattedPrice = new Intl.NumberFormat('en-UG').format(price);
                
                card.innerHTML = `
                    <div class="package-tier-name">${tier}</div>
                    <div class="package-price">UGX ${formattedPrice}</div>
                    <ul style="list-style: none; font-size: 0.85rem; color: rgba(255,255,255,0.7); text-align: left; padding: 0;">
                        ${features[tier].map(f => `<li style="margin: 0.3rem 0;">✓ ${f}</li>`).join('')}
                    </ul>
                `;
                
                container.appendChild(card);
            });
        }

        function selectPackage(tier, price, element) {
            document.querySelectorAll('.package-card').forEach(card => card.classList.remove('selected'));
            element.classList.add('selected');
            document.getElementById('selectedPackage').value = tier;
            document.getElementById('packagePrice').value = price;
        }

        function submitToWhatsApp(e) {
            e.preventDefault();
            
            const formData = new FormData(e.target);
            let message = "🎉 NEW EVENT BOOKING REQUEST 🎉\n\n";
            
            message += `👤 Name: ${formData.get('fullname')}\n`;
            message += `📞 Phone: ${formData.get('phone')}\n`;
            message += `📧 Email: ${formData.get('email')}\n`;
            message += `🎊 Event: ${formData.get('eventType')}\n\n`;
            
            if (formData.get('selectedTheme')) {
                message += `🎨 Theme: ${formData.get('selectedTheme')}\n`;
                message += `🌈 Colors: ${formData.get('themeColors')}\n\n`;
            }
            
            if (formData.get('selectedPackage')) {
                const className = formData.get('selectedClass').charAt(0).toUpperCase() + formData.get('selectedClass').slice(1);
                const tier = formData.get('selectedPackage').charAt(0).toUpperCase() + formData.get('selectedPackage').slice(1);
                const price = new Intl.NumberFormat('en-UG').format(formData.get('packagePrice'));
                message += `💎 Package: ${className} Class - ${tier}\n`;
                message += `💰 Price: UGX ${price}\n\n`;
            }
            
            message += `📅 Date: ${formData.get('eventDate')}\n`;
            message += `⏰ Time: ${formData.get('eventTime')}\n`;
            message += `🏛️ Venue Type: ${formData.get('venueType')}\n`;
            message += `👥 Guests: ${formData.get('guestCount')}\n`;
            message += `📍 Location: ${formData.get('venueAddress')}\n\n`;
            message += `📝 Details: ${formData.get('details') || 'None'}\n\n`;
            message += "Sent from Opulent Decor Website";
            
            window.open(`https://wa.me/256751215607?text=${encodeURIComponent(message)}`, '_blank');
        }

        document.querySelector('[name="eventDate"]').min = new Date().toISOString().split('T')[0];
    </script>
</body>
</html>

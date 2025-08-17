
I'll create a modern, responsive e-commerce website for selling vegetable seeds with all the requested features. Since the request is for a single HTML file with HTML, CSS, and JavaScript, I'll implement a complete frontend solution that simulates backend functionality using localStorage for persistence. This will include:

1. Professional design with green/earthy color scheme
2. Responsive layout with mobile-first approach
3. Product categories with filtering
4. Shopping cart functionality
5. Fake authentication system (since we can't do real backend)
6. All requested pages with navigation
7. WhatsApp integration via link (since we can't actually implement backend)
8. SEO-friendly meta tags


`vegetable_seeds_ecommerce.html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Fresh & healthy vegetable seeds for your garden. Organic, non-GMO seeds for tomatoes, carrots, herbs, and more. Fast shipping and expert growing advice.">
    <meta name="keywords" content="vegetable seeds, garden seeds, organic seeds, tomato seeds, herb seeds, gardening supplies">
    <title>GreenSprout Seeds | Organic Vegetable Seeds</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&family=Playfair+Display:wght@400;500;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #3a7d44;
            --primary-dark: #2d6135;
            --primary-light: #5e9c66;
            --secondary: #e9c46a;
            --dark: #264653;
            --light: #f8f9fa;
            --gray: #6c757d;
            --white: #ffffff;
            --black: #212529;
            --success: #28a745;
            --warning: #ffc107;
            --danger: #dc3545;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            color: var(--dark);
            line-height: 1.6;
            background-color: var(--light);
        }

        h1, h2, h3, h4 {
            font-family: 'Playfair Display', serif;
            margin-bottom: 1rem;
        }

        a {
            text-decoration: none;
            color: var(--primary);
            transition: all 0.3s ease;
        }

        a:hover {
            color: var(--primary-dark);
        }

        button, .btn {
            background-color: var(--primary);
            color: var(--white);
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s ease;
            display: inline-block;
        }

        button:hover, .btn:hover {
            background-color: var(--primary-dark);
            transform: translateY(-2px);
        }

        .btn-outline {
            background-color: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
        }

        .btn-outline:hover {
            background-color: var(--primary);
            color: var(--white);
        }

        .btn-warning {
            background-color: var(--warning);
            color: var(--dark);
        }

        .btn-danger {
            background-color: var(--danger);
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 1rem;
        }

        /* Header */
        header {
            background-color: var(--white);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
            font-family: 'Playfair Display', serif;
            display: flex;
            align-items: center;
        }

        .logo img {
            height: 40px;
            margin-right: 0.5rem;
        }

        nav ul {
            display: flex;
            list-style: none;
        }

        nav ul li {
            margin-left: 1.5rem;
        }

        nav ul li a {
            font-weight: 500;
            color: var(--black);
            padding: 0.5rem 0;
            position: relative;
        }

        nav ul li a:after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            background-color: var(--primary);
            bottom: 0;
            left: 0;
            transition: width 0.3s ease;
        }

        nav ul li a:hover:after {
            width: 100%;
        }

        .header-right {
            display: flex;
            align-items: center;
        }

        .search-bar {
            position: relative;
            margin-right: 1rem;
        }

        .search-bar input {
            padding: 0.5rem 1rem;
            padding-right: 2.5rem;
            border: 1px solid var(--gray);
            border-radius: 4px;
            width: 200px;
        }

        .search-bar button {
            position: absolute;
            right: 0;
            top: 0;
            height: 100%;
            width: 2.5rem;
            background: none;
            color: var(--gray);
            padding: 0;
            border: none;
        }

        .cart-icon, .user-icon {
            margin-left: 1rem;
            position: relative;
            cursor: pointer;
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background-color: var(--danger);
            color: var(--white);
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.75rem;
            font-weight: 600;
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 1.5rem;
            color: var(--dark);
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url('https://placehold.co/1600x900') no-repeat center center/cover;
            height: 60vh;
            display: flex;
            align-items: center;
            color: var(--white);
            text-align: center;
            margin-bottom: 3rem;
        }

        .hero-content {
            max-width: 800px;
            margin: 0 auto;
            padding: 2rem;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1.5rem;
        }

        .hero p {
            font-size: 1.25rem;
            margin-bottom: 2rem;
        }

        /* Categories */
        .categories {
            padding: 3rem 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 2rem;
        }

        .category-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
        }

        .category-card {
            background-color: var(--white);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }

        .category-card:hover {
            transform: translateY(-5px);
        }

        .category-img {
            height: 150px;
            overflow: hidden;
        }

        .category-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .category-card:hover .category-img img {
            transform: scale(1.05);
        }

        .category-info {
            padding: 1.5rem;
            text-align: center;
        }

        .category-info h3 {
            margin-bottom: 0.5rem;
        }

        /* Featured Products */
        .featured-products {
            padding: 3rem 0;
            background-color: var(--white);
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }

        .product-card {
            background-color: var(--light);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
        }

        .product-img {
            height: 200px;
            overflow: hidden;
            position: relative;
        }

        .product-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .product-card:hover .product-img img {
            transform: scale(1.05);
        }

        .product-badge {
            position: absolute;
            top: 1rem;
            left: 1rem;
            background-color: var(--success);
            color: var(--white);
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            font-size: 0.75rem;
            font-weight: 600;
        }

        .product-info {
            padding: 1.5rem;
        }

        .product-title {
            font-size: 1.25rem;
            margin-bottom: 0.5rem;
        }

        .product-price {
            font-weight: 700;
            color: var(--primary);
            font-size: 1.25rem;
            margin-bottom: 1rem;
            display: block;
        }

        .product-price .old-price {
            text-decoration: line-through;
            color: var(--gray);
            font-size: 1rem;
            margin-left: 0.5rem;
        }

        .product-stock {
            display: flex;
            align-items: center;
            margin-bottom: 1rem;
        }

        .stock-status {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            margin-right: 0.5rem;
        }

        .in-stock {
            background-color: var(--success);
        }

        .low-stock {
            background-color: var(--warning);
        }

        .out-of-stock {
            background-color: var(--danger);
        }

        .product-actions {
            display: flex;
            gap: 0.5rem;
        }

        /* About Section */
        .about {
            padding: 3rem 0;
            background-color: var(--light);
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;
        }

        .about-img {
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
        }

        .about-img img {
            width: 100%;
            height: auto;
            display: block;
        }

        /* Newsletter */
        .newsletter {
            padding: 3rem 0;
            background-color: var(--primary);
            color: var(--white);
            text-align: center;
        }

        .newsletter h2 {
            color: var(--white);
        }

        .newsletter-form {
            max-width: 600px;
            margin: 0 auto;
            display: flex;
        }

        .newsletter-form input {
            flex: 1;
            padding: 0.75rem 1rem;
            border: none;
            border-radius: 4px 0 0 4px;
            font-size: 1rem;
        }

        .newsletter-form button {
            border-radius: 0 4px 4px 0;
        }

        /* Footer */
        footer {
            background-color: var(--dark);
            color: var(--white);
            padding: 3rem 0 1rem;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .footer-column h3 {
            color: var(--white);
            margin-bottom: 1.5rem;
            font-size: 1.25rem;
        }

        .footer-column ul {
            list-style: none;
        }

        .footer-column ul li {
            margin-bottom: 0.75rem;
        }

        .footer-column ul li a {
            color: rgba(255, 255, 255, 0.7);
        }

        .footer-column ul li a:hover {
            color: var(--white);
        }

        .social-links {
            display: flex;
            gap: 1rem;
        }

        .social-links a {
            font-size: 1.25rem;
            color: var(--white);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            font-size: 0.875rem;
            color: rgba(255, 255, 255, 0.7);
        }

        /* Page transitions */
        .page {
            display: none;
        }

        .page.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Product Page */
        .product-page {
            padding: 3rem 0;
        }

        .product-detail {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            margin-bottom: 3rem;
        }

        .product-gallery {
            display: grid;
            grid-template-columns: 80px 1fr;
            gap: 1rem;
        }

        .product-thumbnails {
            display: flex;
            flex-direction: column;
            gap: 1rem;
       

# JAGUA-SHOP
Jagua Shop – Online grocery store website built with HTML, CSS and JavaScript.
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>জাগুয়া শপ - সম্পূর্ণ দোকান</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Hind Siliguri', sans-serif;
        }

        body {
            background: #f5f7fa;
            padding: 15px 15px 90px 15px;
            min-height: 100vh;
        }

        /* হেডার */
        .header {
            background: #1a4d2e;
            color: white;
            padding: 20px 15px;
            border-radius: 30px;
            text-align: center;
            margin-bottom: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .header h1 {
            font-size: 36px;
            font-weight: 800;
        }

        .header p {
            font-size: 15px;
            opacity: 0.9;
        }

        /* সার্চ */
        .search-container {
            margin-bottom: 15px;
            position: relative;
        }

        .search-container input {
            width: 100%;
            padding: 15px 20px 15px 50px;
            border: none;
            border-radius: 50px;
            background: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            font-size: 16px;
            border: 1px solid #ddd;
        }

        .search-container::before {
            content: '🔍';
            position: absolute;
            left: 20px;
            top: 50%;
            transform: translateY(-50%);
            font-size: 18px;
            color: #1a4d2e;
        }

        /* ক্যাটাগরি */
        .categories {
            display: flex;
            gap: 8px;
            overflow-x: auto;
            padding: 5px 0 15px 0;
            margin-bottom: 5px;
            scrollbar-width: none;
        }

        .categories::-webkit-scrollbar {
            display: none;
        }

        .cat-btn {
            background: white;
            border: 1px solid #ddd;
            padding: 10px 20px;
            border-radius: 40px;
            font-weight: 600;
            font-size: 14px;
            color: #1a4d2e;
            white-space: nowrap;
            cursor: pointer;
        }

        .cat-btn.active {
            background: #1a4d2e;
            color: white;
            border-color: #1a4d2e;
        }

        /* স্ট্যাটস ও ডেলিভারি */
        .stats {
            background: white;
            padding: 12px 18px;
            border-radius: 40px;
            margin-bottom: 15px;
            display: flex;
            justify-content: space-between;
            font-weight: 600;
            border: 1px solid #eee;
        }

        .delivery {
            background: linear-gradient(135deg, #1a4d2e, #2e7d32);
            color: white;
            padding: 12px 18px;
            border-radius: 50px;
            margin-bottom: 20px;
            text-align: center;
            font-weight: 600;
            border: 1px solid #ffd700;
        }

        .delivery span {
            background: #ffd700;
            color: #1a4d2e;
            padding: 3px 12px;
            border-radius: 40px;
            margin: 0 5px;
        }

        /* প্রোডাক্ট গ্রিড */
        .products {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
            margin-bottom: 20px;
        }

        @media (min-width: 768px) {
            .products {
                grid-template-columns: repeat(3, 1fr);
            }
        }
        @media (min-width: 1024px) {
            .products {
                grid-template-columns: repeat(4, 1fr);
            }
        }

        /* প্রোডাক্ট কার্ড */
        .product-card {
            background: white;
            border-radius: 25px;
            padding: 15px 12px;
            border: 1px solid #eee;
            box-shadow: 0 3px 10px rgba(0,0,0,0.03);
            position: relative;
        }

        .product-image {
            width: 100%;
            height: 120px;
            object-fit: cover;
            border-radius: 20px;
            margin-bottom: 10px;
            background: #f0f8f0;
        }

        .product-name {
            font-weight: 700;
            font-size: 15px;
            color: #1a2e1a;
            height: 42px;
            overflow: hidden;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            margin-bottom: 5px;
        }

        .product-price {
            font-size: 20px;
            font-weight: 800;
            color: #1a4d2e;
            margin: 5px 0;
        }

        .product-unit {
            background: #f0f8f0;
            padding: 3px 10px;
            border-radius: 30px;
            font-size: 12px;
            display: inline-block;
        }

        .details-btn {
            position: absolute;
            top: 10px;
            right: 10px;
            width: 30px;
            height: 30px;
            background: white;
            border: 1px solid #1a4d2e;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 16px;
            cursor: pointer;
        }

        .qty-control {
            display: flex;
            align-items: center;
            gap: 5px;
            background: #f8faf8;
            border-radius: 40px;
            padding: 4px;
            border: 1px solid #1a4d2e;
            margin: 12px 0 8px;
        }

        .qty-btn {
            width: 34px;
            height: 34px;
            border: none;
            background: #1a4d2e;
            color: white;
            font-size: 18px;
            border-radius: 50%;
            cursor: pointer;
        }

        .qty-value {
            flex: 1;
            text-align: center;
            font-weight: 700;
            color: #1a4d2e;
        }

        .presets {
            display: flex;
            gap: 4px;
            flex-wrap: wrap;
            margin-bottom: 10px;
        }

        .preset {
            background: #f0f8f0;
            border: 1px solid #1a4d2e;
            color: #1a4d2e;
            padding: 5px 8px;
            border-radius: 30px;
            font-size: 11px;
            cursor: pointer;
            flex: 1;
            min-width: 35px;
            text-align: center;
        }

        .add-btn {
            background: #1a4d2e;
            color: white;
            border: none;
            padding: 12px;
            width: 100%;
            border-radius: 40px;
            font-weight: 700;
            font-size: 14px;
            cursor: pointer;
        }

        /* ফ্লোটিং কার্ট */
        .floating-cart {
            position: fixed;
            bottom: 15px;
            left: 15px;
            right: 15px;
            background: #1a4d2e;
            border-radius: 60px;
            padding: 15px 25px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            color: white;
            font-weight: 700;
            border: 2px solid #ffd700;
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
            cursor: pointer;
            z-index: 100;
        }

        .cart-badge {
            background: #ffd700;
            color: #1a4d2e;
            padding: 5px 25px;
            border-radius: 40px;
        }

        /* পেজিনেশন */
        .pagination {
            display: flex;
            justify-content: center;
            gap: 8px;
            margin: 20px 0;
            flex-wrap: wrap;
        }

        .page-btn {
            background: white;
            border: 1px solid #ddd;
            border-radius: 20px;
            padding: 8px 16px;
            font-weight: 600;
            min-width: 44px;
            text-align: center;
            cursor: pointer;
        }

        .page-btn.active {
            background: #1a4d2e;
            color: white;
            border-color: #1a4d2e;
        }

        /* মোডাল */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.4);
            padding: 15px;
            z-index: 200;
            overflow-y: auto;
        }

        .modal-content {
            background: white;
            border-radius: 40px;
            max-width: 450px;
            margin: 30px auto;
            padding: 25px;
            border: 2px solid #1a4d2e;
        }

        .close {
            float: right;
            font-size: 30px;
            cursor: pointer;
            width: 40px;
            height: 40px;
            background: #f0f0f0;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* পেমেন্ট */
        .payment-option {
            padding: 16px;
            border-radius: 40px;
            text-align: center;
            cursor: pointer;
            margin-bottom: 12px;
            font-weight: 700;
            border: 2px solid transparent;
        }

        .payment-option.bkash {
            border-color: #ff69b4;
            background: #fff0f5;
            color: #ff1493;
        }

        .payment-option.bkash.selected {
            background: #ffe4f0;
        }

        .payment-option.cod {
            border-color: #1a4d2e;
            background: #f0f8f0;
            color: #1a4d2e;
        }

        .payment-option.cod.selected {
            background: #e8f5e9;
        }

        .delivery-option {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 14px 18px;
            border: 1px solid #ddd;
            border-radius: 40px;
            margin: 8px 0;
            cursor: pointer;
            background: white;
        }

        .delivery-option.selected {
            border-color: #1a4d2e;
            background: #f0f8f0;
        }

        .delivery-option.free.selected {
            border-color: #ffd700;
        }

        .delivery-option.disabled {
            opacity: 0.4;
            pointer-events: none;
        }

        .summary {
            background: #f8faf8;
            padding: 16px;
            border-radius: 30px;
            margin: 15px 0;
            border: 1px solid #1a4d2e;
        }

        .summary-item {
            display: flex;
            justify-content: space-between;
            padding: 8px 0;
            border-bottom: 1px solid #eee;
        }

        .summary-total {
            font-size: 22px;
            font-weight: 800;
            color: #1a4d2e;
            text-align: right;
            padding-top: 8px;
        }

        .order-id {
            background: #1a4d2e;
            color: white;
            padding: 10px;
            border-radius: 40px;
            text-align: center;
            margin: 15px 0;
        }

        .input-field {
            width: 100%;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 40px;
            margin-bottom: 12px;
            font-size: 15px;
        }

        .confirm-btn {
            background: #1a4d2e;
            color: white;
            border: none;
            padding: 18px;
            width: 100%;
            border-radius: 50px;
            font-size: 17px;
            font-weight: 700;
            cursor: pointer;
        }

        .toast {
            position: fixed;
            bottom: 100px;
            left: 15px;
            right: 15px;
            background: #1a4d2e;
            color: white;
            padding: 15px;
            border-radius: 50px;
            text-align: center;
            display: none;
            z-index: 300;
            border: 1px solid #ffd700;
            max-width: 350px;
            margin: 0 auto;
        }

        .help-section {
            background: white;
            border-radius: 40px;
            padding: 20px 15px;
            margin: 25px 0;
            text-align: center;
            border: 1px solid #eee;
        }

        .help-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
        }

        .help-card {
            background: #f8faf8;
            border-radius: 30px;
            padding: 15px 8px;
            border: 1px solid #ddd;
        }

        .help-card a {
            text-decoration: none;
            color: inherit;
        }

        .help-card h4 {
            color: #1a4d2e;
            font-size: 15px;
            margin-bottom: 3px;
        }

        .help-btn {
            background: #1a4d2e;
            color: white;
            padding: 5px 10px;
            border-radius: 30px;
            font-size: 11px;
            display: inline-block;
        }

        .footer {
            background: white;
            padding: 20px;
            border-radius: 40px;
            text-align: center;
            border: 1px solid #eee;
        }

        /* অ্যাডমিন */
        .admin-panel {
            background: white;
            border-radius: 40px;
            padding: 20px;
            border: 2px solid #1a4d2e;
        }

        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .admin-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
            gap: 15px;
        }

        .admin-card {
            background: #f8faf8;
            border-radius: 30px;
            padding: 12px;
            border: 1px solid #ddd;
        }

        .admin-card img {
            width: 100%;
            height: 100px;
            object-fit: cover;
            border-radius: 20px;
        }

        .admin-input {
            width: 100%;
            padding: 6px 10px;
            border: 1px solid #ddd;
            border-radius: 20px;
            margin-bottom: 6px;
        }

        .admin-save {
            background: #1a4d2e;
            color: white;
            border: none;
            padding: 8px;
            width: 100%;
            border-radius: 30px;
            cursor: pointer;
        }

        .login-box {
            max-width: 360px;
            margin: 80px auto;
            background: white;
            border-radius: 40px;
            padding: 25px;
            border: 2px solid #1a4d2e;
        }

        .spinner {
            width: 40px;
            height: 40px;
            border: 4px solid #eee;
            border-top: 4px solid #1a4d2e;
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 20px auto;
        }

        @keyframes spin { to { transform: rotate(360deg); } }
    </style>
</head>
<body>

<div id="app">
    <div style="display: flex; justify-content: center; align-items: center; height: 80vh;">
        <div class="spinner"></div>
    </div>
</div>

<script>
(function() {
    // ---------- প্রোডাক্ট ডাটা ----------
    const baseProducts = [
        { id: 1, code: 'R-001', name: 'নাজিরশাইল চাল', category: 'চাল', price: 85, unit: 'কেজি', minQty: 0.5, maxQty: 50, step: 0.5, image: 'https://images.pexels.com/photos/4110254/pexels-photo-4110254.jpeg?auto=compress&cs=tinysrgb&w=300', desc: 'সুবাসিত নাজিরশাইল চাল' },
        { id: 2, code: 'R-002', name: 'মিনিকেট চাল', category: 'চাল', price: 75, unit: 'কেজি', minQty: 0.5, maxQty: 50, step: 0.5, image: 'https://images.pexels.com/photos/4198605/pexels-photo-4198605.jpeg?auto=compress&cs=tinysrgb&w=300', desc: 'মিনিকেট চাল' },
        { id: 3, code: 'R-003', name: 'পোলাও চাল', category: 'চাল', price: 120, unit: 'কেজি', minQty: 0.5, maxQty: 5, step: 0.5, image: 'https://images.pexels.com/photos/4198573/pexels-photo-4198573.jpeg?auto=compress&cs=tinysrgb&w=300', desc: 'পোলাও চাল' },
        { id: 4, code: 'D-001', name: 'মসুর ডাল', category: 'ডাল', price: 110, unit: 'কেজি', minQty: 0.5, maxQty: 20, step: 0.5, image: 'https://images.pexels.com/photos/4110248/pexels-photo-4110248.jpeg?auto=compress&cs=tinysrgb&w=300', desc: 'মসুর ডাল' },
        { id: 5, code: 'O-001', name: 'সয়াবিন তেল', category: 'তেল', price: 180, unit: 'লিটার', minQty: 1, maxQty: 20, step: 1, image: 'https://images.pexels.com/photos/4198615/pexels-photo-4198615.jpeg?auto=compress&cs=tinysrgb&w=300', desc: 'সয়াবিন তেল' },
        { id: 6, code: 'S-001', name: 'হলুদ গুঁড়া', category: 'মসলা', price: 80, unit: '২০০ গ্রাম', minQty: 1, maxQty: 20, step: 1, image: 'https://images.pexels.com/photos/4198535/pexels-photo-4198535.jpeg?auto=compress&cs=tinysrgb&w=300', desc: 'হলুদ গুঁড়া' },
        { id: 7, code: 'A-001', name: 'আটা', category: 'আটা', price: 60, unit: 'কেজি', minQty: 0.5, maxQty: 50, step: 0.5, image: 'https://images.pexels.com/photos/4198485/pexels-photo-4198485.jpeg?auto=compress&cs=tinysrgb&w=300', desc: 'আটা' },
        { id: 8, code: 'E-001', name: 'দেশি ডিম', category: 'ডিম', price: 45, unit: 'হালি (৪টি)', minQty: 1, maxQty: 25, step: 1, image: 'https://images.pexels.com/photos/162712/egg-white-eggs-shell-egg-shells-162712.jpeg?auto=compress&cs=tinysrgb&w=300', desc: 'দেশি ডিম' }
    ];

    // ১০০ পণ্য জেনারেট
    let products = JSON.parse(localStorage.getItem('jagua_products')) || (() => {
        let prods = [];
        for (let i = 0; i < 100; i++) {
            let base = baseProducts[i % baseProducts.length];
            prods.push({
                ...base,
                id: i + 1,
                code: base.code + '-' + (i+1),
                name: `${base.name} ${Math.floor(i/10)+1}`,
                price: base.price + (i % 15) * 2
            });
        }
        return prods;
    })();

    let cart = JSON.parse(localStorage.getItem('jagua_cart')) || [];
    let categories = ['সব', ...new Set(products.map(p => p.category))];
    let isAdmin = window.location.hash === '#admin';
    let isLoggedIn = localStorage.getItem('jagua_admin') === 'true';
    let currentPage = 1;
    let perPage = 8;
    let currentCat = 'সব';
    let searchTerm = '';
    let quantities = {};
    products.forEach(p => quantities[p.id] = p.minQty || 1);

    let selectedPayment = 'bkash';
    let selectedDelivery = 'paid';

    // লোডিং সিমুলেট
    setTimeout(() => render(), 300);

    function render() {
        if (isAdmin) {
            if (isLoggedIn) renderAdmin();
            else renderLogin();
        } else {
            renderShop();
        }
    }

    function showDetails(product) {
        let modal = document.createElement('div');
        modal.className = 'modal';
        modal.style.display = 'block';
        modal.innerHTML = `
            <div class="modal-content">
                <span class="close" onclick="this.closest('.modal').remove()">&times;</span>
                <h3 style="color:#1a4d2e;">পণ্যের বিবরণ</h3>
                <div style="padding:8px 0;"><strong>কোড:</strong> ${product.code}</div>
                <div style="padding:8px 0;"><strong>নাম:</strong> ${product.name}</div>
                <div style="padding:8px 0;"><strong>ক্যাটাগরি:</strong> ${product.category}</div>
                <div style="padding:8px 0;"><strong>দাম:</strong> ৳${product.price} / ${product.unit}</div>
                <div style="padding:8px 0;"><strong>বিবরণ:</strong> ${product.desc}</div>
            </div>
        `;
        document.body.appendChild(modal);
    }

    function renderShop() {
        let filtered = products.filter(p => {
            if (currentCat !== 'সব' && p.category !== currentCat) return false;
            if (searchTerm && !p.name.toLowerCase().includes(searchTerm.toLowerCase())) return false;
            return true;
        });

        let totalPages = Math.ceil(filtered.length / perPage);
        if (currentPage > totalPages) currentPage = totalPages || 1;
        let start = (currentPage - 1) * perPage;
        let end = start + perPage;
        let pageProds = filtered.slice(start, end);

        let productCards = '';
        for (let p of pageProds) {
            let presets = [];
            if (p.category === 'চাল') {
                if (p.name.includes('পোলাও')) presets = [0.5,1,2,3,5];
                else presets = [0.5,1,2,5,10,25,50];
            } else if (p.category === 'ডাল' || p.category === 'আটা') presets = [0.5,1,2,5];
            else if (p.category === 'তেল') presets = [1,2,3,5];
            else presets = [1,2,3,5];

            let presetBtns = '';
            for (let v of presets) {
                if (v <= (p.maxQty || 100)) {
                    presetBtns += `<span class="preset" onclick="setQty(${p.id}, ${v})">${v}</span>`;
                }
            }

            productCards += `
                <div class="product-card">
                    <span class="details-btn" onclick="showDetails(${JSON.stringify(p).replace(/"/g, '&quot;')})">ⓘ</span>
                    <img src="${p.image}" class="product-image" onerror="this.src='https://via.placeholder.com/300?text=Product'">
                    <div class="product-name">${p.name}</div>
                    <div class="product-price">৳${p.price} <span class="product-unit">/${p.unit}</span></div>
                    <div class="qty-control">
                        <button class="qty-btn" onclick="decQty(${p.id})">−</button>
                        <span class="qty-value" id="qty_${p.id}">${quantities[p.id] || 1}</span>
                        <button class="qty-btn" onclick="incQty(${p.id})">+</button>
                    </div>
                    <div class="presets">${presetBtns}</div>
                    <button class="add-btn" onclick="addToCart(${p.id})">কার্টে যোগ করুন</button>
                </div>
            `;
        }

        let catBtns = '';
        for (let cat of categories) {
            catBtns += `<span class="cat-btn ${cat === currentCat ? 'active' : ''}" onclick="filterCat('${cat}')">${cat}</span>`;
        }

        let pageBtns = '';
        for (let i = 1; i <= totalPages; i++) {
            pageBtns += `<span class="page-btn ${i === currentPage ? 'active' : ''}" onclick="goToPage(${i})">${i}</span>`;
        }

        document.getElementById('app').innerHTML = `
            <div>
                <div class="header">
                    <h1>জাগুয়া শপ</h1>
                    <p>দ্রুত ডেলিভারি • ফ্রেশ প্রোডাক্ট</p>
                </div>
                <div class="search-container">
                    <input type="text" id="searchInput" placeholder="পণ্য খুঁজুন..." value="${searchTerm}">
                </div>
                <div class="categories">${catBtns}</div>
                <div class="stats">
                    <span>📦 মোট: ${filtered.length}</span>
                    <span>📄 ${currentPage}/${totalPages}</span>
                </div>
                <div class="delivery">
                    🚚 ডেলিভারি <span>৪০</span> | ৩০০০+ <span>ফ্রি</span>
                </div>
                <div class="products">${productCards}</div>
                <div class="pagination">
                    <span class="page-btn" onclick="changePage(-1)" ${currentPage===1?'disabled':''}>‹</span>
                    ${pageBtns}
                    <span class="page-btn" onclick="changePage(1)" ${currentPage===totalPages?'disabled':''}>›</span>
                </div>
                <div class="help-section">
                    <h3>যোগাযোগ</h3>
                    <div class="help-grid">
                        <div class="help-card"><a href="mailto:nahidvuiya75@gmail.com"><h4>ইমেইল</h4><p>nahidvuiya75</p><span class="help-btn">ইমেইল</span></a></div>
                        <div class="help-card"><a href="https://www.facebook.com/nahidvuiya75" target="_blank"><h4>ফেসবুক</h4><p>nahidvuiya75</p><span class="help-btn">ফেসবুক</span></a></div>
                        <div class="help-card"><a href="https://wa.me/8801776084491" target="_blank"><h4>হোয়াটসঅ্যাপ</h4><p>01776084491</p><span class="help-btn">হোয়াটসঅ্যাপ</span></a></div>
                        <div class="help-card"><a href="tel:01776084491"><h4>হেল্পলাইন</h4><p>01776084491</p><span class="help-btn">কল</span></a></div>
                    </div>
                </div>
                <div style="text-align:center; margin:15px 0;">
                    <a href="#admin" style="background:#1a4d2e; color:white; padding:12px 30px; border-radius:60px; text-decoration:none;">⚙️ অ্যাডমিন</a>
                </div>
                <div class="floating-cart" onclick="showCart()">
                    <span>🛒 আমার কার্ট</span>
                    <span class="cart-badge" id="cartCount">${cart.length}</span>
                </div>
                <div class="footer">
                    <p>nahidvuiya75@gmail.com | 01776084491</p>
                </div>
            </div>
            <div class="modal" id="cartModal"><div class="modal-content" id="cartContent"></div></div>
            <div class="modal" id="orderModal"><div class="modal-content" id="orderContent"></div></div>
            <div class="toast" id="toast"></div>
        `;

        document.getElementById('searchInput')?.addEventListener('input', e => {
            searchTerm = e.target.value;
            currentPage = 1;
            renderShop();
        });
    }

    // ---------- গ্লোবাল ফাংশন ----------
    window.setQty = function(id, val) {
        let p = products.find(p => p.id === id);
        if (val >= (p.minQty || 1) && val <= (p.maxQty || 100)) {
            quantities[id] = val;
            document.getElementById(`qty_${id}`).innerText = val;
        }
    };
    window.incQty = function(id) {
        let p = products.find(p => p.id === id);
        let step = p.step || 1;
        if (!quantities[id]) quantities[id] = p.minQty || 1;
        if (quantities[id] < (p.maxQty || 100)) {
            quantities[id] = Math.round((quantities[id] + step) * 100) / 100;
            document.getElementById(`qty_${id}`).innerText = quantities[id];
        }
    };
    window.decQty = function(id) {
        let p = products.find(p => p.id === id);
        let step = p.step || 1;
        if (!quantities[id]) quantities[id] = p.minQty || 1;
        if (quantities[id] > (p.minQty || 1)) {
            quantities[id] = Math.round((quantities[id] - step) * 100) / 100;
            document.getElementById(`qty_${id}`).innerText = quantities[id];
        }
    };
    window.addToCart = function(id) {
        let p = products.find(p => p.id === id);
        let qty = quantities[id] || 1;
        let exist = cart.find(item => item.id === id);
        if (exist) exist.qty += qty;
        else cart.push({ id, name: p.name, price: p.price, qty, unit: p.unit, code: p.code });
        localStorage.setItem('jagua_cart', JSON.stringify(cart));
        document.getElementById('cartCount').innerText = cart.length;
        showToast(p.name + ' যোগ হয়েছে');
    };
    window.filterCat = function(cat) { currentCat = cat; currentPage = 1; renderShop(); };
    window.goToPage = function(p) { currentPage = p; renderShop(); window.scrollTo({ top: 0 }); };
    window.changePage = function(dir) {
        let total = Math.ceil(products.length / perPage);
        if (dir === -1 && currentPage > 1) currentPage--;
        else if (dir === 1 && currentPage < total) currentPage++;
        renderShop(); window.scrollTo({ top: 0 });
    };
    window.showCart = function() {
        let total = 0, html = '';
        for (let i = 0; i < cart.length; i++) {
            total += cart[i].price * cart[i].qty;
            html += `
                <div style="display:flex; align-items:center; gap:8px; padding:10px 0; border-bottom:1px solid #ddd;">
                    <div style="width:40px; height:40px; background:#e8f5e9; border-radius:12px;"></div>
                    <div style="flex:1;">
                        <div style="font-weight:bold;">${cart[i].name}</div>
                        <div>৳${cart[i].price} x ${cart[i].qty}</div>
                    </div>
                    <button class="qty-btn" onclick="removeFromCart(${i})" style="background:#dc3545;">সরান</button>
                </div>
            `;
        }
        document.getElementById('cartContent').innerHTML = `
            <span class="close" onclick="closeModal('cartModal')">&times;</span>
            <h3 style="color:#1a4d2e;">আপনার কার্ট</h3>
            ${html || '<p style="text-align:center;">কার্ট খালি</p>'}
            <div class="summary-total">মোট: ৳${total}</div>
            <button class="confirm-btn" onclick="showCheckout()">অর্ডার সম্পন্ন করুন</button>
        `;
        document.getElementById('cartModal').style.display = 'block';
    };
    window.removeFromCart = function(i) { cart.splice(i,1); localStorage.setItem('jagua_cart',JSON.stringify(cart)); document.getElementById('cartCount').innerText = cart.length; showCart(); };

    function generateOrderId() {
        return 'ORD-' + Date.now().toString(36).toUpperCase();
    }

    window.showCheckout = function() {
        if (cart.length === 0) return showToast('কার্ট খালি!');
        let orderId = generateOrderId();
        let subtotal = cart.reduce((s,i) => s + i.price * i.qty, 0);
        document.getElementById('orderContent').innerHTML = `
            <span class="close" onclick="closeModal('orderModal')">&times;</span>
            <h3 style="color:#1a4d2e;">অর্ডার কনফার্মেশন</h3>
            <div class="payment-option bkash selected" id="bkashOpt" onclick="selectPayment('bkash')">বিকাশ</div>
            <div class="payment-option cod" id="codOpt" onclick="selectPayment('cod')">ক্যাশ অন</div>
            <div class="delivery-option selected" id="paidDel" onclick="selectDelivery('paid')">পেইড (৪০ টাকা)</div>
            <div class="delivery-option free" id="freeDel" onclick="selectDelivery('free')">ফ্রি (০ টাকা) <span style="background:#ffd700; padding:2px 8px; border-radius:30px;">সেভ</span></div>
            <div class="summary" id="deliveryNote"></div>
            <div class="summary">
                <div class="summary-item">পণ্যের মূল্য: <span id="subtotal">৳${subtotal}</span></div>
                <div class="summary-item">ডেলিভারি: <span id="deliveryCharge">৳40</span></div>
                <div class="summary-total">মোট: <span id="totalAmount">৳${subtotal+40}</span></div>
            </div>
            <div class="order-id">অর্ডার আইডি: ${orderId}</div>
            <div id="bkashFields"><input class="input-field" id="trxId" placeholder="বিকাশ TrxID"></div>
            <input class="input-field" id="custName" placeholder="আপনার নাম">
            <input class="input-field" id="custAddress" placeholder="ঠিকানা">
            <input class="input-field" id="custPhone" placeholder="মোবাইল নম্বর">
            <button class="confirm-btn" onclick="placeOrder('${orderId}')">অর্ডার কনফার্ম</button>
        `;
        document.getElementById('orderModal').style.display = 'block';
        closeModal('cartModal');
    };

    window.selectPayment = function(type) {
        selectedPayment = type;
        document.getElementById('bkashOpt').classList.remove('selected');
        document.getElementById('codOpt').classList.remove('selected');
        document.getElementById(type + 'Opt').classList.add('selected');
        document.getElementById('bkashFields').style.display = type === 'bkash' ? 'block' : 'none';
    };

    window.selectDelivery = function(type) {
        let sub = cart.reduce((s,i) => s + i.price * i.qty, 0);
        if (type === 'free' && sub < 3000) return;
        selectedDelivery = type;
        document.getElementById('paidDel').classList.remove('selected');
        document.getElementById('freeDel').classList.remove('selected');
        document.getElementById(type === 'paid' ? 'paidDel' : 'freeDel').classList.add('selected');
        let delivery = (type === 'free' && sub >= 3000) ? 0 : 40;
        document.getElementById('deliveryCharge').innerText = delivery === 0 ? 'ফ্রি' : '৳' + delivery;
        document.getElementById('totalAmount').innerText = '৳' + (sub + delivery);
        let note = document.getElementById('deliveryNote');
        if (sub >= 3000) {
            document.getElementById('freeDel').classList.remove('disabled');
            note.innerHTML = '✅ ফ্রি ডেলিভারি!';
        } else {
            document.getElementById('freeDel').classList.add('disabled');
            note.innerHTML = `✨ আরও ৳${3000-sub} কিনলে ফ্রি`;
        }
    };

    window.placeOrder = function(orderId) {
        let name = document.getElementById('custName')?.value.trim() || '';
        let addr = document.getElementById('custAddress')?.value.trim() || '';
        let phone = document.getElementById('custPhone')?.value.trim() || '';
        let trx = document.getElementById('trxId')?.value.trim() || '';
        if (!name || !addr || !phone) return showToast('সব তথ্য দিন');
        if (selectedPayment === 'bkash' && !trx) return showToast('বিকাশ TrxID দিন');

        let subtotal = cart.reduce((s,i) => s + i.price * i.qty, 0);
        let delivery = (selectedDelivery === 'free' && subtotal >= 3000) ? 0 : 40;
        let items = cart.map(i => `• ${i.name} (${i.code}) - ${i.qty} x ৳${i.price} = ৳${i.price * i.qty}`).join('\n');
        let msg = `জাগুয়া শপ\nঅর্ডার আইডি: ${orderId}\nনাম: ${name}\nফোন: ${phone}\nঠিকানা: ${addr}\nপেমেন্ট: ${selectedPayment}\nTrxID: ${trx}\nডেলিভারি: ${delivery===0?'ফ্রি':'৪০'}\nমোট: ৳${subtotal+delivery}\nপণ্য:\n${items}`;
        window.open(`https://wa.me/8801776084491?text=${encodeURIComponent(msg)}`);

        cart = []; localStorage.setItem('jagua_cart', JSON.stringify(cart));
        document.getElementById('cartCount').innerText = '0';
        closeModal('orderModal');
        showToast('অর্ডার সফল!');
    };

    window.closeModal = id => document.getElementById(id).style.display = 'none';
    function showToast(m) { let t = document.getElementById('toast'); t.innerText = m; t.style.display = 'block'; setTimeout(() => t.style.display = 'none', 2000); }

    // ---------- অ্যাডমিন ----------
    function renderLogin() {
        document.getElementById('app').innerHTML = `
            <div class="login-box">
                <h3 style="color:#1a4d2e;">অ্যাডমিন লগইন</h3>
                <input class="input-field" id="adminPass" placeholder="পাসওয়ার্ড" type="password">
                <button class="confirm-btn" onclick="adminLogin()">লগইন</button>
                <p style="margin-top:15px;"><a href="#" onclick="window.location.hash=''; location.reload()">মূল সাইটে ফিরুন</a></p>
            </div>
        `;
    }
    window.adminLogin = function() {
        let pass = document.getElementById('adminPass').value;
        if (pass === 'siratahamednahid75') {
            localStorage.setItem('jagua_admin', 'true');
            isLoggedIn = true;
            renderAdmin();
        } else showToast('ভুল পাসওয়ার্ড');
    };

    let adminPage = 1, adminPerPage = 12, adminSearch = '';
    function renderAdmin() {
        let filtered = products.filter(p => p.name.toLowerCase().includes(adminSearch.toLowerCase()) || p.code.toLowerCase().includes(adminSearch.toLowerCase()));
        let start = (adminPage-1)*adminPerPage, end = start+adminPerPage;
        let cards = filtered.slice(start,end).map(p => `
            <div class="admin-card">
                <img src="${p.image}" onerror="this.src='https://via.placeholder.com/300?text=Product'">
                <input class="admin-input" id="code_${p.id}" value="${p.code}">
                <input class="admin-input" id="name_${p.id}" value="${p.name.replace(/"/g, '&quot;')}">
                <input class="admin-input" id="price_${p.id}" value="${p.price}">
                <input class="admin-input" id="cat_${p.id}" value="${p.category}">
                <input class="admin-input" id="unit_${p.id}" value="${p.unit}">
                <input class="admin-input" id="desc_${p.id}" value="${p.desc}">
                <input class="admin-input" id="image_${p.id}" value="${p.image}">
                <button class="admin-save" onclick="saveProduct(${p.id})">সংরক্ষণ</button>
            </div>
        `).join('');
        let totalPages = Math.ceil(filtered.length / adminPerPage);
        let pageBtns = '';
        for (let i=1; i<=totalPages; i++) pageBtns += `<span class="page-btn ${i===adminPage?'active':''}" onclick="adminGoToPage(${i})">${i}</span>`;
        document.getElementById('app').innerHTML = `
            <div class="admin-panel">
                <div class="admin-header">
                    <h3>অ্যাডমিন প্যানেল</h3>
                    <div>
                        <button class="confirm-btn" onclick="adminLogout()" style="background:#dc3545;">লগআউট</button>
                        <a href="#" onclick="window.location.hash=''; location.reload()" style="background:#1a4d2e; color:white; padding:10px 20px; border-radius:40px;">মূল সাইট</a>
                    </div>
                </div>
                <div class="search-container"><input type="text" id="adminSearch" placeholder="খুঁজুন..." value="${adminSearch}"></div>
                <div class="admin-grid">${cards}</div>
                <div class="pagination">
                    <span class="page-btn" onclick="adminChangePage(-1)" ${adminPage===1?'disabled':''}>‹</span>${pageBtns}<span class="page-btn" onclick="adminChangePage(1)" ${adminPage===totalPages?'disabled':''}>›</span>
                </div>
            </div>
        `;
        document.getElementById('adminSearch')?.addEventListener('input', e => { adminSearch = e.target.value; adminPage = 1; renderAdmin(); });
    }
    window.saveProduct = function(id) {
        let prod = products.find(p => p.id === id);
        if (prod) {
            prod.code = document.getElementById(`code_${id}`).value;
            prod.name = document.getElementById(`name_${id}`).value;
            prod.price = parseFloat(document.getElementById(`price_${id}`).value);
            prod.category = document.getElementById(`cat_${id}`).value;
            prod.unit = document.getElementById(`unit_${id}`).value;
            prod.desc = document.getElementById(`desc_${id}`).value;
            prod.image = document.getElementById(`image_${id}`).value;
            localStorage.setItem('jagua_products', JSON.stringify(products));
            showToast('সংরক্ষিত');
        }
    };
    window.adminGoToPage = p => { adminPage = p; renderAdmin(); };
    window.adminChangePage = dir => {
        let total = Math.ceil(products.length / adminPerPage);
        if (dir === -1 && adminPage > 1) adminPage--;
        else if (dir === 1 && adminPage < total) adminPage++;
        renderAdmin();
    };
    window.adminLogout = function() { localStorage.removeItem('jagua_admin'); window.location.hash = ''; location.reload(); };
})();
</script>

</body>
</html>

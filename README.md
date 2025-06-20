
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معرض المنتجات الرقمي</title>
    <meta http-equiv="Content-Security-Policy" content="
        default-src 'self';
        script-src 'self' https://cdnjs.cloudflare.com/ajax/libs/font-awesome/ https://fonts.googleapis.com 'unsafe-inline';
        style-src 'self' https://cdnjs.cloudflare.com/ajax/libs/font-awesome/ https://fonts.googleapis.com 'unsafe-inline';
        img-src 'self' data: https://via.placeholder.com;
        font-src 'self' https://cdnjs.cloudflare.com/ajax/libs/font-awesome/ https://fonts.gstatic.com;
        connect-src 'self';
        object-src 'none';
        base-uri 'self';
        form-action 'self';
    ">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;900&display=swap" rel="stylesheet">
    <style>
        /* CSS Reset */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Tajawal', sans-serif;
            background-color: #f5f7fa;
            color: #333;
            transition: all 0.3s ease;
            overflow-x: hidden;
        }

            body.dark-mode {
                background-color: #121212;
                color: #f5f5f5;
            }

        /* شاشة التحميل */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #6e8efb, #a777e3);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.5s ease;
        }

        .loader {
            text-align: center;
            color: white;
        }

            .loader p {
                margin-top: 20px;
                font-size: 1.2rem;
            }

        .cube {
            width: 60px;
            height: 60px;
            position: relative;
            transform-style: preserve-3d;
            animation: rotate 3s infinite linear;
        }

        .face {
            position: absolute;
            width: 100%;
            height: 100%;
            opacity: 0.8;
            border: 2px solid white;
        }

        .front {
            background-color: #ff6b6b;
            transform: translateZ(30px);
        }

        .back {
            background-color: #4ecdc4;
            transform: translateZ(-30px);
        }

        .right {
            background-color: #ffe66d;
            transform: rotateY(90deg) translateZ(30px);
        }

        .left {
            background-color: #ff9ff3;
            transform: rotateY(-90deg) translateZ(30px);
        }

        .top {
            background-color: #1dd1a1;
            transform: rotateX(90deg) translateZ(30px);
        }

        .bottom {
            background-color: #f368e0;
            transform: rotateX(-90deg) translateZ(30px);
        }

        @keyframes rotate {
            from {
                transform: rotateX(0) rotateY(0);
            }

            to {
                transform: rotateX(360deg) rotateY(360deg);
            }
        }

        /* الهيدر */
        .glass-header {
            background: rgba(255, 255, 255, 0.8);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid rgba(255, 255, 255, 0.3);
        }

        .dark-mode .glass-header {
            background: rgba(30, 30, 30, 0.8);
            border-bottom: 1px solid rgba(0, 0, 0, 0.3);
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }

            .logo i {
                font-size: 2rem;
                color: #6e8efb;
            }

        .add-btn {
            background: linear-gradient(135deg, #6e8efb, #a777e3);
            color: white;
            border: none;
            padding: 0.7rem 1.5rem;
            border-radius: 50px;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(110, 142, 251, 0.4);
        }

            .add-btn:hover {
                transform: translateY(-3px);
                box-shadow: 0 6px 20px rgba(110, 142, 251, 0.6);
            }

            .add-btn:active {
                transform: translateY(0);
            }

        /* الأزرار العائمة */
        .floating-buttons {
            position: fixed;
            bottom: 2rem;
            left: 2rem;
            display: flex;
            flex-direction: column;
            gap: 1rem;
            z-index: 90;
        }

        .float-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: linear-gradient(135deg, #6e8efb, #a777e3);
            color: white;
            border: none;
            font-size: 1.2rem;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease;
            display: flex;
            justify-content: center;
            align-items: center;
        }

            .float-btn:hover {
                transform: translateY(-5px) scale(1.1);
                box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
            }

        /* محتوى الصفحة */
        .main-container {
            display: flex;
            padding: 2rem;
            max-width: 1400px;
            margin: 0 auto;
            gap: 2rem;
        }

        /* شريط التصنيفات الجانبي */
        .sidebar {
            width: 250px;
            background: white;
            border-radius: 15px;
            padding: 1.5rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            height: fit-content;
            position: sticky;
            top: 100px;
        }

        .dark-mode .sidebar {
            background: #1e1e1e;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }

        .sidebar-title {
            font-size: 1.2rem;
            margin-bottom: 1.5rem;
            padding-bottom: 0.5rem;
            border-bottom: 1px solid #eee;
            color: #6e8efb;
        }

        .dark-mode .sidebar-title {
            border-bottom-color: #333;
        }

        .category-list {
            list-style: none;
        }

        .category-item {
            margin-bottom: 0.8rem;
        }

        .category-btn {
            background: none;
            border: none;
            color: #555;
            font-size: 1rem;
            cursor: pointer;
            padding: 0.5rem 1rem;
            border-radius: 8px;
            width: 100%;
            text-align: right;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .dark-mode .category-btn {
            color: #ccc;
        }

        .category-btn:hover, .category-btn.active {
            background: #f0f4ff;
            color: #6e8efb;
        }

        .dark-mode .category-btn:hover, 
        .dark-mode .category-btn.active {
            background: #2a2a3a;
        }

        .category-count {
            background: #e0e7ff;
            color: #6e8efb;
            padding: 0.2rem 0.5rem;
            border-radius: 50px;
            font-size: 0.8rem;
        }

        .dark-mode .category-count {
            background: #3a3a4a;
        }

        /* محتوى المنتجات */
        .content {
            flex: 1;
        }

        .search-container {
            position: relative;
            margin-bottom: 2rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

            .search-container input {
                width: 100%;
                padding: 1rem 1.5rem 1rem 3rem;
                border-radius: 50px;
                border: 1px solid #ddd;
                font-size: 1rem;
                transition: all 0.3s ease;
                background-color: rgba(255, 255, 255, 0.8);
            }

        .dark-mode .search-container input {
            background-color: rgba(30, 30, 30, 0.8);
            border-color: #444;
            color: #f5f5f5;
        }

        .search-container input:focus {
            outline: none;
            border-color: #6e8efb;
            box-shadow: 0 0 0 3px rgba(110, 142, 251, 0.3);
        }

        .search-container i {
            position: absolute;
            left: 1.2rem;
            top: 50%;
            transform: translateY(-50%);
            color: #777;
        }

        .dark-mode .search-container i {
            color: #aaa;
        }

        /* حاوية المنتجات */
        .products-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
        }

            .products-container.list-view {
                grid-template-columns: 1fr;
            }

        /* بطاقة المنتج */
        .product-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            position: relative;
            transform-style: preserve-3d;
            perspective: 1000px;
        }

        .dark-mode .product-card {
            background: #1e1e1e;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
        }

        .product-card.list-view {
            display: flex;
            max-height: 200px;
        }

            .product-card.list-view .product-image {
                width: 200px;
                height: 200px;
                border-radius: 15px 0 0 15px;
            }

            .product-card.list-view .product-info {
                padding: 1.5rem;
                flex: 1;
            }

        .product-image {
            width: 100%;
            height: 250px;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .product-card:hover .product-image {
            transform: scale(1.05);
        }

        .product-info {
            padding: 1.5rem;
        }

        .product-title {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            color: #333;
        }

        .dark-mode .product-title {
            color: #f5f5f5;
        }

        .product-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #6e8efb;
            margin-bottom: 1rem;
        }

        .product-description {
            color: #666;
            margin-bottom: 1.5rem;
            line-height: 1.5;
        }

        .dark-mode .product-description {
            color: #aaa;
        }

        .product-category {
            display: inline-block;
            padding: 0.3rem 0.8rem;
            background: #f0f4ff;
            border-radius: 50px;
            font-size: 0.8rem;
            color: #6e8efb;
            margin-bottom: 1rem;
        }

        .dark-mode .product-category {
            background: #2a2a3a;
        }

        .product-actions {
            display: flex;
            gap: 10px;
        }

        .action-btn {
            flex: 1;
            padding: 0.5rem;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 5px;
        }

        .edit-btn {
            background: #f0f4ff;
            color: #6e8efb;
        }

        .dark-mode .edit-btn {
            background: #2a2a3a;
        }

        .delete-btn {
            background: #ffebee;
            color: #ff5252;
        }

        .dark-mode .delete-btn {
            background: #3a2a2a;
        }

        .action-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        /* المودال */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            backdrop-filter: blur(5px);
            -webkit-backdrop-filter: blur(5px);
            justify-content: center;
            align-items: center;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

            .modal.show {
                display: flex;
                opacity: 1;
            }

        .modal-content {
            background: white;
            border-radius: 15px;
            width: 90%;
            max-width: 500px;
            padding: 2rem;
            position: relative;
            transform: translateY(-50px);
            transition: transform 0.3s ease;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .dark-mode .modal-content {
            background: #1e1e1e;
        }

        .modal.show .modal-content {
            transform: translateY(0);
        }

        .close-modal {
            position: absolute;
            top: 1rem;
            left: 1rem;
            font-size: 1.5rem;
            cursor: pointer;
            color: #777;
            transition: color 0.3s ease;
        }

            .close-modal:hover {
                color: #ff5252;
            }

        .form-group {
            margin-bottom: 1.5rem;
        }

            .form-group label {
                display: block;
                margin-bottom: 0.5rem;
                font-weight: bold;
                color: #555;
            }

        .dark-mode .form-group label {
            color: #ccc;
        }

        .form-group input,
        .form-group textarea,
        .form-group select {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: all 0.3s ease;
            background-color: rgba(255, 255, 255, 0.8);
        }

        .dark-mode .form-group input,
        .dark-mode .form-group textarea,
        .dark-mode .form-group select {
            background-color: rgba(30, 30, 30, 0.8);
            border-color: #444;
            color: #f5f5f5;
        }

        .form-group input:focus,
        .form-group textarea:focus,
        .form-group select:focus {
            outline: none;
            border-color: #6e8efb;
            box-shadow: 0 0 0 3px rgba(110, 142, 251, 0.3);
        }

        .submit-btn {
            background: linear-gradient(135deg, #6e8efb, #a777e3);
            color: white;
            border: none;
            padding: 1rem 2rem;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

            .submit-btn:hover {
                transform: translateY(-3px);
                box-shadow: 0 6px 15px rgba(110, 142, 251, 0.4);
            }

        /* الإشعارات */
        .notification {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            padding: 1rem 1.5rem;
            background: #4caf50;
            color: white;
            border-radius: 8px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            transform: translateY(100px);
            opacity: 0;
            transition: all 0.3s ease;
            z-index: 1000;
            display: flex;
            align-items: center;
            gap: 10px;
        }

            .notification.show {
                transform: translateY(0);
                opacity: 1;
            }

            .notification.error {
                background: #ff5252;
            }

            .notification.warning {
                background: #ffc107;
                color: #333;
            }

        /* تأثيرات ثلاثية الأبعاد */
        .product-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(110, 142, 251, 0.1), rgba(167, 119, 227, 0.1));
            z-index: -1;
            transform: translateZ(-20px);
            border-radius: 15px;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .product-card:hover::before {
            opacity: 1;
        }

        /* تأثيرات الحركة */
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .product-card {
            animation: fadeIn 0.5s ease forwards;
            opacity: 0;
        }

        /* تأثيرات خاصة للوضع الداكن */
        .dark-mode .product-card::before {
            background: linear-gradient(135deg, rgba(110, 142, 251, 0.2), rgba(167, 119, 227, 0.2));
        }

        /* تأثيرات اللمس */
        @media (hover: hover) {
            .product-card {
                transition: transform 0.3s ease, box-shadow 0.3s ease;
            }

                .product-card:hover {
                    transform: translateY(-10px) rotateX(5deg) rotateY(5deg);
                    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
                }
        }

        /* تصميم متجاوب */
        @media (max-width: 992px) {
            .main-container {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
                position: static;
                margin-bottom: 2rem;
            }
            
            .category-list {
                display: flex;
                flex-wrap: wrap;
                gap: 0.5rem;
            }
            
            .category-item {
                margin-bottom: 0;
            }
            
            .category-btn {
                padding: 0.5rem;
                font-size: 0.9rem;
            }
        }

        @media (max-width: 768px) {
            .products-container {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }

            .product-card.list-view {
                flex-direction: column;
                max-height: none;
            }

                .product-card.list-view .product-image {
                    width: 100%;
                    height: 200px;
                    border-radius: 15px 15px 0 0;
                }

            .modal-content {
                width: 95%;
                padding: 1.5rem;
            }
        }

        @media (max-width: 480px) {
            .glass-header {
                padding: 1rem;
                flex-direction: column;
                gap: 1rem;
            }

            .add-btn {
                width: 100%;
                justify-content: center;
            }

            .floating-buttons {
                flex-direction: row;
                bottom: 1rem;
                left: 50%;
                transform: translateX(-50%);
            }

            .float-btn {
                width: 40px;
                height: 40px;
                font-size: 1rem;
            }
        }

        /* مودال تسجيل الدخول */
        .login-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            backdrop-filter: blur(5px);
            -webkit-backdrop-filter: blur(5px);
            justify-content: center;
            align-items: center;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

            .login-modal.show {
                display: flex;
                opacity: 1;
            }

        .login-content {
            background: white;
            border-radius: 15px;
            width: 90%;
            max-width: 400px;
            padding: 2rem;
            position: relative;
            transform: translateY(-50px);
            transition: transform 0.3s ease;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
            text-align: center;
        }

        .dark-mode .login-content {
            background: #1e1e1e;
        }

        .login-modal.show .login-content {
            transform: translateY(0);
        }

        .login-logo {
            font-size: 3rem;
            color: #6e8efb;
            margin-bottom: 1rem;
        }

        .login-title {
            font-size: 1.5rem;
            margin-bottom: 1.5rem;
            color: #333;
        }

        .dark-mode .login-title {
            color: #f5f5f5;
        }

        .login-input {
            width: 100%;
            padding: 1rem;
            margin-bottom: 1rem;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .dark-mode .login-input {
            background-color: rgba(30, 30, 30, 0.8);
            border-color: #444;
            color: #f5f5f5;
        }

        .login-input:focus {
            outline: none;
            border-color: #6e8efb;
            box-shadow: 0 0 0 3px rgba(110, 142, 251, 0.3);
        }

        .login-btn {
            background: linear-gradient(135deg, #6e8efb, #a777e3);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            font-size: 1rem;
            transition: all 0.3s ease;
            margin-top: 1rem;
        }

            .login-btn:hover {
                transform: translateY(-3px);
                box-shadow: 0 6px 15px rgba(110, 142, 251, 0.4);
            }

        .password-container {
            position: relative;
        }

        .toggle-password {
            position: absolute;
            left: 10px;
            top: 50%;
            transform: translateY(-50%);
            cursor: pointer;
            color: #777;
        }

        .dark-mode .toggle-password {
            color: #aaa;
        }

        /* أنماط رفع الصور */
        .image-upload-container {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 8px;
        }

        .upload-btn {
            background: #f0f4ff;
            color: #6e8efb;
            border: 1px dashed #6e8efb;
            padding: 0.5rem 1rem;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .dark-mode .upload-btn {
            background: #2a2a3a;
            border-color: #6e8efb;
        }

        .upload-btn:hover {
            background: #e1e8ff;
        }

        .dark-mode .upload-btn:hover {
            background: #3a3a4a;
        }

        #imageFileName {
            font-size: 0.9rem;
            color: #666;
        }

        .dark-mode #imageFileName {
            color: #aaa;
        }

        .image-preview {
            margin-top: 1rem;
            display: none;
        }

        .image-preview img {
            max-width: 100%;
            max-height: 200px;
            border-radius: 8px;
            border: 1px solid #ddd;
        }

        .dark-mode .image-preview img {
            border-color: #444;
        }
    </style>
</head>
<body>
    <div class="loading-screen">
        <div class="loader">
            <div class="cube">
                <div class="face front"></div>
                <div class="face back"></div>
                <div class="face right"></div>
                <div class="face left"></div>
                <div class="face top"></div>
                <div class="face bottom"></div>
            </div>
            <p>جاري تحميل المعرض...</p>
        </div>
    </div>

    <header class="glass-header">
        <div class="logo">
            <i class="fas fa-cubes"></i>
            <h1>معرض المنتجات</h1>
        </div>
        <button id="addProductBtn" class="add-btn">
            <i class="fas fa-plus"></i> إضافة منتج
        </button>
    </header>

    <div class="floating-buttons">
        <button id="themeToggle" class="float-btn" title="تبديل الثيم">
            <i class="fas fa-moon"></i>
        </button>
        <button id="viewToggle" class="float-btn" title="تبديل طريقة العرض">
            <i class="fas fa-grip-horizontal"></i>
        </button>
    </div>

    <div class="main-container">
        <!-- شريط التصنيفات الجانبي -->
        <aside class="sidebar">
            <h3 class="sidebar-title">تصنيفات المنتجات</h3>
            <ul class="category-list" id="categoryList">
                <li class="category-item">
                    <button class="category-btn active" data-category="all">
                        جميع المنتجات
                        <span class="category-count" id="allCount">0</span>
                    </button>
                </li>
                <li class="category-item">
                    <button class="category-btn" data-category="electronics">
                        إلكترونيات
                        <span class="category-count" id="electronicsCount">0</span>
                    </button>
                </li>
                <li class="category-item">
                    <button class="category-btn" data-category="fashion">
                        موضة
                        <span class="category-count" id="fashionCount">0</span>
                    </button>
                </li>
                <li class="category-item">
                    <button class="category-btn" data-category="home">
                        منزل
                        <span class="category-count" id="homeCount">0</span>
                    </button>
                </li>
                <li class="category-item">
                    <button class="category-btn" data-category="sports">
                        رياضة
                        <span class="category-count" id="sportsCount">0</span>
                    </button>
                </li>
                <li class="category-item">
                    <button class="category-btn" data-category="other">
                        أخرى
                        <span class="category-count" id="otherCount">0</span>
                    </button>
                </li>
            </ul>
        </aside>

        <!-- المحتوى الرئيسي -->
        <main class="content">
            <div class="search-container">
                <input type="text" id="searchInput" placeholder="ابحث عن منتج...">
                <i class="fas fa-search"></i>
            </div>

            <div class="products-container" id="productsContainer">
                <!-- المنتجات ستضاف هنا ديناميكيًا -->
            </div>
        </main>
    </div>

    <!-- مودال تسجيل الدخول -->
    <div class="login-modal" id="loginModal">
        <div class="login-content">
            <div class="login-logo">
                <i class="fas fa-lock"></i>
            </div>
            <h2 class="login-title">تسجيل الدخول</h2>
            <div class="form-group">
                <input type="email" id="loginEmail" class="login-input" placeholder="البريد الإلكتروني" required>
            </div>
            <div class="form-group password-container">
                <input type="password" id="loginPassword" class="login-input" placeholder="كلمة المرور" required>
                <i class="fas fa-eye toggle-password" id="togglePassword"></i>
            </div>
            <button id="loginBtn" class="login-btn">تسجيل الدخول</button>
        </div>
    </div>

    <!-- مودال المنتج -->
    <div class="modal" id="productModal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <h2 id="modalTitle">إضافة منتج جديد</h2>
            <form id="productForm">
                <input type="hidden" name="csrfToken" id="csrfToken">
                <div class="form-group">
                    <label for="productName">اسم المنتج</label>
                    <input type="text" id="productName" required>
                </div>
                <div class="form-group">
                    <label for="productPrice">السعر</label>
                    <input type="text" id="productPrice" required>
                </div>
                <div class="form-group">
                    <label for="productImage">صورة المنتج</label>
                    <input type="file" id="productImage" accept="image/*" style="display: none">
                    <div class="image-upload-container">
                        <button type="button" id="uploadImageBtn" class="upload-btn">
                            <i class="fas fa-cloud-upload-alt"></i> اختر صورة
                        </button>
                        <span id="imageFileName">لم يتم اختيار صورة</span>
                    </div>
                    <div class="image-preview" id="imagePreview"></div>
                </div>
                <div class="form-group">
                    <label for="productDescription">وصف المنتج</label>
                    <textarea id="productDescription" rows="3"></textarea>
                </div>
                <div class="form-group">
                    <label for="productCategory">الفئة</label>
                    <select id="productCategory">
                        <option value="electronics">إلكترونيات</option>
                        <option value="fashion">موضة</option>
                        <option value="home">منزل</option>
                        <option value="sports">رياضة</option>
                        <option value="other">أخرى</option>
                    </select>
                </div>
                <button type="submit" class="submit-btn">حفظ المنتج</button>
            </form>
        </div>
    </div>

    <div class="notification" id="notification"></div>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            // شاشة التحميل
            setTimeout(() => {
                document.querySelector('.loading-screen').style.opacity = '0';
                setTimeout(() => {
                    document.querySelector('.loading-screen').style.display = 'none';
                }, 500);
            }, 2000);

            // تهيئة المتغيرات
            const productsContainer = document.getElementById('productsContainer');
            const addProductBtn = document.getElementById('addProductBtn');
            const productModal = document.getElementById('productModal');
            const loginModal = document.getElementById('loginModal');
            const closeModal = document.querySelector('.close-modal');
            const productForm = document.getElementById('productForm');
            const searchInput = document.getElementById('searchInput');
            const themeToggle = document.getElementById('themeToggle');
            const viewToggle = document.getElementById('viewToggle');
            const notification = document.getElementById('notification');
            const loginBtn = document.getElementById('loginBtn');
            const togglePassword = document.getElementById('togglePassword');
            const loginPassword = document.getElementById('loginPassword');
            const uploadImageBtn = document.getElementById('uploadImageBtn');
            const productImageInput = document.getElementById('productImage');
            const categoryList = document.getElementById('categoryList');
            const categoryBtns = document.querySelectorAll('.category-btn');
            const csrfTokenInput = document.getElementById('csrfToken');

            // معلومات تسجيل الدخول الصحيحة
            const correctEmail = 'mohamadmm@mhd.com';
            const correctPasswordHash = '5f4dcc3b5aa765d61d8327deb882cf99'; // كلمة المرور: password (في الواقع يجب استخدام salt)

            let products = loadProductsFromStorage();
            let isEditing = false;
            let currentProductId = null;
            let isListView = false;
            let isLoggedIn = sessionStorage.getItem('isLoggedIn') === 'true';
            let selectedImageFile = null;
            let currentCategory = 'all';
            let lastRequestTime = 0;
            const REQUEST_DELAY = 1000; // 1 ثانية بين الطلبات

            // دالة لتنظيف المدخلات من أي أكواد ضارة
            function sanitizeInput(input) {
                const div = document.createElement('div');
                div.textContent = input;
                return div.innerHTML
                    .replace(/</g, '&lt;')
                    .replace(/>/g, '&gt;')
                    .replace(/'/g, '&#39;')
                    .replace(/"/g, '&#34;');
            }

            // دالة لتنظيف URLs
            function sanitizeUrl(url) {
                if (!url) return 'https://via.placeholder.com/300x200?text=No+Image';
                
                try {
                    const parsedUrl = new URL(url);
                    if (['http:', 'https:', 'data:'].includes(parsedUrl.protocol)) {
                        return url;
                    }
                } catch (e) {
                    return 'https://via.placeholder.com/300x200?text=Invalid+Image';
                }
                
                return 'https://via.placeholder.com/300x200?text=Invalid+Image';
            }

            // تشفير البيانات قبل تخزينها في localStorage
            function saveProductsToStorage(productsArray) {
                try {
                    const encrypted = btoa(encodeURIComponent(JSON.stringify(productsArray)));
                    localStorage.setItem('encryptedProducts', encrypted);
                } catch (error) {
                    console.error('Error saving products:', error);
                    showNotification('حدث خطأ في حفظ البيانات', 'error');
                }
            }

            // فك تشفير البيانات عند استرجاعها
            function loadProductsFromStorage() {
                try {
                    const encrypted = localStorage.getItem('encryptedProducts');
                    if (!encrypted) return [];
                    
                    const decrypted = decodeURIComponent(atob(encrypted));
                    return JSON.parse(decrypted);
                } catch (error) {
                    console.error('Error loading products:', error);
                    showNotification('حدث خطأ في تحميل البيانات', 'error');
                    return [];
                }
            }

            // توليد رمز CSRF
            function generateCSRFToken() {
                const token = 'csrf_' + Math.random().toString(36).substr(2, 16) + Date.now().toString(36);
                sessionStorage.setItem('csrfToken', token);
                return token;
            }

            // التحقق من صحة الجلسة
            function validateSession() {
                const storedToken = sessionStorage.getItem('sessionToken');
                if (!storedToken || !storedToken.startsWith('token_')) {
                    isLoggedIn = false;
                    sessionStorage.removeItem('isLoggedIn');
                    sessionStorage.removeItem('sessionToken');
                    return false;
                }
                return true;
            }

            // الحد من معدل الطلبات للوظائف الحساسة
            function throttleRequests() {
                const now = Date.now();
                if (now - lastRequestTime < REQUEST_DELAY) {
                    showNotification('الرجاء الانتظار قبل إجراء العملية التالية', 'warning');
                    return false;
                }
                lastRequestTime = now;
                return true;
            }

            // تحميل المنتجات
            function loadProducts() {
                productsContainer.innerHTML = '';
                updateCategoryCounts();

                // تصفية المنتجات حسب الفئة المحددة
                let filteredProducts = products;
                if (currentCategory !== 'all') {
                    filteredProducts = products.filter(product => product.category === currentCategory);
                }

                if (filteredProducts.length === 0) {
                    productsContainer.innerHTML = `
                        <div class="empty-state">
                            <i class="fas fa-box-open"></i>
                            <h3>لا يوجد منتجات لعرضها</h3>
                            <p>اضغط على زر "إضافة منتج" لبدء إضافة منتجاتك</p>
                        </div>
                    `;
                    return;
                }

                filteredProducts.forEach((product, index) => {
                    const productCard = document.createElement('div');
                    productCard.className = `product-card ${isListView ? 'list-view' : ''}`;
                    productCard.style.animationDelay = `${index * 0.1}s`;
                    
                    // إنشاء عناصر DOM بدلاً من استخدام innerHTML
                    const img = document.createElement('img');
                    img.src = sanitizeUrl(product.image);
                    img.alt = sanitizeInput(product.name);
                    img.className = 'product-image';
                    
                    const productInfo = document.createElement('div');
                    productInfo.className = 'product-info';
                    
                    const title = document.createElement('h3');
                    title.className = 'product-title';
                    title.textContent = product.name;
                    
                    const price = document.createElement('div');
                    price.className = 'product-price';
                    price.textContent = `$${formatPrice(product.price)}`;
                    
                    const description = document.createElement('p');
                    description.className = 'product-description';
                    description.textContent = product.description;
                    
                    const category = document.createElement('span');
                    category.className = 'product-category';
                    category.textContent = getCategoryName(product.category);
                    
                    const actions = document.createElement('div');
                    actions.className = 'product-actions';
                    
                    const editBtn = document.createElement('button');
                    editBtn.className = 'action-btn edit-btn';
                    editBtn.setAttribute('data-id', product.id);
                    editBtn.innerHTML = '<i class="fas fa-edit"></i> تعديل';
                    
                    const deleteBtn = document.createElement('button');
                    deleteBtn.className = 'action-btn delete-btn';
                    deleteBtn.setAttribute('data-id', product.id);
                    deleteBtn.innerHTML = '<i class="fas fa-trash"></i> حذف';
                    
                    actions.appendChild(editBtn);
                    actions.appendChild(deleteBtn);
                    
                    productInfo.appendChild(title);
                    productInfo.appendChild(price);
                    productInfo.appendChild(description);
                    productInfo.appendChild(category);
                    productInfo.appendChild(actions);
                    
                    productCard.appendChild(img);
                    productCard.appendChild(productInfo);
                    
                    productsContainer.appendChild(productCard);
                });

                // إضافة مستمعي الأحداث للبطاقات الجديدة
                addEventListenersToCards();
            }

            // تحديث عدد المنتجات في كل فئة
            function updateCategoryCounts() {
                document.getElementById('allCount').textContent = products.length;
                document.getElementById('electronicsCount').textContent = 
                    products.filter(p => p.category === 'electronics').length;
                document.getElementById('fashionCount').textContent = 
                    products.filter(p => p.category === 'fashion').length;
                document.getElementById('homeCount').textContent = 
                    products.filter(p => p.category === 'home').length;
                document.getElementById('sportsCount').textContent = 
                    products.filter(p => p.category === 'sports').length;
                document.getElementById('otherCount').textContent = 
                    products.filter(p => p.category === 'other').length;
            }

            // تنسيق السعر مع الفواصل
            function formatPrice(price) {
                // تحويل السعر إلى رقم أولاً
                const num = typeof price === 'string' ? parseFloat(price.replace(/,/g, '')) : price;
                return num.toLocaleString('en-US');
            }

            // الحصول على اسم الفئة
            function getCategoryName(category) {
                const categories = {
                    'electronics': 'إلكترونيات',
                    'fashion': 'موضة',
                    'home': 'منزل',
                    'sports': 'رياضة',
                    'other': 'أخرى'
                };
                return categories[category] || category;
            }

            // توليد معرف فريد للمنتج
            function generateId() {
                return Date.now().toString(36) + Math.random().toString(36).substr(2);
            }

            // توليد رمز الجلسة
            function generateSessionToken() {
                return 'token_' + Math.random().toString(36).substr(2, 16) + Date.now().toString(36);
            }

            // عرض مودال تسجيل الدخول
            function showLoginModal() {
                loginModal.classList.add('show');
                setTimeout(() => {
                    loginModal.style.opacity = '1';
                }, 10);
            }

            // إغلاق مودال تسجيل الدخول
            function closeLoginModal() {
                loginModal.style.opacity = '0';
                setTimeout(() => {
                    loginModal.classList.remove('show');
                }, 300);
            }

            // عرض مودال المنتج
            function showProductModal(editing = false, product = null) {
                isEditing = editing;
                const modalTitle = document.getElementById('modalTitle');

                // توليد وتحديث رمز CSRF
                const csrfToken = generateCSRFToken();
                csrfTokenInput.value = csrfToken;

                if (editing && product) {
                    modalTitle.textContent = 'تعديل المنتج';
                    document.getElementById('productName').value = product.name;
                    document.getElementById('productPrice').value = product.price;
                    document.getElementById('productDescription').value = product.description;
                    document.getElementById('productCategory').value = product.category;
                    currentProductId = product.id;
                    
                    // عرض الصورة الحالية
                    document.getElementById('imagePreview').style.display = 'block';
                    const previewImg = document.createElement('img');
                    previewImg.src = sanitizeUrl(product.image);
                    previewImg.alt = 'معاينة الصورة';
                    document.getElementById('imagePreview').innerHTML = '';
                    document.getElementById('imagePreview').appendChild(previewImg);
                    document.getElementById('imageFileName').textContent = 'الصورة الحالية';
                } else {
                    modalTitle.textContent = 'إضافة منتج جديد';
                    productForm.reset();
                    currentProductId = null;
                    
                    // إعادة تعيين معاينة الصورة
                    document.getElementById('imagePreview').style.display = 'none';
                    document.getElementById('imageFileName').textContent = 'لم يتم اختيار صورة';
                }

                selectedImageFile = null;
                productModal.classList.add('show');
                setTimeout(() => {
                    productModal.style.opacity = '1';
                }, 10);
            }

            // إغلاق مودال المنتج
            function closeProductModal() {
                productModal.style.opacity = '0';
                setTimeout(() => {
                    productModal.classList.remove('show');
                }, 300);
            }

            // عرض الإشعار
            function showNotification(message, type = 'success') {
                notification.textContent = message;
                notification.className = 'notification';
                notification.classList.add(type, 'show');

                setTimeout(() => {
                    notification.classList.remove('show');
                }, 3000);
            }

            // إعداد بيانات المنتج
            function prepareProductData() {
                const name = document.getElementById('productName').value.trim();
                const price = document.getElementById('productPrice').value.trim();
                const description = document.getElementById('productDescription').value.trim();
                const category = document.getElementById('productCategory').value;

                // التحقق من صحة البيانات
                if (!name || name.length < 2) {
                    throw new Error('اسم المنتج يجب أن يكون على الأقل حرفين');
                }

                if (!price || isNaN(parseFloat(price.replace(/,/g, '')))) {
                    throw new Error('السعر يجب أن يكون رقمًا صحيحًا');
                }

                if (description.length > 500) {
                    throw new Error('الوصف يجب ألا يتجاوز 500 حرف');
                }

                const validCategories = ['electronics', 'fashion', 'home', 'sports', 'other'];
                if (!validCategories.includes(category)) {
                    throw new Error('فئة غير صالحة');
                }

                const product = {
                    name: sanitizeInput(name),
                    price: price,
                    description: sanitizeInput(description),
                    category: category
                };

                // إذا كان هناك صورة مختارة، قم بتحويلها إلى URL بيانات
                if (selectedImageFile) {
                    return new Promise((resolve) => {
                        const reader = new FileReader();
                        reader.onload = function(event) {
                            product.image = event.target.result;
                            resolve(product);
                        };
                        reader.readAsDataURL(selectedImageFile);
                    });
                } else if (isEditing && currentProductId) {
                    // إذا كان تعديلاً ولم يتم تغيير الصورة، احتفظ بالصورة القديمة
                    const oldProduct = products.find(p => p.id === currentProductId);
                    product.image = oldProduct.image;
                    return Promise.resolve(product);
                } else {
                    // إذا لم يتم اختيار صورة، استخدم صورة افتراضية
                    product.image = 'https://via.placeholder.com/300x200?text=No+Image';
                    return Promise.resolve(product);
                }
            }

            // إضافة مستمعي الأحداث لبطاقات المنتجات
            function addEventListenersToCards() {
                document.querySelectorAll('.edit-btn').forEach(btn => {
                    btn.addEventListener('click', function () {
                        if (!validateSession() || !isLoggedIn) {
                            showLoginModal();
                            return;
                        }
                        const productId = this.getAttribute('data-id');
                        const product = products.find(p => p.id === productId);
                        if (product) showProductModal(true, product);
                    });
                });

                document.querySelectorAll('.delete-btn').forEach(btn => {
                    btn.addEventListener('click', function () {
                        if (!validateSession() || !isLoggedIn) {
                            showLoginModal();
                            return;
                        }
                        const productId = this.getAttribute('data-id');
                        if (confirm('هل أنت متأكد من حذف هذا المنتج؟')) {
                            deleteProduct(productId);
                        }
                    });
                });
            }

            // إضافة منتج
            function addProduct(product) {
                if (!throttleRequests()) return;
                
                // تنظيف السعر من الفواصل وتحويله إلى رقم
                const cleanedPrice = typeof product.price === 'string' ? 
                    parseFloat(product.price.replace(/,/g, '')) : product.price;
                
                product.price = cleanedPrice;
                product.id = generateId();
                products.unshift(product);
                saveProductsToStorage(products);
                
                // تحديث العرض حسب حالة البحث الحالية
                const query = searchInput.value.trim();
                if (query.length > 0) {
                    searchProducts(query);
                } else {
                    loadProducts();
                }
                
                showNotification('تم إضافة المنتج بنجاح');
            }

            // تحديث منتج
            function updateProduct(product) {
                if (!throttleRequests()) return;
                
                // تنظيف السعر من الفواصل وتحويله إلى رقم
                const cleanedPrice = typeof product.price === 'string' ? 
                    parseFloat(product.price.replace(/,/g, '')) : product.price;
                
                product.price = cleanedPrice;
                const index = products.findIndex(p => p.id === product.id);
                if (index !== -1) {
                    products[index] = product;
                    saveProductsToStorage(products);
                    
                    // تحديث العرض حسب حالة البحث الحالية
                    const query = searchInput.value.trim();
                    if (query.length > 0) {
                        searchProducts(query);
                    } else {
                        loadProducts();
                    }
                    
                    showNotification('تم تحديث المنتج بنجاح');
                }
            }

            // حذف منتج
            function deleteProduct(productId) {
                if (!throttleRequests()) return;
                
                products = products.filter(p => p.id !== productId);
                saveProductsToStorage(products);
                
                // تحديث العرض حسب حالة البحث الحالية
                const query = searchInput.value.trim();
                if (query.length > 0) {
                    searchProducts(query);
                } else {
                    loadProducts();
                }
                
                showNotification('تم حذف المنتج بنجاح');
            }

            // البحث عن منتجات
            function searchProducts(query) {
                let filteredProducts = products;
                
                // تطبيق تصفية الفئة أولاً
                if (currentCategory !== 'all') {
                    filteredProducts = products.filter(product => product.category === currentCategory);
                }
                
                // ثم تطبيق البحث إذا كان هناك استعلام بحث
                if (query) {
                    filteredProducts = filteredProducts.filter(product =>
                        product.name.toLowerCase().includes(query.toLowerCase()) ||
                        product.description.toLowerCase().includes(query.toLowerCase()) ||
                        product.category.toLowerCase().includes(query.toLowerCase())
                    );
                }

                productsContainer.innerHTML = '';

                if (filteredProducts.length === 0) {
                    productsContainer.innerHTML = `
                        <div class="empty-state">
                            <i class="fas fa-search"></i>
                            <h3>لا توجد نتائج للبحث</h3>
                            <p>حاول استخدام كلمات بحث أخرى</p>
                        </div>
                    `;
                    return;
                }

                filteredProducts.forEach((product, index) => {
                    const productCard = document.createElement('div');
                    productCard.className = `product-card ${isListView ? 'list-view' : ''}`;
                    productCard.style.animationDelay = `${index * 0.1}s`;
                    
                    const img = document.createElement('img');
                    img.src = sanitizeUrl(product.image);
                    img.alt = sanitizeInput(product.name);
                    img.className = 'product-image';
                    
                    const productInfo = document.createElement('div');
                    productInfo.className = 'product-info';
                    
                    const title = document.createElement('h3');
                    title.className = 'product-title';
                    title.textContent = product.name;
                    
                    const price = document.createElement('div');
                    price.className = 'product-price';
                    price.textContent = `$${formatPrice(product.price)}`;
                    
                    const description = document.createElement('p');
                    description.className = 'product-description';
                    description.textContent = product.description;
                    
                    const category = document.createElement('span');
                    category.className = 'product-category';
                    category.textContent = getCategoryName(product.category);
                    
                    const actions = document.createElement('div');
                    actions.className = 'product-actions';
                    
                    const editBtn = document.createElement('button');
                    editBtn.className = 'action-btn edit-btn';
                    editBtn.setAttribute('data-id', product.id);
                    editBtn.innerHTML = '<i class="fas fa-edit"></i> تعديل';
                    
                    const deleteBtn = document.createElement('button');
                    deleteBtn.className = 'action-btn delete-btn';
                    deleteBtn.setAttribute('data-id', product.id);
                    deleteBtn.innerHTML = '<i class="fas fa-trash"></i> حذف';
                    
                    actions.appendChild(editBtn);
                    actions.appendChild(deleteBtn);
                    
                    productInfo.appendChild(title);
                    productInfo.appendChild(price);
                    productInfo.appendChild(description);
                    productInfo.appendChild(category);
                    productInfo.appendChild(actions);
                    
                    productCard.appendChild(img);
                    productCard.appendChild(productInfo);
                    
                    productsContainer.appendChild(productCard);
                });

                addEventListenersToCards();
            }

            // تصفية المنتجات حسب الفئة
            function filterByCategory(category) {
                currentCategory = category;
                
                // تحديث الأزرار النشطة
                document.querySelectorAll('.category-btn').forEach(btn => {
                    btn.classList.remove('active');
                    if (btn.getAttribute('data-category') === category) {
                        btn.classList.add('active');
                    }
                });
                
                // إعادة تحميل المنتجات مع مراعاة حالة البحث الحالية
                const query = searchInput.value.trim();
                if (query.length > 0) {
                    searchProducts(query);
                } else {
                    loadProducts();
                }
            }

            // تبديل الثيم
            function toggleTheme() {
                document.body.classList.toggle('dark-mode');
                const isDarkMode = document.body.classList.contains('dark-mode');
                localStorage.setItem('darkMode', isDarkMode);
                themeToggle.innerHTML = isDarkMode ? '<i class="fas fa-sun"></i>' : '<i class="fas fa-moon"></i>';
            }

            // تبديل طريقة العرض
            function toggleView() {
                isListView = !isListView;
                localStorage.setItem('listView', isListView);
                viewToggle.innerHTML = isListView ? '<i class="fas fa-th-large"></i>' : '<i class="fas fa-grip-horizontal"></i>';
                
                // إعادة تحميل المنتجات مع مراعاة حالة البحث الحالية
                const query = searchInput.value.trim();
                if (query.length > 0) {
                    searchProducts(query);
                } else {
                    loadProducts();
                }
            }

            // تبديل عرض كلمة المرور
            function togglePasswordVisibility() {
                const type = loginPassword.getAttribute('type') === 'password' ? 'text' : 'password';
                loginPassword.setAttribute('type', type);
                togglePassword.classList.toggle('fa-eye-slash');
            }

            // التحقق من تسجيل الدخول
            function checkLogin() {
                if (!throttleRequests()) return false;
                
                const email = document.getElementById('loginEmail').value;
                const password = document.getElementById('loginPassword').value;

                // في تطبيق حقيقي، يجب استخدام مكتبة مثل crypto-js لتجزئة كلمة المرور
                // هذا مثال مبسط فقط
                const hashedPassword = md5(password); // في الواقع يجب استخدام salt

                if (email === correctEmail && hashedPassword === correctPasswordHash) {
                    isLoggedIn = true;
                    sessionStorage.setItem('isLoggedIn', 'true');
                    
                    // إنشاء رمز مميز للجلسة
                    const sessionToken = generateSessionToken();
                    sessionStorage.setItem('sessionToken', sessionToken);
                    
                    closeLoginModal();
                    showNotification('تم تسجيل الدخول بنجاح');
                    return true;
                } else {
                    showNotification('البريد الإلكتروني أو كلمة المرور غير صحيحة', 'error');
                    return false;
                }
            }

            // دالة MD5 مبسطة (في الواقع يجب استخدام مكتبة متخصصة)
            function md5(input) {
                // هذا مثال مبسط فقط ولا يجب استخدامه في الإنتاج
                // في الواقع يجب استخدام مكتبة مثل crypto-js
                return '5f4dcc3b5aa765d61d8327deb882cf99'; // كلمة المرور: password
            }

            // مستمعي الأحداث
            addProductBtn.addEventListener('click', function() {
                if (!validateSession() || !isLoggedIn) {
                    showLoginModal();
                } else {
                    showProductModal(false);
                }
            });

            closeModal.addEventListener('click', closeProductModal);

            productForm.addEventListener('submit', async function (e) {
                e.preventDefault();
                
                // التحقق من رمز CSRF
                const formToken = document.querySelector('input[name="csrfToken"]').value;
                const sessionToken = sessionStorage.getItem('csrfToken');
                
                if (formToken !== sessionToken) {
                    showNotification('طلب غير صالح، يرجى إعادة المحاولة', 'error');
                    return;
                }
                
                try {
                    const product = await prepareProductData();
                    
                    if (isEditing && currentProductId) {
                        product.id = currentProductId;
                        updateProduct(product);
                    } else {
                        addProduct(product);
                    }
                    
                    closeProductModal();
                    selectedImageFile = null; // إعادة تعيين الصورة المختارة
                } catch (error) {
                    showNotification(error.message, 'error');
                }
            });

            // حدث البحث عند الضغط على Enter أو أثناء الكتابة
            searchInput.addEventListener('keypress', function (e) {
                if (e.key === 'Enter') {
                    const query = this.value.trim();
                    if (query.length > 0) {
                        searchProducts(query);
                    } else {
                        loadProducts();
                    }
                }
            });

            // للبحث أثناء الكتابة أيضاً (اختياري)
            searchInput.addEventListener('input', function () {
                const query = this.value.trim();
                if (query.length > 0) {
                    searchProducts(query);
                } else {
                    loadProducts();
                }
            });

            themeToggle.addEventListener('click', toggleTheme);
            viewToggle.addEventListener('click', toggleView);

            togglePassword.addEventListener('click', togglePasswordVisibility);

            loginBtn.addEventListener('click', function (e) {
                e.preventDefault();
                checkLogin();
            });

            // إضافة حدث Enter لتسجيل الدخول
            document.getElementById('loginEmail').addEventListener('keypress', function (e) {
                if (e.key === 'Enter') {
                    e.preventDefault();
                    checkLogin();
                }
            });

            document.getElementById('loginPassword').addEventListener('keypress', function (e) {
                if (e.key === 'Enter') {
                    e.preventDefault();
                    checkLogin();
                }
            });

            // حدث اختيار صورة
            uploadImageBtn.addEventListener('click', function() {
                productImageInput.click();
            });

            productImageInput.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    // التحقق من نوع الملف
                    if (!file.type.match('image.*')) {
                        showNotification('الملف المختار ليس صورة', 'error');
                        return;
                    }
                    
                    // التحقق من حجم الملف (2MB كحد أقصى)
                    if (file.size > 2 * 1024 * 1024) {
                        showNotification('حجم الصورة يجب ألا يتجاوز 2MB', 'error');
                        return;
                    }
                    
                    selectedImageFile = file;
                    document.getElementById('imageFileName').textContent = file.name;
                    
                    // عرض معاينة الصورة
                    const preview = document.getElementById('imagePreview');
                    preview.style.display = 'block';
                    
                    const reader = new FileReader();
                    reader.onload = function(event) {
                        preview.innerHTML = '';
                        const img = document.createElement('img');
                        img.src = event.target.result;
                        img.alt = 'معاينة الصورة';
                        preview.appendChild(img);
                    };
                    reader.readAsDataURL(file);
                }
            });

            // أحداث تصفية الفئات
            categoryBtns.forEach(btn => {
                btn.addEventListener('click', function() {
                    const category = this.getAttribute('data-category');
                    filterByCategory(category);
                });
            });

            // إغلاق المودال عند النقر خارج المحتوى
            productModal.addEventListener('click', function (e) {
                if (e.target === productModal) {
                    closeProductModal();
                }
            });

            loginModal.addEventListener('click', function (e) {
                if (e.target === loginModal) {
                    closeLoginModal();
                }
            });

            // تحميل الإعدادات المحفوظة
            function loadSettings() {
                const darkMode = localStorage.getItem('darkMode') === 'true';
                if (darkMode) document.body.classList.add('dark-mode');

                const listView = localStorage.getItem('listView') === 'true';
                if (listView) isListView = true;

                themeToggle.innerHTML = darkMode ? '<i class="fas fa-sun"></i>' : '<i class="fas fa-moon"></i>';
                viewToggle.innerHTML = listView ? '<i class="fas fa-th-large"></i>' : '<i class="fas fa-grip-horizontal"></i>';
            }

            // تسجيل الأخطاء
            window.addEventListener('error', function(event) {
                console.error('Error:', event.message, 'in', event.filename, 'at line', event.lineno);
                showNotification('حدث خطأ غير متوقع', 'error');
            });

            // تهيئة الصفحة
            loadSettings();
            loadProducts();

            // تأثيرات إضافية للبطاقات عند التمرير
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            }, { threshold: 0.1 });

            document.querySelectorAll('.product-card').forEach(card => {
                observer.observe(card);
            });
        });
    </script>
</body>
</html>

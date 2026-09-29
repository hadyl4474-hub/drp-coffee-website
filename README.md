# drp-coffee-website
DRP Coffee - A responsive Arabic coffee shop website with menu filtering and product showcase
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>موقع كوفي DRP</title>
    <!-- استيراد خط تجوال العربي العصري -->
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;900&display=swap" rel="stylesheet">
    <!-- مكتبة أيقونات FontAwesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #2c221e;
            --accent-color: #c5a880;
            --bg-color: #f9f8f6;
            --card-bg: #ffffff;
            --text-main: #333333;
            --text-muted: #777777;
            --transition: all 0.3s ease;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Tajawal', sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            direction: rtl;
            text-align: right;
            line-height: 1.6;
        }

        /* الهيدر وشريط التنقل */
        header {
            background-color: var(--primary-color);
            color: #fff;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 10px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo-area {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-img {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid var(--accent-color);
        }

        .logo-text {
            font-size: 1.5rem;
            font-weight: 900;
            letter-spacing: 1px;
            color: var(--accent-color);
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 20px;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            font-weight: 500;
            font-size: 1rem;
            transition: var(--transition);
        }

        .nav-links a:hover {
            color: var(--accent-color);
        }

        .menu-toggle {
            display: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--accent-color);
        }

        /* القسم الرئيسي (Hero) */
        .hero {
            background: linear-gradient(rgba(44, 34, 30, 0.8), rgba(44, 34, 30, 0.8)), url('https://i.ibb.co/RTYdvXHF/IMG-3045.jpg');
            background-size: cover;
            background-position: center;
            height: 70vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: #fff;
            margin-top: 70px;
            padding: 0 20px;
        }

        .hero-content h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            color: var(--accent-color);
            font-weight: 900;
        }

        .hero-content p {
            font-size: 1.2rem;
            margin-bottom: 20px;
            color: #e0e0e0;
        }

        .btn-main {
            background-color: var(--accent-color);
            color: var(--primary-color);
            padding: 12px 30px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: 700;
            font-size: 1.1rem;
            transition: var(--transition);
            display: inline-block;
        }

        .btn-main:hover {
            background-color: #fff;
            transform: translateY(-3px);
        }

        /* محتوى الموقع والأقسام */
        .container {
            max-width: 1200px;
            margin: 40px auto;
            padding: 0 20px;
        }

        .section-title {
            text-align: center;
            font-size: 2.2rem;
            margin-bottom: 40px;
            color: var(--primary-color);
            position: relative;
            font-weight: 800;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 60px;
            height: 3px;
            background-color: var(--accent-color);
            margin: 10px auto 0;
            border-radius: 2px;
        }

        /* شريط تصنيفات المنيو */
        .categories-filter {
            display: flex;
            justify-content: center;
            gap: 12px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .filter-btn {
            background: #fff;
            border: 2px solid var(--accent-color);
            color: var(--primary-color);
            padding: 8px 20px;
            border-radius: 20px;
            cursor: pointer;
            font-weight: 600;
            font-size: 1rem;
            transition: var(--transition);
        }

        .filter-btn.active, .filter-btn:hover {
            background-color: var(--accent-color);
            color: #fff;
        }

        /* شبكة المنتجات (Cards) */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 25px;
            margin-bottom: 50px;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            transition: var(--transition);
            display: flex;
            flex-direction: column;
            border: 1px solid #eaeaea;
        }

        .card:hover {
            transform: translateY(-7px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }

        .card-img-container {
            width: 100%;
            height: 200px;
            overflow: hidden;
            background-color: #f1f1f1;
            position: relative;
        }

        .card-img-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }

        .card:hover .card-img-container img {
            transform: scale(1.05);
        }

        .card-body {
            padding: 20px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            flex-grow: 1;
        }

        .card-title {
            font-size: 1.2rem;
            font-weight: 700;
            margin-bottom: 10px;
            color: var(--primary-color);
        }

        .card-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 15px;
            border-top: 1px solid #f0f0f0;
            padding-top: 12px;
        }

        .price {
            font-size: 1.2rem;
            font-weight: 900;
            color: var(--accent-color);
        }

        .badge-top {
            background-color: #d4af37;
            color: white;
            padding: 4px 10px;
            border-radius: 8px;
            font-size: 0.8rem;
            font-weight: 700;
        }

        /* قسم عنا (About Us) */
        .about-section {
            background-color: #fff;
            padding: 50px;
            border-radius: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            text-align: center;
            margin-bottom: 60px;
        }

        .about-section p {
            font-size: 1.1rem;
            color: var(--text-muted);
            max-width: 800px;
            margin: 0 auto;
            line-height: 1.8;
        }

        /* الفوتر (Footer) */
        footer {
            background-color: var(--primary-color);
            color: #fff;
            text-align: center;
            padding: 30px 20px;
            margin-top: 50px;
        }

        footer p {
            color: #aaa;
            font-size: 0.95rem;
        }

        /* استجابة الشاشات الصغيرة */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
                flex-direction: column;
                position: absolute;
                top: 70px;
                right: 0;
                width: 100%;
                background-color: var(--primary-color);
                padding: 20px;
                text-align: center;
                box-shadow: 0 10px 15px rgba(0,0,0,0.2);
            }

            .nav-links.active {
                display: flex;
            }

            .menu-toggle {
                display: block;
            }

            .hero-content h1 {
                font-size: 2.2rem;
            }
        }
    </style>
</head>
<body>

    <!-- الهيدر -->
    <header>
        <div class="nav-container">
            <div class="logo-area">
                <img src="https://i.ibb.co/RTYdvXHF/IMG-3045.jpg" alt="DRP Logo" class="logo-img">
                <span class="logo-text">DRP COFFEE</span>
            </div>
            <div class="menu-toggle" id="mobile-menu">
                <i class="fas fa-bars"></i>
            </div>
            <ul class="nav-links">
                <li><a href="#home">الرئيسية</a></li>
                <li><a href="#top3">توب ثلاثة</a></li>
                <li><a href="#menu">المنيو</a></li>
                <li><a href="#about">عنا</a></li>
            </ul>
        </div>
    </header>

    <!-- واجهة البداية -->
    <section class="hero" id="home">
        <div class="hero-content">
            <h1>كوفي DRP</h1>
            <p>ذوق مميز وأجود أنوع القهوة والحلى الطازج</p>
            <a href="#menu" class="btn-main">استعرض المنيو</a>
        </div>
    </section>

    <div class="container">

        <!-- قسم توب ثلاثة -->
        <section id="top3">
            <h2 class="section-title">توب ثلاثة ⭐</h2>
            <div class="grid">
                <div class="card">
                    <div class="card-img-container">
                        <img src="https://i.ibb.co/JF2Jw50B/IMG-2998.jpg" alt="ايس كريم شوكو فانيليا كيك" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'">
                    </div>
                    <div class="card-body">
                        <h3 class="card-title">ايس كريم شوكو فانيليا كيك</h3>
                        <div class="card-footer">
                            <span class="price">٢٠ ر.س</span>
                            <span class="badge-top">الأكثر طلباً</span>
                        </div>
                    </div>
                </div>

                <div class="card">
                    <div class="card-img-container">
                        <img src="https://i.ibb.co/Ld7YXqcm/IMG-2998.jpg" alt="كيكة البيكان" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'">
                    </div>
                    <div class="card-body">
                        <h3 class="card-title">كيكة البيكان</h3>
                        <div class="card-footer">
                            <span class="price">٢٢ ر.س</span>
                            <span class="badge-top">الأكثر طلباً</span>
                        </div>
                    </div>
                </div>

                <div class="card">
                    <div class="card-img-container">
                        <img src="https://i.ibb.co/3mDztyFm/IMG-2998.jpg" alt="دولتشي كيك" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'">
                    </div>
                    <div class="card-body">
                        <h3 class="card-title">دولتشي كيك</h3>
                        <div class="card-footer">
                            <span class="price">٢٠ ر.س</span>
                            <span class="badge-top">الأكثر طلباً</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- قسم المنيو الشامل -->
        <section id="menu">
            <h2 class="section-title">قائمة المنيو</h2>
            
            <div class="categories-filter">
                <button class="filter-btn active" onclick="filterMenu('all')">الكل</button>
                <button class="filter-btn" onclick="filterMenu('hot')">مشروبات ساخنة</button>
                <button class="filter-btn" onclick="filterMenu('cold')">مشروبات باردة</button>
                <button class="filter-btn" onclick="filterMenu('dessert')">الحلى والكيك</button>
            </div>

            <div class="grid" id="menu-grid">
                <!-- المشروبات الساخنة -->
                <div class="card" data-category="hot">
                    <div class="card-img-container"><img src="https://i.ibb.co/b5FjHJFv/IMG-2998.jpg" alt="قهوة اليوم حار" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">قهوة اليوم حار</h3><div class="card-footer"><span class="price">٦ ر.س</span></div></div>
                </div>

                <div class="card" data-category="hot">
                    <div class="card-img-container"><img src="https://i.ibb.co/PZV0D4P0/IMG-2998.jpg" alt="كابتشينو" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">كابتشينو</h3><div class="card-footer"><span class="price">١٥ ر.س</span></div></div>
                </div>

                <div class="card" data-category="hot">
                    <div class="card-img-container"><img src="https://i.ibb.co/PZV0D4P0/IMG-2998.jpg" alt="لاتيه حار" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">لاتيه حار</h3><div class="card-footer"><span class="price">١٦ ر.س</span></div></div>
                </div>

                <div class="card" data-category="hot">
                    <div class="card-img-container"><img src="https://i.ibb.co/qYnZvnws/IMG-2998.jpg" alt="سبانش حار" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">سبانش حار</h3><div class="card-footer"><span class="price">١٦ ر.س</span></div></div>
                </div>

                <div class="card" data-category="hot">
                    <div class="card-img-container"><img src="https://i.ibb.co/VW2j351t/IMG-2998.jpg" alt="فلات وايت" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">فلات وايت</h3><div class="card-footer"><span class="price">١٤ ر.س</span></div></div>
                </div>

                <div class="card" data-category="hot">
                    <div class="card-img-container"><img src="https://i.ibb.co/8LZGWFmM/IMG-2998.jpg" alt="اسبرسو" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">اسبرسو</h3><div class="card-footer"><span class="price">١٠ ر.س</span></div></div>
                </div>

                <div class="card" data-category="hot">
                    <div class="card-img-container"><img src="https://i.ibb.co/BVH22rdc/IMG-2998.jpg" alt="كورتادو" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">كورتادو</h3><div class="card-footer"><span class="price">١١ ر.س</span></div></div>
                </div>

                <div class="card" data-category="hot">
                    <div class="card-img-container"><img src="https://i.ibb.co/9kbtwg9w/IMG-2998.jpg" alt="V60 حار" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">V60 حار</h3><div class="card-footer"><span class="price">١٢ ر.س</span></div></div>
                </div>

                <!-- المشروبات الباردة -->
                <div class="card" data-category="cold">
                    <div class="card-img-container"><img src="https://i.ibb.co/wr0YXKxJ/IMG-2998.jpg" alt="قهوة اليوم بارد" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">قهوة اليوم بارد</h3><div class="card-footer"><span class="price">٧ ر.س</span></div></div>
                </div>

                <div class="card" data-category="cold">
                    <div class="card-img-container"><img src="https://i.ibb.co/WNgxZ3Q2/IMG-2998.jpg" alt="قهوة اليوم بارد" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">قهوة اليوم بارد كبير</h3><div class="card-footer"><span class="price">٩ ر.س</span></div></div>
                </div>

                <div class="card" data-category="cold">
                    <div class="card-img-container"><img src="https://i.ibb.co/9kbtwg9w/IMG-2998.jpg" alt="V60 بارد" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">V60 بارد</h3><div class="card-footer"><span class="price">١٢ ر.س</span></div></div>
                </div>

                <div class="card" data-category="cold">
                    <div class="card-img-container"><img src="https://i.ibb.co/21DpCtst/IMG-2998.jpg" alt="سبانش لاتيه بارد" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">سبانش لاتيه بارد</h3><div class="card-footer"><span class="price">١٧ ر.س</span></div></div>
                </div>

                <div class="card" data-category="cold">
                    <div class="card-img-container"><img src="https://i.ibb.co/XxdWYQtS/IMG-2998.jpg" alt="لاتيه بارد" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">لاتيه بارد</h3><div class="card-footer"><span class="price">١٦ ر.س</span></div></div>
                </div>

                <div class="card" data-category="cold">
                    <div class="card-img-container"><img src="https://i.ibb.co/1YhNg8Mh/IMG-2998.jpg" alt="امريكانو" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">امريكانو</h3><div class="card-footer"><span class="price">١٢ ر.س</span></div></div>
                </div>

                <div class="card" data-category="cold">
                    <div class="card-img-container"><img src="https://i.ibb.co/DD54qCry/IMG-2998.jpg" alt="الفريدو" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">الفريدو</h3><div class="card-footer"><span class="price">١٢ ر.س</span></div></div>
                </div>

                <div class="card" data-category="cold">
                    <div class="card-img-container"><img src="https://i.ibb.co/GQ6Bpr5V/IMG-2998.jpg" alt="كركديه" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">كركديه</h3><div class="card-footer"><span class="price">١٠ ر.س</span></div></div>
                </div>

                <div class="card" data-category="cold">
                    <div class="card-img-container"><img src="https://i.ibb.co/B50FDPFy/IMG-2998.jpg" alt="ماتشا" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">ماتشا</h3><div class="card-footer"><span class="price">١٩ ر.س</span></div></div>
                </div>

                <div class="card" data-category="cold">
                    <div class="card-img-container"><img src="https://i.ibb.co/MxD198CS/IMG-2998.jpg" alt="موهيتو" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">موهيتو</h3><div class="card-footer"><span class="price">١٠ ر.س</span></div></div>
                </div>

                <div class="card" data-category="cold">
                    <div class="card-img-container"><img src="https://i.ibb.co/HLY9RHwR/IMG-2998.jpg" alt="ايس تي" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">ايس تي</h3><div class="card-footer"><span class="price">١٢ ر.س</span></div></div>
                </div>

                <!-- الحلى والكيك -->
                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/rKc3dwtP/IMG-2998.jpg" alt="كوكيز" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">كوكيز</h3><div class="card-footer"><span class="price">١٢ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/tprssktH/IMG-2998.jpg" alt="سان سبستيان" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">سان سبستيان</h3><div class="card-footer"><span class="price">١٨ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/1fJCZZyK/IMG-2998.jpg" alt="كيكة شوكولاتة" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">كيكة شوكولاتة</h3><div class="card-footer"><span class="price">١٦ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/r2k7JWKM/IMG-2998.jpg" alt="تشيز بيكان" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">تشيز بيكان</h3><div class="card-footer"><span class="price">١٨ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/SDvQy6Qq/IMG-2998.jpg" alt="تشيز مدريد" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">تشيز مدريد</h3><div class="card-footer"><span class="price">١٩ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/3mDztyFm/IMG-2998.jpg" alt="دولتشي كيك" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">دولتشي كيك</h3><div class="card-footer"><span class="price">٢٠ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/PykP0rq/IMG-2998.jpg" alt="بودنج شوكولاته" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">بودنج شوكولاته</h3><div class="card-footer"><span class="price">١٨ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/QFSgrSmm/IMG-2998.jpg" alt="كيكة جلاكسي" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">كيكة جلاكسي</h3><div class="card-footer"><span class="price">٢٠ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/JF2Jw50B/IMG-2998.jpg" alt="ايس كريم شوكو فانيليا كيك" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">ايس كريم شوكو فانيليا كيك</h3><div class="card-footer"><span class="price">٢٠ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/Cs1B5qYH/IMG-2998.jpg" alt="لافا مولتن كيك" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">لافا مولتن كيك</h3><div class="card-footer"><span class="price">٢٠ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/gLnc5pSr/IMG-2998.jpg" alt="كيكة لندن" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">كيكة لندن</h3><div class="card-footer"><span class="price">٢٠ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/8gmSHmSC/d5fa9f06-a0e8-4c42-9edd-4fad87e5ec56.jpg" alt="بودنق كوكز" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">بودنق كوكز</h3><div class="card-footer"><span class="price">١٨ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/Jw3gwtzh/IMG-2998.jpg" alt="كيكة D R P" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">كيكة D R P</h3><div class="card-footer"><span class="price">١٥ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/Ld7YXqcm/IMG-2998.jpg" alt="كيكة البيكان" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">كيكة البيكان</h3><div class="card-footer"><span class="price">٢٢ ر.س</span></div></div>
                </div>

                <div class="card" data-category="dessert">
                    <div class="card-img-container"><img src="https://i.ibb.co/YFFDshT7/IMG-2998.jpg" alt="ترافل بيكان" onerror="this.src='https://i.ibb.co/RTYdvXHF/IMG-3045.jpg'"></div>
                    <div class="card-body"><h3 class="card-title">ترافل بيكان</h3><div class="card-footer"><span class="price">١٨ ر.س</span></div></div>
                </div>
            </div>
        </section>

        <!-- قسم عنا -->
        <section id="about" class="about-section">
            <h2 class="section-title">عنا</h2>
            <p>نحن في كوفي <strong>DRP</strong> نؤمن بأن كل كوب قهوة نصنعه يحمل قصة شغف وجودة عالية. نقدم لكم أجود أنواع الحبوب المختارة بعناية وألذ أصناف الحلى الطازج لنضمن لكم تجربة استثنائية ترضي جميع الأذواق.</p>
        </section>

    </div>

    <!-- الفوتر -->
    <footer>
        <div style="display: flex; align-items: center; justify-content: center; gap: 10px; margin-bottom: 10px;">
            <img src="https://i.ibb.co/RTYdvXHF/IMG-3045.jpg" alt="Logo" style="width: 30px; height: 30px; border-radius: 50%;">
            <span style="font-weight: bold; color: var(--accent-color);">DRP COFFEE</span>
        </div>
        <p>رقم المصمم الموقع ٠٥٥٠٠٩٣٦١٣ اسم علي عسيري </p>
    </footer>

    <!-- جافاسكريبت للتحكم بالقائمة وتصنيف المنيو -->
    <script>
        // إظهار وإخفاء القائمة في الجوال
        const mobileMenu = document.getElementById('mobile-menu');
        const navLinks = document.querySelector('.nav-links');

        mobileMenu.addEventListener('click', () => {
            navLinks.classList.toggle('active');
        });

        // فلترة المنيو حسب التصنيف
        function filterMenu(category) {
            const buttons = document.querySelectorAll('.filter-btn');
            buttons.forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');

            const cards = document.querySelectorAll('#menu-grid .card');
            cards.forEach(card => {
                if (category === 'all' || card.getAttribute('data-category') === category) {
                    card.style.display = 'flex';
                } else {
                    card.style.display = 'none';
                }
            });
        }
    </script>
</body>
</html>

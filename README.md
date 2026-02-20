<!DOCTYPE html>
<html lang="he">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>בגרות בחנ"ג תיכון אחד העם תשפ"ו</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --success: #27ae60;
            --warning: #f39c12;
            --danger: #e74c3c;
            --light: #ecf0f1;
            --dark: #34495e;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            min-height: 100vh;
            color: #333;
            line-height: 1.6;
            direction: rtl;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            margin-bottom: 40px;
            padding: 30px;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            color: white;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        
        header h2 {
            font-size: 1.8rem;
            font-weight: 300;
            color: var(--light);
        }
        
        .screen {
            display: none;
            background: white;
            border-radius: 10px;
            padding: 30px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
        }
        
        .screen.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .btn-group {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin: 30px 0;
            flex-wrap: wrap;
        }
        
        .btn {
            padding: 15px 30px;
            font-size: 1.1rem;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            min-width: 200px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        .btn-primary {
            background: var(--secondary);
            color: white;
        }
        
        .btn-primary:hover {
            background: #2980b9;
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        
        .btn-secondary {
            background: var(--warning);
            color: white;
        }
        
        .btn-secondary:hover {
            background: #e67e22;
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        
        .btn-success {
            background: var(--success);
            color: white;
        }
        
        .btn-danger {
            background: var(--danger);
            color: white;
        }
        
        .btn-back {
            background: var(--dark);
            color: white;
            padding: 10px 20px;
            margin-bottom: 20px;
            display: inline-flex;
            align-items: center;
            gap: 5px;
        }
        
        .btn-main-home {
            background: var(--primary);
            color: white;
            padding: 10px 20px;
            margin-bottom: 20px;
            display: inline-flex;
            align-items: center;
            gap: 5px;
        }
        
        .btn-save {
            background: var(--success);
            color: white;
            padding: 15px 30px;
            font-size: 1.1rem;
            margin: 20px auto;
            display: block;
        }
        
        .btn-small {
            padding: 5px 10px;
            font-size: 0.9rem;
            min-width: auto;
        }
        
        .info-box {
            background: #e8f4fc;
            padding: 20px;
            border-radius: 8px;
            margin: 20px 0;
            border-left: 5px solid var(--secondary);
        }
        
        .info-box h3 {
            color: var(--primary);
            margin-bottom: 10px;
        }
        
        .tests-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }
        
        .test-card {
            background: var(--light);
            padding: 25px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            border-left: 5px solid var(--secondary);
        }
        
        .test-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .test-card h3 {
            color: var(--primary);
            margin-bottom: 10px;
        }
        
        .classes-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 15px;
            margin: 30px 0;
        }
        
        .class-card {
            background: white;
            padding: 20px;
            text-align: center;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 2px solid var(--light);
            position: relative;
            min-height: 100px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
        
        .class-card:hover {
            border-color: var(--secondary);
            transform: scale(1.05);
        }
        
        .class-card.active {
            border-color: var(--secondary);
            background: var(--light);
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            direction: rtl;
        }
        
        th {
            background: var(--primary);
            color: white;
            padding: 15px;
            text-align: right;
            font-weight: 600;
        }
        
        td {
            padding: 12px 15px;
            border-bottom: 1px solid #eee;
            text-align: right;
        }
        
        tr:hover {
            background: #f9f9f9;
        }
        
        input[type="number"],
        input[type="text"],
        select {
            width: 100%;
            padding: 8px 12px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
            text-align: center;
        }
        
        .result-badge {
            display: inline-block;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 0.9rem;
            font-weight: bold;
            text-align: center;
            min-width: 50px;
        }
        
        .excellent { background: #d4edda; color: #155724; }
        .good { background: #d1ecf1; color: #0c5460; }
        .average { background: #fff3cd; color: #856404; }
        .poor { background: #f8d7da; color: #721c24; }
        
        .summary-box {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px;
            border-radius: 10px;
            margin: 30px 0;
        }
        
        .progress-container {
            margin: 20px 0;
        }
        
        .progress-bar {
            height: 10px;
            background: #eee;
            border-radius: 5px;
            overflow: hidden;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(to right, var(--success), var(--secondary));
            transition: width 0.5s ease;
        }
        
        .ranking {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 15px;
            border-bottom: 1px solid #eee;
            transition: all 0.3s ease;
        }
        
        .ranking:hover {
            background: #f5f7fa;
        }
        
        .rank-number {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--primary);
            min-width: 50px;
            text-align: center;
        }
        
        .legend {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin: 20px 0;
            flex-wrap: wrap;
        }
        
        .legend-item {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .legend-color {
            width: 20px;
            height: 20px;
            border-radius: 4px;
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 25px;
            border-radius: 5px;
            color: white;
            font-weight: 600;
            z-index: 1000;
            animation: slideIn 0.3s ease;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        @keyframes slideIn {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
        
        .notification.success { background: var(--success); }
        .notification.error { background: var(--danger); }
        .notification.warning { background: var(--warning); }
        .notification.info { background: var(--secondary); }
        
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid #f3f3f3;
            border-top: 3px solid var(--secondary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* חיפוש וסינון */
        .filters-container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            margin: 20px 0;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .filters-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }
        
        .filter-group {
            display: flex;
            flex-direction: column;
        }
        
        .filter-group label {
            margin-bottom: 5px;
            font-weight: 600;
            color: var(--primary);
        }
        
        .search-container {
            margin: 20px 0;
            position: relative;
        }
        
        .search-input {
            width: 100%;
            padding: 12px 20px;
            padding-left: 45px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: all 0.3s;
        }
        
        .search-input:focus {
            border-color: var(--secondary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
        }
        
        .search-icon {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: #777;
        }
        
        .search-results {
            margin-top: 10px;
            font-size: 0.9rem;
            color: #666;
        }
        
        .no-results {
            text-align: center;
            padding: 20px;
            color: #666;
            font-style: italic;
        }
        
        .clear-search {
            position: absolute;
            left: 45px;
            top: 50%;
            transform: translateY(-50%);
            background: none;
            border: none;
            color: #999;
            cursor: pointer;
            font-size: 1.2rem;
        }
        
        .clear-search:hover {
            color: var(--danger);
        }
        
        .final-grade {
            font-size: 1.2rem;
            font-weight: bold;
            color: var(--primary);
        }
        
        .weights-table {
            font-size: 0.9rem;
            margin: 10px 0;
        }
        
        .weights-table td {
            padding: 5px 10px;
        }
        
        .status-badge {
            display: inline-block;
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 0.8rem;
            font-weight: bold;
        }
        
        /* תרשים התקדמות */
        .progress-chart-container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            margin: 20px 0;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .chart-controls {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }
        
        .chart-controls select {
            padding: 8px 12px;
            border: 1px solid #ddd;
            border-radius: 4px;
            min-width: 150px;
        }
        
        .chart-canvas-container {
            position: relative;
            height: 300px;
            margin: 20px 0;
        }
        
        /* כרטיס תלמיד בדירוג */
        .student-card {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin: 15px 0;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            border-left: 5px solid var(--secondary);
        }
        
        .student-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
        }
        
        .student-card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .student-card-body {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
        }
        
        .student-test-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 8px 12px;
            background: #f9f9f9;
            border-radius: 4px;
        }
        
        .student-test-item .test-name {
            font-weight: 600;
        }
        
        .student-test-item .test-grade {
            font-weight: bold;
            color: var(--primary);
        }
        
        /* כפתור הראה/הסתר גרף */
        .toggle-chart-btn {
            background: var(--secondary);
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 0.8rem;
            margin-left: 10px;
        }
        
        .toggle-chart-btn:hover {
            background: #2980b9;
        }
        
        /* תוספת לתיקון: כפתור פעיל בדירוג */
        .btn.active {
            transform: scale(1.05);
            box-shadow: 0 0 10px rgba(0,0,0,0.3);
        }
        
        @media (max-width: 768px) {
            .btn {
                min-width: 100%;
            }
            
            .tests-grid {
                grid-template-columns: 1fr;
            }
            
            .classes-grid {
                grid-template-columns: repeat(3, 1fr);
            }
            
            table {
                font-size: 0.9rem;
            }
            
            th, td {
                padding: 8px 10px;
            }
            
            .filters-grid {
                grid-template-columns: 1fr;
            }
            
            .student-card-body {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>בגרות בחנ"ג</h1>
            <h2>תיכון אחד העם תשפ"ו</h2>
        </header>
        
        <!-- מסך ראשי עם אפשרויות -->
        <div id="mainScreen" class="screen active">
            <div class="btn-group">
                <button class="btn btn-primary" id="boysBtn">
                    <i class="fas fa-male"></i>
                    <div>
                        <h3 style="margin: 0;">תלמידים</h3>
                        <p style="font-size: 0.9rem; margin: 5px 0 0 0; font-weight: normal;">
                            מתח, שכיבות שמיכה, דלגית, ריצה עם כדורי כוח, ריצת 2,000
                        </p>
                    </div>
                </button>
                <button class="btn btn-secondary" id="girlsBtn">
                    <i class="fas fa-female"></i>
                    <div>
                        <h3 style="margin: 0;">תלמידות</h3>
                        <p style="font-size: 0.9rem; margin: 5px 0 0 0; font-weight: normal;">
                            מתח עם גומייה, שכיבות שמיכה ברכיים, שכיבות שמיכה רגיל, מעבר סולם, דלגית, פלאנק, ריצת 2,000
                        </p>
                    </div>
                </button>
            </div>
            
            <div class="btn-group">
                <button class="btn btn-success" id="rankingBtn">
                    <i class="fas fa-chart-line"></i>
                    <div>
                        <h3 style="margin: 0;">צפייה בדירוג שכבה</h3>
                        <p style="font-size: 0.9rem; margin: 5px 0 0 0; font-weight: normal;">
                            דירוג כללי לפי כיתות, בנים ובנות בנפרד
                        </p>
                    </div>
                </button>
            </div>
            
            <div class="info-box">
                <h3><i class="fas fa-info-circle"></i> מידע על המערכת</h3>
                <p>המערכת כוללת את כל תלמידי שכבה יב' (כיתות 1-12) עם נתונים מלאים.</p>
                <p>סה"כ תלמידים במערכת: <strong id="totalStudentsCount">טוען...</strong></p>
                <p>כבר נטענו ציוני מבחן עיוני מתוך אקסל!</p>
                <p>בחר "תלמידים" או "תלמידות" כדי להתחיל בהזנת ציונים.</p>
                <button class="btn btn-small" id="debugGirlsBtn">
                    <i class="fas fa-user-female"></i> בדיקת נתוני בנות
                </button>
                <button class="btn btn-small" id="debugBoysBtn">
                    <i class="fas fa-user-male"></i> בדיקת נתוני בנים
                </button>
                <button class="btn btn-small" id="debugSystemBtn">
                    <i class="fas fa-bug"></i> בדיקת מערכת
                </button>
                <button class="btn btn-small" id="loadTheoryBtn">
                    <i class="fas fa-file-excel"></i> טען ציוני מבחן עיוני
                </button>
                <button class="btn btn-small" id="testPushupsBtn">
                    <i class="fas fa-hand-paper"></i> בדוק טבלת שכיבות שמיכה
                </button>
                <button class="btn btn-small" id="testConversionTablesBtn">
                    <i class="fas fa-table"></i> בדוק טבלאות המרה
                </button>
                <button class="btn btn-small" id="testGirlsTableBtn">
                    <i class="fas fa-female"></i> בדוק טבלת בנות
                </button>
                <button class="btn btn-small" id="testGirlsRunningBtn">
                    <i class="fas fa-running"></i> בדוק חוקי ריצת בנות
                </button>
                <button class="btn btn-small" id="testCalculationBtn">
                    <i class="fas fa-calculator"></i> בדוק חישוב ציון לדוגמה
                </button>
            </div>
        </div>
        
        <!-- מסך בחירת כיתה -->
        <div id="classScreen" class="screen">
            <button class="btn btn-back" id="backFromClassBtn">
                <i class="fas fa-arrow-right"></i> חזרה למסך הראשי
            </button>
            <button class="btn btn-main-home" id="homeFromClassBtn" style="margin-right: 10px;">
                <i class="fas fa-home"></i> חזרה למסך ראשי
            </button>
            <h2 id="classScreenTitle"></h2>
            <div class="classes-grid" id="classesGrid"></div>
        </div>
        
        <!-- מסך בחירת מבחן -->
        <div id="testScreen" class="screen">
            <button class="btn btn-back" id="backFromTestBtn">
                <i class="fas fa-arrow-right"></i> חזרה לבחירת כיתה
            </button>
            <button class="btn btn-main-home" id="homeFromTestBtn" style="margin-right: 10px;">
                <i class="fas fa-home"></i> חזרה למסך ראשי
            </button>
            <h2 id="testScreenTitle"></h2>
            <div class="tests-grid" id="testsGrid"></div>
        </div>
        
        <!-- מסך הזנת תוצאות -->
        <div id="resultsScreen" class="screen">
            <button class="btn btn-back" id="backFromResultsBtn">
                <i class="fas fa-arrow-right"></i> חזרה לבחירת מבחן
            </button>
            <button class="btn btn-main-home" id="homeFromResultsBtn" style="margin-right: 10px;">
                <i class="fas fa-home"></i> חזרה למסך ראשי
            </button>
            <h2 id="resultsScreenTitle"></h2>
            <div id="resultsTable"></div>
            <button class="btn btn-save" id="saveResultsBtn">
                <i class="fas fa-save"></i> שמור תוצאות
            </button>
        </div>
        
        <!-- מסך דירוג שכבה -->
        <div id="rankingScreen" class="screen">
            <button class="btn btn-back" id="backFromRankingBtn">
                <i class="fas fa-arrow-right"></i> חזרה למסך הראשי
            </button>
            <button class="btn btn-main-home" id="homeFromRankingBtn" style="margin-right: 10px;">
                <i class="fas fa-home"></i> חזרה למסך ראשי
            </button>
            <h2>דירוג שכבה יב'</h2>
            <div class="info-box">
                <h3><i class="fas fa-info-circle"></i> חישוב ציונים סופיים</h3>
                <p><strong>לבנים:</strong> ריצה (20%) + עיוני (20%) + דלגית (15%) + שכיבות (15%) + מתח (15%) + כדורי כוח (15%)</p>
                <p><strong>לבנות:</strong> עיוני (20%) + ריצה (20%) + דלגית (15%) + שכיבות שמיכה (ברכיים או מלא - 15%) + מתח עם גומיה או מעבר סולם (15%) + פלאנק (15%)</p>
                <p class="final-grade">תלמידים עם ציונים חסרים מקבלים ציון יחסי למה שיש!</p>
            </div>
            <div class="btn-group">
                <button class="btn btn-primary active" id="rankingAllBtn">
                    <i class="fas fa-users"></i> כל השכבה (בנים ובנות)
                </button>
                <button class="btn btn-secondary" id="rankingBoysBtn">
                    <i class="fas fa-male"></i> בנים בלבד
                </button>
                <button class="btn btn-secondary" id="rankingGirlsBtn">
                    <i class="fas fa-female"></i> בנות בלבד
                </button>
            </div>
            
            <!-- סינון מתקדם -->
            <div class="filters-container">
                <h3><i class="fas fa-filter"></i> סינון מתקדם</h3>
                <div class="filters-grid">
                    <div class="filter-group">
                        <label for="filterName">חיפוש לפי שם:</label>
                        <div class="search-container">
                            <i class="fas fa-search search-icon"></i>
                            <input type="text" id="filterName" class="search-input" placeholder="שם פרטי או משפחה...">
                            <button id="clearNameBtn" class="clear-search" style="display: none;">
                                <i class="fas fa-times"></i>
                            </button>
                        </div>
                    </div>
                    
                    <div class="filter-group">
                        <label for="filterClass">סינון לפי כיתה:</label>
                        <select id="filterClass">
                            <option value="all">כל הכיתות</option>
                            <option value="1">יב'1</option>
                            <option value="2">יב'2</option>
                            <option value="3">יב'3</option>
                            <option value="4">יב'4</option>
                            <option value="5">יב'5</option>
                            <option value="6">יב'6</option>
                            <option value="7">יב'7</option>
                            <option value="8">יב'8</option>
                            <option value="9">יב'9</option>
                            <option value="10">יב'10</option>
                            <option value="11">יב'11</option>
                            <option value="12">יב'12</option>
                        </select>
                    </div>
                    
                    <div class="filter-group">
                        <label for="filterStatus">סינון לפי סטטוס:</label>
                        <select id="filterStatus">
                            <option value="all">כל הסטטוסים</option>
                            <option value="full">מלא (כל הציונים)</option>
                            <option value="partial">חלקי (50% ומעלה)</option>
                            <option value="low">מועט (פחות מ-50%)</option>
                            <option value="none">ללא ציונים</option>
                        </select>
                    </div>
                    
                    <div class="filter-group">
                        <label for="filterGender">סינון לפי מגדר:</label>
                        <select id="filterGender">
                            <option value="all">בנים ובנות</option>
                            <option value="boys">בנים בלבד</option>
                            <option value="girls">בנות בלבד</option>
                        </select>
                    </div>
                </div>
                
                <div style="display: flex; gap: 10px; margin-top: 15px;">
                    <button class="btn btn-primary" id="applyFiltersBtn" style="padding: 10px 20px;">
                        <i class="fas fa-filter"></i> החל סינון
                    </button>
                    <button class="btn btn-secondary" id="resetFiltersBtn" style="padding: 10px 20px;">
                        <i class="fas fa-redo"></i> אפס סינון
                    </button>
                </div>
            </div>
            
            <!-- תרשים התקדמות -->
            <div class="progress-chart-container" id="progressChartContainer" style="display: none;">
                <h3><i class="fas fa-chart-line"></i> תרשים התקדמות לתלמיד</h3>
                <div class="chart-controls">
                    <select id="chartStudentSelect">
                        <option value="">בחר תלמיד...</option>
                    </select>
                    <select id="chartTypeSelect">
                        <option value="bar">תרשים עמודות</option>
                        <option value="line">תרשים קווי</option>
                        <option value="radar">תרשים מכ"ם</option>
                    </select>
                    <button class="btn btn-small" id="closeChartBtn">
                        <i class="fas fa-times"></i> סגור תרשים
                    </button>
                </div>
                <div class="chart-canvas-container">
                    <canvas id="progressChart"></canvas>
                </div>
            </div>
            
            <div id="rankingResults"></div>
        </div>
    </div>

    <!-- אזור להתראות -->
    <div id="notificationArea"></div>

    <script>
        // נתוני המערכת
        let currentGender = null;
        let currentClass = null;
        let currentTest = null;
        let currentTestType = null;
        let students = [];
        let allTestResults = {};
        let currentChart = null;
        
        // ============================================
        // טבלאות המרה מהקובץ האקסל
        // ============================================
        
        // טבלת המרה עבור ריצה עם כדורי כוח (זמן בשניות → ציון)
        const medicineBallTable = [
            {time: 30, score: 100},
            {time: 29.5, score: 99},
            {time: 29, score: 98},
            {time: 28.5, score: 97},
            {time: 28, score: 96},
            {time: 27.5, score: 95},
            {time: 27, score: 94},
            {time: 26.5, score: 93},
            {time: 26, score: 92},
            {time: 25.5, score: 91},
            {time: 25, score: 90},
            {time: 24.5, score: 89},
            {time: 24, score: 88},
            {time: 23.5, score: 87},
            {time: 23, score: 86},
            {time: 22.5, score: 85},
            {time: 22, score: 84},
            {time: 21.5, score: 83},
            {time: 21, score: 82},
            {time: 20.5, score: 81},
            {time: 20, score: 80},
            {time: 19.5, score: 77},
            {time: 19, score: 75},
            {time: 18.5, score: 72},
            {time: 18, score: 70},
            {time: 17.5, score: 67},
            {time: 17, score: 65},
            {time: 16.5, score: 62},
            {time: 16, score: 60},
            {time: 15.5, score: 57},
            {time: 15, score: 55},
            {time: 14.5, score: 52},
            {time: 14, score: 50},
            {time: 13.5, score: 47},
            {time: 13, score: 45},
            {time: 12.5, score: 42},
            {time: 12, score: 40},
            {time: 11.5, score: 37},
            {time: 11, score: 35},
            {time: 10.5, score: 32},
            {time: 10, score: 30}
        ];
        
        // טבלת המרה עבור ריצת 2,000 מטר (זמן בפורמט MM:SS → ציון)
        const running2000Table = [
            {time: "07:00", score: 100},
            {time: "07:03", score: 99},
            {time: "07:06", score: 98},
            {time: "07:09", score: 97},
            {time: "07:12", score: 96},
            {time: "07:15", score: 95},
            {time: "07:18", score: 94},
            {time: "07:21", score: 93},
            {time: "07:24", score: 92},
            {time: "07:27", score: 91},
            {time: "07:30", score: 90},
            {time: "07:34", score: 89},
            {time: "07:38", score: 88},
            {time: "07:42", score: 87},
            {time: "07:46", score: 86},
            {time: "07:50", score: 85},
            {time: "07:54", score: 84},
            {time: "07:58", score: 83},
            {time: "08:02", score: 82},
            {time: "08:06", score: 81},
            {time: "08:10", score: 80},
            {time: "08:15", score: 79},
            {time: "08:20", score: 78},
            {time: "08:25", score: 77},
            {time: "08:30", score: 76},
            {time: "08:35", score: 75},
            {time: "08:40", score: 74},
            {time: "08:45", score: 73},
            {time: "08:50", score: 72},
            {time: "08:55", score: 71},
            {time: "09:00", score: 70},
            {time: "09:06", score: 69},
            {time: "09:12", score: 68},
            {time: "09:18", score: 67},
            {time: "09:24", score: 66},
            {time: "09:30", score: 65},
            {time: "09:37", score: 64},
            {time: "09:44", score: 63},
            {time: "09:51", score: 62},
            {time: "09:58", score: 61},
            {time: "10:05", score: 60},
            {time: "10:12", score: 59},
            {time: "10:19", score: 58},
            {time: "10:26", score: 57},
            {time: "10:33", score: 56},
            {time: "10:40", score: 55},
            {time: "10:47", score: 54},
            {time: "10:54", score: 53},
            {time: "11:01", score: 52},
            {time: "11:08", score: 51},
            {time: "11:15", score: 50},
            {time: "11:22", score: 49},
            {time: "11:29", score: 48},
            {time: "11:36", score: 47},
            {time: "11:43", score: 46},
            {time: "11:50", score: 45},
            {time: "11:57", score: 44},
            {time: "12:04", score: 43},
            {time: "12:11", score: 42},
            {time: "12:18", score: 41},
            {time: "12:25", score: 40},
            {time: "12:35", score: 39},
            {time: "12:45", score: 38},
            {time: "12:55", score: 37},
            {time: "13:05", score: 36},
            {time: "13:15", score: 35},
            {time: "13:25", score: 34},
            {time: "13:35", score: 33},
            {time: "13:45", score: 32},
            {time: "13:55", score: 31},
            {time: "14:05", score: 30}
        ];
        
        // טבלת המרה עבור דלגית (כמות → ציון)
        const jumpRopeTable = [
            {count: 150, score: 100},
            {count: 149, score: 99},
            {count: 148, score: 98},
            {count: 146, score: 97},
            {count: 144, score: 96},
            {count: 142, score: 95},
            {count: 140, score: 94},
            {count: 138, score: 93},
            {count: 136, score: 92},
            {count: 135, score: 91},
            {count: 133, score: 90},
            {count: 132, score: 89},
            {count: 130, score: 88},
            {count: 128, score: 87},
            {count: 127, score: 86},
            {count: 125, score: 85},
            {count: 123, score: 84},
            {count: 121, score: 83},
            {count: 118, score: 82},
            {count: 115, score: 81},
            {count: 112, score: 80},
            {count: 110, score: 79},
            {count: 108, score: 78},
            {count: 106, score: 77},
            {count: 103, score: 76},
            {count: 100, score: 75},
            {count: 98, score: 74},
            {count: 96, score: 73},
            {count: 94, score: 72},
            {count: 92, score: 71},
            {count: 89, score: 70},
            {count: 87, score: 69},
            {count: 85, score: 68},
            {count: 84, score: 67},
            {count: 82, score: 66},
            {count: 81, score: 65},
            {count: 79, score: 64},
            {count: 77, score: 63},
            {count: 75, score: 62},
            {count: 73, score: 61},
            {count: 72, score: 60},
            {count: 71, score: 59},
            {count: 70, score: 58},
            {count: 68, score: 57},
            {count: 66, score: 56},
            {count: 65, score: 55},
            {count: 64, score: 54},
            {count: 63, score: 53},
            {count: 62, score: 52},
            {count: 61, score: 51},
            {count: 60, score: 50},
            {count: 59, score: 49},
            {count: 58, score: 48},
            {count: 57, score: 47},
            {count: 56, score: 46},
            {count: 55, score: 45},
            {count: 54, score: 44},
            {count: 53, score: 43},
            {count: 52, score: 42},
            {count: 51, score: 41},
            {count: 50, score: 40}
        ];
        
        // טבלת המרה עבור מתח (כמות → ציון)
        const pullupsTable = [
            {count: 16, score: 100},
            {count: 15, score: 96},
            {count: 14, score: 93},
            {count: 13, score: 90},
            {count: 12, score: 86},
            {count: 11, score: 83},
            {count: 10, score: 80},
            {count: 9, score: 76},
            {count: 8, score: 72},
            {count: 7, score: 68},
            {count: 6, score: 65},
            {count: 5, score: 63},
            {count: 4, score: 61},
            {count: 3, score: 58},
            {count: 2, score: 55},
            {count: 1, score: 50}
        ];
        
        // טבלת המרה עבור שכיבות שמיכה (כמות → ציון)
        const pushupsTable = [
            {count: 55, score: 100},
            {count: 54, score: 98},
            {count: 53, score: 96},
            {count: 52, score: 95},
            {count: 51, score: 94},
            {count: 50, score: 93},
            {count: 49, score: 92},
            {count: 48, score: 91},
            {count: 47, score: 90},
            {count: 46, score: 89},
            {count: 45, score: 88},
            {count: 44, score: 87},
            {count: 43, score: 86},
            {count: 42, score: 85},
            {count: 41, score: 84},
            {count: 40, score: 83},
            {count: 39, score: 82},
            {count: 38, score: 81},
            {count: 37, score: 80},
            {count: 36, score: 79},
            {count: 35, score: 78},
            {count: 34, score: 77},
            {count: 33, score: 76},
            {count: 32, score: 75},
            {count: 31, score: 74},
            {count: 30, score: 73},
            {count: 29, score: 72},
            {count: 28, score: 71},
            {count: 27, score: 70},
            {count: 26, score: 69},
            {count: 25, score: 68},
            {count: 24, score: 67},
            {count: 23, score: 66},
            {count: 22, score: 65},
            {count: 21, score: 64},
            {count: 20, score: 63},
            {count: 19, score: 62},
            {count: 18, score: 60},
            {count: 17, score: 59},
            {count: 16, score: 57},
            {count: 15, score: 55},
            {count: 14, score: 50},
            {count: 13, score: 47},
            {count: 12, score: 45},
            {count: 11, score: 43},
            {count: 10, score: 40},
            {count: 9, score: 35},
            {count: 8, score: 30}
        ];
        
        // ============================================
        // טבלת המרה עבור בנות מהקובץ האקסל
        // ============================================
        const girlsConversionTable = [
            // ניקוד 100
            {score: 100, running: "10:00-10:30", jumprope: 150, pullups_band: 14, pushups_knees: 35, pushups_regular: 15, ladder: 10},
            // ניקוד 99
            {score: 99, jumprope: 149},
            // ניקוד 98
            {score: 98, jumprope: 148, pushups_knees: 34},
            // ניקוד 97
            {score: 97, running: "10:31-11:00", jumprope: 146},
            // ניקוד 96
            {score: 96, jumprope: 144, pullups_band: 13, pushups_knees: 33},
            // ניקוד 95
            {score: 95, running: "11:01-11:30", jumprope: 142, pushups_regular: 14, ladder: 9},
            // ניקוד 94
            {score: 94, jumprope: 140, pushups_knees: 32},
            // ניקוד 93
            {score: 93, jumprope: 138, pullups_band: 12},
            // ניקוד 92
            {score: 92, jumprope: 136, pushups_knees: 31},
            // ניקוד 91
            {score: 91, jumprope: 135},
            // ניקוד 90
            {score: 90, running: "11:31-12:00", jumprope: 133, pullups_band: 11, pushups_knees: 30, pushups_regular: 13, ladder: 8},
            // ניקוד 89
            {score: 89, jumprope: 132},
            // ניקוד 88
            {score: 88, jumprope: 130, pushups_knees: 29},
            // ניקוד 87
            {score: 87, jumprope: 128, pullups_band: 10},
            // ניקוד 86
            {score: 86, jumprope: 127, pushups_knees: 28},
            // ניקוד 85
            {score: 85, running: "12:01-12:30", jumprope: 125, pullups_band: 9, pushups_regular: 12, ladder: 7},
            // ניקוד 84
            {score: 84, jumprope: 124, pushups_knees: 27},
            // ניקוד 83
            {score: 83, jumprope: 121},
            // ניקוד 82
            {score: 82, jumprope: 118, pushups_knees: 26},
            // ניקוד 81
            {score: 81, jumprope: 115},
            // ניקוד 80
            {score: 80, running: "12:31-13:00", jumprope: 112, pullups_band: 8, pushups_knees: 25, pushups_regular: 11},
            // ניקוד 79
            {score: 79, jumprope: 110},
            // ניקוד 78
            {score: 78, jumprope: 108, pushups_knees: 24},
            // ניקוד 77
            {score: 77, jumprope: 106, pullups_band: 7},
            // ניקוד 76
            {score: 76, jumprope: 103, pushups_knees: 23},
            // ניקוד 75
            {score: 75, running: "13:01-13:30", jumprope: 100, pullups_band: 6, pushups_regular: 10, ladder: 6},
            // ניקוד 74
            {score: 74, jumprope: 98, pushups_knees: 22},
            // ניקוד 73
            {score: 73, jumprope: 96},
            // ניקוד 72
            {score: 72, jumprope: 94, pushups_knees: 21},
            // ניקוד 71
            {score: 71, jumprope: 92},
            // ניקוד 70
            {score: 70, running: "13:31-14:00", jumprope: 90, pullups_band: 5, pushups_knees: 20, pushups_regular: 9},
            // ניקוד 69
            {score: 69, jumprope: 88},
            // ניקוד 68
            {score: 68, jumprope: 86, pushups_knees: 19},
            // ניקוד 67
            {score: 67, jumprope: 84},
            // ניקוד 66
            {score: 66, jumprope: 83, pushups_knees: 18},
            // ניקוד 65
            {score: 65, running: "14:01-14:30", jumprope: 81, pullups_band: 4, pushups_regular: 8, ladder: 5},
            // ניקוד 64
            {score: 64, jumprope: 79, pushups_knees: 17},
            // ניקוד 63
            {score: 63, jumprope: 77},
            // ניקוד 62
            {score: 62, jumprope: 75, pushups_knees: 16},
            // ניקוד 61
            {score: 61, jumprope: 73},
            // ניקוד 60
            {score: 60, running: "14:31-15:00", jumprope: 72, pullups_band: 3, pushups_knees: 15, pushups_regular: 7},
            // ניקוד 59
            {score: 59, jumprope: 71},
            // ניקוד 58
            {score: 58, jumprope: 70, pushups_knees: 14},
            // ניקוד 57
            {score: 57, jumprope: 68},
            // ניקוד 56
            {score: 56, jumprope: 66, pushups_knees: 13},
            // ניקוד 55
            {score: 55, running: "15:01-17:00", jumprope: 64, pullups_band: 2, pushups_regular: 6, ladder: 4},
            // ניקוד 54
            {score: 54, jumprope: 62, pushups_knees: 12},
            // ניקוד 53
            {score: 53, jumprope: 60},
            // ניקוד 52
            {score: 52, jumprope: 58, pushups_knees: 11},
            // ניקוד 51
            {score: 51, jumprope: 56},
            // ניקוד 50
            {score: 50, running: "17:01:00", jumprope: 54, pullups_band: 1, pushups_knees: 10, pushups_regular: 5},
            // ניקוד 49
            {score: 49, jumprope: 52},
            // ניקוד 48
            {score: 48, jumprope: 50, pushups_knees: 9},
            // ניקוד 47
            {score: 47, jumprope: 48},
            // ניקוד 46
            {score: 46, jumprope: 46, pushups_knees: 8},
            // ניקוד 45
            {score: 45, jumprope: 44, pushups_regular: 4, ladder: 3},
            // ניקוד 44
            {score: 44, jumprope: 42, pushups_knees: 7},
            // ניקוד 43
            {score: 43, jumprope: 40},
            // ניקוד 42
            {score: 42, jumprope: 38, pushups_knees: 6},
            // ניקוד 41
            {score: 41, jumprope: 36},
            // ניקוד 40
            {score: 40, jumprope: 34, pushups_knees: 5, pushups_regular: 3},
            // ניקוד 39
            {score: 39, jumprope: 32},
            // ניקוד 38
            {score: 38, jumprope: 30, pushups_knees: 4},
            // ניקוד 37
            {score: 37, jumprope: 28},
            // ניקוד 36
            {score: 36, jumprope: 26, pushups_knees: 3},
            // ניקוד 35
            {score: 35, jumprope: 24, pushups_regular: 2, ladder: 2},
            // ניקוד 34
            {score: 34, jumprope: 22, pushups_knees: 2},
            // ניקוד 33
            {score: 33, jumprope: 20, pushups_regular: 1, ladder: 1},
            // ניקוד 32
            {score: 32, jumprope: 18, pushups_knees: 1},
            // ניקוד 31
            {score: 31, jumprope: 16},
            // ניקוד 30
            {score: 30, jumprope: 14, pullups_band: "ניסיון", pushups_knees: "ניסיון", pushups_regular: "ניסיון", ladder: "ניסיון"}
        ];

        // נתוני הבנות המלאים מהאקסל
        const girlsData = [
            // כיתה 1 - 15 תלמידות
            {id: 47, lastName: "בן עמי", firstName: "רומי", grade: "יב", class: 1, gender: "girls"},
            {id: 66, lastName: "גופמן", firstName: "ליאן", grade: "יב", class: 1, gender: "girls"},
            {id: 73, lastName: "גפה", firstName: "עופרי", grade: "יב", class: 1, gender: "girls"},
            {id: 74, lastName: "גפן", firstName: "שקד", grade: "יב", class: 1, gender: "girls"},
            {id: 93, lastName: "הלר", firstName: "רוני", grade: "יב", class: 1, gender: "girls"},
            {id: 98, lastName: "ויטנברג", firstName: "שני", grade: "יב", class: 1, gender: "girls"},
            {id: 105, lastName: "זיטמן", firstName: "עדי", grade: "יב", class: 1, gender: "girls"},
            {id: 122, lastName: "טויטו", firstName: "מעיין", grade: "יב", class: 1, gender: "girls"},
            {id: 164, lastName: "לוי", firstName: "נועה", grade: "יב", class: 1, gender: "girls"},
            {id: 188, lastName: "מילס", firstName: "קורן", grade: "יב", class: 1, gender: "girls"},
            {id: 232, lastName: "עקירב", firstName: "שלי", grade: "יב", class: 1, gender: "girls"},
            {id: 234, lastName: "פדידה", firstName: "ארבל", grade: "יב", class: 1, gender: "girls"},
            {id: 243, lastName: "פניז'ל", firstName: "סיון", grade: "יב", class: 1, gender: "girls"},
            {id: 250, lastName: "פתאל", firstName: "מאי", grade: "יב", class: 1, gender: "girls"},
            {id: 296, lastName: "שפירא", firstName: "נוגה", grade: "יב", class: 1, gender: "girls"},

            // כיתה 2 - 17 תלמידות
            {id: 3, lastName: "אברהם", firstName: "ליבי", grade: "יב", class: 2, gender: "girls"},
            {id: 5, lastName: "אגסי", firstName: "אגם", grade: "יב", class: 2, gender: "girls"},
            {id: 40, lastName: "בכר", firstName: "גאיה", grade: "יב", class: 2, gender: "girls"},
            {id: 68, lastName: "גלד", firstName: "אביגיל", grade: "יב", class: 2, gender: "girls"},
            {id: 94, lastName: "הס", firstName: "אופיר", grade: "יב", class: 2, gender: "girls"},
            {id: 114, lastName: "חלד", firstName: "אוריה", grade: "יב", class: 2, gender: "girls"},
            {id: 125, lastName: "טננבאום", firstName: "אריאל", grade: "יב", class: 2, gender: "girls"},
            {id: 139, lastName: "יוסף", firstName: "מורן", grade: "יב", class: 2, gender: "girls"},
            {id: 160, lastName: "לביד", firstName: "אלה", grade: "יב", class: 2, gender: "girls"},
            {id: 166, lastName: "לויטה", firstName: "מיה", grade: "יב", class: 2, gender: "girls"},
            {id: 202, lastName: "נוסבאום", firstName: "ליה", grade: "יב", class: 2, gender: "girls"},
            {id: 203, lastName: "נחום", firstName: "לי-אל", grade: "יב", class: 2, gender: "girls"},
            {id: 209, lastName: "סודאי", firstName: "מיקה", grade: "יב", class: 2, gender: "girls"},
            {id: 251, lastName: "צדוק מזרחי", firstName: "אמה", grade: "יב", class: 2, gender: "girls"},
            {id: 269, lastName: "רואס", firstName: "אגם", grade: "יב", class: 2, gender: "girls"},
            {id: 283, lastName: "שחף", firstName: "רומי", grade: "יב", class: 2, gender: "girls"},
            {id: 302, lastName: "תוריק", firstName: "תהל", grade: "יב", class: 2, gender: "girls"},

            // כיתה 3 - 20 תלמידות
            {id: 9, lastName: "אהרון", firstName: "שני", grade: "יב", class: 3, gender: "girls"},
            {id: 31, lastName: "בדור", firstName: "נועה", grade: "יב", class: 3, gender: "girls"},
            {id: 39, lastName: "בירנבאום", firstName: "נועם", grade: "יב", class: 3, gender: "girls"},
            {id: 52, lastName: "בר נתן", firstName: "מאיה", grade: "יב", class: 3, gender: "girls"},
            {id: 55, lastName: "ברונז", firstName: "מאיה", grade: "יב", class: 3, gender: "girls"},
            {id: 56, lastName: "ברזני", firstName: "ליאן", grade: "יב", class: 3, gender: "girls"},
            {id: 78, lastName: "דבח", firstName: "גל", grade: "יב", class: 3, gender: "girls"},
            {id: 80, lastName: "דוד", firstName: "ירדן", grade: "יב", class: 3, gender: "girls"},
            {id: 83, lastName: "דניסוב", firstName: "אביגיל", grade: "יב", class: 3, gender: "girls"},
            {id: 106, lastName: "זייתונה", firstName: "מיכל", grade: "יב", class: 3, gender: "girls"},
            {id: 120, lastName: "חנן", firstName: 'ליאור', grade: "יב", class: 3, gender: "girls"},
            {id: 177, lastName: "מאירוביץ", firstName: "ליבי", grade: "יב", class: 3, gender: "girls"},
            {id: 182, lastName: "מועלם", firstName: "ליה", grade: "יב", class: 3, gender: "girls"},
            {id: 199, lastName: "נובוגרודסקי", firstName: "ספיר", grade: "יב", class: 3, gender: "girls"},
            {id: 201, lastName: "נוימן", firstName: "עדן", grade: "יב", class: 3, gender: "girls"},
            {id: 208, lastName: "סגל", firstName: "נויה", grade: "יב", class: 3, gender: "girls"},
            {id: 220, lastName: "עדני", firstName: "הילה", grade: "יב", class: 3, gender: "girls"},
            {id: 268, lastName: "רהב", firstName: "מיקה", grade: "יב", class: 3, gender: "girls"},
            {id: 276, lastName: "רפופורט", firstName: "מעיין", grade: "יב", class: 3, gender: "girls"},

            // כיתה 4 - 8 תלמידות
            {id: 54, lastName: "ברוך", firstName: "נגה", grade: "יב", class: 4, gender: "girls"},
            {id: 88, lastName: "הובר-לרנר", firstName: "נעמה", grade: "יב", class: 4, gender: "girls"},
            {id: 92, lastName: "הלר", firstName: "יערה", grade: "יב", class: 4, gender: "girls"},
            {id: 99, lastName: "וייס", firstName: "שקד", grade: "יב", class: 4, gender: "girls"},
            {id: 221, lastName: "עוזיהו", firstName: "מורן", grade: "יב", class: 4, gender: "girls"},
            {id: 242, lastName: "פנחס", firstName: "עדן", grade: "יב", class: 4, gender: "girls"},
            {id: 247, lastName: "פרידמן", firstName: "אלונה", grade: "יב", class: 4, gender: "girls"},
            {id: 295, lastName: "שנדיבין", firstName: "אביגיל", grade: "יב", class: 4, gender: "girls"},

            // כיתה 5 - 6 תלמידות
            {id: 18, lastName: "אייזמן", firstName: "שיראל", grade: "יב", class: 5, gender: "girls"},
            {id: 27, lastName: "ארניה", firstName: "נויה", grade: "יב", class: 5, gender: "girls"},
            {id: 178, lastName: "מגרי", firstName: "הלל", grade: "יב", class: 5, gender: "girls"},
            {id: 275, lastName: "ריכטר", firstName: "ארבל אסתר", grade: "יב", class: 5, gender: "girls"},
            {id: 282, lastName: "שורשי", firstName: "מאיה", grade: "יב", class: 5, gender: "girls"},
            {id: 286, lastName: "שחר", firstName: "מאיה", grade: "יב", class: 5, gender: "girls"},

            // כיתה 6 - 12 תלמידות
            {id: 29, lastName: "באביאן", firstName: "אגם", grade: "יב", class: 6, gender: "girls"},
            {id: 67, lastName: "גורביץ", firstName: "ליהיא", grade: "יב", class: 6, gender: "girls"},
            {id: 69, lastName: "גלנץ", firstName: "אופק", grade: "יב", class: 6, gender: "girls"},
            {id: 72, lastName: "גנדלמן", firstName: "מאיה", grade: "יב", class: 6, gender: "girls"},
            {id: 100, lastName: "וילנציק", firstName: "נועה", grade: "יב", class: 6, gender: "girls"},
            {id: 156, lastName: "כץ", firstName: "מאיה", grade: "יב", class: 6, gender: "girls"},
            {id: 174, lastName: "לרה", firstName: "יעל", grade: "יב", class: 6, gender: "girls"},
            {id: 195, lastName: "מנשה", firstName: "שירה", grade: "יב", class: 6, gender: "girls"},
            {id: 198, lastName: "משה", firstName: "יובל", grade: "יב", class: 6, gender: "girls"},
            {id: 260, lastName: "קורן", firstName: "עלמה", grade: "יב", class: 6, gender: "girls"},
            {id: 270, lastName: "רובין", firstName: "אגם", grade: "יב", class: 6, gender: "girls"},
            {id: 278, lastName: "שבתאי", firstName: "מיקה", grade: "יב", class: 6, gender: "girls"},

            // כיתה 7 - 16 תלמידות
            {id: 1, lastName: "אביטן", firstName: "נעמה", grade: "יב", class: 7, gender: "girls"},
            {id: 28, lastName: "אשורי", firstName: "רון", grade: "יב", class: 7, gender: "girls"},
            {id: 77, lastName: "גרשון", firstName: "שירה", grade: "יב", class: 7, gender: "girls"},
            {id: 131, lastName: "יהב", firstName: "סיון", grade: "יב", class: 7, gender: "girls"},
            {id: 133, lastName: "יהודה", firstName: "זיו", grade: "יב", class: 7, gender: "girls"},
            {id: 140, lastName: "יוסף", firstName: "ענבר", grade: "יב", class: 7, gender: "girls"},
            {id: 145, lastName: "יצחקי", firstName: "שירה", grade: "יב", class: 7, gender: "girls"},
            {id: 151, lastName: "כהן", firstName: "סתיו הודיה", grade: "יב", class: 7, gender: "girls"},
            {id: 158, lastName: "כץ", firstName: "שירה", grade: "יב", class: 7, gender: "girls"},
            {id: 163, lastName: "לוי", firstName: "יובל", grade: "יב", class: 7, gender: "girls"},
            {id: 179, lastName: "מהדב", firstName: "עדי", grade: "יב", class: 7, gender: "girls"},
            {id: 180, lastName: "מוזס", firstName: "שירה", grade: "יב", class: 7, gender: "girls"},
            {id: 212, lastName: "סילורה", firstName: "נויה", grade: "יב", class: 7, gender: "girls"},
            {id: 236, lastName: "פולישוק", firstName: "רז", grade: "יב", class: 7, gender: "girls"},
            {id: 267, lastName: "קרן", firstName: "שירה", grade: "יב", class: 7, gender: "girls"},
            {id: 289, lastName: "שיפרמן", firstName: "דנה", grade: "יב", class: 7, gender: "girls"},

            // כיתה 8 - 6 תלמידות
            {id: 4, lastName: "אברהם", firstName: "שי", grade: "יב", class: 8, gender: "girls"},
            {id: 16, lastName: "אחיאל", firstName: "ליהי", grade: "יב", class: 8, gender: "girls"},
            {id: 82, lastName: "דנון", firstName: "עדן", grade: "יב", class: 8, gender: "girls"},
            {id: 116, lastName: "חלפון", firstName: "מאיה", grade: "יב", class: 8, gender: "girls"},
            {id: 290, lastName: "שלמה", firstName: "אגם", grade: "יב", class: 8, gender: "girls"},
            {id: 298, lastName: "שריקי", firstName: "רוני", grade: "יב", class: 8, gender: "girls"},

            // כיתה 9 - 6 תלמידות
            {id: 14, lastName: "אוריול", firstName: "מישל", grade: "יב", class: 9, gender: "girls"},
            {id: 89, lastName: "הורוביץ", firstName: "אור", grade: "יב", class: 9, gender: "girls"},
            {id: 115, lastName: "חלפון", firstName: 'ליאל', grade: "יב", class: 9, gender: "girls"},
            {id: 222, lastName: "עזרא", firstName: "הדר", grade: "יב", class: 9, gender: "girls"},
            {id: 230, lastName: "ענית", firstName: "הילה", grade: "יב", class: 9, gender: "girls"},
            {id: 262, lastName: "קורצ'מינסקי", firstName: "מרים", grade: "יב", class: 9, gender: "girls"},

            // כיתה 10 - 16 תלמידות
            {id: 6, lastName: "אגסי", firstName: "רותם", grade: "יב", class: 10, gender: "girls"},
            {id: 13, lastName: "אופיר", firstName: "ליה", grade: "יב", class: 10, gender: "girls"},
            {id: 42, lastName: "בלוקור", firstName: "דריה", grade: "יב", class: 10, gender: "girls"},
            {id: 86, lastName: "האוזמן", firstName: "אמה", grade: "יב", class: 10, gender: "girls"},
            {id: 103, lastName: "ונה", firstName: "שי", grade: "יב", class: 10, gender: "girls"},
            {id: 123, lastName: "טוקר", firstName: "עלמה", grade: "יב", class: 10, gender: "girls"},
            {id: 134, lastName: "יהושע", firstName: "אגם", grade: "יב", class: 10, gender: "girls"},
            {id: 150, lastName: "כהן", firstName: "ליאן", grade: "יב", class: 10, gender: "girls"},
            {id: 185, lastName: "מיטלמן", firstName: "סוואנה", grade: "יב", class: 10, gender: "girls"},
            {id: 186, lastName: "מיכאל", firstName: "הגר", grade: "יב", class: 10, gender: "girls"},
            {id: 200, lastName: "נוימן", firstName: "עדי", grade: "יב", class: 10, gender: "girls"},
            {id: 218, lastName: "סער", firstName: "תמר", grade: "יב", class: 10, gender: "girls"},
            {id: 227, lastName: "עלימה", firstName: "ניצן", grade: "יב", class: 10, gender: "girls"},
            {id: 272, lastName: "רוזנטל", firstName: "ירדן", grade: "יב", class: 10, gender: "girls"},
            {id: 279, lastName: "שובל", firstName: "אביב", grade: "יב", class: 10, gender: "girls"},
            {id: 294, lastName: "שמש", firstName: "מורן", grade: "יב", class: 10, gender: "girls"},

            // כיתה 11 - 2 תלמידות
            {id: 191, lastName: "מכלין", firstName: "יעל", grade: "יב", class: 11, gender: "girls"},
            {id: 231, lastName: "עסיס", firstName: "אושר", grade: "יב", class: 11, gender: "girls"},

            // כיתה 12 - 3 תלמידות
            {id: 49, lastName: "בנבנישתי", firstName: "טליה", grade: "יב", class: 12, gender: "girls"},
            {id: 171, lastName: "ליפוביץ", firstName: "אמילי", grade: "יב", class: 12, gender: "girls"},
            {id: 271, lastName: "רוזנטל", firstName: "דבורה", grade: "יב", class: 12, gender: "girls"}
        ];

        // נתוני הבנים
        const boysData = [
            // כיתה 1 - 18 תלמידים
            {id: 2, lastName: 'אביצור', firstName: 'איל', class: 1, gender: 'boys'},
            {id: 41, lastName: 'בלום', firstName: 'ניר', class: 1, gender: 'boys'},
            {id: 81, lastName: 'דולב', firstName: 'אריאל', class: 1, gender: 'boys'},
            {id: 102, lastName: 'ויצמן', firstName: 'איתי', class: 1, gender: 'boys'},
            {id: 108, lastName: 'חבקוק', firstName: 'מתן', class: 1, gender: 'boys'},
            {id: 110, lastName: 'חזן', firstName: 'סתיו', class: 1, gender: 'boys'},
            {id: 118, lastName: 'חממה', firstName: 'יועד', class: 1, gender: 'boys'},
            {id: 147, lastName: 'כהן', firstName: 'יאיר', class: 1, gender: 'boys'},
            {id: 159, lastName: 'לאוטן', firstName: 'ליאם', class: 1, gender: 'boys'},
            {id: 168, lastName: 'ליברך', firstName: 'עידו', class: 1, gender: 'boys'},
            {id: 184, lastName: 'מחלב', firstName: 'שי', class: 1, gender: 'boys'},
            {id: 207, lastName: 'נשיא', firstName: 'גיא', class: 1, gender: 'boys'},
            {id: 211, lastName: 'סילבר', firstName: 'מתן', class: 1, gender: 'boys'},
            {id: 237, lastName: 'פוקס', firstName: 'ירדן', class: 1, gender: 'boys'},
            {id: 258, lastName: 'קורין', firstName: 'יונתן', class: 1, gender: 'boys'},
            {id: 259, lastName: 'קורן', firstName: 'זוהר', class: 1, gender: 'boys'},
            {id: 264, lastName: 'קרדה', firstName: 'עמית', class: 1, gender: 'boys'},
            {id: 297, lastName: 'שר', firstName: 'יובל', class: 1, gender: 'boys'},

            // כיתה 2 - 13 תלמידים
            {id: 8, lastName: 'אהרון', firstName: 'עידן', class: 2, gender: 'boys'},
            {id: 57, lastName: 'ברכל', firstName: 'רון', class: 2, gender: 'boys'},
            {id: 87, lastName: 'הדר', firstName: 'עומר', class: 2, gender: 'boys'},
            {id: 91, lastName: 'הלאלי', firstName: 'שלו', class: 2, gender: 'boys'},
            {id: 104, lastName: 'זיו', firstName: 'עמית', class: 2, gender: 'boys'},
            {id: 143, lastName: 'יצחקי', firstName: 'אור', class: 2, gender: 'boys'},
            {id: 172, lastName: 'ליפובצקי', firstName: 'דניאל', class: 2, gender: 'boys'},
            {id: 192, lastName: 'ממן', firstName: 'איתמר', class: 2, gender: 'boys'},
            {id: 193, lastName: 'מנסור', firstName: 'אדם', class: 2, gender: 'boys'},
            {id: 194, lastName: 'מנסור', firstName: 'יובל', class: 2, gender: 'boys'},
            {id: 256, lastName: 'קולטניק', firstName: 'ניר', class: 2, gender: 'boys'},
            {id: 300, lastName: 'שרצר', firstName: 'נועם', class: 2, gender: 'boys'},
            {id: 301, lastName: 'ששון', firstName: 'שלו', class: 2, gender: 'boys'},

            // כיתה 3 - 15 תלמידים
            {id: 10, lastName: 'אהרוני', firstName: 'רותם', class: 3, gender: 'boys'},
            {id: 21, lastName: 'אליהו', firstName: 'גיא', class: 3, gender: 'boys'},
            {id: 22, lastName: 'אליהו', firstName: 'עידן', class: 3, gender: 'boys'},
            {id: 24, lastName: 'אסולין', firstName: 'איתי', class: 3, gender: 'boys'},
            {id: 60, lastName: 'גולדנברג', firstName: 'יהלי', class: 3, gender: 'boys'},
            {id: 62, lastName: 'גולדשטיין', firstName: 'עידן', class: 3, gender: 'boys'},
            {id: 71, lastName: 'גמליאל', firstName: 'עידן', class: 3, gender: 'boys'},
            {id: 109, lastName: 'חזות', firstName: 'יואב', class: 3, gender: 'boys'},
            {id: 113, lastName: 'חכם', firstName: 'יהונתן', class: 3, gender: 'boys'},
            {id: 126, lastName: 'טנר', firstName: 'רום', class: 3, gender: 'boys'},
            {id: 128, lastName: 'טפירו', firstName: 'רועי', class: 3, gender: 'boys'},
            {id: 142, lastName: 'ינדרזבסקי', firstName: 'אנדרי', class: 3, gender: 'boys'},
            {id: 245, lastName: 'פסטרנק', firstName: 'רותם', class: 3, gender: 'boys'},
            {id: 288, lastName: 'שיינפלד', firstName: 'עומר', class: 3, gender: 'boys'},

            // כיתה 4 - 17 תלמידים
            {id: 20, lastName: 'אלון', firstName: 'עידו', class: 4, gender: 'boys'},
            {id: 23, lastName: 'אלשיץ', firstName: 'יונתן', class: 4, gender: 'boys'},
            {id: 38, lastName: 'בינחס', firstName: 'תומר', class: 4, gender: 'boys'},
            {id: 46, lastName: 'בן נתן', firstName: 'אוריה', class: 4, gender: 'boys'},
            {id: 70, lastName: 'גלעדי', firstName: 'עידו', class: 4, gender: 'boys'},
            {id: 129, lastName: 'טקו', firstName: 'הראל', class: 4, gender: 'boys'},
            {id: 135, lastName: 'יהושע', firstName: 'איתן', class: 4, gender: 'boys'},
            {id: 136, lastName: 'יונה טלמון', firstName: 'שקד', class: 4, gender: 'boys'},
            {id: 155, lastName: 'כץ', firstName: 'אופיר', class: 4, gender: 'boys'},
            {id: 240, lastName: 'פישמן', firstName: 'אביב', class: 4, gender: 'boys'},
            {id: 241, lastName: 'פלדמן', firstName: 'עידו', class: 4, gender: 'boys'},
            {id: 248, lastName: 'פרל', firstName: 'איתי', class: 4, gender: 'boys'},
            {id: 254, lastName: 'קדר', firstName: 'עומר', class: 4, gender: 'boys'},
            {id: 261, lastName: 'קורסיה', firstName: 'שגיא סעדיה', class: 4, gender: 'boys'},
            {id: 263, lastName: 'קטנוב', firstName: 'זיו', class: 4, gender: 'boys'},
            {id: 274, lastName: 'רון', firstName: 'אופק', class: 4, gender: 'boys'},

            // כיתה 5 - 11 תלמידים
            {id: 15, lastName: 'אורין', firstName: 'עמית', class: 5, gender: 'boys'},
            {id: 25, lastName: 'ארביט', firstName: 'עידן', class: 5, gender: 'boys'},
            {id: 44, lastName: 'בלס', firstName: 'עידן', class: 5, gender: 'boys'},
            {id: 61, lastName: 'גולדשטין', firstName: 'איתמר', class: 5, gender: 'boys'},
            {id: 149, lastName: 'כהן', firstName: 'יונתן', class: 5, gender: 'boys'},
            {id: 167, lastName: 'לוינסון', firstName: 'עידו', class: 5, gender: 'boys'},
            {id: 239, lastName: 'פייבישב', firstName: 'איתן', class: 5, gender: 'boys'},
            {id: 246, lastName: 'פפרני', firstName: 'ירין', class: 5, gender: 'boys'},
            {id: 253, lastName: 'צור', firstName: 'עומר', class: 5, gender: 'boys'},
            {id: 257, lastName: 'קונסטנטינוב', firstName: 'דראל', class: 5, gender: 'boys'},

            // כיתה 6 - 16 תלמידים
            {id: 26, lastName: 'ארגי', firstName: 'אורי', class: 6, gender: 'boys'},
            {id: 34, lastName: 'ביטון', firstName: 'אביתר', class: 6, gender: 'boys'},
            {id: 95, lastName: 'הרונגי', firstName: 'יהונתן', class: 6, gender: 'boys'},
            {id: 96, lastName: 'הרפז', firstName: 'שחר', class: 6, gender: 'boys'},
            {id: 137, lastName: 'יוסף', firstName: 'איתי', class: 6, gender: 'boys'},
            {id: 138, lastName: 'יוסף', firstName: 'דור', class: 6, gender: 'boys'},
            {id: 144, lastName: 'יצחקי', firstName: 'עידו', class: 6, gender: 'boys'},
            {id: 187, lastName: 'מיכאלי', firstName: 'יונתן', class: 6, gender: 'boys'},
            {id: 215, lastName: 'סספורטס', firstName: 'יואב', class: 6, gender: 'boys'},
            {id: 223, lastName: 'עזריה', firstName: 'נועם', class: 6, gender: 'boys'},
            {id: 225, lastName: 'עטר', firstName: 'דניאל', class: 6, gender: 'boys'},
            {id: 228, lastName: 'עמיחי', firstName: 'רון', class: 6, gender: 'boys'},
            {id: 252, lastName: 'צדיק', firstName: 'עומר', class: 6, gender: 'boys'},
            {id: 266, lastName: 'קרמון', firstName: 'טל', class: 6, gender: 'boys'},
            {id: 277, lastName: 'רפפורט', firstName: 'עידן', class: 6, gender: 'boys'},
            {id: 284, lastName: 'שחר', firstName: 'איתי', class: 6, gender: 'boys'},

            // כיתה 7 - 15 תלמידים
            {id: 76, lastName: 'גרונר', firstName: 'נועם', class: 7, gender: 'boys'},
            {id: 107, lastName: 'זינגר', firstName: 'עופר', class: 7, gender: 'boys'},
            {id: 127, lastName: 'טנר', firstName: 'שחק', class: 7, gender: 'boys'},
            {id: 146, lastName: 'ישראלי', firstName: 'סער', class: 7, gender: 'boys'},
            {id: 153, lastName: 'כהן', firstName: 'עידו', class: 7, gender: 'boys'},
            {id: 161, lastName: 'לוי', firstName: 'איתי', class: 7, gender: 'boys'},
            {id: 173, lastName: 'ליפשיץ', firstName: 'אמיר', class: 7, gender: 'boys'},
            {id: 205, lastName: 'נחום', firstName: 'תומר', class: 7, gender: 'boys'},
            {id: 216, lastName: 'סעאת', firstName: 'עמית', class: 7, gender: 'boys'},
            {id: 273, lastName: 'רוט', firstName: 'נבו', class: 7, gender: 'boys'},
            {id: 280, lastName: 'שובל', firstName: 'אורן', class: 7, gender: 'boys'},
            {id: 281, lastName: 'שוורץ', firstName: 'כפיר', class: 7, gender: 'boys'},
            {id: 285, lastName: 'שחר', firstName: 'יואב', class: 7, gender: 'boys'},
            {id: 303, lastName: 'תורתי', firstName: 'אורן', class: 7, gender: 'boys'},

            // כיתה 8 - 19 תלמידים
            {id: 11, lastName: 'אוחנה', firstName: 'טהר', class: 8, gender: 'boys'},
            {id: 35, lastName: 'ביטון', firstName: 'עידן', class: 8, gender: 'boys'},
            {id: 48, lastName: 'בן רפאל', firstName: 'עידן', class: 8, gender: 'boys'},
            {id: 75, lastName: 'גרבלי', firstName: 'אלמוג', class: 8, gender: 'boys'},
            {id: 90, lastName: 'הורוביץ', firstName: 'בר', class: 8, gender: 'boys'},
            {id: 97, lastName: 'הרשקו', firstName: 'יניר', class: 8, gender: 'boys'},
            {id: 111, lastName: 'חי', firstName: 'אריאל', class: 8, gender: 'boys'},
            {id: 119, lastName: 'חנגל', firstName: 'שחר', class: 8, gender: 'boys'},
            {id: 121, lastName: 'טובי', firstName: 'בן', class: 8, gender: 'boys'},
            {id: 152, lastName: 'כהן', firstName: 'עידו', class: 8, gender: 'boys'},
            {id: 154, lastName: 'כהן', firstName: 'רותם', class: 8, gender: 'boys'},
            {id: 157, lastName: 'כץ', firstName: 'עלאי', class: 8, gender: 'boys'},
            {id: 169, lastName: 'ליברמן', firstName: 'אביב', class: 8, gender: 'boys'},
            {id: 190, lastName: 'מכלוף', firstName: 'איתי', class: 8, gender: 'boys'},
            {id: 206, lastName: 'ניסן', firstName: 'רועי', class: 8, gender: 'boys'},
            {id: 213, lastName: 'סימן טוב', firstName: 'עמית', class: 8, gender: 'boys'},
            {id: 217, lastName: 'סער', firstName: 'אופק', class: 8, gender: 'boys'},
            {id: 255, lastName: 'קוירנסקי', firstName: 'בן', class: 8, gender: 'boys'},

            // כיתה 9 - 13 תלמידים
            {id: 30, lastName: 'בבס', firstName: 'שקד', class: 9, gender: 'boys'},
            {id: 33, lastName: 'ביבי', firstName: 'סהר יוסף', class: 9, gender: 'boys'},
            {id: 43, lastName: 'בלוקור', firstName: 'סטפן', class: 9, gender: 'boys'},
            {id: 58, lastName: 'גבאי', firstName: 'ניב', class: 9, gender: 'boys'},
            {id: 59, lastName: 'גולדברג', firstName: 'עידו', class: 9, gender: 'boys'},
            {id: 79, lastName: 'דהאן', firstName: 'שקד', class: 9, gender: 'boys'},
            {id: 85, lastName: 'דעבול', firstName: 'אלון', class: 9, gender: 'boys'},
            {id: 181, lastName: 'מועלם', firstName: 'איתי', class: 9, gender: 'boys'},
            {id: 214, lastName: 'סמנה', firstName: 'רועי', class: 9, gender: 'boys'},
            {id: 219, lastName: 'ספיבק', firstName: 'יהונתן', class: 9, gender: 'boys'},
            {id: 249, lastName: 'פרלס', firstName: 'איל', class: 9, gender: 'boys'},
            {id: 287, lastName: 'שיזף', firstName: 'נדב', class: 9, gender: 'boys'},
            {id: 293, lastName: 'שמואלי', firstName: 'שי', class: 9, gender: 'boys'},

            // כיתה 10 - 17 תלמידים
            {id: 17, lastName: 'איזדורפר', firstName: 'יואב', class: 10, gender: 'boys'},
            {id: 19, lastName: 'איצקוביץ', firstName: 'אורן', class: 10, gender: 'boys'},
            {id: 36, lastName: 'בייגל', firstName: 'אפיק', class: 10, gender: 'boys'},
            {id: 53, lastName: 'ברגר', firstName: 'איתי', class: 10, gender: 'boys'},
            {id: 63, lastName: 'גולן', firstName: 'אופק', class: 10, gender: 'boys'},
            {id: 112, lastName: 'חיים', firstName: 'אורי', class: 10, gender: 'boys'},
            {id: 117, lastName: 'חמי', firstName: 'עידו', class: 10, gender: 'boys'},
            {id: 124, lastName: 'טליו', firstName: 'בן', class: 10, gender: 'boys'},
            {id: 162, lastName: 'לוי', firstName: 'זיו', class: 10, gender: 'boys'},
            {id: 176, lastName: 'מאור', firstName: 'יאיר', class: 10, gender: 'boys'},
            {id: 197, lastName: 'מרום', firstName: 'יואב', class: 10, gender: 'boys'},
            {id: 204, lastName: 'נחום', firstName: 'נועם', class: 10, gender: 'boys'},
            {id: 226, lastName: 'עיני', firstName: 'שחר', class: 10, gender: 'boys'},
            {id: 235, lastName: 'פדר', firstName: 'איליי', class: 10, gender: 'boys'},
            {id: 238, lastName: 'פתאל', firstName: 'רועי', class: 10, gender: 'boys'},
            {id: 291, lastName: 'שם טוב', firstName: 'עומר', class: 10, gender: 'boys'},

            // כיתה 11 - 10 תלמידים
            {id: 50, lastName: 'בנימין בר', firstName: 'דור', class: 11, gender: 'boys'},
            {id: 84, lastName: 'דנישבסקי', firstName: 'נדב', class: 11, gender: 'boys'},
            {id: 130, lastName: 'טריושקין', firstName: 'ליאור', class: 11, gender: 'boys'},
            {id: 132, lastName: 'יהודה', firstName: 'בנימין', class: 11, gender: 'boys'},
            {id: 148, lastName: 'כהן', firstName: 'יהונתן', class: 11, gender: 'boys'},
            {id: 165, lastName: 'לוי', firstName: 'עידן יצחק', class: 11, gender: 'boys'},
            {id: 170, lastName: 'ליפוביץ', firstName: 'איתן', class: 11, gender: 'boys'},
            {id: 244, lastName: 'פנקרטוב', firstName: 'חיים רמי', class: 11, gender: 'boys'},
            {id: 265, lastName: 'קריספין', firstName: 'בן', class: 11, gender: 'boys'},

            // כיתה 12 - 8 תלמידים
            {id: 12, lastName: 'אוספובט', firstName: 'אריאל', class: 12, gender: 'boys'},
            {id: 32, lastName: 'בורשטיין', firstName: 'דב עמיחי', class: 12, gender: 'boys'},
            {id: 37, lastName: 'בילי', firstName: 'יונתן', class: 12, gender: 'boys'},
            {id: 65, lastName: 'גולן', firstName: 'יהלי', class: 12, gender: 'boys'},
            {id: 189, lastName: 'מירן כספי', firstName: 'איתמר', class: 12, gender: 'boys'},
            {id: 229, lastName: 'עמיעז', firstName: 'רומי שמעון', class: 12, gender: 'boys'}
        ];

        // נתוני כל התלמידים
        let allStudentsData = [...boysData, ...girlsData];

        // נתוני מבחן עיוני מהקובץ
        const theoryGradesData = [
            {firstName: 'עמית', lastName: 'זיו', class: 2, score: 71},
            {firstName: 'יונתן', lastName: 'קורין', class: 1, score: 100},
            {firstName: 'שי', lastName: 'מחלב', class: 1, score: 88},
            {firstName: 'מתן', lastName: 'חבקוק', class: 1, score: 98},
            {firstName: 'רוני', lastName: 'הלר', class: 1, score: 100},
            {firstName: 'ניר', lastName: 'בלום', class: 1, score: 91},
            {firstName: 'עידו', lastName: 'ליברך', class: 1, score: 98},
            {firstName: 'אריאל', lastName: 'דולב', class: 1, score: 93},
            {firstName: 'יועד', lastName: 'חממה', class: 1, score: 100},
            {firstName: 'נוגה', lastName: 'שפירא', class: 1, score: 100},
            {firstName: 'מאי', lastName: 'פתאל', class: 1, score: 86},
            {firstName: 'זוהר', lastName: 'קורן', class: 1, score: 98},
            {firstName: 'נועה', lastName: 'לוי', class: 1, score: 100},
            {firstName: 'שקד', lastName: 'גפן', class: 1, score: 96},
            {firstName: 'גיא', lastName: 'נשיא', class: 1, score: 56},
            {firstName: 'רומי', lastName: 'בן עמי', class: 1, score: 97},
            {firstName: 'יאיר', lastName: 'כהן', class: 1, score: 89},
            {firstName: 'ליאן', lastName: 'גופמן', class: 1, score: 80},
            {firstName: 'עמית', lastName: 'קרדה', class: 1, score: 88},
            {firstName: 'ירדן', lastName: 'פוקס', class: 1, score: 95},
            {firstName: 'ליאם', lastName: 'לאוטן', class: 1, score: 100},
            {firstName: 'איל', lastName: 'אביצור', class: 1, score: 98},
            {firstName: 'עדי', lastName: 'זיטמן', class: 1, score: 100},
            {firstName: 'סתיו', lastName: 'חזן', class: 1, score: 98},
            {firstName: 'מתן', lastName: 'סילבר', class: 1, score: 92},
            {firstName: 'איתי', lastName: 'ויצמן', class: 1, score: 100},
            {firstName: 'עופרי', lastName: 'גפה', class: 1, score: 88},
            {firstName: 'יובל', lastName: 'שר', class: 1, score: 98},
            {firstName: 'סיון', lastName: 'פניז\'ל', class: 1, score: 98},
            {firstName: 'קורן', lastName: 'מילס', class: 1, score: 100},
            {firstName: 'ארבל', lastName: 'פדידה', class: 1, score: 93},
            {firstName: 'שני', lastName: 'ויטנברג', class: 1, score: 93},
            {firstName: 'שלי', lastName: 'עקירב', class: 1, score: 100},
            {firstName: 'מעיין', lastName: 'טויטו', class: 1, score: 83},
            {firstName: 'אפיק', lastName: 'בייגל', class: 10, score: 100},
            {firstName: 'אורי', lastName: 'חיים', class: 10, score: 93},
            {firstName: 'יאיר', lastName: 'מאור', class: 10, score: 48},
            {firstName: 'דריה', lastName: 'בלוקור', class: 10, score: 75},
            {firstName: 'שי', lastName: 'ונה', class: 10, score: 100},
            {firstName: 'נועם', lastName: 'נחום', class: 10, score: 71},
            {firstName: 'רותם', lastName: 'אגסי', class: 10, score: 100},
            {firstName: 'שחר', lastName: 'עיני', class: 10, score: 50},
            {firstName: 'יואב', lastName: 'איזדורפר', class: 10, score: 78},
            {firstName: 'אורן', lastName: 'איצקוביץ', class: 10, score: 49},
            {firstName: 'איליי', lastName: 'פדר', class: 10, score: 47},
            {firstName: 'עומר', lastName: 'שם טוב', class: 10, score: 76},
            {firstName: 'אמה', lastName: 'האוזמן', class: 10, score: 42},
            {firstName: 'עידו', lastName: 'חמי', class: 10, score: 76},
            {firstName: 'תמר', lastName: 'סער', class: 10, score: 30},
            {firstName: 'אגם', lastName: 'יהושע', class: 10, score: 57},
            {firstName: 'ניצן', lastName: 'עלימה', class: 10, score: 40},
            {firstName: 'זיו', lastName: 'לוי', class: 10, score: 97},
            {firstName: 'יואב', lastName: 'מרום', class: 10, score: 91},
            {firstName: 'עדי', lastName: 'נוימן', class: 10, score: 75},
            {firstName: 'הגר', lastName: 'מיכאל', class: 10, score: 87},
            {firstName: 'איתי', lastName: 'ברגר', class: 10, score: 76},
            {firstName: 'בן', lastName: 'טליו', class: 10, score: 64},
            {firstName: 'רועי', lastName: 'פתאל', class: 10, score: 62},
            {firstName: 'ליאן', lastName: 'כהן', class: 10, score: 76},
            {firstName: 'סוואנה', lastName: 'מיטלמן', class: 10, score: 76},
            {firstName: 'מורן', lastName: 'שמש', class: 10, score: 63},
            {firstName: 'עלמה', lastName: 'טוקר', class: 10, score: 43},
            {firstName: 'ירדן', lastName: 'רוזנטל', class: 10, score: 65},
            {firstName: 'אופק', lastName: 'גולן', class: 10, score: 100},
            {firstName: 'ליה', lastName: 'אופיר', class: 10, score: 74},
            {firstName: 'דור', lastName: 'בנימין בר', class: 11, score: 58},
            {firstName: 'עידן יצחק', lastName: 'לוי', class: 11, score: 59},
            {firstName: 'יהונתן', lastName: 'כהן', class: 11, score: 29},
            {firstName: 'בן', lastName: 'קריספין', class: 11, score: 39},
            {firstName: 'אושר', lastName: 'עסיס', class: 11, score: 56},
            {firstName: 'יעל', lastName: 'מכלין', class: 11, score: 68},
            {firstName: 'טליה', lastName: 'בנבנישתי', class: 12, score: 68},
            {firstName: 'דב עמיחי', lastName: 'בורשטיין', class: 12, score: 41},
            {firstName: 'דבורה', lastName: 'רוזנטל', class: 12, score: 43},
            {firstName: 'אמילי', lastName: 'ליפוביץ', class: 12, score: 50},
            {firstName: 'יהלי', lastName: 'גולן', class: 12, score: 30},
            {firstName: 'איתמר', lastName: 'מירן כספי', class: 12, score: 31},
            {firstName: 'רומי שמעון', lastName: 'עמיעז', class: 12, score: 41},
            {firstName: 'יונתן', lastName: 'בילי', class: 12, score: 34},
            {firstName: 'אור', lastName: 'יצחקי', class: 2, score: 93},
            {firstName: 'נועם', lastName: 'שרצר', class: 2, score: 97},
            {firstName: 'אדם', lastName: 'מנסור', class: 2, score: 81},
            {firstName: 'אריאל', lastName: 'טננבאום', class: 2, score: 65},
            {firstName: 'אגם', lastName: 'רואס', class: 2, score: 97},
            {firstName: 'רון', lastName: 'ברכל', class: 2, score: 37},
            {firstName: 'לי-אל', lastName: 'נחום', class: 2, score: 86},
            {firstName: 'ניר', lastName: 'קולטניק', class: 2, score: 88},
            {firstName: 'גאיה', lastName: 'בכר', class: 2, score: 93},
            {firstName: 'שלו', lastName: 'הלאלי', class: 2, score: 54},
            {firstName: 'מורן', lastName: 'יוסף', class: 2, score: 88},
            {firstName: 'עומר', lastName: 'הדר', class: 2, score: 42},
            {firstName: 'אגם', lastName: 'אגסי', class: 2, score: 100},
            {firstName: 'תהל', lastName: 'תוריק', class: 2, score: 70},
            {firstName: 'ליבי', lastName: 'אברהם', class: 2, score: 97},
            {firstName: 'אופיר', lastName: 'הס', class: 2, score: 93},
            {firstName: 'אלה', lastName: 'לביד', class: 2, score: 34},
            {firstName: 'עידן', lastName: 'אהרון', class: 2, score: 38},
            {firstName: 'ליה', lastName: 'נוסבאום', class: 2, score: 97},
            {firstName: 'שלו', lastName: 'ששון', class: 2, score: 48},
            {firstName: 'אוריה', lastName: 'חלד', class: 2, score: 67},
            {firstName: 'דניאל', lastName: 'ליפובצקי', class: 2, score: 77},
            {firstName: 'איתמר', lastName: 'ממן', class: 2, score: 48},
            {firstName: 'אמה', lastName: 'צדוק מזרחי', class: 2, score: 64},
            {firstName: 'מיה', lastName: 'לויטה', class: 2, score: 94},
            {firstName: 'אביגיל', lastName: 'גלד', class: 2, score: 56},
            {firstName: 'עידן', lastName: 'גולדשטיין', class: 3, score: 51},
            {firstName: 'יהלי', lastName: 'גולדנברג', class: 3, score: 63},
            {firstName: 'עידן', lastName: 'גמליאל', class: 3, score: 53},
            {firstName: 'יואב', lastName: 'חזות', class: 3, score: 90},
            {firstName: 'רועי', lastName: 'טפירו', class: 3, score: 54},
            {firstName: 'שני', lastName: 'אהרון', class: 3, score: 91},
            {firstName: 'ליאור', lastName: 'חנן', class: 3, score: 67},
            {firstName: 'מעיין', lastName: 'רפופורט', class: 3, score: 67},
            {firstName: 'ליה', lastName: 'מועלם', class: 3, score: 52},
            {firstName: 'רותם', lastName: 'פסטרנק', class: 3, score: 87},
            {firstName: 'ליבי', lastName: 'מאירוביץ', class: 3, score: 52},
            {firstName: 'אביגיל', lastName: 'דניסוב', class: 3, score: 47},
            {firstName: 'עומר', lastName: 'שיינפלד', class: 3, score: 54},
            {firstName: 'ליאן', lastName: 'ברזני', class: 3, score: 62},
            {firstName: 'גל', lastName: 'דבח', class: 3, score: 50},
            {firstName: 'מיכל', lastName: 'זייתונה', class: 3, score: 56},
            {firstName: 'רום', lastName: 'טנר', class: 3, score: 80},
            {firstName: 'רותם', lastName: 'אהרוני', class: 3, score: 54},
            {firstName: 'איתי', lastName: 'אסולין', class: 3, score: 71},
            {firstName: 'גיא', lastName: 'אליהו', class: 3, score: 84},
            {firstName: 'נועה', lastName: 'בדור', class: 3, score: 86},
            {firstName: 'ספיר', lastName: 'נובוגרודסקי', class: 3, score: 58},
            {firstName: 'מיקה', lastName: 'רהב', class: 3, score: 76},
            {firstName: 'נועם', lastName: 'בירנבאום', class: 3, score: 76},
            {firstName: 'יהונתן', lastName: 'חכם', class: 3, score: 65},
            {firstName: 'אנדרי', lastName: 'ינדרזבסקי', class: 3, score: 74},
            {firstName: 'עידן', lastName: 'אליהו', class: 3, score: 56},
            {firstName: 'נויה', lastName: 'סגל', class: 3, score: 76},
            {firstName: 'ירדן', lastName: 'דוד', class: 3, score: 73},
            {firstName: 'מאיה', lastName: 'בר נתן', class: 3, score: 92},
            {firstName: 'זיו', lastName: 'קטנוב', class: 4, score: 100},
            {firstName: 'אופיר', lastName: 'כץ', class: 4, score: 97},
            {firstName: 'יונתן', lastName: 'אלשיץ', class: 4, score: 100},
            {firstName: 'נגה', lastName: 'ברוך', class: 4, score: 59},
            {firstName: 'איתי', lastName: 'פרל', class: 4, score: 96},
            {firstName: 'שגיא סעדיה', lastName: 'קורסיה', class: 4, score: 86},
            {firstName: 'איתן', lastName: 'יהושע', class: 4, score: 77},
            {firstName: 'אלונה', lastName: 'פרידמן', class: 4, score: 84},
            {firstName: 'הראל', lastName: 'טקו', class: 4, score: 93},
            {firstName: 'עידו', lastName: 'גלעדי', class: 4, score: 100},
            {firstName: 'אביב', lastName: 'פישמן', class: 4, score: 55},
            {firstName: 'עדן', lastName: 'פנחס', class: 4, score: 73},
            {firstName: 'אוריה', lastName: 'בן נתן', class: 4, score: 84},
            {firstName: 'עומר', lastName: 'קדר', class: 4, score: 97},
            {firstName: 'שקד', lastName: 'וייס', class: 4, score: 87},
            {firstName: 'תומר', lastName: 'בינחס', class: 4, score: 95},
            {firstName: 'אביגיל', lastName: 'שנדיבין', class: 4, score: 54},
            {firstName: 'עידו', lastName: 'פלדמן', class: 4, score: 88},
            {firstName: 'יערה', lastName: 'הלר', class: 4, score: 100},
            {firstName: 'אופק', lastName: 'רון', class: 4, score: 61},
            {firstName: 'עידו', lastName: 'אלון', class: 4, score: 77},
            {firstName: 'שקד', lastName: 'יונה טלמון', class: 4, score: 59},
            {firstName: 'דראל', lastName: 'קונסטנטינוב', class: 5, score: 79},
            {firstName: 'שיראל', lastName: 'אייזמן', class: 5, score: 95},
            {firstName: 'מאיה', lastName: 'שחר', class: 5, score: 83},
            {firstName: 'ירין', lastName: 'פפרני', class: 5, score: 50},
            {firstName: 'הלל', lastName: 'מגרי', class: 5, score: 72},
            {firstName: 'איתן', lastName: 'פייבישב', class: 5, score: 74},
            {firstName: 'מאיה', lastName: 'שורשי', class: 5, score: 79},
            {firstName: 'נויה', lastName: 'ארניה', class: 5, score: 60},
            {firstName: 'עידן', lastName: 'ארביט', class: 5, score: 88},
            {firstName: 'איתמר', lastName: 'גולדשטין', class: 5, score: 88},
            {firstName: 'עמית', lastName: 'אורין', class: 5, score: 69},
            {firstName: 'יונתן', lastName: 'כהן', class: 5, score: 78},
            {firstName: 'עומר', lastName: 'צור', class: 5, score: 94},
            {firstName: 'עידן', lastName: 'רפפורט', class: 6, score: 67},
            {firstName: 'נועם', lastName: 'עזריה', class: 6, score: 56},
            {firstName: 'דניאל', lastName: 'עטר', class: 6, score: 51},
            {firstName: 'מאיה', lastName: 'כץ', class: 6, score: 47},
            {firstName: 'אביתר', lastName: 'ביטון', class: 6, score: 60},
            {firstName: 'אופק', lastName: 'גלנץ', class: 6, score: 74},
            {firstName: 'דור', lastName: 'יוסף', class: 6, score: 50},
            {firstName: 'יעל', lastName: 'לרה', class: 6, score: 58},
            {firstName: 'שחר', lastName: 'הרפז', class: 6, score: 80},
            {firstName: 'יואב', lastName: 'סספורטס', class: 6, score: 59},
            {firstName: 'רון', lastName: 'עמיחי', class: 6, score: 56},
            {firstName: 'עומר', lastName: 'צדיק', class: 6, score: 72},
            {firstName: 'יובל', lastName: 'משה', class: 6, score: 39},
            {firstName: 'ליהיא', lastName: 'גורביץ', class: 6, score: 53},
            {firstName: 'מיקה', lastName: 'שבתאי', class: 6, score: 47},
            {firstName: 'איתי', lastName: 'יוסף', class: 6, score: 64},
            {firstName: 'שירה', lastName: 'מנשה', class: 6, score: 43},
            {firstName: 'אורי', lastName: 'ארגי', class: 6, score: 59},
            {firstName: 'עידו', lastName: 'יצחקי', class: 6, score: 45},
            {firstName: 'יהונתן', lastName: 'הרונגי', class: 6, score: 73},
            {firstName: 'מאיה', lastName: 'גנדלמן', class: 6, score: 48},
            {firstName: 'אגם', lastName: 'רובין', class: 6, score: 54},
            {firstName: 'נועה', lastName: 'וילנציק', class: 6, score: 87},
            {firstName: 'אגם', lastName: 'באביאן', class: 6, score: 58},
            {firstName: 'עלמה', lastName: 'קורן', class: 6, score: 78},
            {firstName: 'זיו', lastName: 'יהודה', class: 7, score: 82},
            {firstName: 'שירה', lastName: 'קרן', class: 7, score: 76},
            {firstName: 'אורן', lastName: 'תורתי', class: 7, score: 70},
            {firstName: 'סיון', lastName: 'יהב', class: 7, score: 76},
            {firstName: 'סער', lastName: 'ישראלי', class: 7, score: 70},
            {firstName: 'שחק', lastName: 'טנר', class: 7, score: 83},
            {firstName: 'איתי', lastName: 'לוי', class: 7, score: 61},
            {firstName: 'אורן', lastName: 'שובל', class: 7, score: 48},
            {firstName: 'נועם', lastName: 'גרונר', class: 7, score: 71},
            {firstName: 'נבו', lastName: 'רוט', class: 7, score: 73},
            {firstName: 'יואב', lastName: 'שחר', class: 7, score: 76},
            {firstName: 'שירה', lastName: 'גרשון', class: 7, score: 89},
            {firstName: 'נעמה', lastName: 'אביטן', class: 7, score: 67},
            {firstName: 'עופר', lastName: 'זינגר', class: 7, score: 66},
            {firstName: 'כפיר', lastName: 'שוורץ', class: 7, score: 59},
            {firstName: 'שירה', lastName: 'מוזס', class: 7, score: 69},
            {firstName: 'סתיו הודיה', lastName: 'כהן', class: 7, score: 45},
            {firstName: 'ענבר', lastName: 'יוסף', class: 7, score: 70},
            {firstName: 'יובל', lastName: 'לוי', class: 7, score: 71},
            {firstName: 'רז', lastName: 'פולישוק', class: 7, score: 81},
            {firstName: 'שירה', lastName: 'כץ', class: 7, score: 83},
            {firstName: 'שירה', lastName: 'יצחקי', class: 7, score: 53},
            {firstName: 'עידו', lastName: 'כהן', class: 7, score: 72},
            {firstName: 'אמיר', lastName: 'ליפשיץ', class: 7, score: 48},
            {firstName: 'עמית', lastName: 'סעאת', class: 7, score: 51},
            {firstName: 'נויה', lastName: 'סילורה', class: 7, score: 68},
            {firstName: 'רון', lastName: 'אשורי', class: 7, score: 95},
            {firstName: 'עדי', lastName: 'מהדב', class: 7, score: 97},
            {firstName: 'יובל', lastName: 'לוי', class: 7, score: 87},
            {firstName: 'רוני', lastName: 'שריקי', class: 8, score: 40},
            {firstName: 'עידו', lastName: 'כהן', class: 8, score: 38},
            {firstName: 'בן', lastName: 'טובי', class: 8, score: 49},
            {firstName: 'יניר', lastName: 'הרשקו', class: 8, score: 31},
            {firstName: 'בר', lastName: 'הורוביץ', class: 8, score: 58},
            {firstName: 'איתי', lastName: 'מכלוף', class: 8, score: 52},
            {firstName: 'אופק', lastName: 'סער', class: 8, score: 48},
            {firstName: 'אביב', lastName: 'ליברמן', class: 8, score: 71},
            {firstName: 'בן', lastName: 'קוירנסקי', class: 8, score: 40},
            {firstName: 'מאיה', lastName: 'חלפון', class: 8, score: 48},
            {firstName: 'עמית', lastName: 'סימן טוב', class: 8, score: 62},
            {firstName: 'אגם', lastName: 'שלמה', class: 8, score: 41},
            {firstName: 'עידן', lastName: 'ביטון', class: 8, score: 58},
            {firstName: 'טהר', lastName: 'אוחנה', class: 8, score: 33},
            {firstName: 'שחר', lastName: 'חנגל', class: 8, score: 39},
            {firstName: 'רועי', lastName: 'ניסן', class: 8, score: 33},
            {firstName: 'עדן', lastName: 'דנון', class: 8, score: 32},
            {firstName: 'אלמוג', lastName: 'גרבלי', class: 8, score: 59},
            {firstName: 'ליהי', lastName: 'אחיאל', class: 8, score: 34},
            {firstName: 'אריאל', lastName: 'חי', class: 8, score: 69},
            {firstName: 'עידן', lastName: 'בן רפאל', class: 8, score: 52},
            {firstName: 'שקד', lastName: 'בבס', class: 9, score: 55},
            {firstName: 'שי', lastName: 'שמואלי', class: 9, score: 54},
            {firstName: 'ניב', lastName: 'גבאי', class: 9, score: 47},
            {firstName: 'ליאל', lastName: 'חלפון', class: 9, score: 34},
            {firstName: 'נדב', lastName: 'שיזף', class: 9, score: 55},
            {firstName: 'הדר', lastName: 'עזרא', class: 9, score: 36},
            {firstName: 'איתי', lastName: 'מועלם', class: 9, score: 60},
            {firstName: 'הילה', lastName: 'ענית', class: 9, score: 58},
            {firstName: 'אור', lastName: 'הורוביץ', class: 9, score: 48},
            {firstName: 'מרים', lastName: 'קורצ\'מינסקי', class: 9, score: 36},
            {firstName: 'מישל', lastName: 'אוריול', class: 9, score: 33},
            {firstName: 'עידו', lastName: 'גולדברג', class: 9, score: 36},
            {firstName: 'איל', lastName: 'פרלס', class: 9, score: 54}
        ];

        // ============================================
        // פונקציות ניהול בסיסיות
        // ============================================

        // הצגת התראות
        function showNotification(message, type = 'success') {
            const notificationArea = document.getElementById('notificationArea');
            if (!notificationArea) return;
            
            const notification = document.createElement('div');
            notification.className = `notification ${type}`;
            notification.innerHTML = `
                <i class="fas fa-${type === 'success' ? 'check-circle' : type === 'error' ? 'exclamation-circle' : type === 'warning' ? 'exclamation-triangle' : 'info-circle'}"></i>
                ${message}
            `;
            
            notificationArea.appendChild(notification);
            
            setTimeout(() => {
                if (notification && notification.parentNode) {
                    notification.remove();
                }
            }, 5000);
        }

        // ניווט בין מסכים
        function showScreen(screenId) {
            document.querySelectorAll('.screen').forEach(screen => {
                screen.classList.remove('active');
            });
            document.getElementById(screenId).classList.add('active');
        }

        // בחירת מגדר
        function selectGender(gender) {
            currentGender = gender;
            updateClassScreen();
            showScreen('classScreen');
        }

        // עדכון מסך הכיתות
        function updateClassScreen() {
            const title = document.getElementById('classScreenTitle');
            const grid = document.getElementById('classesGrid');
            
            if (title) {
                title.textContent = currentGender === 'boys' ? 'בחר כיתה - תלמידים' : 'בחר כיתה - תלמידות';
            }
            
            if (!grid) return;
            
            grid.innerHTML = '';
            
            // יצירת כיתות מ-1 עד 12
            for (let i = 1; i <= 12; i++) {
                const classCard = document.createElement('div');
                classCard.className = 'class-card';
                
                // ספירת תלמידים בכיתה
                const studentCount = allStudentsData.filter(student => 
                    student.class === i && student.gender === currentGender
                ).length;
                
                classCard.innerHTML = `
                    <div style="font-size: 1.5rem; font-weight: bold;">יב'${i}</div>
                    <div style="font-size: 0.9rem; color: #666; margin-top: 5px;">
                        ${studentCount} ${currentGender === 'boys' ? 'תלמידים' : 'תלמידות'}
                    </div>
                `;
                
                if (studentCount > 0) {
                    classCard.onclick = () => selectClass(i);
                } else {
                    classCard.style.opacity = '0.5';
                    classCard.style.cursor = 'not-allowed';
                    classCard.innerHTML += '<div style="color: #e74c3c; font-size: 0.8rem; margin-top: 5px;">אין תלמידים</div>';
                }
                
                grid.appendChild(classCard);
            }
        }

        // בחירת כיתה
        function selectClass(classNum) {
            currentClass = classNum;
            
            // טעינת תלמידים
            students = allStudentsData.filter(student => 
                student.class === classNum && student.gender === currentGender
            );
            
            if (students.length === 0) {
                showNotification(`לא נמצאו ${currentGender === 'boys' ? 'תלמידים' : 'תלמידות'} בכיתה יב'${classNum}`, 'warning');
                return;
            }
            
            showNotification(`נטענו ${students.length} ${currentGender === 'boys' ? 'תלמידים' : 'תלמידות'} מכיתה יב'${classNum}`, 'success');
            
            // מעבר למסך הבחירה הבא
            updateTestScreen();
            showScreen('testScreen');
        }

        // עדכון מסך המבחנים
        function updateTestScreen() {
            const title = document.getElementById('testScreenTitle');
            if (title) {
                title.textContent = `כיתה יב'${currentClass} - בחר מבחן`;
            }
            
            const grid = document.getElementById('testsGrid');
            if (!grid) return;
            
            grid.innerHTML = '';
            
            // מבחנים שונים לבנים ולבנות
            const tests = currentGender === 'boys' ? [
                { id: 'pullups', name: 'מתח', unit: 'חזרות' },
                { id: 'pushups', name: 'שכיבות שמיכה', unit: 'חזרות' },
                { id: 'jumprope', name: 'דלגית', unit: 'חזרות' },
                { id: 'medicineball', name: 'ריצת כדורי כוח', unit: 'שניות' },
                { id: 'running2000', name: 'ריצת 2,000 מטר', unit: 'דקות:שניות' },
                { id: 'theory', name: 'מבחן עיוני', unit: 'ציון' }
            ] : [
                { id: 'running2000_girls', name: 'ריצת 2,000 מטר', unit: 'דקות:שניות' },
                { id: 'jumprope_girls', name: 'דלגית', unit: 'חזרות' },
                { id: 'pushups_knees', name: 'שכיבות שמיכה ברכיים', unit: 'חזרות' },
                { id: 'pushups_regular', name: 'שכיבות שמיכה רגיל', unit: 'חזרות' },
                { id: 'pullups_band', name: 'מתח עם גומיה', unit: 'חזרות' },
                { id: 'ladder', name: 'מעבר סולם', unit: 'חזרות/זמן' },
                { id: 'plank', name: 'פלאנק', unit: 'שניות' },
                { id: 'theory_girls', name: 'מבחן עיוני', unit: 'ציון' }
            ];
            
            tests.forEach(test => {
                const testCard = document.createElement('div');
                testCard.className = 'test-card';
                
                const icon = getTestIcon(test.id);
                
                // בדיקה אם יש כבר ציונים למבחן זה
                let savedCount = 0;
                const testKey = `${currentGender}_${currentClass}_${test.id}`;
                if (allTestResults[testKey]) {
                    savedCount = Object.keys(allTestResults[testKey]).length;
                }
                
                testCard.innerHTML = `
                    <h3><i class="fas fa-${icon}"></i> ${test.name}</h3>
                    <p style="color: #666; margin: 5px 0;">יחידת מידה: ${test.unit}</p>
                    <div class="progress-container">
                        <small>${savedCount > 0 ? `${savedCount} ציונים נשמרו` : 'לחץ לבחירת המבחן'}</small>
                        <div class="progress-bar">
                            <div class="progress-fill" style="width: ${Math.min(100, (savedCount / students.length) * 100)}%"></div>
                        </div>
                    </div>
                    ${savedCount > 0 ? `
                    <div style="margin-top: 10px;">
                        <button class="btn btn-small btn-danger" onclick="clearTestData('${test.id}', event)">
                            <i class="fas fa-trash"></i> נקה נתוני מבחן זה
                        </button>
                    </div>
                    ` : ''}
                `;
                
                testCard.onclick = () => {
                    currentTest = test.id;
                    currentTestType = test;
                    loadResultsTable();
                    showScreen('resultsScreen');
                };
                
                grid.appendChild(testCard);
            });
        }

        // קבלת אייקון למבחן
        function getTestIcon(testId) {
            const icons = {
                'pullups': 'dumbbell',
                'pushups': 'hand-paper',
                'jumprope': 'running',
                'medicineball': 'basketball-ball',
                'running2000': 'running',
                'theory': 'book',
                'running2000_girls': 'running',
                'jumprope_girls': 'running',
                'pullups_band': 'dumbbell',
                'pushups_knees': 'hand-paper',
                'pushups_regular': 'hand-paper',
                'ladder': 'stairs',
                'plank': 'clock',
                'theory_girls': 'book'
            };
            return icons[testId] || 'running';
        }

        // פונקציה חדשה: ניקוי נתוני מבחן ספציפי
        function clearTestData(testId, event) {
            event.stopPropagation(); // מונע מהקלאק לעבור לכרטיס המבחן
            
            const testName = getTestNameFromId(testId);
            
            if (confirm(`האם אתה בטוח שברצונך למחוק את כל הציונים של ${testName} בכיתה יב'${currentClass}?`)) {
                const testKey = `${currentGender}_${currentClass}_${testId}`;
                
                if (allTestResults[testKey]) {
                    delete allTestResults[testKey];
                    showNotification(`נמחקו כל הציונים של ${testName} מכיתה יב'${currentClass}`, 'success');
                    
                    // עדכון התצוגה
                    updateTestScreen();
                } else {
                    showNotification('לא נמצאו ציונים למבחן זה', 'warning');
                }
            }
        }

        // פונקציה חדשה: קבלת שם מבחן לפי מזהה
        function getTestNameFromId(testId) {
            const testNames = {
                'pullups': 'מתח',
                'pushups': 'שכיבות שמיכה',
                'jumprope': 'דלגית',
                'medicineball': 'ריצת כדורי כוח',
                'running2000': 'ריצת 2,000 מטר',
                'theory': 'מבחן עיוני',
                'running2000_girls': 'ריצת 2,000 מטר',
                'jumprope_girls': 'דלגית',
                'pullups_band': 'מתח עם גומיה',
                'pushups_knees': 'שכיבות שמיכה ברכיים',
                'pushups_regular': 'שכיבות שמיכה רגיל',
                'ladder': 'מעבר סולם',
                'plank': 'פלאנק',
                'theory_girls': 'מבחן עיוני'
            };
            return testNames[testId] || testId;
        }

        // טעינת טבלת התוצאות
        function loadResultsTable() {
            const title = document.getElementById('resultsScreenTitle');
            if (title) {
                title.textContent = `כיתה יב'${currentClass} - ${currentTestType.name}`;
            }
            
            const tableDiv = document.getElementById('resultsTable');
            if (!tableDiv) return;
            
            // בדיקה אם יש ציונים קיימים
            const testKey = `${currentGender}_${currentClass}_${currentTest}`;
            const existingResults = allTestResults[testKey] || {};
            
            let html = `
                <div class="info-box">
                    <h3><i class="fas fa-info-circle"></i> ${students.length} ${currentGender === 'boys' ? 'תלמידים' : 'תלמידות'}</h3>
                    <p>הזן את תוצאות המבחן עבור כל ${currentGender === 'boys' ? 'תלמיד' : 'תלמידה'}</p>
                    <p><strong>הערה:</strong> הציון יחושב אוטומטית לפי טבלאות המרה של משרד החינוך</p>
                </div>
                
                <table>
                    <thead>
                        <tr>
                            <th>מס'</th>
                            <th>שם משפחה</th>
                            <th>שם פרטי</th>
                            <th>תוצאה (${currentTestType.unit})</th>
                            <th>ציון</th>
                            <th>סטטוס</th>
                        </tr>
                    </thead>
                    <tbody>
            `;
            
            students.forEach((student, index) => {
                const studentNumber = index + 1;
                const studentKey = `${student.lastName}_${student.firstName}`;
                const existingResult = existingResults[studentKey];
                const resultValue = existingResult ? existingResult.result : '';
                const gradeValue = existingResult ? existingResult.grade : '';
                const statusText = existingResult ? 'נשמר' : 'ממתין להזנה';
                const statusColor = existingResult ? '#27ae60' : '#666';
                const gradeClass = existingResult ? 
                    (gradeValue >= 90 ? 'excellent' : 
                     gradeValue >= 75 ? 'good' : 
                     gradeValue >= 60 ? 'average' : 'poor') : '';
                
                html += `
                    <tr>
                        <td style="text-align: center;">${studentNumber}</td>
                        <td><strong>${student.lastName}</strong></td>
                        <td>${student.firstName}</td>
                        <td>
                            <input type="${currentTest === 'running2000' || currentTest === 'running2000_girls' || currentTest === 'ladder' || currentTest === 'plank' ? 'text' : 'number'}" 
                                   id="result_${student.id}" 
                                   placeholder="הזן ${currentTestType.unit}"
                                   value="${resultValue}"
                                   style="text-align: center; width: 100%; padding: 5px;"
                                   onchange="updateResult(${student.id}, this.value, '${student.lastName}', '${student.firstName}')"
                                   oninput="updateResult(${student.id}, this.value, '${student.lastName}', '${student.firstName}')"
                                   min="0" ${currentTest === 'medicineball' || currentTest === 'plank' ? 'step="0.1"' : ''}>
                        </td>
                        <td style="text-align: center;">
                            <span id="grade_${student.id}" class="result-badge ${gradeClass}">
                                ${gradeValue || '--'}
                            </span>
                        </td>
                        <td style="text-align: center;">
                            <small id="status_${student.id}" style="color: ${statusColor};">
                                ${statusText}
                            </small>
                        </td>
                    </tr>
                `;
            });
            
            html += `
                    </tbody>
                </table>
                <div class="info-box" style="margin-top: 20px;">
                    <h4>הוראות:</h4>
                    <p>1. הזן את התוצאה עבור כל ${currentGender === 'boys' ? 'תלמיד' : 'תלמידה'}</p>
                    <p>2. הציון יחושב אוטומטית לפי טבלאות משרד החינוך</p>
                    <p>3. לחץ על "שמור תוצאות" כדי לשמור את כל הנתונים</p>
                </div>
            `;
            
            tableDiv.innerHTML = html;
            
            // עדכן ציונים אם יש ערכים קיימים
            students.forEach(student => {
                const resultInput = document.getElementById(`result_${student.id}`);
                if (resultInput && resultInput.value) {
                    updateResult(student.id, resultInput.value, student.lastName, student.firstName);
                }
            });
        }

        // עדכון תוצאה - התוצאה מוסתרת והציון מחושב אוטומטית
        function updateResult(studentId, value, lastName, firstName) {
            const gradeElement = document.getElementById(`grade_${studentId}`);
            const statusElement = document.getElementById(`status_${studentId}`);
            
            if (value && value.trim() !== '') {
                // חישוב ציון לפי סוג המבחן והטבלאות
                let grade = calculateGradeFromTable(value, currentTest);
                
                // הצגת הציון בלבד (התוצאה עצמה לא מוצגת)
                gradeElement.textContent = grade;
                gradeElement.className = `result-badge ${
                    grade >= 90 ? 'excellent' : 
                    grade >= 75 ? 'good' : 
                    grade >= 60 ? 'average' : 'poor'
                }`;
                statusElement.textContent = 'מוכן לשמירה';
                statusElement.style.color = '#f39c12';
            } else {
                gradeElement.textContent = '--';
                gradeElement.className = 'result-badge';
                statusElement.textContent = 'ממתין להזנה';
                statusElement.style.color = '#666';
            }
        }

        // ============================================
        // פונקציות חישוב ציונים עם טבלת בנות
        // ============================================

        // חיפוש ציון בטבלת הבנות
        function getGirlsScoreFromTable(testName, value) {
            if (!value || value === '') return 0;
            
            // המרת ערך למספר אם אפשר
            const numericValue = isNaN(value) ? value : parseFloat(value);
            
            // חיפוש בכל השורות בטבלה
            for (const row of girlsConversionTable) {
                // בדיקת התאמה לפי סוג המבחן
                let matches = false;
                
                switch(testName) {
                    case 'running2000_girls':
                        if (row.running && isTimeInRange(numericValue, row.running)) {
                            return row.score;
                        }
                        break;
                        
                    case 'jumprope_girls':
                        if (row.jumprope && numericValue >= row.jumprope) {
                            return row.score;
                        }
                        break;
                        
                    case 'pullups_band':
                        if (row.pullups_band && numericValue >= row.pullups_band) {
                            return row.score;
                        }
                        break;
                        
                    case 'pushups_knees':
                        if (row.pushups_knees && numericValue >= row.pushups_knees) {
                            return row.score;
                        }
                        break;
                        
                    case 'pushups_regular':
                        if (row.pushups_regular && numericValue >= row.pushups_regular) {
                            return row.score;
                        }
                        break;
                        
                    case 'ladder':
                        if (row.ladder && numericValue >= row.ladder) {
                            return row.score;
                        }
                        break;
                }
            }
            
            // אם לא נמצאה התאמה מדויקת, מחזירים ציון יחסי
            return getRelativeScore(testName, numericValue);
        }

        // בדיקה אם זמן נמצא בטווח
        function isTimeInRange(timeStr, rangeStr) {
            if (!timeStr || !rangeStr) return false;
            
            // ניקוי מחרוזות
            const cleanTime = timeStr.toString().trim().replace('״', '').replace('"', '').replace("'", ':');
            const cleanRange = rangeStr.toString().trim();
            
            // אם הטווח הוא נקודת זמן אחת
            if (!cleanRange.includes('-')) {
                const targetTime = timeToMinutes(cleanTime);
                const rangeTime = timeToMinutes(cleanRange);
                return Math.abs(targetTime - rangeTime) <= 0.1; // דיוק של 0.1 דקות
            }
            
            // פיצול טווח זמן
            const [start, end] = cleanRange.split('-');
            const timeMinutes = timeToMinutes(cleanTime);
            const startMinutes = timeToMinutes(start);
            const endMinutes = timeToMinutes(end);
            
            return timeMinutes >= startMinutes && timeMinutes <= endMinutes;
        }

        // המרת זמן לדקות
        function timeToMinutes(timeStr) {
            if (!timeStr) return 0;
            
            const cleanTime = timeStr.toString().trim().replace('״', '').replace('"', '').replace("'", ':');
            
            if (cleanTime.includes(':')) {
                const [minutes, seconds] = cleanTime.split(':');
                return parseInt(minutes) + (parseInt(seconds) / 60);
            }
            
            return parseFloat(cleanTime) || 0;
        }

        // חישוב ציון יחסי אם לא נמצאה התאמה מדויקת
        function getRelativeScore(testName, value) {
            // חיפוש שני הערכים הקרובים ביותר
            let lowerScore = 0;
            let lowerValue = 0;
            let upperScore = 100;
            let upperValue = Infinity;
            
            for (const row of girlsConversionTable) {
                let rowValue = 0;
                
                switch(testName) {
                    case 'running2000_girls':
                        if (row.running) {
                            const rangeParts = row.running.toString().split('-');
                            rowValue = timeToMinutes(rangeParts[0]);
                        }
                        break;
                        
                    case 'jumprope_girls':
                        rowValue = row.jumprope || 0;
                        break;
                        
                    case 'pullups_band':
                        rowValue = row.pullups_band || 0;
                        break;
                        
                    case 'pushups_knees':
                        rowValue = row.pushups_knees || 0;
                        break;
                        
                    case 'pushups_regular':
                        rowValue = row.pushups_regular || 0;
                        break;
                        
                    case 'ladder':
                        rowValue = row.ladder || 0;
                        break;
                }
                
                if (rowValue <= value && rowValue > lowerValue) {
                    lowerScore = row.score;
                    lowerValue = rowValue;
                }
                
                if (rowValue >= value && rowValue < upperValue) {
                    upperScore = row.score;
                    upperValue = rowValue;
                }
            }
            
            // חישוב ציון יחסי
            if (lowerValue === upperValue) {
                return lowerScore;
            }
            
            const ratio = (value - lowerValue) / (upperValue - lowerValue);
            return Math.round(lowerScore + (upperScore - lowerScore) * ratio);
        }

        // חיפוש ציון מטבלת ריצת 2,000 מטר
        function getScoreFromRunningTable(timeStr) {
            // ניקוי והפיכת הזמן לפורמט אחיד
            let cleanTime = timeStr.trim().replace('״', '').replace('"', '').replace("'", ':');
            
            // אם יש רק מספרים ללא נקודתיים, הוסף נקודתיים
            if (cleanTime.length <= 2) {
                cleanTime = "00:" + cleanTime.padStart(2, '0');
            } else if (!cleanTime.includes(':') && cleanTime.length === 4) {
                cleanTime = cleanTime.substring(0, 2) + ':' + cleanTime.substring(2, 4);
            }
            
            // הפורמט הסופי: MM:SS
            let minutes = 0;
            let seconds = 0;
            
            if (cleanTime.includes(':')) {
                const parts = cleanTime.split(':');
                minutes = parseInt(parts[0]) || 0;
                seconds = parseInt(parts[1]) || 0;
            } else {
                // אם הזמן בפורמט דקות בלבד
                minutes = parseInt(cleanTime) || 0;
            }
            
            // חיפוש מדויק בטבלה
            const searchTime = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
            
            for (const item of running2000Table) {
                if (item.time === searchTime) {
                    return item.score;
                }
            }
            
            // אם לא נמצא, חיפוש לפי הקרוב ביותר
            let bestMatch = running2000Table[0];
            let minDiff = Infinity;
            
            const totalSeconds = minutes * 60 + seconds;
            
            for (const item of running2000Table) {
                const itemParts = item.time.split(':');
                const itemMinutes = parseInt(itemParts[0]);
                const itemSeconds = parseInt(itemParts[1]);
                const itemTotalSeconds = itemMinutes * 60 + itemSeconds;
                
                const diff = Math.abs(itemTotalSeconds - totalSeconds);
                if (diff < minDiff) {
                    minDiff = diff;
                    bestMatch = item;
                }
            }
            
            return bestMatch.score;
        }

        // חיפוש ציון מטבלת כדורי כוח
        function getScoreFromMedicineBallTable(time) {
            for (const item of medicineBallTable) {
                if (time >= item.time) {
                    return item.score;
                }
            }
            return 30; // ציון מינימלי אם הזמן גבוה מהמקסימום בטבלה
        }

        // חיפוש ציון מטבלת דלגית
        function getScoreFromJumpRopeTable(count) {
            for (const item of jumpRopeTable) {
                if (count >= item.count) {
                    return item.score;
                }
            }
            return 40; // ציון מינימלי אם הכמות נמוכה מהמינימום בטבלה
        }

        // חיפוש ציון מטבלת מתח
        function getScoreFromPullupsTable(count) {
            const roundedCount = Math.round(count);
            for (const item of pullupsTable) {
                if (roundedCount >= item.count) {
                    return item.score;
                }
            }
            return 50; // ציון מינימלי אם הכמות נמוכה מהמינימום בטבלה
        }

        // חיפוש ציון מטבלת שכיבות שמיכה
        function getScoreFromPushupsTable(count) {
            const roundedCount = Math.round(count);
            for (const item of pushupsTable) {
                if (roundedCount >= item.count) {
                    return item.score;
                }
            }
            return 30; // ציון מינימלי אם הכמות נמוכה מהמינימום בטבלה
        }

        // ===== פונקציה חדשה: בדיקה אם זמן קטן מ-10 דקות =====
        function isTimeLessThan10Minutes(timeStr) {
            if (!timeStr) return false;
            
            // ניקוי מחרוזת הזמן
            const cleanTime = timeStr.toString().trim().replace('״', '').replace('"', '').replace("'", ':');
            
            let minutes = 0;
            let seconds = 0;
            
            if (cleanTime.includes(':')) {
                const parts = cleanTime.split(':');
                minutes = parseInt(parts[0]) || 0;
                seconds = parseInt(parts[1]) || 0;
            } else if (cleanTime.length <= 2) {
                // אם יש רק שניות (למשל "45")
                seconds = parseInt(cleanTime) || 0;
                minutes = 0;
            } else {
                // אם זה מספר שלם (למשל "950" עבור 9:50)
                const timeNum = parseInt(cleanTime);
                if (timeNum < 1000) {
                    // זמן בפורמט דקות:שניות ללא נקודתיים
                    minutes = Math.floor(timeNum / 100);
                    seconds = timeNum % 100;
                } else {
                    // מספר גדול מדי, לא יכול להיות זמן תקני פחות מ-10 דקות
                    return false;
                }
            }
            
            // בדיקה אם הזמן קטן מ-10:00
            // כלומר: או דקות < 10, או דקות = 9 ושניות < 60
            if (minutes < 9) {
                return true; // כל זמן שהוא 8:XX ומטה
            } else if (minutes === 9) {
                return seconds < 60; // 9:XX (עד 9:59)
            }
            
            return false; // 10:XX ומעלה
        }

        // ===== פונקציית בדיקה לנוחיות =====
        function testGirlsRunningRules() {
            console.log("=== בדיקת חוקי ריצת בנות ===");
            console.log("9:30 -> פחות מ-10:00?", isTimeLessThan10Minutes("9:30"));
            console.log("9:59 -> פחות מ-10:00?", isTimeLessThan10Minutes("9:59"));
            console.log("10:00 -> פחות מ-10:00?", isTimeLessThan10Minutes("10:00"));
            console.log("10:01 -> פחות מ-10:00?", isTimeLessThan10Minutes("10:01"));
            console.log("8:45 -> פחות מ-10:00?", isTimeLessThan10Minutes("8:45"));
            console.log("950 -> פחות מ-10:00? (9:50)", isTimeLessThan10Minutes("950"));
            console.log("959 -> פחות מ-10:00? (9:59)", isTimeLessThan10Minutes("959"));
            console.log("1000 -> פחות מ-10:00? (10:00)", isTimeLessThan10Minutes("1000"));
            
            // בדיקת חישוב ציון
            console.log("\n=== בדיקת חישוב ציון ===");
            console.log("9:30 ->", calculateGradeFromTable("9:30", "running2000_girls"));
            console.log("9:45 ->", calculateGradeFromTable("9:45", "running2000_girls"));
            console.log("10:00 ->", calculateGradeFromTable("10:00", "running2000_girls"));
            console.log("10:15 ->", calculateGradeFromTable("10:15", "running2000_girls"));
            
            showNotification("חוקי ריצת בנות נבדקו - ראה קונסול", "info");
        }

        // חישוב ציון מתוך טבלאות המרה
        function calculateGradeFromTable(value, testType) {
            // המרת הערך למספר או שמירה כמחרוזת (לזמן ריצה)
            let numericValue;
            
            // ===== תיקון: תלמידות שרצות פחות מ-10:00 בריצת 2000 מקבלות ציון 100 =====
            if (testType === 'running2000_girls' && currentGender === 'girls') {
                // בדיקה אם הזמן קטן מ-10:00 (כלומר, 9:59 ומטה)
                if (isTimeLessThan10Minutes(value)) {
                    return 100; // ציון 100 אוטומטית
                }
                return getGirlsScoreFromTable('running2000_girls', value);
            }
            // ===== סוף תיקון =====
            
            if (testType === 'running2000') {
                // ריצת 2,000 מטר - שמירת הזמן כמחרוזת
                return getScoreFromRunningTable(value);
            } else if (testType === 'plank') {
                // פלאנק - חישוב מיוחד (לדוגמה: 60 שניות = 100, 30 שניות = 50)
                numericValue = parseFloat(value);
                if (isNaN(numericValue)) return 0;
                
                // טבלת המרה לפלאנק (זמן בשניות → ציון)
                if (numericValue >= 60) return 100;
                if (numericValue >= 55) return 95;
                if (numericValue >= 50) return 90;
                if (numericValue >= 45) return 85;
                if (numericValue >= 40) return 80;
                if (numericValue >= 35) return 75;
                if (numericValue >= 30) return 70;
                if (numericValue >= 25) return 65;
                if (numericValue >= 20) return 60;
                if (numericValue >= 15) return 55;
                if (numericValue >= 10) return 50;
                if (numericValue >= 5) return 40;
                if (numericValue >= 1) return 30;
                return 0;
            } else {
                // המרה למספר
                numericValue = parseFloat(value);
                if (isNaN(numericValue)) return 0;
                
                // בדיקה לפי סוג המבחן
                if (testType === 'medicineball') {
                    return getScoreFromMedicineBallTable(numericValue);
                } else if (testType === 'jumprope') {
                    return getScoreFromJumpRopeTable(numericValue);
                } else if (testType === 'jumprope_girls') {
                    return getGirlsScoreFromTable('jumprope_girls', numericValue);
                } else if (testType === 'pullups') {
                    return getScoreFromPullupsTable(numericValue);
                } else if (testType === 'pullups_band') {
                    return getGirlsScoreFromTable('pullups_band', numericValue);
                } else if (testType === 'pushups') {
                    return getScoreFromPushupsTable(numericValue);
                } else if (testType === 'pushups_knees') {
                    return getGirlsScoreFromTable('pushups_knees', numericValue);
                } else if (testType === 'pushups_regular') {
                    return getGirlsScoreFromTable('pushups_regular', numericValue);
                } else if (testType === 'ladder') {
                    return getGirlsScoreFromTable('ladder', numericValue);
                } else if (testType === 'theory' || testType === 'theory_girls') {
                    return Math.min(100, Math.max(0, Math.round(numericValue)));
                }
            }
            
            return 0;
        }

        // בדיקת טבלאות המרה
        function testConversionTables() {
            console.log("=== בדיקת טבלאות המרה ===");
            
            // בדיקת דוגמאות
            console.log("דוגמאות לטבלת ריצת 2,000 מטר:");
            console.log("07:00 ->", getScoreFromRunningTable("07:00"));
            console.log("08:30 ->", getScoreFromRunningTable("08:30"));
            console.log("10:00 ->", getScoreFromRunningTable("10:00"));
            
            console.log("\nדוגמאות לטבלת כדורי כוח:");
            console.log("30 שניות ->", getScoreFromMedicineBallTable(30));
            console.log("25 שניות ->", getScoreFromMedicineBallTable(25));
            console.log("20 שניות ->", getScoreFromMedicineBallTable(20));
            
            console.log("\nדוגמאות לטבלת דלגית:");
            console.log("150 ->", getScoreFromJumpRopeTable(150));
            console.log("100 ->", getScoreFromJumpRopeTable(100));
            console.log("50 ->", getScoreFromJumpRopeTable(50));
            
            console.log("\nדוגמאות לטבלת מתח:");
            console.log("16 ->", getScoreFromPullupsTable(16));
            console.log("10 ->", getScoreFromPullupsTable(10));
            console.log("5 ->", getScoreFromPullupsTable(5));
            
            console.log("\nדוגמאות לטבלת שכיבות שמיכה:");
            console.log("55 ->", getScoreFromPushupsTable(55));
            console.log("30 ->", getScoreFromPushupsTable(30));
            console.log("15 ->", getScoreFromPushupsTable(15));
            
            showNotification("טבלאות המרה נבדקו - ראה קונסול לפרטים", "info");
        }

        // בדיקת טבלת בנות
        function testGirlsTable() {
            console.log("=== בדיקת טבלת בנות ===");
            console.log("טבלת הבנות מכילה", girlsConversionTable.length, "שורות");
            
            // בדיקת דוגמאות
            console.log("\nדוגמאות לטבלת דלגית בנות:");
            console.log("150 ->", getGirlsScoreFromTable('jumprope_girls', 150));
            console.log("100 ->", getGirlsScoreFromTable('jumprope_girls', 100));
            console.log("50 ->", getGirlsScoreFromTable('jumprope_girls', 50));
            
            console.log("\nדוגמאות לטבלת מתח עם גומיה:");
            console.log("14 ->", getGirlsScoreFromTable('pullups_band', 14));
            console.log("10 ->", getGirlsScoreFromTable('pullups_band', 10));
            console.log("5 ->", getGirlsScoreFromTable('pullups_band', 5));
            
            console.log("\nדוגמאות לטבלת שכיבות שמיכה ברכיים:");
            console.log("35 ->", getGirlsScoreFromTable('pushups_knees', 35));
            console.log("20 ->", getGirlsScoreFromTable('pushups_knees', 20));
            console.log("10 ->", getGirlsScoreFromTable('pushups_knees', 10));
            
            console.log("\nדוגמאות לטבלת שכיבות שמיכה רגיל:");
            console.log("15 ->", getGirlsScoreFromTable('pushups_regular', 15));
            console.log("10 ->", getGirlsScoreFromTable('pushups_regular', 10));
            console.log("5 ->", getGirlsScoreFromTable('pushups_regular', 5));
            
            console.log("\nדוגמאות לטבלת מעבר סולם:");
            console.log("10 ->", getGirlsScoreFromTable('ladder', 10));
            console.log("7 ->", getGirlsScoreFromTable('ladder', 7));
            console.log("3 ->", getGirlsScoreFromTable('ladder', 3));
            
            console.log("\nדוגמאות לטבלת ריצת 2,000 מטר בנות:");
            console.log("10:15 ->", getGirlsScoreFromTable('running2000_girls', "10:15"));
            console.log("12:00 ->", getGirlsScoreFromTable('running2000_girls', "12:00"));
            console.log("14:30 ->", getGirlsScoreFromTable('running2000_girls', "14:30"));
            
            showNotification("טבלת בנות נבדקה - ראה קונסול לפרטים", "info");
        }

        // שמירת תוצאות
        function saveResults() {
            const testKey = `${currentGender}_${currentClass}_${currentTest}`;
            
            if (!allTestResults[testKey]) {
                allTestResults[testKey] = {};
            }
            
            let savedCount = 0;
            let updatedCount = 0;
            let deletedCount = 0;
            
            students.forEach(student => {
                const resultInput = document.getElementById(`result_${student.id}`);
                const gradeElement = document.getElementById(`grade_${student.id}`);
                const studentKey = `${student.lastName}_${student.firstName}`;
                
                if (resultInput && resultInput.value && resultInput.value.trim() !== '') {
                    // יש תוצאה - שמירה או עדכון
                    const existing = allTestResults[testKey][studentKey];
                    
                    allTestResults[testKey][studentKey] = {
                        result: resultInput.value,
                        grade: parseInt(gradeElement.textContent) || 0,
                        studentId: student.id,
                        lastName: student.lastName,
                        firstName: student.firstName
                    };
                    
                    if (existing) {
                        updatedCount++;
                    } else {
                        savedCount++;
                    }
                } else {
                    // אין תוצאה - מחיקה אם קיימת
                    if (allTestResults[testKey][studentKey]) {
                        delete allTestResults[testKey][studentKey];
                        deletedCount++;
                    }
                }
            });
            
            // ניקוי מפתח ריק אם אין תוצאות
            if (Object.keys(allTestResults[testKey]).length === 0) {
                delete allTestResults[testKey];
            }
            
            let message = '';
            if (savedCount > 0 && updatedCount > 0 && deletedCount > 0) {
                message = `נשמרו ${savedCount} ציונים חדשים, עודכנו ${updatedCount} ונמחקו ${deletedCount}!`;
            } else if (savedCount > 0) {
                message = `נשמרו ${savedCount} ציונים חדשים בהצלחה!`;
            } else if (updatedCount > 0) {
                message = `עודכנו ${updatedCount} ציונים קיימים!`;
            } else if (deletedCount > 0) {
                message = `נמחקו ${deletedCount} ציונים!`;
            } else {
                showNotification('לא נשמרו ציונים חדשים', 'warning');
                return;
            }
            
            showNotification(message, 'success');
            
            // עדכון מסך המבחנים
            setTimeout(() => {
                updateTestScreen();
                showScreen('testScreen');
            }, 1000);
        }

        // טעינת ציוני מבחן עיוני
        function loadTheoryGrades() {
            let loadedCount = 0;
            let errorCount = 0;
            
            theoryGradesData.forEach(gradeData => {
                // מציאת התלמיד המתאים
                let student = null;
                
                // חיפוש בקובץ הבנים
                student = boysData.find(s => 
                    s.firstName === gradeData.firstName && 
                    s.lastName === gradeData.lastName && 
                    s.class === gradeData.class
                );
                
                // אם לא נמצא בנים, חפש בנות
                if (!student) {
                    student = girlsData.find(s => 
                        s.firstName === gradeData.firstName && 
                        s.lastName === gradeData.lastName && 
                        s.class === gradeData.class
                    );
                }
                
                if (student) {
                    const gender = student.gender;
                    const testKey = `${gender}_${gradeData.class}_${gender === 'boys' ? 'theory' : 'theory_girls'}`;
                    
                    if (!allTestResults[testKey]) {
                        allTestResults[testKey] = {};
                    }
                    
                    const studentKey = `${student.lastName}_${student.firstName}`;
                    allTestResults[testKey][studentKey] = {
                        result: gradeData.score.toString(),
                        grade: gradeData.score,
                        studentId: student.id,
                        lastName: student.lastName,
                        firstName: student.firstName
                    };
                    
                    loadedCount++;
                } else {
                    errorCount++;
                    console.log(`לא נמצא: ${gradeData.firstName} ${gradeData.lastName} כיתה ${gradeData.class}`);
                }
            });
            
            showNotification(`נטענו ${loadedCount} ציוני מבחן עיוני! ${errorCount > 0 ? `(${errorCount} לא נמצאו)` : ''}`, 'success');
            
            // עדכון הספירה
            updateTotalCount();
        }

        // בדיקת נתוני הבנות
        function debugGirlsData() {
            console.log("=== נתוני בנות ===");
            console.log("סה\"כ תלמידות:", girlsData.length);
            
            const classCounts = {};
            for (let i = 1; i <= 12; i++) {
                classCounts[i] = girlsData.filter(g => g.class === i).length;
            }
            
            console.log("פירוט לפי כיתות:", classCounts);
            
            showNotification(`נטענו ${girlsData.length} תלמידות`, 'success');
        }

        // בדיקת נתוני הבנים
        function debugBoysData() {
            console.log("=== נתוני בנים ===");
            console.log("סה\"כ תלמידים:", boysData.length);
            
            const classCounts = {};
            for (let i = 1; i <= 12; i++) {
                classCounts[i] = boysData.filter(b => b.class === i).length;
            }
            
            console.log("פירוט לפי כיתות:", classCounts);
            
            showNotification(`נטענו ${boysData.length} תלמידים`, 'success');
        }

        // בדיקת מערכת
        function debugSystem() {
            console.log("=== בדיקת מערכת ===");
            console.log("סה\"כ תלמידים:", allStudentsData.length);
            console.log("בנות:", girlsData.length);
            console.log("בנים:", boysData.length);
            
            // ספירת מבחנים שנשמרו
            let savedTestsCount = Object.keys(allTestResults).length;
            let savedGradesCount = 0;
            
            for (const testKey in allTestResults) {
                savedGradesCount += Object.keys(allTestResults[testKey]).length;
            }
            
            console.log("מבחנים שנשמרו:", savedTestsCount);
            console.log("ציונים שנשמרו:", savedGradesCount);
            
            // בדיקת טבלאות המרה
            console.log("=== טבלאות המרה ===");
            console.log("טבלת ריצת 2,000:", running2000Table.length, "ערכים");
            console.log("טבלת כדורי כוח:", medicineBallTable.length, "ערכים");
            console.log("טבלת דלגית:", jumpRopeTable.length, "ערכים");
            console.log("טבלת מתח:", pullupsTable.length, "ערכים");
            console.log("טבלת שכיבות:", pushupsTable.length, "ערכים");
            console.log("טבלת בנות:", girlsConversionTable.length, "ערכים");
            
            showNotification(`מערכת מוכנה: ${allStudentsData.length} תלמידים, ${savedGradesCount} ציונים`, 'info');
        }

        // עדכון ספירת תלמידים
        function updateTotalCount() {
            const element = document.getElementById('totalStudentsCount');
            if (element) {
                const totalCount = allStudentsData.length;
                element.textContent = totalCount;
            }
        }

        // ============================================
        // פונקציות דירוג שכבה עם סינון וגרפים
        // ============================================

        // ============================================
        // פונקציה חדשה: חישוב ציון סופי מיוחד לבנות - מתוקנת
        // ============================================
        function calculateGirlsFinalGrade(weightedSum, student) {
            const studentKey = `${student.lastName}_${student.firstName}`;
            
            // אתחול משתנים
            let theoryGrade = null;
            let runningGrade = null;
            let jumpropeGrade = null;
            let pushupsRegularGrade = null;
            let pushupsKneesGrade = null;
            let pullupsBandGrade = null;
            let ladderGrade = null;
            let plankGrade = null;
            
            // בדיקה האם יש ציון במבחן עיוני
            for (const testKey in allTestResults) {
                if (testKey.includes('theory_girls') && allTestResults[testKey][studentKey]) {
                    theoryGrade = allTestResults[testKey][studentKey].grade;
                }
            }
            
            // בדיקה האם יש ציון בריצת 2000
            for (const testKey in allTestResults) {
                if (testKey.includes('running2000_girls') && allTestResults[testKey][studentKey]) {
                    runningGrade = allTestResults[testKey][studentKey].grade;
                }
            }
            
            // בדיקה האם יש ציון בדלגית
            for (const testKey in allTestResults) {
                if (testKey.includes('jumprope_girls') && allTestResults[testKey][studentKey]) {
                    jumpropeGrade = allTestResults[testKey][studentKey].grade;
                }
            }
            
            // בדיקה האם יש ציון בשכיבות שמיכה רגיל
            for (const testKey in allTestResults) {
                if (testKey.includes('pushups_regular') && allTestResults[testKey][studentKey]) {
                    pushupsRegularGrade = allTestResults[testKey][studentKey].grade;
                }
            }
            
            // בדיקה האם יש ציון בשכיבות שמיכה ברכיים
            for (const testKey in allTestResults) {
                if (testKey.includes('pushups_knees') && allTestResults[testKey][studentKey]) {
                    pushupsKneesGrade = allTestResults[testKey][studentKey].grade;
                }
            }
            
            // בדיקה האם יש ציון במתח עם גומיה
            for (const testKey in allTestResults) {
                if (testKey.includes('pullups_band') && allTestResults[testKey][studentKey]) {
                    pullupsBandGrade = allTestResults[testKey][studentKey].grade;
                }
            }
            
            // בדיקה האם יש ציון במעבר סולם
            for (const testKey in allTestResults) {
                if (testKey.includes('ladder') && allTestResults[testKey][studentKey]) {
                    ladderGrade = allTestResults[testKey][studentKey].grade;
                }
            }
            
            // בדיקה האם יש ציון בפלאנק
            for (const testKey in allTestResults) {
                if (testKey.includes('plank') && allTestResults[testKey][studentKey]) {
                    plankGrade = allTestResults[testKey][studentKey].grade;
                }
            }
            
            // חישוב weightedSum מחדש
            weightedSum = 0;
            let actualWeight = 0;
            
            // רשימה של כל סוגי המבחנים האפשריים לבנות
            const tests = [
                { grade: theoryGrade, weight: 0.20, name: 'עיוני' },
                { grade: runningGrade, weight: 0.20, name: 'ריצה' },
                { grade: jumpropeGrade, weight: 0.15, name: 'דלגית' },
                { grade: plankGrade, weight: 0.15, name: 'פלאנק' }
            ];
            
            // הוספת שכיבות שמיכה (ברכיים או רגיל)
            if (pushupsRegularGrade !== null) {
                tests.push({ grade: pushupsRegularGrade, weight: 0.15, name: 'שכיבות שמיכה רגיל' });
            } else if (pushupsKneesGrade !== null) {
                tests.push({ grade: pushupsKneesGrade, weight: 0.15, name: 'שכיבות שמיכה ברכיים' });
            } else {
                tests.push({ grade: null, weight: 0.15, name: 'שכיבות שמיכה' });
            }
            
            // הוספת מתח (עם גומיה או מעבר סולם)
            if (pullupsBandGrade !== null) {
                tests.push({ grade: pullupsBandGrade, weight: 0.15, name: 'מתח עם גומיה' });
            } else if (ladderGrade !== null) {
                tests.push({ grade: ladderGrade, weight: 0.15, name: 'מעבר סולם' });
            } else {
                tests.push({ grade: null, weight: 0.15, name: 'מתח/סולם' });
            }
            
            // חישוב weightedSum
            for (const test of tests) {
                if (test.grade !== null) {
                    weightedSum += test.grade * test.weight;
                    actualWeight += test.weight;
                }
            }
            
            // קביעת סטטוס - "מלא" רק כאשר יש את כל 6 המבחנים
            const hasAllGrades = (
                theoryGrade !== null &&
                runningGrade !== null &&
                jumpropeGrade !== null &&
                plankGrade !== null &&
                (pushupsRegularGrade !== null || pushupsKneesGrade !== null) &&
                (pullupsBandGrade !== null || ladderGrade !== null)
            );
            
            return {
                weightedSum: weightedSum,
                actualWeight: actualWeight,
                hasAllGrades: hasAllGrades
            };
        }

        // חישוב ציון סופי לפי משקולות
        function calculateFinalGrade(student) {
            const studentKey = `${student.lastName}_${student.firstName}`;
            const gender = student.gender;
            
            // מבחנים לפי מגדר עם המשקולות המעודכנות
            const requiredTests = gender === 'boys' ? [
                { id: 'theory', name: 'מבחן עיוני', weight: 0.20 },
                { id: 'running2000', name: 'ריצת 2,000 מטר', weight: 0.20 },
                { id: 'jumprope', name: 'דלגית', weight: 0.15 },
                { id: 'pushups', name: 'שכיבות שמיכה', weight: 0.15 },
                { id: 'pullups', name: 'מתח', weight: 0.15 },
                { id: 'medicineball', name: 'ריצת כדורי כוח', weight: 0.15 }
            ] : [];
            
            let weightedSum = 0;
            let totalPossibleWeight = gender === 'boys' ? 1.00 : 1.00;
            let actualWeight = 0;
            let missingGrades = [];
            let hasAllGrades = true;
            
            if (gender === 'girls') {
                // חישוב מיוחד לבנות
                const girlsResult = calculateGirlsFinalGrade(weightedSum, student);
                weightedSum = girlsResult.weightedSum;
                actualWeight = girlsResult.actualWeight;
                hasAllGrades = girlsResult.hasAllGrades;
                
                // בניית רשימת חסרים
                if (!hasAllGrades) {
                    if (!hasTheoryGrade(studentKey)) missingGrades.push('מבחן עיוני');
                    if (!hasRunningGrade(studentKey)) missingGrades.push('ריצת 2000');
                    if (!hasJumpropeGrade(studentKey)) missingGrades.push('דלגית');
                    if (!hasPlankGrade(studentKey)) missingGrades.push('פלאנק');
                    if (!hasPushupsGrade(studentKey)) missingGrades.push('שכיבות שמיכה');
                    if (!hasPullupsOrLadderGrade(studentKey)) missingGrades.push('מתח/סולם');
                }
            } else {
                // חישוב רגיל לבנים
                for (const test of requiredTests) {
                    let foundGrade = null;
                    
                    // חיפוש הציון במערכת
                    for (const testKey in allTestResults) {
                        if (testKey.includes(test.id) && allTestResults[testKey][studentKey]) {
                            foundGrade = allTestResults[testKey][studentKey].grade;
                            break;
                        }
                    }
                    
                    if (foundGrade !== null) {
                        weightedSum += foundGrade * test.weight;
                        actualWeight += test.weight;
                    } else {
                        missingGrades.push(test.name);
                        hasAllGrades = false;
                    }
                }
            }
            
            // חישוב ציון סופי
            let finalGrade;
            if (actualWeight === 0) {
                finalGrade = 0;
            } else {
                // ציון יחסי לפי מה שיש
                finalGrade = weightedSum * (totalPossibleWeight / actualWeight);
            }
            
            // קביעת סטטוס
            let status = 'none';
            if (actualWeight === 0) {
                status = 'none';
            } else if (hasAllGrades) {
                status = 'full';
            } else if (actualWeight >= 0.5) {
                status = 'partial';
            } else {
                status = 'low';
            }
            
            return {
                final: Math.round(finalGrade * 10) / 10,
                hasAllGrades: hasAllGrades,
                missingGrades: missingGrades,
                actualWeight: actualWeight,
                totalPossibleWeight: totalPossibleWeight,
                status: status
            };
        }

        // פונקציות עזר לבדיקת קיום ציונים
        function hasTheoryGrade(studentKey) {
            for (const testKey in allTestResults) {
                if (testKey.includes('theory_girls') && allTestResults[testKey][studentKey]) {
                    return true;
                }
            }
            return false;
        }

        function hasRunningGrade(studentKey) {
            for (const testKey in allTestResults) {
                if (testKey.includes('running2000_girls') && allTestResults[testKey][studentKey]) {
                    return true;
                }
            }
            return false;
        }

        function hasJumpropeGrade(studentKey) {
            for (const testKey in allTestResults) {
                if (testKey.includes('jumprope_girls') && allTestResults[testKey][studentKey]) {
                    return true;
                }
            }
            return false;
        }

        function hasPlankGrade(studentKey) {
            for (const testKey in allTestResults) {
                if (testKey.includes('plank') && allTestResults[testKey][studentKey]) {
                    return true;
                }
            }
            return false;
        }

        function hasPushupsGrade(studentKey) {
            for (const testKey in allTestResults) {
                if ((testKey.includes('pushups_regular') || testKey.includes('pushups_knees')) && allTestResults[testKey][studentKey]) {
                    return true;
                }
            }
            return false;
        }

        function hasPullupsOrLadderGrade(studentKey) {
            for (const testKey in allTestResults) {
                if ((testKey.includes('pullups_band') || testKey.includes('ladder')) && allTestResults[testKey][studentKey]) {
                    return true;
                }
            }
            return false;
        }

        // פונקציות דירוג שכבה עם סינון
        function showRanking(type, filters = {}) {
            const resultsDiv = document.getElementById('rankingResults');
            if (!resultsDiv) return;
            
            let title = "";
            if (type === 'all') title = "דירוג כל השכבה (בנים ובנות)";
            else if (type === 'boys') title = "דירוג בנים בלבד";
            else title = "דירוג בנות בלבד";
            
            // קבלת כל התלמידים לפי הסוג
            let allStudents = type === 'all' ? allStudentsData : 
                             type === 'boys' ? boysData : girlsData;
            
            // חישוב ציונים סופיים לכל התלמידים
            let studentsWithGrades = [];
            
            allStudents.forEach(student => {
                const finalGrade = calculateFinalGrade(student);
                if (finalGrade.actualWeight > 0) {
                    studentsWithGrades.push({
                        ...student,
                        finalGrade: finalGrade
                    });
                }
            });
            
            // הפעלת סינון אם יש
            let filteredStudents = applyFilters(studentsWithGrades, filters);
            
            // מיון לפי ציון סופי
            filteredStudents.sort((a, b) => b.finalGrade.final - a.finalGrade.final);
            
            // עדכון רשימת התלמידים עבור התרשים
            updateChartStudentList(filteredStudents);
            
            // יצירת תוצאות
            resultsDiv.innerHTML = createRankingHTML(title, filteredStudents);
            
            // עדכון הכותרת בכותרת הדירוג
            const rankingTitle = document.querySelector('#rankingScreen h2');
            if (rankingTitle) {
                rankingTitle.textContent = title;
            }
        }

        // הפעלת סינון על תלמידים
        function applyFilters(students, filters) {
            let filtered = [...students];
            
            // סינון לפי שם
            if (filters.name && filters.name.trim() !== '') {
                const searchLower = filters.name.toLowerCase();
                filtered = filtered.filter(student => 
                    student.firstName.toLowerCase().includes(searchLower) ||
                    student.lastName.toLowerCase().includes(searchLower) ||
                    `${student.firstName} ${student.lastName}`.toLowerCase().includes(searchLower)
                );
            }
            
            // סינון לפי כיתה
            if (filters.class && filters.class !== 'all') {
                filtered = filtered.filter(student => student.class.toString() === filters.class);
            }
            
            // סינון לפי סטטוס
            if (filters.status && filters.status !== 'all') {
                filtered = filtered.filter(student => {
                    if (filters.status === 'full') return student.finalGrade.status === 'full';
                    if (filters.status === 'partial') return student.finalGrade.status === 'partial';
                    if (filters.status === 'low') return student.finalGrade.status === 'low';
                    if (filters.status === 'none') return student.finalGrade.status === 'none';
                    return true;
                });
            }
            
            // סינון לפי מגדר (אם סוג=all)
            if (filters.gender && filters.gender !== 'all') {
                filtered = filtered.filter(student => student.gender === filters.gender);
            }
            
            return filtered;
        }

        // יצירת HTML עבור דירוג
        function createRankingHTML(title, students) {
            console.log("Creating ranking HTML for", students.length, "students");
            
            if (students.length === 0) {
                return `
                    <div class="info-box">
                        <h3><i class="fas fa-exclamation-triangle"></i> ${title}</h3>
                        <p>לא נמצאו תלמידים העומדים בקריטריונים של הסינון.</p>
                        <p>נסה לשנות את פרמטרי הסינון או להזין ציונים עבור תלמידים אלו.</p>
                        <button class="btn btn-primary" onclick="resetFiltersHandler()">
                            <i class="fas fa-redo"></i> אפס סינון
                        </button>
                    </div>
                `;
            }
            
            // אם יש תלמידים, יצירת רשימה
            let searchResults = '';
            const filters = {
                name: document.getElementById('filterName') ? document.getElementById('filterName').value : '',
                class: document.getElementById('filterClass') ? document.getElementById('filterClass').value : 'all'
            };
            
            if (filters.name && filters.name.trim() !== '') {
                searchResults = `<div class="search-results">נמצאו ${students.length} תוצאות עבור "${filters.name}"</div>`;
            }
            
            let html = `
                <div class="info-box">
                    <h3><i class="fas fa-chart-bar"></i> ${title}</h3>
                    <p>סה"כ ${students.length} תלמידים עם ציונים</p>
                    ${searchResults}
                </div>
                
                <div class="student-ranking-list">
                    ${students.map((student, index) => createStudentCardHTML(student, index)).join('')}
                </div>
                
                <div class="info-box" style="margin-top: 20px;">
                    <h4><i class="fas fa-info-circle"></i> הסבר על חישוב הציון הסופי:</h4>
                    <p>הציון הסופי מחושב לפי משקולות המבחנים:</p>
                    <table class="weights-table">
                        <tr>
                            <td><strong>מבחן עיוני:</strong></td>
                            <td>20% מהציון הסופי</td>
                        </tr>
                        <tr>
                            <td><strong>ריצת 2,000 מטר:</strong></td>
                            <td>20% מהציון הסופי</td>
                        </tr>
                        <tr>
                            <td><strong>דלגית:</strong></td>
                            <td>15% מהציון הסופי</td>
                        </tr>
                        <tr>
                            <td><strong>שכיבות שמיכה (ברכיים או מלא):</strong></td>
                            <td>15% מהציון הסופי</td>
                        </tr>
                        <tr>
                            <td><strong>מתח עם גומיה או מעבר סולם:</strong></td>
                            <td>15% מהציון הסופי</td>
                        </tr>
                        <tr>
                            <td><strong>פלאנק:</strong></td>
                            <td>15% מהציון הסופי</td>
                        </tr>
                    </table>
                    <p class="final-grade"><strong>הערה:</strong> תלמידים עם ציונים חסרים מקבלים ציון יחסי למה שיש. הסטטוס "מלא" יופיע רק כאשר יש ציונים בכל 6 המבחנים.</p>
                </div>
            `;
            
            return html;
        }

        // יצירת כרטיס תלמיד
        function createStudentCardHTML(student, index) {
            const statusTexts = {
                'full': 'מלא',
                'partial': 'חלקי',
                'low': 'מועט',
                'none': 'ללא'
            };
            
            const statusClasses = {
                'full': 'excellent',
                'partial': 'good',
                'low': 'average',
                'none': 'poor'
            };
            
            const statusText = statusTexts[student.finalGrade.status] || 'ללא';
            const statusClass = statusClasses[student.finalGrade.status] || 'poor';
            
            // קבלת כל הציונים של התלמיד
            const studentTests = getStudentTests(student);
            
            return `
                <div class="student-card">
                    <div class="student-card-header">
                        <div>
                            <h3 style="margin: 0; display: flex; align-items: center; gap: 10px;">
                                <span class="rank-number">${index + 1}</span>
                                ${index < 3 ? '<i class="fas fa-crown" style="color: gold;"></i>' : ''}
                                <span>${student.lastName} ${student.firstName}</span>
                                <span style="font-size: 0.9rem; color: #666; margin-right: 10px;">יב'${student.class}</span>
                            </h3>
                            <p style="margin: 5px 0 0 0; color: #666;">
                                ${student.gender === 'boys' ? 'בן' : 'בת'} | 
                                <span class="result-badge ${statusClass}">${statusText}</span> | 
                                ${Math.round(student.finalGrade.actualWeight * 100)}% מהציונים
                            </p>
                        </div>
                        <div>
                            <span class="result-badge ${
                                student.finalGrade.final >= 90 ? 'excellent' : 
                                student.finalGrade.final >= 75 ? 'good' : 
                                student.finalGrade.final >= 60 ? 'average' : 'poor'
                            }" style="font-size: 1.2rem;">
                                ${student.finalGrade.final.toFixed(1)}
                            </span>
                            <button class="toggle-chart-btn" onclick="showProgressChart(${student.id})">
                                <i class="fas fa-chart-line"></i> הצג גרף
                            </button>
                        </div>
                    </div>
                    
                    <div class="student-card-body">
                        ${studentTests.map(test => `
                            <div class="student-test-item">
                                <span class="test-name">${test.name}:</span>
                                <span class="test-grade ${test.grade >= 90 ? 'excellent' : test.grade >= 75 ? 'good' : test.grade >= 60 ? 'average' : 'poor'}">
                                    ${test.grade}
                                </span>
                            </div>
                        `).join('')}
                    </div>
                    
                    ${!student.finalGrade.hasAllGrades && student.finalGrade.missingGrades.length > 0 ? `
                    <div style="margin-top: 10px; padding: 10px; background: #fff3cd; border-radius: 4px;">
                        <small><strong>חסרים:</strong> ${student.finalGrade.missingGrades.join(', ')}</small>
                    </div>
                    ` : ''}
                </div>
            `;
        }

        // קבלת כל הציונים של תלמיד
        function getStudentTests(student) {
            const studentKey = `${student.lastName}_${student.firstName}`;
            const tests = [];
            
            // רשימת מבחנים לפי מגדר
            const testTypes = student.gender === 'boys' ? [
                { id: 'theory', name: 'מבחן עיוני' },
                { id: 'running2000', name: 'ריצת 2,000 מטר' },
                { id: 'jumprope', name: 'דלגית' },
                { id: 'pushups', name: 'שכיבות שמיכה' },
                { id: 'pullups', name: 'מתח' },
                { id: 'medicineball', name: 'ריצת כדורי כוח' }
            ] : [
                { id: 'theory_girls', name: 'מבחן עיוני' },
                { id: 'running2000_girls', name: 'ריצת 2,000 מטר' },
                { id: 'jumprope_girls', name: 'דלגית' },
                { id: 'pushups_knees', name: 'שכיבות שמיכה ברכיים' },
                { id: 'pushups_regular', name: 'שכיבות שמיכה רגיל' },
                { id: 'pullups_band', name: 'מתח עם גומיה' },
                { id: 'ladder', name: 'מעבר סולם' },
                { id: 'plank', name: 'פלאנק' }
            ];
            
            // חיפוש ציונים
            testTypes.forEach(testType => {
                let foundGrade = null;
                
                for (const testKey in allTestResults) {
                    if (testKey.includes(testType.id) && allTestResults[testKey][studentKey]) {
                        foundGrade = allTestResults[testKey][studentKey].grade;
                        break;
                    }
                }
                
                // לבנות, אם יש גם ברכיים וגם רגיל, נציג את שניהם? לא, נציג את הגבוה או את הרגיל אם יש
                if (student.gender === 'girls' && testType.id === 'pushups_regular' && foundGrade !== null) {
                    // כבר טופל
                } else if (student.gender === 'girls' && testType.id === 'pushups_knees' && foundGrade !== null) {
                    // לא נוסיף כי כבר יש regular? או שנוסיף?
                    // בוא נוסיף רק אם אין regular
                    let hasRegular = false;
                    for (const testKey in allTestResults) {
                        if (testKey.includes('pushups_regular') && allTestResults[testKey][studentKey]) {
                            hasRegular = true;
                            break;
                        }
                    }
                    if (hasRegular) {
                        return; // לא נוסיף knees כי יש regular
                    }
                }
                
                // לבנות, אם יש גם מתח עם גומיה וגם מעבר סולם, נציג רק את הגבוה
                if (student.gender === 'girls' && testType.id === 'pullups_band' && foundGrade !== null) {
                    // נוסיף
                } else if (student.gender === 'girls' && testType.id === 'ladder' && foundGrade !== null) {
                    // נוסיף רק אם אין pullups_band
                    let hasPullupsBand = false;
                    for (const testKey in allTestResults) {
                        if (testKey.includes('pullups_band') && allTestResults[testKey][studentKey]) {
                            hasPullupsBand = true;
                            break;
                        }
                    }
                    if (hasPullupsBand) {
                        return; // לא נוסיף ladder כי יש pullups_band
                    }
                }
                
                tests.push({
                    name: testType.name,
                    grade: foundGrade !== null ? foundGrade : '--'
                });
            });
            
            return tests;
        }

        // עדכון רשימת התלמידים עבור התרשים
        function updateChartStudentList(students) {
            const selectElement = document.getElementById('chartStudentSelect');
            if (!selectElement) return;
            
            selectElement.innerHTML = '<option value="">בחר תלמיד...</option>';
            
            students.forEach(student => {
                const option = document.createElement('option');
                option.value = student.id;
                option.textContent = `${student.lastName} ${student.firstName} - יב'${student.class}`;
                selectElement.appendChild(option);
            });
        }

        // הצגת תרשים התקדמות
        function showProgressChart(studentId) {
            const student = allStudentsData.find(s => s.id === studentId);
            if (!student) return;
            
            // הצגת חלון התרשים
            const chartContainer = document.getElementById('progressChartContainer');
            chartContainer.style.display = 'block';
            
            // עדכון בחירת התלמיד
            const selectElement = document.getElementById('chartStudentSelect');
            if (selectElement) {
                selectElement.value = studentId;
            }
            
            // יצירת התרשים
            createProgressChart(student);
            
            // גלילה לחלון התרשים
            chartContainer.scrollIntoView({ behavior: 'smooth' });
        }

        // יצירת תרשים התקדמות
        function createProgressChart(student) {
            const canvas = document.getElementById('progressChart');
            if (!canvas) return;
            
            // השמדת תרשים קיים אם יש
            if (currentChart) {
                currentChart.destroy();
            }
            
            // קבלת נתוני התלמיד
            const studentTests = getStudentTests(student);
            const testNames = studentTests.map(test => test.name);
            const testGrades = studentTests.map(test => test.grade === '--' ? 0 : test.grade);
            
            // יצירת התרשים
            const ctx = canvas.getContext('2d');
            const chartType = document.getElementById('chartTypeSelect').value;
            
            currentChart = new Chart(ctx, {
                type: chartType,
                data: {
                    labels: testNames,
                    datasets: [{
                        label: `ציוני ${student.firstName} ${student.lastName}`,
                        data: testGrades,
                        backgroundColor: [
                            'rgba(54, 162, 235, 0.6)',
                            'rgba(75, 192, 192, 0.6)',
                            'rgba(255, 206, 86, 0.6)',
                            'rgba(255, 99, 132, 0.6)',
                            'rgba(153, 102, 255, 0.6)',
                            'rgba(255, 159, 64, 0.6)',
                            'rgba(199, 199, 199, 0.6)',
                            'rgba(83, 102, 255, 0.6)'
                        ],
                        borderColor: [
                            'rgba(54, 162, 235, 1)',
                            'rgba(75, 192, 192, 1)',
                            'rgba(255, 206, 86, 1)',
                            'rgba(255, 99, 132, 1)',
                            'rgba(153, 102, 255, 1)',
                            'rgba(255, 159, 64, 1)',
                            'rgba(199, 199, 199, 1)',
                            'rgba(83, 102, 255, 1)'
                        ],
                        borderWidth: 2
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: chartType === 'radar' ? {} : {
                        y: {
                            beginAtZero: true,
                            max: 100,
                            title: {
                                display: true,
                                text: 'ציון'
                            }
                        },
                        x: {
                            title: {
                                display: true,
                                text: 'מבחנים'
                            }
                        }
                    },
                    plugins: {
                        title: {
                            display: true,
                            text: `התקדמות ${student.firstName} ${student.lastName} - כיתה יב'${student.class}`,
                            font: {
                                size: 16
                            }
                        },
                        legend: {
                            display: chartType !== 'radar'
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return `ציון: ${context.parsed.y || context.raw}`;
                                }
                            }
                        }
                    }
                }
            });
        }

        // בדיקת דוגמת חישוב ציון סופי לבנות
        function testGirlsCalculationExample() {
            console.log("=== בדיקת דוגמת חישוב ציון סופי לבנות ===");
            
            // דוגמת הציונים:
            const exampleGrades = {
                theory: 80,
                running: 82,
                jumprope: 65,
                pushups_regular: 100, // שכיבות שמיכה מלא
                pullups_band: 90, // מתח עם גומיה
                plank: 100
            };
            
            console.log("דוגמת ציונים:");
            console.log("- עיוני: 80 (20%)");
            console.log("- ריצת 2,000: 82 (20%)");
            console.log("- דלגית: 65 (15%)");
            console.log("- שכיבות שמיכה מלא: 100 (15%)");
            console.log("- מתח עם גומיה: 90 (15%)");
            console.log("- פלאנק: 100 (15%)");
            
            // חישוב:
            const total = 
                (80 * 0.20) + 
                (82 * 0.20) + 
                (65 * 0.15) + 
                (100 * 0.15) + 
                (90 * 0.15) + 
                (100 * 0.15);
            
            console.log("\nחישוב:");
            console.log("80 × 0.20 = 16");
            console.log("82 × 0.20 = 16.4");
            console.log("65 × 0.15 = 9.75");
            console.log("100 × 0.15 = 15");
            console.log("90 × 0.15 = 13.5");
            console.log("100 × 0.15 = 15");
            console.log("\nסך הכל: 16 + 16.4 + 9.75 + 15 + 13.5 + 15 =", total);
            console.log("ציון סופי מעוגל:", Math.round(total));
            
            showNotification("דוגמת חישוב נבדקה - ראה קונסול", "info");
        }

        // הגדרת אירועי לחיצה
        function setupEventListeners() {
            // כפתורים במסך הראשי
            document.getElementById('boysBtn').addEventListener('click', () => selectGender('boys'));
            document.getElementById('girlsBtn').addEventListener('click', () => selectGender('girls'));
            document.getElementById('rankingBtn').addEventListener('click', () => {
                showScreen('rankingScreen');
                showRanking('all', {});
            });
            
            // כפתורי חזרה
            document.getElementById('backFromClassBtn').addEventListener('click', () => showScreen('mainScreen'));
            document.getElementById('homeFromClassBtn').addEventListener('click', () => showScreen('mainScreen'));
            
            document.getElementById('backFromTestBtn').addEventListener('click', () => {
                showScreen('classScreen');
                updateClassScreen();
            });
            document.getElementById('homeFromTestBtn').addEventListener('click', () => showScreen('mainScreen'));
            
            document.getElementById('backFromResultsBtn').addEventListener('click', () => {
                showScreen('testScreen');
                updateTestScreen();
            });
            document.getElementById('homeFromResultsBtn').addEventListener('click', () => showScreen('mainScreen'));
            
            document.getElementById('backFromRankingBtn').addEventListener('click', () => showScreen('mainScreen'));
            document.getElementById('homeFromRankingBtn').addEventListener('click', () => showScreen('mainScreen'));
            
            // כפתורי דירוג
            document.getElementById('rankingAllBtn').addEventListener('click', () => {
                showRanking('all', {});
                // עדכון מצב פעיל
                document.querySelectorAll('#rankingScreen .btn-group .btn').forEach(btn => {
                    btn.classList.remove('active');
                });
                document.getElementById('rankingAllBtn').classList.add('active');
            });
            document.getElementById('rankingBoysBtn').addEventListener('click', () => {
                showRanking('boys', {});
                // עדכון מצב פעיל
                document.querySelectorAll('#rankingScreen .btn-group .btn').forEach(btn => {
                    btn.classList.remove('active');
                });
                document.getElementById('rankingBoysBtn').classList.add('active');
            });
            document.getElementById('rankingGirlsBtn').addEventListener('click', () => {
                showRanking('girls', {});
                // עדכון מצב פעיל
                document.querySelectorAll('#rankingScreen .btn-group .btn').forEach(btn => {
                    btn.classList.remove('active');
                });
                document.getElementById('rankingGirlsBtn').classList.add('active');
            });
            
            // סינון מתקדם
            document.getElementById('applyFiltersBtn').addEventListener('click', applyFiltersHandler);
            document.getElementById('resetFiltersBtn').addEventListener('click', resetFiltersHandler);
            document.getElementById('filterName').addEventListener('input', function() {
                const clearBtn = document.getElementById('clearNameBtn');
                clearBtn.style.display = this.value ? 'block' : 'none';
            });
            document.getElementById('clearNameBtn').addEventListener('click', function() {
                document.getElementById('filterName').value = '';
                this.style.display = 'none';
            });
            
            // תרשים התקדמות
            document.getElementById('chartStudentSelect').addEventListener('change', function() {
                if (this.value) {
                    const student = allStudentsData.find(s => s.id === parseInt(this.value));
                    if (student) {
                        createProgressChart(student);
                    }
                }
            });
            
            document.getElementById('chartTypeSelect').addEventListener('change', function() {
                const selectElement = document.getElementById('chartStudentSelect');
                if (selectElement.value) {
                    const student = allStudentsData.find(s => s.id === parseInt(selectElement.value));
                    if (student) {
                        createProgressChart(student);
                    }
                }
            });
            
            document.getElementById('closeChartBtn').addEventListener('click', function() {
                document.getElementById('progressChartContainer').style.display = 'none';
            });
            
            // כפתורי בדיקה
            document.getElementById('debugGirlsBtn').addEventListener('click', debugGirlsData);
            document.getElementById('debugBoysBtn').addEventListener('click', debugBoysData);
            document.getElementById('debugSystemBtn').addEventListener('click', debugSystem);
            document.getElementById('loadTheoryBtn').addEventListener('click', loadTheoryGrades);
            document.getElementById('testPushupsBtn').addEventListener('click', () => {
                console.log("טבלת שכיבות שמיכה נבדקת:");
                console.log("55 שכיבות ->", getScoreFromPushupsTable(55));
                console.log("30 שכיבות ->", getScoreFromPushupsTable(30));
                console.log("15 שכיבות ->", getScoreFromPushupsTable(15));
                showNotification("טבלת שכיבות נבדקה - ראה קונסול", "info");
            });
            document.getElementById('testConversionTablesBtn').addEventListener('click', testConversionTables);
            document.getElementById('testGirlsTableBtn').addEventListener('click', testGirlsTable);
            document.getElementById('testGirlsRunningBtn').addEventListener('click', testGirlsRunningRules);
            document.getElementById('testCalculationBtn').addEventListener('click', testGirlsCalculationExample);
            
            // כפתור שמירה
            document.getElementById('saveResultsBtn').addEventListener('click', saveResults);
        }

        // טיפול בסינון מתקדם
        function applyFiltersHandler() {
            const filters = {
                name: document.getElementById('filterName').value,
                class: document.getElementById('filterClass').value,
                status: document.getElementById('filterStatus').value,
                gender: document.getElementById('filterGender').value
            };
            
            console.log("Applying filters:", filters);
            
            // קביעת סוג הדירוג הנוכחי
            let currentRankingType = 'all';
            if (document.getElementById('rankingBoysBtn').classList.contains('active')) {
                currentRankingType = 'boys';
            } else if (document.getElementById('rankingGirlsBtn').classList.contains('active')) {
                currentRankingType = 'girls';
            }
            
            // אם סינון לפי מגדר מופעל, שנה את סוג הדירוג
            if (filters.gender && filters.gender !== 'all') {
                currentRankingType = filters.gender;
            }
            
            // הסר את הכיתה הפעילה מכל הכפתורים והוסף לכפתור הנוכחי
            document.querySelectorAll('#rankingScreen .btn-group .btn').forEach(btn => {
                btn.classList.remove('active');
            });
            
            if (currentRankingType === 'boys') {
                document.getElementById('rankingBoysBtn').classList.add('active');
            } else if (currentRankingType === 'girls') {
                document.getElementById('rankingGirlsBtn').classList.add('active');
            } else {
                document.getElementById('rankingAllBtn').classList.add('active');
            }
            
            showRanking(currentRankingType, filters);
        }

        // איפוס סינון
        function resetFiltersHandler() {
            document.getElementById('filterName').value = '';
            document.getElementById('filterClass').value = 'all';
            document.getElementById('filterStatus').value = 'all';
            document.getElementById('filterGender').value = 'all';
            document.getElementById('clearNameBtn').style.display = 'none';
            
            // קביעת סוג הדירוג הנוכחי
            let currentRankingType = 'all';
            if (document.getElementById('rankingBoysBtn').classList.contains('active')) {
                currentRankingType = 'boys';
            } else if (document.getElementById('rankingGirlsBtn').classList.contains('active')) {
                currentRankingType = 'girls';
            }
            
            // עדכון מצב פעיל
            document.querySelectorAll('#rankingScreen .btn-group .btn').forEach(btn => {
                btn.classList.remove('active');
            });
            
            if (currentRankingType === 'boys') {
                document.getElementById('rankingBoysBtn').classList.add('active');
            } else if (currentRankingType === 'girls') {
                document.getElementById('rankingGirlsBtn').classList.add('active');
            } else {
                document.getElementById('rankingAllBtn').classList.add('active');
            }
            
            showRanking(currentRankingType, {});
        }

        // אתחול המערכת
        function initSystem() {
            // עדכון ספירת תלמידים
            updateTotalCount();
            
            // הגדרת אירועים
            setupEventListeners();
            
            // טעינת ציוני מבחן עיוני אוטומטית
            loadTheoryGrades();
            
            console.log('System initialized with', allStudentsData.length, 'students');
            console.log('Conversion tables loaded:');
            console.log('- Medicine Ball:', medicineBallTable.length, 'entries');
            console.log('- Running 2000m:', running2000Table.length, 'entries');
            console.log('- Jump Rope:', jumpRopeTable.length, 'entries');
            console.log('- Pullups:', pullupsTable.length, 'entries');
            console.log('- Pushups:', pushupsTable.length, 'entries');
            console.log('- Girls Table:', girlsConversionTable.length, 'entries');
            
            showNotification(`מערכת מוכנה: ${girlsData.length} תלמידות ו-${boysData.length} תלמידים`, 'success');
        }

        // הפעלת המערכת
        document.addEventListener('DOMContentLoaded', initSystem);
    </script>
</body>
</html>

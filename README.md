<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نُـبــل - منشئ اختبارات ذكي</title>
    
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* Reset */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        :root {
            /* Navy Dark Theme */
            --primary: #0a192f;
            --secondary: #112240;
            --accent: #64ffda;
            --accent-light: #8892b0;
            --text-primary: #e6f1ff;
            --text-secondary: #a8b2d1;
            --success: #00d26a;
            --warning: #ffb347;
            --danger: #ff6b6b;
            --gold: #FFD700;
            --border: #233554;
            --radius: 10px;
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            --transition: all 0.3s ease;
        }
        
        body {
            font-family: 'Segoe UI', 'Cairo', sans-serif;
            background: var(--primary);
            color: var(--text-primary);
            line-height: 1.6;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        /* Header */
        .header {
            background: var(--secondary);
            padding: 20px;
            border-radius: var(--radius);
            margin-bottom: 30px;
            text-align: center;
            border: 1px solid var(--border);
        }
        
        .logo-text {
            position: relative;
            display: inline-block;
        }
        
        .noble-text {
            font-size: 42px;
            font-weight: 700;
            color: var(--accent);
            font-family: 'Arial', sans-serif;
            letter-spacing: 2px;
        }
        
        .damma {
            position: absolute;
            top: -5px;
            right: 60%;
            color: var(--gold);
            font-size: 20px;
            font-weight: bold;
        }
        
        .logo-subtitle {
            color: var(--text-secondary);
            font-size: 16px;
            margin-top: 10px;
        }
        
        /* Main Content Grid */
        .main-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }
        
        @media (max-width: 1024px) {
            .main-grid {
                grid-template-columns: 1fr;
            }
        }
        
        /* Cards */
        .card {
            background: var(--secondary);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 25px;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.4);
        }
        
        .card-title {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid var(--border);
        }
        
        .card-title i {
            color: var(--accent);
            font-size: 20px;
        }
        
        .card-title h3 {
            font-size: 18px;
            font-weight: 600;
        }
        
        /* License Section */
        .license-input {
            width: 100%;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            color: var(--text-primary);
            font-size: 16px;
            margin-bottom: 15px;
            transition: var(--transition);
        }
        
        .license-input:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 3px rgba(100, 255, 218, 0.1);
        }
        
        .btn {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            padding: 15px 25px;
            border: none;
            border-radius: var(--radius);
            font-size: 16px;
            font-weight: 500;
            cursor: pointer;
            transition: var(--transition);
            width: 100%;
        }
        
        .btn-primary {
            background: linear-gradient(135deg, var(--accent), #4db8ff);
            color: var(--primary);
        }
        
        .btn-primary:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(100, 255, 218, 0.3);
        }
        
        .btn-secondary {
            background: rgba(255, 255, 255, 0.05);
            color: var(--text-primary);
            border: 1px solid var(--border);
        }
        
        .btn-success {
            background: var(--success);
            color: white;
        }
        
        .btn-danger {
            background: var(--danger);
            color: white;
        }
        
        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
            transform: none !important;
        }
        
        /* Alert */
        .alert {
            padding: 15px;
            border-radius: var(--radius);
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 12px;
        }
        
        .alert-success {
            background: rgba(0, 210, 106, 0.1);
            border: 1px solid rgba(0, 210, 106, 0.2);
            color: var(--success);
        }
        
        .alert-error {
            background: rgba(255, 107, 107, 0.1);
            border: 1px solid rgba(255, 107, 107, 0.2);
            color: var(--danger);
        }
        
        .alert-warning {
            background: rgba(255, 179, 71, 0.1);
            border: 1px solid rgba(255, 179, 71, 0.2);
            color: var(--warning);
        }
        
        .alert-info {
            background: rgba(100, 255, 218, 0.1);
            border: 1px solid rgba(100, 255, 218, 0.2);
            color: var(--accent);
        }
        
        /* Tabs */
        .tabs {
            display: flex;
            background: rgba(255, 255, 255, 0.05);
            border-radius: var(--radius);
            padding: 5px;
            margin-bottom: 20px;
        }
        
        .tab {
            flex: 1;
            padding: 12px;
            text-align: center;
            color: var(--text-secondary);
            border-radius: calc(var(--radius) - 2px);
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        
        .tab.active {
            background: var(--primary);
            color: var(--accent);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }
        
        /* Input Groups */
        .input-group {
            margin-bottom: 20px;
        }
        
        .input-label {
            display: block;
            margin-bottom: 8px;
            color: var(--text-secondary);
            font-size: 14px;
            font-weight: 500;
        }
        
        .input-field {
            width: 100%;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            color: var(--text-primary);
            font-size: 16px;
            transition: var(--transition);
        }
        
        .input-field:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 3px rgba(100, 255, 218, 0.1);
        }
        
        /* Question Types */
        .question-types {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
            margin-bottom: 20px;
        }
        
        @media (max-width: 768px) {
            .question-types {
                grid-template-columns: 1fr;
            }
        }
        
        .type-checkbox {
            position: relative;
        }
        
        .type-checkbox input {
            position: absolute;
            opacity: 0;
            cursor: pointer;
        }
        
        .type-label {
            display: flex;
            align-items: center;
            gap: 15px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.03);
            border: 2px solid var(--border);
            border-radius: var(--radius);
            cursor: pointer;
            transition: var(--transition);
            height: 100%;
        }
        
        .type-label:hover {
            border-color: var(--accent);
            transform: translateY(-3px);
        }
        
        .type-checkbox input:checked + .type-label {
            background: rgba(100, 255, 218, 0.1);
            border-color: var(--accent);
        }
        
        .checkmark {
            width: 24px;
            height: 24px;
            border: 2px solid var(--text-secondary);
            border-radius: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
            flex-shrink: 0;
        }
        
        .type-checkbox input:checked + .type-label .checkmark {
            background: var(--accent);
            border-color: var(--accent);
        }
        
        .checkmark i {
            color: var(--primary);
            font-size: 14px;
            opacity: 0;
            transition: var(--transition);
        }
        
        .type-checkbox input:checked + .type-label .checkmark i {
            opacity: 1;
        }
        
        .type-icon {
            font-size: 24px;
            color: var(--accent);
        }
        
        .type-content {
            flex: 1;
        }
        
        .type-name {
            font-weight: 600;
            margin-bottom: 5px;
            color: var(--text-primary);
        }
        
        .type-desc {
            font-size: 13px;
            color: var(--text-secondary);
            line-height: 1.4;
        }
        
        /* Question Count Dropdown */
        .count-selector {
            position: relative;
        }
        
        .select-wrapper {
            position: relative;
        }
        
        .select-wrapper::after {
            content: '\f078';
            font-family: 'Font Awesome 6 Free';
            font-weight: 900;
            position: absolute;
            left: 20px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--text-secondary);
            pointer-events: none;
        }
        
        .count-select {
            width: 100%;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            color: var(--text-primary);
            font-size: 16px;
            cursor: pointer;
            appearance: none;
            -webkit-appearance: none;
            -moz-appearance: none;
        }
        
        .count-select:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 3px rgba(100, 255, 218, 0.1);
        }
        
        /* File Preview */
        .file-preview {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 20px;
            margin-top: 20px;
        }
        
        .file-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .file-icon {
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, var(--accent), #4db8ff);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary);
            font-size: 20px;
        }
        
        .file-details {
            flex: 1;
        }
        
        .file-name {
            font-weight: 600;
            margin-bottom: 5px;
            color: var(--text-primary);
        }
        
        .file-size {
            font-size: 14px;
            color: var(--text-secondary);
        }
        
        /* Progress Bar */
        .progress-container {
            margin: 20px 0;
        }
        
        .progress-bar {
            height: 8px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 4px;
            overflow: hidden;
            margin-bottom: 10px;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--accent), #4db8ff);
            border-radius: 4px;
            transition: width 0.5s ease;
            width: 0%;
        }
        
        .progress-text {
            text-align: center;
            color: var(--text-secondary);
            font-size: 14px;
        }
        
        /* Questions Section */
        .questions-container {
            margin-top: 40px;
        }
        
        .question-card {
            background: var(--secondary);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: var(--shadow);
        }
        
        .question-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid var(--border);
        }
        
        .question-number {
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: 600;
            color: var(--accent);
        }
        
        .question-type-badge {
            padding: 6px 15px;
            background: rgba(100, 255, 218, 0.1);
            border-radius: 20px;
            font-size: 13px;
            font-weight: 500;
            color: var(--accent);
        }
        
        .question-text {
            font-size: 18px;
            line-height: 1.7;
            margin-bottom: 25px;
            color: var(--text-primary);
        }
        
        /* Options */
        .options-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 12px;
            margin-bottom: 20px;
        }
        
        .option {
            background: rgba(255, 255, 255, 0.03);
            border: 2px solid var(--border);
            border-radius: var(--radius);
            padding: 18px;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .option:hover:not(.disabled) {
            border-color: var(--accent);
            transform: translateX(5px);
        }
        
        .option.selected {
            background: rgba(100, 255, 218, 0.1);
            border-color: var(--accent);
        }
        
        .option.correct {
            background: rgba(0, 210, 106, 0.1);
            border-color: var(--success);
        }
        
        .option.incorrect {
            background: rgba(255, 107, 107, 0.1);
            border-color: var(--danger);
        }
        
        .option.disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }
        
        .option-letter {
            width: 35px;
            height: 35px;
            background: var(--primary);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
            flex-shrink: 0;
            color: var(--text-primary);
        }
        
        .option.selected .option-letter,
        .option.correct .option-letter {
            background: var(--accent);
            color: var(--primary);
        }
        
        .option.incorrect .option-letter {
            background: var(--danger);
            color: white;
        }
        
        .option-text {
            flex: 1;
            font-size: 16px;
            color: var(--text-primary);
        }
        
        /* Feedback */
        .feedback {
            margin-top: 25px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.03);
            border-radius: var(--radius);
        }
        
        .feedback-title {
            font-weight: 600;
            margin-bottom: 12px;
            color: var(--accent);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .feedback-content {
            color: var(--text-secondary);
            line-height: 1.6;
        }
        
        /* Score Card */
        .score-card {
            background: linear-gradient(135deg, var(--accent), #4db8ff);
            color: var(--primary);
            padding: 40px;
            border-radius: var(--radius);
            text-align: center;
            margin: 40px 0;
        }
        
        .score-value {
            font-size: 48px;
            font-weight: 700;
            margin: 15px 0;
        }
        
        .score-message {
            font-size: 18px;
            opacity: 0.9;
        }
        
        /* Loading Screen */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(10, 25, 47, 0.95);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 2000;
        }
        
        .loading-content {
            text-align: center;
            max-width: 500px;
            padding: 40px;
            background: var(--secondary);
            border-radius: var(--radius);
            border: 1px solid var(--border);
        }
        
        .loading-spinner {
            width: 60px;
            height: 60px;
            border: 4px solid rgba(100, 255, 218, 0.1);
            border-top-color: var(--accent);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 0 auto 30px;
        }
        
        .loading-title {
            font-size: 24px;
            font-weight: 600;
            margin-bottom: 15px;
            color: var(--accent);
        }
        
        .loading-text {
            color: var(--text-secondary);
            margin-bottom: 25px;
            line-height: 1.6;
        }
        
        .countdown {
            font-size: 36px;
            font-weight: 700;
            color: var(--accent);
            margin: 20px 0;
        }
        
        /* Pagination */
        .pagination {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin: 30px 0;
        }
        
        .page-btn {
            width: 40px;
            height: 40px;
            border-radius: 8px;
            background: var(--secondary);
            border: 1px solid var(--border);
            color: var(--text-primary);
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .page-btn.active {
            background: var(--accent);
            color: var(--primary);
            border-color: var(--accent);
        }
        
        .page-btn:hover:not(.active) {
            background: rgba(100, 255, 218, 0.1);
            border-color: var(--accent);
        }
        
        /* Animations */
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        
        /* Utilities */
        .hidden {
            display: none !important;
        }
        
        .mb-4 { margin-bottom: 20px; }
        .mt-4 { margin-top: 20px; }
        
        /* RTL/LTR Support */
        body[dir="ltr"] .select-wrapper::after {
            left: auto;
            right: 20px;
        }
        
        body[dir="ltr"] .option:hover:not(.disabled) {
            transform: translateX(-5px);
        }
    </style>
</head>
<body dir="rtl">
    <div class="container">
        <!-- Header -->
        <div class="header">
            <div class="logo-text">
                <h1 class="noble-text">
                    نُـبــل
                    <span class="damma">ـُـ</span>
                </h1>
                <div class="logo-subtitle">منشئ اختبارات ذكي بتقنية الذكاء الاصطناعي</div>
            </div>
        </div>

        <!-- Main Grid -->
        <div class="main-grid">
            <!-- Left Column -->
            <div>
                <!-- License Card -->
                <div class="card mb-4">
                    <div class="card-title">
                        <i class="fas fa-key"></i>
                        <h3>مفتاح الترخيص</h3>
                    </div>
                    
                    <div class="input-group">
                        <label class="input-label">أدخل مفتاح الترخيص</label>
                        <input type="text" 
                               id="licenseInput" 
                               class="input-field" 
                               placeholder="أدخل مفتاح الترخيص هنا..."
                               autocomplete="off">
                    </div>
                    
                    <button id="activateBtn" class="btn btn-primary mt-4">
                        <i class="fas fa-check-circle"></i>
                        تفعيل المفتاح
                    </button>
                </div>

                <!-- Mode Selection -->
                <div class="card mb-4">
                    <div class="card-title">
                        <i class="fas fa-magic"></i>
                        <h3>طريقة التوليد</h3>
                    </div>
                    
                    <div class="tabs">
                        <div class="tab active" id="tabManual">
                            <i class="fas fa-keyboard"></i>
                            موضوع يدوي
                        </div>
                        <div class="tab" id="tabFile">
                            <i class="fas fa-file-upload"></i>
                            من ملف
                        </div>
                    </div>
                    
                    <!-- Manual Content -->
                    <div id="manualContent">
                        <div class="input-group">
                            <label class="input-label">الموضوع</label>
                            <input type="text" 
                                   id="topicInput" 
                                   class="input-field" 
                                   placeholder="أدخل موضوع الأسئلة (مثل: علوم الحاسب، التاريخ، الرياضيات...)">
                        </div>
                    </div>
                    
                    <!-- File Content -->
                    <div id="fileContent" class="hidden">
                        <div class="input-group">
                            <label class="input-label">اختر ملف</label>
                            <input type="file" 
                                   id="fileInput" 
                                   accept=".pdf,.png,.jpg,.jpeg,.doc,.docx" 
                                   class="input-field"
                                   style="padding: 12px; cursor: pointer;">
                        </div>
                        
                        <div id="filePreview" class="file-preview hidden">
                            <div class="file-info">
                                <div class="file-icon">
                                    <i class="fas fa-file-pdf"></i>
                                </div>
                                <div class="file-details">
                                    <div id="fileName" class="file-name"></div>
                                    <div id="fileSize" class="file-size"></div>
                                </div>
                                <button id="removeFileBtn" class="btn btn-secondary" style="padding: 8px 16px;">
                                    <i class="fas fa-times"></i>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Question Types -->
                <div class="card mb-4">
                    <div class="card-title">
                        <i class="fas fa-list-check"></i>
                        <h3>أنواع الأسئلة</h3>
                    </div>
                    
                    <div class="question-types">
                        <!-- Multiple Choice -->
                        <label class="type-checkbox">
                            <input type="checkbox" id="typeMultiple" checked>
                            <div class="type-label">
                                <div class="type-icon">
                                    <i class="fas fa-list-ul"></i>
                                </div>
                                <div class="type-content">
                                    <div class="type-name">اختيار متعدد</div>
                                    <div class="type-desc">أسئلة باختيارات متعددة مع إجابة واحدة صحيحة</div>
                                </div>
                                <div class="checkmark">
                                    <i class="fas fa-check"></i>
                                </div>
                            </div>
                        </label>
                        
                        <!-- True/False -->
                        <label class="type-checkbox">
                            <input type="checkbox" id="typeTrueFalse">
                            <div class="type-label">
                                <div class="type-icon">
                                    <i class="fas fa-check-double"></i>
                                </div>
                                <div class="type-content">
                                    <div class="type-name">صح/خطأ</div>
                                    <div class="type-desc">أسئلة تقييم العبارات بصحة أو خطأ</div>
                                </div>
                                <div class="checkmark">
                                    <i class="fas fa-check"></i>
                                </div>
                            </div>
                        </label>
                        
                        <!-- Fill in the Blank -->
                        <label class="type-checkbox">
                            <input type="checkbox" id="typeFillBlank">
                            <div class="type-label">
                                <div class="type-icon">
                                    <i class="fas fa-edit"></i>
                                </div>
                                <div class="type-content">
                                    <div class="type-name">أكمل الفراغ</div>
                                    <div class="type-desc">أسئلة إكمال النص الناقص بكلمات مناسبة</div>
                                </div>
                                <div class="checkmark">
                                    <i class="fas fa-check"></i>
                                </div>
                            </div>
                        </label>
                    </div>
                </div>
            </div>

            <!-- Right Column -->
            <div>
                <!-- Question Count -->
                <div class="card mb-4">
                    <div class="card-title">
                        <i class="fas fa-hashtag"></i>
                        <h3>عدد الأسئلة</h3>
                    </div>
                    
                    <div class="count-selector">
                        <div class="select-wrapper">
                            <select id="questionCount" class="count-select">
                                <option value="5">5 أسئلة</option>
                                <option value="10">10 أسئلة</option>
                                <option value="15">15 أسئلة</option>
                                <option value="20">20 أسئلة</option>
                                <option value="25">25 أسئلة</option>
                                <option value="30">30 أسئلة</option>
                                <option value="40">40 أسئلة</option>
                                <option value="50">50 أسئلة</option>
                            </select>
                        </div>
                    </div>
                </div>

                <!-- Action Buttons -->
                <div class="card mb-4">
                    <button id="generateBtn" class="btn btn-primary mb-4" disabled>
                        <i class="fas fa-bolt"></i>
                        توليد الأسئلة
                    </button>
                    
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px;">
                        <button id="checkAllBtn" class="btn btn-success" disabled>
                            <i class="fas fa-check-double"></i>
                            التحقق الكامل
                        </button>
                        <button id="resetBtn" class="btn btn-danger" disabled>
                            <i class="fas fa-redo"></i>
                            إعادة تعيين
                        </button>
                    </div>
                </div>

                <!-- Alerts Container -->
                <div id="alertContainer"></div>

                <!-- Score Card -->
                <div id="scoreContainer" class="score-card hidden">
                    <div style="font-size: 20px;">نتيجة الاختبار</div>
                    <div id="scoreValue" class="score-value">0/0</div>
                    <div id="scoreMessage" class="score-message"></div>
                </div>
            </div>
        </div>

        <!-- Pagination -->
        <div id="pagination" class="pagination hidden"></div>

        <!-- Questions Output -->
        <div id="questionsOutput" class="questions-container"></div>
    </div>

    <!-- Loading Screen -->
    <div id="loadingScreen" class="loading-screen hidden">
        <div class="loading-content">
            <div class="loading-spinner"></div>
            <div class="loading-title">جارٍ توليد الأسئلة...</div>
            <div class="loading-text">الرجاء الانتظار، جارٍ معالجة طلبك وتوليد الأسئلة باستخدام الذكاء الاصطناعي.</div>
            <div class="countdown" id="countdown">30</div>
            <div class="loading-text">ثواني متبقية</div>
        </div>
    </div>

    <script>
        // API Configuration
        const API_BASE = "https://batching-project.onrender.com";
        const API_MANUAL = API_BASE + "/generate/batch";
        const API_IMAGE = API_BASE + "/generate/from-image";
        const API_PDF = API_BASE + "/generate/from-file";

        // Application State
        const state = {
            licenseKey: null,
            language: 'ar',
            mode: 'manual',
            questionTypes: {
                multiple_choice: true,
                true_false: false,
                fill_blank: false
            },
            questionCount: 5,
            questions: [],
            userAnswers: {},
            answeredCount: 0,
            score: { correct: 0, total: 0 },
            deviceId: localStorage.getItem('deviceId') || 'device-' + Math.random().toString(36).substr(2, 9),
            currentPage: 1,
            questionsPerPage: 5
        };

        // DOM Elements
        const elements = {
            // License
            licenseInput: document.getElementById('licenseInput'),
            activateBtn: document.getElementById('activateBtn'),
            
            // Mode
            tabManual: document.getElementById('tabManual'),
            tabFile: document.getElementById('tabFile'),
            manualContent: document.getElementById('manualContent'),
            fileContent: document.getElementById('fileContent'),
            topicInput: document.getElementById('topicInput'),
            fileInput: document.getElementById('fileInput'),
            filePreview: document.getElementById('filePreview'),
            fileName: document.getElementById('fileName'),
            fileSize: document.getElementById('fileSize'),
            removeFileBtn: document.getElementById('removeFileBtn'),
            
            // Question Types
            typeMultiple: document.getElementById('typeMultiple'),
            typeTrueFalse: document.getElementById('typeTrueFalse'),
            typeFillBlank: document.getElementById('typeFillBlank'),
            
            // Question Count
            questionCount: document.getElementById('questionCount'),
            
            // Buttons
            generateBtn: document.getElementById('generateBtn'),
            checkAllBtn: document.getElementById('checkAllBtn'),
            resetBtn: document.getElementById('resetBtn'),
            
            // Containers
            alertContainer: document.getElementById('alertContainer'),
            scoreContainer: document.getElementById('scoreContainer'),
            scoreValue: document.getElementById('scoreValue'),
            scoreMessage: document.getElementById('scoreMessage'),
            questionsOutput: document.getElementById('questionsOutput'),
            
            // Loading Screen
            loadingScreen: document.getElementById('loadingScreen'),
            countdown: document.getElementById('countdown'),
            
            // Pagination
            pagination: document.getElementById('pagination')
        };

        // Initialize Application
        function init() {
            // Setup event listeners
            setupEventListeners();
            
            // Update UI
            updateUI();
            
            // Save device ID
            if (!localStorage.getItem('deviceId')) {
                localStorage.setItem('deviceId', state.deviceId);
            }
        }

        // Setup Event Listeners
        function setupEventListeners() {
            // License
            elements.activateBtn.addEventListener('click', activateLicense);
            elements.licenseInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') activateLicense();
            });
            
            // Mode tabs
            elements.tabManual.addEventListener('click', () => setMode('manual'));
            elements.tabFile.addEventListener('click', () => setMode('file'));
            
            // File handling
            elements.fileInput.addEventListener('change', handleFileSelect);
            elements.removeFileBtn.addEventListener('click', () => {
                elements.fileInput.value = '';
                elements.filePreview.classList.add('hidden');
            });
            
            // Question types
            elements.typeMultiple.addEventListener('change', updateQuestionTypes);
            elements.typeTrueFalse.addEventListener('change', updateQuestionTypes);
            elements.typeFillBlank.addEventListener('change', updateQuestionTypes);
            
            // Question count
            elements.questionCount.addEventListener('change', () => {
                state.questionCount = parseInt(elements.questionCount.value);
            });
            
            // Action buttons
            elements.generateBtn.addEventListener('click', generateQuestions);
            elements.checkAllBtn.addEventListener('click', checkAllAnswers);
            elements.resetBtn.addEventListener('click', resetQuestions);
        }

        // Update UI
        function updateUI() {
            const hasLicense = !!state.licenseKey;
            
            // Update buttons
            elements.generateBtn.disabled = !hasLicense;
            elements.checkAllBtn.disabled = state.questions.length === 0;
            elements.resetBtn.disabled = state.questions.length === 0;
            
            // Update mode
            if (state.mode === 'manual') {
                elements.tabManual.classList.add('active');
                elements.tabFile.classList.remove('active');
                elements.manualContent.classList.remove('hidden');
                elements.fileContent.classList.add('hidden');
            } else {
                elements.tabManual.classList.remove('active');
                elements.tabFile.classList.add('active');
                elements.manualContent.classList.add('hidden');
                elements.fileContent.classList.remove('hidden');
            }
        }

        // Set Mode
        function setMode(mode) {
            state.mode = mode;
            updateUI();
        }

        // Update Question Types
        function updateQuestionTypes() {
            state.questionTypes = {
                multiple_choice: elements.typeMultiple.checked,
                true_false: elements.typeTrueFalse.checked,
                fill_blank: elements.typeFillBlank.checked
            };
        }

        // Activate License
        async function activateLicense() {
            const key = elements.licenseInput.value.trim();
            if (!key) {
                showAlert('أدخل مفتاح الترخيص', 'error');
                return;
            }
            
            showAlert('جارٍ التحقق من الرخصة...', 'info');
            
            try {
                // Test license with a simple request
                const response = await fetch(API_MANUAL, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'license-key': key,
                        'device-id': state.deviceId
                    },
                    body: JSON.stringify({
                        topic: 'اختبار الترخيص',
                        total_questions: 1,
                        question_types: { multiple_choice: true }
                    })
                });
                
                if (!response.ok) {
                    const error = await response.text();
                    throw new Error('الرخصة غير صالحة');
                }
                
                // Save license
                state.licenseKey = key;
                
                // Update UI
                elements.activateBtn.textContent = "تم التفعيل";
                elements.activateBtn.disabled = true;
                elements.licenseInput.disabled = true;
                
                showAlert('تم تفعيل الرخصة بنجاح', 'success');
                updateUI();
                
            } catch (error) {
                showAlert('فشل تفعيل الرخصة: ' + error.message, 'error');
            }
        }

        // Handle File Select
        function handleFileSelect(event) {
            const file = event.target.files[0];
            if (!file) return;
            
            const isImage = file.type.startsWith('image/');
            const isPDF = file.type === 'application/pdf' || file.name.toLowerCase().endsWith('.pdf');
            
            if (!isImage && !isPDF) {
                showAlert('الملف غير مدعوم. يرجى اختيار صورة أو PDF', 'error');
                elements.fileInput.value = '';
                return;
            }
            
            // Update file preview
            elements.fileName.textContent = file.name;
            elements.fileSize.textContent = formatFileSize(file.size);
            elements.filePreview.classList.remove('hidden');
        }

        // Generate Questions
        async function generateQuestions() {
            // Validate license
            if (!state.licenseKey) {
                showAlert('يجب تفعيل الرخصة أولاً', 'error');
                return;
            }
            
            // Validate question types
            const hasTypes = Object.values(state.questionTypes).some(v => v);
            if (!hasTypes) {
                showAlert('اختر نوع سؤال واحد على الأقل', 'error');
                return;
            }
            
            // Validate inputs based on mode
            if (state.mode === 'manual') {
                const topic = elements.topicInput.value.trim();
                if (!topic) {
                    showAlert('أدخل موضوع الأسئلة', 'error');
                    return;
                }
            } else {
                if (!elements.fileInput.files[0]) {
                    showAlert('اختر ملفاً أولاً', 'error');
                    return;
                }
            }
            
            // Clear previous results
            clearResults();
            
            // Show loading screen
            showLoadingScreen();
            
            // Start countdown
            startCountdown();
            
            try {
                let apiUrl, body, headers;
                
                if (state.mode === 'manual') {
                    apiUrl = API_MANUAL;
                    body = JSON.stringify({
                        topic: elements.topicInput.value.trim(),
                        total_questions: state.questionCount,
                        question_types: state.questionTypes
                    });
                    headers = {
                        'Content-Type': 'application/json',
                        'license-key': state.licenseKey,
                        'device-id': state.deviceId
                    };
                } else {
                    const file = elements.fileInput.files[0];
                    const isPDF = file.type === 'application/pdf' || file.name.toLowerCase().endsWith('.pdf');
                    apiUrl = isPDF ? API_PDF : API_IMAGE;
                    
                    const formData = new FormData();
                    formData.append('file', file);
                    formData.append('total_questions', state.questionCount.toString());
                    formData.append('multiple_choice', state.questionTypes.multiple_choice.toString());
                    formData.append('true_false', state.questionTypes.true_false.toString());
                    formData.append('fill_blank', state.questionTypes.fill_blank.toString());
                    
                    body = formData;
                    headers = {
                        'license-key': state.licenseKey,
                        'device-id': state.deviceId
                    };
                }
                
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: headers,
                    body: body
                });
                
                if (!response.ok) {
                    const errorData = await response.json().catch(() => ({}));
                    throw new Error(errorData.detail || 'فشل في توليد الأسئلة');
                }
                
                const data = await response.json();
                
                if (!data.questions || data.questions.length === 0) {
                    throw new Error('لم يتم توليد أي أسئلة');
                }
                
                // Save questions
                state.questions = data.questions;
                state.score.total = state.questions.length;
                
                // Hide loading screen
                hideLoadingScreen();
                
                showAlert(`تم توليد ${state.questions.length} سؤالاً بنجاح`, 'success');
                
                // Render questions with pagination
                renderQuestionsWithPagination();
                
                // Update UI
                updateUI();
                
            } catch (error) {
                // Hide loading screen
                hideLoadingScreen();
                showAlert('حدث خطأ: ' + error.message, 'error');
            }
        }

        // Show Loading Screen
        function showLoadingScreen() {
            elements.loadingScreen.classList.remove('hidden');
        }

        // Hide Loading Screen
        function hideLoadingScreen() {
            elements.loadingScreen.classList.add('hidden');
        }

        // Start Countdown
        function startCountdown() {
            let seconds = 30;
            elements.countdown.textContent = seconds;
            
            const countdownInterval = setInterval(() => {
                seconds--;
                elements.countdown.textContent = seconds;
                
                if (seconds <= 0) {
                    clearInterval(countdownInterval);
                }
            }, 1000);
        }

        // Render Questions with Pagination
        function renderQuestionsWithPagination() {
            elements.questionsOutput.innerHTML = '';
            elements.pagination.innerHTML = '';
            
            // Calculate total pages
            const totalPages = Math.ceil(state.questions.length / state.questionsPerPage);
            
            // Create pagination buttons
            for (let i = 1; i <= totalPages; i++) {
                const pageBtn = document.createElement('button');
                pageBtn.className = `page-btn ${i === state.currentPage ? 'active' : ''}`;
                pageBtn.textContent = i;
                pageBtn.addEventListener('click', () => {
                    state.currentPage = i;
                    renderCurrentPage();
                    updatePaginationButtons();
                });
                elements.pagination.appendChild(pageBtn);
            }
            
            elements.pagination.classList.remove('hidden');
            
            // Render first page
            renderCurrentPage();
        }

        // Render Current Page
        function renderCurrentPage() {
            elements.questionsOutput.innerHTML = '';
            
            // Calculate start and end indices
            const startIndex = (state.currentPage - 1) * state.questionsPerPage;
            const endIndex = Math.min(startIndex + state.questionsPerPage, state.questions.length);
            
            // Render questions for current page
            for (let i = startIndex; i < endIndex; i++) {
                const question = state.questions[i];
                const questionCard = createQuestionCard(question, i);
                elements.questionsOutput.appendChild(questionCard);
            }
        }

        // Update Pagination Buttons
        function updatePaginationButtons() {
            const pageButtons = elements.pagination.querySelectorAll('.page-btn');
            pageButtons.forEach((btn, index) => {
                if (index + 1 === state.currentPage) {
                    btn.classList.add('active');
                } else {
                    btn.classList.remove('active');
                }
            });
        }

        // Create Question Card
        function createQuestionCard(question, index) {
            const card = document.createElement('div');
            card.className = 'question-card';
            card.dataset.index = index;
            
            // Header
            const header = document.createElement('div');
            header.className = 'question-header';
            
            const number = document.createElement('div');
            number.className = 'question-number';
            number.innerHTML = `<i class="fas fa-question-circle"></i> سؤال ${index + 1}`;
            
            const typeBadge = document.createElement('div');
            typeBadge.className = 'question-type-badge';
            
            switch(question.type) {
                case 'multiple_choice':
                    typeBadge.textContent = 'اختيار متعدد';
                    break;
                case 'true_false':
                    typeBadge.textContent = 'صح/خطأ';
                    break;
                case 'fill_blank':
                    typeBadge.textContent = 'أكمل الفراغ';
                    break;
                default:
                    typeBadge.textContent = question.type;
            }
            
            header.appendChild(number);
            header.appendChild(typeBadge);
            
            // Question Text
            const text = document.createElement('div');
            text.className = 'question-text';
            text.innerHTML = question.q;
            
            card.appendChild(header);
            card.appendChild(text);
            
            // Options based on question type
            if (question.type === 'multiple_choice') {
                const options = createMultipleChoiceOptions(question, index);
                card.appendChild(options);
            } else if (question.type === 'true_false') {
                const options = createTrueFalseOptions(question, index);
                card.appendChild(options);
            } else if (question.type === 'fill_blank') {
                const input = createFillBlankInput(question, index);
                card.appendChild(input);
            }
            
            return card;
        }

        // Create Multiple Choice Options
        function createMultipleChoiceOptions(question, index) {
            const container = document.createElement('div');
            container.className = 'options-grid';
            
            question.options.forEach((option, optionIndex) => {
                const optionElement = document.createElement('div');
                optionElement.className = 'option';
                optionElement.dataset.optionIndex = optionIndex;
                
                const letter = document.createElement('div');
                letter.className = 'option-letter';
                letter.textContent = String.fromCharCode(1632 + optionIndex + 1);
                
                const text = document.createElement('div');
                text.className = 'option-text';
                text.textContent = option;
                
                optionElement.appendChild(letter);
                optionElement.appendChild(text);
                
                optionElement.addEventListener('click', () => {
                    if (optionElement.classList.contains('disabled')) return;
                    selectAnswer(index, optionIndex, question);
                });
                
                container.appendChild(optionElement);
            });
            
            return container;
        }

        // Create True/False Options
        function createTrueFalseOptions(question, index) {
            const container = document.createElement('div');
            container.className = 'options-grid';
            
            const trueOption = document.createElement('div');
            trueOption.className = 'option';
            trueOption.dataset.answer = 'true';
            
            const falseOption = document.createElement('div');
            falseOption.className = 'option';
            falseOption.dataset.answer = 'false';
            
            // True option
            const trueLetter = document.createElement('div');
            trueLetter.className = 'option-letter';
            trueLetter.innerHTML = '<i class="fas fa-check"></i>';
            
            const trueText = document.createElement('div');
            trueText.className = 'option-text';
            trueText.textContent = 'صح';
            
            trueOption.appendChild(trueLetter);
            trueOption.appendChild(trueText);
            
            // False option
            const falseLetter = document.createElement('div');
            falseLetter.className = 'option-letter';
            falseLetter.innerHTML = '<i class="fas fa-times"></i>';
            
            const falseText = document.createElement('div');
            falseText.className = 'option-text';
            falseText.textContent = 'خطأ';
            
            falseOption.appendChild(falseLetter);
            falseOption.appendChild(falseText);
            
            // Event listeners
            [trueOption, falseOption].forEach(option => {
                option.addEventListener('click', () => {
                    if (option.classList.contains('disabled')) return;
                    const answer = option.dataset.answer === 'true';
                    selectAnswer(index, answer, question);
                });
            });
            
            container.appendChild(trueOption);
            container.appendChild(falseOption);
            
            return container;
        }

        // Create Fill in the Blank Input
        function createFillBlankInput(question, index) {
            const container = document.createElement('div');
            container.style.display = 'flex';
            container.style.gap = '15px';
            container.style.alignItems = 'center';
            
            const input = document.createElement('input');
            input.type = 'text';
            input.className = 'input-field';
            input.placeholder = 'اكتب الإجابة هنا...';
            input.style.flex = '1';
            
            const button = document.createElement('button');
            button.className = 'btn btn-primary';
            button.style.width = 'auto';
            button.style.padding = '12px 20px';
            button.innerHTML = '<i class="fas fa-check"></i> تأكيد';
            
            button.addEventListener('click', () => {
                const answer = input.value.trim();
                if (!answer) {
                    showAlert('أدخل إجابة أولاً', 'error');
                    return;
                }
                
                selectAnswer(index, answer, question);
                input.disabled = true;
                button.disabled = true;
                button.innerHTML = '<i class="fas fa-check-circle"></i> تم';
            });
            
            container.appendChild(input);
            container.appendChild(button);
            
            return container;
        }

        // Select Answer
        function selectAnswer(questionIndex, answer, question) {
            // Save answer
            state.userAnswers[questionIndex] = answer;
            state.answeredCount++;
            
            // Get question card
            const questionCard = document.querySelector(`.question-card[data-index="${questionIndex}"]`);
            const options = questionCard.querySelectorAll('.option');
            
            // Disable all options
            options.forEach(opt => {
                opt.classList.add('disabled');
            });
            
            // Check answer
            const isCorrect = checkAnswer(answer, question.answer);
            
            // Mark correct/incorrect answers
            if (question.type === 'multiple_choice') {
                options.forEach((opt, idx) => {
                    if (idx === question.answer) {
                        opt.classList.add('correct');
                    } else if (idx === answer) {
                        opt.classList.add('incorrect');
                    }
                });
            } else if (question.type === 'true_false') {
                options.forEach(opt => {
                    const isTrue = opt.dataset.answer === 'true';
                    if (isTrue === question.answer) {
                        opt.classList.add('correct');
                    } else if (isTrue === answer) {
                        opt.classList.add('incorrect');
                    }
                });
            }
            
            // Add feedback
            addFeedback(questionCard, isCorrect, question.correct_explanation);
            
            // Check if all questions answered
            if (state.answeredCount === state.questions.length) {
                showAlert('تمت الإجابة على جميع الأسئلة!', 'success');
                showResults();
            }
        }

        // Check Answer
        function checkAnswer(userAnswer, correctAnswer) {
            if (Array.isArray(userAnswer) && Array.isArray(correctAnswer)) {
                return JSON.stringify(userAnswer.sort()) === JSON.stringify(correctAnswer.sort());
            }
            return userAnswer === correctAnswer;
        }

        // Add Feedback
        function addFeedback(questionCard, isCorrect, explanation) {
            const feedback = document.createElement('div');
            feedback.className = 'feedback';
            
            const title = document.createElement('div');
            title.className = 'feedback-title';
            title.innerHTML = isCorrect 
                ? '<i class="fas fa-check-circle"></i> إجابة صحيحة!'
                : '<i class="fas fa-times-circle"></i> إجابة خاطئة';
            
            const content = document.createElement('div');
            content.className = 'feedback-content';
            content.textContent = explanation || 'تفسير مفصل للإجابة الصحيحة';
            
            feedback.appendChild(title);
            feedback.appendChild(content);
            questionCard.appendChild(feedback);
        }

        // Show Results (only after all questions are answered)
        function showResults() {
            // Calculate score
            let correct = 0;
            state.questions.forEach((question, index) => {
                if (state.userAnswers[index] !== undefined) {
                    if (checkAnswer(state.userAnswers[index], question.answer)) {
                        correct++;
                    }
                }
            });
            
            state.score.correct = correct;
            
            // Update score display
            const percentage = (correct / state.questions.length) * 100;
            elements.scoreValue.textContent = `${correct}/${state.questions.length}`;
            
            let message = '';
            if (percentage >= 90) message = 'ممتاز! أداء رائع 👏';
            else if (percentage >= 70) message = 'جيد جداً! 👍';
            else if (percentage >= 50) message = 'مقبول، يمكنك التحسن 💪';
            else message = 'حاول مرة أخرى 📚';
            
            elements.scoreMessage.textContent = message;
            elements.scoreContainer.classList.remove('hidden');
            
            // Scroll to results
            elements.scoreContainer.scrollIntoView({ behavior: 'smooth' });
        }

        // Check All Answers
        function checkAllAnswers() {
            const unanswered = state.questions.length - state.answeredCount;
            
            if (unanswered > 0) {
                showAlert(`يوجد ${unanswered} سؤال لم يتم الإجابة عليه`, 'warning');
                
                // Highlight unanswered questions
                state.questions.forEach((_, index) => {
                    if (!state.userAnswers[index]) {
                        const card = document.querySelector(`.question-card[data-index="${index}"]`);
                        if (card) {
                            card.style.animation = 'none';
                            card.scrollIntoView({ behavior: 'smooth', block: 'center' });
                        }
                    }
                });
            } else {
                showAlert('تمت الإجابة على جميع الأسئلة', 'success');
                showResults();
            }
        }

        // Reset Questions
        function resetQuestions() {
            if (!confirm('هل تريد إعادة تعيين جميع الأسئلة والإجابات؟')) return;
            
            state.userAnswers = {};
            state.answeredCount = 0;
            state.score.correct = 0;
            
            // Reset UI
            document.querySelectorAll('.question-card').forEach(card => {
                // Reset options
                card.querySelectorAll('.option').forEach(opt => {
                    opt.classList.remove('selected', 'correct', 'incorrect', 'disabled');
                });
                
                // Reset input fields
                const input = card.querySelector('input');
                if (input) {
                    input.value = '';
                    input.disabled = false;
                }
                
                // Reset buttons
                const button = card.querySelector('button');
                if (button) {
                    button.disabled = false;
                    button.innerHTML = '<i class="fas fa-check"></i> تأكيد';
                }
                
                // Remove feedback
                const feedback = card.querySelector('.feedback');
                if (feedback) {
                    feedback.remove();
                }
            });
            
            // Reset score
            elements.scoreContainer.classList.add('hidden');
            showAlert('تم إعادة تعيين جميع الأسئلة', 'success');
        }

        // Clear Results
        function clearResults() {
            elements.questionsOutput.innerHTML = '';
            elements.scoreContainer.classList.add('hidden');
            elements.pagination.classList.add('hidden');
            state.questions = [];
            state.userAnswers = {};
            state.answeredCount = 0;
            state.score.correct = 0;
            state.currentPage = 1;
        }

        // Show Alert
        function showAlert(message, type) {
            const alert = document.createElement('div');
            alert.className = `alert alert-${type}`;
            alert.innerHTML = `
                <i class="fas fa-${getAlertIcon(type)}"></i>
                <div>${message}</div>
            `;
            
            elements.alertContainer.innerHTML = '';
            elements.alertContainer.appendChild(alert);
            
            // Remove alert after 5 seconds
            setTimeout(() => {
                alert.remove();
            }, 5000);
        }

        // Get Alert Icon
        function getAlertIcon(type) {
            switch(type) {
                case 'success': return 'check-circle';
                case 'error': return 'times-circle';
                case 'warning': return 'exclamation-triangle';
                case 'info': return 'info-circle';
                default: return 'info-circle';
            }
        }

        // Format File Size
        function formatFileSize(bytes) {
            if (bytes === 0) return '0 بايت';
            const k = 1024;
            const sizes = ['بايت', 'كيلوبايت', 'ميجابايت', 'جيجابايت'];
            const i = Math.floor(Math.log(bytes) / Math.log(k));
            return parseFloat((bytes / Math.pow(k, i)).toFixed(2)) + ' ' + sizes[i];
        }

        // Initialize on load
        document.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>
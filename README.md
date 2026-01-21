<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>نُـبــل - منشئ اختبارات ذكي</title>
    
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* Reset */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
            -webkit-text-size-adjust: none;
        }
        
        html {
            height: 100%;
            overflow-x: hidden;
        }
        
        body {
            font-family: 'Segoe UI', 'Cairo', -apple-system, BlinkMacSystemFont, sans-serif;
            background: #0a192f;
            color: #e6f1ff;
            line-height: 1.6;
            min-height: 100vh;
            padding: 0;
            margin: 0;
            overflow-x: hidden;
            position: relative;
            transition: all 0.3s ease;
        }
        
        /* Language Toggle */
        .language-toggle {
            position: absolute;
            top: 15px;
            left: 20px;
            z-index: 1001;
        }
        
        .language-btn {
            padding: 8px 15px;
            background: rgba(100, 255, 218, 0.1);
            border: 2px solid #64ffda;
            border-radius: 20px;
            color: #64ffda;
            font-weight: 600;
            font-size: 14px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .language-btn:hover {
            background: #64ffda;
            color: #0a192f;
            transform: translateY(-2px);
        }
        
        /* Top Bar */
        .top-bar {
            background: linear-gradient(135deg, #112240 0%, #0a192f 100%);
            padding: 15px 20px;
            border-bottom: 3px solid #64ffda;
            position: relative;
            overflow: hidden;
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
            border-radius: 0 0 30px 30px;
        }
        
        .top-bar::before {
            content: '';
            position: absolute;
            top: 0;
            left: -50%;
            width: 200%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(100, 255, 218, 0.1), transparent);
            transform: rotate(-5deg);
        }
        
        .top-buttons {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
            position: relative;
            z-index: 2;
        }
        
        .top-btn {
            padding: 12px 25px;
            background: rgba(100, 255, 218, 0.1);
            border: 2px solid #64ffda;
            border-radius: 50px;
            color: #64ffda;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: 600;
            font-size: 15px;
            transition: all 0.3s ease;
            white-space: nowrap;
            box-shadow: 0 4px 15px rgba(100, 255, 218, 0.2);
            cursor: pointer;
            border: none;
            outline: none;
        }
        
        .top-btn:hover {
            background: #64ffda;
            color: #0a192f;
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(100, 255, 218, 0.4);
        }
        
        .top-btn.whatsapp {
            background: linear-gradient(135deg, #25D366, #128C7E);
            border-color: #25D366;
            color: white;
        }
        
        .top-btn.whatsapp:hover {
            background: linear-gradient(135deg, #128C7E, #25D366);
            transform: translateY(-3px);
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            padding-top: 30px;
        }
        
        /* Header */
        .header {
            background: #112240;
            padding: 25px;
            border-radius: 20px;
            margin-bottom: 30px;
            text-align: center;
            border: 1px solid #233554;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
        }
        
        .logo-text {
            position: relative;
            display: inline-block;
        }
        
        .noble-text {
            font-size: 42px;
            font-weight: 700;
            color: #64ffda;
            font-family: 'Arial', sans-serif;
            letter-spacing: 2px;
        }
        
        .damma {
            position: absolute;
            top: -5px;
            right: 60%;
            color: #FFD700;
            font-size: 20px;
            font-weight: bold;
        }
        
        .logo-subtitle {
            color: #a8b2d1;
            font-size: 16px;
            margin-top: 10px;
        }
        
        /* Main Content Grid */
        .main-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
            margin-bottom: 30px;
        }
        
        /* Questions Page */
        .questions-page {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .questions-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 2px solid #64ffda;
        }
        
        .back-to-main {
            padding: 10px 20px;
            background: rgba(100, 255, 218, 0.1);
            border: 2px solid #64ffda;
            border-radius: 10px;
            color: #64ffda;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .back-to-main:hover {
            background: #64ffda;
            color: #0a192f;
            transform: translateX(-5px);
        }
        
        @media (max-width: 1024px) {
            .main-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .container {
                padding: 15px;
            }
            
            .top-bar {
                padding: 12px 15px;
                border-radius: 0 0 20px 20px;
            }
            
            .top-buttons {
                gap: 10px;
            }
            
            .top-btn {
                padding: 10px 20px;
                font-size: 14px;
            }
            
            .language-toggle {
                position: relative;
                top: 0;
                left: 0;
                margin-bottom: 15px;
            }
        }
        
        @media (max-width: 768px) {
            .noble-text {
                font-size: 36px;
            }
            
            .main-grid {
                gap: 15px;
            }
            
            .header {
                padding: 20px;
                margin-bottom: 20px;
            }
            
            .questions-header {
                flex-direction: column;
                gap: 15px;
                text-align: center;
            }
        }
        
        @media (max-width: 480px) {
            .noble-text {
                font-size: 32px;
            }
            
            .top-buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .top-btn {
                width: 100%;
                max-width: 300px;
                justify-content: center;
            }
            
            .container {
                padding: 10px;
            }
        }
        
        /* Cards */
        .card {
            background: #112240;
            border: 1px solid #233554;
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
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
            border-bottom: 1px solid #233554;
        }
        
        .card-title i {
            color: #64ffda;
            font-size: 20px;
        }
        
        .card-title h3 {
            font-size: 18px;
            font-weight: 600;
        }
        
        /* License Section */
        .license-input {
            width: 100%;
            padding: 16px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid #233554;
            border-radius: 10px;
            color: #e6f1ff;
            font-size: 16px;
            margin-bottom: 15px;
            transition: all 0.3s ease;
        }
        
        .license-input:focus {
            outline: none;
            border-color: #64ffda;
            box-shadow: 0 0 0 3px rgba(100, 255, 218, 0.1);
        }
        
        .license-alerts {
            margin-top: 15px;
            min-height: 40px;
        }
        
        .alert {
            padding: 12px 15px;
            border-radius: 8px;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 14px;
            animation: fadeIn 0.3s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .alert-success {
            background: rgba(0, 210, 106, 0.1);
            border: 1px solid rgba(0, 210, 106, 0.2);
            color: #00d26a;
        }
        
        .alert-error {
            background: rgba(255, 107, 107, 0.1);
            border: 1px solid rgba(255, 107, 107, 0.2);
            color: #ff6b6b;
        }
        
        .alert-warning {
            background: rgba(255, 179, 71, 0.1);
            border: 1px solid rgba(255, 179, 71, 0.2);
            color: #ffb347;
        }
        
        .alert-info {
            background: rgba(100, 255, 218, 0.1);
            border: 1px solid rgba(100, 255, 218, 0.2);
            color: #64ffda;
        }
        
        .btn {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            padding: 16px 25px;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
        }
        
        .btn-primary {
            background: linear-gradient(135deg, #64ffda, #4db8ff);
            color: #0a192f;
        }
        
        .btn-primary:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(100, 255, 218, 0.3);
        }
        
        .btn-secondary {
            background: rgba(255, 255, 255, 0.05);
            color: #e6f1ff;
            border: 1px solid #233554;
        }
        
        .btn-success {
            background: #00d26a;
            color: white;
        }
        
        .btn-danger {
            background: #ff6b6b;
            color: white;
        }
        
        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
            transform: none !important;
        }
        
        /* Tabs */
        .tabs {
            display: flex;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            padding: 5px;
            margin-bottom: 20px;
        }
        
        .tab {
            flex: 1;
            padding: 12px;
            text-align: center;
            color: #a8b2d1;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        
        .tab.active {
            background: #0a192f;
            color: #64ffda;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }
        
        /* Input Groups */
        .input-group {
            margin-bottom: 20px;
        }
        
        .input-label {
            display: block;
            margin-bottom: 8px;
            color: #a8b2d1;
            font-size: 14px;
            font-weight: 500;
        }
        
        .input-field {
            width: 100%;
            padding: 16px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid #233554;
            border-radius: 10px;
            color: #e6f1ff;
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        .input-field:focus {
            outline: none;
            border-color: #64ffda;
            box-shadow: 0 0 0 3px rgba(100, 255, 218, 0.1);
        }
        
        /* Question Types */
        .question-types {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
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
            gap: 12px;
            padding: 18px;
            background: rgba(255, 255, 255, 0.03);
            border: 2px solid #233554;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            height: 100%;
        }
        
        .type-label:hover {
            border-color: #64ffda;
            transform: translateY(-3px);
        }
        
        .type-checkbox input:checked + .type-label {
            background: rgba(100, 255, 218, 0.1);
            border-color: #64ffda;
        }
        
        .checkmark {
            width: 22px;
            height: 22px;
            border: 2px solid #a8b2d1;
            border-radius: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            flex-shrink: 0;
        }
        
        .type-checkbox input:checked + .type-label .checkmark {
            background: #64ffda;
            border-color: #64ffda;
        }
        
        .checkmark i {
            color: #0a192f;
            font-size: 12px;
            opacity: 0;
            transition: all 0.3s ease;
        }
        
        .type-checkbox input:checked + .type-label .checkmark i {
            opacity: 1;
        }
        
        .type-icon {
            font-size: 22px;
            color: #64ffda;
        }
        
        .type-content {
            flex: 1;
        }
        
        .type-name {
            font-weight: 600;
            margin-bottom: 4px;
            color: #e6f1ff;
        }
        
        .type-desc {
            font-size: 12px;
            color: #a8b2d1;
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
            color: #a8b2d1;
            pointer-events: none;
        }
        
        .count-select {
            width: 100%;
            padding: 16px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid #233554;
            border-radius: 10px;
            color: #e6f1ff;
            font-size: 16px;
            cursor: pointer;
            appearance: none;
            -webkit-appearance: none;
            -moz-appearance: none;
        }
        
        .count-select:focus {
            outline: none;
            border-color: #64ffda;
            box-shadow: 0 0 0 3px rgba(100, 255, 218, 0.1);
        }
        
        /* File Preview */
        .file-preview {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid #233554;
            border-radius: 10px;
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
            background: linear-gradient(135deg, #64ffda, #4db8ff);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #0a192f;
            font-size: 20px;
        }
        
        .file-details {
            flex: 1;
        }
        
        .file-name {
            font-weight: 600;
            margin-bottom: 5px;
            color: #e6f1ff;
        }
        
        .file-size {
            font-size: 14px;
            color: #a8b2d1;
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
            background: #112240;
            border-radius: 15px;
            border: 1px solid #233554;
            margin: 20px;
        }
        
        .loading-spinner {
            width: 60px;
            height: 60px;
            border: 4px solid rgba(100, 255, 218, 0.1);
            border-top-color: #64ffda;
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 0 auto 30px;
        }
        
        .loading-title {
            font-size: 24px;
            font-weight: 600;
            margin-bottom: 15px;
            color: #64ffda;
        }
        
        .loading-text {
            color: #a8b2d1;
            margin-bottom: 25px;
            line-height: 1.6;
        }
        
        .countdown {
            font-size: 36px;
            font-weight: 700;
            color: #64ffda;
            margin: 20px 0;
        }
        
        /* Pagination */
        .pagination {
            display: flex;
            justify-content: center;
            gap: 8px;
            margin: 30px 0;
            flex-wrap: wrap;
        }
        
        .page-btn {
            width: 40px;
            height: 40px;
            border-radius: 8px;
            background: #112240;
            border: 1px solid #233554;
            color: #e6f1ff;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
        }
        
        .page-btn.active {
            background: #64ffda;
            color: #0a192f;
            border-color: #64ffda;
        }
        
        .page-btn:hover:not(.active) {
            background: rgba(100, 255, 218, 0.1);
            border-color: #64ffda;
        }
        
        /* Questions Section */
        .questions-container {
            margin-top: 40px;
        }
        
        .question-card {
            background: #112240;
            border: 1px solid #233554;
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }
        
        .question-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid #233554;
        }
        
        .question-number {
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: 600;
            color: #64ffda;
        }
        
        .question-type-badge {
            padding: 6px 15px;
            background: rgba(100, 255, 218, 0.1);
            border-radius: 20px;
            font-size: 13px;
            font-weight: 500;
            color: #64ffda;
        }
        
        .question-text {
            font-size: 18px;
            line-height: 1.7;
            margin-bottom: 25px;
            color: #e6f1ff;
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
            border: 2px solid #233554;
            border-radius: 10px;
            padding: 18px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .option:hover:not(.disabled) {
            border-color: #64ffda;
            transform: translateX(5px);
        }
        
        .option.selected {
            background: rgba(100, 255, 218, 0.1);
            border-color: #64ffda;
        }
        
        .option.correct {
            background: rgba(0, 210, 106, 0.1);
            border-color: #00d26a;
        }
        
        .option.incorrect {
            background: rgba(255, 107, 107, 0.1);
            border-color: #ff6b6b;
        }
        
        .option.disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }
        
        .option-letter {
            width: 35px;
            height: 35px;
            background: #0a192f;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
            flex-shrink: 0;
            color: #e6f1ff;
        }
        
        .option.selected .option-letter,
        .option.correct .option-letter {
            background: #64ffda;
            color: #0a192f;
        }
        
        .option.incorrect .option-letter {
            background: #ff6b6b;
            color: white;
        }
        
        .option-text {
            flex: 1;
            font-size: 16px;
            color: #e6f1ff;
        }
        
        /* Feedback */
        .feedback {
            margin-top: 25px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.03);
            border-radius: 10px;
        }
        
        .feedback-title {
            font-weight: 600;
            margin-bottom: 12px;
            color: #64ffda;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .feedback-content {
            color: #a8b2d1;
            line-height: 1.6;
        }
        
        /* Wrong Options Explanation Button */
        .explain-wrong-btn {
            margin-top: 15px;
            padding: 10px 20px;
            background: rgba(255, 107, 107, 0.1);
            border: 1px solid rgba(255, 107, 107, 0.3);
            border-radius: 8px;
            color: #ff6b6b;
            cursor: pointer;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            font-size: 14px;
        }
        
        .explain-wrong-btn:hover {
            background: rgba(255, 107, 107, 0.2);
            transform: translateY(-2px);
        }
        
        .wrong-explanation {
            margin-top: 15px;
            padding: 15px;
            background: rgba(255, 107, 107, 0.05);
            border-radius: 8px;
            border-right: 3px solid #ff6b6b;
            color: #a8b2d1;
            display: none;
            animation: fadeIn 0.3s ease;
        }
        
        .wrong-explanation.show {
            display: block;
        }
        
        /* Score Card */
        .score-card {
            background: linear-gradient(135deg, #64ffda, #4db8ff);
            color: #0a192f;
            padding: 40px;
            border-radius: 15px;
            text-align: center;
            margin: 40px 0;
            box-shadow: 0 10px 30px rgba(100, 255, 218, 0.3);
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
        
        /* User Guide Modal */
        .guide-modal {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(10, 25, 47, 0.95);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 3000;
            padding: 20px;
        }
        
        .guide-content {
            background: #112240;
            border-radius: 20px;
            padding: 40px;
            max-width: 800px;
            width: 100%;
            max-height: 80vh;
            overflow-y: auto;
            border: 2px solid #64ffda;
            box-shadow: 0 15px 50px rgba(0, 0, 0, 0.5);
        }
        
        .guide-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 1px solid #233554;
        }
        
        .guide-title {
            font-size: 28px;
            font-weight: 700;
            color: #64ffda;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .close-guide {
            background: transparent;
            border: none;
            color: #a8b2d1;
            font-size: 24px;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 8px;
        }
        
        .close-guide:hover {
            background: rgba(255, 107, 107, 0.1);
            color: #ff6b6b;
        }
        
        /* Animations */
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        
        /* Utilities */
        .hidden {
            display: none !important;
        }
        
        .show {
            display: block !important;
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
        
        body[dir="ltr"] .back-to-main:hover {
            transform: translateX(5px);
        }
        
        /* Disable zoom on mobile */
        @media (max-width: 768px) {
            body {
                touch-action: pan-x pan-y;
            }
            
            input, select, textarea {
                font-size: 16px !important;
            }
        }
    </style>
</head>
<body dir="rtl">
    <!-- Language Toggle -->
    <div class="language-toggle">
        <button id="languageBtn" class="language-btn">
            <i class="fas fa-language"></i>
            <span id="languageText">English</span>
        </button>
    </div>

    <!-- Top Bar -->
    <div class="top-bar">
        <div class="top-buttons">
            <button id="whatsappBtn" class="top-btn whatsapp">
                <i class="fab fa-whatsapp"></i>
                <span id="whatsappText">للاشتراك والحصول على كود التفعيل</span>
            </button>
            <button id="guideBtn" class="top-btn">
                <i class="fas fa-book"></i>
                <span id="guideText">دليل الاستخدام</span>
            </button>
        </div>
    </div>

    <!-- User Guide Modal -->
    <div id="guideModal" class="guide-modal hidden">
        <div class="guide-content">
            <div class="guide-header">
                <h2 class="guide-title">
                    <i class="fas fa-graduation-cap"></i>
                    <span id="guideTitleText">دليل الاستخدام - نُـبــل</span>
                </h2>
                <button id="closeGuideBtn" class="close-guide">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="guide-steps" id="guideSteps">
                <!-- Steps will be dynamically loaded based on language -->
            </div>
        </div>
    </div>

    <!-- Main Page -->
    <div id="mainPage" class="container">
        <!-- Header -->
        <div class="header">
            <div class="logo-text">
                <h1 class="noble-text">
                    <span id="nobleText">نُـبــل</span>
                    <span class="damma">ـُـ</span>
                </h1>
                <div class="logo-subtitle" id="subtitleText">منشئ اختبارات ذكي بتقنية الذكاء الاصطناعي</div>
            </div>
        </div>

        <!-- Test Language Selector -->
        <div class="card mb-4">
            <div class="card-title">
                <i class="fas fa-globe"></i>
                <h3 id="testLanguageTitle">لغة الاختبار</h3>
            </div>
            
            <div class="input-group">
                <label class="input-label" id="testLanguageLabel">اختر لغة الأسئلة المراد توليدها</label>
                <div class="select-wrapper">
                    <select id="testLanguage" class="count-select">
                        <option value="ar">العربية</option>
                        <option value="en">English</option>
                    </select>
                </div>
            </div>
        </div>

        <!-- Main Grid -->
        <div class="main-grid">
            <!-- Left Column -->
            <div>
                <!-- Activation Code Card -->
                <div class="card mb-4">
                    <div class="card-title">
                        <i class="fas fa-key"></i>
                        <h3 id="activationTitle">كود التفعيل</h3>
                    </div>
                    
                    <div class="input-group">
                        <label class="input-label" id="licenseLabel">أدخل كود التفعيل</label>
                        <input type="text" 
                               id="licenseInput" 
                               class="license-input" 
                               placeholder="أدخل كود التفعيل هنا..."
                               autocomplete="off">
                    </div>
                    
                    <button id="activateBtn" class="btn btn-primary mt-4">
                        <i class="fas fa-check-circle"></i>
                        <span id="activateBtnText">تفعيل الكود</span>
                    </button>
                    
                    <div id="licenseAlerts" class="license-alerts"></div>
                </div>

                <!-- Mode Selection -->
                <div class="card mb-4">
                    <div class="card-title">
                        <i class="fas fa-magic"></i>
                        <h3 id="generationMethodTitle">طريقة التوليد</h3>
                    </div>
                    
                    <div class="tabs">
                        <div class="tab active" id="tabManual">
                            <i class="fas fa-keyboard"></i>
                            <span id="manualTabText">موضوع يدوي</span>
                        </div>
                        <div class="tab" id="tabFile">
                            <i class="fas fa-file-upload"></i>
                            <span id="fileTabText">من ملف</span>
                        </div>
                    </div>
                    
                    <!-- Manual Content -->
                    <div id="manualContent">
                        <div class="input-group">
                            <label class="input-label" id="topicLabel">الموضوع</label>
                            <input type="text" 
                                   id="topicInput" 
                                   class="input-field" 
                                   placeholder="أدخل موضوع الأسئلة (مثل: علوم الحاسب، التاريخ، الرياضيات...)">
                        </div>
                    </div>
                    
                    <!-- File Content -->
                    <div id="fileContent" class="hidden">
                        <div class="input-group">
                            <label class="input-label" id="fileLabel">اختر ملف</label>
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
                        <h3 id="questionTypesTitle">أنواع الأسئلة</h3>
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
                                    <div class="type-name" id="multipleChoiceText">اختيار متعدد</div>
                                    <div class="type-desc" id="multipleChoiceDesc">أسئلة باختيارات متعددة مع إجابة واحدة صحيحة</div>
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
                                    <div class="type-name" id="trueFalseText">صح/خطأ</div>
                                    <div class="type-desc" id="trueFalseDesc">أسئلة تقييم العبارات بصحة أو خطأ</div>
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
                                    <div class="type-name" id="fillBlankText">أكمل الفراغ</div>
                                    <div class="type-desc" id="fillBlankDesc">أسئلة إكمال النص الناقص بكلمات مناسبة</div>
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
                        <h3 id="questionCountTitle">عدد الأسئلة</h3>
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
                        <span id="generateBtnText">توليد الأسئلة</span>
                    </button>
                    
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px;">
                        <button id="checkAllBtn" class="btn btn-success" disabled>
                            <i class="fas fa-check-double"></i>
                            <span id="checkAllBtnText">التحقق الكامل</span>
                        </button>
                        <button id="resetBtn" class="btn btn-danger" disabled>
                            <i class="fas fa-redo"></i>
                            <span id="resetBtnText">إعادة تعيين</span>
                        </button>
                    </div>
                </div>

                <!-- Alerts Container -->
                <div id="alertContainer"></div>

                <!-- Score Card -->
                <div id="scoreContainer" class="score-card hidden">
                    <div style="font-size: 20px;" id="testResultText">نتيجة الاختبار</div>
                    <div id="scoreValue" class="score-value">0/0</div>
                    <div id="scoreMessage" class="score-message"></div>
                </div>
            </div>
        </div>
    </div>

    <!-- Questions Page -->
    <div id="questionsPage" class="questions-page container">
        <div class="questions-header">
            <a href="#" id="backToMain" class="back-to-main">
                <i class="fas fa-arrow-right"></i>
                <span id="backToMainText">العودة للصفحة الرئيسية</span>
            </a>
            <h2 id="questionsPageTitle">الأسئلة</h2>
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
            <div class="loading-title" id="loadingTitle">جارٍ توليد الأسئلة...</div>
            <div class="loading-text" id="loadingText">الرجاء الانتظار، جارٍ معالجة طلبك وتوليد الأسئلة باستخدام الذكاء الاصطناعي.</div>
            <div class="countdown" id="countdown">30</div>
            <div class="loading-text" id="countdownText">ثواني متبقية</div>
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
            language: 'ar', // UI language
            testLanguage: 'ar', // Test content language
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

        // Translations
        const translations = {
            ar: {
                // UI Texts
                whatsappText: "للاشتراك والحصول على كود التفعيل",
                guideText: "دليل الاستخدام",
                languageText: "English",
                nobleText: "نُـبــل",
                subtitleText: "منشئ اختبارات ذكي بتقنية الذكاء الاصطناعي",
                
                // Main Page
                testLanguageTitle: "لغة الاختبار",
                testLanguageLabel: "اختر لغة الأسئلة المراد توليدها",
                activationTitle: "كود التفعيل",
                licenseLabel: "أدخل كود التفعيل",
                activateBtnText: "تفعيل الكود",
                generationMethodTitle: "طريقة التوليد",
                manualTabText: "موضوع يدوي",
                fileTabText: "من ملف",
                topicLabel: "الموضوع",
                topicPlaceholder: "أدخل موضوع الأسئلة (مثل: علوم الحاسب، التاريخ، الرياضيات...)",
                fileLabel: "اختر ملف",
                questionTypesTitle: "أنواع الأسئلة",
                multipleChoiceText: "اختيار متعدد",
                multipleChoiceDesc: "أسئلة باختيارات متعددة مع إجابة واحدة صحيحة",
                trueFalseText: "صح/خطأ",
                trueFalseDesc: "أسئلة تقييم العبارات بصحة أو خطأ",
                fillBlankText: "أكمل الفراغ",
                fillBlankDesc: "أسئلة إكمال النص الناقص بكلمات مناسبة",
                questionCountTitle: "عدد الأسئلة",
                generateBtnText: "توليد الأسئلة",
                checkAllBtnText: "التحقق الكامل",
                resetBtnText: "إعادة تعيين",
                
                // Questions Page
                backToMainText: "العودة للصفحة الرئيسية",
                questionsPageTitle: "الأسئلة",
                
                // Loading
                loadingTitle: "جارٍ توليد الأسئلة...",
                loadingText: "الرجاء الانتظار، جارٍ معالجة طلبك وتوليد الأسئلة باستخدام الذكاء الاصطناعي.",
                countdownText: "ثواني متبقية",
                
                // Alerts
                enterLicense: "أدخل كود التفعيل",
                verifyingLicense: "جارٍ التحقق من كود التفعيل...",
                licenseSuccess: "تم تفعيل الكود بنجاح",
                licenseFailed: "فشل تفعيل الكود: ",
                selectQuestionType: "اختر نوع سؤال واحد على الأقل",
                enterTopic: "أدخل موضوع الأسئلة",
                selectFile: "اختر ملفاً أولاً",
                generatingQuestions: "جارٍ توليد الأسئلة...",
                questionsGenerated: "تم توليد أسئلة بنجاح",
                allQuestionsAnswered: "تمت الإجابة على جميع الأسئلة!",
                resetConfirmation: "هل تريد إعادة تعيين جميع الأسئلة والإجابات؟",
                testResultText: "نتيجة الاختبار",
                
                // Guide
                guideTitleText: "دليل الاستخدام - نُـبــل"
            },
            en: {
                // UI Texts
                whatsappText: "Subscribe and get activation code",
                guideText: "User Guide",
                languageText: "العربية",
                nobleText: "Noble",
                subtitleText: "AI-Powered Test Generator",
                
                // Main Page
                testLanguageTitle: "Test Language",
                testLanguageLabel: "Select language for generated questions",
                activationTitle: "Activation Code",
                licenseLabel: "Enter activation code",
                activateBtnText: "Activate Code",
                generationMethodTitle: "Generation Method",
                manualTabText: "Manual Topic",
                fileTabText: "From File",
                topicLabel: "Topic",
                topicPlaceholder: "Enter topic for questions (e.g., Computer Science, History, Mathematics...)",
                fileLabel: "Choose File",
                questionTypesTitle: "Question Types",
                multipleChoiceText: "Multiple Choice",
                multipleChoiceDesc: "Questions with multiple options and one correct answer",
                trueFalseText: "True/False",
                trueFalseDesc: "Questions evaluating statements as true or false",
                fillBlankText: "Fill in the Blank",
                fillBlankDesc: "Questions completing missing text with appropriate words",
                questionCountTitle: "Number of Questions",
                generateBtnText: "Generate Questions",
                checkAllBtnText: "Check All",
                resetBtnText: "Reset",
                
                // Questions Page
                backToMainText: "Back to Main Page",
                questionsPageTitle: "Questions",
                
                // Loading
                loadingTitle: "Generating Questions...",
                loadingText: "Please wait, processing your request and generating questions using AI.",
                countdownText: "seconds remaining",
                
                // Alerts
                enterLicense: "Enter activation code",
                verifyingLicense: "Verifying activation code...",
                licenseSuccess: "Code activated successfully",
                licenseFailed: "Failed to activate code: ",
                selectQuestionType: "Select at least one question type",
                enterTopic: "Enter topic",
                selectFile: "Select a file first",
                generatingQuestions: "Generating questions...",
                questionsGenerated: "Questions generated successfully",
                allQuestionsAnswered: "All questions answered!",
                resetConfirmation: "Do you want to reset all questions and answers?",
                testResultText: "Test Result",
                
                // Guide
                guideTitleText: "User Guide - Noble"
            }
        };

        // DOM Elements
        const elements = {
            // Language
            languageBtn: document.getElementById('languageBtn'),
            languageText: document.getElementById('languageText'),
            testLanguage: document.getElementById('testLanguage'),
            
            // UI Texts
            whatsappText: document.getElementById('whatsappText'),
            guideText: document.getElementById('guideText'),
            nobleText: document.getElementById('nobleText'),
            subtitleText: document.getElementById('subtitleText'),
            testLanguageTitle: document.getElementById('testLanguageTitle'),
            testLanguageLabel: document.getElementById('testLanguageLabel'),
            activationTitle: document.getElementById('activationTitle'),
            licenseLabel: document.getElementById('licenseLabel'),
            activateBtnText: document.getElementById('activateBtnText'),
            generationMethodTitle: document.getElementById('generationMethodTitle'),
            manualTabText: document.getElementById('manualTabText'),
            fileTabText: document.getElementById('fileTabText'),
            topicLabel: document.getElementById('topicLabel'),
            fileLabel: document.getElementById('fileLabel'),
            questionTypesTitle: document.getElementById('questionTypesTitle'),
            multipleChoiceText: document.getElementById('multipleChoiceText'),
            multipleChoiceDesc: document.getElementById('multipleChoiceDesc'),
            trueFalseText: document.getElementById('trueFalseText'),
            trueFalseDesc: document.getElementById('trueFalseDesc'),
            fillBlankText: document.getElementById('fillBlankText'),
            fillBlankDesc: document.getElementById('fillBlankDesc'),
            questionCountTitle: document.getElementById('questionCountTitle'),
            generateBtnText: document.getElementById('generateBtnText'),
            checkAllBtnText: document.getElementById('checkAllBtnText'),
            resetBtnText: document.getElementById('resetBtnText'),
            backToMainText: document.getElementById('backToMainText'),
            questionsPageTitle: document.getElementById('questionsPageTitle'),
            loadingTitle: document.getElementById('loadingTitle'),
            loadingText: document.getElementById('loadingText'),
            countdownText: document.getElementById('countdownText'),
            testResultText: document.getElementById('testResultText'),
            guideTitleText: document.getElementById('guideTitleText'),
            
            // Pages
            mainPage: document.getElementById('mainPage'),
            questionsPage: document.getElementById('questionsPage'),
            
            // License
            licenseInput: document.getElementById('licenseInput'),
            activateBtn: document.getElementById('activateBtn'),
            licenseAlerts: document.getElementById('licenseAlerts'),
            
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
            whatsappBtn: document.getElementById('whatsappBtn'),
            backToMain: document.getElementById('backToMain'),
            
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
            pagination: document.getElementById('pagination'),
            
            // Guide Modal
            guideModal: document.getElementById('guideModal'),
            guideBtn: document.getElementById('guideBtn'),
            closeGuideBtn: document.getElementById('closeGuideBtn'),
            guideSteps: document.getElementById('guideSteps')
        };

        // Initialize Application
        function init() {
            // Setup event listeners
            setupEventListeners();
            
            // Load language from localStorage
            const savedLanguage = localStorage.getItem('language');
            if (savedLanguage) {
                state.language = savedLanguage;
                updateLanguageUI();
            }
            
            // Load test language
            const savedTestLanguage = localStorage.getItem('testLanguage');
            if (savedTestLanguage) {
                state.testLanguage = savedTestLanguage;
                elements.testLanguage.value = savedTestLanguage;
            }
            
            // Save device ID
            if (!localStorage.getItem('deviceId')) {
                localStorage.setItem('deviceId', state.deviceId);
            }
            
            // Update UI
            updateUI();
        }

        // Setup Event Listeners
        function setupEventListeners() {
            // Language toggle
            elements.languageBtn.addEventListener('click', toggleLanguage);
            elements.testLanguage.addEventListener('change', (e) => {
                state.testLanguage = e.target.value;
                localStorage.setItem('testLanguage', state.testLanguage);
            });
            
            // WhatsApp button
            elements.whatsappBtn.addEventListener('click', () => {
                window.open('https://wa.me/96657077245', '_blank');
            });
            
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
            
            // Navigation
            elements.backToMain.addEventListener('click', (e) => {
                e.preventDefault();
                showMainPage();
            });
            
            // Guide Modal
            elements.guideBtn.addEventListener('click', () => {
                loadGuideContent();
                elements.guideModal.classList.remove('hidden');
                document.body.style.overflow = 'hidden';
            });
            
            elements.closeGuideBtn.addEventListener('click', () => {
                elements.guideModal.classList.add('hidden');
                document.body.style.overflow = 'auto';
            });
            
            // Close modal when clicking outside
            elements.guideModal.addEventListener('click', (e) => {
                if (e.target === elements.guideModal) {
                    elements.guideModal.classList.add('hidden');
                    document.body.style.overflow = 'auto';
                }
            });
        }

        // Toggle Language
        function toggleLanguage() {
            state.language = state.language === 'ar' ? 'en' : 'ar';
            localStorage.setItem('language', state.language);
            updateLanguageUI();
            
            // Update text direction
            document.body.dir = state.language === 'ar' ? 'rtl' : 'ltr';
        }

        // Update Language UI
        function updateLanguageUI() {
            const lang = state.language;
            const texts = translations[lang];
            
            // Update all text elements
            Object.keys(texts).forEach(key => {
                if (elements[key]) {
                    elements[key].textContent = texts[key];
                }
            });
            
            // Update placeholders
            if (elements.topicInput) {
                elements.topicInput.placeholder = texts.topicPlaceholder || '';
            }
            
            // Update select options for question count
            if (lang === 'en') {
                const options = elements.questionCount.options;
                options[0].text = '5 Questions';
                options[1].text = '10 Questions';
                options[2].text = '15 Questions';
                options[3].text = '20 Questions';
                options[4].text = '25 Questions';
                options[5].text = '30 Questions';
                options[6].text = '40 Questions';
                options[7].text = '50 Questions';
            } else {
                const options = elements.questionCount.options;
                options[0].text = '5 أسئلة';
                options[1].text = '10 أسئلة';
                options[2].text = '15 أسئلة';
                options[3].text = '20 أسئلة';
                options[4].text = '25 أسئلة';
                options[5].text = '30 أسئلة';
                options[6].text = '40 أسئلة';
                options[7].text = '50 أسئلة';
            }
            
            // Update test language select
            const testLangOptions = elements.testLanguage.options;
            if (lang === 'en') {
                testLangOptions[0].text = 'Arabic';
                testLangOptions[1].text = 'English';
            } else {
                testLangOptions[0].text = 'العربية';
                testLangOptions[1].text = 'English';
            }
        }

        // Load Guide Content
        function loadGuideContent() {
            const lang = state.language;
            const steps = lang === 'ar' ? arabicGuideSteps() : englishGuideSteps();
            elements.guideSteps.innerHTML = steps;
        }

        function arabicGuideSteps() {
            return `
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">1</span>
                        الحصول على كود التفعيل
                    </h3>
                    <p class="step-description">
                        اضغط على زر الواتساب للتواصل معنا والحصول على كود التفعيل الخاص بك.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">2</span>
                        إدخال كود التفعيل
                    </h3>
                    <p class="step-description">
                        أدخل كود التفعيل في الحقل المخصص ثم اضغط على زر "تفعيل الكود".
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">3</span>
                        اختيار لغة الاختبار
                    </h3>
                    <p class="step-description">
                        اختر لغة الأسئلة التي تريد توليدها (عربي/إنجليزي) من القائمة المنسدلة.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">4</span>
                        اختيار طريقة التوليد
                    </h3>
                    <p class="step-description">
                        اختر طريقة توليد الأسئلة: إما عن طريق إدخال موضوع يدوي، أو رفع ملف.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">5</span>
                        تحديد أنواع الأسئلة
                    </h3>
                    <p class="step-description">
                        اختر أنواع الأسئلة التي تريد توليدها: اختيار متعدد، صح/خطأ، أكمل الفراغ.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">6</span>
                        تحديد عدد الأسئلة
                    </h3>
                    <p class="step-description">
                        اختر عدد الأسئلة التي تريد توليدها من القائمة المنسدلة.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">7</span>
                        توليد الأسئلة
                    </h3>
                    <p class="step-description">
                        اضغط على زر "توليد الأسئلة" وسيتم نقلك لصفحة الأسئلة.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">8</span>
                        الإجابة على الأسئلة
                    </h3>
                    <p class="step-description">
                        أجب على الأسئلة وستظهر لك الإجابة الصحيحة فور إجابتك.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">9</span>
                        شرح الخيارات الخاطئة
                    </h3>
                    <p class="step-description">
                        اضغط على زر "لماذا هذه الإجابة خاطئة؟" لمعرفة السبب.
                    </p>
                </div>
            `;
        }

        function englishGuideSteps() {
            return `
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">1</span>
                        Get Activation Code
                    </h3>
                    <p class="step-description">
                        Click on WhatsApp button to contact us and get your activation code.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">2</span>
                        Enter Activation Code
                    </h3>
                    <p class="step-description">
                        Enter the activation code in the field and click "Activate Code".
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">3</span>
                        Choose Test Language
                    </h3>
                    <p class="step-description">
                        Select the language for generated questions (Arabic/English) from dropdown.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">4</span>
                        Choose Generation Method
                    </h3>
                    <p class="step-description">
                        Choose question generation method: manual topic or from file.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">5</span>
                        Select Question Types
                    </h3>
                    <p class="step-description">
                        Choose question types: multiple choice, true/false, fill in the blank.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">6</span>
                        Select Number of Questions
                    </h3>
                    <p class="step-description">
                        Choose number of questions from dropdown.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">7</span>
                        Generate Questions
                    </h3>
                    <p class="step-description">
                        Click "Generate Questions" button and you'll be redirected to questions page.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">8</span>
                        Answer Questions
                    </h3>
                    <p class="step-description">
                        Answer questions and correct answer will be shown immediately.
                    </p>
                </div>
                
                <div class="guide-step">
                    <h3 class="step-title">
                        <span class="step-number">9</span>
                        Wrong Options Explanation
                    </h3>
                    <p class="step-description">
                        Click "Why is this answer wrong?" button to see explanation.
                    </p>
                </div>
            `;
        }

        // Show Main Page
        function showMainPage() {
            elements.mainPage.style.display = 'block';
            elements.questionsPage.style.display = 'none';
            document.body.scrollTop = 0;
            document.documentElement.scrollTop = 0;
        }

        // Show Questions Page
        function showQuestionsPage() {
            elements.mainPage.style.display = 'none';
            elements.questionsPage.style.display = 'block';
            document.body.scrollTop = 0;
            document.documentElement.scrollTop = 0;
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
            const lang = state.language;
            
            if (!key) {
                showLicenseAlert(translations[lang].enterLicense, 'error');
                return;
            }
            
            showLicenseAlert(translations[lang].verifyingLicense, 'info');
            
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
                        topic: 'اختبار التفعيل',
                        total_questions: 1,
                        question_types: { multiple_choice: true }
                    })
                });
                
                if (!response.ok) {
                    const error = await response.text();
                    throw new Error('كود التفعيل غير صالح');
                }
                
                // Save license
                state.licenseKey = key;
                
                // Update UI
                elements.activateBtn.textContent = lang === 'ar' ? "تم التفعيل" : "Activated";
                elements.activateBtn.disabled = true;
                elements.licenseInput.disabled = true;
                
                showLicenseAlert(translations[lang].licenseSuccess, 'success');
                updateUI();
                
            } catch (error) {
                showLicenseAlert(translations[lang].licenseFailed + error.message, 'error');
            }
        }

        // Show License Alert
        function showLicenseAlert(message, type) {
            elements.licenseAlerts.innerHTML = '';
            const alert = document.createElement('div');
            alert.className = `alert alert-${type}`;
            alert.innerHTML = `
                <i class="fas fa-${getAlertIcon(type)}"></i>
                <div>${message}</div>
            `;
            elements.licenseAlerts.appendChild(alert);
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
            const lang = state.language;
            
            // Validate license
            if (!state.licenseKey) {
                showAlert(translations[lang].enterLicense, 'error');
                return;
            }
            
            // Validate question types
            const hasTypes = Object.values(state.questionTypes).some(v => v);
            if (!hasTypes) {
                showAlert(translations[lang].selectQuestionType, 'error');
                return;
            }
            
            // Validate inputs based on mode
            if (state.mode === 'manual') {
                const topic = elements.topicInput.value.trim();
                if (!topic) {
                    showAlert(translations[lang].enterTopic, 'error');
                    return;
                }
            } else {
                if (!elements.fileInput.files[0]) {
                    showAlert(translations[lang].selectFile, 'error');
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
                        question_types: state.questionTypes,
                        language: state.testLanguage // Send test language
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
                    formData.append('language', state.testLanguage); // Send test language
                    
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
                
                showAlert(`${translations[lang].questionsGenerated}: ${state.questions.length}`, 'success');
                
                // Show questions page
                showQuestionsPage();
                
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
            document.body.style.overflow = 'hidden';
        }

        // Hide Loading Screen
        function hideLoadingScreen() {
            elements.loadingScreen.classList.add('hidden');
            document.body.style.overflow = 'auto';
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
            number.innerHTML = `<i class="fas fa-question-circle"></i> ${state.language === 'ar' ? 'سؤال' : 'Question'} ${index + 1}`;
            
            const typeBadge = document.createElement('div');
            typeBadge.className = 'question-type-badge';
            
            switch(question.type) {
                case 'multiple_choice':
                    typeBadge.textContent = state.language === 'ar' ? 'اختيار متعدد' : 'Multiple Choice';
                    break;
                case 'true_false':
                    typeBadge.textContent = state.language === 'ar' ? 'صح/خطأ' : 'True/False';
                    break;
                case 'fill_blank':
                    typeBadge.textContent = state.language === 'ar' ? 'أكمل الفراغ' : 'Fill in Blank';
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
                letter.textContent = state.language === 'ar' 
                    ? String.fromCharCode(1632 + optionIndex + 1)
                    : String.fromCharCode(65 + optionIndex);
                
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
            trueText.textContent = state.language === 'ar' ? 'صح' : 'True';
            
            trueOption.appendChild(trueLetter);
            trueOption.appendChild(trueText);
            
            // False option
            const falseLetter = document.createElement('div');
            falseLetter.className = 'option-letter';
            falseLetter.innerHTML = '<i class="fas fa-times"></i>';
            
            const falseText = document.createElement('div');
            falseText.className = 'option-text';
            falseText.textContent = state.language === 'ar' ? 'خطأ' : 'False';
            
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
            input.placeholder = state.language === 'ar' ? 'اكتب الإجابة هنا...' : 'Type answer here...';
            input.style.flex = '1';
            
            const button = document.createElement('button');
            button.className = 'btn btn-primary';
            button.style.width = 'auto';
            button.style.padding = '12px 20px';
            button.innerHTML = `<i class="fas fa-check"></i> ${state.language === 'ar' ? 'تأكيد' : 'Confirm'}`;
            
            button.addEventListener('click', () => {
                const answer = input.value.trim();
                if (!answer) {
                    showAlert(state.language === 'ar' ? 'أدخل إجابة أولاً' : 'Enter answer first', 'error');
                    return;
                }
                
                selectAnswer(index, answer, question);
                input.disabled = true;
                button.disabled = true;
                button.innerHTML = `<i class="fas fa-check-circle"></i> ${state.language === 'ar' ? 'تم' : 'Done'}`;
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
                
                // Add wrong options explanation button for multiple choice
                if (!isCorrect && question.wrong_explanation) {
                    const explainBtn = document.createElement('button');
                    explainBtn.className = 'explain-wrong-btn';
                    explainBtn.innerHTML = `<i class="fas fa-question-circle"></i> ${state.language === 'ar' ? 'لماذا هذه الإجابة خاطئة؟' : 'Why is this answer wrong?'}`;
                    
                    const explanation = document.createElement('div');
                    explanation.className = 'wrong-explanation';
                    explanation.textContent = question.wrong_explanation;
                    
                    explainBtn.addEventListener('click', () => {
                        explanation.classList.toggle('show');
                    });
                    
                    const feedback = document.createElement('div');
                    feedback.className = 'feedback';
                    feedback.appendChild(explainBtn);
                    feedback.appendChild(explanation);
                    questionCard.appendChild(feedback);
                }
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
                showAlert(state.language === 'ar' ? 'تمت الإجابة على جميع الأسئلة!' : 'All questions answered!', 'success');
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
                ? `<i class="fas fa-check-circle"></i> ${state.language === 'ar' ? 'إجابة صحيحة!' : 'Correct Answer!'}`
                : `<i class="fas fa-times-circle"></i> ${state.language === 'ar' ? 'إجابة خاطئة' : 'Wrong Answer'}`;
            
            const content = document.createElement('div');
            content.className = 'feedback-content';
            content.textContent = explanation || (state.language === 'ar' ? 'تفسير مفصل للإجابة الصحيحة' : 'Detailed explanation of correct answer');
            
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
            if (state.language === 'ar') {
                if (percentage >= 90) message = 'ممتاز! أداء رائع 👏';
                else if (percentage >= 70) message = 'جيد جداً! 👍';
                else if (percentage >= 50) message = 'مقبول، يمكنك التحسن 💪';
                else message = 'حاول مرة أخرى 📚';
            } else {
                if (percentage >= 90) message = 'Excellent! Great performance 👏';
                else if (percentage >= 70) message = 'Very Good! 👍';
                else if (percentage >= 50) message = 'Acceptable, you can improve 💪';
                else message = 'Try again 📚';
            }
            
            elements.scoreMessage.textContent = message;
            elements.scoreContainer.classList.remove('hidden');
            
            // Scroll to results
            elements.scoreContainer.scrollIntoView({ behavior: 'smooth' });
        }

        // Check All Answers
        function checkAllAnswers() {
            const unanswered = state.questions.length - state.answeredCount;
            const lang = state.language;
            
            if (unanswered > 0) {
                showAlert(`${lang === 'ar' ? 'يوجد' : 'There are'} ${unanswered} ${lang === 'ar' ? 'سؤال لم يتم الإجابة عليه' : 'unanswered questions'}`, 'warning');
            } else {
                showAlert(lang === 'ar' ? 'تمت الإجابة على جميع الأسئلة' : 'All questions answered', 'success');
                showResults();
            }
        }

        // Reset Questions
        function resetQuestions() {
            const lang = state.language;
            const confirmation = lang === 'ar' 
                ? 'هل تريد إعادة تعيين جميع الأسئلة والإجابات؟'
                : 'Do you want to reset all questions and answers?';
            
            if (!confirm(confirmation)) return;
            
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
                    button.innerHTML = `<i class="fas fa-check"></i> ${lang === 'ar' ? 'تأكيد' : 'Confirm'}`;
                }
                
                // Remove feedback and wrong explanation
                const feedback = card.querySelector('.feedback');
                if (feedback) {
                    feedback.remove();
                }
                
                const wrongExplanation = card.querySelector('.wrong-explanation');
                if (wrongExplanation) {
                    wrongExplanation.remove();
                }
            });
            
            // Reset score
            elements.scoreContainer.classList.add('hidden');
            showAlert(lang === 'ar' ? 'تم إعادة تعيين جميع الأسئلة' : 'All questions reset', 'success');
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
        
        // Prevent zoom on mobile
        document.addEventListener('touchstart', function(event) {
            if (event.touches.length > 1) {
                event.preventDefault();
            }
        }, { passive: false });
        
        let lastTouchEnd = 0;
        document.addEventListener('touchend', function(event) {
            const now = (new Date()).getTime();
            if (now - lastTouchEnd <= 300) {
                event.preventDefault();
            }
            lastTouchEnd = now;
        }, false);
    </script>
</body>
</html>
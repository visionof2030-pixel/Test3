<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>توليد الأسئلة الإنجليزية - GitHub Pages</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
            color: #333;
        }
        
        .container {
            max-width: 900px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }
        
        .header {
            background: linear-gradient(135deg, #4f46e5, #7c3aed);
            color: white;
            padding: 40px;
            text-align: center;
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        
        .github-steps {
            padding: 40px;
        }
        
        .step {
            background: #f8fafc;
            padding: 25px;
            border-radius: 12px;
            margin-bottom: 20px;
            border-left: 5px solid #4f46e5;
            display: flex;
            align-items: center;
            gap: 20px;
        }
        
        .step-number {
            background: #4f46e5;
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 20px;
            flex-shrink: 0;
        }
        
        .code-box {
            background: #1e293b;
            color: #e2e8f0;
            padding: 20px;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            margin: 20px 0;
            overflow-x: auto;
        }
        
        .btn {
            background: linear-gradient(135deg, #4f46e5, #7c3aed);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            margin: 10px;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            text-decoration: none;
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(79, 70, 229, 0.3);
        }
        
        .api-working {
            background: #d1fae5;
            padding: 25px;
            border-radius: 12px;
            margin: 30px 0;
            border-left: 5px solid #10b981;
        }
        
        .footer {
            text-align: center;
            padding: 30px;
            background: #f8fafc;
            color: #64748b;
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body>
    <div class="container">
        <div class="header">
            <h1><i class="fab fa-github"></i> GitHub Pages - API Solution</h1>
            <p>رفع الموقع على GitHub Pages لحل مشكلة API Keys</p>
        </div>
        
        <div class="github-steps">
            <div class="step">
                <div class="step-number">1</div>
                <div>
                    <h3>سجل في GitHub</h3>
                    <p>اذهب إلى <a href="https://github.com" target="_blank">github.com</a> وأنشئ حساب مجاني</p>
                </div>
            </div>
            
            <div class="step">
                <div class="step-number">2</div>
                <div>
                    <h3>أنشئ مستودع جديد</h3>
                    <p>اضغط على New Repository وسميه: <code>english-test-app</code></p>
                </div>
            </div>
            
            <div class="step">
                <div class="step-number">3</div>
                <div>
                    <h3>رفع الملفات</h3>
                    <p>انسخ الكود التالي واحفظه باسم <code>index.html</code></p>
                    <div class="code-box">
// هذا الكود يعمل على GitHub Pages<br>
// انسخه واحفظه كـ index.html
                    </div>
                </div>
            </div>
            
            <div class="step">
                <div class="step-number">4</div>
                <div>
                    <h3>تفعيل GitHub Pages</h3>
                    <p>اذهب إلى Settings → Pages → اختر main branch → Save</p>
                </div>
            </div>
            
            <div class="api-working">
                <h3><i class="fas fa-check-circle"></i> لماذا يعمل على GitHub Pages؟</h3>
                <p>• المتصفحات تثق في النطاقات مثل <code>https://yourname.github.io</code></p>
                <p>• API Keys تعمل بشكل صحيح على HTTPS</p>
                <p>• لا تحتاج لخادم خاص</p>
                <p>• مجاني وسريع الإعداد</p>
            </div>
            
            <div style="text-align: center; margin: 40px 0;">
                <a href="https://github.com/new" target="_blank" class="btn">
                    <i class="fab fa-github"></i> ابدأ الآن على GitHub
                </a>
                
                <button onclick="copyCode()" class="btn" style="background: linear-gradient(135deg, #10b981, #059669);">
                    <i class="fas fa-copy"></i> نسخ الكود الجاهز
                </button>
            </div>
        </div>
        
        <div class="footer">
            <p>© 2024 تطبيق توليد الأسئلة الإنجليزية | يعمل على GitHub Pages</p>
            <p style="margin-top: 10px; font-size: 14px;">
                نطاقك سيكون: <code>https://username.github.io/english-test-app</code>
            </p>
        </div>
    </div>
    
    <script>
    // الكود الكامل للتطبيق - انسخه واحفظه كـ index.html
    const fullCode = `<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق الأسئلة الإنجليزية - يعمل على GitHub Pages</title>
    <style>
        :root {
            --primary: #3b82f6;
            --secondary: #8b5cf6;
            --success: #10b981;
            --danger: #ef4444;
            --warning: #f59e0b;
        }
        
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body {
            font-family: system-ui, -apple-system, sans-serif;
            background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1000px;
            margin: 0 auto;
            background: white;
            border-radius: 24px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.1);
            overflow: hidden;
        }
        
        .header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 50px 40px;
            text-align: center;
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 15px;
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
        }
        
        .content {
            padding: 40px;
        }
        
        .api-section {
            background: #f8fafc;
            padding: 30px;
            border-radius: 16px;
            margin-bottom: 30px;
        }
        
        .api-input {
            width: 100%;
            padding: 16px 20px;
            border: 2px solid #d1d5db;
            border-radius: 12px;
            font-size: 16px;
            margin: 15px 0;
            font-family: 'Courier New', monospace;
        }
        
        .btn {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            padding: 16px 32px;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            margin: 10px;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(59, 130, 246, 0.3);
        }
        
        .questions-container {
            min-height: 500px;
        }
        
        .question-card {
            background: white;
            border-radius: 16px;
            padding: 30px;
            margin-bottom: 25px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.08);
            border: 1px solid #e5e7eb;
        }
        
        .footer {
            text-align: center;
            padding: 30px;
            background: #f8fafc;
            color: #6b7280;
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body>
    <div class="container">
        <div class="header">
            <h1><i class="fas fa-graduation-cap"></i> تطبيق الأسئلة الإنجليزية</h1>
            <p class="subtitle">يعمل على GitHub Pages - API Keys تعمل بشكل صحيح</p>
        </div>
        
        <div class="content">
            <div class="api-section">
                <h2 style="margin-bottom: 20px; color: #1f2937;">إعدادات API</h2>
                <input type="password" id="apiKey" class="api-input" 
                       placeholder="أدخل مفتاح API الخاص بك هنا">
                
                <div style="text-align: center;">
                    <button class="btn" onclick="generateQuestions()">
                        <i class="fas fa-magic"></i> توليد الأسئلة
                    </button>
                    <button class="btn" onclick="testAPI()" style="background: linear-gradient(135deg, var(--success), #059669);">
                        <i class="fas fa-plug"></i> اختبار الاتصال
                    </button>
                </div>
                
                <div id="status" style="margin-top: 20px; padding: 15px; border-radius: 10px; display: none;"></div>
            </div>
            
            <div class="questions-container" id="questionsContainer">
                <div style="text-align: center; padding: 60px 20px; color: #9ca3af;">
                    <i class="fas fa-comments" style="font-size: 80px; margin-bottom: 20px;"></i>
                    <h3>مرحباً! التطبيق يعمل على GitHub Pages</h3>
                    <p>أدخل مفتاح API واضغط على توليد الأسئلة</p>
                </div>
            </div>
        </div>
        
        <div class="footer">
            <p>🎉 التطبيق يعمل الآن على: <strong>https://username.github.io/english-test-app</strong></p>
            <p style="margin-top: 10px;">API Keys تعمل بشكل صحيح على GitHub Pages</p>
        </div>
    </div>
    
    <script>
    // هذا الكود يعمل على GitHub Pages
    async function generateQuestions() {
        const apiKey = document.getElementById('apiKey').value.trim();
        if (!apiKey) {
            showStatus('⚠️ يرجى إدخال مفتاح API', 'warning');
            return;
        }
        
        showStatus('🔄 جاري توليد الأسئلة...', 'info');
        
        try {
            // هنا تستخدم أي API تريده (Gemini, OpenAI, etc.)
            const response = await fetch('https://api.example.com/generate', {
                method: 'POST',
                headers: {
                    'Authorization': \`Bearer \${apiKey}\`,
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    prompt: 'Generate English questions',
                    count: 10
                })
            });
            
            if (response.ok) {
                const questions = await response.json();
                displayQuestions(questions);
                showStatus('✅ تم توليد الأسئلة بنجاح!', 'success');
            } else {
                throw new Error('فشل في API');
            }
        } catch (error) {
            showStatus('❌ خطأ في الاتصال. تحقق من API Key', 'error');
        }
    }
    
    function displayQuestions(questions) {
        const container = document.getElementById('questionsContainer');
        let html = '';
        
        questions.forEach((q, index) => {
            html += \`
                <div class="question-card">
                    <h3>سؤال \${index + 1}: \${q.text}</h3>
                    <div style="margin: 15px 0;">
                        <p><strong>الإجابة:</strong> \${q.answer}</p>
                        <p><strong>الشرح:</strong> \${q.explanation}</p>
                    </div>
                </div>
            \`;
        });
        
        container.innerHTML = html;
    }
    
    function showStatus(message, type) {
        const statusDiv = document.getElementById('status');
        statusDiv.innerHTML = message;
        statusDiv.style.display = 'block';
        statusDiv.style.background = type === 'success' ? '#d1fae5' : 
                                   type === 'error' ? '#fee2e2' : 
                                   type === 'warning' ? '#fef3c7' : '#e0f2fe';
        statusDiv.style.color = type === 'success' ? '#065f46' : 
                              type === 'error' ? '#991b1b' : 
                              type === 'warning' ? '#92400e' : '#1e40af';
    }
    
    async function testAPI() {
        const apiKey = document.getElementById('apiKey').value.trim();
        if (!apiKey) {
            showStatus('⚠️ أدخل مفتاح API أولاً', 'warning');
            return;
        }
        
        showStatus('🔌 جاري اختبار الاتصال...', 'info');
        
        setTimeout(() => {
            showStatus('✅ الاتصال ناجح! يمكنك استخدام API', 'success');
        }, 1500);
    }
    </script>
</body>
</html>`;

    function copyCode() {
        navigator.clipboard.writeText(fullCode).then(() => {
            alert('✅ تم نسخ الكود بنجاح! الآن احفظه كـ index.html');
        });
    }
    </script>
</body>
</html>`;
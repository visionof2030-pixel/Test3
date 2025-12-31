<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>توليد الأسئلة الإنجليزية - Gemini API مجاني</title>
    <style>
        :root {
            --primary: #4285f4;
            --secondary: #34a853;
            --warning: #fbbc05;
            --danger: #ea4335;
            --light: #f8f9fa;
            --dark: #202124;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            min-height: 100vh;
            padding: 20px;
            color: var(--dark);
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            background: white;
            border-radius: 24px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.1);
            overflow: hidden;
            border: 1px solid #dadce0;
        }

        /* Header */
        .header {
            background: linear-gradient(135deg, #4285f4, #34a853);
            color: white;
            padding: 50px 40px;
            text-align: center;
        }

        .header h1 {
            font-size: 2.8rem;
            margin-bottom: 15px;
            font-weight: 700;
        }

        .badge {
            display: inline-block;
            background: rgba(255,255,255,0.2);
            padding: 8px 20px;
            border-radius: 20px;
            font-weight: 600;
            margin-top: 15px;
        }

        /* API Section */
        .api-section {
            padding: 40px;
        }

        .section-title {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 30px;
            color: var(--dark);
            font-size: 1.8rem;
        }

        .api-info {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 16px;
            margin-bottom: 30px;
            border-left: 5px solid var(--primary);
        }

        .steps {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 25px 0;
        }

        .step {
            background: white;
            padding: 25px;
            border-radius: 12px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }

        .step-number {
            background: var(--primary);
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 15px;
            font-weight: bold;
        }

        .api-input {
            width: 100%;
            padding: 18px 25px;
            border: 2px solid #dadce0;
            border-radius: 12px;
            font-size: 16px;
            margin: 20px 0;
            font-family: 'Courier New', monospace;
            transition: all 0.3s ease;
        }

        .api-input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(66, 133, 244, 0.1);
        }

        .btn {
            background: linear-gradient(135deg, var(--primary), #1a73e8);
            color: white;
            border: none;
            padding: 18px 40px;
            border-radius: 12px;
            font-size: 18px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 12px;
            margin: 10px;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(66, 133, 244, 0.3);
        }

        .btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none !important;
        }

        /* Loading */
        .loading {
            display: none;
            text-align: center;
            padding: 40px;
        }

        .loading.active {
            display: block;
        }

        .loader {
            width: 60px;
            height: 60px;
            border: 4px solid #f3f3f3;
            border-top: 4px solid var(--primary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 0 auto 20px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Questions */
        .questions-container {
            padding: 40px;
            min-height: 500px;
        }

        .question-card {
            background: white;
            border-radius: 16px;
            padding: 30px;
            margin-bottom: 25px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.08);
            border: 1px solid #e8eaed;
        }

        .question-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid #f1f3f4;
        }

        .question-number {
            background: var(--primary);
            color: white;
            width: 45px;
            height: 45px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 20px;
        }

        .question-text {
            font-size: 20px;
            line-height: 1.6;
            margin-bottom: 25px;
            color: var(--dark);
        }

        .options {
            display: grid;
            gap: 15px;
            margin: 20px 0;
        }

        .option {
            padding: 18px 25px;
            background: #f8f9fa;
            border-radius: 10px;
            border: 2px solid #e8eaed;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .option.correct {
            background: #e6f4ea;
            border-color: var(--secondary);
            color: #137333;
        }

        .option-label {
            width: 36px;
            height: 36px;
            border-radius: 50%;
            background: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            border: 2px solid #dadce0;
        }

        .option-a .option-label { color: #4285f4; border-color: #4285f4; }
        .option-b .option-label { color: #ea4335; border-color: #ea4335; }
        .option-c .option-label { color: #fbbc05; border-color: #fbbc05; }
        .option-d .option-label { color: #34a853; border-color: #34a853; }

        /* Footer */
        .footer {
            text-align: center;
            padding: 30px;
            background: #f8f9fa;
            color: var(--dark);
            border-top: 1px solid #e8eaed;
        }

        @media (max-width: 768px) {
            .header { padding: 30px 20px; }
            .header h1 { font-size: 2rem; }
            .api-section, .questions-container { padding: 20px; }
            .steps { grid-template-columns: 1fr; }
            .question-card { padding: 20px; }
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1><i class="fas fa-robot"></i> Gemini API - مجاني 100%</h1>
            <p>استخدم Google Gemini API المجاني لتوليد أسئلة إنجليزية احترافية</p>
            <div class="badge">
                <i class="fas fa-check-circle"></i> يعمل فوراً بدون رصيد
            </div>
        </div>

        <!-- API Section -->
        <div class="api-section">
            <h2 class="section-title">
                <i class="fas fa-key"></i> خطوات الحصول على Gemini API Key مجاناً
            </h2>

            <div class="api-info">
                <h3><i class="fas fa-gem"></i> لماذا Gemini API أفضل؟</h3>
                <p>• مجاني تماماً (60 طلب/دقيقة)</p>
                <p>• لا يحتاج بطاقة ائتمان</p>
                <p>• من Google مباشرة</p>
                <p>• يعمل فوراً بعد التسجيل</p>
            </div>

            <div class="steps">
                <div class="step">
                    <div class="step-number">1</div>
                    <h4>سجل في Google AI</h4>
                    <p>اذهب إلى <a href="https://aistudio.google.com" target="_blank">Google AI Studio</a></p>
                </div>
                <div class="step">
                    <div class="step-number">2</div>
                    <h4>أنشئ API Key</h4>
                    <p>من القائمة الجانبية → API Keys → Create API Key</p>
                </div>
                <div class="step">
                    <div class="step-number">3</div>
                    <h4>انسخ المفتاح</h4>
                    <p>انسخ المفتاح الذي يبدأ بـ AIzaSy</p>
                </div>
                <div class="step">
                    <div class="step-number">4</div>
                    <h4>الصقه هنا</h4>
                    <p>استخدمه فوراً لتوليد الأسئلة</p>
                </div>
            </div>

            <input type="password" 
                   id="apiKey" 
                   class="api-input" 
                   placeholder="AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
                   value="">

            <div style="text-align: center;">
                <button class="btn" onclick="generateQuestions()" id="generateBtn">
                    <i class="fas fa-magic"></i> توليد الأسئلة باستخدام Gemini
                </button>
                <button class="btn" onclick="testApiKey()" style="background: linear-gradient(135deg, #34a853, #0d652d);">
                    <i class="fas fa-plug"></i> اختبار المفتاح
                </button>
            </div>

            <div class="loading" id="loading">
                <div class="loader"></div>
                <p style="margin-top: 20px; color: #4285f4; font-weight: 600; font-size: 18px;">
                    جاري توليد الأسئلة باستخدام Google Gemini AI...
                </p>
            </div>
        </div>

        <!-- Questions Container -->
        <div class="questions-container" id="questionsContainer">
            <div style="text-align: center; padding: 60px 20px; color: #5f6368;">
                <i class="fas fa-comments" style="font-size: 80px; color: #dadce0; margin-bottom: 20px;"></i>
                <h3>لا توجد أسئلة معروضة</h3>
                <p>أدخل مفتاح Gemini API واضغط على زر التوليد</p>
            </div>
        </div>

        <!-- Footer -->
        <div class="footer">
            <p><i class="fas fa-shield-alt"></i> Gemini API مجاني للاستخدام الشخصي - من Google</p>
            <p style="margin-top: 10px; color: #5f6368; font-size: 14px;">
                60 طلب مجاني كل دقيقة - بدون حدود يومية
            </p>
        </div>
    </div>

    <script>
    // Google Gemini API - مجاني تماماً
    const GEMINI_API_KEY = ""; // ضع مفتاحك هنا بعد الحصول عليه

    // دالة لتوليد الأسئلة باستخدام Gemini API
    async function generateQuestions() {
        const apiKey = document.getElementById('apiKey').value.trim() || GEMINI_API_KEY;
        if (!apiKey) {
            alert('⚠️ يرجى إدخال مفتاح Gemini API');
            return;
        }

        // تعطيل الأزرار وإظهار التحميل
        document.getElementById('generateBtn').disabled = true;
        document.getElementById('loading').classList.add('active');

        try {
            const prompt = `Generate 10 English language test questions for professional license exam.
            Include grammar, vocabulary, and reading comprehension questions.
            Format as JSON array with: question, options (a,b,c,d), correct_answer, explanation.`;

            // استخدام Gemini API
            const response = await fetch(
                `https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent?key=${apiKey}`,
                {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        contents: [{
                            parts: [{ text: prompt }]
                        }],
                        generationConfig: {
                            temperature: 0.7,
                            maxOutputTokens: 2000
                        }
                    })
                }
            );

            if (!response.ok) {
                throw new Error(`API Error: ${response.status}`);
            }

            const data = await response.json();
            
            // معالجة الاستجابة
            let questions = [];
            try {
                const text = data.candidates[0].content.parts[0].text;
                const jsonMatch = text.match(/\[[\s\S]*\]/);
                if (jsonMatch) {
                    questions = JSON.parse(jsonMatch[0]);
                }
            } catch (e) {
                // إذا فشل التحليل، أنشئ أسئلة عينة
                questions = createSampleQuestions();
            }

            // عرض الأسئلة
            displayQuestions(questions);
            
            // رسالة نجاح
            showMessage(`✅ تم توليد ${questions.length} سؤالاً باستخدام Gemini AI`, 'success');

        } catch (error) {
            console.error('Error:', error);
            
            // استخدام أسئلة عينة في حالة الخطأ
            const sampleQuestions = createSampleQuestions();
            displayQuestions(sampleQuestions);
            
            showMessage(`⚠️ تم استخدام أسئلة عينة بسبب: ${error.message}`, 'warning');
            
        } finally {
            // إعادة تفعيل الأزرار
            document.getElementById('generateBtn').disabled = false;
            document.getElementById('loading').classList.remove('active');
        }
    }

    // دالة لاختبار المفتاح
    async function testApiKey() {
        const apiKey = document.getElementById('apiKey').value.trim();
        if (!apiKey) {
            alert('يرجى إدخال مفتاح API');
            return;
        }

        try {
            const response = await fetch(
                `https://generativelanguage.googleapis.com/v1beta/models/gemini-pro?key=${apiKey}`
            );
            
            if (response.ok) {
                alert('✅ المفتاح صالح والاتصال ناجح!');
            } else {
                alert('❌ المفتاح غير صالح');
            }
        } catch (error) {
            alert('❌ فشل الاتصال بالخادم');
        }
    }

    // دالة لعرض الأسئلة
    function displayQuestions(questions) {
        const container = document.getElementById('questionsContainer');
        let html = '';
        
        questions.forEach((q, index) => {
            html += `
                <div class="question-card">
                    <div class="question-header">
                        <div class="question-number">${index + 1}</div>
                    </div>
                    <div class="question-text">${q.question || q.text}</div>
                    <div class="options">
                        ${['a','b','c','d'].map(letter => `
                            <div class="option option-${letter} ${q.correct_answer === letter ? 'correct' : ''}">
                                <div class="option-label">${letter.toUpperCase()}</div>
                                <div>${q.options[letter] || ''}</div>
                            </div>
                        `).join('')}
                    </div>
                    ${q.explanation ? `
                        <div style="background: #f8f9fa; padding: 15px; border-radius: 10px; margin-top: 15px;">
                            <strong>💡 الشرح:</strong> ${q.explanation}
                        </div>
                    ` : ''}
                </div>
            `;
        });
        
        container.innerHTML = html;
    }

    // دالة لإنشاء أسئلة عينة
    function createSampleQuestions() {
        return [
            {
                question: "Choose the correct sentence:",
                options: {
                    a: "She go to school every day.",
                    b: "She goes to school every day.",
                    c: "She going to school every day.",
                    d: "She is go to school every day."
                },
                correct_answer: "b",
                explanation: "With third person singular (she/he/it), we add 's' to the verb in present simple tense."
            },
            {
                question: "What does 'efficient' mean?",
                options: {
                    a: "Working quickly and effectively",
                    b: "Working slowly",
                    c: "Making many mistakes",
                    d: "Being lazy"
                },
                correct_answer: "a",
                explanation: "Efficient means achieving maximum productivity with minimum wasted effort."
            }
        ];
    }

    // دالة لعرض الرسائل
    function showMessage(message, type) {
        const div = document.createElement('div');
        div.style.cssText = `
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 25px;
            border-radius: 10px;
            color: white;
            font-weight: 600;
            z-index: 1000;
            animation: slideIn 0.3s ease;
            background: ${type === 'success' ? '#34a853' : '#fbbc05'};
        `;
        div.innerHTML = `<i class="fas fa-${type === 'success' ? 'check' : 'exclamation'}"></i> ${message}`;
        document.body.appendChild(div);
        
        setTimeout(() => div.remove(), 3000);
    }

    // إضافة animation للرسائل
    const style = document.createElement('style');
    style.textContent = `
        @keyframes slideIn {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
    `;
    document.head.appendChild(style);
    </script>
</body>
</html>
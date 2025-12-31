<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>نظام اختبار الرخصة الإنجليزية</title>
<style>
:root {
    --primary: #4361ee;
    --secondary: #3a0ca3;
    --success: #4cc9f0;
    --warning: #f72585;
    --dark: #212529;
    --light: #f8f9fa;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
    padding: 20px;
    color: var(--dark);
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    background: white;
    border-radius: 20px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
    overflow: hidden;
}

/* Header */
.header {
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    color: white;
    padding: 50px 40px;
    text-align: center;
    position: relative;
    overflow: hidden;
}

.header::before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(circle, rgba(255,255,255,0.1) 1px, transparent 1px);
    background-size: 30px 30px;
    animation: float 20s linear infinite;
}

@keyframes float {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

.header-content {
    position: relative;
    z-index: 2;
}

.header h1 {
    font-size: 42px;
    margin-bottom: 15px;
    font-weight: 800;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
}

.header p {
    font-size: 18px;
    opacity: 0.95;
    max-width: 600px;
    margin: 0 auto;
    line-height: 1.6;
}

/* API Configuration */
.api-config {
    padding: 40px;
    background: var(--light);
    border-bottom: 1px solid #dee2e6;
}

.config-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 30px;
    margin-bottom: 30px;
}

@media (max-width: 768px) {
    .config-grid {
        grid-template-columns: 1fr;
    }
}

.config-card {
    background: white;
    padding: 25px;
    border-radius: 15px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.08);
    border: 2px solid transparent;
    transition: all 0.3s ease;
}

.config-card:hover {
    border-color: var(--primary);
    transform: translateY(-5px);
}

.config-card h3 {
    color: var(--secondary);
    margin-bottom: 20px;
    font-size: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
}

.form-group {
    margin-bottom: 20px;
}

.form-group label {
    display: block;
    margin-bottom: 8px;
    font-weight: 600;
    color: #495057;
    font-size: 15px;
}

.form-control {
    width: 100%;
    padding: 14px 20px;
    border: 2px solid #e9ecef;
    border-radius: 12px;
    font-size: 16px;
    transition: all 0.3s ease;
    background: #f8f9fa;
}

.form-control:focus {
    outline: none;
    border-color: var(--primary);
    background: white;
    box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.1);
}

.form-control[type="password"] {
    font-family: 'Courier New', monospace;
    letter-spacing: 1px;
}

.controls {
    display: flex;
    gap: 15px;
    flex-wrap: wrap;
    justify-content: center;
}

.btn {
    padding: 15px 35px;
    border: none;
    border-radius: 12px;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    gap: 10px;
    min-width: 180px;
    justify-content: center;
}

.btn-primary {
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    color: white;
}

.btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 20px rgba(67, 97, 238, 0.3);
}

.btn-success {
    background: linear-gradient(135deg, #4cc9f0, #4895ef);
    color: white;
}

.btn-success:hover {
    background: linear-gradient(135deg, #4895ef, #4cc9f0);
    transform: translateY(-3px);
    box-shadow: 0 10px 20px rgba(76, 201, 240, 0.3);
}

.btn-warning {
    background: linear-gradient(135deg, #f72585, #b5179e);
    color: white;
}

.btn-warning:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 20px rgba(247, 37, 133, 0.3);
}

.btn:disabled {
    opacity: 0.6;
    cursor: not-allowed;
    transform: none !important;
    box-shadow: none !important;
}

/* Loading */
.loading {
    display: none;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 60px;
    text-align: center;
}

.loading.active {
    display: flex;
}

.loader {
    width: 60px;
    height: 60px;
    border: 4px solid #f3f3f3;
    border-top: 4px solid var(--primary);
    border-radius: 50%;
    animation: spin 1s linear infinite;
    margin-bottom: 20px;
}

@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

/* Questions Display */
.questions-section {
    padding: 40px;
}

.stats-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    color: white;
    padding: 20px 30px;
    border-radius: 15px;
    margin-bottom: 30px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

.stat-item {
    text-align: center;
}

.stat-value {
    font-size: 32px;
    font-weight: 800;
    margin-bottom: 5px;
}

.stat-label {
    font-size: 14px;
    opacity: 0.9;
}

.questions-container {
    min-height: 400px;
}

.questions-grid {
    display: grid;
    gap: 25px;
}

.question-card {
    background: white;
    border-radius: 15px;
    padding: 30px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.08);
    border: 2px solid transparent;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
}

.question-card:hover {
    border-color: var(--primary);
    transform: translateY(-5px);
    box-shadow: 0 15px 35px rgba(0,0,0,0.12);
}

.question-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 5px;
    height: 100%;
    background: linear-gradient(to bottom, var(--primary), var(--secondary));
}

.question-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 25px;
    padding-bottom: 15px;
    border-bottom: 2px solid #f1f3f5;
}

.question-number {
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    color: white;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    font-size: 20px;
    box-shadow: 0 4px 10px rgba(67, 97, 238, 0.3);
}

.question-meta {
    display: flex;
    gap: 15px;
    align-items: center;
}

.question-type {
    background: #e9ecef;
    padding: 8px 20px;
    border-radius: 25px;
    font-size: 14px;
    font-weight: 600;
    color: #495057;
}

.difficulty {
    padding: 8px 20px;
    border-radius: 25px;
    font-size: 14px;
    font-weight: 600;
}

.difficulty-easy { background: #d4edda; color: #155724; }
.difficulty-medium { background: #fff3cd; color: #856404; }
.difficulty-hard { background: #f8d7da; color: #721c24; }

.question-text {
    font-size: 20px;
    line-height: 1.6;
    color: var(--dark);
    margin-bottom: 30px;
    font-weight: 500;
    padding-right: 10px;
}

.options-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 15px;
    margin: 25px 0;
}

.option {
    padding: 18px 25px;
    background: #f8f9fa;
    border-radius: 12px;
    border: 2px solid #e9ecef;
    transition: all 0.3s ease;
    cursor: pointer;
    font-size: 16px;
    display: flex;
    align-items: center;
    gap: 15px;
}

.option:hover {
    background: #e9ecef;
    transform: translateX(5px);
}

.option.correct {
    background: linear-gradient(135deg, #d4edda, #c3e6cb);
    border-color: #28a745;
    color: #155724;
}

.option-label {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: white;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    font-size: 18px;
    flex-shrink: 0;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

.option-a .option-label { color: #4361ee; }
.option-b .option-label { color: #f72585; }
.option-c .option-label { color: #4cc9f0; }
.option-d .option-label { color: #3a0ca3; }

.answer-section {
    margin-top: 25px;
    padding: 20px;
    background: linear-gradient(135deg, #e3f2fd, #bbdefb);
    border-radius: 12px;
    border-left: 5px solid #1976d2;
}

.answer-section h4 {
    color: #1976d2;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    gap: 10px;
}

.explanation {
    background: #fff3e0;
    padding: 20px;
    border-radius: 12px;
    margin-top: 20px;
    border-left: 5px solid #f57c00;
}

.explanation h4 {
    color: #f57c00;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    gap: 10px;
}

/* Response Info */
.response-info {
    background: linear-gradient(135deg, #f8f9fa, #e9ecef);
    padding: 30px;
    border-radius: 15px;
    margin-top: 40px;
    border: 2px solid #dee2e6;
}

.response-info h3 {
    color: var(--secondary);
    margin-bottom: 25px;
    font-size: 22px;
    display: flex;
    align-items: center;
    gap: 10px;
}

.response-stats {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
}

.stat-card {
    background: white;
    padding: 20px;
    border-radius: 12px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.05);
    text-align: center;
}

.stat-card .value {
    font-size: 28px;
    font-weight: 800;
    color: var(--primary);
    margin-bottom: 5px;
}

.stat-card .label {
    font-size: 14px;
    color: #6c757d;
    font-weight: 600;
}

/* Error State */
.error-state {
    text-align: center;
    padding: 80px 40px;
    background: white;
    border-radius: 15px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
}

.error-icon {
    font-size: 80px;
    color: #f72585;
    margin-bottom: 25px;
    animation: bounce 2s infinite;
}

@keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-20px); }
}

.error-state h3 {
    color: var(--dark);
    margin-bottom: 15px;
    font-size: 28px;
}

.error-state p {
    color: #6c757d;
    margin-bottom: 30px;
    font-size: 16px;
    line-height: 1.6;
}

/* Footer */
.footer {
    text-align: center;
    padding: 30px;
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    color: white;
}

.footer-content {
    max-width: 800px;
    margin: 0 auto;
}

.security-notice {
    background: rgba(255,255,255,0.1);
    padding: 15px;
    border-radius: 10px;
    margin-bottom: 20px;
    font-size: 14px;
}

.security-notice i {
    color: #ffdd00;
    margin-right: 10px;
}

/* Animations */
@keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

.fade-in {
    animation: fadeIn 0.5s ease forwards;
}

/* Responsive */
@media (max-width: 992px) {
    .header h1 {
        font-size: 32px;
    }
    
    .btn {
        min-width: 150px;
        padding: 12px 25px;
    }
    
    .question-text {
        font-size: 18px;
    }
    
    .options-grid {
        grid-template-columns: 1fr;
    }
}

@media (max-width: 576px) {
    .header {
        padding: 30px 20px;
    }
    
    .header h1 {
        font-size: 24px;
    }
    
    .api-config {
        padding: 20px;
    }
    
    .questions-section {
        padding: 20px;
    }
    
    .controls {
        flex-direction: column;
    }
    
    .btn {
        width: 100%;
    }
    
    .stats-bar {
        flex-direction: column;
        gap: 15px;
        text-align: center;
    }
}

/* Custom Scrollbar */
::-webkit-scrollbar {
    width: 10px;
}

::-webkit-scrollbar-track {
    background: #f1f1f1;
    border-radius: 5px;
}

::-webkit-scrollbar-thumb {
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    border-radius: 5px;
}

::-webkit-scrollbar-thumb:hover {
    background: linear-gradient(135deg, var(--secondary), var(--primary));
}
</style>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body>

<div class="container">
    <!-- Header -->
    <header class="header">
        <div class="header-content">
            <h1><i class="fas fa-graduation-cap"></i> نظام اختبار الرخصة الإنجليزية</h1>
            <p>توليد أسئلة احترافية لاختبار الرخصة باستخدام الذكاء الاصطناعي</p>
        </div>
    </header>

    <!-- API Configuration -->
    <section class="api-config">
        <div class="config-grid">
            <div class="config-card">
                <h3><i class="fas fa-key"></i> إعدادات OpenAI API</h3>
                <div class="form-group">
                    <label for="apiKey">🔑 مفتاح API الخاص بك:</label>
                    <input type="password" id="apiKey" class="form-control" 
                           placeholder="sk-... أدخل مفتاح OpenAI API الخاص بك">
                    <small style="color: #666; display: block; margin-top: 5px;">
                        احصل على المفتاح من <a href="https://platform.openai.com/api-keys" target="_blank">OpenAI Platform</a>
                    </small>
                </div>
            </div>
            
            <div class="config-card">
                <h3><i class="fas fa-cogs"></i> إعدادات التوليد</h3>
                <div class="form-group">
                    <label for="questionCount">📊 عدد الأسئلة:</label>
                    <select id="questionCount" class="form-control">
                        <option value="5">5 أسئلة</option>
                        <option value="10" selected>10 أسئلة</option>
                        <option value="15">15 أسئلة</option>
                        <option value="20">20 أسئلة</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="difficulty">📈 مستوى الصعوبة:</label>
                    <select id="difficulty" class="form-control">
                        <option value="easy">سهل</option>
                        <option value="medium" selected>متوسط</option>
                        <option value="hard">صعب</option>
                    </select>
                </div>
            </div>
        </div>

        <div class="controls">
            <button class="btn btn-primary" onclick="generateQuestions()" id="generateBtn">
                <i class="fas fa-magic"></i> توليد الأسئلة
            </button>
            <button class="btn btn-success" onclick="loadSampleQuestions()" id="sampleBtn">
                <i class="fas fa-eye"></i> عرض أمثلة
            </button>
            <button class="btn btn-warning" onclick="clearAll()" id="clearBtn">
                <i class="fas fa-trash"></i> مسح الكل
            </button>
        </div>
        
        <div class="loading" id="loadingIndicator">
            <div class="loader"></div>
            <p style="margin-top: 20px; color: #4361ee; font-weight: 600;">
                جاري توليد الأسئلة باستخدام الذكاء الاصطناعي...
            </p>
            <p style="color: #666; margin-top: 10px; font-size: 14px;">
                قد تستغرق العملية بضع ثوانٍ
            </p>
        </div>
    </section>

    <!-- Questions Display -->
    <section class="questions-section">
        <div class="stats-bar" id="statsBar" style="display: none;">
            <div class="stat-item">
                <div class="stat-value" id="totalQuestions">0</div>
                <div class="stat-label">إجمالي الأسئلة</div>
            </div>
            <div class="stat-item">
                <div class="stat-value" id="grammarCount">0</div>
                <div class="stat-label">أسئلة القواعد</div>
            </div>
            <div class="stat-item">
                <div class="stat-value" id="readingCount">0</div>
                <div class="stat-label">فهم القراءة</div>
            </div>
            <div class="stat-item">
                <div class="stat-value" id="vocabularyCount">0</div>
                <div class="stat-label">المفردات</div>
            </div>
        </div>

        <div class="questions-container">
            <div class="questions-grid" id="questionsGrid">
                <div class="empty-state" id="emptyState">
                    <div style="font-size: 100px; color: #dee2e6; margin-bottom: 20px;">
                        <i class="fas fa-file-alt"></i>
                    </div>
                    <h3 style="color: #6c757d; margin-bottom: 15px;">لا توجد أسئلة معروضة</h3>
                    <p style="color: #adb5bd; max-width: 500px; margin: 0 auto; line-height: 1.6;">
                        اضغط على زر "توليد الأسئلة" لإنشاء أسئلة احترافية لاختبار الرخصة الإنجليزية
                        باستخدام تقنية الذكاء الاصطناعي من OpenAI
                    </p>
                </div>
            </div>

            <div class="response-info" id="responseInfo" style="display: none;">
                <h3><i class="fas fa-chart-bar"></i> معلومات التوليد</h3>
                <div class="response-stats" id="responseStats"></div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="footer-content">
            <div class="security-notice">
                <i class="fas fa-shield-alt"></i>
                <strong>ملاحظة أمنية:</strong> مفتاح API لا يخزن على الخادم ويستخدم فقط في الجلسة الحالية
            </div>
            <p>© 2024 نظام اختبار الرخصة الإنجليزية | مصمم باستخدام OpenAI API</p>
            <p style="margin-top: 10px; font-size: 14px; opacity: 0.8;">
                <i class="fas fa-info-circle"></i>
                الأسئلة المولدة لأغراض تعليمية واختبارية فقط
            </p>
        </div>
    </footer>
</div>

<script>
// حالة التطبيق
const appState = {
    questions: [],
    stats: {
        total: 0,
        grammar: 0,
        reading: 0,
        vocabulary: 0
    }
};

// نماذج الأسئلة التجريبية
const SAMPLE_QUESTIONS = [
    {
        id: 1,
        type: "قواعد",
        difficulty: "medium",
        text: "Choose the correct sentence structure:",
        options: [
            { id: "a", text: "She go to work by bus every day." },
            { id: "b", text: "She goes to work by bus every day." },
            { id: "c", text: "She going to work by bus every day." },
            { id: "d", text: "She is go to work by bus every day." }
        ],
        correct_answer: "b",
        explanation: "With third person singular (she/he/it), we add 's' to the verb in present simple tense."
    },
    {
        id: 2,
        type: "فهم قراءة",
        difficulty: "easy",
        text: "Read the following email excerpt: 'Please submit the quarterly report by Friday EOD. The meeting with stakeholders is scheduled for next Monday.' When is the deadline for the report?",
        options: [
            { id: "a", text: "Next Monday" },
            { id: "b", text: "Friday end of day" },
            { id: "c", text: "Tomorrow" },
            { id: "d", text: "End of this month" }
        ],
        correct_answer: "b",
        explanation: "EOD stands for 'End of Day', so the deadline is Friday end of day."
    },
    {
        id: 3,
        type: "مفردات",
        difficulty: "hard",
        text: "What is the meaning of 'to leverage' in a business context?",
        options: [
            { id: "a", text: "To avoid something" },
            { id: "b", text: "To use something to maximum advantage" },
            { id: "c", text: "To reduce costs" },
            { id: "d", text: "To delegate tasks" }
        ],
        correct_answer: "b",
        explanation: "In business, 'to leverage' means to use something (like resources or relationships) to gain an advantage."
    }
];

// توليد الأسئلة باستخدام OpenAI API
async function generateQuestions() {
    const apiKey = document.getElementById('apiKey').value.trim();
    const questionCount = document.getElementById('questionCount').value;
    const difficulty = document.getElementById('difficulty').value;
    
    if (!apiKey) {
        showError('⚠️ يرجى إدخال مفتاح OpenAI API');
        return;
    }
    
    if (!apiKey.startsWith('sk-')) {
        showError('❌ مفتاح API غير صحيح. يجب أن يبدأ بـ sk-');
        return;
    }
    
    // تعطيل الأزرار أثناء التحميل
    document.getElementById('generateBtn').disabled = true;
    document.getElementById('sampleBtn').disabled = true;
    document.getElementById('clearBtn').disabled = true;
    
    // إظهار مؤشر التحميل
    document.getElementById('loadingIndicator').classList.add('active');
    document.getElementById('emptyState').style.display = 'none';
    
    const startTime = Date.now();
    
    try {
        // إعداد الطلب لـ OpenAI API
        const prompt = `Generate ${questionCount} professional English test questions for a license exam.
Difficulty level: ${difficulty}.
Include these types:
- Grammar questions (verb tenses, prepositions, sentence structure)
- Reading comprehension (short business texts)
- Vocabulary (business and professional terms)

For each question, provide:
1. Question text in English
2. 4 multiple choice options (labeled a, b, c, d)
3. Correct answer (a, b, c, or d)
4. Brief explanation in English

Format the response as a JSON array with this structure:
[
  {
    "type": "grammar|reading|vocabulary",
    "difficulty": "easy|medium|hard",
    "text": "question text",
    "options": {
      "a": "option text",
      "b": "option text",
      "c": "option text",
      "d": "option text"
    },
    "correct_answer": "a",
    "explanation": "explanation text"
  }
]`;

        const response = await fetch("https://api.openai.com/v1/chat/completions", {
            method: "POST",
            headers: {
                "Content-Type": "application/json",
                "Authorization": `Bearer ${apiKey}`
            },
            body: JSON.stringify({
                model: "gpt-3.5-turbo",
                messages: [
                    {
                        role: "system",
                        content: "You are an English language testing expert. Generate professional test questions in JSON format only."
                    },
                    {
                        role: "user",
                        content: prompt
                    }
                ],
                temperature: 0.7,
                max_tokens: 2000
            })
        });

        if (!response.ok) {
            const errorData = await response.json();
            throw new Error(`OpenAI API Error: ${errorData.error?.message || response.statusText}`);
        }

        const data = await response.json();
        const endTime = Date.now();
        const responseTime = endTime - startTime;
        
        let questions;
        try {
            // محاولة استخراج JSON من الرد
            const content = data.choices[0].message.content;
            const jsonMatch = content.match(/\[[\s\S]*\]/);
            
            if (jsonMatch) {
                questions = JSON.parse(jsonMatch[0]);
            } else {
                // إذا لم يكن JSON، استخدام النص كأسئلة
                questions = parseTextToQuestions(content);
            }
        } catch (parseError) {
            console.error('Parse error:', parseError);
            questions = parseTextToQuestions(data.choices[0].message.content);
        }
        
        // حفظ الأسئلة وتحديث الإحصائيات
        appState.questions = questions;
        updateStatistics();
        
        // عرض الأسئلة
        displayQuestions();
        
        // عرض معلومات الاستجابة
        showResponseInfo(responseTime, data.usage);
        
    } catch (error) {
        console.error('Error:', error);
        showError(`❌ خطأ في توليد الأسئلة: ${error.message}`);
        
        // عرض الأسئلة التجريبية كبديل
        setTimeout(() => {
            if (confirm('فشل الاتصال بـ OpenAI. هل تريد عرض أسئلة تجريبية بدلاً من ذلك؟')) {
                loadSampleQuestions();
            }
        }, 1000);
    } finally {
        // إعادة تفعيل الأزرار
        document.getElementById('generateBtn').disabled = false;
        document.getElementById('sampleBtn').disabled = false;
        document.getElementById('clearBtn').disabled = false;
        document.getElementById('loadingIndicator').classList.remove('active');
    }
}

// تحويل النص إلى كائنات أسئلة
function parseTextToQuestions(text) {
    const lines = text.split('\n').filter(line => line.trim());
    const questions = [];
    let currentQuestion = null;
    
    for (const line of lines) {
        if (line.match(/^\d+[\.\)]/)) {
            // سؤال جديد
            if (currentQuestion) {
                questions.push(currentQuestion);
            }
            currentQuestion = {
                type: "general",
                difficulty: "medium",
                text: line.replace(/^\d+[\.\)]\s*/, ''),
                options: {},
                correct_answer: "",
                explanation: ""
            };
        } else if (line.match(/^[a-d][\.\)]/i)) {
            // خيار
            const match = line.match(/^([a-d])[\.\)]\s*(.+)/i);
            if (match && currentQuestion) {
                const [, letter, optionText] = match;
                currentQuestion.options[letter.toLowerCase()] = optionText.trim();
            }
        } else if (line.toLowerCase().includes('correct') || line.includes('✓')) {
            // إجابة صحيحة
            if (currentQuestion) {
                const match = line.match(/[a-d]/i);
                if (match) {
                    currentQuestion.correct_answer = match[0].toLowerCase();
                }
            }
        } else if (line.toLowerCase().includes('explanation') || questions.length > 0) {
            // شرح
            if (currentQuestion && !currentQuestion.explanation) {
                currentQuestion.explanation = line.replace(/^(explanation|شرح)[:\s]*/i, '');
            }
        }
    }
    
    if (currentQuestion) {
        questions.push(currentQuestion);
    }
    
    return questions.slice(0, 10); // الحد الأقصى 10 أسئلة
}

// عرض الأسئلة
function displayQuestions() {
    const questionsGrid = document.getElementById('questionsGrid');
    
    if (!appState.questions || appState.questions.length === 0) {
        questionsGrid.innerHTML = `
            <div class="empty-state">
                <div style="font-size: 100px; color: #dee2e6;">
                    <i class="fas fa-exclamation-circle"></i>
                </div>
                <h3 style="color: #6c757d;">لا توجد أسئلة لعرضها</h3>
            </div>
        `;
        return;
    }
    
    let html = '';
    
    appState.questions.forEach((question, index) => {
        const options = question.options || {};
        const optionLetters = ['a', 'b', 'c', 'd'];
        
        html += `
            <div class="question-card fade-in">
                <div class="question-header">
                    <div class="question-number">${index + 1}</div>
                    <div class="question-meta">
                        <span class="question-type">${getArabicType(question.type)}</span>
                        <span class="difficulty difficulty-${question.difficulty || 'medium'}">
                            ${getArabicDifficulty(question.difficulty)}
                        </span>
                    </div>
                </div>
                
                <div class="question-text">${question.text}</div>
                
                <div class="options-grid">
                    ${optionLetters.map(letter => `
                        <div class="option option-${letter} ${question.correct_answer === letter ? 'correct' : ''}">
                            <div class="option-label">${letter.toUpperCase()}</div>
                            <div class="option-text">${options[letter] || ''}</div>
                        </div>
                    `).join('')}
                </div>
                
                ${question.correct_answer ? `
                    <div class="answer-section">
                        <h4><i class="fas fa-check-circle"></i> الإجابة الصحيحة</h4>
                        <p><strong>${question.correct_answer.toUpperCase()})</strong> ${options[question.correct_answer] || ''}</p>
                    </div>
                ` : ''}
                
                ${question.explanation ? `
                    <div class="explanation">
                        <h4><i class="fas fa-lightbulb"></i> الشرح</h4>
                        <p>${question.explanation}</p>
                    </div>
                ` : ''}
            </div>
        `;
    });
    
    questionsGrid.innerHTML = html;
    
    // إظهار شريط الإحصائيات
    document.getElementById('statsBar').style.display = 'flex';
}

// تحديث الإحصائيات
function updateStatistics() {
    if (!appState.questions) return;
    
    const stats = {
        total: appState.questions.length,
        grammar: 0,
        reading: 0,
        vocabulary: 0
    };
    
    appState.questions.forEach(question => {
        const type = question.type?.toLowerCase();
        if (type.includes('grammar')) stats.grammar++;
        else if (type.includes('reading')) stats.reading++;
        else if (type.includes('vocabulary')) stats.vocabulary++;
        else stats.grammar++; // افتراضي
    });
    
    appState.stats = stats;
    
    // تحديث الواجهة
    document.getElementById('totalQuestions').textContent = stats.total;
    document.getElementById('grammarCount').textContent = stats.grammar;
    document.getElementById('readingCount').textContent = stats.reading;
    document.getElementById('vocabularyCount').textContent = stats.vocabulary;
}

// عرض معلومات الاستجابة
function showResponseInfo(responseTime, usage) {
    const responseInfo = document.getElementById('responseInfo');
    const responseStats = document.getElementById('responseStats');
    
    responseInfo.style.display = 'block';
    
    responseStats.innerHTML = `
        <div class="stat-card">
            <div class="value">${responseTime}ms</div>
            <div class="label">وقت الاستجابة</div>
        </div>
        ${usage ? `
        <div class="stat-card">
            <div class="value">${usage.prompt_tokens}</div>
            <div class="label">Tokens المستخدمة</div>
        </div>
        <div class="stat-card">
            <div class="value">${usage.completion_tokens}</div>
            <div class="label">Tokens المولدة</div>
        </div>
        <div class="stat-card">
            <div class="value">${usage.total_tokens}</div>
            <div class="label">إجمالي Tokens</div>
        </div>
        ` : ''}
    `;
}

// تحميل الأسئلة التجريبية
function loadSampleQuestions() {
    appState.questions = SAMPLE_QUESTIONS;
    updateStatistics();
    displayQuestions();
    
    // إخفاء حالة التحميل إذا كانت ظاهرة
    document.getElementById('loadingIndicator').classList.remove('active');
    document.getElementById('emptyState').style.display = 'none';
    
    // إظهار رسالة
    showMessage('✅ تم تحميل الأسئلة التجريبية بنجاح', 'success');
}

// مسح الكل
function clearAll() {
    if (confirm('هل أنت متأكد من مسح جميع الأسئلة والإعدادات؟')) {
        appState.questions = [];
        appState.stats = { total: 0, grammar: 0, reading: 0, vocabulary: 0 };
        
        document.getElementById('apiKey').value = '';
        document.getElementById('questionsGrid').innerHTML = `
            <div class="empty-state" id="emptyState">
                <div style="font-size: 100px; color: #dee2e6;">
                    <i class="fas fa-file-alt"></i>
                </div>
                <h3 style="color: #6c757d;">لا توجد أسئلة معروضة</h3>
                <p style="color: #adb5bd;">قم بتوليد أسئلة جديدة للبدء</p>
            </div>
        `;
        
        document.getElementById('statsBar').style.display = 'none';
        document.getElementById('responseInfo').style.display = 'none';
        
        showMessage('🧹 تم مسح جميع البيانات', 'info');
    }
}

// دوال مساعدة
function getArabicType(type) {
    const typeMap = {
        'grammar': 'قواعد',
        'reading': 'فهم قراءة',
        'vocabulary': 'مفردات',
        'general': 'عام'
    };
    return typeMap[type.toLowerCase()] || type;
}

function getArabicDifficulty(difficulty) {
    const diffMap = {
        'easy': 'سهل',
        'medium': 'متوسط',
        'hard': 'صعب'
    };
    return diffMap[difficulty] || difficulty;
}

function showError(message) {
    const questionsGrid = document.getElementById('questionsGrid');
    questionsGrid.innerHTML = `
        <div class="error-state">
            <div class="error-icon">
                <i class="fas fa-exclamation-triangle"></i>
            </div>
            <h3>حدث خطأ</h3>
            <p>${message}</p>
            <button onclick="loadSampleQuestions()" class="btn btn-success" style="margin-top: 20px;">
                <i class="fas fa-eye"></i> عرض أسئلة تجريبية
            </button>
        </div>
    `;
}

function showMessage(message, type = 'info') {
    // إنشاء عنصر الرسالة
    const messageDiv = document.createElement('div');
    messageDiv.className = `message ${type}`;
    messageDiv.style.cssText = `
        position: fixed;
        top: 20px;
        right: 20px;
        background: ${type === 'success' ? '#d4edda' : type === 'error' ? '#f8d7da' : '#fff3cd'};
        color: ${type === 'success' ? '#155724' : type === 'error' ? '#721c24' : '#856404'};
        padding: 15px 25px;
        border-radius: 10px;
        border-left: 5px solid ${type === 'success' ? '#28a745' : type === 'error' ? '#dc3545' : '#ffc107'};
        z-index: 1000;
        box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        animation: slideIn 0.3s ease;
    `;
    
    messageDiv.innerHTML = `
        <i class="fas fa-${type === 'success' ? 'check-circle' : type === 'error' ? 'exclamation-circle' : 'info-circle'}"></i>
        ${message}
    `;
    
    document.body.appendChild(messageDiv);
    
    // إزالة الرسالة بعد 3 ثوانٍ
    setTimeout(() => {
        messageDiv.style.animation = 'slideOut 0.3s ease';
        setTimeout(() => {
            if (messageDiv.parentNode) {
                messageDiv.parentNode.removeChild(messageDiv);
            }
        }, 300);
    }, 3000);
}

// إضافة أنماط CSS للرسائل المتحركة
const style = document.createElement('style');
style.textContent = `
@keyframes slideIn {
    from { transform: translateX(100%); opacity: 0; }
    to { transform: translateX(0); opacity: 1; }
}

@keyframes slideOut {
    from { transform: translateX(0); opacity: 1; }
    to { transform: translateX(100%); opacity: 0; }
}
`;
document.head.appendChild(style);

// إضافة مستمع للأخطاء العامة
window.addEventListener('error', function(e) {
    console.error('Global error:', e.error);
    showError('حدث خطأ غير متوقع في التطبيق');
});

// تهيئة التطبيق
document.addEventListener('DOMContentLoaded', function() {
    // إضافة تأثيرات للعناصر
    const cards = document.querySelectorAll('.config-card');
    cards.forEach((card, index) => {
        card.style.animationDelay = `${index * 0.1}s`;
    });
});
</script>
</body>
</html>
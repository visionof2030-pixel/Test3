
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>أداة إعداد التقارير التعليمية</title>

<style>
:root {
  --primary-color: #0a3b40;
  --secondary-color: #1a7a80;
  --accent-color: #2ea4ab;
  --light-bg: #f5fbfb;
  --light-green: #e8f5f3;
  --light-blue: #e8f0f7;
  --border-color: #d0e6e4;
  --success-color: #2e7d32;
  --warning-color: #e6b800;
  --error-color: #c62828;
  --text-dark: #1a3c40;
  --text-light: #5a7a7d;
  --shadow: 0 8px 25px rgba(10, 59, 64, 0.08);
  --radius: 12px;
  --transition: all 0.3s ease;
}

* {
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Arial, sans-serif;
  background: linear-gradient(135deg, #eef7f5 0%, #f5f9fa 100%);
  margin: 0;
  padding: 25px;
  color: var(--text-dark);
  line-height: 1.6;
  min-height: 100vh;
}

.container {
  max-width: 1000px;
  margin: 0 auto;
  background: white;
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  overflow: hidden;
}

.tool {
  padding: 30px;
}

.header {
  background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
  color: white;
  padding: 25px 30px;
  text-align: center;
  border-bottom: 4px solid var(--accent-color);
}

.header h1 {
  margin: 0 0 10px;
  font-size: 28px;
  font-weight: 700;
}

.header p {
  margin: 0;
  opacity: 0.9;
  font-size: 16px;
}

.tool-section {
  margin-bottom: 30px;
  padding-bottom: 25px;
  border-bottom: 1px solid var(--border-color);
}

.tool-section:last-of-type {
  border-bottom: none;
}

.section-title {
  color: var(--primary-color);
  font-size: 20px;
  margin-bottom: 20px;
  padding-bottom: 10px;
  border-bottom: 2px solid var(--light-green);
  position: relative;
}

.section-title:after {
  content: '';
  position: absolute;
  bottom: -2px;
  right: 0;
  width: 70px;
  height: 2px;
  background: var(--accent-color);
}

label {
  font-weight: 600;
  margin-top: 15px;
  margin-bottom: 8px;
  display: block;
  color: var(--text-dark);
}

input, textarea, select {
  width: 100%;
  padding: 12px 15px;
  margin-top: 5px;
  border-radius: 8px;
  border: 1px solid var(--border-color);
  font-size: 15px;
  transition: var(--transition);
  background-color: #fdfdfd;
  font-family: 'Segoe UI', Tahoma, Arial, sans-serif;
}

input:focus, textarea:focus, select:focus {
  outline: none;
  border-color: var(--accent-color);
  box-shadow: 0 0 0 3px rgba(42, 164, 171, 0.1);
}

textarea {
  min-height: 100px;
  resize: vertical;
}

.small-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 15px;
  margin-top: 10px;
}

@media (max-width: 768px) {
  .small-grid {
    grid-template-columns: 1fr;
    gap: 15px;
  }
}

.auto-row {
  display: flex;
  gap: 10px;
  margin-top: 10px;
  flex-wrap: wrap;
}

.auto-btn {
  flex: 1;
  background: var(--light-green);
  border: 1px solid var(--secondary-color);
  color: var(--primary-color);
  font-size: 13px;
  padding: 10px;
  border-radius: 6px;
  cursor: pointer;
  transition: var(--transition);
  font-weight: 500;
  min-width: 100px;
}

.auto-btn:hover {
  background: var(--secondary-color);
  color: white;
}

.clear-btn {
  background: #fff5f5;
  border: 1px solid var(--error-color);
  color: var(--error-color);
}

.clear-btn:hover {
  background: var(--error-color);
  color: white;
}

.checkbox-label {
  display: flex;
  align-items: center;
  gap: 8px;
  font-weight: 600;
  margin-top: 15px;
  cursor: pointer;
}

.checkbox-label input {
  width: auto;
  margin-top: 0;
}

.images-section {
  border: 2px dashed var(--border-color);
  border-radius: var(--radius);
  padding: 20px;
  text-align: center;
  margin-top: 15px;
  background-color: var(--light-bg);
}

.images-section:hover {
  border-color: var(--accent-color);
}

.images-section label {
  cursor: pointer;
  color: var(--secondary-color);
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  font-size: 16px;
}

.images-section input[type="file"] {
  display: none;
}

.images-preview {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 15px;
  margin-top: 20px;
}

.images-preview img {
  width: 100%;
  height: 180px;
  object-fit: cover;
  border-radius: 8px;
  border: 1px solid var(--border-color);
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
}

.export-btn {
  background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
  color: white;
  border: none;
  border-radius: var(--radius);
  padding: 16px;
  font-size: 17px;
  font-weight: 600;
  cursor: pointer;
  transition: var(--transition);
  margin-top: 25px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.export-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 15px rgba(10, 59, 64, 0.2);
}

.export-btn:active {
  transform: translateY(0);
}

.footer-note {
  text-align: center;
  margin-top: 20px;
  font-size: 14px;
  color: var(--text-light);
  padding: 15px;
  border-top: 1px solid var(--border-color);
}

/* ===== التقرير للطباعة ===== */
.report {
  display: none;
}

@media print {
  body {
    background: white;
    padding: 0;
    font-size: 12pt;
  }
  
  .container, .tool {
    display: none;
  }
  
  .report {
    display: block;
    width: 100%;
    padding: 15px;
  }
  
  .header {
    background: var(--primary-color);
    color: white;
    text-align: center;
    padding: 10px;
    margin-bottom: 10px;
    font-size: 14pt;
    border-radius: 0;
    border-bottom: 3px solid var(--accent-color);
  }
  
  .header .hijri {
    font-size: 11pt;
    margin-top: 5px;
  }
  
  .top-info {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    margin-bottom: 12px;
  }
  
  .box {
    border: 1px solid #ccc;
    padding: 8px;
    text-align: center;
    font-size: 11pt;
    border-radius: 5px;
    background-color: #f9f9f9;
  }
  
  .goal-section {
    background: #e8f5e9;
    border: 2px solid var(--success-color);
    padding: 10px;
    margin-bottom: 12px;
    border-radius: 6px;
  }
  
  .goal-section strong {
    color: #1b5e20;
    display: block;
    border-bottom: 1px solid var(--success-color);
    margin-bottom: 6px;
    font-size: 13pt;
  }
  
  .section {
    border: 1px solid #ccc;
    padding: 10px;
    font-size: 11pt;
    border-radius: 5px;
    margin-bottom: 8px;
  }
  
  .section strong {
    display: block;
    border-bottom: 1px solid var(--primary-color);
    margin-bottom: 5px;
    font-size: 12pt;
  }
  
  .grid2 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-bottom: 12px;
  }
  
  .optional {
    background: #fff8cc;
    border: 1px dashed var(--warning-color);
  }
  
  .images {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-top: 12px;
  }
  
  .images img {
    width: 100%;
    height: 180px;
    object-fit: cover;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .signatures {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
    margin-top: 40px;
    font-size: 11pt;
  }
  
  .signatures div {
    text-align: center;
  }
  
  .line {
    border-bottom: 1px dashed #000;
    height: 1px;
    margin-top: 20px;
    width: 80%;
    margin-left: auto;
    margin-right: auto;
  }
}

/* تحسينات للشاشات الصغيرة */
@media (max-width: 768px) {
  body {
    padding: 15px;
  }
  
  .tool {
    padding: 20px;
  }
  
  .header {
    padding: 20px 15px;
  }
  
  .header h1 {
    font-size: 24px;
  }
  
  .section-title {
    font-size: 18px;
  }
  
  .auto-row {
    flex-direction: column;
  }
  
  .auto-btn {
    width: 100%;
  }
  
  .images-preview {
    grid-template-columns: 1fr;
  }
}

/* تأثيرات إضافية */
select, input[type="text"], input[type="number"] {
  background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%230a3b40' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3e%3cpolyline points='6 9 12 15 18 9'%3e%3c/polyline%3e%3c/svg%3e");
  background-repeat: no-repeat;
  background-position: left 15px center;
  background-size: 16px;
  padding-left: 45px;
}

/* تأثيرات التركيز */
.input-group {
  position: relative;
  margin-bottom: 20px;
}

.input-group input, .input-group select, .input-group textarea {
  width: 100%;
}

.input-group label {
  position: absolute;
  top: -10px;
  right: 12px;
  background: white;
  padding: 0 8px;
  font-size: 13px;
  color: var(--secondary-color);
}

/* رسائل التوجيه */
.hint {
  font-size: 13px;
  color: var(--text-light);
  margin-top: 5px;
  display: block;
}

/* حالة التحميل */
.loading {
  display: inline-block;
  width: 20px;
  height: 20px;
  border: 3px solid rgba(255,255,255,.3);
  border-radius: 50%;
  border-top-color: white;
  animation: spin 1s ease-in-out infinite;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}
</style>
</head>

<body>
<div class="container">
  <div class="header">
    <h1>أداة إعداد التقارير التعليمية</h1>
    <p>أداة متكاملة لإعداد التقارير التربوية بصيغة PDF مع الحفاظ على التصميم الأصلي</p>
  </div>
  
  <div class="tool">
    <div class="tool-section">
      <div class="section-title">المعلومات الأساسية</div>
      
      <label>إدارة التعليم</label>
      <select onchange="sync('edu',this.value)" class="form-select">
        <option value="">اختر إدارة التعليم</option>
        <option>الإدارة العامة للتعليم بمنطقة مكة المكرمة</option>
        <option>الإدارة العامة للتعليم بمنطقة الرياض</option>
        <option>الإدارة العامة للتعليم بمنطقة المدينة المنورة</option>
        <option>الإدارة العامة للتعليم بالمنطقة الشرقية</option>
        <option>الإدارة العامة للتعليم بمنطقة القصيم</option>
        <option>الإدارة العامة للتعليم بمنطقة عسير</option>
        <option>الإدارة العامة للتعليم بمنطقة تبوك</option>
        <option>الإدارة العامة للتعليم بمنطقة حائل</option>
        <option>الإدارة العامة للتعليم بمنطقة الحدود الشمالية</option>
        <option>الإدارة العامة للتعليم بمنطقة جازان</option>
        <option>الإدارة العامة للتعليم بمنطقة نجران</option>
        <option>الإدارة العامة للتعليم بمنطقة الباحة</option>
        <option>الإدارة العامة للتعليم بمنطقة الجوف</option>
        <option>الإدارة العامة للتعليم بمحافظة الأحساء</option>
        <option>الإدارة العامة للتعليم بمحافظة الطائف</option>
        <option>الإدارة العامة للتعليم بمحافظة جدة</option>
      </select>
      
      <label>اسم المدرسة</label>
      <input type="text" oninput="sync('school',this.value)" placeholder="أدخل اسم المدرسة">
    </div>
    
    <div class="tool-section">
      <div class="section-title">تفاصيل التقرير</div>
      
      <div class="small-grid">
        <div class="input-group">
          <label>المعيار التربوي</label>
          <select id="axisSelect" onchange="updateReports()">
            <option value="">اختر المعيار التربوي</option>
            <option value="improve">تحسين نواتج التعلم</option>
            <option value="strategies">استراتيجيات التدريس والتعلم</option>
          </select>
        </div>
        
        <div class="input-group">
          <label>التقرير التربوي</label>
          <select id="reportSelect" disabled onchange="syncReport()">
            <option value="">اختر التقرير</option>
          </select>
        </div>
        
        <div class="input-group">
          <label>المستفيدون</label>
          <input type="text" placeholder="المستفيدون" oninput="sync('target',this.value)">
        </div>
        
        <div class="input-group">
          <label>عدد المستفيدين</label>
          <input type="number" placeholder="عدد المستفيدين" oninput="sync('count',this.value)">
        </div>
      </div>
    </div>
    
    <div class="tool-section">
      <div class="section-title">محتوى التقرير</div>
      
      <!-- الحقول الديناميكية -->
      <div id="fields"></div>
    </div>
    
    <div class="tool-section">
      <div class="section-title">المرفقات والتوقيعات</div>
      
      <label>إرفاق الصور (حد أقصى صورتين)</label>
      <div class="images-section">
        <label for="imageUpload">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
            <circle cx="8.5" cy="8.5" r="1.5"></circle>
            <polyline points="21 15 16 10 5 21"></polyline>
          </svg>
          انقر لرفع الصور
        </label>
        <input type="file" id="imageUpload" multiple accept="image/*" onchange="loadImages(this)">
        <span class="hint">يمكنك رفع صورتين كحد أقصى</span>
        
        <div class="images-preview" id="imagesPreview"></div>
      </div>
      
      <div class="small-grid">
        <div class="input-group">
          <label>اسم المعلم</label>
          <input type="text" oninput="sync('teacher',this.value)" placeholder="اسم المعلم">
        </div>
        
        <div class="input-group">
          <label>اسم مدير المدرسة</label>
          <input type="text" oninput="sync('principal',this.value)" placeholder="اسم مدير المدرسة">
        </div>
      </div>
    </div>
    
    <button class="export-btn" onclick="window.print()">
      <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
        <polyline points="7 10 12 15 17 10"></polyline>
        <line x1="12" y1="15" x2="12" y2="3"></line>
      </svg>
      تصدير PDF
    </button>
    
    <div class="footer-note">
      سيظهر التقرير في صفحة الطباعة بصيغة PDF جاهزة للتحميل
    </div>
  </div>
</div>

<!-- قسم التقرير للطباعة -->
<div class="report">
  <div class="header">
    <div id="edu"></div>
    <div id="school"></div>
    <div id="hijriDate" class="hijri"></div>
  </div>

  <div class="top-info">
    <div class="box"><strong>المعيار</strong><div id="axis"></div></div>
    <div class="box"><strong>التقرير</strong><div id="reportTitle"></div></div>
    <div class="box"><strong>المستفيدون</strong><div id="target"></div></div>
    <div class="box"><strong>العدد</strong><div id="count"></div></div>
  </div>

  <div class="goal-section"><strong>الهدف التربوي</strong><div id="goal"></div></div>

  <div class="grid2">
    <div class="section"><strong>وصف مختصر</strong><div id="desc1"></div></div>
    <div class="section"><strong>إجراءات التنفيذ</strong><div id="desc2"></div></div>
  </div>

  <div class="grid2">
    <div class="section"><strong>النتائج</strong><div id="desc3"></div></div>
    <div class="section"><strong>التوصيات</strong><div id="desc4"></div></div>
  </div>

  <div class="grid2">
    <div class="section optional" id="challengesBox"><strong>التحديات</strong><div id="challenges"></div></div>
    <div class="section optional" id="strengthsBox"><strong>نقاط القوة</strong><div id="strengths"></div></div>
  </div>

  <div class="images" id="imagesBox"></div>

  <div class="signatures">
    <div><div id="teacher"></div><div class="line"></div>توقيع المعلم</div>
    <div><div id="principal"></div><div class="line"></div>توقيع مدير المدرسة</div>
  </div>
</div>

<script>
// البيانات الأساسية
const fields = [
  ['goal', 'الهدف التربوي'],
  ['desc1', 'وصف مختصر'],
  ['desc2', 'إجراءات التنفيذ'],
  ['desc3', 'النتائج'],
  ['desc4', 'التوصيات'],
  ['challenges', 'التحديات'],
  ['strengths', 'نقاط القوة']
];

const data = {
  improve: {
    "تقرير نشاط إثرائي": {
      goal: [
        "تنمية مهارات التفكير العليا ورفع مستوى التحصيل الدراسي لدى الطلاب.",
        "تعزيز قدرات الطلاب المعرفية وتنمية مهارات التعلم الذاتي.",
        "دعم التفوق الدراسي وتنمية الإبداع لدى الطلاب."
      ],
      desc1: [
        "أنشطة تعليمية إثرائية داعمة لتنمية المهارات المعرفية.",
        "برامج إثرائية مكملة للمحتوى الدراسي.",
        "أنشطة تعليمية إضافية لتنمية الفهم العميق."
      ],
      desc2: [
        "تنفيذ أنشطة منظمة وفق خطة زمنية محددة.",
        "تطبيق برامج إثرائية باستخدام استراتيجيات متنوعة.",
        "متابعة التنفيذ وتقويم الأداء بشكل دوري."
      ],
      desc3: [
        "تحسن ملحوظ في مستوى التحصيل الدراسي.",
        "زيادة دافعية الطلاب للتعلم.",
        "ارتفاع مستوى المشاركة الصفية."
      ],
      desc4: [
        "الاستمرار في تنفيذ البرامج الإثرائية.",
        "تطوير الأنشطة وفق احتياجات الطلاب.",
        "توسيع نطاق الأنشطة التعليمية."
      ],
      challenges: [
        "ضيق الوقت الدراسي.",
        "تفاوت مستويات الطلاب.",
        "محدودية الموارد التعليمية."
      ],
      strengths: [
        "دعم الإدارة المدرسية.",
        "تفاعل الطلاب الإيجابي.",
        "كفاءة الكادر التعليمي."
      ]
    }
  }
};

// عرض الحقول الديناميكية
function renderFields() {
  const fieldsBox = document.getElementById('fields');
  fieldsBox.innerHTML = '';
  
  fields.forEach(f => {
    const fieldId = f[0];
    const fieldLabel = f[1];
    
    const fieldHTML = `
      <div class="input-group">
        <label>${fieldLabel}</label>
        <textarea id="${fieldId}Input" oninput="sync('${fieldId}', this.value)" placeholder="أدخل ${fieldLabel}"></textarea>
        <div class="auto-row">
          <button class="auto-btn" onclick="fill('${fieldId}',0)">نص مقترح 1</button>
          <button class="auto-btn" onclick="fill('${fieldId}',1)">نص مقترح 2</button>
          <button class="auto-btn" onclick="fill('${fieldId}',2)">نص مقترح 3</button>
          <button class="auto-btn clear-btn" onclick="clearText('${fieldId}')">مسح النص</button>
        </div>
      </div>`;
    
    fieldsBox.innerHTML += fieldHTML;
  });
}

// تحديث التقارير بناءً على المحور المختار
function updateReports() {
  const reportSelect = document.getElementById('reportSelect');
  const axisSelect = document.getElementById('axisSelect');
  
  reportSelect.innerHTML = '<option value="">اختر التقرير</option>';
  reportSelect.disabled = !axisSelect.value;
  
  if (!axisSelect.value) return;
  
  // تحديث النص المعروض للمعيار
  sync('axis', axisSelect.options[axisSelect.selectedIndex].text);
  
  // ملء خيارات التقارير
  if (data[axisSelect.value]) {
    Object.keys(data[axisSelect.value]).forEach(r => {
      reportSelect.innerHTML += `<option value="${r}">${r}</option>`;
    });
  }
  
  // تمكين التحديد
  reportSelect.disabled = false;
}

// مزامنة التقرير المختار
function syncReport() {
  const reportSelect = document.getElementById('reportSelect');
  sync('reportTitle', reportSelect.value);
}

// تعبئة الحقل بنص مقترح
function fill(k, i) {
  const axisSelect = document.getElementById('axisSelect');
  const reportSelect = document.getElementById('reportSelect');
  
  if (!axisSelect.value || !reportSelect.value) {
    alert('يرجى اختيار المعيار والتقرير أولاً');
    return;
  }
  
  const textData = data[axisSelect.value][reportSelect.value][k];
  
  if (textData && textData[i]) {
    document.getElementById(k + 'Input').value = textData[i];
    sync(k, textData[i]);
    
    // إضافة تأثير بسيط
    const field = document.getElementById(k + 'Input');
    field.style.backgroundColor = 'var(--light-green)';
    setTimeout(() => {
      field.style.backgroundColor = '';
    }, 500);
  }
}

// مسح نص الحقل
function clearText(k) {
  document.getElementById(k + 'Input').value = '';
  sync(k, '');
}

// مزامنة البيانات بين الواجهة والتقرير
function sync(id, v) {
  const element = document.getElementById(id);
  if (element) {
    element.textContent = v;
  }
}

// تحميل الصور وعرض معاينتها
function loadImages(input) {
  const imagesBox = document.getElementById('imagesBox');
  const imagesPreview = document.getElementById('imagesPreview');
  
  imagesBox.innerHTML = '';
  imagesPreview.innerHTML = '';
  
  const files = Array.from(input.files).slice(0, 2);
  
  if (files.length === 0) return;
  
  files.forEach(f => {
    const reader = new FileReader();
    
    reader.onload = function(e) {
      // إضافة الصورة لمعاينة الواجهة
      const previewImg = document.createElement('img');
      previewImg.src = e.target.result;
      previewImg.alt = 'معاينة الصورة';
      imagesPreview.appendChild(previewImg);
      
      // إضافة الصورة للتقرير
      const reportImg = document.createElement('img');
      reportImg.src = e.target.result;
      reportImg.alt = 'صورة التقرير';
      imagesBox.appendChild(reportImg);
    };
    
    reader.readAsDataURL(f);
  });
}

// تحميل التاريخ الهجري
async function loadHijri() {
  const d = new Date();
  const day = String(d.getDate()).padStart(2, '0');
  const month = String(d.getMonth() + 1).padStart(2, '0');
  const year = d.getFullYear();
  
  try {
    const res = await fetch(`https://api.aladhan.com/v1/gToH/${day}-${month}-${year}`);
    const j = await res.json();
    
    if (j.data && j.data.hijri) {
      const hijriDate = document.getElementById('hijriDate');
      hijriDate.textContent = `${j.data.hijri.day} ${j.data.hijri.month.ar} ${j.data.hijri.year} هـ`;
    }
  } catch (error) {
    console.log('تعذر تحميل التاريخ الهجري:', error);
    const hijriDate = document.getElementById('hijriDate');
    hijriDate.textContent = 'التاريخ الهجري غير متوفر حاليًا';
  }
}

// تهيئة الصفحة عند التحميل
document.addEventListener('DOMContentLoaded', () => {
  renderFields();
  loadHijri();
  
  // إضافة مؤشر تاريخ الميلادي
  const today = new Date();
  const options = { year: 'numeric', month: 'long', day: 'numeric' };
  const gregorianDate = today.toLocaleDateString('ar-SA', options);
  
  // إضافة تعليمات للمستخدم
  console.log('أهلاً بك في أداة إعداد التقارير التعليمية');
  console.log('تاريخ اليوم الميلادي: ' + gregorianDate);
});

// تحديث التاريخ الهجري قبل الطباعة
window.onbeforeprint = loadHijri;

// إضافة رسالة تأكيد عند محاولة الخروج
window.addEventListener('beforeunload', (e) => {
  const inputs = document.querySelectorAll('input, textarea');
  let hasData = false;
  
  inputs.forEach(input => {
    if (input.value.trim() !== '') {
      hasData = true;
    }
  });
  
  if (hasData) {
    e.preventDefault();
    e.returnValue = 'لديك بيانات غير محفوظة. هل أنت متأكد من المغادرة؟';
  }
});
</script>
</body>
</html>
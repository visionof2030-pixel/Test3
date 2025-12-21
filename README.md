<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>أداة إعداد التقارير التعليمية</title>

<style>
* {
  box-sizing: border-box;
}

body {
  font-family: Tahoma, Arial, sans-serif;
  background: #eef7f5;
  margin: 0;
  padding: 15px;
  min-height: 100vh;
}

.tool {
  max-width: 900px;
  margin: auto;
  background: white;
  padding: 20px;
  border-radius: 16px;
  box-shadow: 0 10px 25px rgba(0,0,0,.1);
}

.tool h2 {
  text-align: center;
  color: #0a3b40;
  margin-bottom: 25px;
  font-size: 1.4rem;
}

label {
  font-weight: 700;
  margin-top: 15px;
  display: block;
  color: #333;
}

input, textarea, select {
  width: 100%;
  padding: 12px;
  margin-top: 8px;
  border-radius: 8px;
  border: 1px solid #ccc;
  font-size: 16px;
  font-family: inherit;
}

textarea {
  resize: none;
  min-height: 100px;
}

/* تحسين التنسيق للشاشات الصغيرة */
@media (max-width: 768px) {
  body {
    padding: 10px;
  }
  
  .tool {
    padding: 15px;
  }
  
  .tool h2 {
    font-size: 1.2rem;
  }
  
  input, textarea, select {
    padding: 10px;
    font-size: 15px;
  }
}

/* الشبكة للعناصر الصغيرة */
.small-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 12px;
  margin: 15px 0;
}

@media (max-width: 480px) {
  .small-grid {
    grid-template-columns: 1fr;
    gap: 10px;
  }
}

.auto-row {
  display: flex;
  gap: 8px;
  margin-top: 8px;
  flex-wrap: wrap;
}

.auto-btn {
  flex: 1;
  min-width: 70px;
  background: #e0f2f1;
  border: 1px solid #0a3b40;
  color: #0a3b40;
  font-size: 13px;
  padding: 8px 5px;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.3s;
}

.auto-btn:hover {
  background: #b2dfdb;
}

.clear-btn {
  background: #fdecea;
  border: 1px solid #c62828;
  color: #c62828;
}

.clear-btn:hover {
  background: #ffcdd2;
}

/* خيارات الاختيار */
.checkbox-container {
  display: flex;
  align-items: center;
  gap: 10px;
  margin: 15px 0;
  padding: 12px;
  background: #f8f9fa;
  border-radius: 8px;
  border: 1px solid #ddd;
}

.checkbox-container input[type="checkbox"] {
  width: 20px;
  height: 20px;
  margin: 0;
  cursor: pointer;
}

.checkbox-container label {
  margin: 0;
  font-size: 16px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 8px;
}

.checkbox-label {
  display: flex;
  align-items: center;
  gap: 8px;
  font-weight: 700;
  margin-top: 10px;
}

button {
  margin-top: 20px;
  padding: 15px;
  width: 100%;
  background: #0a3b40;
  color: white;
  border: none;
  border-radius: 10px;
  font-size: 16px;
  cursor: pointer;
  transition: background 0.3s;
  font-weight: bold;
}

button:hover {
  background: #084148;
}

/* ===== التقرير ===== */
.report {
  display: none;
}

@media print {
  body {
    background: white;
    padding: 0;
    margin: 0;
    font-size: 12pt;
  }
  
  .tool {
    display: none !important;
  }
  
  .report {
    display: block;
    width: 100%;
    max-width: 100%;
    padding: 10px;
  }
  
  .header {
    background: #0a3b40;
    color: white;
    text-align: center;
    padding: 10px;
    margin-bottom: 10px;
    font-size: 14px;
    page-break-inside: avoid;
  }
  
  .header .hijri {
    font-size: 12px;
    margin-top: 4px;
    opacity: 0.9;
  }
  
  .top-info {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 8px;
    margin-bottom: 10px;
    page-break-inside: avoid;
  }
  
  @media print and (max-width: 800px) {
    .top-info {
      grid-template-columns: repeat(2, 1fr);
    }
  }
  
  @media print and (max-width: 500px) {
    .top-info {
      grid-template-columns: 1fr;
    }
  }
  
  .box {
    border: 1px solid #ccc;
    padding: 8px;
    text-align: center;
    font-size: 11pt;
    page-break-inside: avoid;
  }
  
  .goal-section {
    background: #e8f5e9;
    border: 2px solid #2e7d32;
    padding: 10px;
    margin-bottom: 10px;
    page-break-inside: avoid;
  }
  
  .goal-section strong {
    color: #1b5e20;
    display: block;
    border-bottom: 1px solid #2e7d32;
    margin-bottom: 6px;
    font-size: 13pt;
  }
  
  .section {
    border: 1px solid #ccc;
    padding: 8px;
    font-size: 11pt;
    margin-bottom: 8px;
    page-break-inside: avoid;
  }
  
  .section strong {
    display: block;
    border-bottom: 1px solid #0a3b40;
    margin-bottom: 5px;
    font-size: 12pt;
  }
  
  .grid2 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-bottom: 10px;
  }
  
  @media print and (max-width: 600px) {
    .grid2 {
      grid-template-columns: 1fr;
    }
  }
  
  .optional {
    background: #fff8cc;
    border: 1px dashed #e6b800;
  }
  
  .optional.hidden {
    display: none !important;
  }
  
  .images {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-top: 10px;
    page-break-inside: avoid;
  }
  
  .images.hidden {
    display: none !important;
  }
  
  @media print and (max-width: 500px) {
    .images {
      grid-template-columns: 1fr;
    }
  }
  
  .images img {
    width: 100%;
    height: 180px;
    object-fit: cover;
    border: 1px solid #ccc;
  }
  
  .signatures {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 30px;
    margin-top: 20px;
    font-size: 10pt;
    page-break-inside: avoid;
  }
  
  @media print and (max-width: 500px) {
    .signatures {
      grid-template-columns: 1fr;
      gap: 20px;
    }
  }
  
  .signatures div {
    text-align: center;
  }
  
  .line {
    border-bottom: 1px dashed #000;
    height: 15px;
    margin-top: 5px;
    width: 80%;
    margin-left: auto;
    margin-right: auto;
  }
  
  /* إخفاء العناصر غير المطلوبة */
  .no-print {
    display: none !important;
  }
}

/* تحسين المظهر العام للشاشات الصغيرة */
@media (max-width: 480px) {
  .checkbox-container {
    flex-direction: column;
    align-items: flex-start;
    gap: 8px;
  }
  
  .checkbox-container label {
    font-size: 14px;
  }
  
  .auto-btn {
    font-size: 12px;
    padding: 6px 4px;
    min-width: 60px;
  }
}
</style>
</head>

<body>

<div class="tool">
<h2>أداة إعداد التقارير التعليمية</h2>

<label>إدارة التعليم</label>
<select onchange="sync('edu',this.value)">
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
<input oninput="sync('school',this.value)">

<div class="small-grid">
<select id="axisSelect" onchange="updateReports()">
<option value="">المعيار التربوي</option>
<option value="improve">تحسين نواتج التعلم</option>
<option value="strategies">استراتيجيات التدريس والتعلم</option>
</select>

<select id="reportSelect" disabled onchange="syncReport()">
<option value="">التقرير التربوي</option>
</select>

<input placeholder="المستفيدون" oninput="sync('target',this.value)">
<input placeholder="عدد المستفيدين" oninput="sync('count',this.value)">
</div>

<!-- ===== الحقول ===== -->
<div id="fields"></div>

<!-- خيارات الاختيار -->
<div class="checkbox-container">
  <input type="checkbox" id="includeChallenges" checked onchange="toggleOptionalField('challenges')">
  <label for="includeChallenges">✅ تضمين "التحديات" في التقرير</label>
</div>

<div class="checkbox-container">
  <input type="checkbox" id="includeStrengths" checked onchange="toggleOptionalField('strengths')">
  <label for="includeStrengths">✅ تضمين "نقاط القوة" في التقرير</label>
</div>

<div class="checkbox-container">
  <input type="checkbox" id="includeImages" checked onchange="toggleImages()">
  <label for="includeImages">✅ تضمين الصور في التقرير</label>
</div>

<label>إرفاق الصور (حد أقصى صورتين)</label>
<input type="file" multiple accept="image/*" onchange="loadImages(this)">

<label>اسم المعلم</label>
<input oninput="sync('teacher',this.value)">

<label>اسم مدير المدرسة</label>
<input oninput="sync('principal',this.value)">

<button onclick="preparePrint()">تصدير PDF / طباعة</button>
</div>

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

let uploadedImages = [];

function renderFields() {
  const fieldsBox = document.getElementById('fields');
  fields.forEach(f => {
    const fieldId = f[0];
    const fieldLabel = f[1];
    
    fieldsBox.innerHTML += `
      <label for="${fieldId}Input">${fieldLabel}</label>
      <textarea id="${fieldId}Input" oninput="sync('${fieldId}', this.value)"></textarea>
      <div class="auto-row">
        <button class="auto-btn" onclick="fill('${fieldId}', 0)">نص 1</button>
        <button class="auto-btn" onclick="fill('${fieldId}', 1)">نص 2</button>
        <button class="auto-btn" onclick="fill('${fieldId}', 2)">نص 3</button>
        <button class="auto-btn clear-btn" onclick="clearText('${fieldId}')">مسح النص</button>
      </div>`;
  });
}

function updateReports() {
  const reportSelect = document.getElementById('reportSelect');
  const axisSelect = document.getElementById('axisSelect');
  
  reportSelect.innerHTML = '<option value="">التقرير التربوي</option>';
  reportSelect.disabled = !axisSelect.value;
  
  if (!axisSelect.value) return;
  
  Object.keys(data[axisSelect.value]).forEach(r => {
    reportSelect.innerHTML += `<option>${r}</option>`;
  });
  
  sync('axis', axisSelect.options[axisSelect.selectedIndex].text);
}

function syncReport() {
  const reportSelect = document.getElementById('reportSelect');
  sync('reportTitle', reportSelect.value);
}

function fill(k, i) {
  const axisSelect = document.getElementById('axisSelect');
  const reportSelect = document.getElementById('reportSelect');
  
  if (!axisSelect.value || !reportSelect.value) {
    alert('يرجى اختيار المعيار والتقرير أولاً');
    return;
  }
  
  const text = data[axisSelect.value][reportSelect.value][k][i];
  document.getElementById(k + 'Input').value = text;
  sync(k, text);
}

function clearText(k) {
  document.getElementById(k + 'Input').value = '';
  sync(k, '');
}

function sync(id, v) {
  const element = document.getElementById(id);
  if (element) {
    element.textContent = v;
  }
}

function toggleOptionalField(fieldName) {
  const checkbox = document.getElementById('include' + fieldName.charAt(0).toUpperCase() + fieldName.slice(1));
  const fieldBox = document.getElementById(fieldName + 'Box');
  
  if (checkbox.checked) {
    fieldBox.classList.remove('hidden');
  } else {
    fieldBox.classList.add('hidden');
  }
}

function toggleImages() {
  const checkbox = document.getElementById('includeImages');
  const imagesBox = document.getElementById('imagesBox');
  
  if (checkbox.checked) {
    imagesBox.classList.remove('hidden');
  } else {
    imagesBox.classList.add('hidden');
  }
}

function loadImages(input) {
  const imagesBox = document.getElementById('imagesBox');
  imagesBox.innerHTML = '';
  uploadedImages = [];
  
  const files = Array.from(input.files).slice(0, 2);
  
  if (files.length === 0) {
    imagesBox.innerHTML = '<p style="text-align:center; color:#666; padding:10px;">لم يتم رفع أي صور</p>';
    return;
  }
  
  files.forEach((f, index) => {
    const reader = new FileReader();
    reader.onload = e => {
      const img = document.createElement('img');
      img.src = e.target.result;
      img.alt = `صورة ${index + 1}`;
      imagesBox.appendChild(img);
      uploadedImages.push(e.target.result);
    };
    reader.readAsDataURL(f);
  });
}

async function loadHijri() {
  const d = new Date();
  const day = String(d.getDate()).padStart(2, '0');
  const month = String(d.getMonth() + 1).padStart(2, '0');
  const year = d.getFullYear();
  
  try {
    const res = await fetch(`https://api.aladhan.com/v1/gToH/${day}-${month}-${year}`);
    const j = await res.json();
    const hijriDate = document.getElementById('hijriDate');
    hijriDate.textContent = `${j.data.hijri.day} ${j.data.hijri.month.ar} ${j.data.hijri.year} هـ`;
  } catch {
    const hijriDate = document.getElementById('hijriDate');
    hijriDate.textContent = 'التاريخ الهجري غير متوفر';
  }
}

function preparePrint() {
  // تحديث خيارات العرض قبل الطباعة
  toggleOptionalField('challenges');
  toggleOptionalField('strengths');
  toggleImages();
  
  // تحديث التاريخ الهجري
  loadHijri();
  
  // الانتظار قليلاً قبل الطباعة لضمان تحديث العناصر
  setTimeout(() => {
    window.print();
  }, 100);
}

document.addEventListener('DOMContentLoaded', () => {
  renderFields();
  loadHijri();
});

window.onbeforeprint = loadHijri;
</script>

</body>
</html>
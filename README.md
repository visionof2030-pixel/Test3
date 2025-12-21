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

body{
  font-family:Tahoma,Arial,sans-serif;
  background:#eef7f5;
  margin:0;
  padding:15px;
  min-height:100vh;
}

.tool{
  max-width:900px;
  margin:auto;
  background:white;
  padding:20px;
  border-radius:16px;
  box-shadow:0 10px 25px rgba(0,0,0,.1);
}

.tool h2{
  text-align:center;
  color:#0a3b40;
  margin-top:0;
  font-size:1.5rem;
}

label{
  font-weight:700;
  margin-top:15px;
  display:block;
  color:#0a3b40;
  font-size:0.95rem;
}

input,textarea,select{
  width:100%;
  padding:10px;
  margin-top:6px;
  border-radius:8px;
  border:1px solid #ccc;
  font-size:0.95rem;
  background:#fff;
}

textarea{
  resize:none;
  min-height:80px;
}

.small-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit, minmax(200px, 1fr));
  gap:12px;
  margin-top:10px;
}

.auto-row{
  display:flex;
  flex-wrap:wrap;
  gap:8px;
  margin-top:8px;
}

.auto-btn{
  flex:1;
  min-width:80px;
  background:#e0f2f1;
  border:1px solid #0a3b40;
  color:#0a3b40;
  font-size:0.85rem;
  padding:8px 5px;
  border-radius:6px;
  cursor:pointer;
  transition:all 0.3s;
}

.auto-btn:hover{
  background:#b2dfdb;
}

.clear-btn{
  background:#fdecea;
  border:1px solid #c62828;
  color:#c62828;
}

.clear-btn:hover{
  background:#ffcdd2;
}

.optional-toggle{
  display:flex;
  align-items:center;
  gap:10px;
  margin:15px 0 8px;
  padding:10px;
  background:#f8f9fa;
  border-radius:8px;
  border:1px solid #ddd;
}

.optional-toggle input{
  width:auto;
  margin:0;
  transform:scale(1.2);
}

.optional-toggle label{
  margin:0;
  cursor:pointer;
  display:flex;
  align-items:center;
  gap:8px;
  font-weight:700;
}

button{
  margin-top:20px;
  padding:14px;
  width:100%;
  background:#0a3b40;
  color:white;
  border:none;
  border-radius:10px;
  font-size:1rem;
  cursor:pointer;
  transition:background 0.3s;
  font-weight:bold;
}

button:hover{
  background:#0d5058;
}

/* ===== التقرير ===== */
.report{display:none}

@media print{
  body{background:white;padding:0}
  .tool{display:none}
  .report{display:block}
  
  .header{
    background:#0a3b40;
    color:white;
    text-align:center;
    padding:8px;
    margin-bottom:8px;
    font-size:12px;
  }
  
  .header .hijri{
    font-size:11px;
    margin-top:4px;
  }
  
  .top-info{
    display:grid;
    grid-template-columns:repeat(4,1fr);
    gap:8px;
    margin-bottom:10px;
  }
  
  .box{
    border:1px solid #ccc;
    padding:6px;
    text-align:center;
    font-size:11pt;
    min-height:50px;
    display:flex;
    flex-direction:column;
    justify-content:center;
  }
  
  .goal-section{
    background:#e8f5e9;
    border:2px solid #2e7d32;
    padding:8px;
    margin-bottom:10px;
    page-break-inside:avoid;
  }
  
  .goal-section strong{
    color:#1b5e20;
    display:block;
    border-bottom:1px solid #2e7d32;
    margin-bottom:6px;
    padding-bottom:4px;
  }
  
  .section{
    border:1px solid #ccc;
    padding:8px;
    font-size:11pt;
    min-height:120px;
    page-break-inside:avoid;
  }
  
  .section strong{
    display:block;
    border-bottom:1px solid #0a3b40;
    margin-bottom:6px;
    padding-bottom:4px;
  }
  
  .grid2{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:10px;
    margin-bottom:10px;
  }
  
  .optional{
    background:#fff8cc;
    border:1px dashed #e6b800;
  }
  
  .images{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:10px;
    margin-top:15px;
    page-break-inside:avoid;
  }
  
  .images img{
    width:100%;
    height:180px;
    object-fit:cover;
    border:1px solid #ccc;
  }
  
  .signatures{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:40px;
    margin-top:20px;
    font-size:10pt;
    page-break-inside:avoid;
  }
  
  .signatures div{
    text-align:center;
  }
  
  .line{
    border-bottom:1px dashed #000;
    height:20px;
    margin-top:5px;
  }
}

/* ===== تجاوب مع الشاشات الصغيرة ===== */
@media (max-width: 768px) {
  .small-grid{
    grid-template-columns:1fr;
  }
  
  .grid2{
    grid-template-columns:1fr !important;
    gap:15px;
  }
  
  .top-info{
    grid-template-columns:repeat(2, 1fr) !important;
  }
  
  .images{
    grid-template-columns:1fr !important;
  }
  
  .signatures{
    grid-template-columns:1fr !important;
    gap:25px;
  }
  
  .tool{
    padding:15px;
  }
  
  .auto-row{
    flex-direction:column;
  }
  
  .auto-btn{
    width:100%;
  }
}

@media (max-width: 480px) {
  .top-info{
    grid-template-columns:1fr !important;
  }
  
  body{
    padding:10px;
  }
  
  .tool{
    padding:12px;
  }
  
  .tool h2{
    font-size:1.3rem;
  }
  
  input,textarea,select{
    padding:8px;
    font-size:0.9rem;
  }
}

/* تلميح للطباعة */
.print-hint{
  background:#fff3cd;
  border:1px solid #ffc107;
  color:#856404;
  padding:10px;
  border-radius:8px;
  margin:15px 0;
  text-align:center;
  font-size:0.9rem;
}
</style>
</head>

<body>

<div class="tool">
<h2>أداة إعداد التقارير التعليمية</h2>

<div class="print-hint">
  ⓘ للحصول على أفضل نتيجة عند التصدير لـ PDF، استخدم إعدادات الطباعة: <br>
  الهوامش → لا شيء | خيارات → خلفية الرسومات
</div>

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
<input placeholder="عدد المستفيدين" type="number" oninput="sync('count',this.value)">
</div>

<!-- ===== الحقول ===== -->
<div id="fields"></div>

<!-- خيارات اختيارية -->
<div class="optional-toggle">
  <input type="checkbox" id="includeChallenges" checked>
  <label for="includeChallenges">✅ تضمين "التحديات" في التقرير</label>
</div>

<div class="optional-toggle">
  <input type="checkbox" id="includeStrengths" checked>
  <label for="includeStrengths">✅ تضمين "نقاط القوة" في التقرير</label>
</div>

<label>إرفاق الصور (حد أقصى صورتين)</label>
<input type="file" multiple accept="image/*" onchange="loadImages(this)">

<label>اسم المعلم</label>
<input oninput="sync('teacher',this.value)">

<label>اسم مدير المدرسة</label>
<input oninput="sync('principal',this.value)">

<button onclick="generatePDF()">تصدير PDF</button>
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

<div class="grid2" id="optionalFields">
<!-- سيتم إضافة الحقول الاختيارية هنا ديناميكيًا -->
</div>

<div class="images" id="imagesBox"></div>

<div class="signatures">
<div><div id="teacher"></div><div class="line"></div>توقيع المعلم</div>
<div><div id="principal"></div><div class="line"></div>توقيع مدير المدرسة</div>
</div>
</div>

<script>
const fields=[
 ['goal','الهدف التربوي'],
 ['desc1','وصف مختصر'],
 ['desc2','إجراءات التنفيذ'],
 ['desc3','النتائج'],
 ['desc4','التوصيات'],
 ['challenges','التحديات'],
 ['strengths','نقاط القوة']
];

const data={
 improve:{
  "تقرير نشاط إثرائي":{
   goal:[
    "تنمية مهارات التفكير العليا ورفع مستوى التحصيل الدراسي لدى الطلاب.",
    "تعزيز قدرات الطلاب المعرفية وتنمية مهارات التعلم الذاتي.",
    "دعم التفوق الدراسي وتنمية الإبداع لدى الطلاب."
   ],
   desc1:[
    "أنشطة تعليمية إثرائية داعمة لتنمية المهارات المعرفية.",
    "برامج إثرائية مكملة للمحتوى الدراسي.",
    "أنشطة تعليمية إضافية لتنمية الفهم العميق."
   ],
   desc2:[
    "تنفيذ أنشطة منظمة وفق خطة زمنية محددة.",
    "تطبيق برامج إثرائية باستخدام استراتيجيات متنوعة.",
    "متابعة التنفيذ وتقويم الأداء بشكل دوري."
   ],
   desc3:[
    "تحسن ملحوظ في مستوى التحصيل الدراسي.",
    "زيادة دافعية الطلاب للتعلم.",
    "ارتفاع مستوى المشاركة الصفية."
   ],
   desc4:[
    "الاستمرار في تنفيذ البرامج الإثرائية.",
    "تطوير الأنشطة وفق احتياجات الطلاب.",
    "توسيع نطاق الأنشطة التعليمية."
   ],
   challenges:[
    "ضيق الوقت الدراسي.",
    "تفاوت مستويات الطلاب.",
    "محدودية الموارد التعليمية."
   ],
   strengths:[
    "دعم الإدارة المدرسية.",
    "تفاعل الطلاب الإيجابي.",
    "كفاءة الكادر التعليمي."
   ]
  }
 }
};

// عناصر HTML
let optionalFieldsContainer;

function renderFields(){
 const fieldsBox = document.getElementById('fields');
 fieldsBox.innerHTML = '';
 
 fields.forEach(f=>{
  if(f[0] !== 'challenges' && f[0] !== 'strengths') {
   fieldsBox.innerHTML += `
    <label>${f[1]}</label>
    <textarea id="${f[0]}Input" oninput="sync('${f[0]}',this.value)"></textarea>
    <div class="auto-row">
     <button class="auto-btn" onclick="fill('${f[0]}',0)">نص 1</button>
     <button class="auto-btn" onclick="fill('${f[0]}',1)">نص 2</button>
     <button class="auto-btn" onclick="fill('${f[0]}',2)">نص 3</button>
     <button class="auto-btn clear-btn" onclick="clearText('${f[0]}')">مسح النص</button>
    </div>`;
  } else {
   // الحقول الاختيارية
   fieldsBox.innerHTML += `
    <label>${f[1]}</label>
    <textarea id="${f[0]}Input" oninput="sync('${f[0]}',this.value)"></textarea>
    <div class="auto-row">
     <button class="auto-btn" onclick="fill('${f[0]}',0)">نص 1</button>
     <button class="auto-btn" onclick="fill('${f[0]}',1)">نص 2</button>
     <button class="auto-btn" onclick="fill('${f[0]}',2)">نص 3</button>
     <button class="auto-btn clear-btn" onclick="clearText('${f[0]}')">مسح النص</button>
    </div>`;
  }
 });
 
 // تهيئة حاوية الحقول الاختيارية للتقرير
 optionalFieldsContainer = document.getElementById('optionalFields');
 updateOptionalFields();
}

function updateOptionalFields() {
  optionalFieldsContainer.innerHTML = '';
  
  if(document.getElementById('includeChallenges').checked) {
    optionalFieldsContainer.innerHTML += `
      <div class="section optional">
        <strong>التحديات</strong>
        <div id="challenges"></div>
      </div>
    `;
  }
  
  if(document.getElementById('includeStrengths').checked) {
    optionalFieldsContainer.innerHTML += `
      <div class="section optional">
        <strong>نقاط القوة</strong>
        <div id="strengths"></div>
      </div>
    `;
  }
  
  // إذا كان هناك حقل واحد فقط محدد، نجعل الشبكة عمود واحد
  const checkedCount = 
    (document.getElementById('includeChallenges').checked ? 1 : 0) +
    (document.getElementById('includeStrengths').checked ? 1 : 0);
    
  if(checkedCount === 1) {
    optionalFieldsContainer.classList.remove('grid2');
    optionalFieldsContainer.style.gridTemplateColumns = '1fr';
  } else {
    optionalFieldsContainer.classList.add('grid2');
  }
}

function updateReports(){
 const reportSelect = document.getElementById('reportSelect');
 reportSelect.innerHTML='<option value="">التقرير التربوي</option>';
 reportSelect.disabled=!axisSelect.value;
 if(!axisSelect.value) return;
 Object.keys(data[axisSelect.value]).forEach(r=>{
  reportSelect.innerHTML+=`<option>${r}</option>`;
 });
 sync('axis',axisSelect.options[axisSelect.selectedIndex].text);
}

function syncReport(){
 const reportSelect = document.getElementById('reportSelect');
 sync('reportTitle',reportSelect.value);
}

function fill(k,i){
 const axisSelect = document.getElementById('axisSelect');
 const reportSelect = document.getElementById('reportSelect');
 if(!axisSelect.value || !reportSelect.value) {
   alert('يرجى اختيار المعيار والتقرير أولاً');
   return;
 }
 const t = data[axisSelect.value][reportSelect.value][k][i];
 document.getElementById(k+'Input').value = t;
 sync(k,t);
}

function clearText(k){
 document.getElementById(k+'Input').value='';
 sync(k,'');
}

function sync(id,v){
 const element = document.getElementById(id);
 if(element) {
   element.textContent = v;
 }
}

function loadImages(input){
 const imagesBox = document.getElementById('imagesBox');
 imagesBox.innerHTML='';
 
 // إضافة صور جديدة (حد أقصى صورتين)
 Array.from(input.files).slice(0,2).forEach(f=>{
   const reader = new FileReader();
   reader.onload = function(e){
     const img = document.createElement('img');
     img.src = e.target.result;
     img.alt = 'صورة النشاط';
     imagesBox.appendChild(img);
   };
   reader.readAsDataURL(f);
 });
 
 // إذا لم تكن هناك صور، نضيف رسالة
 if(input.files.length === 0) {
   imagesBox.innerHTML = '<div style="text-align:center; padding:20px; color:#666;">لا توجد صور مرفقة</div>';
 }
}

async function loadHijri(){
 const d = new Date();
 const day = String(d.getDate()).padStart(2,'0');
 const month = String(d.getMonth()+1).padStart(2,'0');
 const year = d.getFullYear();
 try{
   const res = await fetch(`https://api.aladhan.com/v1/gToH/${day}-${month}-${year}`);
   const j = await res.json();
   document.getElementById('hijriDate').textContent = `${j.data.hijri.day} ${j.data.hijri.month.ar} ${j.data.hijri.year} هـ`;
 } catch {
   document.getElementById('hijriDate').textContent = 'التاريخ الهجري غير متوفر';
 }
}

function generatePDF() {
  // تحديث الحقول الاختيارية قبل الطباعة
  updateOptionalFields();
  
  // تحديث التاريخ الهجري
  loadHijri();
  
  // الانتظار قليلاً ثم الطباعة
  setTimeout(() => {
    window.print();
  }, 500);
}

document.addEventListener('DOMContentLoaded',()=>{
  window.fieldsBox = document.getElementById('fields');
  window.axisSelect = document.getElementById('axisSelect');
  window.reportSelect = document.getElementById('reportSelect');
  
  renderFields();
  loadHijri();
  
  // إضافة مستمعين للأزرار الاختيارية
  document.getElementById('includeChallenges').addEventListener('change', updateOptionalFields);
  document.getElementById('includeStrengths').addEventListener('change', updateOptionalFields);
});

// تحديث التاريخ عند الطباعة
window.onbeforeprint = loadHijri;
</script>

</body>
</html>
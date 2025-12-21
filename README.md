<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<title>أداة إعداد التقارير التعليمية</title>

<style>
body{
  font-family:Tahoma,Arial,sans-serif;
  background:#eef7f5;
  margin:0;
  padding:20px;
}

.tool{
  max-width:900px;
  margin:auto;
  background:white;
  padding:22px;
  border-radius:16px;
  box-shadow:0 10px 25px rgba(0,0,0,.1);
}

.tool h2{text-align:center;color:#0a3b40}

label{font-weight:700;margin-top:10px;display:block}

input,textarea,select{
  width:100%;
  padding:9px;
  margin-top:5px;
  border-radius:8px;
  border:1px solid #ccc;
  font-size:14px;
}

textarea{resize:none}

.small-grid{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:8px;
}

.auto-row{
  display:flex;
  gap:6px;
  margin-top:4px;
}

.auto-btn{
  flex:1;
  background:#e0f2f1;
  border:1px solid #0a3b40;
  color:#0a3b40;
  font-size:12px;
  padding:5px;
  border-radius:6px;
  cursor:pointer;
}

.clear-btn{
  background:#fdecea;
  border:1px solid #c62828;
  color:#c62828;
}

button{
  margin-top:14px;
  padding:11px;
  width:100%;
  background:#0a3b40;
  color:white;
  border:none;
  border-radius:10px;
  font-size:14px;
  cursor:pointer;
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
  padding:6px;
  margin-bottom:6px;
  font-size:11px;
}

.header .hijri{font-size:10px;margin-top:2px}

.top-info{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:5px;
  margin-bottom:6px;
}

.box{
  border:1px solid #ccc;
  padding:4px;
  text-align:center;
  font-size:10pt;
}

/* ===== الهدف التربوي (محسن بدون كسر الهيكل) ===== */
.goal-section{
  background:#e8f5e9;
  border:2px solid #2e7d32;
  padding:14px 12px;
  margin-bottom:10px;
  line-height:1.9;
  page-break-inside:avoid;
}

.goal-section strong{
  color:#1b5e20;
  display:block;
  border-bottom:1px solid #2e7d32;
  margin-bottom:6px;
}

/* ===== باقي الأقسام ===== */
.section{
  border:1px solid #ccc;
  padding:5px;
  font-size:10.5pt;
  page-break-inside:avoid;
}

.section strong{
  display:block;
  border-bottom:1px solid #0a3b40;
  margin-bottom:3px;
}

.grid2{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:5px;
  margin-bottom:5px;
}

.optional{
  background:#fff8cc;
  border:1px dashed #e6b800;
}

.images{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:6px;
  margin-top:6px;
  page-break-inside:avoid;
}

.images img{
  width:100%;
  height:170px;
  object-fit:cover;
  border:1px solid #ccc;
}

.signatures{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:18px;
  margin-top:10px;
  font-size:9pt;
  page-break-inside:avoid;
}

.signatures div{text-align:center}

.line{
  border-bottom:1px dashed #000;
  height:12px;
  margin-top:3px;
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

<div id="fields"></div>

<label>إرفاق الصور (حد أقصى صورتين)</label>
<input type="file" multiple accept="image/*" onchange="loadImages(this)">

<label>اسم المعلم</label>
<input oninput="sync('teacher',this.value)">

<label>اسم مدير المدرسة</label>
<input oninput="sync('principal',this.value)">

<button onclick="window.print()">تصدير PDF</button>
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

<div class="goal-section">
<strong>الهدف التربوي</strong>
<div id="goal"></div>
</div>

<div class="grid2">
<div class="section"><strong>وصف مختصر</strong><div id="desc1"></div></div>
<div class="section"><strong>إجراءات التنفيذ</strong><div id="desc2"></div></div>
</div>

<div class="grid2">
<div class="section"><strong>النتائج</strong><div id="desc3"></div></div>
<div class="section"><strong>التوصيات</strong><div id="desc4"></div></div>
</div>

<div class="grid2">
<div class="section optional"><strong>التحديات</strong><div id="challenges"></div></div>
<div class="section optional"><strong>نقاط القوة</strong><div id="strengths"></div></div>
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

function renderFields(){
 const fieldsBox=document.getElementById('fields');
 fieldsBox.innerHTML='';
 fields.forEach(f=>{
  fieldsBox.innerHTML+=`
   <label>${f[1]}</label>
   <textarea id="${f[0]}Input"></textarea>
   <div class="auto-row">
    <button class="auto-btn" onclick="fill('${f[0]}',0)">نص 1</button>
    <button class="auto-btn" onclick="fill('${f[0]}',1)">نص 2</button>
    <button class="auto-btn" onclick="fill('${f[0]}',2)">نص 3</button>
    <button class="auto-btn clear-btn" onclick="clearText('${f[0]}')">مسح النص</button>
   </div>`;
 });
}

function updateReports(){
 const axisSelect=document.getElementById('axisSelect');
 const reportSelect=document.getElementById('reportSelect');
 reportSelect.innerHTML='<option value="">التقرير التربوي</option>';
 reportSelect.disabled=!axisSelect.value;
 if(!axisSelect.value)return;
 Object.keys(data[axisSelect.value]).forEach(r=>{
  reportSelect.innerHTML+=`<option>${r}</option>`;
 });
 document.getElementById('axis').textContent=axisSelect.options[axisSelect.selectedIndex].text;
}

function syncReport(){
 document.getElementById('reportTitle').textContent=document.getElementById('reportSelect').value;
}

function fill(k,i){
 const axis=document.getElementById('axisSelect').value;
 const report=document.getElementById('reportSelect').value;
 if(!axis||!report)return;
 const t=data[axis][report][k][i];
 document.getElementById(k+'Input').value=t;
 document.getElementById(k).textContent=t;
}

function clearText(k){
 document.getElementById(k+'Input').value='';
 document.getElementById(k).textContent='';
}

function sync(id,v){
 const el=document.getElementById(id);
 if(el)el.textContent=v;
}

function loadImages(input){
 const box=document.getElementById('imagesBox');
 box.innerHTML='';
 [...input.files].slice(0,2).forEach(f=>{
  const r=new FileReader();
  r.onload=e=>{
   const img=document.createElement('img');
   img.src=e.target.result;
   box.appendChild(img);
  };
  r.readAsDataURL(f);
 });
}

async function loadHijri(){
 const d=new Date();
 const day=String(d.getDate()).padStart(2,'0');
 const month=String(d.getMonth()+1).padStart(2,'0');
 const year=d.getFullYear();
 try{
  const res=await fetch(`https://api.aladhan.com/v1/gToH/${day}-${month}-${year}`);
  const j=await res.json();
  document.getElementById('hijriDate').textContent=
   `${j.data.hijri.day} ${j.data.hijri.month.ar} ${j.data.hijri.year} هـ`;
 }catch{
  document.getElementById('hijriDate').textContent='التاريخ الهجري غير متوفر';
 }
}

document.addEventListener('DOMContentLoaded',()=>{
 renderFields();
 loadHijri();
});
window.onbeforeprint=loadHijri;
</script>

</body>
</html>
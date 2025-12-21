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

label{
  font-weight:700;
  margin-top:14px;
  display:block;
}

input,textarea,select{
  width:100%;
  padding:9px;
  margin-top:6px;
  border-radius:8px;
  border:1px solid #ccc;
  font-size:14px;
}

textarea{resize:none}

.section-box{
  margin-top:20px;
  padding:15px;
  border:1px solid #dcdcdc;
  border-radius:10px;
  background:#f9fbfb;
}

.section-box h3{
  margin:0 0 10px 0;
  font-size:15px;
  color:#0a3b40;
  border-bottom:1px solid #ddd;
  padding-bottom:6px;
}

.auto-row{
  display:flex;
  gap:6px;
  margin-top:6px;
}

.auto-btn{
  flex:1;
  background:#e0f2f1;
  border:1px solid #0a3b40;
  color:#0a3b40;
  font-size:12px;
  padding:6px;
  border-radius:6px;
  cursor:pointer;
}

.clear-btn{
  background:#fdecea;
  border:1px solid #c62828;
  color:#c62828;
}

button{
  margin-top:20px;
  padding:12px;
  width:100%;
  background:#0a3b40;
  color:white;
  border:none;
  border-radius:10px;
  font-size:15px;
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
  padding:8px;
  font-size:12px;
  margin-bottom:10px;
}

.top-info{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:8px;
  margin-bottom:12px;
}

.box{
  border:1px solid #ccc;
  padding:8px;
  text-align:center;
  font-size:11pt;
}

.goal-section{
  background:#e8f5e9;
  border-right:5px solid #2e7d32;
  border-radius:8px;
  padding:12px;
  margin-bottom:12px;
  text-align:center;
}

.goal-section strong{
  display:block;
  margin-bottom:6px;
  color:#1b5e20;
}

.section{
  border:1px solid #ccc;
  padding:8px;
  font-size:11pt;
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

.signatures{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:40px;
  margin-top:20px;
  font-size:10pt;
}

.line{
  border-bottom:1px dashed #000;
  height:18px;
  margin-top:6px;
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
</select>

<label>اسم المدرسة</label>
<input oninput="sync('school',this.value)">

<div class="section-box">
<h3>بيانات التقرير</h3>

<label>المعيار التربوي</label>
<select id="axisSelect" onchange="updateReports()">
<option value="">اختر المعيار</option>
<option value="improve">تحسين نواتج التعلم</option>
</select>

<label>التقرير التربوي</label>
<select id="reportSelect" disabled onchange="sync('reportTitle',this.value)">
<option value="">اختر التقرير</option>
</select>
</div>

<div class="section-box">
<h3>بيانات المستهدفين</h3>

<label>المستهدفون</label>
<input placeholder="مثال: طلاب الصف الثالث" oninput="sync('target',this.value)">

<label>العدد</label>
<input type="number" placeholder="مثال: 25" oninput="sync('count',this.value)">
</div>

<div class="section-box">
<h3>الهدف التربوي</h3>
<textarea id="goalInput" oninput="sync('goal',this.value)"></textarea>
<div class="auto-row">
<button class="auto-btn" onclick="fill('goal')">نص تلقائي</button>
<button class="auto-btn clear-btn" onclick="clearText('goal')">مسح</button>
</div>
</div>

<button onclick="window.print()">تصدير PDF</button>
</div>

<div class="report">
<div class="header">
<div id="edu"></div>
<div id="school"></div>
</div>

<div class="top-info">
<div class="box"><strong>المعيار</strong><div id="axis"></div></div>
<div class="box"><strong>التقرير</strong><div id="reportTitle"></div></div>
<div class="box"><strong>المستهدفون</strong><div id="target"></div></div>
<div class="box"><strong>العدد</strong><div id="count"></div></div>
</div>

<div class="goal-section">
<strong>الهدف التربوي</strong>
<div id="goal"></div>
</div>

<div class="signatures">
<div><div id="teacher"></div><div class="line"></div>توقيع المعلم</div>
<div><div id="principal"></div><div class="line"></div>توقيع مدير المدرسة</div>
</div>
</div>

<script>
const data={
 improve:{
  "تقرير نشاط إثرائي":{
   goal:["تنمية مهارات التفكير العليا ورفع مستوى التحصيل الدراسي لدى الطلاب."]
  }
 }
};

function updateReports(){
 reportSelect.innerHTML='<option value="">اختر التقرير</option>';
 reportSelect.disabled=!axisSelect.value;
 if(!axisSelect.value)return;
 Object.keys(data[axisSelect.value]).forEach(r=>{
  reportSelect.innerHTML+=`<option>${r}</option>`;
 });
 sync('axis',axisSelect.options[axisSelect.selectedIndex].text);
}

function fill(k){
 const t=data[axisSelect.value][reportSelect.value][k][0];
 document.getElementById(k+'Input').value=t;
 sync(k,t);
}

function clearText(k){
 document.getElementById(k+'Input').value='';
 sync(k,'');
}

function sync(id,v){
 const el=document.getElementById(id);
 if(el) el.textContent=v;
}
</script>

</body>
</html>
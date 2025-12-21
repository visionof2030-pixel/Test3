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

/* ✅ تكبير مربع الهدف التربوي في الأداة */
#goalInput{
  min-height:130px;
  background:#f4fbf7;
  border:2px solid #2e7d32;
}

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

/* ✅ تكبير وتنسيق الهدف التربوي في التقرير */
.goal-section{
  background:#e8f5e9;
  border:2px solid #2e7d32;
  padding:10px;
  margin-bottom:8px;
  min-height:130px;
  page-break-inside:avoid;
}

.goal-section strong{
  color:#1b5e20;
  display:block;
  border-bottom:1px solid #2e7d32;
  margin-bottom:6px;
}

.section{
  border:1px solid #ccc;
  padding:5px;
  font-size:10.5pt;
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
  margin-top:6px;
  font-size:9pt;
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

<!-- 🔻 باقي الملف كما هو بدون أي تغيير 🔻 -->

</body>
</html>
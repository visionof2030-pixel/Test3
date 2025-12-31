<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق الأسئلة الإنجليزية - GitHub Pages</title>
    <style>
        /* CSS هنا */
    </style>
</head>
<body>
    <div class="container">
        <h1>🎯 تطبيق يعمل على GitHub Pages</h1>
        <p>API Keys تعمل هنا بشكل صحيح!</p>
        
        <input type="password" id="apiKey" placeholder="أدخل مفتاح API">
        <button onclick="useAPI()">استخدام API</button>
        
        <div id="result"></div>
    </div>
    
    <script>
    async function useAPI() {
        const apiKey = document.getElementById('apiKey').value;
        
        // على GitHub Pages، API Keys تعمل!
        const response = await fetch('https://api.example.com/endpoint', {
            headers: {
                'Authorization': `Bearer ${apiKey}`
            }
        });
        
        // ... معالجة الاستجابة
    }
    </script>
</body>
</html>
---
layout: page
title: ""
---
# welcome

# 欢迎凯凯
# 欢迎亮亮
# 欢迎洁达

<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>名人名言</title>
    <style>
        body {
            font-family: 'Lato', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(135deg, #74b9ff, #a29bfe);
            color: white;
            text-align: center;
        }
        #quote {
            font-size: 24px;
            opacity: 0;
            transition: opacity 2s;
        }
        #reload {
            display: none;
            padding: 10px 20px;
            font-size: 16px;
            color: white;
            background-color: #636e72;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div>
        <p id="quote">加载中...</p>
        <button id="reload" onclick="fetchQuote()">重试加载名言</button>
    </div>
    <script>
        function fetchQuote() {
            fetch('https://api.xygeng.cn/openapi/one')
                .then(response => response.json())
                .then(data => {
                    const quote = data.data.content;
                    const origin = data.data.origin;
                    document.getElementById('quote').innerText = `"${quote}" —— ${origin}`;
                    document.getElementById('quote').style.opacity = 1;
                    document.getElementById('reload').style.display = 'none';
                })
                .catch(error => {
                    console.error('获取名人名言失败：', error);
                    document.getElementById('quote').innerText = '无法获取名言';
                    document.getElementById('reload').style.display = 'block';
                });
        }
        fetchQuote(); // 初始加载
        setInterval(fetchQuote, 30000); // 每30秒更新一次
    </script>
</body>
</html>

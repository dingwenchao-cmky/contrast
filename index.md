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
        #quote-container {
            transition: opacity 2s;
            opacity: 0;
        }
        .button {
            padding: 10px 20px;
            font-size: 16px;
            color: white;
            background-color: #636e72;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 20px;
        }
        @media (max-width: 600px) {
            #quote {
                font-size: 16px;
            }
        }
    </style>
</head>
<body>
    <div id="quote-container">
        <p id="quote">加载中...</p>
        <button id="like" class="button" style="display: none;">收藏</button>
        <button id="share" class="button" style="display: none;">分享</button>
        <button id="reload" class="button" onclick="fetchQuote()">重试加载名言</button>
    </div>
    <script>
        function fetchQuote() {
            fetch('https://api.xygeng.cn/openapi/one')
                .then(response => response.json())
                .then(data => {
                    const quote = data.data.content;
                    const origin = data.data.origin;
                    document.getElementById('quote').innerText = `"${quote}" —— ${origin}`;
                    document.getElementById('quote-container').style.opacity = 1;
                    document.getElementById('like').style.display = 'block';
                    document.getElementById('share').style.display = 'block';
                    document.getElementById('reload').style.display = 'none';
                })
                .catch(error => {
                    console.error('获取名人名言失败：', error);
                    document.getElementById('quote').innerText = '无法获取名言';
                    document.getElementById('reload').style.display = 'block';
                    document.getElementById('like').style.display = 'none';
                    document.getElementById('share').style.display = 'none';
                });
        }

        document.getElementById('like').addEventListener('click', function() {
            const likedQuote = document.getElementById('quote').innerText;
            localStorage.setItem('likedQuote', likedQuote);
            alert('名言已收藏！');
        });

        document.getElementById('share').addEventListener('click', function() {
            const quoteToShare = document.getElementById('quote').innerText;
            const shareUrl = `https://twitter.com/intent/tweet?text=${encodeURIComponent(quoteToShare)}`;
            window.open(shareUrl, '_blank');
        });

        fetchQuote(); // 初始加载
        setInterval(fetchQuote, 30000); // 每30秒更新一次
    </script>
</body>
</html>

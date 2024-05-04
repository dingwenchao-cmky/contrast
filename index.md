---
layout: page
title: ""
---
# welcome

# 欢迎凯凯
# 欢迎亮亮
# 欢迎洁达
```html
<div id="daily-quote-container">
    <h2>每日语句</h2>
    <p id="daily-quote">正在加载每日语句...</p>
</div>

<script>
      // 发起网络请求获取每日语句
    fetch('https://api.example.com/daily-quote')
        .then(response => response.json())
        .then(data => {
            // 将每日语句插入到页面中
            document.getElementById('daily-quote').innerText = data.quote;
        })
        .catch(error => {
            console.error('Error fetching daily quote:', error);
            // 如果请求失败，显示错误消息
            document.getElementById('daily-quote').innerText = 'Failed to fetch daily quote';
        });
</script>

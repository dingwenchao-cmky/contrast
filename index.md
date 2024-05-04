---
layout: page
title: ""
---
# welcome

# 欢迎凯凯
# 欢迎亮亮
# 欢迎洁达

# 名人名言
<div id="quote-container">
    <h2>名人名言</h2>
    <p id="quote">正在加载名言...</p>
</div>

<script>
    // 发起网络请求获取名人名言
    fetch('https://quotes.rest/qod?category=inspire')
        .then(response => response.json())
        .then(data => {
            // 从响应中获取名言内容
            const quote = data.contents.quotes[0].quote;
            // 将名言插入到页面中
            document.getElementById('quote').innerText = quote;
        })
        .catch(error => {
            console.error('Error fetching quote:', error);
            // 如果请求失败，显示错误消息
            document.getElementById('quote').innerText = '无法获取名言';
        });
</script>

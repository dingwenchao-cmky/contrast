---
layout: page
title: ""
---
# welcome

# 欢迎凯凯
# 欢迎亮亮
# 欢迎洁达

<div id="quote-container">
    <p id="quote">加载中...</p>
</div>
<style>
    #quote {
        font-family: Arial, sans-serif;
        color: blue;
    }
</style>
<script>
    // 发起网络请求获取名人名言
    fetch('https://api.xygeng.cn/openapi/one')
        .then(response => response.json())
        .then(data => {
            // 从响应中获取名言内容
            const quote = data.data.content;
            const origin = data.data.origin;
            // 将名言插入到页面中
            document.getElementById('quote').innerText = `"${quote}" —— ${origin}`;
        })
        .catch(error => {
            console.error('获取名人名言失败：', error);
            // 如果请求失败，显示错误消息
            document.getElementById('quote').innerText = '无法获取名言';
        });
</script>

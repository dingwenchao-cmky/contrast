---
layout: home
title: ""
---

## Featured Posts

{% for post in site.posts limit:3 %}
- [{{ post.title }}]({{ post.url | relative_url }}) - {{ post.date | date: "%b %d, %Y" }}
{% endfor %}

## Explore

- [Python Tutorials](/categories/python-programming)
- [C++ Tutorials](/categories/c-plus-plus-programming)

## Stay Connected

- [Follow on GitHub](https://github.com/dingwenchao-cmky)
- [Subscribe to our Newsletter](#subscribe)

<div id="quote-container">
    <p id="quote">加载中...</p>
</div>
<style>
    body{
        font-family: 'Lato', sans-serif;    
    }
    #quote {
        color: black;
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

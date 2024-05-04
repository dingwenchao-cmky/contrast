---
layout: page
title: ""
---

<style>
  .hero {
    background: linear-gradient(to right, #6a11cb 0%, #2575fc 100%);
    color: white;
    padding: 20px;
    border-radius: 8px;
  }
  .feature-image {
    width: 100%;
    height: auto;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  }
</style>

<div class="hero">
  <h1>Welcome to My Programming Blog!</h1>
  <p>Discover the latest in Python, C++, and Web Development.</p>
</div>

![Feature Image](/path/to/your/image.jpg)

## Featured Posts

{% for post in site.posts limit:3 %}
- [{{ post.title }}]({{ post.url | relative_url }}) - {{ post.date | date: "%b %d, %Y" }}
{% endfor %}

## Explore

- [Python Tutorials](/categories/python-programming)
- [C++ Tutorials](/categories/c-plus-plus-programming)

## Stay Connected

- [Follow on GitHub](https://github.com/yourusername)
- [Subscribe to our Newsletter](#subscribe)

<div>
  <h3>Follow Our Social Media</h3>
  <!-- Social media plugin -->
</div>

## Contact Us

Feel free to [get in touch](/contact) or drop us an email at info@example.com!

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

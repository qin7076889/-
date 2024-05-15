# -<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<title>游戏资讯</title>
<style>
    body { font-family: Arial, sans-serif; background-color: #f4f4f4; color: #333; margin: 0; padding: 0; }
    .header { background: #0073e6; padding: 10px 20px; color: white; text-align: center; }
    .news-item { background: white; margin: 10px; padding: 10px; border-radius: 5px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
    .news-item h2 { color: #0073e6; }
    .news-item a { color: #0073e6; text-decoration: none; }
    .news-item p { margin: 5px 0; }
</style>
</head>
<body>
<div class="header">
    <h1>最新游戏资讯</h1>
</div>
<div id="news-container"></div>
<script>
function fetchGameNews() {
    fetch('https://newsapi.org/v2/top-headlines?category=technology&apiKey=b7d20506394e4d4c93331f8b6861cd1b')
    .then(response => response.json())
    .then(data => {
        const newsContainer = document.getElementById('news-container');
        newsContainer.innerHTML = ''; // 清除旧新闻
        data.articles.forEach(news => {
            const newsItem = document.createElement('div');
            newsItem.className = 'news-item';
            newsItem.innerHTML = `<h2><a href="${news.url}">${news.title}</a></h2><p>${news.description}</p>`;
            newsContainer.appendChild(newsItem);
        });
    })
    .catch(error => console.error('Error fetching game news:', error));
}

fetchGameNews();
</script>
</body>
</html>
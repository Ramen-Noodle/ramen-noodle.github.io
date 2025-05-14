---
layout: page
lang: ja
title: 検索
permalink: /ja/search
---

<div id="search-container">
    <input type="text" id="search-input" placeholder="ブログ投稿を検索...">
    <ul id="results-container"></ul>
</div>

<script src="{{ site.baseurl }}/assets/simple-jekyll-search.min.js" type="text/javascript"></script>

<script>
  fetch('{{ site.baseurl }}/search.json')
  .then(response => response.json())
  .then(data => {
    const currentLang = document.documentElement.lang || 'ja'; // Detect lang from <html lang="ja">
    const filteredData = data.filter(post => post.lang === currentLang);

    SimpleJekyllSearch({
      searchInput: document.getElementById('search-input'),
      resultsContainer: document.getElementById('results-container'),
      searchResultTemplate: '<div style="text-align: left !important;"><a href="{url}"><h1 style="text-align:left !important;">{title}</h1></a><span style="text-align:left !important;">{date}</span></div>',
      json: filteredData
    });
  });
</script>
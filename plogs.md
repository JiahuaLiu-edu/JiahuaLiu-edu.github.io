---
layout: page
permalink: /plogs/index.html
title: 我的 Plogs
---

<header class="plog-index-header">
  <p class="plog-index-kicker">STUDY · BUILD · REFLECT</p>
  <h1>学习 Plog</h1>
  <p>记录课堂内外值得留下的瞬间：一个刚弄懂的概念、一次项目尝试，或一段阶段性的复盘。</p>
</header>

{% capture plog_tags_csv %}{% for plog in site.plogs %}{% for tag in plog.tags %}{{ tag }},{% endfor %}{% endfor %}{% endcapture %}
{% assign plog_tags = plog_tags_csv | split: "," | uniq | sort %}

<section class="plog-tools" aria-label="搜索与标签筛选">
  <div class="plog-search">
    <svg class="plog-search__icon" viewBox="0 0 24 24" aria-hidden="true">
      <circle cx="11" cy="11" r="7"></circle>
      <path d="m20 20-4-4"></path>
    </svg>
    <input id="plogSearch" type="search" autocomplete="off" placeholder="搜索标题、摘要或标签" aria-label="搜索学习 Plog">
    <button id="plogSearchClear" class="plog-search__clear" type="button" aria-label="清空搜索" title="清空搜索" hidden>
      <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M6 6l12 12M18 6 6 18"></path></svg>
    </button>
  </div>

  <div class="plog-filter-row">
    <span class="plog-filter-label">标签</span>
    <div class="plog-tag-filter" id="plogTagFilter" role="group" aria-label="按标签筛选">
      <button class="is-active" type="button" data-plog-tag="" aria-pressed="true">全部</button>
      {% for tag in plog_tags %}
      {% unless tag == "" %}<button type="button" data-plog-tag="{{ tag | escape }}" aria-pressed="false">#{{ tag }}</button>{% endunless %}
      {% endfor %}
    </div>
  </div>

  <div class="plog-results" id="plogResults" aria-live="polite">{{ site.plogs | size }} 条记录</div>
</section>

<div class="plog-grid">
  {% assign sorted_plogs = site.plogs | sort: "date" | reverse %}
  {% for plog in sorted_plogs %}
  <article class="plog-card" data-plog-tags="{{ plog.tags | join: '|' | escape }}">
    <a class="plog-card__link" href="{{ site.url }}{{ plog.url }}" aria-label="阅读：{{ plog.title }}">
      <div class="plog-card__media plog-card__media--{{ plog.cover_shape | default: 'wide' }}{% if plog.cover_fit == 'contain' %} plog-card__media--contain{% endif %}">
        <img src="{{ site.url }}{{ plog.cover }}" alt="{{ plog.cover_alt | default: plog.title }}" loading="lazy">
        <span class="plog-card__category">{{ plog.category }}</span>
      </div>
      <div class="plog-card__body">
        <time datetime="{{ plog.date | date_to_xmlschema }}">{{ plog.date | date: "%Y.%m.%d" }}</time>
        <h2>{{ plog.title }}</h2>
        <p>{{ plog.summary }}</p>
        {% if plog.tags %}
        <div class="plog-card__tags" aria-label="标签">
          {% for tag in plog.tags %}<span>#{{ tag }}</span>{% endfor %}
        </div>
        {% endif %}
      </div>
    </a>
  </article>
  {% endfor %}
</div>

<div class="plog-empty" id="plogEmpty" hidden>
  <h2>没有匹配的记录</h2>
  <p>换一个关键词或标签试试。</p>
  <button id="plogFilterReset" type="button">清除筛选</button>
</div>

<script>
(function() {
  var input = document.getElementById('plogSearch');
  var clearButton = document.getElementById('plogSearchClear');
  var resetButton = document.getElementById('plogFilterReset');
  var tagButtons = Array.prototype.slice.call(document.querySelectorAll('[data-plog-tag]'));
  var cards = Array.prototype.slice.call(document.querySelectorAll('.plog-card'));
  var results = document.getElementById('plogResults');
  var empty = document.getElementById('plogEmpty');
  if (!input || !cards.length || !results || !empty) return;

  var activeTag = '';

  function normalize(value) {
    return (value || '').trim().toLocaleLowerCase('zh-CN');
  }

  function applyFilters() {
    var terms = normalize(input.value).split(/\s+/).filter(Boolean);
    var visibleCount = 0;

    cards.forEach(function(card) {
      var text = normalize(card.textContent);
      var tags = (card.getAttribute('data-plog-tags') || '').split('|');
      var matchesSearch = terms.every(function(term) { return text.indexOf(term) !== -1; });
      var matchesTag = !activeTag || tags.indexOf(activeTag) !== -1;
      var isVisible = matchesSearch && matchesTag;
      card.hidden = !isVisible;
      if (isVisible) visibleCount += 1;
    });

    clearButton.hidden = !input.value;
    empty.hidden = visibleCount !== 0;
    results.textContent = visibleCount + ' 条记录';
  }

  function selectTag(button) {
    activeTag = button.getAttribute('data-plog-tag') || '';
    tagButtons.forEach(function(item) {
      var selected = item === button;
      item.classList.toggle('is-active', selected);
      item.setAttribute('aria-pressed', selected ? 'true' : 'false');
    });
    applyFilters();
  }

  input.addEventListener('input', applyFilters);
  clearButton.addEventListener('click', function() {
    input.value = '';
    input.focus();
    applyFilters();
  });
  tagButtons.forEach(function(button) {
    button.addEventListener('click', function() { selectTag(button); });
  });
  resetButton.addEventListener('click', function() {
    input.value = '';
    selectTag(tagButtons[0]);
    input.focus();
  });
})();
</script>

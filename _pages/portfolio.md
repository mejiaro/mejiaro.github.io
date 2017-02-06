---
layout: home
title: Portfolio
permalink: /portfolio
---
<header class="mdl-layout__header mdl-layout__header--scroll mdl-color--primary">
  <div class="mdl-layout--large-screen-only mdl-layout__header-row">
  </div>
  <div class="mdl-layout--large-screen-only mdl-layout__header-row">
    <h3>Ricardo Mejía</h3>
  </div>
  <div class="mdl-layout--large-screen-only mdl-layout__header-row">
  </div>
  <div class="mdl-layout__tab-bar mdl-js-ripple-effect mdl-color--primary-dark">
    <a href="/about" class="mdl-layout__tab">About</a>
    <a href="#portfolio" class="mdl-layout__tab is-active">Portfolio</a>
    <a href="/" class="mdl-layout__tab">Articles</a>
  </div>
</header>
<main class="mdl-layout__content">
   <div class="mdl-layout__tab-panel is-active" id="portfolio">
      {% for card in site.cards %}
        {% include card.html %}
      {% endfor %}
   </div>           
</main>
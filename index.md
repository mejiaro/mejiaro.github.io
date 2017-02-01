---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
title: Home
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
    <a href="/" class="mdl-layout__tab is-active">Articles</a>
    <a href="/portfolio" class="mdl-layout__tab">Portfolio</a>
    <a href="/contact" class="mdl-layout__tab">Contact</a>
  </div>
</header>
<main class="mdl-layout__content">
	<div class="mdl-layout__tab-panel is-active" id="home">
    {% for post in site.posts %}
      {% include tile.html %}
    {% endfor %}
  </div>        
</main>
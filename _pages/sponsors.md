---
layout: inner
title: Nuestros patrocinadores
permalink: /patrocinadores/
---

<div class="sponsors-wrapper">
  <div class="row">
    {% for sponsor in site.data.sponsors %}
    <div class="col-sm-4 col-md-4">
      <div class="thumbnail">
        <a href="{{ sponsor.url }}" target="_blank">
          <img
            src="{{ sponsor.image }}"
            alt="{{ sponsor.name }}"
          />
        </a>
      </div>
    </div>
    {% assign mod = forloop.index | modulo: 3 %} {% if mod == 0 and forloop.last
    == false %}
  </div>
  <div class="row">{% endif %} {% endfor %}
  </div>
</div>

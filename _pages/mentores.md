---
layout: inner
title: Mentoras/es
lead_text:
permalink: /mentores/
---

<div class="row">
    {% for coach in site.data.mentores %}
    <div class="col-sm-3 col-md-3">
        <div class="thumbnail">
            <img
                src="{{ coach.image }}"
                alt="Coach {{ coach.name }}"
                width="150"
            />
            <div class="caption">
                <h3 class="text-center">{{ coach.name }}</h3>
                <p class="role-container">
                    <span class="strong">Rol:</span> {{ coach.role }}
                </p>
                <p>
                    <span class="strong">Trabajo en:</span> {{ coach.company }}
                </p>
            </div>
        </div>
    </div>
    {% assign mod = forloop.index | modulo: 4 %} {% if mod == 0 and forloop.last
    == false %}
</div>
<div class="row">{% endif %} {% endfor %}</div>

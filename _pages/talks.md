---
layout: inner
title: Charlas
lead_text: Nuestras speakers
permalink: /charlas/
---

<style>
    .role-container {
        margin-top: 3rem;
    }

    .strong {
        font-weight: 700;
    }
</style>

<div class="row">
    {% for talk in site.data.charlas %}
    <div class="col-sm-6 col-md-6">
        <div class="thumbnail">
            <img src="{{ talk.image }}" alt="Speaker {{ talk.name }}" width="150" />
            <div class="caption">
                <h3 class="text-center">{{ talk.name }}</h3>
                <p class="role-container">
                    <span class="strong">Rol:</span> {{ talk.role }}
                </p>
                {% if talk.company %}
                <p>
                    <span class="strong">Trabajo en:</span> {{ talk.company }}
                </p>
                {% endif %}
                <p>
                    <span class="strong">Experiencia:</span> {{ talk.experience }}
                </p>
                <p>
                    <span class="strong">Título de tu charla:</span> {{ talk.talk_title }}
                </p>
                <p>
                    <span class="strong">Sobre tu charla:</span> {{ talk.talk_description }}
                </p>
            </div>
        </div>
    </div>
    {% assign mod = forloop.index | modulo: 2 %} {% if mod == 0 and forloop.last
    == false %}
</div>
<div class="row">{% endif %} {% endfor %}
</div>

---
layout: inner
title: Speakers 2023
lead_text: Nuestras speakers
permalink: /speakers2023/
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
    {% for speaker in site.data.speakers2023 %}
    <div class="col-sm-6 col-md-6">
        <div class="thumbnail">
            <img src="{{ speaker.image }}" alt="Speaker {{ speaker.name }}" width="150" />
            <div class="caption">
                <h3 class="text-center">{{ speaker.name }}</h3>
                <p class="role-container">
                    <span class="strong">Rol:</span> {{ speaker.role }}
                </p>
                <p>
                    <span class="strong">Trabajo en:</span> {{ speaker.company }}
                </p>
                <p>
                    <span class="strong">Experiencia:</span> {{ speaker.experience }}
                </p>
                <p>
                    <span class="strong">Título de tu charla:</span> {{ speaker.talk_title }}
                </p>
                <p>
                    <span class="strong">Sobre tu charla:</span> {{ speaker.talk_description }}
                </p>
            </div>
        </div>
    </div>
    {% assign mod = forloop.index | modulo: 2 %} {% if mod == 0 and forloop.last
    == false %}
</div>
<div class="row">{% endif %} {% endfor %}
</div>

---
layout: default
title: Bavaria (Bayern)
map_type: state
state_id: bayern
permalink: /en/bayern/
slug: bayern
lang: en
cities:
  - name: "Munich (München)"
    lat: 48.1351
    lng: 11.5820
    url: "/bayern/muenchen/"
  - name: "Nuremberg (Nürnberg)"
    lat: 49.4521
    lng: 11.0767
    url: "/bayern/nuernberg/"
---

## Bavaria Exploration Map
Click the pins on the map above, and join me as we dive deep into the towns of Bavaria. Or...

<div class="quick-access">
    <h3 style="margin-top: 0; font-size: 1.2rem; border-left: 4px solid #3498db; padding-left: 10px; border-bottom: none;">
        Hop on the City Express below 🚅 Guaranteed to be faster than the Deutsche Bahn!
    </h3>
    <div class="city-grid">
        {% for city in page.cities %}
            {% comment %} 根據語言判斷前綴 {% endcomment %}
            {% if page.lang == "en" %}
                {% assign lang_prefix = "/en" %}
            {% elsif page.lang == "jp" %}
                {% assign lang_prefix = "/jp" %}
            {% else %}
                {% assign lang_prefix = "" %}
            {% endif %}
            
            {% comment %} 拼接完整路徑 {% endcomment %}
            {% capture city_full_url %}{{ lang_prefix }}{{ city.url }}{% endcapture %}

            <a href="{{ city_full_url | relative_url }}" class="city-link">
                {{ city.name }}
            </a>
        {% endfor %}
    </div>
</div>

<style>
    .quick-access {
        background: #f8f9fa;
        padding: 20px;
        border-radius: 8px;
        margin: 20px 0 30px 0;
        border: 1px solid #eee;
    }
    .city-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
        gap: 10px;
        margin-top: 15px;
    }
    .city-link {
        display: block;
        padding: 8px 12px;
        background: white;
        border: 1px solid #3498db;
        color: #3498db;
        text-align: center;
        border-radius: 6px;
        text-decoration: none;
        font-size: 14px;
        font-weight: 500;
        transition: all 0.2s ease;
    }
    .city-link:hover {
        background: #3498db;
        color: white;
        transform: translateY(-2px);
    }
</style>

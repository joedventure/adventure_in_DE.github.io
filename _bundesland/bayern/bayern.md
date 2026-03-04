---
layout: default
title: 巴伐利亞 (Bayern)
map_type: state
state_id: bayern
permalink: /bayern/
slug: bayern
lang: zh
cities:
  - name: "慕尼黑 (München)"
    lat: 48.1351
    lng: 11.5820
    url: "/bayern/muenchen/"
  - name: "紐倫堡 (Nürnberg)"
    lat: 49.4521
    lng: 11.0767
    url: "/bayern/nuernberg/"
---

## 巴伐利亞探索地圖
點擊地圖上的圖釘，跟我一起深入探索巴伐利亞的各個城鎮。或是...

<div class="quick-access">
    <h3 style="margin-top: 0; font-size: 1.2rem; border-left: 4px solid #3498db; padding-left: 10px; border-bottom: none;">
        搭乘下面的城市直達車🚅 絕對比德鐵更快！
    </h3>
    <div class="city-grid">
        {% for city in page.cities %}
            <a href="{{ city.url | relative_url }}" class="city-link">
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


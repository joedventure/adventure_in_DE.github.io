---
layout: default
title: "德國旅遊互動地圖"
---

<div id="map" style="height: 600px; width: 100%; border: 1px solid #ccc;"></div>

<script>
    // 使用 window.onload 確保 default.html 裡的 Leaflet JS 已載入
    window.onload = function() {
        if (typeof L === 'undefined') {
            console.error("Leaflet 尚未載入，請檢查 default.html 是否有正確引入 JS。");
            return;
        }

        const map = L.map('map').setView([51.1657, 10.4515], 6);
        const baseUrl = "{{ site.baseurl }}";

        // 加入底圖，否則只會看到空白
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '© OpenStreetMap contributors'
        }).addTo(map);

        // 載入全德地圖數據
        fetch(`${baseUrl}/assets/germany.geojson`)
            .then(res => {
                if (!res.ok) throw new Error("找不到 GeoJSON 檔案，請檢查路徑。");
                return res.json();
            })
            .then(data => {
                L.geoJSON(data, {
                    style: { color: "#3388ff", weight: 2, fillOpacity: 0.1 },
                    onEachFeature: (feature, layer) => {
                        layer.on({
                            mouseover: (e) => e.target.setStyle({ fillOpacity: 0.4 }),
                            mouseout: (e) => e.target.setStyle({ fillOpacity: 0.1 }),
                            click: () => {
                                // 抓取 id 或將 name 轉為小寫
                                const id = feature.properties.id || feature.properties.name.toLowerCase();
                                window.location.href = `${baseUrl}/${id}/`;
                            }
                        });
                        layer.bindTooltip(feature.properties.name);
                    }
                }).addTo(map);
            })
            .catch(err => console.error("地圖載入錯誤:", err));
    };
</script>

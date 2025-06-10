---
layout: default
title: Pictures
---

<h1>Photo Gallery</h1>
<div class="intro-text">
    <p>As part of the photovoice students were asked to take photos around campus relating to sustainability. They were then asked to share their top 5 along with a short description on why they chose this photograph.</p>
    <p>Below are some of their submissions</p>
</div>
<div class="gallery" id="gallery"></div>
<script>
    fetch('data.json')
        .then(response => response.json())
        .then(data => {
            const gallery = document.getElementById('gallery');
            let count = 0;
            data.forEach(item => {
                count++;
                const card = document.createElement('div');
                card.className = 'photo-card';
                card.innerHTML = `
                    <img src="${item.image_src}" alt="${item.alt}">
                <div class="description">${item.description.replace(/\n/g, '<br>')}</div>
                `;
                gallery.appendChild(card);
            });
        });
</script>
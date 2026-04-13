---
permalink: /fieldwork/
title: ""
author_profile: true
---

<div style="text-align: center;">
  <h2 style="color: #cb2027;">Fieldwork in Ghana</h2>
</div>

<style>
.fw-carousel {
  position: relative;
  width: 100%;
  max-width: 800px;
  margin: 0 auto;
  user-select: none;
}
.fw-track {
  overflow: hidden;
  border-radius: 4px;
}
.fw-slides {
  display: flex;
  transition: transform 0.4s ease;
}
.fw-slides img {
  flex-shrink: 0;
  height: 500px;
  object-fit: cover;
  display: block;
}
.fw-btn {
  position: absolute;
  top: 45%;
  transform: translateY(-50%);
  background: rgba(0,0,0,0.45);
  color: #fff;
  border: none;
  padding: 12px 18px;
  font-size: 20px;
  cursor: pointer;
  border-radius: 3px;
  z-index: 10;
  line-height: 1;
}
.fw-btn:hover { background: rgba(0,0,0,0.7); }
.fw-btn.prev { left: 8px; }
.fw-btn.next { right: 8px; }
.fw-dots {
  text-align: center;
  padding: 10px 0 4px;
}
.fw-dot {
  display: inline-block;
  width: 9px;
  height: 9px;
  margin: 0 4px;
  background: #ccc;
  border-radius: 50%;
  cursor: pointer;
  transition: background 0.2s;
}
.fw-dot.active { background: #cb2027; }
.fw-counter {
  text-align: center;
  padding-bottom: 6px;
  font-size: 0.85em;
  color: #666;
}
</style>

<div class="fw-carousel" id="fw-carousel">
  <div class="fw-track" id="fw-track">
    <div class="fw-slides" id="fw-slides">
      <img src="/images/Fieldwork/20220527_165750.jpg" alt="Fieldwork Ghana">
      <img src="/images/Fieldwork/20220607_183343.jpg" alt="Fieldwork Ghana">
      <img src="/images/Fieldwork/20220531_111201.jpg" alt="Fieldwork Ghana">
      <img src="/images/Fieldwork/20220523_095415.jpg" alt="Fieldwork Ghana">
      <img src="/images/Fieldwork/20220523_095401.jpg" alt="Fieldwork Ghana">
      <img src="/images/Fieldwork/20220527_092723.jpg" alt="Fieldwork Ghana">
      <img src="/images/Fieldwork/20220527_092731.jpg" alt="Fieldwork Ghana">
      <img src="/images/Fieldwork/20220523_095540.jpg" alt="Fieldwork Ghana">
      <img src="/images/Fieldwork/20220603_085728.jpg" alt="Fieldwork Ghana">
      <img src="/images/Fieldwork/20220603_101136.jpg" alt="Fieldwork Ghana">
      <img src="/images/Fieldwork/20220602_140312_modified_edited.jpg" alt="Fieldwork Ghana">
      <img src="/images/Fieldwork/20220619_164340.jpg" alt="Fieldwork Ghana">
    </div>
  </div>
  <button class="fw-btn prev" id="fw-prev">&#8249;</button>
  <button class="fw-btn next" id="fw-next">&#8250;</button>
  <div class="fw-dots" id="fw-dots"></div>
  <div class="fw-counter" id="fw-counter"></div>
</div>

<script>
document.addEventListener('DOMContentLoaded', function () {
  var track = document.getElementById('fw-track');
  var slides = document.getElementById('fw-slides');
  var dotsContainer = document.getElementById('fw-dots');
  var counter = document.getElementById('fw-counter');
  var imgs = slides.getElementsByTagName('img');
  var total = imgs.length;
  var current = 0;

  function slideWidth() {
    return track.offsetWidth;
  }

  function setImageWidths() {
    var w = slideWidth();
    for (var i = 0; i < total; i++) {
      imgs[i].style.width = w + 'px';
    }
  }

  setImageWidths();

  for (var i = 0; i < total; i++) {
    var d = document.createElement('span');
    d.style.cssText = 'display:inline-block;width:9px;height:9px;margin:0 4px;border-radius:50%;cursor:pointer;transition:background 0.2s;background:#ccc;';
    d.setAttribute('data-i', String(i));
    d.addEventListener('click', (function (idx) {
      return function () { go(idx); };
    })(i));
    dotsContainer.appendChild(d);
  }

  function update() {
    slides.style.transform = 'translateX(-' + (current * slideWidth()) + 'px)';
    var dots = dotsContainer.getElementsByTagName('span');
    for (var i = 0; i < dots.length; i++) {
      dots[i].style.background = i === current ? '#cb2027' : '#ccc';
    }
    counter.textContent = (current + 1) + ' / ' + total;
  }

  function move(dir) {
    current = (current + dir + total) % total;
    update();
  }

  function go(idx) {
    current = idx;
    update();
  }

  document.getElementById('fw-prev').addEventListener('click', function () { move(-1); });
  document.getElementById('fw-next').addEventListener('click', function () { move(1); });

  document.addEventListener('keydown', function (e) {
    if (e.key === 'ArrowLeft') move(-1);
    if (e.key === 'ArrowRight') move(1);
  });

  var startX = null;
  slides.addEventListener('touchstart', function (e) { startX = e.touches[0].clientX; }, { passive: true });
  slides.addEventListener('touchend', function (e) {
    if (startX === null) return;
    var dx = e.changedTouches[0].clientX - startX;
    if (Math.abs(dx) > 40) move(dx < 0 ? 1 : -1);
    startX = null;
  }, { passive: true });

  window.addEventListener('resize', function () {
    setImageWidths();
    update();
  });

  update();
});
</script>

---
layout: post
title:  "SVG 动画 by After Effects 2"
date:   2018-04-02
tags: [note]
commentIssueId: 76
---

监听 click 函数, 和 svg 动画做交互
* html 代码
* js 控制 svg 动画代码
* svg 交互动画效果
* 使用 canvas 渲染

## html 代码

```html
<div id="bm_animation">

  <div id="click_r"></div>
  <div id="click_l"></div>

</div>
```

## js 控制 svg 动画

```js
var container = document.getElementById('bm_animation');
var animData = {
  container: container,
  renderer: 'svg', // 此处还可使用 canvas 渲染
  loop: true,
  prerender: false,
  autoplay: true,
  autoloadSegments: false,
  path: './fight.json'
};

var anim;
var isHitting = false;


anim = bodymovin.loadAnimation(animData);
anim.addEventListener('DOMLoaded', startAnimation);
click_r.onclick = hitRight;
click_l.onclick = hitLeft;

function hitComplete() {
  isHitting = false;
  anim.removeEventListener('loopComplete', hitComplete);
}

function hitRight() {
  if (isHitting) {
    return;
  }
  isHitting = true;
  anim.playSegments([
    [75, 95],
    [65, 75]
  ], true);
  anim.addEventListener('loopComplete', hitComplete);
}


function hitLeft() {
  if (isHitting) {
    return;
  }
  isHitting = true;
  anim.playSegments([
    [95, 115],
    [65, 75]
  ], true);
  anim.addEventListener('loopComplete', hitComplete);
}

function startAnimation() {
  anim.playSegments([
    [0, 65],
    [65, 75]
  ], true);
}

```


## svg 交互动画效果

<iframe style='width: 100%; display: block; border: none; height: 500px;' src='https://zhoukekestar.github.io/notes/assets/2018/04-02-after-effects2/index.html'></iframe>

## canvas 渲染

<iframe style='width: 100%; display: block; border: none; height: 500px;' src='https://zhoukekestar.github.io/notes/assets/2018/04-02-after-effects2/canvas.html'></iframe>


## References
* [lottie-web](https://github.com/airbnb/lottie-web)
* [bodymovin](https://creative.adobe.com/addons/products/12557)
* [demo 来源](http://wow.techbrood.com/fiddle/32208)
  > 特别注意，以上动画非作者本人编写，原作者保留所有版权

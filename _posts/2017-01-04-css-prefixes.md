---
layout: post
title: CSS Class Prefixes
published: true
---

* l-: Layout
* c-: Component
* u-: Utility
* t-: Theme
* is-, has-: Stateful
* js-: JavaScript
* qa-: QA

## l-: Layout

```css
.l-grid__item {}
.l-two-column {}
```

## c-: Component

```css
.c-modal {}
.c-modal__title {}
.c-card {}
```

## u-: Utility

```css
.u-clearfix {}
.u-margin-bottom-double {}
.u-font-size-large {}
```

## t-: Theme

```css
.t-light {}
.t-9cells {}
```

## is-, has,: Stateful

```css
.is-open {}
.is-active {}
.is-disabled {}
.has-dropdown {}
```

## js-: JavaScript

```css
.js-modal-trigger 
```

JavaScript 타겟용. 스타일 적용 없음.

## qa-: QA

```css
.qa-error-login {}
```

일반적이진 않지만, 테스트용으로 사용.

### 참고 

[http://bradfrost.com/blog/post/css-architecture-for-design-systems/](http://bradfrost.com/blog/post/css-architecture-for-design-systems/)
[http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/#detecting-namespaces](http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/#detecting-namespaces)
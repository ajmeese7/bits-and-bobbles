---
id: pmoon12tt6k5jelthikv4vt
title: 'Pixelated resize using canvas with transparent PNG'
desc: ''
updated: 1664735181472
created: 1645589580000
tags:
  - javascript
  - canvas
  - image
  - transparent
  - pixel
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/71229461/6456163) for the original answer.

This has since been made into an extremely minimalist library, and my PR for PNG support can be found [here](https://github.com/rogeriopvl/8bit/pull/6).

Once it has been merged I will come back and update this answer.

The full code, generalized and simplified from @Blindman67's answer:

```javascript
/**
 * 8bit
 *
 * A module that converts an image into a pixelated version (just like
 * 8bit artwork).
 *
 * @author rogeriopvl <https://github.com/rogeriopvl>
 * @license MIT
 */

(function (root, factory) {
  if (typeof define === "function" && define.amd) {
    define([], factory);
  } else if (typeof exports === "object") {
    module.exports = factory();
  } else {
    root.eightBit = factory();
  }
} (this, function () {
  // Necessary to hide the original image with PNG transparency
  const invisibleCanvas = document.createElement("canvas");
  const invisibleCtx = invisibleCanvas.getContext("2d");

  /**
   * Draws a pixelated version of an image in a given canvas.
   * @param {object} canvas - a canvas object
   * @param {object} image - an image HTMLElement object
   * @param {number} quality - the new quality: between 0 and 100
   */
  const eightBit = function (canvas, image, quality) {
    quality /= 100;

    canvas.width = invisibleCanvas.width = image.width;
    canvas.height = invisibleCanvas.height = image.height;

    const scaledW = canvas.width * quality;
    const scaledH = canvas.height * quality;
    const ctx = canvas.getContext("2d");

    ctx.mozImageSmoothingEnabled = false;
    ctx.webkitImageSmoothingEnabled = false;
    ctx.imageSmoothingEnabled = false;

    // Draws image scaled to desired quality on the invisible canvas, then
    // draws that scaled image on the visible canvas.
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    invisibleCtx.clearRect(0, 0, invisibleCtx.canvas.width, invisibleCtx.canvas.height);
    invisibleCtx.drawImage(image, 0, 0, scaledW, scaledH);
    ctx.drawImage(invisibleCtx.canvas, 0, 0, scaledW, scaledH, 0, 0, canvas.width, canvas.height);
  };

  return eightBit;
}));
```

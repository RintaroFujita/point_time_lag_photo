
## 説明

このプログラムは、p5.jsを使用してビデオキャプチャを取得し、キャンバス上にランダムに描画します。キャプチャされた画像から中央を切り取り、その一部を使用してランダムなエリアに色を描画します。

### コード

```javascript
let capture;

function setup() {
  createCanvas(700, 700);
  capture = createCapture(VIDEO);
  capture.size(700, 700);
  capture.hide();
}

function draw() {
  let img = capture.get();

  let offsetX = (img.width - width) / 2;
  let offsetY = (img.height - height) / 2;

  for (let i = 0; i < 10000; i++) {
    let x = random(width);
    let y = random(height);

    let captureColor = img.get(x + offsetX, y + offsetY);
    fill(captureColor);
    noStroke();
    ellipse(x, y, 1, 1);
  }
}

function keyPressed() {
  if (key === 's') {
    saveCanvas('canvasimg' + '.webp');
  }
}
```

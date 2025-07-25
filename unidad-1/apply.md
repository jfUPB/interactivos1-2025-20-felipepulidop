# Unidad 1

## 🛠 Fase: Apply

---

# Actividad 6

##  Enlace al programa en el editor de p5.js

https://editor.p5js.org/felipepulido090605/sketches/K3w4Cn8Mk

---

##  Código del programa en p5.js

```javascript
let port;
let reader;
let latestData = 0;
let circleX;

function setup() {
  createCanvas(600, 400);
  circleX = width / 2;

  let connectBtn = createButton('Conectar Micro:bit');
  connectBtn.position(10, 10);
  connectBtn.mousePressed(connectSerial);
}

async function connectSerial() {
  port = await navigator.serial.requestPort();
  await port.open({ baudRate: 115200 });
  reader = port.readable.getReader();
  readSerial();
}

async function readSerial() {
  let buffer = '';
  while (true) {
    const { value, done } = await reader.read();
    if (done) break;
    buffer += new TextDecoder().decode(value);

    const lines = buffer.split('\n');
    buffer = lines.pop(); 
    for (let line of lines) {
      let val = parseInt(line.trim());
      if (!isNaN(val)) {
        latestData = val;
      }
    }
  }
}

function draw() {
  background(220);
  fill(0, 102, 255);
  circle(circleX, height / 2, 50);

  circleX += latestData * 5;
  circleX = constrain(circleX, 0, width);
}
```
---

## Código del programa del micro:bit

```python
from microbit import *

uart.init(baudrate=115200)
display.show(Image.SWORD)

while True:
    if button_a.is_pressed():
        uart.write("-1\n") 
    elif button_b.is_pressed():
        uart.write("1\n")   
    else:
        uart.write("0\n")   
    sleep(100)

```

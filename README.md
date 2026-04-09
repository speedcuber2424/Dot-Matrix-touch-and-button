# 🎮 Touch + Button + Dot Matrix Display — Arduino UNO R4 Minima

> **Built by Aryan. Overthought by Dad.**

A fun interactive project where a TTP223 capacitive touch sensor and a push button each trigger scrolling messages on a MAX7219 8×8 dot matrix display.

---

## 📦 Components Used

| Component | Model |
|---|---|
| Microcontroller | Arduino UNO R4 Minima |
| Touch Sensor | TTP223 Capacitive Touch Module |
| Push Button | Tactile Switch |
| Dot Matrix Display | MAX7219 8×8 LED Matrix (FC16 hardware) |

---

## 🔌 Wiring

| Component | Component Pin | Arduino UNO R4 Minima Pin |
|---|---|---|
| TTP223 Touch | VCC | 3.3V |
| TTP223 Touch | GND | GND |
| TTP223 Touch | SIG | D2 |
| Push Button | One leg | D3 |
| Push Button | Other leg | GND |
| MAX7219 Matrix | VCC | 5V |
| MAX7219 Matrix | GND | GND |
| MAX7219 Matrix | DIN | D11 |
| MAX7219 Matrix | CLK | D13 |
| MAX7219 Matrix | CS | D10 |

> ⚠️ TTP223 runs on **3.3V**, not 5V. Push button uses Arduino's **internal pull-up** — no external resistor needed.

---

## 📚 Libraries Required

Install these via **Sketch → Include Library → Manage Libraries** in Arduino IDE:

- `MD_Parola` by MajicDesigns
- `MD_MAX72XX` by MajicDesigns

> ⚠️ **Known conflict on R4 Minima:** If you have `ArduinoGraphics` or `Arduino_LED_Matrix` installed, they will clash with MD_MAX72XX. Uninstall them or isolate this sketch in its own folder.

---

## ⚙️ How It Works

- **Touch the TTP223** → Display scrolls **"TOUCH!"**
- **Press the button** → Display scrolls **"PRESS!"**
- **Nothing pressed** → Display scrolls **"READY"**

The TTP223 is **active-LOW** — it outputs LOW when touched, HIGH when not. The push button also reads LOW when pressed (because of `INPUT_PULLUP`). The display animation always completes before switching messages, so no letters get cut off.

---

## 🧠 Key Concepts Learned

| Concept | What It Means |
|---|---|
| Active-LOW sensor | Signal goes LOW when triggered, not HIGH |
| INPUT_PULLUP | Built-in resistor keeps pin HIGH until button pulls it LOW |
| Edge detection | Only reacting the *moment* something changes, not every loop tick |
| displayAnimate() | Must be called every loop tick — like cranking a film projector |

---

## 🐛 Troubleshooting

| Problem | Fix |
|---|---|
| Nothing shows on display | Check DIN→D11, CLK→D13, CS→D10. Make sure hardware type is `FC16_HW` |
| Display shows garbage/flicker | Remove or uninstall ArduinoGraphics and Arduino_LED_Matrix libraries |
| Touch sensor always triggered | Your module may be active-HIGH — swap LOW and HIGH in the touch condition |
| Button not responding | Confirm one leg goes to D3, the other directly to GND |
| Text gets cut off mid-letter | Make sure `displayAnimate()` is called every loop with no `delay()` blocking it |
| Can't upload sketch | Double-tap the reset button on the Arduino to enter bootloader mode, then upload |

---

## 📁 File Path

```
C:\Users\Aryan\Desktop\Raspberry pi,Arduino and Python\Arduino\
```

---

## 🎬 Part of the Summer YouTube Series

This project is part of Aryan's summer maker series on the family YouTube channel — exploring sensors, displays, and real-world builds using Arduino. Check out the video for the full paper-card explanation and live demo!


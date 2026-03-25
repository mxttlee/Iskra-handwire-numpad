## Iskra Handwired Numpad

### Overview
Iskra is a DIY 10‑key hand‑wired macropad designed for both wired USB and Bluetooth (ZMK) use. It uses low‑profile Kailh Choc switches and a Pro Micro nRF52840 (nice!nano v2 clone). The design is fully open source and supports ZMK Studio for easy keymap customization.

![Front render](files%20and%20media/iskra%20front%20render.png)

#### Key features
- **3 programmable layers** (ZMK firmware)
- **Compact** credit‑card size layout (approx. 82 × 60 × 22 mm)
- **Hand‑wired** 3×4 matrix with 1N4148 diodes (10 keys populated)
- **Wired USB‑C** and **Bluetooth** modes
- **ZMK Studio** support for on‑device editing
- 3D printable, files on [MakerWorld](https://makerworld.com/en/models/1859378)

### Real photos
<p>
  <img src="files%20and%20media/real%20pics/home%20view.jpg" alt="Home view" width="45%"/>
  <img src="files%20and%20media/real%20pics/with%20printed%20keycaps.jpg" alt="With printed keycaps" width="45%"/>
</p>
<p>
  <img src="files%20and%20media/real%20pics/card%20compare%202.jpg" alt="Card compare 2" width="45%"/>
  <img src="files%20and%20media/real%20pics/card%20compare%201.jpg" alt="Card compare 1" width="45%"/>
</p>

---

### Bill of Materials (BOM)

| Part | Qty | Price (EUR) | Link |
| --- | ---: | ---: | --- |
| Kailh Choc switches | 10 | 2.00 | [AliExpress](https://www.aliexpress.com/item/1005006626760418.html) |
| Pro Micro nRF52840 (nice!nano clone) | 1 | 3.80 | [AliExpress](https://www.aliexpress.com/item/1005007010555229.html) |
| M2 brass standoff, 6 mm | 2 | 0.20 | [AliExpress](https://www.aliexpress.com/item/1005006049595637.html) |
| M2 screw, 6 mm | 4 | 0.10 | [AliExpress](https://www.aliexpress.com/item/1005005070119421.html) |
| 1N4148 diodes | 10 | 0.13 | [AliExpress](https://www.aliexpress.com/item/1005006861038367.html) |
| Copper wire | 15 cm | 0.05 | [AliExpress](https://www.aliexpress.com/item/1005009078359338.html) |

Assumes you already have a soldering iron, solder, insulation/masking tape, and a few wires.

---

### Firmware
- Prebuilt firmware (drag‑and‑drop): `Firmware/Ready to flash firmware/iskra.uf2`
- Config source (ZMK): `Firmware/zmk-config-iskra`

#### How to flash (UF2)
1. Connect the numpad to the PC.
2. Short the `GND` and `RST` pins twice quickly (double‑tap reset).
3. A removable drive (e.g. “NICE NANO”) will appear.
4. Copy `iskra.uf2` into the drive.
5. It will restart; the numpad is now flashed.

Note: The prebuilt firmware assumes the same controller (nRF52840 nice!nano v2‑compatible) and the pin wiring specified below.

---

### Documentation
- [Build and wiring guide (PDF)](files%20and%20media/Iskra%20Numpad%20Build%20and%20wiring%20guide.pdf)
- [User manual (PDF)](files%20and%20media/Iskra%20Numpad,%20user%20manual.pdf)

 These documents provide a step‑by‑step reference for building a hand‑wired numpad: keyboard matrix wiring with **1N4148 diodes**, **Kailh Choc** low‑profile switches, and a **Pro Micro nRF52840** (nice!nano v2 clone). Topics include routing rows and columns, insulating wires to avoid shorts, mapping pins to firmware, flashing ZMK via **UF2**, configuring **Bluetooth** profiles, and using **ZMK Studio** to adjust keymaps.

---

### Layout, Layers, and Combos

![Keymap](files%20and%20media/iskra%20keymap.png)

#### Layers (from firmware config)
- **Base**: `1 2 3 / 4 5 6 / 7 8 9 0`
- **Bluetooth**: Bottom row provides Bluetooth controls — `BT_SEL 1`, `BT_SEL 2`, `BT_SEL 3`, `BT_CLR`; other keys are transparent.
- **Layer 3**: Media and navigation
  - Top row: Previous, Play/Pause, Next
  - Middle row: Ctrl+C, Ctrl+V, Ctrl+X
  - Bottom row: Arrow Left, Up, Down, Right

#### Combos
- **Base layer combo**: Press the top three keys at the same time → switches to Base
- **Bluetooth layer combo**: Press the middle three keys at the same time → switches to Bluetooth
- **Third layer combo**: Press the bottom three keys at the same time → switches to Layer 3
- **ZMK Studio unlock**: Press the top two keys at the same time

Combo visuals:

<p>
  <img src="files%20and%20media/combo%20for%20base%20layer.png" alt="Combo for base layer" width="32%"/>
  <img src="files%20and%20media/combo%20for%20bluetooth%20layer.png" alt="Combo for Bluetooth layer" width="32%"/>
  <img src="files%20and%20media/combo%20for%20third%20layer.png" alt="Combo for third layer" width="32%"/>
</p>

<img src="files%20and%20media/ZMK%20studio%20unllock%20combo.png" alt="ZMK Studio unlock combo" width="40%"/>

---

### Bluetooth usage
1. Power Iskra from a PC or power bank.
2. Use the **Bluetooth layer combo** (press the middle three keys simultaneously).
3. Select a Bluetooth profile using one of the bottom‑row keys: `BT1`, `BT2`, or `BT3`.
4. Pair from your device. The advertised name is “Iskra Numpad”.
5. To switch devices later, change the Bluetooth profile. Example: PC on BT1, phone on BT2.
6. Use **BT Clear** to forget the current profile.

---

### ZMK Studio and customization
- Use ZMK Studio on the web: `https://zmk.studio/` or download: `https://zmk.studio/download/`.
- Connect Iskra and select it in Studio.
- Press the **ZMK Studio unlock combo** (top two keys: 1 and 2).
- Edit and customize keys. Avoid removing the Bluetooth keys entirely (you can move them), or you may lose Bluetooth control.
- Save and exit.

---



#### Pin mapping (as used by the firmware)
- Rows
  - Top row → pin `100`
  - Middle row → pin `106`
  - Bottom row (with 4 keys) → pin `009`
- Columns
  - Column 1 (single key) → pin `010`
  - Column 2 → pin `104`
  - Column 3 → pin `113`
  - Column 4 → pin `002`

Reference image: ![Pinout](files%20and%20media/Pinout%20for%20rows%20and%20columns.png)

---


Exploded view:

![Exploded view](files%20and%20media/exploded%20view.png)

---

### License
Open‑source hardware and firmware. 



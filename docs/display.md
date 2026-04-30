# Display

> **Status: work in progress.** The display is physically installed but the ZMK firmware config is not yet complete.

**Display:** Waizowl nice!view clone (Sharp LS011B7DH03 panel, 5-pin SPI)

---

## Why a bodge wire is needed

The Tidbit's OLED footprint is **I2C** (4 pins). The nice!view clone uses **SPI** (5 pins). They are not directly compatible: the footprint has no hole for the CS (chip select) pin, so it must be wired separately.

## Pin mapping

| Display label | SPI signal | Connection | Wire colour |
|---|---|---|---|
| SCS | CS (chip select) | Bodge wire → 106 (P1.06) on nice!nano | Blue |
| GND | Ground | GND hole in OLED footprint | Black |
| 3V-5V | VCC | VCC hole in OLED footprint | Red |
| SCLK | SCK | SCL hole in OLED footprint | Yellow |
| SI | MOSI | SDA hole in OLED footprint | Green |

## Footprint hole verification

Before wiring, confirm the Tidbit's OLED footprint hole order using a multimeter in continuity mode. With the board unplugged, probe against a known GND pin on the nice!nano and touch each footprint hole to identify which is GND — then map the rest from there.

## Bodge wire

Run a short wire from the **SCS** pin on the display to the **106 (P1.06)** hole on the nice!nano. 28 AWG silicone wire works well — it is thin and flexible.

## Physical mounting

No housing is designed for the display. Use 1mm foam tape on the back of the display to secure it and provide a small standoff gap.

---

## ZMK firmware config (to-do)

Three changes are needed in the firmware once the hardware is ready:

### 1. Enable the display in `config/tidbit.conf`

Uncomment:
```
CONFIG_ZMK_DISPLAY=y
```

### 2. Add a nice!view shield overlay

The nice!view requires SPI configuration. The CS pin must match the GPIO used for the bodge wire (D1/P0.06). Refer to the ZMK docs and the `zmk-nice-view` shield definition for the exact overlay syntax.

### 3. Update ZMK version in `config/west.yml`

The current ZMK pin is `v0.3`. The nice!view shield was added to upstream ZMK after that release, so it will not be available at `v0.3`.

Before bumping the version:
- Check the ZMK changelog for breaking changes to keymap or config syntax between `v0.3` and the target version
- Rebuild and test the keymap after the version bump, as binding names and include paths have changed across releases

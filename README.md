# Nullbits Tidbit Wireless Numpad

A wireless numpad/macropad built on the Nullbits Tidbit PCB, running ZMK firmware on a nice!nano v2 controller with a nice!view clone display and LiPo battery.

**Hardware:** Nullbits Tidbit PCB · nice!nano v2 · Waizowl nice!view clone · 301230 LiPo · EC11 rotary encoder

**Firmware:** ZMK · board `nice_nano_v2` · shield `tidbit`

---

## Quick-start: flashing firmware

1. Double-tap the reset button on the nice!nano — a drive called `NICENANO` appears on your computer
2. Drag the `.uf2` firmware file onto the drive
3. The controller reboots automatically

To build the firmware, see [docs/firmware.md](docs/firmware.md).

---

## Documentation

- [Hardware — BOM and assembly](docs/hardware.md)
- [Firmware — ZMK config and keymap](docs/firmware.md)
- [Display — wiring and ZMK config](docs/display.md) *(work in progress)*

---

## Known issues / to-do

- [ ] 2U zero key — stabiliser fit and feel not yet verified
- [ ] Display ZMK firmware config — to be completed (see [docs/display.md](docs/display.md))
- [ ] Verify OLED footprint hole order with multimeter before display install
- [ ] Optionally: calculator widget on the display (requires forking ZMK)

---

## Resources

- [Nullbits Discord](https://discord.com/invite/nullbits-735314509949829151)
- [ZMK hardware list](https://zmk.dev/docs/hardware)
- [Typeractive docs](https://docs.typeractive.xyz) — good reference for nice!nano socketing and display wiring
- [40% Club build guides](https://www.40percent.club)

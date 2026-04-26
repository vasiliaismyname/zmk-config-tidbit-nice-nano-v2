# Firmware

ZMK firmware, built via GitHub Actions.

- **Board:** `nice_nano_v2`
- **Shield:** `tidbit`

## Setup

1. Fork or clone the [zmk-user-config](https://github.com/zmkfirmware/zmk-user-config) template
2. `build.yaml` is already configured:
   ```yaml
   include:
     - board: nice_nano_v2
       shield: tidbit
   ```
3. Edit `config/tidbit.keymap` for your layout
4. Push to GitHub — Actions builds the firmware automatically
5. Download the `.uf2` artifact from the Actions tab

## Flashing

1. Double-tap the reset button to enter bootloader — a drive called `NICENANO` appears
2. Drag the `.uf2` file onto the drive
3. The controller reboots automatically

## Keymap

Two layers: a default numpad layer and a function layer accessed by holding either of the `lt 1` keys.

### Default layer

```
         NumLock   *       -
  7       8        9       +
  4       5        6       /
  1       2        3       Enter (hold = func)
  0       0 (hold = func)  .       Enter
```

Encoder: volume up / volume down.

### Function layer

```
         —         Reset   Bootloader
  Out    USB       BLE     —
  BT 0   BT prev   BT next BT clear
  BT 1   BT 2      BT 3    —
  Mute   —         —       —
```

Encoder: volume up / volume down (same as default layer).

**Output toggle** (`Out`): cycles between USB and BLE output. `USB` and `BLE` force the specific output.

**BT profiles:** ZMK supports 5 profiles (0–4) by default. The keymap exposes 0–3. To add a fifth, add `&bt BT_SEL 4` to the func layer.

### 2U zero key

The 2U zero occupies two switch positions in the layout. Both positions are bound:

- Left position: `&kp KP_NUMBER_0` — always sends 0
- Right position: `&lt 1 KP_NUMBER_0` — tap for 0, hold for func layer

The right half of the 2U keycap needs to be physically pressable to reach the func layer this way. Verify this after fitting the stabiliser and keycap.

## Notes

- ZMK is **not** compatible with VIA or Vial — all keymap changes require editing `config/tidbit.keymap` and rebuilding
- ZMK is currently pinned to `v0.3` in `config/west.yml`. Display work will require bumping to a newer version — see [docs/display.md](display.md) for details
- Bootloader entry: double-tap reset; the `NICENANO` drive appears within a few seconds

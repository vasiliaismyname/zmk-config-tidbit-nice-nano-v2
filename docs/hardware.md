# Hardware

## Bill of Materials

| Item | Detail | Notes |
|---|---|---|
| PCB kit | Nullbits Tidbit | Includes PCB, acrylic case layers, hardware |
| Controller | nice!nano v2 | Wireless (BLE), ZMK-compatible |
| Display | Waizowl nice!view clone | Sharp LS011B7DH03 panel, 5-pin SPI |
| Battery | JST PH 2mm 3.7V LiPo 301230 | ~110mAh; 30×12×3mm |
| Battery pigtail | JST PH 2mm 2-pin female pigtail cable | Connects battery to B+/B− pads on nice!nano |
| Sockets (controller) | Mill-Max socket pins | Inserted into nice!nano for removability |
| Sockets (PCB) | Machine pin sockets | Soldered into Tidbit PCB; controller plugs in |
| Bodge wire | 28 AWG silicone wire | CS pin bodge from display SCS to GPIO D1/P0.06 |
| Diodes | 1N4148 SOD-123 | One per switch; check if included in kit |
| Switches | MX-compatible | Your choice |
| Keycaps | MX-compatible | Numpad layout; 2U zero key needs a stabiliser |
| Encoder | Rotary encoder (EC11 or compatible) | Optional; used for volume in this build |
| Encoder knob | To fit encoder shaft | Your choice |

## Tools & Consumables

| Item | Notes |
|---|---|
| Soldering iron | Temperature-controlled recommended |
| Solder | 60/40 or 63/37 rosin-core; fine gauge (0.5–0.6mm) |
| Flux | Helps with small pads |
| Multimeter | Essential for polarity checks and continuity testing |
| Electrical tape | Insulation over battery solder joints |
| Tweezers | For placing diodes |

---

## Assembly

### 1. Diodes

Solder diodes to the Tidbit PCB. These are SOD-123 surface-mount components — polarity matters. The cathode band on the diode must match the line marked on the PCB silkscreen.

### 2. Switches

Press switches into the top plate and solder to the PCB. Ensure they are fully seated and straight before soldering.

### 3. Socketing the nice!nano

Rather than soldering the controller directly (which makes it unremovable), use a socket system:

- **Machine pin sockets** are soldered into the Tidbit PCB
- **Mill-Max socket pins** are inserted into the nice!nano's pin holes and soldered on top

This lets you remove the controller later if needed. Key technique: seat the nice!nano into the machine pin sockets during soldering to keep the Mill-Max pins aligned.

**Important:** Leave the **B+** and **B−** holes on the nice!nano empty — no Mill-Max pins here. Battery wires solder directly to these pads.

### 4. Battery wiring

The nice!nano does **not** have a JST socket. The battery connects via two wires soldered to the **B+** and **B−** pads on the underside of the controller.

**Polarity check (mandatory before soldering):**

1. Plug the battery into the pigtail cable
2. Set multimeter to DC voltage mode
3. Touch red probe to red wire, black probe to black wire
4. A positive reading (~3.7V) means red = B+, black = B−
5. If the reading is negative, swap — wire colour convention is not always reliable

**Soldering:**

- Tin both the wires and the pads first
- Work quickly — hold iron on the joint for 1–2 seconds only
- Apply a small piece of electrical tape over the joints as insulation

### 5. Encoder

The Tidbit supports up to four encoders. The encoder in this build is in the **top-left** position, using ZMK label `encoder_1_top_row`.

Valid ZMK encoder labels for the Tidbit shield:

| Label | Position | Notes |
|---|---|---|
| `encoder_1` | Top-left | A/B reversed vs `encoder_1_top_row` |
| `encoder_1_top_row` | Top-left | Correct rotation direction for top-left position |
| `encoder_2` | — | |
| `encoder_3` | — | Cannot be used at the same time as the I2C OLED |
| `encoder_4` | — | |

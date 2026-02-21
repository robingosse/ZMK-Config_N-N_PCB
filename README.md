# GossieKey ZMK Config

Split keyboard firmware for the GossieKey 3×5+3 using nice!nano v2 boards.

## Hardware

| Signal | Pin    |
|--------|--------|
| R0     | P0.17  |
| R1     | P0.20  |
| R2     | P0.22  |
| C0     | P0.29  |
| C1     | P0.02  |
| C2     | P1.15  |
| C3     | P1.13  |
| C4     | P1.11  |
| C5     | P1.02  |
| TRRS TX | P0.06 |
| TRRS RX | P0.08 |
| TRRS VCC | 3V3  |

Left half = central (plug USB here).  
Right half = peripheral (powered via TRRS VCC).

## Building

Push to GitHub — Actions will build automatically using `build.yaml`.  
Artifacts: `gossiekey_left-nice_nano_v2-zmk.uf2` and `gossiekey_right-nice_nano_v2-zmk.uf2`.

Flash by double-tapping the reset button on each nice!nano to enter bootloader mode, then drag-drop the correct .uf2.

## ZMK Studio

With `CONFIG_ZMK_STUDIO=y` enabled, you can edit your keymap live using the  
[ZMK Studio web app](https://zmk.studio) without reflashing. Connect the left half via USB.

## Diode Direction

The overlays are set to `col2row`. This means:
- **Rows are outputs** (driven HIGH)  
- **Cols are inputs** (pulled DOWN)

If keys aren't registering or you get ghost presses, double-check your diode orientation.  
If diodes point the other way, change to `row2col` and swap the `GPIO_ACTIVE_HIGH` /  
`GPIO_PULL_DOWN` flags between `row-gpios` and `col-gpios`.

## Thumb Key Layout

The keymap uses a 3×6 grid per side. In the transform, thumbs are on  
row 2 cols 3/4/5 (left) and cols 6/7/8 (right). Edit `gossiekey.keymap`  
to match your physical thumb key positions.

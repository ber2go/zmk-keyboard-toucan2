# ZMK config for beekeeb Toucan2 Keyboard

[The beekeeb Toucan2 Keyboard](https://beekeeb.com/introducing-toucan2/) is a wireless split 42-key column‑stagger keyboard that a display and a trackpad, with an aggressive stagger on the pinky columns.

# Customizations

- **Keymap**: [config/toucan.keymap](config/toucan.keymap)
- **General configs**: [boards/shields/toucan/toucan_left.conf](boards/shields/toucan/toucan_left.conf) and [boards/shields/toucan/toucan_right.conf](boards/shields/toucan/toucan_right.conf)
- **Swipe shortcuts**: the `swipe_button_mapper` node in [boards/shields/toucan/toucan.dtsi](boards/shields/toucan/toucan.dtsi)
- **Invert scroll / trackpad settings**: the `tps43_trackpad` node in [boards/shields/toucan/toucan_right.overlay](boards/shields/toucan/toucan_right.overlay)

# Keymap

Auto-generated with [keymap-drawer](https://github.com/caksoylar/keymap-drawer) on every keymap change (see [keymap-drawer.yaml](.github/workflows/keymap-drawer.yaml)).

![Toucan2 keymap](keymap-drawer/toucan.svg)

# Debugging with USB logging

`CONFIG_ZMK_USB_LOGGING=y` in the `.conf` files enables serial logging over USB, which shows each key position and whether a home row mod resolved as tap or hold. Rebuild and reflash after changing it. Remove it when done, since it increases power use and can add latency.

**Reading the log by OS**

- **macOS:** `screen /dev/tty.usbmodem* 115200`
- **Linux:** `screen /dev/ttyACM0 115200` (you may need to be in the `dialout` group)
- **Windows:** Open PuTTY or Tera Term, choose Serial, pick the COM port shown in Device Manager, and set 115200 baud.
- **Any OS:** The `serial-monitor` extension in VS Code, or `python -m serial.tools.miniterm <port> 115200` (requires `pyserial`).

**Caveats**

- The keyboard must be connected over USB. The log doesn't come through Bluetooth.
- Only the half you plug in logs its own events. On a split keyboard, the central half (usually left) also reports the other half's key presses.
- If you use ZMK's `zmk-usb-logging` snippet instead, the config line isn't needed, but your build setup must support snippets.

# License

The code in this repo is available under the MIT license.

The included shield nice_view_gem is modified from https://github.com/M165437/nice-view-gem licensed under the MIT License.

The linked trackpad module is based on https://github.com/geeksville/zmk_driver_azoteq

ZMK code snippets are taken from the ZMK documentation under the MIT license.

The embedded font QuinqueFive is designed by GGBotNet, licensed under under the SIL Open Font License, Version 1.1.

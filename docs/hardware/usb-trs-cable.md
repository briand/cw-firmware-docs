# USB-C to TRS Paddle Cable (UV-K5 v3 / UV-K1)

The UV-K5 v3 and UV-K1 both have a USB-C port that is connected to the microcontroller (the USB-C port in the K5 v1 is for charging only). The CW firmware can read a
paddle directly off that port's `DP`/`DM` data lines as plain GPIO inputs —
it does not speak USB protocol to do this, it just reads the raw line
state. A cable that wires a standard TRS paddle plug straight to the
USB-C connector's data pins lets you use any off-the-shelf iambic paddle
without opening the radio.

This is the v3/K1 equivalent of the [CEC cable](cec-cable.md) trick used on
the original UV-K5 — a no-rework way to plug in a paddle — but since v3/K1
expose real digital lines on USB-C instead of a single ADC line, the wiring
is direct, with no resistors or calibration involved.

!!! important
    This cable is **not** a "USB-C audio adapter" or any other USB-C to 1/8" TRS adapter device that you might find on Amazon today. It's a passive cable with no electronics, and it doesn't match any standard cable that device manufacturers currently make. You will have to custom build this cable.

## How it works

- **DP** (USB D+) — wire to the paddle's TRS **Tip** (dit contact). This wire is _usually_ green inside most USB cables.
- **DM** (USB D−) — wire to the paddle's TRS **Ring** (dah contact). This wire is _usually_ white inside most USB cables.
- **USB ground** — wire to the paddle's TRS **Sleeve** (common/ground).

Select one of the `USB Port` options under
[`CWkin`](../menus-and-settings.md#cw-key-input-cwkin) to enable reading
the paddle this way — see that page for the available USB Port input
modes (USB Port Iambic, USB Port Iambic Reversed, Handkey). If D+/D- got swapped because of non-standard coloring, just pick the Reversed mode as needed.

!!! note
    The built-in USB functionality (serial port, etc) will not function while the radio is in CW mode with a USB Port input mode. It will return to functioning when the mode is switched away from USB, or away from a USB Port mode.

    The headset port serial will continue to work.

## Wiring Diagram

![USBC-TRS wiring diagram](../assets/USBC_TRS_cable.drawio.png)

## Next

- [Menus and settings — CW Key Input](../menus-and-settings.md#cw-key-input-cwkin)
- [CW paddle input overview](cw-paddle-input.md)
- [Paddle rework overview](rework-overview.md)

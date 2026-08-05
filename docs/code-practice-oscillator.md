# Code Practice Oscillator (CPO)

CPO mode turns the radio into a standalone CW practice buzzer: no
receiving, no transmitting, just sidetone and an on-screen decode of what
you key in iambic modes. It's useful for practicing copy and sending without making RF.

Because it doesn't transmit, using the CPO does not require a license, except in some jurisdictions where a license is required to own any radio equipment regardless of use.

## Entering CPO

=== "UV-K5 (v1 original)"

    Long press **5**.

=== "UV-K5 v3 / UV-K1"

    Press **F**, then long press **5**. The radio's current VFO must
    already be set to CW mode (`Modulation` = CW) — if it isn't, you'll
    get an error beep instead of entering CPO.

While in CPO, the radio doesn't receive or transmit. Use your normal
[CW key input](menus-and-settings.md#cw-key-input-cwkin) to send — CPO
plays it back as sidetone and decodes it on screen as you go. To change the keyer style or input method, exit the CPO and enter the Menu from the main screen.

## Exiting CPO

Tap **EXIT**. If you changed the WPM while inside CPO, the new speed is
saved as your normal `CWwpm` setting on the way out.

## Button reference

| Button | Action |
|---|---|
| **EXIT** | Leave CPO and return to the main screen. |
| **UP** / **DOWN** | Adjust sending speed in WPM (range 10–45 inside CPO). Saved as your `CWwpm` setting on exit if changed. |
| **\*** | Toggle the backlight on/off for the duration of CPO. |
| **4** | Toggle flashlight-on-key-down, so the flashlight LED flashes in time with your sending. |
| **5** | Clear the previously decoded text. |

## See also

- [Menus and Settings](menus-and-settings.md) for the CW menu items CPO
  reads its defaults from (`CWfreq`, `CWvol`, `CWwpm`, `CWkin`, `CWkmod`).

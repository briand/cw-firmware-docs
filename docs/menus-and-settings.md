# Menus and Settings

The CW firmware adds a block of menu items to the stock UV-K5/UV-K1 menu, all
prefixed with `CW` on the radio's display. This page documents what each one
does, the values you can set, and where the original UV-K5 (v1) hardware
differs from the UV-K5 v3 and UV-K1.

Open the menu with **M**, then scroll (or long-press a number key to jump)
until you reach the `CW...` entries.

## CW Tone Frequency — `CWfreq`

Sets the sidetone (and transmitted CW tone) frequency.

- Range: 450 Hz to 800 Hz, in 50 Hz steps.
- Default: 600 Hz.

## CW Sidetone Volume — `CWvol`

Sets the volume of the sidetone you hear in your speaker while
sending.

- Range: `OFF`, then levels 1–6.
- Default: level 4.

This only affects what you hear locally — it has no effect on the
transmitted signal. `OFF` is only really useful if you're using an external keyer that has its own sidetone.

## CW Keyer Mode — `CWkmod`

Selects the iambic keyer timing behavior used when a paddle input is
selected in [`CWkin`](#cw-key-input-cwkin).

- **Mode A** — Curtis iambic Mode A style, edge-triggered dit/dah memory
- **Mode B** — Accu-keyer iambic Mode B style, dit/dah memory, adds the trailing opposite element when both paddles are released during an element, and Elecraft-style partial edge-triggering

Default: Mode B.

## CW Keying Speed — `CWwpm`

Sets the keyer speed in words per minute. Applies to both the iambic keyer
and the macro message playback speed.

=== "UV-K5 v3 / UV-K1"

    - Range: 10–40 WPM.

=== "UV-K5 (v1 original)"

    - Range: 10–30 WPM.

Default: 18 WPM (both builds).

## CW Key Input — `CWkin`

Selects what hardware is used as the paddle/key input, and whether the
keyer logic (iambic timing) is applied to it or the input is treated as a
plain hand key.

=== "UV-K5 v3 / UV-K1"

    | Setting | Description |
    |---|---|
    | PTT HandKey | PTT button is a straight key. No iambic keyer. |
    | Port HandKey | External port acts as a straight key. No iambic keyer. |
    | Side Btn Iambic | PTT = dah, Side button 1 = dit. Iambic keyer active. |
    | Side Btn Iambic Reversed | Same as above with dit/dah swapped. |
    | Port Iambic | External 2-pin port wired as a paddle. Iambic keyer active. |
    | Port Iambic Reversed | Same as above with dit/dah swapped. |
    | Port+Btn Iambic | Port paddle plus Side button 1, either can send dit/dah. Iambic keyer active. |
    | Port+Btn Iambic Reversed | Same as above with dit/dah swapped. |
    | USB Port Iambic | Paddle wired through the USB-C connector. Iambic keyer active. |
    | USB Port Iambic Reversed | Same as above with dit/dah swapped. |

    The UV-K5 v3 and UV-K1 detect the USB paddle digitally, so no
    calibration step is required.

=== "UV-K5 (v1 original)"

    | Setting | Description |
    |---|---|
    | PTT HandKey | PTT button is a straight key. No iambic keyer. |
    | Port HandKey | External port acts as a straight key. No iambic keyer. |
    | Side Btn Iambic | PTT = dah, Side button 1 = dit. Iambic keyer active. |
    | Side Btn Iambic Reversed | Same as above with dit/dah swapped. |
    | Port Iambic | External 2-pin port wired as a paddle. Iambic keyer active. |
    | Port Iambic Reversed | Same as above with dit/dah swapped. |
    | Port+Btn Iambic | Port paddle plus Side button 1, either can send dit/dah. Iambic keyer active. |
    | Port+Btn Iambic Reversed | Same as above with dit/dah swapped. |
    | CEC Cable | Paddle wired through a CEC-style cable, detected by reading a resistor value on the audio/CEC line. Iambic keyer active. |
    | CEC Cable Reversed | Same as above with dit/dah swapped. |
    | CEC Cable Handkey | CEC cable input treated as a straight key. No iambic keyer. |

    !!! note "Calibrate the CEC cable before first use"
        The original UV-K5 doesn't have a dedicated digital paddle port, so
        the CEC cable modes identify the dit/dah contacts by reading an
        analog voltage produced by a resistor in the cable. See the
        [CEC paddle cable page](hardware/cec-cable.md) for how the cable
        works and how to build one. Use
        [`CWcrd`, `CWcLo`, and `CWcHi`](#cec-cable-calibration-uv-k5-v1-only)
        to calibrate these thresholds for your specific cable before
        relying on a CEC cable mode.

    PTT can't be used at the same time as a CEC Cable mode, since the same
    line is shared.

Default: PTT HandKey.

## CW Messages — `CWmsg1` – `CWmsg4`

Four programmable memory slots for short CW macros (callsign, CQ call,
report exchange, etc).

Selecting a slot shows its current contents (or `empty`), and lets you
choose:

- **Record new?** — start recording. Key the message using your configured
  paddle/key input, then exit the submenu to save it.
- **Play** — send the stored message once.
- **Repeat** — send the stored message repeatedly, with the delay set by
  [`CWmrpt`](#cw-message-repeat-delay-cwmrpt) between repeats.

Recording and playback both require the radio to be in CW mode (TX
modulation set to CW). The keyer must also be working — if key input
validation has failed, playback/recording for these slots is blocked.

## CW Message Repeat Delay — `CWmrpt`

Sets the pause, in seconds, between repeats when playing a message in
repeat mode.

- Range: 0–127 seconds.
- Default: 4 seconds.

## CW Break-in — `CWbkin`

When enabled, sending CW automatically keys the transmitter for the
duration of your sending (full break-in / QSK-style behavior driven by the
keyer), rather than requiring a separate PTT press.

- Range: `OFF` / `ON`.
- Default: `ON`.

## CEC Cable Calibration (UV-K5 v1 only)

These three menu items only appear on the original UV-K5, where a CEC-style
cable is used as a paddle input and is identified by an ADC reading of a
resistor value in the cable rather than a dedicated digital input. They are
not present on the UV-K5 v3 or UV-K1, which read a real digital paddle
signal over the USB-C port and need no calibration. See the
[CEC paddle cable page](hardware/cec-cable.md) for how the cable works and
how to build one.

- **`CWcrd`** — ADC Read Check. Open this submenu with your cable plugged
  in and a paddle contact held closed to see the live ADC reading, which
  you then use to set the two thresholds below.
- **`CWcLo`** — the ADC threshold for the lower-resistance ("20k") contact.
- **`CWcHi`** — the ADC threshold for the higher-resistance ("10k") contact.

Use `CWcrd` to read the ADC value for each paddle contact pressed
individually, then set `CWcLo` and `CWcHi` to those readings so the
firmware can reliably tell the two contacts apart.

## Model-specific notes

The differences above come from real hardware differences, not arbitrary
firmware choices:

- The UV-K5 v3 and UV-K1 expose a real digital paddle signal on their
  USB-C port, so paddle detection is immediate and needs no calibration,
  and Semi Bug keying and faster WPM ranges are available because of
  headroom in the updated keyer implementation.
- The original UV-K5 has no dedicated paddle port. The CEC cable mode
  reuses an existing audio/CEC line and tells the two paddle contacts
  apart by reading an analog voltage, which varies cable to cable and
  needs the one-time calibration described above.

See the [hardware overview](hardware/index.md) and
[identify your radio](hardware/identify-your-radio.md) pages if you're not
sure which hardware you have.

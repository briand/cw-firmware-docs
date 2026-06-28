# Menus and Settings

The CW firmware adds a block of menu items to the stock UV-K5/UV-K1 menu, all
prefixed with `CW` on the radio's display. This page documents what each one
does, the values you can set, and where the original UV-K5 (v1) hardware
differs from the UV-K5 v3 and UV-K1.

Open the menu with **M**, then scroll (or press a number key to jump)
until you reach the `CW...` entries.

!!! tip
    The `CW` entries are the last ones in the menu, so when you first turn the radio on, you can scroll up to reach them immediately.

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
- **Ultimatic** — both paddles squeezed at once sends whichever one was pressed *most recently*, rather than alternating dit/dah like the iambic modes. No dit/dah memory.
- **Bug** — semi-automatic bug keyer. The dah paddle behaves like a plain hand key (hold it down for a continuous dah, any length). The dit paddle auto-repeats dits at the configured [`CWwpm`](#cw-keying-speed-cwwpm) speed for as long as it's held, with no trailing element or extra gap when released.

Default: Mode B.

## CW Keying Speed — `CWwpm`

Sets the keyer speed in words per minute. Applies to both the iambic keyer
and the macro message playback speed.

- Range: 10–45 WPM.

Default: 18 WPM.

## CW Key Input — `CWkin`

Selects what hardware is used as the paddle/key input, and whether the
keyer logic (iambic timing) is applied to it or the input is treated as a
plain hand key.

When an input mode other than PTT or Side Btn is chosen, the firmware will test the iambic inputs. If a short is detected, the screen will show `key err` and will not accept the mode change. 

The short-detect routine also runs at radio startup, and if a stuck key is detected the display will show `CW KEY STUCK` and revert to PTT HandKey input mode temporarily. To fix this: turn the radio back off, release the keys, and turn it on again to re-initialize the input mode.

#### Common input configs (all radios)

  | Setting | Description |
  |---|---|
  | PTT HandKey | PTT button is a straight key. No iambic keyer. |
  | Port HandKey * | External port acts as a straight key. No iambic keyer. |
  | Side Btn Iambic | PTT = dah, Side button 1 = dit. Iambic keyer active. |
  | Side Btn Iambic Reversed | Same as above with dit/dah swapped. |
  | Port Iambic * | External 2-pin port wired as a paddle. Iambic keyer active. |
  | Port Iambic Reversed * | Same as above with dit/dah swapped. |
  | Port+Btn Iambic * | Port paddle plus Side button 1, either can send dit/dah. Iambic keyer active. |
  | Port+Btn Iambic Reversed * | Same as above with dit/dah swapped. |

!!! note
    (*) The 'Port' input modes [require rework](hardware/rework-overview.md)

#### Model-specific input configs

=== "UV-K5 (v1 original) only"

    | Setting | Description |
    |---|---|
    | CEC Cable | Paddle wired through a CEC-style cable, detected by reading a resistor value on the audio/CEC line. Iambic keyer active. |
    | CEC Cable Reversed | Same as above with dit/dah swapped. |
    | CEC Cable Handkey | CEC cable input treated as a straight key on either paddle contact, no iambic keyer. |

    !!! note
        The 'CEC' input modes require a [custom CEC cable](hardware/cec-cable.md)


=== "UV-K5 v3 / UV-K1 only"

    | Setting | Description |
    |---|---|    
    | USB Port Iambic | Paddle wired through the USB-C connector. Iambic keyer active. |
    | USB Port Iambic Reversed | Same as above with dit/dah swapped. |
    | USB Port Handkey | USB-C TRS input treated as a straight key on either paddle contact, no iambic keyer. |

    !!! note
        The 'USB Port' input modes require a [USB-C to TRS cable](hardware/usb-trs-cable.md)




Default: PTT HandKey.

## CW Messages — `CWmsg1` – `CWmsg4`

Four programmable memory slots for short CW macros (callsign, CQ call,
report exchange, etc). Messages may be up to 46 characters each, not including spaces.

Selecting a slot shows its current contents (or `empty`), and lets you
choose:

- **Record new?** — start recording. Key the message using your configured
  paddle/key input, then use the `M` button to save it. `exit` will exit macro recording without saving. An iambic input mode must be used; recording from handkey does not work.
- **Play** — send the stored message once.
- **Repeat** — send the stored message repeatedly, with the delay set by
  [`CWmrpt`](#cw-message-repeat-delay-cwmrpt) between repeats.

Recording and playback both require the radio to be in CW mode (TX
modulation set to CW). Break-in (`CWbkin`) must be enabled for a message to transmit RF, otherwise it will play sidetone only. Messages will play with the WPM set in `CWwpm`.

!!! tip
    Message play and repeat actions may also be mapped to a keypress, using the menu items `F1Short`, `F1Long`, `F2Short`, `F2Long`, `M Long`.

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

!!! note
    These items are in the "hidden tech menu". Enable by powering on the radio while holding the PTT and first side button.

These three menu items only appear on the original UV-K5, where a CEC-style
cable is used as a paddle input and is identified by an ADC reading of a
resistor value in the cable rather than a dedicated digital input. They are
not present on the UV-K5 v3 or UV-K1. See the
[CEC paddle cable page](hardware/cec-cable.md) for how the cable works and
how to build one.

- **`CWcrd`** — ADC Read Check. Shows the CEC input value.
- **`CWcLo`** — set the ADC threshold for the low value ("20k") contact.
- **`CWcHi`** — set the ADC threshold for the high value ("10k") contact.

Connect a paddle via a CEC cable, then use `CWcrd` to read the ADC value for each paddle contact pressed individually. Set `CWcLo` and `CWcHi` to those readings so the firmware can reliably tell the two contacts apart.

## Model-specific notes

Each model's CW mod firmware (v1 vs the v3/k1) is based on a different original firmware (see [Upstream projects](index.md#upstream-projects) for more). Each adds unique additional menu items that are not part of the CW mod. See their respective documentation for more details about those non-CW features and menu items.

See the [hardware overview](hardware/index.md) and
[identify your radio](hardware/identify-your-radio.md) pages if you're not
sure which hardware you have.

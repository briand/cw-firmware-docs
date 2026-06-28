# Main Screen

This page covers what you see on the radio's main (VFO) screen while
sending or receiving CW, and the button shortcuts that are specific to CW
mode.

## CW decode display

While in CW mode, the firmware decodes what's being keyed — your own
sending, or whatever Morse it hears on the receive audio — and prints the
decoded text across the middle line of the screen.

- Shows up to ~19 characters at a time; once the line fills, older text
  scrolls off the left as new characters are decoded.
- A small play-arrow glyph appears at the far left of the line while a
  [recorded message](menus-and-settings.md#cw-messages-cwmsg1-cwmsg4) is
  being played back.

## Button shortcuts

These long-press shortcuts are active on the main screen.

| Button | Action |
| --- | --- |
| Long press `0 / FM` | Cycle modulation: FM → AM → USB → CW → (back to FM) |
| Long press `4 / FC` (UV-K5 v3 / UV-K1: **`F`**, then long press `4`) | Cycle filter width (only while in CW mode) |
| Long press `5 / NOAA` (UV-K5 v3 / UV-K1: **`F`**, then long press `5`) | Launch the [Code Practice Oscillator](code-practice-oscillator.md) |
| Long press `7 / VOX` | Toggle CW break-in (`CWbkin`) on/off |
| Long press `8 / R` | Toggle SSB cross-mode |

Filter width and CPO are the only two of these that need the **F** prefix
on the UV-K5 v3 / UV-K1 — on the original UV-K5 (v1) both are plain long
presses, same as the other three shortcuts. Modulation cycling, break-in,
and cross-mode are plain long presses (no F prefix) on every model.

### Modulation cycling — long press `0/FM`

Cycle between the modulation modes: FM → AM → USB → CW → (back to FM)

The firmware automatically opens squelch full-time whenever switching to USB and CW modes. Use side button 1 (or map a different button to the `monitor` action) to close squelch.

!!! warning
    Selecting **USB** mode lets you *receive* and listen to upper-sideband
    SSB signals — the radio listens to baseband from the carrier frequency so
    SSB audio sounds right. It does **not** transmit SSB. If you key up while
    in USB mode, the radio still transmits plain FM.

    FM still carries a recognizable amplitude pattern that roughly follows
    the SSB envelope, so an SSB operator listening to your FM transmission
    will likely be able to make out what you're saying — but it will sound
    rough, since they're decoding an FM signal as if it were SSB.

### Filter width — long press `4/FC`

Only does this while the radio is in CW mode, in the other modes this will launch the scanner. Cycles through the available IF filter bandwidths, which can help narrow out other signals or noise next to the one you're trying to copy. The current filter width (when not the default "wide" setting) is shown in the status area of the screen.

### Code Practice Oscillator — long press `5/NOAA`

Launches [CPO](code-practice-oscillator.md), a standalone practice buzzer
mode that doesn't receive or transmit. On the UV-K5 v3 / UV-K1 the radio's
current VFO must already be in CW mode or you'll get an error beep instead
— see the [CPO page](code-practice-oscillator.md#entering-cpo) for the
exact entry steps per model.

### Break-in toggle — long press `7/VOX`

Toggles the same [`CWbkin`](menus-and-settings.md#cw-break-in-cwbkin)
setting found in the menu, without having to go into the menu. A `BKIN`
indicator appears at the top of the screen, in the status bar, whenever
break-in is enabled while in CW mode; it disappears when break-in is
turned off.

### SSB cross-mode — long press `8/R`

Cross-mode shifts your transmitted CW signal's frequency up by the sidetone
tone frequency ([`CWfreq`](menus-and-settings.md#cw-tone-frequency-cwfreq)),
putting it inside the passband an SSB operator will hear when listening at the given frequency. That lets you work an SSB station in "cross-mode": they hear your keyed CW tone (at your programmed sidetone frequency), and your own receive hears their voice without having to retune. For example, if the op is listening at 144.200 USB, and your sidetone is programmed to 600Hz, they will hear a 600Hz tone when you transmit on 144.200 with cross-mode enabled - your radio is actually transmitting at 144.200.6 and then jumping back to .200 to listen to them.

Without cross-mode, your CW signal will be at 0hz from their VFO frequency, and the SSB AF bandpass prevent them from hearing you without dropping their VFO or changing to CW mode themselves.

While cross-mode is on, the modulation indicator on the main screen shows
`CWx` instead of plain `CW`.

Default: off. The toggle reverts to off on every power cycle.

## Next

- [Menus and settings](menus-and-settings.md)
- [Code Practice Oscillator](code-practice-oscillator.md)

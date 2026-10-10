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
- On the UV-K5 v3 / UV-K1, zeros are drawn dotted so they can't be mistaken
  for the letter O.

## Button shortcuts

These long-press shortcuts are active on the main screen.

| Button | Action |
| --- | --- |
| Long press `0 / FM` | Cycle modulation: FM → AM → USB → CW → (back to FM) |
| Long press `4 / FC` (UV-K5 v3 / UV-K1: **`F`**, then long press `4`) | Change filter width |
| Long press `5 / NOAA` (UV-K5 v3 / UV-K1: **`F`**, then long press `5`) | Launch the [Code Practice Oscillator](code-practice-oscillator.md) |
| Long press `7 / VOX` | Toggle CW break-in (`CWbkin`) on/off |
| Long press `8 / R` | Toggle SSB cross-mode |

Filter width and CPO are the only two of these that need the **F** prefix
on the UV-K5 v3 / UV-K1 — on the original UV-K5 (v1) both are plain long
presses, same as the other three shortcuts. Modulation cycling, break-in,
and cross-mode are plain long presses (no F prefix) on every model.

On the UV-K5 v3 / UV-K1, a short press of `*` in CW mode opens
[RIT/XIT adjust](#rit-xit). In other modes `*` works as before.

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

=== "UV-K5 v3 / UV-K1"

    Press **F**, then long press **4** to switch the filter between wide and
    narrow. In CW and USB those are 6.25 kHz and 2.0 kHz, and the VFO's info
    line shows `6k` or `2k`. The narrow filter helps cut out signals and noise
    next to the one you're trying to copy. In FM and AM the same press switches
    that mode's own wide and narrow widths.

    Switching a VFO to CW selects the 2k filter. Switching it back to FM or AM
    puts back the width it had before.

    The `WIDE NARROW` [side-key action](#side-key-actions) switches the same
    filter.

=== "UV-K5 (v1 original)"

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

## RIT/XIT (UV-K5 v3 / UV-K1 only) {#rit-xit}

RIT shifts your receive frequency and XIT your transmit frequency by the
same offset, up to ±9.99 kHz in 10 Hz steps, without moving the dial. You can
turn either or both on. The offset and switches live in memory only, so the
radio always powers on with both off and the offset at zero.

In CW mode, press `*` to open the adjust screen. If RIT and XIT are both off
when you open it, RIT turns on. The screen shows the received signal (S-units
or S9+dB, plus dBm) for peaking the offset on a station, the offset in kHz,
`RIT` and `XIT` (highlighted when on), the frequency the offset puts you on,
and a key legend.

| Key | Action |
|---|---|
| **1** / **3** | -10 Hz / +10 Hz |
| **4** / **6** | -100 Hz / +100 Hz |
| **7** / **9** | -1 kHz / +1 kHz |
| Arrow keys | ±10 Hz. Which arrows follows the `SetNav` setting. |
| **2** | RIT on/off |
| **8** | XIT on/off |
| **5** | Zero the offset |
| **0** | Move the dial by the offset and zero it (VFO mode, and only when the new frequency is in band) |
| **\*** or **EXIT** | Close |

The screen also closes when you start keying, or after 5 seconds without a
key press. While an offset is applied, the VFO's info line shows a tag such as
`R+0.12` (RIT), `X-0.05` (XIT) or `RX+0.12` (both), in kHz.

The radio's error beep can't sound in CW, so a key the screen can't act on
plays a single dit on the sidetone instead. That's a step past ±9.99 kHz (the
offset stops at the limit), **0** when it can't move the dial, and **M** or
**F**.

## CW side-key actions (UV-K5 v3 / UV-K1 only) {#side-key-actions}

You can assign these actions to the side keys and to a long press of **M**,
in the `F1Shrt`, `F1Long`, `F2Shrt`, `F2Long` and `M Long` menus or from
CHIRP. The [CW message](menus-and-settings.md#cw-messages-cwmsg1-cwmsg4) play
and repeat actions are in the same list.

| Action | What it does |
|---|---|
| CW KEYER MODE | Steps through Iambic A, Iambic B, Ultimatic and Bug, like [`CWkmod`](menus-and-settings.md#cw-keyer-mode-cwkmod), and shows the new mode in a popup. |
| PROPER ROGER | Sends a "proper roger": an R with a long dah (di-daaaah-dit). [`CWrgr`](menus-and-settings.md#cwrgr) sets the dah length. The LED glows amber while it sends. CW mode only; other modes give an error beep. |
| CW SPEED | Opens a popup where the arrow keys change the keyer speed (10–45 WPM) while you listen. The speed is saved when the popup closes. In CW, a step past 10 or 45 WPM plays a single dit on the sidetone, since the radio's error beep can't sound in CW. |
| CW KEY INPUT | The first press shows the current [key input](menus-and-settings.md#cw-key-input-cwkin), and each further press (or the arrow keys) steps to the next one. Press **M** to apply it. The popup shows a ✓ at its left end for **M** (with a small `M` beside it when `SetNav` is UP/DOWN) and an ✗ at its right end for **EXIT**. **EXIT**, keying, any other key, or 5 seconds without a key press cancels it. If the new input reads as stuck, the radio goes back to PTT HandKey and shows `KEY STUCK`. |
| CW BREAK-IN | Turns [break-in](menus-and-settings.md#cw-break-in-cwbkin) on or off, the same as long press **7**. The `BKIN` icon shows the result. |
| CODE PRACTICE | Opens the [Code Practice Oscillator](code-practice-oscillator.md). |

The keyer mode, speed and key input popups sit over the middle of the main
screen. The arrows on the speed and key input popups follow `SetNav`:
left/right with LEFT/RIGHT, up/down with UP/DOWN.

- **M** or **EXIT** closes a popup. For key input, only **M** applies the new
  input.
- Any other key closes the popup and then does its normal job, so you can
  start typing a frequency straight away.
- Keying or transmitting closes it too. A new speed stays; a key input you
  haven't applied with **M** is dropped.
- Pressing the same side key again steps the popup or closes it. A side key
  with a different action closes the popup and runs that action.
- The keyer mode and speed popups close after 2 seconds without a key press.
  The key input popup closes after 5 seconds, without applying the new input.

### Default key layout

On a new radio, or after a Reset ALL, the keys start with this layout:

| Key | Default action |
|---|---|
| `F1Shrt` | PROPER ROGER |
| `F1Long` | PLAY CW MSG 1 |
| `F2Shrt` | CW SPEED |
| `F2Long` | CW KEY INPUT |
| `M Long` | MONITOR |

These defaults only fill keys that have never been set. Once you assign an
action, from the menu or from CHIRP, the radio keeps it, and a radio upgraded
from earlier firmware keeps the actions it already had.

## Transmit timeout (UV-K5 v3 / UV-K1 only) {#tx-timeout}

If keying runs for 7 seconds without a gap of at least two dit lengths, the
radio stops keying, drops transmit, and shows `TX TIMEOUT` / `RELEASE KEY`.
Normal sending always pauses between characters, so this catches a stuck key
or a shorted paddle, including one that sends an endless string of dits.
Holding the key down for a long tuning carrier trips it too. Keying stays
locked out until the key has been released for 1 second. A
message that's playing back stops too.

## Next

- [Menus and settings](menus-and-settings.md)
- [Code Practice Oscillator](code-practice-oscillator.md)

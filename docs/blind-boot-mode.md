# Blind Boot Mode and Say Label (UV-K5 v1 only)

The UV-K5 (v1) firmware has an accessibility mode for operators who can't
see the screen. One key combination at power-on sets the radio up to speak
its frequency, read menus aloud in voice or CW, and let you set and check
your keyer speed by ear.

!!! note
    Blind boot mode, SAY LABEL and CW enunciation are only in the UV-K5 (v1)
    firmware. The UV-K5 v3 / UV-K1 firmware doesn't have them yet.

## Turning it on

1. Turn the radio off.
2. Hold **PTT** and **side key 2**, the lower of the two small buttons under
   PTT.
3. Turn the radio on while still holding both.
4. Let go of both buttons.

The radio starts up normally once both buttons are released. Because voice
prompts are now on, it says "Welcome", then "Frequency mode" or "Channel
mode" depending on how the VFO is set.

The power switch is also the volume knob, so at power-on the volume may be
too low to hear the welcome. To confirm another way, turn the volume up and
press side key 2 on the main screen. If you hear the frequency read out,
blind boot mode is set.

!!! tip
    Don't confuse this with **PTT + side key 1** at power-on. That opens the
    hidden tech menu and also sets the key input back to PTT HandKey.

## What it changes

Blind boot mode sets these, whatever they were before:

| Setting | Becomes |
|---|---|
| `Voice` | On |
| `F2Shrt` (side key 2, short press) | [SAY LABEL](#say-label) |
| `F2Long` (side key 2, long press) | [CW SPEED](#setting-your-speed-by-ear) |
| [`CWvol`](menus-and-settings.md#cw-sidetone-volume-cwvol) | Level 2, only if it was `OFF`. A sidetone level you'd already set is kept. |

The settings are saved right away, so they stay after you turn the radio
off. You only need to do this once. Nothing else changes: your channels, CW
settings and side key 1 actions are left as they were.

Side key 2 was picked because side key 1 is the dit paddle in the Side Btn
[key inputs](menus-and-settings.md#cw-key-input-cwkin), so SAY LABEL and CW
SPEED stay usable with any key input. If you don't use button keying, Side button 2 can be used for other actions as usual.

The sidetone matters because CW enunciation plays on it: with `CWvol` at
`OFF`, anything sent in CW is silent.

To undo it, set `Voice`, `F2Shrt`, `F2Long` and `CWvol` back the way you
want them in the menus. There are no other permanent changes made.

## Say Label {#say-label}

SAY LABEL is a side-key action that reads out what's on the screen. Blind
boot mode puts it on a short press of side key 2, and you can also assign it
to any side key or to a long press of **M** in the `F1Shrt`, `F1Long`,
`F2Shrt`, `F2Long` and `M Long` menus, or from CHIRP.

What it reads depends on where you are:

| Screen | What you hear |
|---|---|
| Main screen | The frequency of the active VFO, the one you'd transmit on, in voice. |
| Menu, scrolling the list | The highlighted menu item's name, in CW. |
| Menu, changing a value | The value shown on screen, in CW. |
| Anywhere else | Nothing. |

SAY LABEL only works with `Voice` on. With voice off it does nothing.

### Frequency readout

The frequency is spoken as single digits: the MHz part, a short pause, then
up to four digits after the decimal point, with trailing zeros dropped.

| Display | Spoken |
|---|---|
| 144.200 | "one four four" … "two" |
| 146.520 | "one four six" … "five two" |
| 432.0625 | "four three two" … "zero six two five" |
| 146.025 | "one four six" ... "zero two five" |

In channel mode it reads the channel's frequency, not its number or name.

### Menu readout

In the menu, SAY LABEL sends in CW, even for items that have a voice clip.
Anything Morse has no character for, such as spaces, line breaks or a decimal point, becomes a word gap. Some
examples:

| On screen | Sent |
|---|---|
| `CWwpm` | CWWPM |
| `18 WPM` | 18 WPM |
| `600 Hz` | 600 HZ |
| `Dah` / `9 dits` | DAH 9 DITS |

Very long values are cut off after about 24 characters.

## CW enunciation

With `Voice` on, the radio also announces some things on its own. Anything
with a voice clip is spoken as usual, and the rest is sent in CW:

- **Opening a menu item with M:** the item's name is spoken, or sent in CW
  if it has no voice clip, which includes all the `CW` items except
  `CWbkin`, which uses the spoken "VOX" clip. Scrolling the list is silent,
  so use [SAY LABEL](#say-label) to hear where you are.
- **Long press 0 (rotate modulation):** sends the new mode's name, `FM`, `AM`, `USB`
  or `CW`.
- **Long press 7 (break-in toggle) in CW mode:** says "VOX on" or "VOX off".
- **Entering code practice:** sends `CPO`.
- **CW SPEED popup:** sends a `5` at each speed. See
  [below](#setting-your-speed-by-ear).

CW enunciation always uses your settings:

- Pitch: [`CWfreq`](menus-and-settings.md#cw-tone-frequency-cwfreq)
- Volume: [`CWvol`](menus-and-settings.md#cw-sidetone-volume-cwvol)
- Speed: [`CWwpm`](menus-and-settings.md#cw-keying-speed-cwwpm)

It's sidetone only and never transmits, in any mode. It starts once you let
go of the key that triggered it, and receive audio is muted while it plays,
even with squelch open, so static doesn't cover it. It won't start while
you're transmitting, keying or playing a message, and any keying or message
playback cuts it short.

## Setting your speed by ear {#setting-your-speed-by-ear}

The CW SPEED popup is on a long press of side key 2 after a blind boot. It
works from the main screen in any mode:

1. Long press side key 2. The radio sends a `5` (five dits) at your current
   speed.
2. Press **UP** or **DOWN** to change the speed by 1 WPM. Each step sends
   another `5` at the new speed. The range is 10–45 WPM, and a step past
   either end gives an error beep.
3. Press **MENU** or **EXIT**, long press side key 2 again, or just start
   keying. The new speed is kept and saved.

With `Voice` on, the popup stays open until you close it, so you can take
your time. Any other key also closes it and then does its normal job.
See [CW side-key actions](main-screen.md#side-key-actions) for how the popup
works with voice off.

## Turning voice on without blind boot mode

Voice prompts and CW enunciation can be used on their own. Set `Voice` to
`ON` in the menu, and assign SAY LABEL and CW SPEED to whichever keys you
like. A radio with erased settings, such as after a first-time flash, starts
with voice off.

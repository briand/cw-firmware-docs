# Code Practice Oscillator (CPO)

CPO mode turns the radio into a standalone CW practice buzzer: no
receiving, no transmitting, just sidetone and an on-screen decode of what
you key in iambic modes. It's useful for practicing copy and sending without making RF.

Because it doesn't transmit, using the CPO does not require a license, except in some jurisdictions where a license is required to own any radio equipment regardless of use.

On the UV-K5 v3 / UV-K1, CPO also has [drills](#drills) for sending and
copying callsigns, with optional Farnsworth spacing.

## Entering CPO

=== "UV-K5 (v1 original)"

    Long press **5**. With `Voice` on, the radio sends `CPO` in CW as it
    starts. See [CW enunciation](blind-boot-mode.md#cw-enunciation).

=== "UV-K5 v3 / UV-K1"

    Press **F**, then long press **5**, or use the CODE PRACTICE
    [side-key action](main-screen.md#side-key-actions). This works from any
    modulation: the radio uses CW for the session and puts the VFO's mode
    back when you leave.

While in CPO, the radio doesn't receive or transmit. Use your normal
[CW key input](menus-and-settings.md#cw-key-input-cwkin) to send — CPO
plays it back as sidetone and decodes it on screen as you go. To change the keyer style or input method, exit the CPO and enter the Menu from the main screen.

## Exiting CPO

Tap **EXIT**. If you changed the WPM while inside CPO, the new speed is
saved as your normal `CWwpm` setting on the way out. On the UV-K5 v3 / UV-K1,
the [spacing](#farnsworth-spacing) settings are saved the same way.

## Button reference

| Button | Action |
|---|---|
| **EXIT** | Leave CPO and return to the main screen. |
| **UP** / **DOWN** | Adjust sending speed in WPM (range 10–45 inside CPO). Saved as your `CWwpm` setting on exit if changed. |
| **\*** | Toggle the backlight on/off for the duration of CPO. |
| **4** | Toggle flashlight-on-key-down, so the flashlight LED flashes in time with your sending. |
| **5** | Clear the previously decoded text. In a drill (UV-K5 v3 / UV-K1), also start the callsign over in Send Callsigns, or play it again in Copy Callsigns, without counting a miss. |
| **F** (UV-K5 v3 / UV-K1) | Choose a [drill](#drills): Off, Send Callsigns, Copy Callsigns, then back to Off. |
| **2** / **8** (UV-K5 v3 / UV-K1) | In Copy Callsigns, narrow or widen the [Farnsworth spacing](#farnsworth-spacing). |
| **0** (UV-K5 v3 / UV-K1) | In Copy Callsigns, turn [auto spacing](#auto-spacing) on or off. |

## Drills (UV-K5 v3 / UV-K1 only) {#drills}

Press **F** in CPO to step through the drills. The title line names the
current one.

| Drill | What you do |
|---|---|
| Send Callsigns | Key the callsign shown on screen. |
| Copy Callsigns | Listen to a callsign and key back what you heard. |

The drills work with paddle and bug keying. HandKey inputs don't feed the
decoder, so they can't be scored.

### The drill screen

From the top, the screen shows:

1. The drill name.
2. The target, in large text: the callsign to send, or in Copy Callsigns `?`
   until you've copied it.
3. What you've keyed, in large text, each character under the one it should
   match.
4. `OK` after a correct callsign or `MISS` after a wrong character. For a
   moment after you change the spacing, this line shows the new setting
   instead.
5. The speed, your score as hits/misses (up to 999/999), and indicators: `A`
   for auto spacing, `*` for the backlight and `^` for the flashlight.

Each character is checked as soon as it's decoded, and the score resets when
you change drills. Keying that doesn't decode to a character, such as an
unknown pattern or more than nine elements, shows as `*` and counts as a miss.

The drills wait until you pause for a word space before playing anything or
reacting to a miss. They never play over your keying, and the rest of a word
after a miss doesn't count as more misses.

### Send Callsigns

A random callsign appears. A wrong character counts a miss, shows `MISS`, and
gives you the same callsign again. Key the whole callsign correctly and you
get `OK`, then a new callsign a second later. **5** starts the callsign over
without a miss.

About two-thirds of the callsigns are US formats (1x2, 1x3, 2x1, 2x2 and 2x3,
with K, N, W and AA–AL prefixes) and the rest use 28 common DX prefixes. They
are up to six characters long.

### Copy Callsigns

The callsign plays as sidetone and stays hidden. Key back what you heard:

- If it's right, you get `OK`, the callsign appears, the radio sends "dit dit",
  and the next one plays.
- A wrong character shows `MISS` and plays the callsign again. After the third
  miss on the same callsign, it's shown for 3 seconds and the next one plays.
- Key `?`, or press **5**, to hear it again with no penalty.

As when asking for a repeat on the air, you can key the start you're sure of
followed by `?`, for example `W1A?`. That start goes on the callsign line as
notes and stays there through misses and replays until the next callsign.

### Farnsworth spacing {#farnsworth-spacing}

Copy is easier to learn at a high character speed with extra space between
characters: you hear each character at full speed and still have time to
recognize it, and you narrow the space as your copy improves. In Copy
Callsigns, characters play at your keyer speed (**UP** / **DOWN**) and the gaps
between them stretch so the text averages a slower effective speed:

- **8** widens the gaps by one effective WPM at a time, down to 5 WPM.
- **2** narrows them. Narrowing all the way to the keyer speed turns the
  extra spacing off.

The bottom line shows both speeds as `25(12)`: 25 WPM characters at an
effective 12 WPM. With the extra spacing off it shows `25 WPM`. If you lower
the keyer speed to or below the effective speed, the extra spacing pauses
until you raise it again.

The firmware uses the ARRL Farnsworth timing (by KE3Z). At 25 WPM the gap
between characters is normally 144 ms. At 20, 15, 12 and 10 WPM effective it
becomes 238, 396, 554 and 712 ms.

Only the drill's callsign gets the extra spacing. The "dit dit" after
a correct copy, your stored messages, the proper roger and your own keying
keep normal timing.

### Auto spacing {#auto-spacing}

Press **0** in Copy Callsigns to have the radio adjust the spacing as you go.
An `A` on the bottom line shows it's on.

- Five callsigns in a row copied on the first listen (no miss, `?` or
  replay) narrow the spacing one step.
- One you miss three times widens it one step. If the extra spacing was off,
  this turns it on.

Each change shows the new setting on screen for a moment.

## See also

- [Menus and Settings](menus-and-settings.md) for the CW menu items CPO
  reads its defaults from (`CWfreq`, `CWvol`, `CWwpm`, `CWkin`, `CWkmod`).

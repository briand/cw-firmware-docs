# Release Notes (UV-K5 v3 / UV-K1)

What changed in each release of the UV-K5 v3 / UV-K1 firmware
([uv-k1-k5v3-firmware-custom](https://github.com/briand/uv-k1-k5v3-firmware-custom)),
newest first. The downloads for every release are on the
[GitHub releases page](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases).
For the latest firmware and how to flash it, see
[Download and Flash](download-and-flash.md).

!!! note
    These notes cover the UV-K5 v3 / UV-K1 firmware only. The original UV-K5
    (v1) firmware has its own
    [releases page](https://github.com/briand/uv-k5-firmware-custom-cw/releases).

## v2.0

The NR7Y CW mod firmware is now Brass 🎺 !

v2.0 moves the firmware onto Armel F4HWN's v6.x codebase, up to F4HWN
v6.3.0 (v1.4 was at Fusion v5.9.0). From v2.0 the firmware edition is named
**Brass**, and the release files are named `brass.k1-k5v3.v2.0.bin`,
`brass.k1-k5v3.v2.0.uf2` and `brass.k1-k5v3.chirp.v2.0.py`.

### Before you upgrade

v2.0 stores settings in a new layout: CW settings and macros move to new
places, and key assignments are numbered differently. **The firmware doesn't
convert your old settings. The v2.0 CHIRP module does.** If you skip these
steps, your channels stay, but CW settings, macros and key assignments go back
to their defaults.

1. **Before you flash v2.0**, while the radio still runs v1.x, use CHIRP with
   the module from your current v1.x release (for example
   `nr7y.k1-k5v3.chirp.v1.4a.py`). Download from the radio and **save the
   image** (`.img`). Keep this file; it's your backup.
2. Flash v2.0 (see [Download and Flash](download-and-flash.md)).
3. On the radio, boot into "hidden menu mode" by holding PTT+side1 at poweron,
   then choose **Reset → ALL** from the menu and let it restart. This clears
   out the old layout. Calibration isn't affected.
4. In CHIRP, load the v2.0 module (`brass.k1-k5v3.chirp.v2.0.py`), then
   **open the image you saved in step 1**. The module converts it to the v2.0
   layout as it loads: channels, settings, CW settings, macros and key
   assignments. CW and USB channels start at the v2.0 filter defaults (CW
   narrow, USB wide).
5. Upload to the radio.

After upgrading, use only the v2.0 CHIRP module. It refuses to upload to v1.x
firmware, and a v1.x module would write CW settings and macros where v2.0 no
longer reads them.

If you skip the CHIRP step on a radio that had macros recorded, CHIRP can show
up to 12 garbage entries at channels 449–460, where v1.x stored the macros.
Delete them, or do the steps above.

### From F4HWN v6.0 to v6.3

- [Multiboot](f4hwn-functions.md#multiboot): keep up to four firmware images
  on the radio and pick one at power-on (hold **M** while you turn the radio
  on). Each slot has its own settings bank, which **SetCfg** in the menu
  can switch (the radio restarts to change banks).
- [Overlay apps](f4hwn-functions.md#overlay-apps): press **F**, then **7** to
  open the app launcher. Install apps with
  [UV Studio](https://armel.github.io/uvstudio/).
- [UV Studio Live Viewer](f4hwn-functions.md#uv-studio-live-viewer) mirrors
  the radio's screen in the browser.

Armel's release notes cover the rest of what's new in
[v6.0.0](https://github.com/armel/uv-k1-k5v3-firmware-custom/releases/tag/v6.0.0),
[v6.1.0](https://github.com/armel/uv-k1-k5v3-firmware-custom/releases/tag/v6.1.0),
[v6.2.0](https://github.com/armel/uv-k1-k5v3-firmware-custom/releases/tag/v6.2.0) and
[v6.3.0](https://github.com/armel/uv-k1-k5v3-firmware-custom/releases/tag/v6.3.0).

### Moved to apps, or removed

To make room for the CW features:

- The broadcast FM radio and the spectrum analyzer are no longer built in.
  They're overlay apps now, so install them with UV Studio if you use them.
  The FM RADIO side-key action and **F**, then long press **0 FM** open the
  FM app, and give the error beep if it isn't installed.
- DTMF and scan ranges are left out of this firmware.
- AM is receive-only, as in F4HWN. v1.4 could transmit "AM", which wasn't
  actually AM. (spoiler alert: "SSB" doesn't transmit SSB either)

### CW

- `CWwpm` goes up to 60 WPM (was 45). This is pushing the edge of what's
  possible reliably in this firmware and processor, and may not always be
  perfectly timed.
- `CWfreq` covers 400–900 Hz in 50 Hz steps (was 450–800 Hz).
- New [`CWdisp`](menus-and-settings.md#cwdisp) menu sets how long the decoded
  text of what you sent stays on screen after you stop keying: 1000 ms (as
  before), 5000 ms, 10000 ms or Infinite. CHIRP has the same setting
  ([#55](https://github.com/briand/uv-k1-k5v3-firmware-custom/pull/55),
  [@frye](https://github.com/frye)).
- New [`CWrtyp`](menus-and-settings.md#cwrtyp) menu picks what PROPER ROGER
  sends: Normal (R), Stutter (E E R) or Skipping (E S R). CHIRP has the same
  setting
  ([#58](https://github.com/briand/uv-k1-k5v3-firmware-custom/pull/58),
  [@dechristopher](https://github.com/dechristopher)).
- In the USB Port [key inputs](menus-and-settings.md#cw-key-input-cwkin),
  PTT is also a straight key, for sending a roger by hand next to the paddle
  ([#58](https://github.com/briand/uv-k1-k5v3-firmware-custom/pull/58)).
- The status bar shows the current key input in CW, for example `UI` for USB
  Port Iambic. See the [key input indicator](main-screen.md#key-input-indicator).
- The Port [key inputs](menus-and-settings.md#cw-key-input-cwkin) are renamed
  TRS (`TRS HandKey`, `TRS Iambic` and so on), so they aren't confused with the
  USB Port inputs.
- CW and USB have a wide and a narrow filter again. **F**, then long press
  **4**, the FILTER WIDTH action and the `Filter` menu switch between them,
  and the status line shows **W** or **N**. A channel switched to CW starts
  narrow; USB and the other modes start wide.
- After you leave an app or VFO frequency entry, CW and USB go back to
  monitor (open squelch, green RX LED).
- Opening the app launcher, or an app from a side key, stops a playing macro
  and ends a CW transmission. The paddle and key inputs don't key the radio
  while an app is open.
- In the code practice callsign drills, the callsign and your response sit one
  character further in, away from the screen edge.

### Fixes

- In CW, refusing a transmission (for example on a TX-locked channel) no
  longer leaves the display stuck on `TX DISABLE`
  ([#51](https://github.com/briand/uv-k1-k5v3-firmware-custom/issues/51)).
- The USB-C connection shows up as **Quansheng USB** in the browser's device
  picker, with a serial number unique to the radio. The USB driver also
  rejects malformed requests that could overrun its buffers.

### CHIRP

- A **Filter** column shows each channel's wide or narrow filter, in every
  mode. FM and AM also show narrow as NFM and NAM.
- Fixed: a blank or too-short DTMF code on the radio stopped CHIRP from
  saving its settings. CHIRP now reads such a code as its default, the same
  way the firmware does.

## v1.4

Released 2026-10-15.
[Release page](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/tag/v1.4)

This release brings in a large set of features from
[@dechristopher](https://github.com/dechristopher) (KF1BER), who also joined
as a maintainer. It brings the firmware up to parity with F4HWN Fusion v5.9.0.

!!! note "Updated CHIRP module"
    The CHIRP module was updated on 10/15 to `nr7y.k1-k5v3.chirp.v1.4a.py`.
    It fixes actions that didn't upload with the right values for the new
    action choices. The firmware is unchanged.

### Summary

- The KF1BER "Proper Roger" overhaul
  ([#43](https://github.com/briand/uv-k1-k5v3-firmware-custom/pull/43)): CW
  side-key actions, RIT/XIT, stuck-key transmit timeout, prosign decode, and
  code practice callsign drills.
- Keypad lock also locks out CW keying when PTT is set in lockout
  ([#37](https://github.com/briand/uv-k1-k5v3-firmware-custom/issues/37)).
- The hidden menu `F LOCK` setting correctly locks and unlocks TX on VHF
  ([#30](https://github.com/briand/uv-k1-k5v3-firmware-custom/issues/30)).
- Boot logo enabled
  ([#41](https://github.com/briand/uv-k1-k5v3-firmware-custom/issues/41)).
- Broadcast FM radio enabled: **F**, then long press **0 FM**, or a saved
  memory
  ([#32](https://github.com/briand/uv-k1-k5v3-firmware-custom/issues/32)).

### Before you upgrade

- Your settings, CW messages and key assignments carry over.
- Flash the firmware first, then use the CHIRP module attached to this
  release. It won't upload to a radio that's still on older firmware.
- On first boot the radio updates its stored channels once. There's nothing
  for you to do.
- [`CWvol`](menus-and-settings.md#cw-sidetone-volume-cwvol) now has 15
  levels. Your sidetone stays exactly as loud, but its number changes: old
  levels 1–6 become 6, 11, 12, 13, 14 and 15.

### New for CW

- Five new [side-key actions](main-screen.md#side-key-actions): PROPER ROGER,
  CW SPEED, CW KEYER MODE, CW KEY INPUT and CW BREAK-IN. CW SPEED changes the
  speed as you press the arrows. Keyer mode and key input only change when
  you press **M**, like the menu.
    - PROPER ROGER sends an R with a long dah (di-daaaah-dit) and lights the
      LED amber while it sends. The new
      [`CWrgr`](menus-and-settings.md#cwrgr) menu sets the dah length, 3–20
      dits (default 9).
    - A new radio, or one after Reset ALL, starts with a
      [CW key layout](main-screen.md#default-key-layout-uv-k5-v3-uv-k1-only): roger and message 1
      on F1, speed and key input on F2. An upgraded radio keeps its current
      key assignments.
- [RIT/XIT](main-screen.md#rit-xit): press `*` in CW to shift receive,
  transmit or both by up to ±9.99 kHz without moving the dial. The adjust
  screen shows signal strength, so you can peak a station.
- [`CWhang`](menus-and-settings.md#cwhang) sets the break-in hang time,
  10–2000 ms. It used to be fixed at 300 ms.
- [Transmit timeout](main-screen.md#tx-timeout): keying that runs for 7
  seconds without a gap between characters drops TX, so a stuck key or
  shorted paddle can't keep you on the air.
- The decoder shows the prosigns SK, BK, KA, SN, UR and SOS as underlined
  letters, and zeros get a dot so they don't read as O. You can record
  prosigns in [CW messages](menus-and-settings.md#cw-messages-cwmsg1-cwmsg4),
  and CHIRP shows them as `<SK>`, `<BK>` and so on.
- `CWvol` goes quieter at the low end, which helps when the volume knob is
  turned up for a weak station.
- [Bug mode](menus-and-settings.md#cw-keyer-mode-cwkmod) no longer drops a
  dit flicked right after a dah, which could turn a fast K into an M.
- CW and USB now have a single 6.25 kHz
  [filter](main-screen.md#filter-width-long-press-4fc). The "2k" setting shown
  before didn't actually work (it was always 6k audio), and has been removed.
  The WIDE NARROW action is renamed FILTER WIDTH, and keys bound to it keep
  working.
- The radio's error beep can't sound in CW, so in CW an error (like stepping
  past the speed limit) plays a short, low dit.

### Code practice

- Press **F** in code practice to pick a
  [drill](code-practice-oscillator.md#drills). Send Callsigns shows a callsign
  for you to key, and Copy Callsigns plays one for you to copy and key back.
  Both keep score.
- Copy Callsigns has
  [Farnsworth spacing](code-practice-oscillator.md#farnsworth-spacing) on
  **2** and **8**, and [auto spacing](code-practice-oscillator.md#auto-spacing)
  on **0** that narrows the gaps as your copy improves.
- Code practice now
  [starts from any mode](code-practice-oscillator.md#entering-cpo) and puts
  your mode back when you leave.

### Fixes

- `F Lock` now restricts transmit on CW and USB channels and in VFO mode.
  Before, even `DISABLE ALL` didn't stop transmitting there.
- With a Port key input set, CHIRP can connect again once the radio is out of
  CW mode, without a power cycle
  ([#31](https://github.com/briand/uv-k1-k5v3-firmware-custom/issues/31)).
- Message playback no longer clips its first element.
- The `BKIN` status icon no longer blinks
  ([#38](https://github.com/briand/uv-k1-k5v3-firmware-custom/pull/38),
  [@robschreiber](https://github.com/robschreiber)).
- `SetNav` is saved across power cycles
  ([#34](https://github.com/briand/uv-k1-k5v3-firmware-custom/pull/34),
  [@cranklin](https://github.com/cranklin)).
- CHIRP: a long message with spaces no longer disappears from the settings,
  and `+`, `(` and `&` are accepted in messages.

### From F4HWN Fusion 5.8.0 and 5.9.0

- The [menu](menus-and-settings.md) opens on a list of categories, with CW at
  the top.
- Press **F**, then long press a side key, to
  [pick any action](main-screen.md#action-picker) and run it once.
- `POnMsg` has a `LOGO` option that shows a boot logo you load with
  [UV Studio](https://armel.github.io/uvstudio/) or
  [BKG Programmer](https://programmer.bkg.club/).

Armel's release notes cover the rest of Fusion
[v5.8.0](https://github.com/armel/uv-k1-k5v3-firmware-custom/releases/tag/v5.8.0)
and [v5.9.0](https://github.com/armel/uv-k1-k5v3-firmware-custom/releases/tag/v5.9.0).

## v1.3.1

Released 2026-08-06.
[Release page](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/tag/v1.3.1)

A bug fix release. It shortens the handkey release debounce time, which was a
little too strong and slowed the response, especially when sideswiping
([#27](https://github.com/briand/uv-k1-k5v3-firmware-custom/issues/27)). If
you don't use the handkey or Bug modes, you don't need this version.

## v1.3

Released 2026-07-30.
[Release page](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/tag/v1.3)

- In Port Handkey mode, both paddle contacts act as a straight key
  ([#22](https://github.com/briand/uv-k1-k5v3-firmware-custom/issues/22)).
- Merged F4HWN Fusion v5.7.0.
- The [Code Practice Oscillator](code-practice-oscillator.md) can be mapped to
  a side-key action, and **5** clears the text. Thanks
  [@Lucasmoidel](https://github.com/Lucasmoidel)!
- Fixed: message playback left too much space between characters and words.
- A debounce filter on the handkey and Bug modes stops glitches from a slowly
  closing contact.

## v1.2.3

Released 2026-07-08.
[Release page](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/tag/v1.2.3)

- Bug keyer: dits complete even if the dit paddle is released and pressed
  again during a dit (glitch filtering).
- Better noise filtering on the USB port input, which mostly fixes
  [#18](https://github.com/briand/uv-k1-k5v3-firmware-custom/issues/18).
- An updated CHIRP module, attached after the release, fixes CW and SSB
  channel uploads.

!!! tip "RFI and the USB port input"
    The USB port input is very sensitive to RFI, because of how the radio's
    USB port ground is wired. There may still be setups where RFI causes a
    hard key-down or constant keying. If that happens, long press **EXIT** to
    stop sending. To avoid it:

    - Keep your key cable short and shielded.
    - Use only as much power as you need. Medium is much less likely to cause
      trouble than High.
    - Use a balanced antenna, or move the antenna away from the radio with
      coax. One operator had success adding a "rat tail" counterpoise.

    See [USB-C to TRS cable](hardware/usb-trs-cable.md) for more.

## v1.2.2

Released 2026-07-03.
[Release page](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/tag/v1.2.2)

v1.2.1 claimed to fix iambic keying on side button 1, but it was still broken.
This release actually fixes it. If you don't key with the side buttons and
already have v1.2.1, you can skip this one.

## v1.2.1

Released 2026-07-03.
[Release page](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/tag/v1.2.1)

- Fixed an Ultimatic keyer bug when the opposite paddle is tapped briefly
  during an element. Thanks [@SP5DNA](https://github.com/SP5DNA)!
- Sidetone "off" really turns it off.
- Sidetone level 1 is quieter.
- Fixed: Iambic Button input mode didn't respond to PTT.
- Fixed squelch in SSB and CW: it stays quiet when closed, and opens on
  signals.
- A devcontainer config lets GitHub Codespaces build the project.

## v1.2

Released 2026-06-28.
[Release page](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/tag/v1.2)

- USB port input mode: connect a paddle without opening the radio, using the
  [USB-C to TRS cable](hardware/usb-trs-cable.md).
- Ultimatic keyer.
- Semi-automatic Bug keyer.
- Fixed decoding of characters with more than 6 elements.
- Fixed audio pops between elements while transmitting.
- Decodes the prosigns AR `+`, KN `(` and AS `&`.

This release also launched this documentation site.

## v1.1

Released 2026-06-13.
[Release page](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/tag/v1.1)

An all-fixes release. Thanks [@rysiekuk](https://github.com/rysiekuk) for
issue reports and code fixes!

- Fixed low or missing mic audio at startup outside CW mode.
- The frequency offset from tech mode menu item 82 is stored properly.
- Tech mode starts in PTT handkey, so CW can transmit while you tune the
  frequency offset.
- Fixed a tone that lingered between and after CW elements.
- Swapped the TRS pins, so dit and dah are assigned correctly by default.

## v1.0.0

Released 2026-05-25.
[Release page](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/tag/v1.0.0)

The first release built and published by GitHub Actions (formerly "beta 3").

- Merged F4HWN Fusion v5.5.0.
- Fewer pops on CW and SSB transmit.
- In CW, the VOX button toggles break-in.
- **F**, then long press **5** enters the code practice keyer, and **F**, then
  long press **4** cycles the filters.
- WPM range goes up to 40 (was 30).
- SSB mode turns off the scrambler, compander, PTT-ID, CTCSS tail and roger
  beep.
- Clearer menu labels for the CW features, and clearer names for the CW input
  modes.
- First CHIRP module, based on the F4HWN Fusion 5.5 module.
- Fixed a stall in side button 1 keying detection.
- Updated the UV-K1 / UV-K5 v3 paddle rework instructions.

## beta2

Released 2026-04-30.
[Release page](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/tag/beta2)

Brings over all of the CW features and fixes from the UV-K5 (v1) firmware,
through its v1.0.1 release.

!!! note
    The UV-K5 v3 / UV-K1 can't use the
    [CEC cable](hardware/cec-cable.md): its microcontroller doesn't have the
    analog features on those pins that made CEC possible. Use button keying
    (PTT + Side 1), the [paddle rework](hardware/rework-overview.md) to make
    the 3.5 mm port take a standard paddle cable, or (from v1.2) the
    [USB-C to TRS cable](hardware/usb-trs-cable.md).

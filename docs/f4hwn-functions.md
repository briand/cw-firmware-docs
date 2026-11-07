# F4HWN Functions (UV-K5 v3 / UV-K1)

The UV-K5 v3 / UV-K1 firmware is built on Armel F4HWN's v6.x codebase, and it
carries several of his features along with the CW additions. This page gives a
short overview of each one, notes where it interacts with CW operation, and
links to [Armel's wiki](https://github.com/armel/uv-k1-k5v3-firmware-custom/wiki)
for the full details.

!!! note
    These features are in the UV-K5 v3 / UV-K1 firmware from v2.0 (named Brass
    from v2.0 on). The UV-K5 (v1) firmware doesn't have them. See the
    [v2.0 release notes](release-notes.md#v20) for what else
    changed, and how to carry your settings over from v1.x.

## Multiboot

Multiboot keeps several firmware images on the radio's external flash, and
lets you pick which one runs when you turn the radio on. You can keep this
firmware and stock F4HWN Fusion side by side, and switch between them without
a computer.

Full details: [Multiboot and Multiconfig](https://github.com/armel/uv-k1-k5v3-firmware-custom/wiki/Multiboot-and-Multiconfig)
on Armel's wiki.

### Slots

The radio always runs the firmware in its internal flash, the same flash the
regular flashing tools write. Multiboot adds storage slots on the external
flash chip:

| Slot | What it holds |
|---|---|
| **M** (Main) | A copy of the firmware you last flashed with a regular flashing tool. The radio keeps it up to date itself. |
| **1**–**4** | Firmware images you put there with [UV Studio](https://armel.github.io/uvstudio/)'s **Firmware Slots** view. |

Switching to a slot copies that slot's image into internal flash, and the
radio restarts into it. The slots themselves don't change, so you can switch
back later.

After you flash new firmware with a regular flashing tool, the first boot shows
**Init Main** and **DO NOT POWER OFF** with a progress bar while the radio
copies the new firmware into slot M. It only happens once, and it replaces what
M held before. If you want to keep that firmware, copy it to one of slots 1–4
with UV Studio **before** you flash something else.

### Switching firmware

1. Turn the radio off.
2. Hold **M** (the MENU key) and turn the radio on.
3. When the screen says **Release keys**, let go. The radio lists the slots.
4. Use **Up** / **Down** to pick a slot, and press **M**. The radio asks
   **Restore slot N?** (or **Restore Main?**). Press **M** again to confirm.
5. The radio shows **DO NOT POWER OFF** while it writes the firmware, then
   restarts into it.

Press **Exit** at the slot list to carry on booting the current firmware.

If a slot can't be used (empty, incomplete or damaged), the radio shows
**SLOT NOT VALID** and a reason, and leaves internal flash alone.

!!! warning
    Don't turn the radio off while it shows **DO NOT POWER OFF** during a
    switch. It is rewriting internal flash, and an interrupted write leaves no
    working firmware. If it happens, put the radio in flashing mode (power on
    while holding PTT) and flash firmware again with a regular flashing tool.

!!! danger "Every slot needs a multiboot firmware"
    Only put firmware that includes multiboot into a slot: this firmware from
    v2.0 on, or F4HWN Fusion v6.x and its editions. Neither UV Studio nor the
    radio checks this. If you switch to firmware without multiboot, holding
    **M** at power-on does nothing and UV Studio can't see the slots any more.

    The slots are still there. To get them back, flash a multiboot firmware
    with a regular flashing tool (see [Download and Flash](download-and-flash.md)).
    It copies itself into slot M at the first boot, and slots 1–4 are left as
    they were.

### Settings banks

Each slot has its own settings bank: channels, menu settings and key
assignments, CW settings and macros included. Slot M uses the radio's original
settings area, and slots 1–4 each get a bank of their own, so different
firmware never reads settings another firmware wrote in its own format.

- **SysInf** in the menu shows which slot and bank are running, as labels
  such as **SLOT 2** and **CFG 2**.
- **SetCfg** in the menu points the running firmware at a different bank
  (**CFG M**, **CFG 1** to **CFG 4**). It asks you to confirm, then restarts
  the radio on the new bank.

!!! info "Differences from F4HWN"
    Armel's firmware switches banks with SetCfg without a restart, and shows
    the active bank in the status bar. This firmware restarts instead, and
    leaves out the status bar badge, to save flash space for CW features.

### Tips

- Before you try new firmware, copy the firmware you're happy with into one of
  slots 1–4, so you can always switch back to it.
- Back up the radio's calibration data before you start, as described in
  [Download and Flash](download-and-flash.md#flash-it).

## Overlay apps

Overlay apps are small programs stored on the radio's external flash and
loaded into RAM when you run them. Armel's catalog includes decoders (APRS,
POCSAG, radiosondes and more), tools, games, and CW apps. Some functions that
used to be built into the firmware, such as the FM broadcast receiver and the
spectrum analyzer, now come as apps, which leaves room in the firmware for the
CW features.

Full details: [Overlay apps](https://github.com/armel/uv-k1-k5v3-firmware-custom/wiki/Overlay-apps)
(how they work) and the [app catalog](https://github.com/armel/uv-k1-k5v3-firmware-custom/wiki/Overlay-applications)
on Armel's wiki.

### Installing apps

Apps are installed from a computer with the **Apps** view of
[UV Studio](https://armel.github.io/uvstudio/), from its catalog or from a
local `.app` file. See [Apps](https://github.com/armel/uv-k1-k5v3-firmware-custom/wiki/UV-Studio#apps-labs)
on Armel's UV Studio page.

### Running apps

1. Press **F**, then **7**. The app launcher lists the installed apps.
2. Use **Up** / **Down** to pick one, and press **M** to run it.
3. Press **Exit** in the app to leave it. Most apps go back to the launcher.
   Press **Exit** again to return to the main screen.

In the launcher, **\*** switches the right-hand column between each app's
size and version.

Some apps can also be opened directly from a programmable side key
(FM RADIO, FOX HUNT, BEACON, BEAM, TONE CALL). The action only works when the
matching app is installed; otherwise the radio gives the error beep.

!!! info "CW interactions"
    - In CW mode, **F** then **7** opens the launcher, and long press **7**
      (without **F**) toggles break-in. See
      [Break-in toggle](main-screen.md#break-in-toggle-long-press-7vox).
    - Opening the launcher, or an app from a side key, stops any macro that's
      playing and ends a CW transmission straight away. The paddle and key
      inputs don't key the radio while the launcher or an app is open.
    - When you leave, the keyer is ready again, and in CW and USB the radio
      goes back to monitor (open squelch, green RX LED).
    - The CW apps in Armel's catalog, such as CW Keyer and CW Decode, are
      separate from this firmware's built-in keyer. They keep their own
      settings and don't use the CW menu settings. The CW Keyer app, for
      example, has its own speed setting.

## UV Studio Live Viewer

[UV Studio](https://armel.github.io/uvstudio/)'s **Live Viewer** (also known
as K5Viewer) mirrors the radio's screen and LEDs in the browser while the
radio is connected over USB. You can work the radio from the virtual keypad
or the computer keyboard, and take screenshots. The viewer can't start a
transmission.

Full details: [Live Viewer](https://github.com/armel/uv-k1-k5v3-firmware-custom/wiki/UV-Studio#live-viewer)
on Armel's UV Studio page.

!!! info "CW interactions: keying timing while connected"
    While the Live Viewer is mirroring the screen, each screen update briefly
    pauses the radio's main loop, typically for 10–20 ms. If a pause lands in
    the middle of an element, that dit or dah runs long by the same amount.
    In testing it affected 1–2% of elements. That's hardly noticeable at
    ordinary speeds, but at high speed a 20 ms stretch is a whole dit (at
    60 WPM). For the cleanest keying, disconnect UV Studio while you operate.

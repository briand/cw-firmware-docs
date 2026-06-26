# cw-firmware-docs

User documentation for the NR7Y CW firmware family, covering two firmware
projects that share most of their featureset:

- `uv-k5-firmware-custom` — original UV-K5 (v1) and UV-K5 v3.
- `uv-k1-k5v3-firmware-custom` — UV-K1 and UV-K5 v3 (newer shared codebase).

Both firmware repos are checked out as sibling, **read-only** working
directories alongside this one. Treat them purely as source material — pull
menu strings, eeprom layouts, and behavior from the code there, never edit
them from this project.

This is a [Zensical](https://zensical.org/) site (syntax and config are
close to Material for MkDocs). Config is in `mkdocs.yml`, content is under
`docs/`.

## Local build

```bash
uv sync
uv run zensical serve   # live preview
uv run zensical build   # static build into site/
```

## Style

- Call a held key press a **"long press"** (e.g. "long press 5"), not "hold"
  or "press and hold". Use this consistently across pages and button
  reference tables.

## Content model

- The two firmware projects intentionally stay in sync on features. Default
  to writing **one shared explanation** for a feature.
- Only split content when the *hardware* actually differs — not just because
  the code lives in two repos. Use Material/Zensical tabbed content
  (`=== "Tab Title"`) to present model-specific variants inline, e.g.:

  ```markdown
  === "UV-K5 v3 / UV-K1"

      Shared behavior text.

  === "UV-K5 (v1 original)"

      Different behavior text.
  ```

  The common split is "K5 v1 only" vs "K5 v3 + K1 combined," since v3 and K1
  share the newer codebase. Check both `menu.c` files before assuming a
  setting is identical — ranges, enum sizes, and available options
  sometimes differ even when the menu key name matches.
- For genuinely hardware-specific pages (rework guides, identification),
  prefer separate pages under `docs/hardware/`, with shared step blocks
  factored out via `pymdownx.snippets` (`--8<-- "path/to/file.md:section"`)
  rather than copy-pasting steps. See `docs/hardware/rework-uv-k5-v3.md` for
  the section-anchor pattern other rework pages pull from.
- Don't invent behavior. If you can't find the relevant code path in either
  firmware repo, say so rather than guessing.

## Where to look in the firmware repos

- `ui/menu.c` — `MenuList[]` defines the on-screen menu key strings (e.g.
  `"CWfreq"`) and maps them to `MENU_*` enum ids. CW-specific items are all
  prefixed `CW` and guarded by `#ifdef ENABLE_CW_MODULATOR`. This same file
  has the `gSubMenu_CW_*` string arrays and the per-item display formatting
  switch.
- `app/menu.c` — the min/max range (`*pMin`/`*pMax`) switch and the
  get/set-on-confirm switches for each `MENU_*` id. This is where numeric
  ranges, units, and stored-value formulas live.
- `app/cwhardware.c` / `app/cwhardware.h` (or `App/app/cwhardware.*` in the
  k1/k5v3 repo) — what each key input mode actually wires up in hardware
  (`CW_KEY_FLAG_*` bitmap, port/ADC/button details).
- `app/cwkeyer.c` — iambic/bug keyer state machine behavior (Mode A vs Mode
  B vs Semi Bug timing).
- `settings.h` / `settings.c` — eeprom field comments and default values for
  `gEeprom.CW_*` fields; useful for confirming defaults to document.

## Known hardware-driven differences (as of this writing)

- UV-K5 v1 lacks a dedicated digital paddle port; its "CEC Cable" key input
  modes identify paddle contacts by reading an analog voltage and need a
  one-time ADC calibration (`CWcrd`/`CWcLo`/`CWcHi` menu items, present only
  in `uv-k5-firmware-custom`).
- UV-K5 v3 / UV-K1 read a real digital paddle signal over USB-C, need no
  calibration, and additionally support a Semi Bug keyer mode and a wider
  WPM range (10–40 vs 10–30 on v1).

Re-verify these against the code rather than trusting this list blindly —
firmware behavior can change after this was written.

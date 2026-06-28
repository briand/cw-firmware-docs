# CW Firmware Docs

This site is the companion manual for the Quansheng UV-K5/K5v3/K1 firmware CW mods by NR7Y:

* [uv-k5-firmware-custom](https://github.com/briand/uv-k5-firmware-custom-cw)
* [uv-k1-k5v3-firmware-custom](https://github.com/briand/uv-k1-k5v3-firmware-custom)

## Start here

- [Identify your radio](hardware/identify-your-radio.md)
- [Download and flash](download-and-flash.md)
- [Main screen](main-screen.md)
- [Menus and settings](menus-and-settings.md)
- [CW paddle input — cable or rework?](hardware/cw-paddle-input.md)
- [Paddle rework overview](hardware/rework-overview.md)

## Why the CW mod?

This mod builds on existing open-source firmware for the respective radio models. They're great, but they don't enable CW (Continuous Wave - morse code) sending. The CW mod enables precise transmission of CW morse code, and a rich set of features for the CW operator.

- Automatic iambic keyer with A/B/Ultimatic/Bug modes
- paddle support using the PTT/Side1 buttons
- External paddle support with rework - allows direct connection of a standard paddle with no cable change
- External paddle support without rework using a custom cable
- Macro message recording by keying and playback
- Code Practice mode with optional flashlight LED sending

## Upstream projects

The CW mods documented here build on top of two upstream firmware projects, and neither would exist without them. Big thanks to both:

- [egzumer/uv-k5-firmware-custom](https://github.com/egzumer/uv-k5-firmware-custom) — the upstream firmware for the original UV-K5 (v1). egzumer has put tons of work into that project and its feature set. egzumer firmware is based on the original open-source K5 firmware by DualTachyon, work by OneOfEleven plus mods from fagci.
- [armel/uv-k1-k5v3-firmware-custom](https://github.com/armel/uv-k1-k5v3-firmware-custom) — Armel's (F4HWN) "Fusion" firmware for the UV-K5 v3 and UV-K1. Fusion is fantastic, incredibly featureful, and actively developed; I'll try to pull and keep up to date with Armel's changes and new features as I'm able. Fusion is also originally based on egzumer.

Each upstream project has its own README and documentation covering its full feature set. This site only documents the CW-specific mods layered on top — for everything else the firmware can do, see the upstream repos directly.

## Open for contributions

Found a mistake, an unclear explanation, or a gap in the docs? Pull requests are welcome — open one against the [GitHub repo](https://github.com/briand/cw-firmware-docs). Small fixes (typos, broken links, clarifications) are easiest to review and merge quickly.

## License

This documentation is licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/). You're free to share and adapt it for non-commercial purposes, with attribution, as long as you license any derivative under the same terms. See the [LICENSE](https://github.com/briand/cw-firmware-docs/blob/main/LICENSE) file in the repo for the full text.

## Firmware licensing

The two firmware repos this site documents, [uv-k5-firmware-custom](https://github.com/briand/uv-k5-firmware-custom-cw) and [uv-k1-k5v3-firmware-custom](https://github.com/briand/uv-k1-k5v3-firmware-custom), are licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0). That license applies to the firmware source code itself, not to this documentation site.

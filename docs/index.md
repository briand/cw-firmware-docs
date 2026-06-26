# CW Firmware Docs

This site is the companion manual for the CW firmware family.

It will eventually cover both firmware repos and their shared operating concepts, while keeping the hardware-specific instructions split out where they need to differ.

## Start here

- [Identify your radio](hardware/identify-your-radio.md)
- [Download and flash](download-and-flash.md)
- [Menus and settings](menus-and-settings.md)
- [CW paddle input — cable or rework?](hardware/cw-paddle-input.md)
- [Paddle rework overview](hardware/rework-overview.md)

## What this site is for

- Shared CW feature documentation
- Model-specific hardware rework instructions
- Starter operating guides for day-to-day use
- A stable place for screenshots, diagrams, and rework photos

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

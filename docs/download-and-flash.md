# Download and Flash

Not sure which radio you have? Check the [radio identification guide](hardware/identify-your-radio.md) first.

!!! danger
    Make **sure** you know which radio model you have, and use the correct firmware family for that radio. 
    
    * You **must** use the correct firmware for the radio model.
    * You **must** use the correct flashing tool or mode for that model.

    It's very easy to flash the wrong firmware onto a radio or use the wrong tool/mode, and very hard to fix when that happens.

## Get the firmware

Download a ready-to-flash binary from the releases page of the firmware repo for your radio. You **don't** need to compile anything yourself — the releases page has prebuilt binaries you can flash directly. If you'd rather build from source, the same repos support that too.

### UV-K5 v1 original downloads

[uv-k5-firmware-custom releases](https://github.com/briand/uv-k5-firmware-custom-cw/releases)

Latest binary for K5 original: [nr7y_1.5.packed.bin](https://github.com/briand/uv-k5-firmware-custom-cw/releases/download/v1.5/nr7y_1.5.packed.bin)

Chirp Module: [uvk5_NR7Y_1.5.py](https://github.com/briand/uv-k5-firmware-custom-cw/releases/download/v1.5/uvk5_NR7Y_1.5.py)

### UV-K5 v3 / UV-K1 downloads

All releases: [uv-k1-k5v3-firmware-custom releases](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases)

What changed in each release: [Release notes](release-notes.md)

Latest binary for K5v3 / K1: [brass.k1-k5v3.v2.0.bin](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/download/v2.0/brass.k1-k5v3.v2.0.bin)

Chirp Module: [brass.k1-k5v3.chirp.v2.0.py](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/download/v2.0/brass.k1-k5v3.chirp.v2.0.py)

!!! warning "Upgrading from v1.x"
    v2.0 changes the settings layout. Save a CHIRP image with your v1.x module
    **before** you flash, or your CW settings, macros and key assignments go
    back to their defaults. Follow the steps in
    [Before you upgrade](release-notes.md#before-you-upgrade).

!!! note
    Use the CHIRP module from the same release as your firmware. Newer modules
    check the radio before uploading and refuse to write to one running older
    firmware, since that would scramble its CW and USB channel settings. If
    CHIRP says the radio's firmware is too old, flash the new firmware first,
    then upload. A saved image from older firmware still opens, and is
    converted when you load it.

## Flash it

!!! tip
    If you've never backed up your radio's calibration data, **now is the time**. Boot into normal firmware mode, and use the appropriate web tool below to dump the calibration data. Store it somewhere safe, consider naming it after your radio's serial number.

    Flash tools and firmware all try hard not to corrupt the factory calibration data, but it could happen. A backup is a great safety net.

!!! success
    To enter flashing mode, power on the radio while holding PTT. The flashlight LED will light, the screen will stay blank and unlit.

    When the tool starts the firmware update, the LED will flash. Because it's flashing the firmware, get it?

### UV-K5 v1 original flash tools

* [egzumer's UVTools](https://egzumer.github.io/uvtools/)
* [K5TOOL](https://github.com/qrp73/K5TOOL) if you'd rather flash from the command line. Run using:  
`k5tool -wrflash <firmwarename.packed.bin>`

K5TOOL can dump or restore calibration data for K5 v1 radios. You can also dump calibration data (but not flash the firmware!) from a v1 radio using UVTools2 (link below).

### UV-K5 v3 / UV-K1 flash tools

* [Armel's UVTools2](https://armel.github.io/uvtools2/)
* [n7six Multi-firmware tool](https://n7six.github.io/UVTools/) in K1/K5 version 2 mode

Both these tools can dump or restore calibration data.

!!! info "Multiboot"
    From v2.0, the UV-K5 v3 / UV-K1 firmware can keep several firmware images
    on the radio and switch between them at power-on. Flashing with one of
    these tools also updates the multiboot Main slot. Read
    [Multiboot](f4hwn-functions.md#multiboot) before you flash over a multiboot setup, or put
    firmware into a slot.

!!! note
    The web-based tools talk to the radio over WebSerial, which only works in a selection of modern browsers.

## Program the radio with CHIRP

The CHIRP module lets you edit channels, CW messages, side key actions and
other settings from your computer. Each firmware release posts a CHIRP module
versioned to match it, alongside the firmware binary. Download the module from
the same release as the firmware on your radio (see
[Get the firmware](#get-the-firmware) above). The steps below are the same for
every radio; only the module file and the model you pick differ.

CHIRP doesn't ship with this module, so you load it yourself from the file you
downloaded. That needs CHIRP's developer mode, which is off by default.

1. Install a recent [CHIRP-next](https://chirpmyradio.com/projects/chirp/wiki/Download)
   build if you don't already have one.
2. Turn on developer mode: **Help → Developer Mode**. CHIRP asks to restart;
   let it. You only need to do this once.
3. Load the module: **File → Load Module**, then pick the `.py` file you
   downloaded. CHIRP warns that modules can run code on your computer; accept
   to continue.
4. Read from the radio: **Radio → Download from radio**. Choose vendor
   **Quansheng**, then the model and variant for your radio, then your serial
   port:
    - UV-K5 v3 / UV-K1: model **UV-K1 & UV-K5 V3 (F4HWN Fusion)**, variant
      **Brass**.
    - UV-K5 (v1 original): model **UV-K5**, variant **NR7Y**.
5. Make your changes, then **Radio → Upload to radio**.

!!! warning
    A loaded module only lasts until you close CHIRP. Each time you start
    CHIRP, repeat **File → Load Module** before you download from or upload
    to the radio. If you skip it, the Brass or NR7Y variant won't be in the list. Don't
    substitute one of CHIRP's built-in Quansheng models; they don't know
    about the CW settings.

!!! tip
    If CHIRP can't talk to the radio, make sure the radio isn't in CW mode
    with a port-based paddle input. See [CHIRP programming and the paddle
    port](hardware/cw-paddle-input.md#how-is-serial-port-chirp-programming-affected-by-the-rework).

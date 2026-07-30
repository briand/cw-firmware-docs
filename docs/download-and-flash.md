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

Latest binary for K5 original: [nr7y_1.2.packed.bin](https://github.com/briand/uv-k5-firmware-custom-cw/releases/download/v1.2/nr7y_1.2.packed.bin)

### UV-K5 v3 / UV-K1 downloads

All releases: [uv-k1-k5v3-firmware-custom releases](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases)

Latest binary for K5v3 / K1: [nr7y.k1-k5v3.v1.3.bin](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/download/v1.3/nr7y.k1-k5v3.v1.3.bin)

Chirp Module: [nr7y.k1-k5v3.chirp.v1.3.py](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases/download/v1.3/nr7y.k1-k5v3.chirp.v1.3.py)
## Flash it

!!! tip
    If you've never backed up your radio's calibration data, **now is the time**. Boot into normal firmware mode, and use the appropriate web tool below to dump the calibration data. Store it somewhere safe, consider naming it after your radio's serial number.

    Flash tools and firmware all try hard not to corrupt the factory calibration data, but it could happen. A backup is a great safety net.

!!! success
    To enter flashing mode, power on the radio while holding PTT. The flashlight LED will light, the screen will stay blank and unlit.

    When the tool starts the firmware update, the LED will flash. Because it's flashing the firmware, get it?

### UV-K5 v1 original flash tools

* [egzumer's UVTools](https://egzumer.github.io/uvtools/)
* [n7six Multi-firmware tool](https://n7six.github.io/UVTools/) in K5/K5 version 1 mode
* [K5TOOL](https://github.com/qrp73/K5TOOL) if you'd rather flash from the command line. Run using:  
`k5tool -wrflash <firmwarename.packed.bin>`

n7six tool and K5TOOl can dump or restore calibration data.

### UV-K5 v3 / UV-K1 flash tools

* [Armel's UVTools2](https://armel.github.io/uvtools2/)
* [n7six Multi-firmware tool](https://n7six.github.io/UVTools/) in K1/K5 version 2 mode

Both these tools can dump or restore calibration data.

!!! note
    The web-based tools talk to the radio over WebSerial, which only works in Chrome/Chromium-based browsers.

# Download and Flash

Not sure which radio you have? Check the [radio identification guide](hardware/identify-your-radio.md) first.

## Get the firmware

Download a ready-to-flash binary from the releases page of the firmware repo for your radio. You **don't** need to compile anything yourself — the releases page has prebuilt binaries you can flash directly. If you'd rather build from source, the same repos support that too.

=== "UV-K5 v1 original"
    [uv-k5-firmware-custom releases](https://github.com/briand/uv-k5-firmware-custom-cw/releases)

=== "UV-K5 v3 / UV-K1"
    [uv-k1-k5v3-firmware-custom releases](https://github.com/briand/uv-k1-k5v3-firmware-custom/releases)

## Flash it

!!! tip
    If you've never backed up your radio's calibration data, **now is the time**. Boot into normal firmware mode, and use the appropriate web tool below to dump the calibration data. Store it somewhere safe, consider naming it after your radio's serial number.

    Flash tools and firmware all try hard not to corrupt the factory calibration data, but it could happen. A backup is a great safety net.

=== "UV-K5 v1 original"

    * [egzumer's UVTools](https://egzumer.github.io/uvtools/)
    * [n7six Multi-firmware tool](https://n7six.github.io/UVTools/) in K5/K5 version 1 mode - this tool can also dump or restore calibration data
    * [K5TOOL](https://github.com/qrp73/K5TOOL) if you'd rather flash from the command line - this tool can aldo dump or restore calibration data

=== "UV-K5 v3 / UV-K1"

    * [Armel's UVTools2](https://armel.github.io/uvtools2/)
    * [n7six Multi-firmware tool](https://n7six.github.io/UVTools/) in K1/K5 version 2 mode

    Both these tools can dump or restore calibration data

!!! note
    The web-based tools talk to the radio over WebSerial, which only works in Chrome/Chromium-based browsers.

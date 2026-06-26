# Paddle Rework

This section documents the CW paddle rework for use with the CW firmware. If you haven't yet decided between the rework and a cable-based input, see [CW Paddle Input](cw-paddle-input.md) first.

## Choose your radio model

If you're not sure which radio model you have, follow the [radio identification guide](identify-your-radio.md)

=== "UV-K5 v1 original"
    This page covers the original UV-K5 hardware rework. All the v1 models like K6, K5(99) and others with V1.x PCBs inside follow this style.

    Go to [the v1 rework guide](rework-uv-k5-v1.md).

=== "UV-K5 v3"
    This page covers the UV-K5 v3 board layout and the updated resistor positions. It's really similar to the v1, things just moved around slightly.

    Go to [the v3 rework guide](rework-uv-k5-v3.md).

=== "UV-K1"
    This page covers the UV-K1-specific rework path. Things moved around a little more versus the v1, but it's still easy to perform.

    Go to [the UV-K1 rework guide](rework-uv-k1.md).

!!! warning "Mic behavior"
    The external mic/PTT path no longer works the same way after this rework. An external mic will not be able to trigger PTT. The internal mic still works when the paddle is unplugged, but once the paddle is plugged in the mic is switched out of the circuit, so unplug the paddle when using a voice mode.

## Next

- [CW Paddle Input FAQs](cw-paddle-input.md#faqs)

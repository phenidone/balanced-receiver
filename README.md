# balanced-receiver

This is the PCB design for a simple, 4-channel balanced line-level receiver PCB with unbalanced outputs.
It is by no means a high performance (high CMRR from DC to daylight) design but it is good enough where
cable lengths are short and/or connect between units within a single rack.

The circuit uses one op-amp per channel. Attenuation is set via a voltage divider on the output,
which can be bridged for unity gain.

It has a first-order RC RF filter on the input, which results in non-optimal CMRR at HF.  While
a bootstrapped-capacitor arrangement would be "better", you end up with 4x as much silicon and
that's total overkill for those of us running short cables.

## Op-Amps

8-pin dual op-amps are required, in the standard footprint, e.g. LM833, TL072, etc.

If only two channels are required, you could leave U1 and its related R/C networks unpopulated.

## Power Supply

The receiver can be powered either from a regulated (about +/- 12V, depending on what your
chosen op-amps are rated for) or unregulated supply, e.g. the amplifier main filter caps.  Using
LM317 and LM337 regulators, the unregulated supply must be no greater than +/- 50V DC.

If you need many channels in a single box, you could populate the regulators on one board and chain
the other boards via the regulated-supply terminals.

Beware your ground routing and the relationship between grounds at: the power supply, the amplifier,
and this receiver board.  This receiver board should obtain its power and ground connections from
as close to the amp as possible, so as to avoid noise induced by power-supply currents in its
ground connections.

## Terminals

Use 0.2" screw terminals, Phoenix-style, for the power supply connection(s).

Use any suitable 0.1" pitch terminals for the analog inputs and outputs.  Screws are best, or
plug-in headers may suit in a low-vibration environment.

## License

This hardware design is (C) 2017 William Brodie-Tyrrell and is licensed under the CERN OHL; see cern_ohl_v_1_2.pdf
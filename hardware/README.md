# hardware/

This directory will contain the mechanical design files for the FieldNode enclosure and mounting hardware.

## Planned contents

* `enclosure.step` and `enclosure.stl` for the main body
* `enclosure-lid.step` and `enclosure-lid.stl` for the removable lid
* `panel-bracket.step` and `panel-bracket.stl` for the solar panel mount
* `mast-mount.step` and `mast-mount.stl` for pole and mast installation
* Source file (`.FCStd` for FreeCAD) so the design is editable, not just printable

## Status

Not yet started. The enclosure design is an open item on the v1.0 punch list.

## License

All files published here will be licensed under [CERN-OHL-S-2.0](../LICENSE). Derivative designs must be shared under the same license.

## How to contribute a CAD design

If you have experience with FreeCAD, Fusion 360, OpenSCAD, or Onshape and want to produce the first draft of the enclosure, please open an issue in this repository to coordinate. Constraints:

* Printable on a 200 mm bed in PETG or ASA
* IP65 equivalent when sealed with the gasket listed in `BOM.md`
* Accommodates the RAK WisBlock RAK4631 baseline module (primary) and the Heltec LoRa32 V4 (fallback) with minimal design changes
* Cable entry for a solar lead via M12 gland
* SMA bulkhead for the antenna
* Mounting features for zip ties, hose clamp, and U bolt options
* Desiccant pocket

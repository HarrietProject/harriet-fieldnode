# harriet-fieldnode

The FieldNode is Tier 3 of the Harriet hardware stack. It is a solar powered, weatherproof Reticulum relay node designed to be placed in the field and left unattended for extended periods. One small computer, one LoRa radio, one battery, one antenna, one job: relay mesh traffic.

The FieldNode is the first Harriet deliverable. It is targeted for 2026. It is the simplest tier to build, the cheapest to deploy, and the one that delivers immediate value to the wider Reticulum network the moment it comes online.

## Status

Early architecture phase. Hardware selection is locked at the module level (see `SPEC.md`). The prototype build is pending component delivery. Enclosure CAD is not started. No finished kit is shipping yet.

## What you get when the FieldNode ships

* A documented bill of materials with US first sourcing and approximate prices
* A step by step build guide that a motivated person can follow in an afternoon
* Flashing instructions for RNode firmware
* A weatherproof enclosure design suitable for outdoor, mast, or rooftop mounting
* A deployment guide covering placement, solar orientation, and maintenance

The FieldNode does not require a subscription, an account, a SIM card, a cell tower, or a working internet connection. Once deployed, it participates in the Reticulum mesh as a transport node and forwards traffic for any Harriet, Sideband, MeshChat, or Columba user within LoRa range.

## Target cost

60 to 100 USD per node, depending on component choice and sourcing.

## Why the FieldNode ships first

1. Lowest engineering complexity of any Harriet tier. No custom PCB, no Android build, no display integration.
2. Immediate utility. Every node deployed adds routing capacity to the Reticulum mesh.
3. Low barrier to entry. An afternoon build at consumer component prices is the widest possible on ramp for contributors.
4. Supply chain validation. Shipping the first 50 kits exposes every sourcing, documentation, and logistics issue before the more complex Anchor and Brick tiers are attempted.
5. Revenue path. Pre built FieldNode kits fund development of the higher tiers.

## Files in this repository

| File | Purpose |
|------|---------|
| `SPEC.md` | Complete hardware specification and module selection rationale |
| `BOM.md` | Bill of materials with sourcing and approximate prices |
| `BUILD_GUIDE.md` | Step by step assembly instructions (placeholder pending prototype) |
| `FIRMWARE.md` | RNode firmware flashing and configuration |
| `DEPLOYMENT.md` | Field placement, solar orientation, maintenance |
| `hardware/` | CAD files for enclosure and mounting hardware (placeholder) |
| `CONTRIBUTING.md` | How to contribute, including AI assisted contribution disclosure |
| `LICENSE` | CERN-OHL-S-2.0 |

## Related repositories

| Repository | Role |
|------------|------|
| [Harriet](https://github.com/HarrietProject/Harriet) | Project overview, governance, threat model, channel plan |
| [harriet-docs](https://github.com/HarrietProject/harriet-docs) | Reticulum setup, radio primer, software stack guide |
| [harriet-kits](https://github.com/HarrietProject/harriet-kits) | Pre built kit offerings and sourcing guides |
| [harriet-anchor](https://github.com/HarrietProject/harriet-anchor) | Tier 2 base station that anchors a local FieldNode cluster |

## License

Hardware designs, schematics, and CAD files in this repository are licensed under [CERN-OHL-S-2.0](LICENSE). See the main [Harriet](https://github.com/HarrietProject/Harriet) repository for full license terms across the project.

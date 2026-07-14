# Contributing to harriet-fieldnode

Thank you for considering a contribution. This repository is part of Project Harriet, an open source hardware and documentation effort. Contributions of all kinds are welcome: hardware improvements, firmware configuration notes, build photographs, measurement data, sourcing information, corrections, and clearer writing.

See the main [Harriet](https://github.com/HarrietProject/Harriet) repository for project wide governance and the code of conduct.

## How to contribute

1. Fork this repository.
2. Create a branch with a descriptive name, for example `fieldnode-enclosure-cad` or `bom-eu-sourcing`.
3. Make your changes.
4. Open a pull request against `main` with a clear description of what changed and why.

## What makes a good contribution

* Specific and actionable. "Add EU vendor for RAK WisBlock" is better than "improve sourcing."
* Backed by data. Current draw measurements, range tests, and photographs beat opinions.
* Consistent with locked project decisions. See Section 18 of the main project decisions document before proposing changes to the hardware stack.
* Licensed compatibly. Hardware contributions under CERN-OHL-S-2.0. Documentation under CC BY-SA 4.0.

## AI assisted contribution disclosure

If you used a language model or other AI tool to generate any part of your contribution, you must disclose this in the pull request description. A short note such as "portions of the BOM narrative were drafted with an AI assistant and verified manually" is sufficient.

This requirement is a governance decision of Project Harriet. It exists because undisclosed AI authored contributions to open source communications projects have caused trust incidents in adjacent ecosystems. Harriet takes a different position: AI tools are legitimate but must be visible.

## Reporting issues

Hardware and documentation issues can be filed in the issue tracker. Please include:

* Which variant you built (RAK4631 baseline, Heltec fallback, LILYGO variant)
* Firmware version (`rnodeconf --info` output)
* A description of what happened and what you expected to happen
* Environmental conditions if relevant (temperature, weather, mounting)
* Photographs if they help

## Code of conduct

Contributors are expected to follow the project code of conduct, which is published in the main [Harriet](https://github.com/HarrietProject/Harriet) repository.

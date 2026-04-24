# FieldNode Build Guide

Status: placeholder. This document will be filled in once the v1 prototype has been built and validated outdoors. Target timeframe: 2026.

## 1. Scope

This guide covers the physical assembly of a single FieldNode from the components listed in `BOM.md`. It assumes the reader has basic soldering skills, access to a 3D printer or printed parts, and no prior radio experience.

Firmware flashing is covered in `FIRMWARE.md`. Field placement is covered in `DEPLOYMENT.md`.

## 2. Expected time

An experienced builder: 2 to 3 hours, excluding print time for the enclosure.
A first time builder: 4 to 6 hours, excluding print time for the enclosure.

## 3. Required tools

* Soldering iron, 350 C
* 60/40 or SAC305 solder, 0.6 to 0.8 mm
* Flush cutters
* Wire strippers
* Small Phillips and hex driver set (2.5 mm for M3)
* Multimeter
* Heat gun for heat shrink and threaded inserts
* Isopropyl alcohol and flux for cleanup

## 4. Procedure (outline, to be expanded after prototype)

1. Print the enclosure per the files in `hardware/` (STL or STEP).
2. Install M3 threaded brass inserts in the enclosure body with a soldering iron or dedicated press.
3. Dry fit the LoRa module, PMIC, and battery holder to confirm spacing.
4. Wire the solar input through the schottky diode to the PMIC solar input.
5. Wire the PMIC battery output to the LoRa module power input.
6. Install the battery into the holder. Confirm voltage at the module input with a multimeter before powering up.
7. Install the SMA bulkhead connector. Connect the pigtail from the module to the bulkhead.
8. Install the solar cable through the M12 gland. Apply RTV silicone sealant around the gland at the enclosure face.
9. Install the antenna gasket and tighten the SMA bulkhead.
10. Place the desiccant pack inside the enclosure.
11. Close the enclosure with the EPDM gasket and M3 bolts. Do not overtighten.
12. Flash RNode firmware per `FIRMWARE.md`.
13. Confirm the node comes online on a bench Reticulum instance before field deployment.

## 5. Bench test checklist (pre deployment)

Before any FieldNode is placed in the field, it must pass all of the following:

* [ ] Battery charges from solar input with no module powered
* [ ] Module powers up and boots RNode firmware
* [ ] RNode announces and is visible from a second Reticulum node on the bench
* [ ] Deep sleep current draw is within expected range for the chosen module
* [ ] Antenna VSWR is acceptable on a bench antenna analyzer (target under 2.0)
* [ ] Enclosure passes a dry rain test (5 minutes of simulated rainfall, no ingress)
* [ ] Identity hash is recorded on the serial card

## 6. Safety notes

* Li-ion cells are a fire risk if punctured, short circuited, overcharged, or exposed to high temperatures. Always use a protected cell and a PMIC with overvoltage, undervoltage, and short circuit protection.
* Do not seal the enclosure with a cell at less than 20 percent state of charge. The PMIC may not recover from deep discharge without intervention.
* Solar panels can produce voltages above 6 V in open circuit. Verify PMIC input rating before connecting.
* Antenna feedlines should be short and well secured. A loose SMA connector under tension can short the module.

## 7. Contribution

This guide is a living document. Once the prototype is validated, it will be rewritten as a full step by step illustrated build with photos. Pull requests with photographs, timing data, and clarifications from first time builders are welcome.

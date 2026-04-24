# FieldNode Hardware Specification

Version: 0.1 (draft, pre prototype)
Status: component selection locked at the module level, final SKU selection pending power draw measurements on the prototype bench.

## 1. Mission

A weatherproof, solar powered Reticulum relay that can be deployed to a rooftop, mast, tower, tree, or ridge and left for a year. The node runs RNode firmware in transport node mode. It forwards LoRa mesh traffic for any Reticulum compatible client in range.

The FieldNode has no user interface, no buttons, no screen, and no voice capability. It is pure infrastructure.

## 2. Design constraints

1. Zero subscription and zero infrastructure. The node functions with only sun, line of sight to another LoRa device, and no other inputs.
2. Buildable in an afternoon from off the shelf components.
3. Target total bill of materials: 60 to 100 USD.
4. Target outdoor service interval: 12 months unattended with 4 or more hours of direct sun per day.
5. Legal operation under FCC Part 15 rules in the 902 to 928 MHz ISM band in the United States.
6. All files, schematics, and CAD under CERN-OHL-S-2.0.

## 3. Architecture overview

```
+----------------+      +---------------+      +------------------+
| Solar panel    | ---> | Charge / PMIC | ---> | Battery          |
| 5 to 6 V, 1-3W |      | (BQ25895 or   |      | Li-ion 2000-6000 |
|                |      |  TP4056)      |      | mAh              |
+----------------+      +-------+-------+      +------------------+
                                |
                                v
                        +---------------+
                        | LoRa module   | <--- 915 MHz antenna
                        | (see 4.1)     |
                        +---------------+
```

All components sit inside a single weatherproof 3D printed enclosure with an external SMA antenna port, an external solar panel cable entry, and a desiccant pocket.

## 4. Component selection

### 4.1 Compute and radio module

The FieldNode is built around a single combined LoRa + MCU module. Three candidates are tracked. The final v1.0 kit SKU will be chosen after measured current draw data from a prototype bench test. All three run RNode firmware v1.82 or newer via the `rnodeconf --autoinstall` tool.

| Option | SoC | LoRa chip | Typical price (US) | Deep sleep | Notes |
|--------|-----|-----------|--------------------|-----------|-------|
| RAK WisBlock RAK4631 | Nordic nRF52840 | Semtech SX1262 | 25 to 37 USD kit | 11 uA | Best candidate for solar duty cycle. Low power champion. |
| LILYGO T-Beam Supreme | Espressif ESP32-S3 | Semtech SX1262 | 50 to 70 USD | roughly 150 uA | Integrated u-blox M10S GNSS, BME280, IMU. Frequently out of stock. |
| Heltec LoRa32 V4 | Espressif ESP32-S3 | Semtech SX1262 | 32 to 50 USD | several hundred uA typical | 28 dBm TX capability. Widely available. Use as fallback. |

Reference information on these modules is published by Rokland, RAK Wireless, LILYGO, and Heltec Automation.

**Current working assumption:** the RAK WisBlock RAK4631 is the preferred module for the solar powered FieldNode because its deep sleep current makes unattended outdoor operation tractable on a small battery and small solar panel.

### 4.2 Power system

| Sub-component | Selection | Notes |
|---------------|-----------|-------|
| Battery | Single cell Li-ion or LiPo, 2000 to 6000 mAh, 3.7 V nominal | 18650 or 21700 for serviceability; flat LiPo for compact variants |
| Charge IC | BQ25895 preferred, TP4056 acceptable for budget builds | BQ25895 provides true power path, I2C telemetry, and input current optimization suitable for small solar panels |
| Solar panel | 5 to 6 V, 1 to 3 W monocrystalline mini panel | Voltaic V6 style, Amazon generics, or equivalent |
| Protection | Schottky diode on panel input, polyfuse on battery line | Standard practice |

The target is indefinite solar sustained operation at 4 or more hours of direct sun per day. See `DEPLOYMENT.md` for placement guidance.

### 4.3 Antenna

| Sub-component | Selection | Notes |
|---------------|-----------|-------|
| Primary antenna | 915 MHz 2 dBi rubber duck, SMA male | Baseline for portable and urban deployments, roughly 5 USD |
| Fixed site antenna | 915 MHz 3 to 6 dBi omnidirectional colinear, N or SMA | Rooftop or mast installations, roughly 15 to 45 USD |
| Connector on enclosure | SMA female bulkhead with rubber gasket | IP65 when mated with mating antenna |
| Pigtail | SMA or U.FL to match module | Low loss RG316 for short runs |

Antenna gain must be chosen so that total effective radiated power remains within FCC Part 15 limits for 902 to 928 MHz.

### 4.4 Enclosure

| Sub-component | Selection | Notes |
|---------------|-----------|-------|
| Material | 3D printed PETG or ASA | ASA preferred for UV resistance |
| Sealing | EPDM foam gasket, IP65 equivalent | Silicone sealant on cable penetrations |
| Cable entry | M12 compression gland for solar lead, SMA bulkhead for antenna | Both rated IP65 |
| Fasteners | 8x M3 threaded brass inserts, M3 stainless bolts | No ferrous hardware |
| Mounting | Slots for zip ties, hose clamp straps, or U bolt mast mount | Rooftop parapet brackets as a later option |
| Internal | Silica gel desiccant pack, foam cell battery retention | Desiccant is replaced annually |

Enclosure CAD is not yet published. `hardware/` will contain STEP and STL files once the v1 prototype has been validated outdoors.

## 5. Firmware

* RNode firmware version 1.82 or newer
* Installed via `rnodeconf --autoinstall`
* Role: transport node (always on), not a user handset
* Channels: see `CHANNEL_PLAN.md` in the main [GroundWave](https://github.com/GroundWaveJack/GroundWave) repository
* Identity: generated at first boot; the identity hash is written on a laminated serial card included with each kit

See `FIRMWARE.md` for the flashing procedure.

## 6. Operating parameters

| Parameter | Target |
|-----------|--------|
| Continuous RX duty cycle | 100 percent when battery voltage is above low cutoff |
| Average current draw | to be measured on prototype, target under 30 mA RX idle on RAK4631 |
| Enclosure temperature range | minus 20 C to plus 60 C |
| Ingress protection | IP65 equivalent |
| Service interval | 12 months unattended |
| TX duty cycle | RNode default, LoRa mesh typical |
| Effective radiated power | within FCC Part 15 limits for 902 to 928 MHz |

## 7. Known open questions

These items are tracked as open. Pull requests with measurements and data are welcome.

1. Final module SKU (RAK4631 vs LILYGO T-Beam Supreme vs Heltec LoRa32 V4). Depends on measured current draw and battery plus panel sizing.
2. Enclosure CAD. Not started. Contributors with FreeCAD, Fusion 360, or OpenSCAD experience are invited.
3. Optimal antenna gain by deployment type (portable, mast, ridge line).
4. Winter and low sun performance. Needs empirical validation in the 35 to 45 degrees north latitude band.
5. Reliability at sustained temperatures above 55 C inside the enclosure.

## 8. Success criteria for v1.0

1. Three independent builders, working only from the files in this repository, can produce a working FieldNode.
2. One assembled unit operates unattended outdoors for 30 continuous days.
3. The unit relays Reticulum mesh traffic that can be observed from a second Reticulum node.
4. All design files are present in this repository under CERN-OHL-S-2.0.
5. The bill of materials in `BOM.md` is accurate to within plus or minus 10 percent at the time of publication.

## 9. References

Specifications above are compiled from published datasheets and community testing of the listed modules. See `BOM.md` for vendor links and `FIRMWARE.md` for RNode documentation references.

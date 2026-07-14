# FieldNode Bill of Materials

Version: 0.1 (draft)
Prices are approximate as of early 2026 and are subject to tariff and stock fluctuation. All prices are in US dollars.

This bill of materials covers the baseline solar powered FieldNode. Fixed site and portable variants are noted where applicable.

## 1. Core modules

| Ref | Item | Qty | Price | Primary source | Alt source | Notes |
|-----|------|-----|-------|----------------|------------|-------|
| U1  | RAK WisBlock Starter Kit 915 MHz (RAK19007 base + RAK4631 core) | 1 | 30 | [Rokland](https://store.rokland.com/) | [RAK Store](https://store.rakwireless.com/) | Baseline module. nRF52840 + SX1262. 11 uA deep sleep. |
| U1a | Alt: LILYGO T-Beam Supreme 915 MHz | 1 | 55 | [LILYGO Shop](https://www.lilygo.cc/) | AliExpress, Rokland when stocked | Only if RAK4631 is not chosen as final SKU |
| U1b | Alt: Heltec LoRa32 V4 915 MHz | 1 | 35 | [Heltec Store](https://heltec.org/) | Rokland, Amazon | Fallback if RAK4631 is not available |

## 2. Power system

| Ref | Item | Qty | Price | Primary source | Notes |
|-----|------|-----|-------|----------------|-------|
| BAT1 | 18650 or 21700 Li-ion cell, protected, 3000 to 5000 mAh | 1 | 8 to 18 | 18650BatteryStore, IMR Batteries | Samsung 30Q, Samsung 50E, Molicel P28A are acceptable |
| BAT2 | Cell holder (18650 or 21700) with solder tabs | 1 | 2 | DigiKey, Amazon | Match chosen cell |
| PMIC1 | Solar compatible Li-ion charger board, BQ25895 based | 1 | 10 to 15 | DFRobot, Adafruit, SparkFun | BQ25895 preferred. TP4056 accepted for budget builds. |
| SOL1 | 5 to 6 V, 2 to 3 W monocrystalline solar panel | 1 | 10 to 20 | Voltaic, Amazon generics | Match enclosure face area |
| D1 | Schottky diode, SS14 or equivalent, 1 A 40 V | 1 | 0.20 | DigiKey, Mouser | Reverse blocking on panel input |
| F1 | Polyfuse, 1 A to 2 A hold | 1 | 0.50 | DigiKey, Mouser | On battery line |

## 3. Antenna and RF

| Ref | Item | Qty | Price | Primary source | Notes |
|-----|------|-----|-------|----------------|-------|
| ANT1 | 915 MHz 2 dBi rubber duck, SMA male | 1 | 5 | Rokland, DigiKey, Amazon | Baseline antenna |
| ANT2 | Optional: 915 MHz 3 to 6 dBi colinear omni, N or SMA | 0 or 1 | 15 to 45 | Rokland, Proxicast | Fixed site variant |
| CON1 | SMA female bulkhead connector with O-ring | 1 | 3 | DigiKey, Amazon | IP65 when mated |
| CAB1 | U.FL to SMA pigtail, RG316, 10 to 15 cm | 1 | 3 | DigiKey, Amazon | Match connector on chosen module |

## 4. Enclosure and mechanical

| Ref | Item | Qty | Price | Primary source | Notes |
|-----|------|-----|-------|----------------|-------|
| ENC1 | 3D printed enclosure in ASA or PETG | 1 | 3 to 10 | Self printed | STL and STEP will be published in `hardware/` |
| GSK1 | EPDM foam gasket strip, 3 mm x 10 mm | 1 | 2 | McMaster-Carr, Amazon | Enclosure seam seal |
| GLD1 | M12 cable compression gland, IP68 | 1 | 2 | Amazon, DigiKey | Solar cable entry |
| INS1 | M3 brass threaded inserts, heat set | 8 | 0.10 each | McMaster-Carr, Amazon | Enclosure body |
| BLT1 | M3 x 8 stainless steel socket cap bolts | 8 | 0.10 each | McMaster-Carr | Matching |
| DSC1 | Silica gel desiccant pack, 5 g, indicating | 1 | 0.25 | Amazon, Uline | Internal humidity control |
| MNT1 | Mounting hardware (zip ties, hose clamp, or U bolt) | set | 2 to 8 | Hardware store | Installation dependent |

## 5. Consumables

| Item | Qty | Price | Notes |
|------|-----|-------|-------|
| Silicone sealant (RTV) | small tube | 4 | Cable penetration detail |
| Heat shrink tubing assortment | set | 5 | Wiring |
| Solder, 60/40 or SAC305 | as needed | 10 per roll | Standard |

## 6. Totals by variant

| Variant | Module | Antenna | Battery | Estimated BOM |
|---------|--------|---------|---------|---------------|
| Baseline (urban or portable) | RAK4631 | 2 dBi rubber duck | 3000 mAh 18650 | 65 to 80 USD |
| Fixed site | RAK4631 | 6 dBi colinear omni | 5000 mAh 21700 | 90 to 120 USD |
| Budget | Heltec LoRa32 V4 | 2 dBi rubber duck | 3000 mAh 18650 | 55 to 75 USD |

Prices exclude shipping, consumables already on hand, and 3D printing filament cost.

## 7. Sourcing notes

* **Rokland** (store.rokland.com) is the recommended US first source for LoRa modules. They stock RAK, LILYGO, and Heltec with US warehousing and avoid the import duty surprise.
* **DigiKey** and **Mouser** are the preferred sources for passives, connectors, PMICs, and mechanical hardware. Same day shipping, US stock, predictable tariff handling.
* **Amazon** is acceptable for commodity items (cable, enclosure accessories, antennas) but avoid it for semiconductors and critical ICs where counterfeit risk exists.
* **AliExpress** may quote lower prices but US customs duties now commonly add 25 to 60 percent to electronics imports. Price it with duty included before choosing this channel.

## 8. Supply chain risk

| Risk level | Item | Mitigation |
|------------|------|------------|
| Low | RAK WisBlock, Heltec LoRa32, sensors, connectors, enclosure materials | Multiple US sources |
| Moderate | Solar panels (specific wattage and voltage) | Substitute voltage compatible equivalents |
| High | LILYGO T-Beam Supreme | Frequently sold out. Use RAK or Heltec as fallback. |

See [harriet-kits/SUPPLY_CHAIN.md](https://github.com/HarrietProject/harriet-kits) for a project wide risk register.

## 9. Contributions welcome

Corrections, vendor additions, and regional sourcing alternatives (EU, UK, AU, CA) are welcome as pull requests. Include:

* Vendor name and URL
* Part number and description
* Current price at time of submission
* Any tariff or shipping notes
* Your country of purchase

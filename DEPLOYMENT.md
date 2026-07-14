# FieldNode Deployment Guide

The FieldNode is designed to be installed once and left unattended for approximately one year. This document covers placement, solar orientation, expected range, and maintenance.

## 1. Siting principles

A FieldNode adds value to a Reticulum mesh in direct proportion to its line of sight to other Reticulum nodes. LoRa is a radio technology with limited foliage and terrain penetration. The two single biggest factors in deployed range are:

1. Antenna height above surrounding terrain and structures
2. Direct line of sight to a peer node

Rule of thumb: elevating the antenna from 2 meters to 10 meters above ground often doubles or triples effective range in suburban terrain. Dense forest, buildings, and steep valleys cut range dramatically.

## 2. Placement checklist

Before installing a FieldNode, confirm:

* [ ] Clear view of the sky for 4 or more hours of direct sun per day, facing within 30 degrees of true solar south (northern hemisphere) or true solar north (southern hemisphere)
* [ ] Antenna position has line of sight to at least one known peer node, or is elevated enough to reach one through terrain
* [ ] The enclosure is secure against wind up to the worst expected gust in the local climate
* [ ] No overhanging metal roofing or awning within 1 meter of the antenna
* [ ] Cable runs are strain relieved at the enclosure
* [ ] The identity hash on the serial card has been recorded and stored off device

## 3. Solar orientation

* **Northern hemisphere:** solar panel faces true solar south, tilted at an angle roughly equal to site latitude in degrees. For year round performance with minimal adjustment, use latitude plus 10 degrees.
* **Southern hemisphere:** mirror the above, facing true solar north.
* **Equatorial sites:** panel flat or with 10 degrees tilt for self cleaning by rainfall.

True south is not magnetic south. The magnetic declination offset varies by location. For a site in the continental United States, declination can be obtained from the NOAA magnetic declination calculator (available offline as a PDF table). See the paper map and declination card shipped with the Ghost tier kit for an offline reference.

## 4. Mounting options

| Location | Mount | Notes |
|----------|-------|-------|
| Rooftop parapet | U bolt or parapet clamp | Easiest for residential and small commercial sites |
| Mast on a building | Hose clamp or U bolt to a 25 to 50 mm mast | Good elevation, moderate installation effort |
| Tree, live branch | Strap, not bolt | Do not penetrate living wood. Relocate as the tree grows. |
| Tree, dead wood | Bolt | Acceptable for standing deadwood; not for climbing |
| Standalone pole | 2 inch galvanized pipe with guying, set in ground | Highest effort, best performance |
| Vehicle or trailer | Magnetic base or NMO mount, 3 dBi whip | Mobile variant, not the baseline FieldNode |

For the baseline enclosure, zip ties, hose clamps, or a U bolt are provided by the builder. A rooftop FieldNode is usually the highest return on effort.

## 5. Expected range

Range is highly site dependent. Published and community tested figures:

| Environment | Expected LoRa range |
|-------------|---------------------|
| Dense urban, low antenna (under 3 m) | 100 to 500 m |
| Suburban, antenna at 6 to 10 m | 1 to 3 km |
| Rural clear terrain, antenna at 10 m | 5 to 10 km |
| Ridge to ridge line of sight | 20 km and beyond |
| Balloon or aircraft relay to ground | 100 km and beyond (research) |

These figures are conservative. LoRa with SX1262 at 22 dBm and a 6 dBi antenna regularly achieves better performance with good elevation.

## 6. Ongoing operation

### Monthly

* No user action required in normal operation.

### Quarterly (if accessible)

* Verify the node is reachable via Reticulum from a known peer.
* Wipe the solar panel face clean of dust, pollen, or bird droppings.

### Annually

* Retrieve the node. Open the enclosure. Inspect for moisture intrusion.
* Replace the silica gel desiccant pack.
* Check battery health. Replace the cell if capacity has dropped more than 30 percent from baseline.
* Reseat the antenna connector. Apply fresh RTV silicone if degraded.
* Return to service.

### On failure

1. Retrieve the node.
2. Record the failure mode (no RF, no power, water ingress, mechanical damage).
3. Repair or replace components as needed.
4. Re flash firmware only if the identity has been compromised or the flash is corrupt. Otherwise, reuse the existing identity so the node keeps its presence on the mesh.
5. Redeploy.

## 7. Decommissioning

A FieldNode that is permanently retired from service should have its identity revoked (future work) and the cell discharged and recycled at a municipal battery drop off. The enclosure, PCB, and solar panel are recyclable via standard electronics and plastics channels.

## 8. Legal notes

The FieldNode operates in the 902 to 928 MHz ISM band under FCC Part 15 rules in the United States. No license is required. Operators remain responsible for antenna gain and effective radiated power compliance. The FieldNode at the baseline antenna gain (2 dBi rubber duck) and the chosen module's TX power is inside these limits.

Installation on property you do not own requires permission of the owner. Installation on utility poles, public towers, or commercial structures requires written permission and may require a structural engineering review.

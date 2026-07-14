# FieldNode Firmware

The FieldNode runs RNode firmware in transport node mode. RNode is the reference LoRa firmware developed for the Reticulum Network Stack. It is self replicating: any RNode can flash any compatible supported board using the RNode auto installer.

## 1. Firmware version

* RNode firmware v1.82 or newer
* Reticulum stack v1.1.3 or newer on the host used to flash

## 2. Supported boards for the FieldNode

The following boards are supported by RNode and are viable FieldNode hardware. See `SPEC.md` for the selection rationale.

* RAK WisBlock RAK4631 (nRF52840 + SX1262), preferred
* LILYGO T-Beam Supreme (ESP32-S3 + SX1262), when available
* Heltec LoRa32 V4 (ESP32-S3 + SX1262), fallback

## 3. Flashing procedure

The procedure below uses the official RNode tooling. Do not attempt to build RNode firmware from source unless you have a specific reason.

### 3.1 Install the tooling

On a Linux, macOS, or Windows host with Python 3.9 or newer:

```
pip install rns rnodeconf
```

This installs the Reticulum stack and the RNode configuration utility. On Linux, add your user to the `dialout` group (Debian or Ubuntu) or `uucp` group (Arch) so that serial port access does not require root.

### 3.2 Connect the board

Connect the chosen board to the flashing host with a known good USB data cable. Power the board from USB only. Do not connect the battery or solar input during flashing.

Confirm the host sees a serial device:

```
rnodeconf --list
```

### 3.3 Run the auto installer

```
rnodeconf /dev/ttyACM0 --autoinstall
```

Replace `/dev/ttyACM0` with the serial device reported by `rnodeconf --list`. On macOS the device appears under `/dev/tty.usbmodem*`. On Windows the device appears as `COMn`.

The auto installer detects the board, downloads the correct firmware image, flashes it, and configures the radio parameters. Follow the prompts.

### 3.4 Set frequency and channel

The installer asks for a frequency. Use the Harriet channel plan. See [CHANNEL_PLAN.md](https://github.com/HarrietProject/Harriet/blob/main/CHANNEL_PLAN.md) in the main Harriet repository for current assignments.

For the v1.0 FieldNode, the default channel is Harriet CH2 (relay only). The node is configured to forward traffic for CH0, CH1, CH2, and CH9 within legal duty cycle.

### 3.5 Enable transport mode

A FieldNode must have transport mode enabled. On the host that will use the FieldNode as a transport, or on the FieldNode itself if it runs a Reticulum instance, set:

```
[reticulum]
enable_transport = True
```

in `~/.reticulum/config`. For a bare RNode based FieldNode that does not run Reticulum itself, transport forwarding is inherent to the RNode firmware when announced by a paired Reticulum instance.

### 3.6 Record the identity hash

After flashing, the device prints an identity hash. Write this hash on the laminated serial card shipped with the kit. This hash identifies the node on the Reticulum network for the life of the firmware installation.

## 4. Verification

After flashing:

1. Run `rnodeconf /dev/ttyACM0 --info`. Confirm the firmware version and frequency match the values set during the install.
2. On a second host with Reticulum, run `rnstatus`. The FieldNode should appear as a reachable interface within a minute.
3. From a Sideband, MeshChat, or Columba client on a second device, send a test message to a known LXMF destination and confirm delivery.

## 5. Updating firmware in the field

FieldNode firmware is not updated remotely in v1.0. A field update requires physical retrieval of the node and reconnection to a USB host.

Future work may include over the air firmware updates via Reticulum, but this is out of scope for v1.0 and is tracked as a research item.

## 6. References

* RNode project and firmware: published by the original Reticulum author. The `rnodeconf --autoinstall` tool continues to work as of early 2026.
* RetiNet: an AGPL fork of Reticulum with identical wire format. Usable as a replacement host stack.
* Reticulum-rs: a Rust implementation tracked for future integration.

See [harriet-docs/RETICULUM_GUIDE.md](https://github.com/HarrietProject/harriet-docs) for background on the Reticulum stack and the current fork situation.

---
name: download
description: Flash/download firmware to the RA8P1 target via pyocd/DAPLink. Use when the user asks to download, flash, or program the chip.
---

# Download firmware to RA8P1

Flash the compiled firmware (rtthread.hex) to the RA8P1 chip via DAPLink using pyocd.

## Prerequisites

The project must be compiled first (see the `compile` skill). The hex file is at `build/target/rtthread.hex`.

## Flash command

Run the following in `/home/a/workspace/minist/titan_board_minist`:

```bash
pyocd load build/target/rtthread.hex -u 5666132D37325 -t r7ka8p1kf -f 1m -e sector
```

| Parameter | Value | Description |
|-----------|-------|-------------|
| `-u` | `5666132D37325` | DAPLink probe unique ID |
| `-t` | `r7ka8p1kf` | Target: RA8P1 DualCore 1M |
| `-f` | `1m` | Flash size: 1 MB |
| `-e` | `sector` | Erase mode: sector |

## Expected warnings (non-fatal)

- SVD parser `AttributeError` — pyocd internal issue with RA8P1 SVD file
- `Error probing AP#2: SWD/JTAG communication failure` — normal for RA8P1 dual-core
- `Invalid coresight component, cidr=0x5900d00` — unrecognized debug component

These do not affect the flash operation. Confirm success by the final line showing "Erased ... bytes, programmed ... bytes".

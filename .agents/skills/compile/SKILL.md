---
name: compile
description: Compile the titan_board_minist RT-Thread project (RA8P1, Cortex-M85, GCC). Use when the user asks to build or compile this project.
---

# Compile titan_board_minist

Compile the RT-Thread firmware for the RA8P1 platform.

## Build command

Run the following in `/home/a/workspace/minist/titan_board_minist`:

```bash
RTT_EXEC_PATH=/usr/bin scons -j$(nproc)
```

- The `RTT_EXEC_PATH` environment variable overrides the Windows path in `rtconfig.py` to point to the Linux ARM GCC toolchain at `/usr/bin`.
- Output files: `build/target/rtthread.elf` and `build/target/rtthread.hex`.

If compilation succeeds, report the memory usage summary (RAM/FLASH) and confirm the output.

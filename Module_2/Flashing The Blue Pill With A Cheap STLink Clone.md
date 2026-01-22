
## Flashing The Blue Pill With A Cheap STLink Clone

- If you try to connect and try to flash a Blue Pill via an ST-Link clone (the ones widely available in grift marts online), you'll be forced into a firmware update that locks out devices with a specific internal ID which is unauthorised by ST.
- It seems as if we're out of luck. STM32CubeIDE is such an incredibly powerful tool, but if I can't get hold of a relatively expensive programmer, I can't program boards which are not officially distributed by STMicroelectronics.   
- Thankfully, here's where the st-flash utility comes to our rescue. 

### What is `st-flash`?

- `st-flash` is a command-line utility for programming STM32 microcontrollers via the SWD interface using ST-Link programmers—**both original and most clones**.
- It is part of the stlink project on GitHub, and works on Windows, macOS, and Linux.

### 1. **Prerequisites**

- **ST-Link V2 clone** (can be found for a few dollars online)
- **STM32 target board**
- **Wiring:** Connect SWDIO, SWCLK, 3.3V, GND (optionally NRST) from the ST-Link to the STM32. Consult your board’s pinout.
- **Binary or HEX firmware file** to flash (e.g., `my_firmware.bin`)

### 2. **Installation**

#### **Linux (Ubuntu/Debian)**

```
sudo apt update  
sudo apt install stlink
```

#### **macOS** (with Homebrew)

```
brew install stlink
```

#### **Windows**
- Download prebuilt binaries or build from source:  
  [stlink GitHub Releases](https://github.com/stlink-org/stlink/releases)
- Add the binary folder to your `PATH` for convenient use.

### 3. **Plug in Your ST-Link Clone**

- Connect your ST-Link clone to the PC’s USB port.
- Plug in or connect your STM32 target as described above.

On Linux, you can check the device is detected by running:

```
lsusb
```

You should see an entry like `STMicroelectronics ST-LINK/V2`.

### 4. **Basic Usage**

#### **Writing a Binary to Flash**

```
st-flash write my_firmware.bin 0x08000000
```

- `my_firmware.bin`: your binary firmware file.
- `0x8000000`: the starting FLASH address for STM32; this is typical for most STM32 MCUs.

Add `--reset` to automatically reset the MCU after flashing:

```
st-flash write my_firmware.bin 0x08000000 --reset
```

#### **Reading Data from MCU**

```
st-flash read output.bin 0x08000000 4096
```

This reads 4096 bytes starting from FLASH memory address `0x08000000` into `output.bin`.

### 5. **Common Tips**

- **HEX files:** You may flash `.hex` files directly; sometimes the address does not need to be specified since it’s included in the HEX.
- **Permissions (Linux):** You may need to run as root (`sudo st-flash ...`) or set up udev rules for non-root access.
- **Erasing Flash:** Flash is automatically erased prior to programming, but you can also mass-erase using:

```
st-flash erase
```

### 6. **Advanced Options**

- Specify target FLASH size for clones with larger memory:

```
st-flash --flash=128k write my_firmware.bin 0x08000000
```

(Use `k` or `M` suffix for kilobytes or megabytes).

### 7.  Example of Common Commands**

#### Write firmware to board, then reset

```
st-flash write my_firmware.bin 0x8000000 --reset
```

#### Erase the entire flash

```
st-flash erase
```

#### Read out 4KB of flash from address 0x08000000

```
st-flash read dump.bin 0x08000000 4096
```


### 9. **References and Further Reading**
For a deep-dive, visit the [official stlink tutorial], [project repo], or practical connection how-to's.

### **Summary Table**

| Task         | Command Example                                     |
| ------------ | --------------------------------------------------- |
| Flash BIN    | `st-flash write my_firmware.bin 0x08000000 --reset` |
| Read Flash   | `st-flash read dump.bin 0x08000000 4096`            |
| Erase Flash  | `st-flash erase`                                    |
| Set Flash Sz | `st-flash --flash=128k write fw.bin 0x8000000`      |

With these steps, you can reliably program STM32 microcontrollers using cheap ST-Link V2 clones with the `st-flash` utility on any platform.

---
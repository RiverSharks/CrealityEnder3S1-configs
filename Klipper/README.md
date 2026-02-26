# Klipper Firmware Configuration

This repository contains my **Klipper firmware configuration** for a specific STM32F4-based board.

> ⚠️ This configuration is tailored for my exact board revision and STM chip.  
> Please verify compatibility before flashing.

---

## 📦 Requirements

- Linux/macOS environment (or WSL)
- `git`
- Build tools required by Klipper
- FAT32-formatted SD card

---

## 🔄 Firmware Upgrade Guide

Follow these steps to build and flash the firmware:

### 1️⃣ Clone or Update Klipper

```bash
git clone https://github.com/Klipper3d/klipper.git
# or if already cloned
cd klipper
git pull
```

---

### 2️⃣ Apply Configuration

Copy the provided `.config` file into the `klipper` root directory:

```bash
cp /path/to/.config klipper/
```

This `.config` file is built specifically for my board and STM32 chip  
(see repository images for board reference).

---

### 3️⃣ (Optional) Reconfigure

If upgrading Klipper or changing hardware, you may want to re-run:

```bash
make menuconfig
```

Verify:
- Micro-controller Architecture
- Processor model (STM32F4 series)
- Bootloader offset
- Communication interface

---

### 4️⃣ Clean Previous Builds

```bash
make clean
```

---

### 5️⃣ Build Firmware

```bash
make
```

After successful build, the firmware will be located at:

```
out/klipper.bin
```

---

### 6️⃣ Flash the Firmware

1. Format SD card as **FAT32**
2. Copy firmware to:

```
STM32F4_UPDATE/unique_name.bin
```

⚠️ **Important:**
- The filename must be unique.
- If you reuse the same filename, the board may skip flashing.
- Example:

```
STM32F4_UPDATE/firmware_v2.bin
```
3. Disable printer and remove any connected usb devices
4. Insert SD card into the board.
5. Enable printer and wait for 1 minute
6. Disable printer and connected devices
7. Enable printer and it should be upgraded.


---

## 📝 Notes

- This configuration is tested on my hardware only.
- Always back up your working firmware before flashing.
- Double-check voltage and bootloader compatibility.

---

## 📸 Hardware Reference

See the repository images for board photos and chip markings.

---

## ⚠️ Disclaimer

Flashing firmware always carries risk.  
Proceed at your own responsibility.
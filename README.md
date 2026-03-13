```markdown
# TWRP Device Tree for UNISOC UD710 (Tiger T710)

Minimal TWRP device tree for UD710-based devices with eMMC/UFS. Includes prebuilt kernel, FBE decryption, and essential recovery components.

## Adapting for Your Device

To use this tree on another UD710 device:

1. Edit `BoardConfig.mk`: adjust `TARGET_DEVICE`, kernel command line, partition sizes.
2. Replace `prebuilt/Image.gz-dtb` with your device's kernel if needed.
3. Update `recovery.fstab` with correct partition names and mount points.
4. Rename `omni_ud710_2h10.mk` to `omni_<device>.mk` and adjust contents.


## Building

```bash
# Initialize TWRP manifest (twrp-9.0 branch)
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni -b twrp-9.0
repo sync

# Setup environment and build
source build/envsetup.sh
lunch omni_ud710_2h10-eng
make recoveryimage -j$(nproc --all)
```

Output: out/target/product/ud710_2h10/recovery.img

Credits

· Atlas for decryption help
· OmniROM team for TWRP base

```
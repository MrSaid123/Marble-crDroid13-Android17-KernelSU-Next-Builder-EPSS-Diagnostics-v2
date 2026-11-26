# POCO F5 (marble) — crDroid 13.1 / Android 17 build profile

This builder profile uses the LineageOS `lineage-24.0` kernel, modules and
Devicetree repositories as the Android 17 baseline for marble:

- `LineageOS/android_kernel_xiaomi_sm8450`
- `LineageOS/android_kernel_xiaomi_sm8450-modules`
- `LineageOS/android_kernel_xiaomi_sm8450-devicetrees`
- branch: `lineage-24.0`
- base defconfig: `gki_defconfig`
- fragments: `vendor/waipio_GKI.config`, `vendor/xiaomi_GKI.config`,
  `vendor/marble_GKI.config`, `vendor/debugfs.config`
- compiler: Android Clang `clang-r416183b`

The profile is a source-compatible candidate, not a claim that a kernel has
already been built or boot-tested on crDroid 13.1. The official LineageOS
marble build guide lists `lineage-24.0` as a supported branch; crDroid 13.1
for marble is Android 17. The exact kernel revision used by the crDroid
maintainer's November 2026 build has not been independently confirmed here.

## GitHub Actions

Run **Build Marble Kernel** with:

- Kernel source: `lineage-24.0-marble`
- Build: `KernelSU-Next`
- SUSFS: enabled
- Toolchain: `auto`
- LTO: `thin`
- Build scope: `image-only`

The generated AnyKernel3 installer no longer rejects the ROM solely because
its build fingerprint does not identify Pablo/AOSPA. Device matching remains
restricted by AnyKernel3's `marble` / `marblein` device properties.

A successful CI run is still required before flashing. First boot testing is
not implied by successful compilation.

# Cam OV3660 firmware

Dedicated OV3660 ESP32-S3 N16R8 firmware repository. The OV5640 project is separate.

## Planned update
- Green startup LED: GPIO41
- Blue BLE LED: GPIO42
- BLE Live web viewer: rotate 90° clockwise
- Saved photo orientation and capture logic unchanged

## Build prerequisites
The original final archive contains a single 80 KB `.cpp` source and compiled binaries, **not** the complete ESP-IDF project, including its project-local exFAT FatFs integration. The previously compiled binary does **not** contain the new LED pin assignments.

To build a valid new image, add the original ESP-IDF project tree at the repository root, including `CMakeLists.txt`, `main/CMakeLists.txt`, `sdkconfig.defaults` (if used), and the custom exFAT FatFs component and other dependencies. Replace the corresponding source with `ESP32_Cam_HD_FULL_EXFAT_SOURCE_LED41_42.cpp` from the supplied source package and retain the original component wiring.

The web viewer is a separate HTML asset and does not require firmware compilation.

GitHub Actions will run the ESP-IDF build and upload the generated `.bin` files after the full project is supplied. Do not flash a binary from a failed or unverified build.

# ack-build-workflow
A github workflow to build custom android common kernels with specified parameters

# How to use this?
[Fork this repo](https://github.com/chickendrop89/ack-build-workflow/fork), 
open the 'Actions' tab in your fork and run the only workflow there

These parameters are by default configured for [chickernel](https://github.com/chickendrop89/device_xiaomi_unified-kernel), 
however, they can be configured for any ACK if you know what you're doing.

Parameters:
- 🔴 Android-common-kernel branch:
    - ACK branch to use (e.g. `common-android13-5.15`)
    - Google provides a list of [possible ACK branches here](https://source.android.com/docs/setup/reference/bazel-support)
    - `default:` **common-android13-5.15**
- 🔴 Custom kernel repository:
    - Custom URL leading to your custom kernel repository
    - `default:` **[chickernel](https://github.com/chickendrop89/device_xiaomi_unified-kernel)**
- 🔴 Custom kernel repository branch:
    - Branch to use from your custom kernel repository
    - `default:` **[android13-5.15-lts](https://github.com/chickendrop89/device_xiaomi_unified-kernel/tree/android13-5.15-lts)**
- 🔴 Use the latest clang prebuilts
    - If enabled, will override the ACK manifest to use `main` branch of `clang` prebuilts
    - Select this strictly only if your custom kernel uses them, or if you get the `clang: not found` error.
- 🟡 AnyKernel3 fork URL:
    - Custom URL leading to your AK3 fork
    - Used in post-build to package the kernel image(s)
    - `default:` **[chickernel AK3 fork](https://github.com/chickendrop89/AnyKernel3)**
- 🟡 AnyKernel3 fork branch:
    - Branch to use from your AK3 fork
    - If not set, will use the repo's default branch
- 🟡 Kernel image to package:
    - Decides what image type is packaged with AK3
    - This allows for using compressed `Image.<xxx>` or `Image.<xxx>-dtb`
    - `default`: `Image`
- 🟢 Instruct tools to perform a Fast Build: 
    - If enabled, will force ThinLTO which will reduce the total build time
    - `default:` yes
- 🟢 Use kleaf build system instead of build script:
    - Whether to build using `kleaf (bazel)` instead of `build.sh`
    - Requires a different build configuration type (not starting with `build.config...`)
    - `default:` no
- 🟢 Space-separated list of build configurations:
    - `default:` chickernel vanilla, ksu, ksu + susfs

# Notes
**A**ndroid **c**ommon **k**ernels above `common-android13-5.15` don't have `build.sh` support, 
and building without `kleaf` may not be possible. Make sure to select building with `kleaf` if that's the case.

By default, this GitHub workflow will retain artifacts for 30 days. You can increase or remove this timeout 
if you need to by modifying the `retention-days` value in `build.yml`.

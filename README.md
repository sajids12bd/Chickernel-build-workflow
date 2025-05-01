# gki-build-workflow
A custom github workflow to build kernel images with specified parameters and manifest 

# How to use this?
Either click "[Use this template](https://github.com/new?template_name=gki-build-workflow&template_owner=chickendrop89)" or [fork this](https://github.com/chickendrop89/gki-build-workflow/fork), open the 'Actions' tab in your repo and run the only workflow there

Parameters:
- A manifest URL: 
    - Custom ACK manifest URL (**[example manifests](https://android.googlesource.com/kernel/manifest/+refs)**)
    - `default:` **[chickernel manifest](https://raw.githubusercontent.com/chickendrop89/device_xiaomi_unified-kernel/refs/heads/readme/chickernel.xml)**
- AnyKernel3 fork URL:
    - Custom URL leading to your AK3 fork
    - Used in post-build to package the kernel image(s)
    - `default:` **[chickernel branch of my AK3 fork](https://github.com/chickendrop89/AnyKernel3)**
- Kernel image to package:
    - Decides what image type is packaged with AK3
    - This allows for using compressed `Image.<xxx>` or `Image.<xxx>-dtb`
    - `default`: `Image`
- Instruct tools to perform a fast Build: 
    - If enabled, will force ThinLTO which will reduce the total build time
    - `default:` yes
- Use `bazel` build system instead of build script (not recommended)
    - Whenever to build using `bazel` instead of `build.sh`
    - Requires a different build configuration type (not starting with `build.config...`)
    - `default:` no
- Space-separated list of build configurations:
    - `default:` chickernel vanilla, ksu, ksu + susfs

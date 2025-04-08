# gki-build-workflow
A custom github workflow to build kernel images with specified parameters and manifest 

# How to use this?
Fork this, open the 'Actions' tab in your repo and run the only workflow there

Parameters:
- A manifest URL: 
    - Custom ACK manifest URL (**[example manifests](https://android.googlesource.com/kernel/manifest/+refs)**)
    - default: **[chickernel manifest](https://raw.githubusercontent.com/chickendrop89/device_xiaomi_unified-kernel/refs/heads/readme/chickernel.xml)**
- Fast Build: 
    - If enabled, will force ThinLTO which will reduce the total build time
    - default: 1
- Build configurations:
    - At least the first one is required to build!
    - default: chickernel build configurations

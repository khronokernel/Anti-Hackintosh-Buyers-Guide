# Anti-Hackintosh-Buyers-Guide

Hyperlinks:
* [CPU](README.md#CPU)
* [GPU](README.md#GPU)
* [Motherboard](README.md#Motherboard)
* [Storage](README.md#Storage)
* [RAM](README.md#RAM)
* [Cooler](README.md#Cooler)
* [Networking](README.md#Networking)
* [Wireless](README.md#Wireless)
* [Power Supply](README.md#Power-Supply)
* [Case](README.md#Case)
* [Thermal Paste](README.md#Thermal-Paste)

# An introduction

So what is the Anti Hackintosh Buyers Guide and why should you care about this post? Well this is a guide of what not to buy whne building a hackintosh and will be kept up-to-date as new hardwrae comes out. While this guide won't give exact recommendations, it'll try and point you in the right direction.

# CPUs

**CPUs To Avoid:**

While AMD CPUs can work but we advise highly agaisnt them due to numerous issues still plaguing them as they're not natively supported. They require quite a bit more work to get setup but for those who like pain there is the [AMD Vanilla Guide](https://vanilla.amd-osx.com)

* AMD Ryzen 1000 Series
* AMD Ryzen 2000 Series
* AMD Ryzen 3000 Series
* AMD FX Series

With intel, the thanks to most of the CPUs being quite similar they have support when the CPU is spoofed to a supported model. The only downside is that the iGPU rarely work on these models meaning a cheap iGPU hackintosh is impossible with these CPUs. 

* Intel Atoms
* Intel Celerons
* Intel Pentiums
* Intel X99/LGA 2011

# GPUs

~~Get an RTX GPU, I want to see people suffer as they slowly realize that they don't even have suprt in HighSierra. Let the Nvidia fans die a slow and painful death, let this be a reminder to never cross our lord and savior Tim Apple~~
If you don't want a headache, stay away from all Nvidia GPU that aren't kepler based. Currently(and likely forever), Turing and Volta GPUs have no support whatsoever in any version of macOS while Pascal and Maxwell have their support stopping in High Sierra while also requiring WebDrivers so they're not native GPUs.

With AMD, Navi GPUs drivers are currently not included in either macOS Mojave 10.14.6 nor macOS Catalina 10.15 so please hold off until these GPUs have drivers included in macOS. And Lexa based AMD GPUs like the RX 550 have never had support

For GPUs we recommend, check out the [Mojave GPU Buyers Guide](https://www.reddit.com/r/hackintosh/comments/b91vf5/mojave_gpu_buyers_guide/) and the soon to come [Catalina GPU Buyers Guide](https://github.com/khronokernel/Catalina-GPU-Buyers-Guide)
And for those who are running unspported GPUs, there's still hope for you! With my patent pending [**How to disable your unsupported Nvidia GPU for macOS Guide**](https://github.com/khronokernel/How-to-disable-your-unsupported-GPU-for-MacOS/blob/master/README.md), even a simpleton like you can experice the glories of Mojave and beyond!

**GPUs That Aren't Supported AT ALL**

Turing

* Titan RTX
* RTX 2080/Ti
* RTX 2070
* RTX 2060
* GTX 1660/Ti
* GTX 1650/Ti

* Quadro RTX 4000
* Quadro RTX 5000
* Quadro RTX 6000
* Quadro RTX 8000

Volta

* Titan V
* Titan V CEO Edition

* Quadro GV100

Navi 10

* RX 5700
* RX 5700 XT
* RX 5700 XT 50th Anniversary Edition

Lexa

* RX 540/X
* RX 550/X

**GPUs To Avoid**

Pascal

* GTX Titan X(GP 102-400 Pascal core)
* GTX Titan Xp(GP 102-450 Pascal core)
* GTX 1080/Ti
* GTX 1070/Ti
* GTX 1060
* GTX 1050/Ti
* GT 1030

* Quadro P400
* Quadro P600
* Quadro P620
* Quadro P1000
* Quadro P2000
* Quadro P4000
* Quadro P5000
* Quadro P6000
* Quadro GP100

Maxwell

* GTX Titan X(GM 200 Maxwell core)
* GTX 980/ti
* GTX 970
* GTX 960
* GTX 950
* GTX 750/ti
* GTX 745

* Quadro K620
* Quadro K1200
* Quadro K220
* Quadro M2000
* Quadro M4000
* Quadro M5000
* Quadro M6000
* NVS 510

# Motherboards

So with motherboards the main thing to keep in mind is what controller your sytem is running, specificaly:

* Networking Interface Controller (Ethernet)
* Audio Interface Controller
* USB Controllers

With audio and ethernet, most boards are supported and you can find a more extensive list from [AppleALC](https://github.com/acidanthera/AppleALC/wiki/Supported-codecs) for audio and going through Mieze's ethernet kexts for networking([IntelMausiEthernet.kext](https://github.com/Mieze/IntelMausiEthernet), [AtherosE2200Ethernet.kext](https://github.com/Mieze/AtherosE2200Ethernet) and [RealtekRTL8111.kext ](https://github.com/Mieze/RTL8111_driver_for_OS_X)). And there's patches for usnspported USB with XHCI-unsupported.kext(which can be found within [Rehabman's USBInjectAll's project](https://github.com/RehabMan/OS-X-USB-Inject-All)

But where the real issues come in are when we look towards server boards and non-Z370 300 series motherboards. Server boards don't like to play nicely with macOS so users often opt for running a hypervisor in between to avoid issues with but it still is possible to run macOS natively if you're willing to put the effort in. Non-Z370 300 series motherboards have the issues where nvram, audio and onboard video out don't correectly and require more work to function with onboard video sometimes not fixable even with manual connector patches through WhateverGreen. NVRAM can be solved with either EmuVariableUEFI-64.efi or with [OpenCorePkg](https://github.com/khronokernel/Getting-Started-With-OpenCore)(OC is still in early alpha so avoid unless you like pain)

**Motherboards To Avoid**
* C612 (generally seen in server boards)
* B360
* B365
* H310
* H370
* Q370
* Z390

# Storage

Storage is a section that can be quite confusing as there a lot of mixed reports regarding PCIe/NVMe based devices, manyy of these reports are based off old information from back when PCIe/NVMe drives were not natively supported like block size mattering or require kexts/.efi drivers. Well High Sierra brought native support for these types of drives but certain ones still do not work and can cause iinstability if not removed/blocked out at an ACPI level. These drives include the following:

* Samsung PM981 (Commonly found in OEM systems like laptops)
* Samsung 970 Evo Plus (While not natively supported OOB, a [firmware update from Samsung](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/) will allow these drives to operate in macOS without issue)
* Any eMMC based SSD(Commonly found in netbooks)

# RAM

With RAM, it's generally the same logic for Windows: Make sure the CPU's memory controller can support the speeds you wish to run. macOS seems to be a bit more memory sensitive than Windows so you may get random lock-ups/kernel panics and the more memory you add, the more you need to lower the frequency to ease the memory controller. Generally 32GB 3000Mhz will run just fine on an i7 8700k but an i7 6700k may have to drop to 2666Mhz for stablity reasons

# Cooler

Keep in mind that with an AIO and any cooler that relies on USB will generally have their fan curves, pump speed and RGB lighting reset when booting macOS. Some users in the comunity may have developed a driver/applcation for controlling your model of AIO but do your research to know if yours is affect/has a solution. Solutin for this is to control the fans and pump speed with the motherboard instead

# Networking

This section is specifcally for dedicated NICs, generally

# Wireless

For wireless, keep in mind that macOS has a very limited selection for native Wifi and Bluetooth cards. The [r/Hackintosh FAQ](https://www.reddit.com/r/hackintosh/wiki/faq#wiki_wifi_compatibility) has a great list on supported models

# Power Supply

~~If it has RGB in it, I will personally come to your house and force a Unibeast installer down your throat~~ 
Just don't cheap out on your PSU but be reasonable with what you buy, RGB aint a good purchacing decision

# Case

If your shoe fits in it, your hack will likely boot in it

# Thermal Paste

Don't use tooth paste, that's all I got to say. Nutella is the way to go

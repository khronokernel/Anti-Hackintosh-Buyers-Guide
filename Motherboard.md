# Motherboards

So with motherboards, the main thing to keep in mind is what controller your system is running, specifically:

* Networking Interface Controller (Ethernet)
* Audio Interface Controller
* USB Controllers
* ~~NVRAM~~(Recently fixed)
* RTC vs AWAC

With audio and ethernet, most boards are supported and you can find a more extensive list from [AppleALC](https://github.com/acidanthera/AppleALC/wiki/Supported-codecs) for audio and going through Mieze's ethernet kexts for networking([IntelMausiEthernet.kext](https://github.com/Mieze/IntelMausiEthernet), [AtherosE2200Ethernet.kext](https://github.com/Mieze/AtherosE2200Ethernet) and [RealtekRTL8111.kext](https://github.com/Mieze/RTL8111_driver_for_OS_X)). Please see the Networking section of this guide for more details.

And there's patches for unsupported USB with XHCI-unsupported.kext(which can be found within [Rehabman's USBInjectAll's project](https://github.com/RehabMan/OS-X-USB-Inject-All). See below for AMD Chipset note.

But where the real issues come in are when we look towards server boards and non-Z370 300 series motherboards. Server boards don't like to play nicely with macOS so users often opt for running a hypervisor in between to avoid issues with but it still is possible to run macOS natively if you're willing to put the effort in. Non-Z370 300 series motherboards have the issues where ~~NVARM~~, memory maps, audio and onboard video out don't work correctly and require more work to function with onboard video sometimes not fixable even without [manual BusID patches through WhateverGreen](https://khronokernel.github.io/Opencore-Vanilla-Desktop-Guide/extras/gpu-patches.html). NVRAM luckily was recently fixed with [SSDT_PMC](https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/AcpiSamples/SSDT-PMC.dsl), more info can be found here: [NVRAM for all! 300 series users rejoice!](https://www.reddit.com/r/hackintosh/comments/erd2th/nvram_for_all_300_series_users_rejoice/). 

With RTC vs AWAC, macOS ouright won't boot with systems that have their clock using AWAC and most BIOS GUIs don't even show the option to change it. So we need to either [force RTC with an SSDT](https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/AcpiSamples/SSDT-AWAC.dsl), [create a fake systems clock](https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/AcpiSamples/SSDT-RTC0.dsl) or [patch it out](https://www.hackintosh-forum.de/forum/thread/39846-asrock-z390-taichi-ultimate/?pageNo=2)(both solutions are not ideal).

Another issue these platforms face is that they rely on OsxAptioFix2Drv-free2000 which is now concidered destructive to your system meaning build guides based of it are now invalid. More info can be found [here](https://www.reddit.com/r/hackintosh/comments/cfjyla/i_unleashed_a_plague_upon_you_guys_and_i_am_sorry/). These issues can mostly be aliviated by calculating your slide value: [Understanding and fixing "Couldn't allocate runtime area" errors](https://khronokernel-2.gitbook.io/opencore-vanilla-desktop-guide/extras/kalsr-fix)

While there are workarounds for this platform, anytime you're not running native hardware means there's one more point of failure. Yes, others may have gotten their systems to run but keep in mind that the more complicated an EFI gets, the more places you'll need to examine when troubleshooting and the harder it is for users of the community to help you.

Note for HEDT: Support for these platforms including server boards are much better on OpenCore so if you're having issues it's recommended to try them.

**Chipsets to avoid**
* C612 (generally seen in server boards)
* X79
* X99
* X299
* B360
* B365
* H310
* H370
* Z390

**Brands to avoid**

* MSI(Weird Memory Layout and just really poor ACPI programming, many Z390 systems are unbootable on Clover)
* AsRock(non-native USB controller)


## AMD Chipset boards

While you've avoided my warning on CPUs, I suppose I can at least explain the issues with these boards:

* Chipset differences mean nothing, an X570 will work just as bad as a B450
* Brands also don't matter
* USB is a hit or miss on AMD, you can try to [port map](https://github.com/khronokernel/Opencore-Vanilla-Desktop-Guide/blob/master/AMD/AMD-USB-map.md) them but note that all of them are not native

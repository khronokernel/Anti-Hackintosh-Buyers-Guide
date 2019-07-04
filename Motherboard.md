# Motherboards

So with motherboards, the main thing to keep in mind is what controller your system is running, specifically:

* Networking Interface Controller (Ethernet)
* Audio Interface Controller
* USB Controllers
* NVRAM

With audio and ethernet, most boards are supported and you can find a more extensive list from [AppleALC](https://github.com/acidanthera/AppleALC/wiki/Supported-codecs) for audio and going through Mieze's ethernet kexts for networking([IntelMausiEthernet.kext](https://github.com/Mieze/IntelMausiEthernet), [AtherosE2200Ethernet.kext](https://github.com/Mieze/AtherosE2200Ethernet) and [RealtekRTL8111.kext ](https://github.com/Mieze/RTL8111_driver_for_OS_X)). And there's patches for usnspported USB with XHCI-unsupported.kext(which can be found within [Rehabman's USBInjectAll's project](https://github.com/RehabMan/OS-X-USB-Inject-All))

But where the real issues come in are when we look towards server boards and non-Z370 300 series motherboards. Server boards don't like to play nicely with macOS so users often opt for running a hypervisor in between to avoid issues with but it still is possible to run macOS natively if you're willing to put the effort in. Non-Z370 300 series motherboards have the issues where nvram, audio and onboard video out don't work correctly and require more work to function with onboard video sometimes not fixable even with manual connector patches through WhateverGreen. NVRAM can be solved with either EmuVariableUEFI-64.efi or with [OpenCorePkg](https://github.com/khronokernel/Getting-Started-With-OpenCore)(OC is still in early alpha so avoid unless you like pain). While there are workarounds for this platform, anytime you're not running native hardware means there's one more point of failure. Yes, others may have gotten their systems to run but keep in mind that the more complicated an EFI gets, the more places you'll need to examine when troubleshooting and the harder it is for users of the community to help you.

**Chipsets to avoid**
* C612 (generally seen in server boards)
* B360
* B365
* H310
* H370
* Q370
* Z390

**Brands to avoid**

* MSI(Weird Memory Layout that can break AptioMemoryFix requiring you to use the OSX variant which isn't as stable)
* AsRock(non-native USB controller)

# Storage

Storage is a section that can be quite confusing as there a lot of mixed reports regarding PCIe/NVMe based devices, many of these reports are based off old information from back when PCIe/NVMe drives were not natively supported like block size mattering or require kexts/.efi drivers. Well, High Sierra brought native support for these types of drives but certain ones still do not work and can cause instability if not removed/blocked out at an ACPI level. 

The other big issue surrounds all Samsung NVMe drives, specifically that they're known to slow down macOS, not play well with TRIM and even create instability at times. This is due to the Pheonix controller found on Samsung drives that macOS isn't too fond of, much preferring the Phison controller found in WD SN750's and Sabrent Rocket drives. The easiest way to see this is with boot up, most systems running Samsung drives will have extra long boot times and have their drives run hotter due to the software TRIM failing(hardware TRIM still should be enabled but no partiality). Also some older Intel drives and Kingston NVMe drives also experience these issues.

And while not an issue anymore, do note that all of Apple's PCIe drives are 4k sector-based so for best support only choose drives with such sectors.

**Note for laptop users**: Intel SSDs don't always play nicely with laptops and can cause issues, avoid when possible

**SSDs that aren't supported AT ALL**

* Samsung PM981 (Commonly found in OEM systems like laptops)
* Any eMMC based SSD(Commonly found in netbooks)

**SSDs to avoid**

Samsung:
* Samsung 960
* Samsung 960 Pro
* Samsung 950 Pro
* Samsung PM961
* Samsung PM951

Intel:
* Intel 530

Kingston:
* Kingston A1000

**Recommended SSDs**
* Samsung 970 Evo Plus (While not natively supported OOB, a [firmware update from Samsung](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/) will allow these drives to operate in macOS)
* Samsung 970 Evo
* Samsung 970 Pro

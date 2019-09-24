# Storage

Storage is a section that can be quite confusing as there a lot of mixed reports regarding PCIe/NVMe based devices, many of these reports are based off old information from back when PCIe/NVMe drives were not natively supported like block size mattering or require kexts/.efi drivers. Well, High Sierra brought native support for these types of drives but certain ones still do not work and can cause instability if not removed/blocked out at an ACPI level. These drives include the following:

**SSDs that aren't supported AT ALL**

* Samsung PM981 (Commonly found in OEM systems like laptops)
* Any eMMC based SSD(Commonly found in netbooks)

**SSDs that need extra attention**

* Samsung 970 Evo Plus (On early versions of this SSD, a [firmware update from Samsung](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/) is required to allow these drives to operate in macOS without issue)

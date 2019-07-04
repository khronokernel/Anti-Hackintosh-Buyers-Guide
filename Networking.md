This section is specifically for dedicated NICs, generally most networking is supported either natively, like with Aquantia, or has drivers provided Mieze([IntelMausiEthernet.kext](https://github.com/Mieze/IntelMausiEthernet), [AtherosE2200Ethernet.kext](https://github.com/Mieze/AtherosE2200Ethernet) and [RealtekRTL8111.kext ](https://github.com/Mieze/RTL8111_driver_for_OS_X)). The issues come in when you either involve onboard server NICs or dedicated hardware like Mellanox's MNPA19-XTR 10Gbe NIC. You need to be quite vigilante and see if either the manufactures or the Hackintosh community have developed drivers, or instead, you can take the safe route and grab a 10Gbe Aquantia AQtion AQC-107 NIC as these are shipped in the iMacPro1,1 so full native support. [SmallTree](https://www.small-tree.com/categories/10gb-ethernet-cards/) is the other popular option

**NICs cards to avoid**

* Intel Server NICs(including both 1Gbe and 10Gbe, there's work arounds for X520 and X540 NICs)
* HP Server NICs(including both 1Gbe and 10Gbe, generally rebranded Qlogic)
* Dell Server NICs(including both 1Gbe and 10Gbe, generally rebranded Broadcom or Intel)
* Mellanox NICs

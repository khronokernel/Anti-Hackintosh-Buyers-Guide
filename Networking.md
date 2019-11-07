This section is specifically for dedicated NICs, generally most networking is supported either natively, like with Aquantia, or has drivers provided Mieze([IntelMausiEthernet.kext](https://github.com/Mieze/IntelMausiEthernet), [AtherosE2200Ethernet.kext](https://github.com/Mieze/AtherosE2200Ethernet) and [RealtekRTL8111.kext ](https://github.com/Mieze/RTL8111_driver_for_OS_X)). 

Certain consumer NICs don't have support such as:
* Realtek L8200A(Only found in Asus boards)
* Realtek RTL8125(2.5Gbe, mostly found on higher end gaming boards)

Note: Newer Intel chipsets based off of I211-AT will need the [I211-AT SmallTree kext](https://cdn.discordapp.com/attachments/390417931659378688/556912824228773888/SmallTree-Intel-211-AT-PCIe-GBE.kext.zip)


The issues come in when you either involve onboard server NICs or dedicated hardware like Mellanox's MNPA19-XTR 10Gbe NIC. You need to be quite vigilante and see if either the manufactures or the Hackintosh community have developed drivers, or instead, you can take the safe route and grab a 10Gbe Aquantia AQtion AQC-107 NIC as these are shipped in the iMacPro1,1 so full native support. [SmallTree](https://www.small-tree.com/categories/10gb-ethernet-cards/) is the other popular option

**NICs cards to avoid**

* Intel Server NICs(including both 1Gbe and 10Gbe, [there's work arounds for X520 and X540 NICs](https://www.tonymacx86.com/threads/how-to-build-your-own-imac-pro-successful-build-extended-guide.229353/))
* HP Server NICs(including both 1Gbe and 10Gbe, generally rebranded Qlogic)
* Dell Server NICs(including both 1Gbe and 10Gbe, generally rebranded Broadcom or Intel)
* Mellanox NICs

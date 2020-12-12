**GENERAL**

Use this script:

```
#!/bin/bash
shopt -s nullglob
for g in /sys/kernel/iommu_groups/*; do
    echo "IOMMU Group ${g##*/}:"
    for d in $g/devices/*; do
        echo -e "\t$(lspci -nns ${d##*/})"
    done;
done;
```

Alternative:

lspci -nnk 

output in my case:

00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Root Complex [1022:1450]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7c02]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) I/O Memory Management Unit [1022:1451]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7c02]
00:01.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge [1022:1452]
00:01.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe GPP Bridge [1022:1453]
	Kernel driver in use: pcieport
00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge [1022:1452]
00:03.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge [1022:1452]
00:03.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe GPP Bridge [1022:1453]
	Kernel driver in use: pcieport
00:04.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge [1022:1452]
00:07.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge [1022:1452]
00:07.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B [1022:1454]
	Kernel driver in use: pcieport
00:08.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge [1022:1452]
00:08.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B [1022:1454]
	Kernel driver in use: pcieport
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:790b] (rev 59)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7c02]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c_piix4, sp5100_tco
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:790e] (rev 51)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7c02]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 0 [1022:1460]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 1 [1022:1461]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 2 [1022:1462]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 3 [1022:1463]
	Kernel driver in use: k10temp
	Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 4 [1022:1464]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 5 [1022:1465]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 6 [1022:1466]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 7 [1022:1467]
03:00.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset USB 3.1 XHCI Controller [1022:43d5] (rev 01)
	Subsystem: ASMedia Technology Inc. Device [1b21:1142]
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci
03:00.1 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset SATA Controller [1022:43c8] (rev 01)
	Subsystem: ASMedia Technology Inc. Device [1b21:1062]
	Kernel driver in use: ahci
03:00.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Bridge [1022:43c6] (rev 01)
	Kernel driver in use: pcieport
20:00.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port [1022:43c7] (rev 01)
	Kernel driver in use: pcieport
20:01.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port [1022:43c7] (rev 01)
	Kernel driver in use: pcieport
20:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port [1022:43c7] (rev 01)
	Kernel driver in use: pcieport
20:06.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port [1022:43c7] (rev 01)
	Kernel driver in use: pcieport
20:07.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port [1022:43c7] (rev 01)
	Kernel driver in use: pcieport
22:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7c02]
	Kernel driver in use: r8169
	Kernel modules: r8169
28:00.0 USB controller [0c03]: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller [1912:0014] (rev 03)
	Subsystem: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller [1912:0014]
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci
**29:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP102 [GeForce GTX 1080 Ti] [10de:1b06] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:6593]
	Kernel driver in use: nvidia
	Kernel modules: nouveau, nvidia_drm, nvidia
29:00.1 Audio device [0403]: NVIDIA Corporation GP102 HDMI Audio Controller [10de:10ef] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:6593]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel**
2a:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Zeppelin/Raven/Raven2 PCIe Dummy Function [1022:145a]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7c02]
2a:00.2 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Platform Security Processor [1022:1456]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7c02]
	Kernel driver in use: ccp
	Kernel modules: ccp
2a:00.3 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] Zeppelin USB 3.0 Host controller [1022:145f]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7c02]
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci
2b:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Zeppelin/Renoir PCIe Dummy Function [1022:1455]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7c02]
2b:00.2 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901] (rev 51)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7c02]
	Kernel driver in use: ahci
2b:00.3 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) HD Audio Controller [1022:1457]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:ec02]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel



**GENERAL**

Watch out for the IOMMU group  in my case group 29

lspci -nnk -d 10de:1b06
lspci -nnk -d 10de:10ef


29:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP102 [GeForce GTX 1080 Ti] [10de:1b06] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:6593]
	Kernel driver in use: nvidia
	Kernel modules: nouveau, nvidia_drm, nvidia
29:00.1 Audio device [0403]: NVIDIA Corporation GP102 HDMI Audio Controller [10de:10ef] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:6593]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel










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

output in my case:


`IOMMU Group 0:
        00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
IOMMU Group 1:
        00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
IOMMU Group 10:
        02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
IOMMU Group 2:
        00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
IOMMU Group 3:
        00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
IOMMU Group 4:
        00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
IOMMU Group 5:
        00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
IOMMU Group 6:
        00:1c.4 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 [8086:8c18] (rev d5)
IOMMU Group 7:
        00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
IOMMU Group 8:
        00:1f.0 ISA bridge [0601]: Intel Corporation B85 Express LPC Controller [8086:8c50] (rev 05)
        00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05)
        00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
IOMMU Group 9:
        01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP106 [GeForce GTX 1060 6GB] [10de:1c03] (rev a1)
        01:00.1 Audio device [0403]: NVIDIA Corporation GP106 High Definition Audio Controller [10de:10f1] (rev a1)`








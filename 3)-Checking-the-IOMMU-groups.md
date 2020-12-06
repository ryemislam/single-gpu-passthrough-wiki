sudo dmesg | grep -i -e DMAR -e IOMMU


Output can be this:

[    0.242020] iommu: Default domain type: Translated 
[    0.585240] pci 0000:00:00.2: AMD-Vi: IOMMU performance counters supported
[    0.585290] pci 0000:00:01.0: Adding to iommu group 0
[    0.585298] pci 0000:00:01.3: Adding to iommu group 1
[    0.585311] pci 0000:00:02.0: Adding to iommu group 2
[    0.585324] pci 0000:00:03.0: Adding to iommu group 3
[    0.585332] pci 0000:00:03.1: Adding to iommu group 4
[    0.585343] pci 0000:00:04.0: Adding to iommu group 5
[    0.585355] pci 0000:00:07.0: Adding to iommu group 6
[    0.585362] pci 0000:00:07.1: Adding to iommu group 7
[    0.585373] pci 0000:00:08.0: Adding to iommu group 8
[    0.585382] pci 0000:00:08.1: Adding to iommu group 9
[    0.585396] pci 0000:00:14.0: Adding to iommu group 10
[    0.585403] pci 0000:00:14.3: Adding to iommu group 10
[    0.585435] pci 0000:00:18.0: Adding to iommu group 11
[    0.585442] pci 0000:00:18.1: Adding to iommu group 11
[    0.585449] pci 0000:00:18.2: Adding to iommu group 11
[    0.585456] pci 0000:00:18.3: Adding to iommu group 11
[    0.585463] pci 0000:00:18.4: Adding to iommu group 11
[    0.585470] pci 0000:00:18.5: Adding to iommu group 11
[    0.585477] pci 0000:00:18.6: Adding to iommu group 11
[    0.585484] pci 0000:00:18.7: Adding to iommu group 11
[    0.585501] pci 0000:03:00.0: Adding to iommu group 12
[    0.585509] pci 0000:03:00.1: Adding to iommu group 12
[    0.585518] pci 0000:03:00.2: Adding to iommu group 12
[    0.585522] pci 0000:20:00.0: Adding to iommu group 12
[    0.585525] pci 0000:20:01.0: Adding to iommu group 12
[    0.585528] pci 0000:20:04.0: Adding to iommu group 12
[    0.585531] pci 0000:20:06.0: Adding to iommu group 12
[    0.585534] pci 0000:20:07.0: Adding to iommu group 12
[    0.585537] pci 0000:22:00.0: Adding to iommu group 12
[    0.585540] pci 0000:28:00.0: Adding to iommu group 12
**[    0.585555] pci 0000:29:00.0: Adding to iommu group 13
[    0.585564] pci 0000:29:00.1: Adding to iommu group 13**
[    0.585573] pci 0000:2a:00.0: Adding to iommu group 14
[    0.585582] pci 0000:2a:00.2: Adding to iommu group 15
[    0.585590] pci 0000:2a:00.3: Adding to iommu group 16
[    0.585599] pci 0000:2b:00.0: Adding to iommu group 17
[    0.585608] pci 0000:2b:00.2: Adding to iommu group 18
[    0.585616] pci 0000:2b:00.3: Adding to iommu group 19
[    0.589062] pci 0000:00:00.2: AMD-Vi: Found IOMMU cap 0x40
[    0.590420] perf/amd_iommu: Detected AMD IOMMU #0 (2 banks, 4 counters/bank).

Check for the right groups in my case group 13.

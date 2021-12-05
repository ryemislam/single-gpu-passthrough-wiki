
Optional only needed when you need a rom file.


<hostdev mode="subsystem" type="pci" managed="yes">
  <source>
    <address domain="0x0000" bus="0x29" slot="0x00" function="0x0"/>
  </source>
  <address type="pci" domain="0x0000" bus="0x06" slot="0x00" function="0x0"/>
</hostdev>


**FEDORA** (or other distro without apparmor like selinux)

![image](uploads/ec7bccb488dc1ef5c4ea16034e1d9055/image.png)

add this line 
`<rom file='/var/lib/libvirt/vbios/<romfile>.rom'/> `


**POPOS! / Ubuntu / Linux Mint / ARCH / OPENSUSE (or other apparmor distro)**

![2020-12-15_22-21](uploads/508daeed4e2ebcfae09b8b1f7f119877/2020-12-15_22-21.png)

add this line 
`<rom file="/usr/share/vgabios/<romfile>.rom"/> `


**GENERAL:**

Remove spice / qxl stuff in VM

add keyboard and mouse device or passtrough the complete usb device.




Download virtio (stable) drivers: 
https://docs.fedoraproject.org/en-US/quick-docs/creating-windows-virtual-machines-using-virtio-drivers/index.html

Download the latest windows 10 build iso.

![image](uploads/8dc75941114862dd1f8ea448569696ed/image.png)


**GENERAL:**

**IMPORTANT**
You have to start customize the vm before installation
choice win10 as vm name because of scripts.
Choice for Q35 chipset
Choice for **UEFI firmware**:

/usr/share/edk2/ovmf/OVMF_CODE.fd


**Popos!**

/usr/share/OVMF/OVMF_CODE_4M.fd

**Opensuse**

/usr/share/qemu/ovmf-x86_64.bin

![2020-06-13_14-31_1](uploads/1581b6dd65be8cb7ea01e8aa9b1f12ab/2020-06-13_14-31_1.png)

Choice the max Logical Host CPU's
Choice Topology

![2020-06-13_14-40](uploads/8b61113a13e524d1e007680e46a2dff0/2020-06-13_14-40.png)

Choice Memory 8GB or more

![2020-06-13_14-43](uploads/6531691d3ba60e44e86ca675cb018879/2020-06-13_14-43.png)

Choice Virtio 
Choice the option Cache mode writeback

![image](uploads/dc35b091e4fc5b0b333e72d86d310a1f/image.png)

Attach the 2 iso's of windows 10 and virtio to SATA CDROM

![2020-06-13_14-44](uploads/929e78368ad62ae07b3dd28aab334d50/2020-06-13_14-44.png)

Choice 'Virtual network 'default': NAT'
Choice virtio

**GENERAL:**


We do NOT attached the GPU and HDMI sound on this moment. 
Bootup the VM and install windows in de VM with virtio drivers. 


![Screenshot_win10-7](uploads/dfa4828fea018d3f441cc2566ab37fc0/Screenshot_win10-7.png)

Choice load driver 

![Screenshot_win10-9](uploads/ef14ba6add48683e5d43e81724cb8d4d/Screenshot_win10-9.png)

Choice the right folder on the mounted virtio ISO.

![Screenshot_win10-91](uploads/86c041a58d70d30d10543de56b23ff2d/Screenshot_win10-91.png)
![Screenshot_win10-92](uploads/9d1137d7749b470aba734baca9e268ac/Screenshot_win10-92.png)

The virtio drive is now visible.

Install windows like normal. 




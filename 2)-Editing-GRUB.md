Editing GRUB



**arch / manjaro / fedora / Ubuntu / Linux Mint / OpenSUSE**

sudo nano /etc/default/grub 

**popos!**

sudo nano /boot/efi/loader/entries/Pop_OS-current.conf  


![image](uploads/a827fb07cae2163c98f8fb132b262d78/image.png)



**ARCH LINUX:**

- intel_iommu=on for intel cpu's
- amd_iommu=on for amd cpu's



edit line:
GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on iommu=pt"

update grub
sudo grub-mkconfig -o /boot/grub/grub.cfg

**MANJARO**

edit line:
GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on iommu=pt quiet apparmor=1 security=apparmor udev.log_priority=3"

update grub
sudo update-grub

**FEDORA**

edit line:
GRUB_CMDLINE_LINUX="resume=/dev/mapper/fedora_localhost--live-swap rd.lvm.lv=fedora_localhost-live/root rd.lvm.lv=fedora_localhost-live/swap amd_iommu=on iommu=pt quiet"

update grub
sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg

**POPOS!**

edit line:
options root=UUID=211de945-3abe-4b4e-87f1-4ec1a062d9b6 ro quiet loglevel=0 systemd.show_status=false amd_iommu=on iommu=pt splash

update grub
sudo bootctl update

**Ubuntu / Linux Mint**

edit line
GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on iommu=pt video=efifb:off quiet splash"

update grub
sudo update-grub

**Opensuse**

edit line:
GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on iommu=pt splash=silent resume=/dev/disk/by-uuid/1652c07d-e2ba-4161-af2f-3e874eedfe1a mitigations=auto quiet"

update grub:
sudo grub2-mkconfig -o /boot/grub2/grub.cfg


**IMPORTANT:**

REBOOT














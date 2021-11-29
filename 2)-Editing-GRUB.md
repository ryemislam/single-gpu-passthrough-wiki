**ARCH / MANJARO / FEDORA / UBUNTU / LINUX MINT / OPENSUSE**

Editing GRUB

### Enable IOMMU

Set the parameter `intel_iommu=on` or `amd_iommu=on` respective to your system in grub config

Set the parameter `iommu=pt` in grub config for safety reasons

You can add this parameter `video=efifb:off` fixes issues that few people have with returning back to the host. (Mostly AMD users)

**EXAMPLE OF GRUB**

* sudo nano /etc/default/grub

![image](/risingprismtv/single-gpu-passthrough/-/wikis/uploads/a827fb07cae2163c98f8fb132b262d78/image.png)

**popos!**

* sudo nano /boot/efi/loader/entries/Pop_OS-current.conf

**ARCH LINUX:**

EDIT LINE: GRUB_CMDLINE_LINUX_DEFAULT="**_amd_iommu=on iommu=pt_**"

UPDATE GRUB:

* sudo grub-mkconfig -o /boot/grub/grub.cfg

**MANJARO**

EDIT LINE: GRUB_CMDLINE_LINUX_DEFAULT="**_amd_iommu=on iommu=pt_** quiet apparmor=1 security=apparmor udev.log_priority=3"

UPDATE GRUB:

* sudo update-grub

**FEDORA**

EDIT LINE: GRUB_CMDLINE_LINUX="resume=/dev/mapper/fedora_localhost--live-swap rd.lvm.lv=fedora_localhost-live/root rd.lvm.lv=fedora_localhost-live/swap **_amd_iommu=on iommu=pt_** quiet"

UPDATE GRUB:

* sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg

**POPOS!**

EDIT LINE: options root=UUID=211de945-3abe-4b4e-87f1-4ec1a062d9b6 ro quiet loglevel=0 systemd.show_status=false **_amd_iommu=on iommu=pt_** splash

UPDATE GRUB:

* sudo bootctl update

**Ubuntu / Linux Mint**

EDIT LINE: GRUB_CMDLINE_LINUX_DEFAULT="**_amd_iommu=on iommu=pt_** quiet splash"

UPDATE GRUB:

* sudo update-grub

**Opensuse**

EDIT LINE: GRUB_CMDLINE_LINUX_DEFAULT="**_amd_iommu=on iommu=pt_** splash=silent resume=/dev/disk/by-uuid/1652c07d-e2ba-4161-af2f-3e874eedfe1a mitigations=auto quiet"

UPDATE GRUB:

* sudo grub2-mkconfig -o /boot/grub2/grub.cfg

**IMPORTANT:**

REBOOT
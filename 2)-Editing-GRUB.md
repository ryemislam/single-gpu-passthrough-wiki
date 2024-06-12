## Enable IOMMU

Set the parameter respective to your system in the grub config:

| AMD CPU                                        | Intel CPU        |
|:----------------------------------------------:|:----------------:|
| Kernel auto-detects if IOMMU is enabled in BIOS | `intel_iommu=on` |

More info: [Arch Wiki Enabling IOMMU](https://wiki.archlinux.org/title/PCI_passthrough_via_OVMF#Enabling_IOMMU)

Mostly for AMD users, the parameter `video=efifb:off` can fix issues when returning back to the host, it is recommended that you add it.

<details> 
  <summary><strong>Example of an edited grub file</strong></summary>
  <img src="uploads/a827fb07cae2163c98f8fb132b262d78/image.png">
</details>

The default path, for distros that aren't listed below, is `/etc/default/grub`, to update it after you edited the file, run `sudo grub-mkconfig` or **search for your distro specific grub update command**

<details> 
  <summary><strong>Ubuntu, Linux Mint, or any debian based distro</strong></summary>

  Run <code>sudo nano /etc/default/grub</code>

  Edit the line that starts with <code>GRUB_CMDLINE_LINUX</code> so it ressembles something like this, keeping the previous parameters:

  <code>GRUB_CMDLINE_LINUX_DEFAULT="<strong>amd_iommu=on iommu=pt</strong> quiet splash"</code>

  Update grub with the command <code>sudo update-grub</code>
</details>

<details> 
  <summary><strong>Arch linux, and most Arch based distros</strong></summary>

  Run <code>sudo nano /etc/default/grub</code>

  Edit the line that starts with <code>GRUB_CMDLINE_LINUX_DEFAULT</code> so it ressembles something like this, keeping any previous parameters if there is any:

  <code>GRUB_CMDLINE_LINUX_DEFAULT="<strong>amd_iommu=on iommu=pt</strong>"</code>

  Update grub with the command <code>sudo grub-mkconfig -o /boot/grub2/grub.cfg</code>
</details>

<details> 
  <summary><strong>Fedora, and Fedora based distros</strong></summary>

  Run <code>sudo nano /etc/default/grub</code>

  Edit the line that starts with <code>GRUB_CMDLINE_LINUX</code> so it ressembles something like this, keeping the previous parameters:

  <code>GRUB_CMDLINE_LINUX="resume=/dev/mapper/fedora_localhost--live-swap rd.lvm.lv=fedora_localhost-live/root rd.lvm.lv=fedora_localhost-live/swap <strong>amd_iommu=on iommu=pt</strong> quiet"</code>

  <a href="https://fedoraproject.org/wiki/GRUB_2#Updating_the_GRUB_configuration_file">Update grub</a> with the command <code>sudo grub2-mkconfig -o /boot/grub2/grub.cfg</code> for Fedora 34 and up, <code>sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg</code> for Fedora 33 and lower
</details>

<details> 
  <summary><strong>Pop!_OS</strong></summary>

  Run <code>sudo nano /boot/efi/loader/entries/Pop_OS-current.conf</code>

  Edit the line that starts with <code>options</code> so it ressembles something like this, keeping the previous parameters: 
  
  <code>options root=UUID=211de945-3abe-4b4e-87f1-4ec1a062d9b6 ro quiet loglevel=0 systemd.show_status=false <strong>amd_iommu=on iommu=pt</strong> splash</code>
  
  Update grub with the command <code>sudo bootctl update</code>
</details>

<details> 
  <summary><strong>Manjaro</strong></summary>

  Run <code>sudo nano /etc/default/grub</code>

  Edit the line that starts with <code>GRUB_CMDLINE_LINUX_DEFAULT</code> so it ressembles something like this, keeping the previous parameters:

  <code>GRUB_CMDLINE_LINUX_DEFAULT="<strong>amd_iommu=on iommu=pt</strong> quiet apparmor=1 security=apparmor udev.log_priority=3"</code>

  Update grub with the command <code>sudo update-grub</code>
</details>

<details> 
  <summary><strong>OpenSuse</strong></summary>

  Run <code>sudo nano /etc/default/grub</code>

  Edit the line that starts with <code>GRUB_CMDLINE_LINUX_DEFAULT</code> so it ressembles something like this, keeping the previous parameters:

  <code>GRUB_CMDLINE_LINUX_DEFAULT="<strong>amd_iommu=on iommu=pt</strong> splash=silent resume=/dev/disk/by-uuid/1652c07d-e2ba-4161-af2f-3e874eedfe1a mitigations=auto quiet"</code>

  Update grub with the command <code>sudo grub2-mkconfig -o /boot/grub2/grub.cfg</code>
</details>

**IMPORTANT: REBOOT** your system to apply the new changes.
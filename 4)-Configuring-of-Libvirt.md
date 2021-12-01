**Configure libvirt**

Check out this webpage <https://fedoramagazine.org/full-virtualization-system-on-fedora-workstation-30/>

Installing the packages:

**ARCH LINUX / MANJARO**

* sudo pacman -S virt-manager qemu vde2 dnsmasq bridge-utils ovmf

**FEDORA**

* sudo dnf install @virtualization

**POPOS! / UBUNTU / Linux Mint**

* sudo apt install qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virt-manager ovmf

**Opensuse**

* sudo zypper in libvirt libvirt-client libvirt-daemon virt-manager virt-install virt-viewer qemu qemu-kvm qemu-ovmf-x86_64 qemu-tools

**This step is needed to use Virtual Machine Manager under user rights and adding logs**

**GENERAL**

**EDIT LIBVIRTD.CONF**

sudo nano /etc/libvirt/libvirtd.conf

uncomment the # off the following lines:

* unix_sock_group = "libvirt"


- unix_sock_rw_perms = "0770"

**IMPORTANT you need this for logs.**

Add this lines at the end of the file\
\
_log_filters="1:qemu"\
log_outputs="1:file:/var/log/libvirt/libvirtd.log"_

* sudo usermod -a -G libvirt $(whoami)
* sudo systemctl start libvirtd
* sudo systemctl enable libvirtd

**EDIT QEMU.CONF**

* sudo nano /etc/libvirt/qemu.conf

edit the following lines #user = "root" to user = "your username" #group = "root" to group = "your username"

* sudo systemctl restart libvirtd

**Note specific:** Linux Mint / Ubuntu / Popos!

sudo usermod -a -G kvm,libvirt $(whoami)
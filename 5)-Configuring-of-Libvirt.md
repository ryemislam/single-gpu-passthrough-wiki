**Configure libvirt**

Check out this webpage https://fedoramagazine.org/full-virtualization-system-on-fedora-workstation-30/


Installing the packages:

**ARCH LINUX / MANJARO**

sudo pacman -S virt-manager qemu vde2 ebtables dnsmasq bridge-utils openbsd-netcat ovmf

**FEDORA**

sudo dnf install @virtualization

**POPOS! / UBUNTU / Linux Mint**

sudo apt install qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virt-manager ovmf

**Opensuse**

sudo zypper in libvirt libvirt-client libvirt-daemon virt-manager virt-install virt-viewer qemu qemu-kvm qemu-ovmf-x86_64 qemu-tools


**This step is need to use Virtual Machine Manager under user rights and adding logs**


**GENERAL**

sudo nano /etc/libvirt/libvirtd.conf

edit the follow lines:
unix_sock_group = "libvirt"
unix_sock_rw_perms = "0770"


**IMPORTANT you need this for logs.**

Last lines:
log_filters="1:qemu"
log_outputs="1:file:/var/log/libvirt/libvirtd.log"


sudo usermod -a -G libvirt $(whoami)
sudo systemctl start libvirtd
sudo systemctl enable libvirtd



sudo nano /etc/libvirt/qemu.conf

edit the follow lines
#user = "root" naar user = "you're username"
#group = "root" naar group = "you're username"

sudo systemctl restart libvirtd



Note specific:
Linux Mint

sudo usermod -a  -G kvm "you're username"
sudo usermod -a  -G libvirtd "you're usernam"












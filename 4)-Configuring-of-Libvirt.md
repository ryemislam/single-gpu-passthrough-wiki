# Installing the packages


### <ins>ARCH LINUX / MANJARO</ins>
``` bash
sudo pacman -S virt-manager qemu vde2 ebtables iptables dnsmasq bridge-utils ovmf
```

### <ins>FEDORA</ins>
**Please note:** check out the link below if your using fedora. It will help you going forward.\
<https://fedoramagazine.org/full-virtualization-system-on-fedora-workstation-30/>
``` bash
sudo dnf install @virtualization
```

### <ins>POPOS! / UBUNTU / Linux Mint</ins>

``` bash
sudo apt install qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virt-manager ovmf
```

### <ins>Opensuse</ins>

``` bash
sudo zypper in libvirt libvirt-client libvirt-daemon virt-manager virt-install virt-viewer qemu qemu-kvm qemu-ovmf-x86_64 qemu-tools
```

**This step is needed to use Virtual Machine Manager under user rights and adding logs**

&nbsp;
&nbsp;

## GENERAL

### <ins>EDIT LIBVIRTD.CONF</ins>

Use your terminals editor `vim,nvim,nano` to edit this file.
``` bash
sudo nano /etc/libvirt/libvirtd.conf
```

&nbsp;

Uncomment the `#` off the following lines:

``` bash
unix_sock_group = "libvirt"
```
``` bash
unix_sock_rw_perms = "0770"
```
&nbsp;

**IMPORTANT:** You need this for detailed logs.

Add this lines at the end of the file

``` bash
log_filters="1:qemu"
log_outputs="1:file:/var/log/libvirt/libvirtd.log"
```

&nbsp;

Then run these commands in your terminal.\
This command assigns your user the libvirt group.
``` bash
sudo usermod -a -G libvirt $(whoami)
```
``` bash
sudo systemctl start libvirtd
```
``` bash
sudo systemctl enable libvirtd
```

&nbsp;

You can verify libvirt has been added to your users groups by using the following command.
```bash
sudo groups $(whoami)
```
It should return your current users groups like so.

`username libvirt` etc...

&nbsp;

### <ins>EDIT QEMU.CONF</ins>

``` bash
sudo nano /etc/libvirt/qemu.conf
```

&nbsp;

Edit the following lines.

``` bash
#user = "root" to user = "your username"
```
``` bash
#group = "root" to group = "your username"
```

&nbsp;

Then restart the libvirt demon with the following.

``` bash
sudo systemctl restart libvirtd
```

&nbsp;

**Note specific for use on:** Linux Mint / Ubuntu / Popos or other Debian based systems!

``` bash
sudo usermod -a -G kvm,libvirt $(whoami)
```

&nbsp;

You can verify libvirt and kvm has been added to your users groups by using the following command.
```bash
sudo groups $(whoami)
```
It should return your current users groups like so.

`username libvirt kvm` etc...

&nbsp;

### <ins>Enabling the virtual machine default network</ins>

**Important:** This will make your virsh internal network automaticly start when you start up your computer.

``` bash
sudo virsh net-autostart default
```

If you prefer not to have the virtual machine network not to automaticly start you will have to run this 
command ever time you start up your computer.

``` bash
sudo virsh net-start default
```
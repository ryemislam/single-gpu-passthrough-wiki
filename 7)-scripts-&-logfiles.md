We will now install the startup and teardown scripts for the VM, as well as the qemu hook. Everything will be automated thanks to the installation script available in the RisingPrism repo.

*Note for AMD users: If the RisingPrism scripts do not work, use the [akshaycodes scripts](https://gitlab.com/akshaycodes/vfio-script) instead.*

## Cloning the repo

The first step of the installation is to recoverer the repository containing the files. Go in the folder of your choice, and [clone the repository using git](https://git-scm.com/docs/git-clone
):

```
git clone https://gitlab.com/risingprismtv/single-gpu-passthrough.git
```

In the newly created `single-gpu-passthrough` folder, run the installation as root:

```
sudo chmod +x install_hooks.sh
sudo ./install_hooks.sh
```

Verify that the files are installed correctly. You should have files in the following location:
```
/etc/systemd/system/libvirt-nosleep@.service
/bin/vfio-startup.sh
/bin/vfio-teardown.sh
/etc/libvirt/hooks/qemu
```

## Location of Libvirtd's log files

If you followed step 1.2 in part 4), you should be able to find your logs in `/var/log/libvirt/` folder:
```
win10.log        => /var/log/libvirt/qemu
custom_hooks.log => /var/log/libvirt/
libvirtd.log     => /var/log/libvirt/
```

*Note for akshaycodes scripts users: `custom_hooks.log` is located in `/var/tmp/vfio-script.log` instead of the usual location*
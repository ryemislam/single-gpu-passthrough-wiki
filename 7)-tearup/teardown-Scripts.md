**GENERAL**

Study this url
https://gitlab.com/risingprismtv/single-gpu-passthrough

Download the files and unzip them.
Copy the hooks directory /etc/libvirt/hooks 

sudo cp -r hooks/ /etc/libvirt/

Run the script with ./install_hooks.sh with root rights

Check the scripts are in place.

/etc/systemd/system/libvirt-nosleep@.service
/bin/vfio-startup.sh
/bin/vfio-teardown.sh
/etc/libvirt/hooks/qemu

**NOTE:**

The place of the log files are

win10.log. You can find them in /var/log/libvirt/qemu
custom_hooks.log. You can find them in/var/log/libvirt
libvirtd.log You can find them in /var/log/libvirt/

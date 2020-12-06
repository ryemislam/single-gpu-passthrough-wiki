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
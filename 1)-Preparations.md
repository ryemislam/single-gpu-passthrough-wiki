# Warning

<strong  style="color: red">This wiki is intended for experienced linux users and NOT advisable for new linux users. It is recommended that you are familiar with these concepts of the linux system before starting:</strong>

- The commandline
- File and folder movement through commandline
- File and folder permissions and ownership
- File and folder structure of linux
- File editing from the commandline (nano, vim, or anything else)

**Your configuration and the one in this wiki can, and will be different.** Therefore,***take all the steps with a grain of salt and do not blindly copy-paste the values*** that are written in various configuration files showed.

**Last warning, your GPU has to support UEFI, and so does your system. Be sure to have installed your distro with UEFI, otherwise you might have to do some more workarounds that are not explained in this guide.**

<strong  style="color: red">For people coming for a Mac OS VM:</strong>
Please understand that running Mac OS is already very hard, so it is **even harder to pass a GPU**.
Please refer to [this link](https://elitemacx86.com/threads/nvidia-gpu-compatibility-list-for-macos.614/) for Nvidia GPUs compatibility.
Please refer to [this link](https://elitemacx86.com/threads/amd-gpu-compatibility-list-for-macos.617/) for AMD GPUs compatibility.
For all other hardware, check [this forum listing](https://elitemacx86.com/forums/hardware-compatibility.291/) for more info.

# Preparations:

- Check if your motherboard BIOS version is up to date. (This can help you have better IOMMU groups for the next steps)
- Check if your system is installed in **UEFI mode**, do not use CSM, as it will install your system as Legacy, which doesn't work with GPU passthrough. (Force UEFI in your BIOS when installing your distro)

## Bios settings

Depending on your machine CPU, you need to enable certain settings in your BIOS for your passthrough to succeed. **Enable** the settings listed in this table:

| AMD CPU    | Intel CPU   |
|:----------:|:-----------:|
| IOMMU      | VT-D        |
| NX mode    | VT-X        |
| SVM mode   |             |

Note for Intel : You may not have both options, in that case, just enable the one available to you.

**If you do not have any virtualisation settings,** like said before make sure your BIOS is up to date, and that your CPU and motherboard support virtualisation.
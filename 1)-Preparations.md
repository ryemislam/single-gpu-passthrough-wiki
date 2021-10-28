**Warning this wiki is intended for experienced linux users and NOT advisable for new linux users .**

**Warning your configuration and mine can be differ. Therefore, take all the steps with a grain of salt and do not blindly copy-paste the values that I am setting in various configuration files.**

**Warning your GPU has to support UEFI.**

**Preperations:**

* Update youre UEFI or BIOS to the latest version.
* Check in the UEFI/BIOS that you're videocard wil be detected

**AMD:**

* IOMMU = enabled
* NX mode = enabled
* SVM mode = enabled

**INTEL:** VT-D = Enabled VT-X = Enabled

**GENERAL**

* Install your distro
* Update your distro
* Update or install when needed the nvidia/AMD drivers
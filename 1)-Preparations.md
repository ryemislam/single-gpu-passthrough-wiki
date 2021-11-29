**Warning this wiki is intended for experienced linux users and NOT advisable for new linux users .**

**Warning your configuration and mine can be different. Therefore, take all the steps with a grain of salt and do not blindly copy-paste the values that I am setting in various configuration files.**

**Warning your GPU has to support UEFI.**

**Preperations:**

* Check if your motherboard BIOS version is recent. (this can help you with having better IOMMU groups)
* Check if your system is installed in UEFI mode. (CSM disabled in bios for AMD)

**AMD:**

* IOMMU = enabled
* NX mode = enabled
* SVM mode = enabled

**INTEL:** 

* VT-D = Enabled VT-X = Enabled

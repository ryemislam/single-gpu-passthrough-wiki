# Vision
The goal of this project is to automate the process of creating a 'passthrough' virtual machine, i.e. one where physical devices such as the gpu can be passed to the virtual machine.

Ideally if this project achieves its goals it should be as simple as the following to get a working gpu passthrough vm:

```
sudo dnf enable <some copr repo>
sudo dnf install gpu-passthrough
```
Followed by a reboot. Upon rebooting, you should be able to open virt manager and see that a VM has already been created for you and set up to pass your primary gpu. You simply need to provide the storage (create a virtual drive or use a physical one) as well as the install media (such as a Windows ISO).
For AMD CPUs, you can enable `topoext` to allow hyperthreading like this.

```
  <cpu mode='host-passthrough' check='none'>
    <topology sockets='1' dies='1' cores='12' threads='2'/>
    <feature policy='require' name='topoext'/>
  </cpu>
```

edit the following line with INTEL CPU:
For Intel CPUs, you can enable `SMEP` (Supervisor Mode Execution Protection) like this:
```
  <cpu mode='host-passthrough' check='none'>
    <topology sockets='1' dies='1' cores='12' threads='2'/>
    <feature policy='disable' name='smep'/>
  </cpu>
```

You can allow your KVM to take snapshots by replacing `pflash` by `rom` in the `<loader>` tag in your XML, like this: 
```XML
<loader readonly="yes" type="pflash">/usr/share/edk2-ovmf/x64/OVMF_CODE.fd</loader>
```
Replaced by rom:
```XML
<loader readonly="yes" type="rom">/usr/share/edk2-ovmf/x64/OVMF_CODE.fd</loader>
```
However, this option might not be useful, as control other virt-manager is taken away when the passthrough is enabled. Snapshots might still be possible using virsh, but aren't tested. It also might render your XML invalid, and prevent you from booting.

**ONLY WITH NVIDIA**

sudo su
export EDITOR=nano
virsh edit win10

  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
      <vendor_id state='on' value='any random value of 12 digets'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
    <vmport state='off'/>
    <ioapic driver='kvm'/>

**GENERAL**

edit the following line with AMD CPU:

```
  </features>
  <cpu mode='host-passthrough' check='none'>
    <topology sockets='1' cores='6' threads='2'/>
    <feature policy='require' name='topoext'/>
  </cpu>
```

edit the following line with INTEL CPU:  

```
</features>
  <cpu mode='host-passthrough' check='none'>
    <topology sockets='1' cores='6' threads='2'/>
    <feature policy='disable' name='smep'/>
  </cpu>
```

NOTE:

to make snapshots edit the following line to

`<loader readonly='yes' type='pflash'>/usr/share/edk2/ovmf/OVMF_CODE.fd</loader>`

replace it with:

` <loader readonly='yes' type='rom'>/usr/share/edk2-ovmf/x64/OVMF_CODE.fd</loader>`



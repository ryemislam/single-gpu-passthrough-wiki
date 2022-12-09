For NVidia GPUs older than the GTX 1000 series (included), it might be necessary to add these parameters to your VM XML. Go in the `<features>` section of your XML, and add the following lines:
```XML
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
      <vendor_id state='on' value='123456789123'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
    <vmport state='off'/>
    <ioapic driver='kvm'/>
```

For mobile cards, it is necessary to emulate a battery, and to pass the vendor ID of your card.
Change the first line of your XML to this:
```XML
<domain xmlns:qemu="http://libvirt.org/schemas/domain/qemu/1.0" type="kvm">
```
And, at the bottom of your XMl, before `</domain>`, add this block:
```XML
</qemu:commandline>
  <qemu:override>
    <qemu:device alias='hostdev0'>
      <qemu:frontend>
        <qemu:property name='x-pci-sub-vendor-id' type='unsigned' value='4136'/>
        <qemu:property name='x-pci-sub-device-id' type='unsigned' value='1909'/>
      </qemu:frontend>
    </qemu:device>
  </qemu:override>
</domain>
```
For more information, please refer to [this forum](https://forum.garudalinux.org/t/guide-gpu-passthrough-with-dual-graphics-laptop-using-optimus-manager/16420), [the Arch Wiki](https://wiki.archlinux.org/title/PCI_passthrough_via_OVMF#%22Error_43:_Driver_failed_to_load%22_with_mobile_(Optimus/max-q)_nvidia_GPUs) and [this message on our discord server](
https://discord.com/channels/696488545619279882/761752489246457857/1017172550498926633).
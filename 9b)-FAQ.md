# Frequently Asked Questions
*and other troubleshooting suggestions*

## General troubleshooting
<details>
  <summary>My custom systemd service dies when starting my VM!</summary>
<strong>SOLUTION:</strong><br>
Under the<code>[Unit]</code> section of your service, add<code>IgnoreOnIsolate=yes</code>
</details>

<details>
  <summary>
I get a blackscreen/console when I start my VM, and my libvirtd logs say&nbsp;<code>unsupported configuration: pci backend driver 'default' is not supported</code></summary>
<strong>SOLUTION:</strong> Remove your NIC like virtio and passthrough your own network card like you can find in your IOMMU groups in step 3 of our guide.
</details>

## Guest system related troubleshooting and tips

<details>
  <summary>I want to hide my KVM from anti-cheats and the like</summary>
  <strong>RisingPrismTV and the RisingPrism discord staff will not take responsibility for any game account or damage done to your VM. If you attempt these steps you, you understand the risk involved. We will not provide support.</strong>

  A good point to start KVM hiding is ~~watching&nbsp;<a href='https://youtu.be/L1JCCdo1bG4'>Mutah's video</a> on the subject~~, as he goes in details on how to do so (UPDATE: The methods in the video are outdated, but we're keeping it since it's still a good resource)

  Another step you can take (especially for EAC now detecting VMs) is adding&nbsp;<code>&lt;smbios mode="host"/></code> to the <code>&lt;os></code> section of your KVM XML.
  
  Disabling HyperV is one way to hide your KVM,&nbsp;<a href='https://www.reddit.com/r/VFIO/comments/cpf96e/comment/ewrksdr/'>here is an example</a> of an HyperV configuration:
  <pre>
  &lt;acpi/>
  &lt;apic/>
  &lt;hyperv mode="custom">
    &lt;relaxed state="on"/>
    &lt;vapic state="on"/>
    &lt;spinlocks state="on" retries="8191"/>
    &lt;vpindex state="off"/>
    &lt;runtime state="off"/>
    &lt;synic state="off"/>
    &lt;stimer state="off"/>
    &lt;reset state="off"/>
    &lt;vendor_id state="on" value="randomid"/>
    &lt;frequencies state="off"/>
  &lt;/hyperv></pre>
  You can also checkout the documentation of VRChat about this: [https://docs.vrchat.com/docs/using-vrchat-in-a-virtual-machine](https://docs.vrchat.com/docs/using-vrchat-in-a-virtual-machine)
</details>
<details>
  <summary>My VM is having some slowdowns, what can I do to mitigate this?</summary>
  Note the keyword<strong>mitigate</strong> here, as these tips might not completely work for you. Take these with a grain of salt.
  <br>
  <br>
  CPU Pinning can help you improve performance a bit, but it will not bring amazing improvements.&nbsp;<a href='https://youtu.be/Pb2upx53fUM?t=150'>This video at 2:30</a> shows how to assign CPU cores statically to your KVM, the start of the video goes in the details of CPU pinning. Take the time to study it and watch in its entirety, then edit your XML accordingly.
  Here is the XML for an 8 core CPU for example:
  <pre>
  &lt;cputune>
    &lt;vcpupin vcpu='0' cpuset='0'/>
    &lt;vcpupin vcpu='1' cpuset='1'/>
    &lt;vcpupin vcpu='2' cpuset='2'/>
    &lt;vcpupin vcpu='3' cpuset='3'/>
    &lt;vcpupin vcpu='4' cpuset='4'/>
    &lt;vcpupin vcpu='5' cpuset='5'/>
    &lt;vcpupin vcpu='6' cpuset='6'/>
    &lt;vcpupin vcpu='7' cpuset='7'/>
  &lt;/cputune></pre>
  <br>
  Huge pages can be enabled to improve performance a little too (mostly to reduce stuttering due to ram assignment). You can follow<a href='https://access.redhat.com/solutions/36741'>this page from redhat</a>,<a href='https://help.ubuntu.com/community/KVM%20-%20Using%20Hugepages'>this page from Ubuntu to enable it</a> and<a href='https://wiki.archlinux.org/title/PCI_passthrough_via_OVMF#Huge_memory_pages'>this page</a> from the Arch Wiki (which I recommend following to enable huge pages), however these page do not show how to enable it on systemd. As a complement for systemd, to enable it, you need to create a unit mount file in<code>/etc/systemd/system/</code> named&nbsp;<code>dev-hugepages.mount</code>, based on<a href='https://github.com/systemd/systemd/blob/main/units/dev-hugepages.mount'>this unit</a> taken from the systemd github repo.
  <br>
  <br>
  memballoon can also be a source of slowdowns on your VM, to disable it, search for a<code>&lt;memballoon model="XXXX"/></code> line, and set it to<code>&lt;memballoon model="none"/></code>
  <br>
  <br>
  You can check out more optimizations<a href='https://leduccc.medium.com/improving-the-performance-of-a-windows-10-guest-on-qemu-a5b3f54d9cf5'>here</a>, although do note that some tips shared in this article are already either applied in the previous guide, or discussed right here (mainly 2.1, 2.2 and 4.1).
</details>
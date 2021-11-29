**Lot of people has reported:** unsupported configuration: pci backend driver 'default' is not supported

**Solution:** Remove your NIC like virtio and passthrough your own network card like you can find in your IOMMU groups.
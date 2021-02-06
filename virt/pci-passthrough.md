# pci passthrough

PCI passthrough with qemu/kvm:

Permanent/early boot configuration:
* activate iommu/amd-vi in the bios
* boot linux with iommu support (if necessary) (grub)
  * `GRUB_CMDLINE_LINUX_DEFAULT="... amd_iommu=on iommu=pt"`
* (check iommu support and iommu groups)
* vfio-pci
  * bind devices with device id to vfio-pci driver on boot (grub)
    * `GRUB_CMDLINE_LINUX_DEFAULT="... vfio-pci.ids=1234:0abc,1234:1def"`
  * load vfio-pci driver module in `mkinitcpio.conf` before other drivers in
    ramdisk
    * `MODULES=(... vfio_pci vfio vfio_iommu_type1 vfio_virqfd ...)`
* qemu
  * use devices with pci id using `"-device vfio-pci,host=01:00.0"` in vm


IOMMU groups listing script:
```bash
#!/bin/bash
shopt -s nullglob
for g in /sys/kernel/iommu_groups/*; do
    echo "IOMMU Group ${g##*/}:"
    for d in $g/devices/*; do
        echo -e "\t$(lspci -nns ${d##*/})"
    done;
done;
```

Links:
* <https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF>
* <https://lettieri.iet.unipi.it/virtualization/2017/vn09.pdf>
* <https://turlucode.com/qemu-kvm-on-arch-linux-guide/#Step_5_Configurevfio-pci>

* <https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_administration_guide/sect-attch-nic-physdev>
* <https://serverfault.com/questions/446658/assign-individual-nic-to-kvm-guest>
* <https://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM>
* <https://www.linux-kvm.org/page/10G_NIC_performance:_VFIO_vs_virtio>

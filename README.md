# Build Your First NixOS Hypervisor Workstation
It is the same workstation I am using now.

### Warning!!! Check whether your GPU supports virtualization before start! Or you might get VMs without GPU!

# My set

### Hardware
- MiniPC: [`MINISFORUM M1 Pro-285H`](https://www.minisforum.com/products/minisforum-m1-pro-285h-mini-pc)
- CPU: `Intel Core Ultra 9 285H, 16 Cores`
- GPU: [`Intel Arc 140T`](https://www.intel.com/content/www/us/en/products/sku/241747/intel-core-ultra-9-processor-285h-24m-cache-up-to-5-40-ghz/specifications.html)
- RAM: `96GB`
- Disk: `4T`

### Software
- NixOS
- [`strongtz/i915-sriov-dkms`](https://github.com/strongtz/i915-sriov-dkms)

# Process

#### 1. Go to [NixOS website](https://nixos.org/) to download the iso file.

#### 2. Install

#### 3. Set configuration of your computer
  - set up the download application
  - set up vm envirnment

#### 4. Open `virt-manager`

#### 5. Create your first Windows vm(for me, win11)
  - download win11 iso
  - follow vm instruction to create
    - vCPU:`8`, topology: `1 sockets, 8 cores, 1 threads`
    - disk: if you want disk `D:/`, create two, and I recommend not to allocate too much (128G for each is enough, you can add more if you want later)
  - download [VirtIO Windows driver ISO](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso) and install it
  - add `TPM` and enable it in your hypervisor configuration (Only for win11 requirement)
  - change your disk from `SATA` to `VirtIO` (or your win will be sloooow)

#### 6. Create your first Linux vm(for me, Ubuntu26.04)
  - download ubuntu iso
  - Install 
  > yes, way easier than win XD

#### 7. Cut your GPU into 8 pieces (the coolest part)
  - set the configuration, and find out your GPU driver (`i915` or `xe`)
  - test if your GPU can be cut: 
  ```bash
  # Cheers if it is greater than zero. Mine is 7
  cat /sys/devices/pci0000:00/0000:00:02.0/sriov_totalvfs
  # or /sys/bus/pci/devices/0000:00:02.0/sriov_totalvfs if the path doesn't work
  ```
  - clone [`strongtz/i915-sriov-dkms`](https://github.com/strongtz/i915-sriov-dkms), and follow the instruction they give, and you will get many GPUs

#### 8. Allocate your GPUs to all your vm, now enjoy your Kingdom(or Queendom)!

# Advanced Option

- Allocate a shared disk for all VMs
- Use `Remmina` to control your running VMs
- Make your old laptop a vm in your new computer
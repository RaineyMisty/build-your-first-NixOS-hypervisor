# Build Your First NixOS Hypervisor Workstation
It is the same workstation I am using now.

### Warning!!! search for your GPU to find out whether it can be virtulized or not! or you might get vm without GPU!

# My set

### Hardware
- MiniPC: `Minisforum M1 Pro 285H`
- CPU: `i9, 16core`
- GPU: `Arc 140/130`
- Ram: `96GB`
- Disk: `4T`

### Software
- nixos
- strongtz

# Process

#### 1. Go to [NixOS website](http://nixos.com) to download the iso file.

#### 2. Install

#### 3. Set configuration of your computer
  - set the download application
  - set vm envirnment

#### 4. open virt-manager(there must be something else, but I can't remember right now)

#### 5. create your first Windows vm(for me, win11)
  - download win11 iso
  - follow vm instruction to create
    - vCPU:8, topology: 1sockets, 8cores, 1threads
    - disk: if you want disk `D:/`, create 2, and I recommand not allocate too much(128G for each is enough)
  - download the tool(I forget the name, whatever, you will find it easyly on Google)
  - Add `TPM`, set it in your hypervisor configuration. This step is only for win11 requirement.
  - change your disk from `SATA` to `VirtIO` (or your win will be sloooow)

#### 6. create your first Linux vm(for me, Ubuntu26.04)
  - download ubuntu iso
  - install(yes, way more easy than win XD)

#### 7. cut your GPT into 8 pieces(most cool part)
  - set the configuration, finding out your GPU mod(i915 or xe)
  - test if your GPU can be cut: 
  ```
  (some command)
  ```
  - clone strongtz, and follow the instruction they give, and you will get many GPUs

#### 8. Allocate your GPUs to all your vm, now enjoy your Kingdom(or Queendom)!

# Advanced Option

- Allocate a sharing disk for all vm
- Use `Remmina` to control your running vm
- Make your old laptop a vm in your new computer
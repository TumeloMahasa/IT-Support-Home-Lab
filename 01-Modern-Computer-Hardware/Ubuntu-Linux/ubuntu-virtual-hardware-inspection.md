# Lab B: Ubuntu Virtual Hardware Inspection

## 1. Objective

To inspect the CPU, memory, virtual storage devices, and root filesystem visible to the Ubuntu virtual machine using Linux terminal commands.

## 2. Environment

- **Host computer:** MacBook Air (M1, 2020)
- **Virtualisation software:** UTM
- **Virtual machine:** Ubuntu-IT-Lab
- **Guest operating system:** Ubuntu Linux
- **Architecture reported by Ubuntu:** aarch64 (64-bit ARM)

## 3. Tools Used

| Command | Purpose |
|---|---|
| `lscpu` | Displays CPU architecture and processor information visible to Ubuntu |
| `free -h` | Displays memory and swap usage in human-readable units |
| `lsblk` | Lists block devices, disks, and partitions |
| `df -h /` | Displays space usage for the filesystem mounted at the root directory `/` |

## 4. Procedure and Results

### 4.1 CPU Inspection — `lscpu`

**Key results:**

- Architecture: `aarch64`
- CPU operating modes: `64-bit`
- Byte order: Little Endian
- CPUs visible to Ubuntu: `4`
- Online CPUs: `0–3`
- Threads per core: `1`
- Cores per socket: `4`
- Sockets: `1`
- NUMA nodes: `1`

**Observations and interpretation:**

Ubuntu reports a 64-bit ARM architecture and four CPUs available to the virtual machine. These are the processor resources exposed to the guest operating system; they do not represent the total physical CPU cores in the MacBook Air.

The physical Mac has an Apple M1 chip with eight CPU cores. The difference illustrates how a virtual machine can be allocated a subset of the host computer's resources.

### 4.2 Memory Inspection — `free -h`

**Results:**

| Memory metric | Reported value |
|---|---:|
| Total memory | 3.3 GiB |
| Used memory | 2.2 GiB |
| Free memory | 152 MiB |
| Shared memory | 55 MiB |
| Buff/cache | 1.2 GiB |
| Available memory | 1.1 GiB |
| Total swap | 3.8 GiB |
| Swap used | 616 KiB |
| Swap free | 3.8 GiB |

**Observations and interpretation:**

Ubuntu reports approximately 3.3 GiB of memory available to the virtual machine. This is less than the Mac's physical 8 GB of unified memory because the guest operating system sees the memory allocated to it, not all the host's memory.

The `available` figure is especially useful when assessing memory pressure. Linux uses some memory for caches and buffers, which can be reclaimed when needed. Therefore, the low `free` figure alone does not mean the system is running out of memory.

Swap usage was minimal at the time of inspection.

### 4.3 Block Device and Partition Inspection — `lsblk`

**Key results:**

| Device | Size | Type | Mount point |
|---|---:|---|---|
| `/dev/vda` | 32 GB | Disk | — |
| `/dev/vda1` | 1 GB | Partition | `/boot/efi` |
| `/dev/vda2` | 30.9 GB | Partition | `/` |
| `/dev/sr0` | 1024 MB | ROM device | — |

Ubuntu also displayed multiple `loop` devices associated with Snap packages.

**Observations and interpretation:**

The virtual machine sees a 32 GB virtual disk named `/dev/vda`. It contains an EFI partition used for booting and a larger partition mounted as the root filesystem.

The `loop` devices are normal in Ubuntu systems that use Snap packages. Their presence is not, by itself, evidence of a disk problem.

The device sizes shown by `lsblk` describe the virtual storage presented to Ubuntu, not the Mac's physical 256 GB SSD.

### 4.4 Root Filesystem Capacity and Usage — `df -h /`

**Command:**

`df -h /`

**Results:**

| Metric | Reported value |
|---|---:|
| Filesystem | `/dev/vda2` |
| Size | 31 GB |
| Used | 12 GB |
| Available | 18 GB |
| Usage | 41% |
| Mount point | `/` |

**Observations and interpretation:**

The root filesystem is mounted on `/dev/vda2`. It has approximately 31 GB of usable filesystem capacity, of which 12 GB is used and 18 GB is available. The reported usage is 41%.

This indicates that, at the time of inspection, the root filesystem had substantial space available. The values are rounded by the `-h` option, so the displayed figures may not add up exactly.

The difference between the 32 GB virtual disk reported by `lsblk` and the 31 GB filesystem size reported by `df -h /` is normal. Partitioning, filesystem metadata, reserved space, and human-readable rounding can account for differences.

## 5. Overall Findings

The four commands provide complementary information about the resources visible to the Ubuntu virtual machine:

- **CPU:** Ubuntu sees four virtual CPUs on a 64-bit ARM architecture.
- **Memory:** Ubuntu reports 3.3 GiB of total memory and 1.1 GiB available at the time of inspection.
- **Virtual disk:** Ubuntu sees a 32 GB virtual disk with an EFI partition and a root partition.
- **Filesystem:** The root filesystem reports 41% usage, with approximately 18 GB available.

These results describe the virtual machine's current resource view and usage. They should not be interpreted as a complete measurement of the Mac's physical hardware or overall performance.

## 6. Troubleshooting Application

These commands can help establish a baseline when investigating common Linux issues:

- `lscpu` helps identify the processor architecture and CPUs visible to the operating system.
- `free -h` helps investigate memory pressure.
- `lsblk` helps identify disks and partitions.
- `df -h /` helps investigate low disk space on the root filesystem.

Together, these commands provide evidence that can guide further troubleshooting instead of relying on assumptions.

## 7. What I Learned

I learned how to inspect CPU information, memory usage, virtual storage devices, and filesystem capacity using Linux terminal commands.

I also learned that related commands can report different but complementary information. For example, `lsblk` identifies the virtual disk and partitions, while `df -h /` reports filesystem capacity and usage.

I learned to distinguish between physical host resources and the resources exposed to a virtual machine.

## 8. Evidence

Evidence to include in the portfolio:

- Screenshot of `lscpu` showing the architecture and CPU count.
- Screenshot of `free -h` showing memory and swap figures.
- Screenshot of `lsblk` showing the virtual disk and partitions.
- Screenshot of `df -h /` showing root filesystem capacity and usage.


## 9. Reflection

This lab strengthened my understanding of how an operating system reports its available resources and how to use terminal commands to collect evidence during troubleshooting.

## 10. Lab Status

**Status:** Completed

**Date completed:** [15/10/2026]

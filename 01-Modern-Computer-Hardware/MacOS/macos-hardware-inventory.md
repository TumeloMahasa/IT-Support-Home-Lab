# Lab A: Mac Hardware Inventory

## 1. Objective

To inspect the hardware specifications of a physical computer using macOS System Information and identify the roles of the CPU, memory, and storage in a computer system.

## 2. Environment

- **Computer:** MacBook Air (2020)
- **Model identifier:** MacBookAir10,1
- **Processor:** Apple M1
- **Installed memory:** 8 GB
- **Storage:** 256 GB
- **Operating system:** macOS

## 3. Tools Used

**macOS System Information**

This built-in macOS utility provides information about the computer's hardware, firmware, memory, and connected devices.

## 4. Procedure

1. Opened macOS System Information.
2. Viewed the Hardware Overview section.
3. Identified the computer model, chip, processor core configuration, and installed memory.
4. Recorded the storage capacity separately because it was not displayed in the main Hardware Overview.
5. Excluded serial numbers and unique device identifiers from the portfolio notes.

## 5. Results and Observations

| Hardware detail | Observed result |
|---|---|
| Model name | MacBook Air |
| Model identifier | MacBookAir10,1 |
| Chip | Apple M1 |
| Total CPU cores | 8 |
| Performance cores | 4 |
| Efficiency cores | 4 |
| Installed memory | 8 GB |
| Storage capacity | 256 GB |

**Observation:** The MacBook Air uses an Apple M1 chip with eight CPU cores divided into four performance cores and four efficiency cores. The system has 8 GB of memory and 256 GB of storage.

The processor and memory information were obtained from Hardware Overview. The storage capacity was recorded separately rather than assumed to be visible on that screen.

## 6. Technical Interpretation

- **CPU and chip:** The Apple M1 is a system-on-a-chip (SoC) that integrates the CPU and other computing components into one chip package.
- **CPU cores:** The four performance cores are designed for demanding workloads, while the four efficiency cores are designed to handle suitable workloads with lower energy consumption.
- **Memory:** The system has 8 GB of unified memory shared by the CPU and other components. It supports active applications, instructions, and working data.
- **Storage:** The 256 GB storage capacity represents the computer's long-term storage. It holds the operating system, applications, and personal files. Actual available space will be lower because some storage is occupied by macOS and other data.
- **Hardware identification:** System Information provides a convenient way for an IT support technician to identify a computer's specifications before investigating compatibility, performance, or hardware-related issues.

## 7. Troubleshooting Application

If a user reports that their Mac is running slowly, I would first gather information about the symptoms and when they occur. I would then inspect resource usage, including memory pressure and CPU activity, and check available storage space.

I would use the findings to narrow down potential causes before recommending a solution. The hardware specifications alone would not prove that any particular component was responsible for the slowdown.

## 8. What I Learned

1. How to access hardware information using a built-in macOS utility.
2. How to identify the processor, CPU core configuration, memory, and storage capacity.
3. The difference between short-term working memory and long-term storage.
4. Why collecting system information is a useful first step in IT troubleshooting.
5. Why technical documentation should include verified results and exclude unnecessary sensitive identifiers.

## 9. Evidence

- Hardware Overview: processor, core configuration, and memory.
- Storage information: capacity verified separately.
- Screenshots: stored in the lab's `screenshots` folder, with sensitive identifiers excluded.

## 10. Reflection

This exercise helped me practise gathering hardware information from a real computer and documenting verified specifications. It also reinforced the importance of protecting device identifiers and distinguishing observed results from assumptions.

**Lab status:** Completed.

**Date completed:** [15/10/2026]

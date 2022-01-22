# https://mobile-swam.github.io
The official home page for mobile-aware SWAM (Revisiting Swap & OOMK for New Challenge on Mobile Devices)

![SWAM, the SWAM mascot](/img/mobile-swam-logo3.png)  


## Introduction
Recently, to mitigate memory shortage problem of applications in mobile devices, swapping mechanism has been introduced, which can preserve the state of the swapped-out processes. However, frequent swap operations cause very similar effect to thrashing in paging systems, which worsens application responsiveness. Meanwhile, as the size of applications grew, the RAM capacity of mobile devices was increased 16-fold from 512 MB to 8 GB. This change again created an environment where applications consuming larger memory capacity can be developed and more applications can be run. Consequently, modern mobile devices need much larger physical memory capacity as a response to the growing memory competition among the applications. However, even though the physical memory capacity increases, the forced termination of processes due to OOMK operation occurs frequently because more applications use a large memory space indiscriminately, which degrades the application performance significantly.

To solve these problems, this paper proposes the SWAM, a new integrated memory management technique that complements the shortcomings of both the swapping and killing mechanism in mobile devices. SWAM consists of (1) On-Demand Swap that dynamically manages the swap space, (2) OOM Cleaner that preserves the process state by removing the shared object pages instead of killing the processes themselves, and (3) EOOM Killer that delays high-initialization-cost applications from being victim processes. Experimental results demonstrate that SWAM significantly reduces the number of applications killed by OOMK (18x lower), and improves application launch time (41% faster) and response time (48% faster), compared to the conventional schemes.


## Getting Started
* https://github.com/mobile-swam/mobile-swam
* https://github.com/mobile-swam/third-party

![SWAM, make menuconfig](/img/make-menuconfig-swam.png)


## Demo

* Before SWAM:

[![Before SWAM](img/demo-before.jpg)](https://youtu.be/stYu2EhvBFk)

* After SWAM:

[![After SWAM](img/demo-after.jpg)](https://youtu.be/JvZp1Kymsl8)


## Related work
We summarize the main contribution, as well as the strong and weak elements, from the important 50 publications published between 1999 and 2021.
* For more details, please refer to [Here](https://github.com/mobile-swam/mobile-swam.github.io/wiki/Related-works)

![50 papers between 1999 and 2021](/img/related-work-50-papers.png)

Between 1999 and 2021, this graph depicts the trend of research articles on protecting free memory. By visualizing the statistics as a graph, it is clear that while HDDs are being replaced by SSDs and storage IO such as eMMC/eUFS/NVRAM is developed, research articles on implementing SWAP in mobile devices are progressively increasing, with 2013 as the starting point. have. As can be observed, SWAP is a critical keyword for ensuring consistent and predictable user responsiveness and app launch speed in the mobile device environment when memory pressure is achieved. While OOM is a strategy for securing free memory without the user's permission, SWAP uses a temporary storage device to secure free memory without killing a process without the user's permission. SWAP, on the other hand, has structural issues with IO thrashing and NAND longevity. As a result, SWAP studies are critical for resolving these difficulties in mobile devices.

## Discussion Channel
* https://gather.town/app/AwPmQH37E46wxaN2/SWAM

![GatherTodwn](img/gather-town-swam.png)


## How to Contribute
* Please refer to [How to contribute](doc/contributing.md).


## Teminology
* SWAM: Swap + OOMK
* OOM: Out-of-Memory
* OOMK: OOM Killer
* LMK: Low Memory Killer in kernel-space
* LMKD: LMK Daemon in user-space
* Segfault: Segmentaiton Fault
* swap-out: A procedure that Kswapd try to move  anonymous pages from a memory to a swap device
* swap-clean: A procedure that try to remove a anomymous page of a so-page types

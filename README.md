# https://mobile-swam.github.io
The official home page for mobile-aware SWAM

## Introduction
Recently, to mitigate memory shortage problem of applications in mobile devices, swapping mechanism has been introduced, which can preserve the state of the swapped-out processes. However, frequent swap operations cause very similar effect to thrashing in paging systems, which worsens application responsiveness. Meanwhile, as the size of applications grew, the RAM capacity of mobile devices was increased 16-fold from 512 MB to 8 GB. This change again created an environment where applications consuming larger memory capacity can be developed and more applications can be run. Consequently, modern mobile devices need much larger physical memory capacity as a response to the growing memory competition among the applications. However, even though the physical memory capacity increases, the forced termination of processes due to OOMK operation occurs frequently because more applications use a large memory space indiscriminately, which degrades the application performance significantly.

To solve these problems, this paper proposes the SWAM, a new integrated memory management technique that complements the shortcomings of both the swapping and killing mechanism in mobile devices. SWAM consists of (1) On-Demand Swap that dynamically manages the swap space, (2) OOM Cleaner that preserves the process state by removing the shared object pages instead of killing the processes themselves, and (3) EOOM Killer that delays high-initialization-cost applications from being victim processes. Experimental results demonstrate that SWAM significantly reduces the number of applications killed by OOMK (18x lower), and improves application launch time (41% faster) and response time (48% faster), compared to the conventional schemes.


## Getting Started

* https://github.com/mobile-swam/mobile-swam
* https://github.com/mobile-swam/third-party

![SWAM, make menuconfig](/img/make-menuconfig-swam.png)


## Demo
![Coming soon](img/notavailable.png)


## Discussion Channel
* https://gather.town/app/AwPmQH37E46wxaN2/SWAM

![Coming soon](img/gather-town-swam.png)


## How to Contribute
![Coming soon](img/wip.png)


## Teminology
* SWAM: Swap + OOMK
* OOM: Out-of-Memory
* OOMK: OOM Killer
* LMK: Low Memory Killer in kernel-space
* LMKD: LMK Daemon in user-space
* Segfault: Segmentaiton Fault
* swap-out: A procedure that Kswapd try to move  anonymous pages from a memory to a swap device
* swap-clean: A procedure that try to remove a anomymous page of a so-page types

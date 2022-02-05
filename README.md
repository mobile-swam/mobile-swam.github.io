[![GitHub license](https://dmlc.github.io/img/apache2.svg)](LICENSE) 
![Gitter](https://img.shields.io/gitter/room/mobile-swam/mobile-swam.github.io) ![GitHub repo size](https://img.shields.io/github/repo-size/mobile-swam/mobile-swam.github.io) ![GitHub issues](https://img.shields.io/github/issues/mobile-swam/mobile-swam.github.io) ![GitHub pull requests](https://img.shields.io/github/issues-pr/mobile-swam/mobile-swam.github.io)

## https://mobile-swam.github.io
The [official home page](https://mobile-swam.github.io) for mobile-aware SWAM 
* SWAM: Revisiting Swap & OOMK for Improving User Responsiveness on Mobile Devices

![SWAM, the SWAM mascot](/img/mobile-swam-logo4-small.gif) 


## Introduction
Recently, to mitigate memory shortage problem of applications in mobile devices, swapping mechanism has been introduced, which can preserve the state of the swapped-out processes. 
However, frequent swap operations cause very similar effect to thrashing in paging systems, which worsens application responsiveness. 
Meanwhile, as the size of applications grew, the RAM capacity of mobile devices was increased 16-fold from 512 MB (2010) to 8 GB (2021). This change again created an environment where applications consuming larger memory capacity can be developed and more applications can be run. 
Consequently, modern mobile devices need much larger physical memory capacity as a response to the growing memory competition among the applications. However, even though the physical memory capacity increases, the forced termination of processes due to OOMK operation occurs frequently because more applications use a large memory space indiscriminately, which degrades the application performance significantly.

To solve these problems, this paper proposes the SWAM, a new integrated memory management technique that complements the shortcomings of both the swapping and killing mechanism in mobile devices. 
SWAM consists of (1) On-Demand Swap that dynamically manages the swap space, (2) OOM Cleaner that preserves the process state by removing the shared object pages instead of killing the processes themselves, and (3) EOOM Killer that delays high-initialization-cost applications from being victim processes. Experimental results demonstrate that SWAM significantly reduces the number of applications killed by OOMK (18x lower), and improves application launch time (41% faster) and response time (48% faster), compared to the conventional schemes.


## Getting Started
If you want to access the GitHub addresses listed below, please send an email to leemgs.at.gmail.com.
* [SWAM](https://github.com/mobile-swam/swam) (Member only)
* [Third-party](https://github.com/mobile-swam/third-party) (Member only)

![SWAM Development, make menuconfig](/img/make-menuconfig-swam02.png)


## Demo
This demonstration shows the evaluation result of the Mobile-Aware SWAM. 
Chrome, KakaoTalk, MP3 player, Skype, and the Stock application are all shown in order.
Please press the below "**demo**" image.
The left video depicts the conventional system, whereas the right video depicts the SWAM system. 
During a memory contention situation, SWAM-based user-space applications can be persistent without killing activity, relaunch time, application refreshes, and deferred response time.

[![SWAM Video](/img/demo04.gif)](https://youtu.be/KOInpOcQMEI)

## Related Work
We summarize the main contribution, as well as the strong and weak elements, from the meaningful 50 papers among 113 research articles published between 1999 and 2021. 
For more details, please refer to the below links.
* [PDF](/relatedwork/relatedwork.pdf)
* [PNG](/relatedwork/relatedwork.zip)
* [WiKi](https://github.com/mobile-swam/mobile-swam.github.io/wiki/Related-works)


![50 papers between 1999 and 2021](/img/related-work-50-papers.png)

The above figure illustrates the direction and trend of research articles on securing available memory space between 1999 and 2021. 
By visualizing the statistics as a graph, it is clear that while HDDs are being replaced by faster storage devices (e.g., SSD, eMMC, and eUFS) is developed, research articles on implementing SWAP in mobile devices are progressively increasing, with 2013 as the starting point. 

As can be observed, SWAP is a critical keyword for ensuring consistent and predictable app response time and app launch time in the mobile device environment when memory pressure is achieved. 
While OOM is a strategy for securing free memory without the user's permission, SWAP uses a temporary storage device to secure free memory without killing a process without the user's permission. 
SWAP, on the other hand, has structural issues with I/O thrashing and NAND speed. 
As a result, SWAP studies are critical for resolving these difficulties in mobile devices.

## Discussion Channel
We open a communication channel to discuss on the memory management of mobile devices.
If you want to talk about related studies, techniques, idea, and new challenge, please visit [the SWAM room](https://gather.town/app/AwPmQH37E46wxaN2/SWAM) in gather.town.

![GatherTown](img/gather-town-swam.png)


## How to Contribute
Contributing to open source can be a rewarding way to learn, teach, and build experience in just about any skill you can imagine.
Please refer to [How to contribute](contributing.md).


## Teminology
Terminology is a broad term that refers to a collection of specialized terms or definitions associated with a specific field, such as the SWAM project. We explain terminology  the SWAM project and how it is utilized to represent specific meanings.

* SWAM: Swap + OOMK
* OOM: Out-of-Memory
* OOMK: OOM Killer
* LMK: Low Memory Killer in kernel-space
* LMKD: LMK Daemon in user-space
* Segfault: Segmentaiton Fault
* Anonymous page: A shared page such as stack, heap, shared memory, and shared library
* Zram-out: A procedure to move anonymous pages from a memory to compressed in-memory swap space
* Swap-out: A procedure to move anonymous pages from a memory to a storage swap device
* **Swap-clean**: A procedure to remove swapped-out pages of a SO-page type
* **SO files**: Shared Object files (.so) in a storage (e.g., SSD, eMMC/eUFS)
* **SO pages**: Shared Object pages in a memory (e.g., DRAM)
* **Swam file**: A file-system based swap file to swap-out/swap-in the SO pages only from/to the memory

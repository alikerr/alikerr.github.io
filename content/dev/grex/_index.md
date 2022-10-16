---
weight: 2000
linkTitle: "Grex"
title: "Grex: High Performance Computing Cluster at UManitoba"
description: "All you need to know about Grex and how to use it for running jobs"
titleIcon: "fa-solid fa-user-gear"
categories: ["Information"]
#tags: ["Content management"]
---

## Introduction
---

Grex is a UManitoba High Performance Computing (HPC) system, first put in production in early __2011__ as part of WestGrid consortium. "Grex" is a _Latin_ name for "herd" (or maybe "flock"?). The names of the Grex login nodes ([bison](https://en.wikipedia.org/wiki/Bison "Bison"), tatanka, [aurochs](https://en.wikipedia.org/wiki/Aurochs "Aurochs"), [yak](https://en.wikipedia.org/wiki/Yak "Yak")) also refer to various kinds of bovine animals.

Since being defunded by WestGrid (on April 2, 2018), Grex is now available only to the users affiliated with University of Manitoba and their collaborators. The old WestGrid documentation, hosted on the WestGrid website became irrelevant after the Grex upgrade, so please visit Grex's new [documentation.](/) 

<!--
Thus, if you are an experienced user in the previous "version" of Grex, you might benefit from reading this document: description of Grex [changes.](changes/linux-slurm-update)
-->

If you are a new Grex user, proceed to the [quick start guide](start-guide) and documentation right away.

## Hardware 
---

The orihginal Grex was an SGI Altix machine, with 312 compute nodes (Xeon 5560, 12 CPU cores and 48 GB of RAM per node) and QDR 40 Gb/s InfiniBand network. In 2017, a new Seagate **Storage Building Blocks (SBB)** based Lustre filesystem of **418 TB** of useful space was added to Grex. In 2020 and 2021, the University added several modern Intel CascadeLake CPU nodes, a few GPU nodes, a new NVME storage for home directories, and EDR InfiniBand interconnect. So, the current computing hardware available for general use is as follow:

### Login nodes
---

As of Sep 14, 2022, Grex is using UManitoba network. We have decommissioned the old WG and BCNET network that was used for about 11 years. Now, the DNS names use **hpc.umanitoba.ca** instead of the previous name **westgrid.ca**

On Grex, we have multiple login nodes:

* __Bison__: bison.hpc.umanitoba.ca
* __Tatanka__: tatanka.hpc.umanitoba.ca
* __Yak__: yak.hpc.umanitoba.ca (please note that the architecture for this node is avx512).
* __Aurochs__: https://aurochs.hpc.umanitoba.ca (only used for [OOD](./ood))

### CPU nodes
---

In addition to the original nodes, new skylake nodes have been added to Grex:

| Hardware            | Number of nodes | CPUs/Node | Mem/Node | Network |
| :-------:           | :-------------: | :-------: | :------: | :-----: |
| Intel CPU           | 12              | **40**    | 384 GB   | EDR 100GB/s IB interconnect |
| Intel 6230R         | 42              | **52**    |  96 GB   | EDR 100GB/s IB interconnect |
| Intel Xeon 5560[^1] | 312             | **12**    |  48 GB   | QDR 40GB/s IB interconnect  |
| Contributed[^2]     | 4               | **20**    |  32 GB   | -                           |

<!--
| GPU                 | 2               | **32**    | 192 GB   | FDR 56GB/s IB interconnect  |
-->
[^1]: Original Grex nodes: **slated for decommission in the near furure**
[^2]: Contributed nodes.

### GPU nodes
---

There are also several researcher-contributed nodes (CPU and GPU) to Grex which make it a "community cluster". The researcher-contributed nodes are available for others on opportunistic basis; the owner groups will preempt the others' workloads.

| Hardware            | Number of nodes | GPUs/Node | CPUs/node |Mem/Node |
| :-------:           | :-------------: | :-------: | :-------: |:------: |
| GPU                 | 2               | 4         | 32        | 192 GB  |
| 4 [V100-32 GB][^3]  | 2               | 4         | 32        | 187 GB  |
| 4 [V100-16 GB][^4]  | 3               | 4         | 32        | 187 GB  |
| 16 [V100-32 GB][^5] | 1               | 16        | 48        | 1500 GB |
| AMD [A30][^6]       | 2               | 2         | 18        | 500 GB  |

[^3]: GPU nodes available for all users (general purpose).
[^4]: GPU nodes contributed by Prof. R. Stamps (Department of Physics and Astronomy).
[^5]: NVSwitch server contributed by Prof. L. Livi (Department of Computer Science).
[^6]: GPU nodes contributed by Faculty of Agriculture.

<!--  
> - 12 [ __40 core Intel CPU__ ] nodes, 384 GB RAM, EDR 100GB/s IB interconnect
> - 43 [ __52 core Intel 6230R__ ] nodes, 96 GB RAM, EDR 100GB/s IB interconnect
> - 2 [ __4xV100 NVLINK, 32 core Intel 5218 CPUs__ ] GPU nodes, 192 GB RAM, FDR 56GB/s IB interconnect
> - Original Grex (**slated for decommission in Spring 2022**) Xeon 5560, 12 CPU cores, 48 GB of RAM, QDR 40GB/s IB interconnect
-->

## Storage
---

Grex's compute nodes have access to three filesystems:

<!--
- __/home__ filesystem, NFSv4/RDMA, **15 TB** total usable, 100 GB / user quota.
- __/global/scratch__ filesystem, Lustre, **418 TB** total usable, 4 TB / user quota.
-->

| File system         | Type        | Total space  | Quota per user   |
| :-----------:       | :----:      | :----------: | :--------------: |
| __/home__           | NFSv4/RDMA  | **15 TB**    | 100 GB           |
| __/global/scratch__ | Lustre      | **418 TB**   | 4 TB             |
| __/project__        | Lustre      | **1 PB**     | -                |

<!--
There is a **10 GB/s** Ethernet connection between Grex and [CANARIE](https://www.canarie.ca/network/) network.
-->

## Software
---

Grex is a traditional HPC machine, running CentOS Linux under SLURM resource management system.

## Useful links
---

* [Digital Research Alliance of Canada](https://alliancecan.ca/) (the Alliance), formerly known as Compute Canada.
* the Alliance [documentation](https://docs.alliancecan.ca/wiki/Main_Page)
* Grex Status [page](https://grex-status.netlify.app)
* Grex [documentation](/)
* [Local Resources at UManitoba](localit)

---

{{< alert type="warning" >}}
__WestGrid__ cessed its operations since April 1st, 2022. The former WestGrid institutions are now re-organized into two consortia: __BC DRI group__ and __Prairies DRI group.__
{{< /alert >}}

<!-- {{< treeview display="tree" />}} -->

<!-- Changes and update:
* 
*
*
-->

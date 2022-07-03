---
weight: 1000
linkTitle: "ORCA"
title: "Running ORCA on Grex"
description: "Everything you need to know about running ORCA on Grex."
categories: ["Software", "Scheduler"]
#tags: ["Configuration"]
---

## Introduction
---

[ORCA](http://cec.mpg.de/forum/) is a flexible, efficient and easy-to-use general purpose tool for quantum chemistry with specific emphasis on spectroscopic properties of open-shell  molecules. It features a wide variety of standard quantum chemical methods ranging from semi-empirical methods to DFT to single - and multi-reference correlated ab initio methods. It can also treat environmental and relativistic effects.

## User Responsibilities and Access
---

ORCA is a proprietary software, even if it is free it still requires you to agree to the ORCA license conditions. We have installed ORCA on Grex, but to access the binaries each of the ORCA users has to confirm they have accepted the license terms.

The procedure is as follows: first, register at [ORCA forum](https://orcaforum.kofo.mpg.de/). After the registration is complete,  go to the ORCA download page, and accept the license conditions. Then contact us (via Compute Canada support for example) quoting the ORCA email and stating that you also would like to access ORCA on Grex. The same procedure is applied to get access to [ORCA on the Alliance's clusters](https://docs.alliancecan.ca/wiki/ORCA).

## System specific notes
---

To see the versions installed on Grex and how to load them, please use **module spider orca** and follow the instructions. Both **ORCA-4** and **ORCA-5** are available on Grex.

To load **ORCA-5**, use:

{{< highlight bash >}}
module load gcc/4.8 ompi/4.1.1 orca/5.0.2
{{< /highlight >}}

To load **ORCA-4**, use:

{{< highlight bash >}}
module load gcc/4.8 ompi/3.1.4 orca/4.2.1
{{< /highlight >}}

**Note:**

{{< alert type="warning" >}}
The first released version of **ORCA-5** (5.0.1) is available on Grex. However, ORCA users should use the versions released after (as for now: **5.0.2** since it addresses some bugs of the two first releases 5.0.0 and 5.0.1). We may remove these versions any time.
{{< /alert >}}

## Using ORCA with SLURM
---

In addition to the different keywords required to run a given simulation, users should make sure to set two additional parameters, like Number of CPUs and maxcore in their input files.

### Example on input file
---

### Sample SLURM Script for running ORCA on Grex
---

{{< collapsible title="Script example for running ORCA on Grex" >}}
{{< snippet
    file="scripts/jobs/orca/run-orca-grex.sh"
    caption="run-orca-grex.sh"
    codelang="bash"
/>}}
{{< /collapsible >}}

Assuming the script above is saved as __run-orca-grex.sh__, it can be submitted with:

{{< highlight bash >}}
sbatch run-orca-grex.sh
{{< /highlight >}}

For more information, visit the page [running jobs on Grex](running-jobs)

## Related links
---

* ORCA [forum](http://cec.mpg.de/forum/)
* ORCA on the [Alliance's clusters](https://docs.alliancecan.ca/wiki/ORCA)
* ORCA [input libraries](https://sites.google.com/site/orcainputlibrary/home)
* ORCA [common problems](https://sites.google.com/site/orcainputlibrary/orca-common-problems)
* SCF [convergence-issues](https://sites.google.com/site/orcainputlibrary/scf-convergence-issues)
* ORCA [tutorial](https://www.orcasoftware.de/tutorials_orca/)
* [Running jobs on Grex](running-jobs)
 
---

<!-- {{< treeview display="tree" />}} -->

<!-- Changes and update:
* 
*
*
-->

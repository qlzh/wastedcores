# The Linux Scheduler: a Decade of Wasted Cores

As a central part of resource management, the OS thread scheduler must maintain
the following, simple, invariant: make sure that ready threads are scheduled on
available cores. As simple as it may seem, we found that this invariant is
often broken in Linux. Cores may stay idle for seconds while ready threads are
waiting in runqueues. In our experiments, these performance bugs caused
many-fold performance degradation for synchronization-heavy scientific
applications, 13% higher latency for kernel make, and a 14-23% decrease in
TPC-H throughput for a widely used commercial database. The main contribution
of this work is the discovery and analysis of these bugs and providing the
fixes. Conventional testing techniques and debugging tools are ineffective at
confirming or understanding this kind of bugs, because their symptoms are often
evasive. To drive our investigation, we built new tools that check for
violation of the invariant online and visualize scheduling activity. They are
simple, easily portable across kernel versions and run with a negligible
overhead. We believe that making these tools part of the kernel developers'
tool belt can help keep this type of bugs at bay.

# Important note about the patches

The main point of our paper is to raise awareness about issues in the Linux
scheduler. The provided patches fix the issues encountered with our workloads,
but they are not intended as generic bug fixes. They may have unwanted side
effects and result in performance loss or energy waste on your machine.

# Article

**The Linux Scheduler: a Decade of Wasted Cores**, Jean-Pierre Lozi, Baptiste
Lepers, Justin Funston, Fabien Gaud, Vivien Quéma, and Alexandra Fedorova. *To
appear in* Proceedings of the Eleventh European Conference on Computer Systems
*(EuroSys '16), London, United Kingdom, 2016.*

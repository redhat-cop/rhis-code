# Kernel Live Patching
The Red Hat Enterprise Linux kernel live patching solution can be used to patch a running kernel without rebooting or restarting any processes.

In the future, live patching will essentially create its own patch stream, enabling customers to receive live patches for critical and important CVEs for any supported kernel for a full year after the kernel is updated. This allows reboots to be scheduled at one's convenience. The tradeoff is that live patches will no longer be provided for every errata kernel, but only for selected kernels (approximately quarterly) within the various errata streams.

Red Hat still recommends updating your on-disk kernel as frequently as practical for the following reasons:

1. Live patches do not address every available CVE and bug fix, making it prudent to periodically update the underlying kernel.
2. Customers likely need to reboot periodically for other reasons, presenting a good opportunity to perform a kernel update.

Live kernel patching is already enabled in Red Hat Enterprise Linux (RHEL) versions starting with version 8.1.

You can check by ensuring that kpatch is installed:
``` bash
$ sudo dnf install kpatch
```

You can install live patching like below:
``` bash
$ sudo dnf install "kpatch-patch = $(uname -r)"
```

`kpatch-dnf` enables automatic subscription for any kernel the system currently uses, and also for kernels to-be-installed in the future.

Update to a new cumulative version for the current kernel

``` bash
$ sudo dnf update "kpatch-patch = $(uname -r)"
```

Please checkout [RHEL 9 documentation](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/managing_monitoring_and_updating_the_kernel/applying-patches-with-kernel-live-patching_managing-monitoring-and-updating-the-kernel#components-of-kernel-live-patching_applying-patches-with-kernel-live-patching) for more details.

!!! warning
Currently, Red Hat does not support reverting live patches without rebooting your system. In case of any issues, contact our support team.

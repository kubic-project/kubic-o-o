---
layout: post
title:  "Kubic Project Wound Down"
date:   2022-06-10 12:00:00 +0100
author: Richard Brown
---

## Announcement

As [previously discussed](https://lists.opensuse.org/archives/list/kubic@lists.opensuse.org/thread/23ODJTP4PLGC3HWFQNA2MD4ETFSNW4KV/) on the Kubic Project mailing lists, the Kubic Project is now officially wound down.

Kubic is no longer available for download, and will no longer be maintained.

openSUSE MicroOS, once an offshoot of the Kubic Project, will now take more of a prominent role for those of us contributing who previously needed to split our attention between them.

Users wishing to run kubernetes workloads atop of an openSUSE base are recommended to install [openSUSE MicroOS](https://microos.opensuse.org) and then install [k3s](https://rancher.com/docs/k3s/latest/en/installation/install-options/#options-for-installation-with-script).

Users who prefer the kubernetes RPM packages and containers formerly offered by the Kubic Project may continue to use them, as they will be maintained by a new community maintainer going forward. Please understand this effort is entirely voluntary and on a 'best effort'. It is not expected to be as polished an experience as previously offered under Kubic. Exact details regarding any installation/migration/upgrade steps using those packages will be communicated via the Kubic mailing list and openSUSE wiki.

All of the 'non-kubernetes' official openSUSE containers that were jointly maintained by the MicroOS and Kubic Project teams will continue to be maintained and supported for MicroOS. You can get them, as always, direct from [registry.opensuse.org](https://registry.opensuse.org/cgi-bin/cooverview?srch_term=project%3D%5EopenSUSE%3AContainers%3A+container%3Dopensuse%5C%2F%2F*)

Thanks for everyones contributions over the years, and we look forward to seeing where we can take MicroOS with this more focused approach.

**The Kubic/MicroOS Team**

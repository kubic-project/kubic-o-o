---
layout: post
title:  "kubic-control and own kubernetes control plan on openSUSE Kubic"
date:   2019-08-14 08:54:00 +0200
author: Thorsten Kukuk
---
## Why should I want to use kubeadm?

We have [kubeadm]({{ site.baseurl }}{% post_url 2018-08-20-kubeadm-intro %}) on openSUSE Kubic to manage kubernetes, why do we need yet another management tool?
There is a nice blog giving an answer to this [Automated High Availability in kubeadm v1.15: Batteries Included But Swappable](https://kubernetes.io/blog/2019/06/24/automated-high-availability-in-kubeadm-v1.15-batteries-included-but-swappable/), which explains, beside kubernetes multi master, also the scope of kubeadm very well: "kubeadm is focused on performing the actions necessary to get a minimum viable, secure cluster up and running in a user-friendly way. kubeadm’s scope is limited to the local machine’s filesystem and the Kubernetes API, and it is intended to be a `composable building block for higher-level tools`."

The following tasks are out of scope:
- Infrastructure provisioning
- Third-party networking
- Non-critical add-ons, e.g. monitoring, logging and visualitzation
- Specific cloud provider integrations

kubic-control is such a higher-level toolkit. It configures the Host OS (in the feature, it will even be able to install new baremetal nodes with help of [yomi](https://github.com/openSUSE/yomi)), setups all necessary services, uses kubeadm to deploy kubernetes and installs and configures all necessary add-ons, like pod network and update and reboot services for the OS and the cluster. It will also help you to avoid mistakes like not calling kubeadm with the right arguments if you want to use flannel for the network.

## What is kubic-control?

kubic-control consists of three binaries:
- kubicd, a daemon which communicates via gRPC with clients. It's setting up kubernetes on openSUSE Kubic, including pod network, kured, transactional-update, ...
- kubicctl, a cli interface
- haproxycfg, a cli interface adjust haproxy.cfg for use as loadbalancer for the kubernetes API

The communication is encrypted, the kubicctl command can run on any machine. The user authenticates with his certificate, using RBAC to determine if the user is allowed to call this function. kubiccd will use kubeadm and kubectl to deploy and manage the cluster. So the admin can at everytime modify the cluster with this commands, too, there is no hidden state-database.

## Next Steps

This is just the beginning of our journey to make kubic-control a tool to
manage your whole openSUSE Kubic cluster. Many more things are planned or
under active development:

* Re-configure a haproxy loadbalancer when adding or removing master nodes
* Install new nodes with yomi
* Certificate handling
* Extend support and handling of add-ons, including rolling updates
* Enhance YaST2 to configure the salt-minion already during installation
* Integration of ignition

As with any new software, especially stuff we're changing so quickly, there is a chance of bugs. If you try the steps in this guide and find any, please report them to our [Bugzilla](http://bugzilla.opensuse.org/enter_bug.cgi?product=openSUSE+Tumbleweed&format=guided) under the "Kubic" component.

**Please Note:**  kubic-control on Kubic is under heavy active development. Many new functionality will come which may change current  functionality.

Thanks, and have a lot of fun!

# Microk8s Add-ons

![](https://img.shields.io/badge/amd64-%E2%9C%93-383)
![](https://img.shields.io/badge/arm64-%E2%9C%93-orange)
![](https://img.shields.io/badge/classic-%E2%9C%93-338)
![](https://img.shields.io/badge/strict-%E2%9C%93-85f)

Enable the ByJG microk8s add-ons.

## Installation

Access the microk8s host machine and run:

```shell
git clone https://github.com/byjg/microk8s-addons.git /var/snap/microk8s/common/addons/byjg
```

Check if it is installed:

```text
$ microk8s status

microk8s is running
...
addons:
  ...
  disabled:
    easyhaproxy          # (byjg) EasyHAProxy can detect and configure HAProxy automatically based on ingress labels
    parking              # (byjg) Static webserver to park a domain. Requires EasyHAProxy.
    ....
```

## EasyHAProxy

EasyHAProxy can detect and configure HAProxy automatically based on ingress labels.

Usage:

Install as a Daemonset

```shell
microk8s enable easyhaproxy
```

Install as a NodePort

```shell
microk8s enable easyhaproxy --nodeport
```

## Parking

Static webserver to park a domain. Works better with EasyHAProxy.

Usage:

```shell
microk8s enable parking domain1.com,domain2.com
```

The list of domains is necessary to easyhaproxy auto discover.

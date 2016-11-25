# ironfunctions-murano

Murano application package for [IronFunctions](https://github.com/iron-io/functions/) on OpenStack.

## Quick Start Guide

This guide assumes you have Murano installed. See the [Murano docs](http://murano.readthedocs.io/en/stable-kilo/install/index.html#prepare-a-lab-for-murano)
for setting up a lab environment.

### Supported container management platforms

* Docker standalone host
    * Containers are run on a dedicated VM running Docker.
* Kubernetes
    * Run Docker applications in a clustered environment on Kubernetes pods.

### Getting started (stable/mitaka release)

Note: some details may differ depending on which OpenStack release you are using. For this guide, we are using Mitaka.

1. From the Horizon UI dashboard, select Manage -> Packages

2. Import Package

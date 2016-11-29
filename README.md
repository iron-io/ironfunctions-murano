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

1. Log in to the OpenStack dashboard.
2. Navigate to Applications > Manage > Packages.
3. Click on the Import Package button.
4. Select the Package Source in the Import Package menu.
    * URL (http://storage.apps.openstack.org/apps/)
    * Zip file
        * Run [`build.sh`](build.sh) and upload the correspending zip file.
5. Deploy an application (http://docs.openstack.org/developer/murano/enduser-guide/quickstart/quickstart.html#deploy-an-application)

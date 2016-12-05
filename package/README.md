# ironfunctions-murano

Murano application package for [IronFunctions](https://github.com/iron-io/functions/) on OpenStack.

## Quick Start Guide

This guide assumes you have Murano installed. See the [Murano docs](http://murano.readthedocs.io/en/stable-kilo/install/index.html#prepare-a-lab-for-murano)
for setting up a lab environment.

### Supported container management platforms

* Docker standalone host
    * Containers are run on a dedicated VM running Docker.
* Kubernetes pod
    * Run Docker applications in a clustered environment on Kubernetes pod(s).

### Getting started

Note: some details may differ depending on which OpenStack release you are using. For this guide, we are running Mitaka.

1. Log in to the OpenStack dashboard.

2. Navigate to Applications > Manage > Packages.

3. Click on the Import Package button.

4. Select the Package Source in the Import Package menu.

    * URL (http://storage.apps.openstack.org/apps/)
    * Zip file (make changes locally and upload custom zip)
        * cd to package directory and run `zip -r ironfunctions.zip`

5. Deploy IronFunctions to an environment

    * Add the IronFunctions application component

    ![Alt text](https://monosnap.com/file/okURrogUAKbjYWiEmTr30GkqS91iW0.png)

    * Select 'Container Host', either 'Docker Standalone Host' or 'Kubernetes Pod'. For the simplicity of this example, we will select 'Docker Standalone Host'.

    ![Alt text](https://monosnap.com/file/HQfox1M5Q6dsftgoSO1R8yaAJHpwId.png)

    * Follow the prompts to configure the Docker host and hit 'Create'

    ![Alt text](https://monosnap.com/file/tbA0aJZCLm8ABVb00f73Zi3xQaQdMV.png)

    ![Alt text](https://monosnap.com/file/f21gUMbwrPl4FFaacywZ2yFhx46ufO.png)

    * Select 'Deploy This Environment'

    ![Alt text](https://monosnap.com/file/9b3BQyRYUypXI3l23KWujan5lNBKxg.png)

    * Murano will create a new VM, install Docker, pull down the image for IronFunctions, and start the application.
    The deployment time will depend on your hardware and the selected instance size.

    ![Alt text](https://monosnap.com/file/R7pfGWZXv9jNnCa4ejuHX2L4iSmkEi.png)

    * Once the deployment has completed. Test it out:

        * Note the floating IP assigned to the host

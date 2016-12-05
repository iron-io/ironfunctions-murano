# ironfunctions-murano

Murano application package for [IronFunctions](https://github.com/iron-io/functions/) on OpenStack.

## Quick Start Guide

This guide assumes you have Murano installed. See the
[Murano docs](http://murano.readthedocs.io/en/stable-kilo/install/index.html#prepare-a-lab-for-murano)
for setting up a lab environment.

### Supported container management platforms

* Docker standalone host
    * Containers are run on a dedicated VM running Docker.
* Kubernetes pod
    * Run Docker applications in a clustered environment on Kubernetes pod(s).

### Considerations

* For optimal performance, see the docs on [Docker configuration](https://github.com/iron-io/functions/blob/master/docs/operating/docker.md)
* Note that there is currently no Ubuntu 16.04 image in the OpenStack app-catalog, so for this guide we will be using Ubuntu 14.04, with AUFS,
pre-installed with the Murano-agent and Docker 1.12.

### Getting started

Note: some details may differ depending on which OpenStack release you are using.
For this guide, we are running Mitaka.

1. Log in to the OpenStack dashboard.

2. Navigate to Applications > Manage > Packages.

3. Click on the __Import Package__ button.

4. Select an option for __Package Source__ in the menu.

    * URL (http://storage.apps.openstack.org/apps/)
    * Zip file (make changes locally and upload custom zip)
        * cd to package directory and run `zip -r ironfunctions.zip`

5. Deploy IronFunctions to an OpenStack compute environment

    * Add the IronFunctions application component

    ![Alt text](https://monosnap.com/file/xEiDqs22ydcYXkO2ClBRtsU2Vi6aRt.png)

    * Select __Container Host__, either __Docker Standalone Host__ or __Kubernetes Pod__.
    For the simplicity of this example, we will select __Docker Standalone Host__.

    ![Alt text](https://monosnap.com/file/u7mzH5pzr6x8JbNHmLbD6h0upNPWhn.png)

    * Follow the prompts to configure the Docker host and hit __Create__.

    ![Alt text](https://monosnap.com/file/HQfox1M5Q6dsftgoSO1R8yaAJHpwId.png)

    ![Alt text](https://monosnap.com/file/tbA0aJZCLm8ABVb00f73Zi3xQaQdMV.png)

    * Select __Deploy This Environment__.

    Note: To access the API publically, check your environment and enable inbound TCP
    for the default port, 8080, or whatever port is specified in the form field in the previous step.

    ![Alt text](https://monosnap.com/file/xLFesE2chuhYGxP1dWp5niTgyUoBVI.png)

    * Murano will create a new VM, install Docker, pull down the image for IronFunctions,
    and start the application. The deployment time will depend on your hardware, selected
    instance size, and size of the host OS image.

    ![Alt text](https://monosnap.com/file/2HpGRe8ko2pBc2aE37i5xpbdAUEdm4.png)

    ![Alt text](https://monosnap.com/file/P8FVHd4ah9nQFiY7SZCIxPRJvfMlxn.png)

### Once the deployment has completed, let's test it out!

Note the URL returned in the IronFunctions component deployment status. Our API URL in this this case is `http://172.16.0.193:8080`

```sh
export API_URL=http://172.16.0.193:8080
```

#### Install the IronFunctions CLI tool:

```sh
curl -sSL http://get.iron.io/fn | sh
```


#### Create an application

```sh
fn apps create myapp
```

#### Add a route

```sh
fn routes create myapp /hello iron/hello
```

#### Call the function

```sh
fn call myapp /hello
```

#### Pass data to the function

```sh
echo '{"name":"OpenStack"}' | fn call myapp /hello
```

You should see it say Hello OpenStack! now instead of Hello World!.

See [Writing Functions](https://github.com/iron-io/functions/blob/master/docs/writing.md) for more information.
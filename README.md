# Offline Tools

This repo contains a collection of tools that can be self-hosted for offline use.  These tools have been tested on Docker Desktop for Windows, using Linux containers.

## Setup

For our initial release of offline-tools, we are using `docker-compose` file(s) to run the different tools.  In order to use the `docker-compose` file, you will need to complete the following:
1. [Install Docker](https://docs.docker.com/install/)
2. [Install Docker Compose](https://docs.docker.com/compose/install/)
3. Clone this **wc-offline-tools** repository with `git clone https://github.com/warrior-companions/wc-offline-tools.git`
4. Determine which `docker-compose` file you will use
    - Make note of the file name, as it will be used in the next step
    - Review the file and make updates as needed
5. Start the containers using the selected `docker-compose` file
    - Navigate to the `wc-offline-tools` directory
    - Issue `docker-compose -f docker-compose-<selected_file>.yml up -d`


### Downloading Docker Images

If you have not downloaded any Docker images, you can download them using the [`docker pull`](https://docs.docker.com/engine/reference/commandline/pull/) command.
- Example downloading the [`mpepping/cyberchef`](https://hub.docker.com/r/mpepping/cyberchef/) image:
    ```
    docker pull mpepping/cyberchef
    ```

You can also pull [`tagged images`](https://www.geeksforgeeks.org/docker-using-image-tags/) by including the `tag` after the image name.
- Example downloading the `kiwix/kiwix-serve:3.4.0` image:
    ```
    docker pull kiwix/kiwix-serve:3.4.0
    ```

### Importing Docker Images

If you already have Docker images stored as `.tar` files, you can import them using the [`docker load`](https://docs.docker.com/engine/reference/commandline/load/) command.
- Example loading the `immauss/openvas` image from the `openvas.tar` file:
    ```
    docker load -i D:\path-to\docker-image-files\openvas.tar
    ```
- Docker should respond with: 
    > Loaded image: immauss/openvas:latest


### Updating and Exporting Docker images

If you find you want to export a downloaded image, you can use the [`docker save`](https://docs.docker.com/engine/reference/commandline/save/) command.
- Example saving the `mpepping/cyberchef` image to the `cyberchef.tar` file:
    ```
    docker save -o D:\path-to\docker-image-files\cyberchef.tar mpepping/cyberchef
    ```

You can also save [`tagged images`](https://www.geeksforgeeks.org/docker-using-image-tags/) by including the `tag` after the image name.
- Example saving the `kiwix/kiwix-serve:3.4.0` image to the `kiwix-serve-3.4.0.tar` file:
    ```
    docker save -o D:\path-to\docker-image-files\kiwix-serve-3.4.0.tar kiwix/kiwix-serve:3.4.0
    ```

## Tools

This section needs to be completed.

## Challenge: Fix a broken container

### Common issue ###
** Can not create container because out of space **
- Explanation: 
    * Docker engine is actually run on a tiny VM
    * If it said out of space, it means the VM is out of space

- Solution: `docker system prune` to remove all unused containers, networks, images (both dangling and unreferenced), and optionally, volumes.

- Approach:
    * Run `df -h /` to check the disk usage, if it is still full, you need to remove unused containers by using `docker rm <container_id>` or `docker rm -f <container_id>` to force remove

    * Remove unused images, `docker images` to list all images, `docker rmi <image_id>` to remove image, or remove multiple images by using `docker rmi <image_id> <image_id> <image_id> ...` or force remove by using `docker rmi -f <image_id>`
    :exclamation: You need to stop container before removing image by using `docker rm`

** The container running really slow **
- Solution:
    * `docker stats` to check the usage of CPU, memory, network, disk I/O
    * `docker top <container_name>` to check the process running inside the container
    * `docker inspect <container_name>` to show advanced information on container in Json format, you can using `docker inspect <container_name> | grep <keyword>` to filter the result or `docker inspect <container_name> | less` to show the result in page by page
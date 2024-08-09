## Docker Network ##
- Docker has an entire sub command for working with networks, its called `docker network`
![DockerNetwork](https://github.com/meofiscoding/Docker-Journey/blob/main/asset/DockerNetwork.png)
- List all networks
```bash
docker network ls
```
![List all networks](https://github.com/meofiscoding/Docker-Journey/blob/main/asset/ListAllNetworks.png)
- To know how network is configured, run this command:
```bash
docker network inspect <network-name>
```
![Inspect network](https://github.com/meofiscoding/Docker-Journey/blob/main/asset/InspectNetwork.png)
    - Every network has a Name and an ID
    - We can see it's IP Address through IPAM/Config property
    - In this case the Subnet is: `172.17.0.0/16`
    - This mean that every container hat joining this network will get an IP Address starting with `172.17`
    - The `\16` here indicate how big the network is
    - You can use this formula `(2^16) - 2` to calculate the number of IP Address can fit into this network

- To create a network, run this command:
```bash
docker network create <network-name>
```
- To create container and attach it to a network, run this command:
```bash
docker run -d --name <container-name> --network <network-name> <image-name>
```
- To connect a container to a network, run this command:
```bash
docker network connect <network-name> <container-name>
```
 :bangbang: 
 - Only container in same network can communicate with each other  
 - You have to stop a container and then connect to another container's network and start it again to make it work

 ### Exposing Container Port between Container ###
 - To expose a port between container, run this command:
```bash
    docker run -d --name <container-name> -p <host-port>:<container-port> <image-name>
```

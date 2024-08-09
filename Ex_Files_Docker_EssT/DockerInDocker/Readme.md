## Docker "in" Docker ##
### Step ###
1. Create container with docker.sock file mapping
```bash
    docker run --rm -v /var/run/docker.sock:/var/run/docker.sock --entrypoint bash -i -t my-image
```
- The command above mapping the docker.sock file from the host to the container
- This concept is called `bind mounting`

2. Since this image include `curl`, we need to make sure that we can communicate with Docker Engine
```bash
    curl --unix-socket /var/run/docker.sock http://localhost/containers/json
```
- The command above uisng curl to communicate with the UNIX socket
- Since we're going to be talking to the Docker Engine by HTTP so we have to put http:// here
- Since we're talking through a UNIX socket, we actually don't need a valid host name here, we can put anything we want
-  Finally, we need to provide an endpoint within the Docker engine that we want to interact with. The Docker engine has a lot of [endpoint](https://docs.docker.com/engine/api/latest) that we can interact with. 
- Since we're just testing that we can communicate with the Docker engine, let's try to list containers. The endpoint to do that is `/containers/json`

3. Install Docker client
```bash
    curl -L get.docker.io | bash
```

4. Verify that we're up and running
```bash
    docker ps
```
- After running the command above, we can see `my-image` container is running

5. Check that we can Docker in Docker by creating a new container 
```bash
    docker run --rm my-image
```
Note that almost any application that supports the Docker API will be able to create and manage containers through the Docker engine just like we're doing here. They might just do it a little differently.

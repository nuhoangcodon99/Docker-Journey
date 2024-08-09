## Challenge: Starting NGINX
![Preview](https://github.com/meofiscoding/Docker-Journey/blob/main/Ex_Files_Learning_Docker/Challenge/StartingNGINX/asset/Preview.png)
- [x] Start an instance of NGINX in Docker with the included website
- [x] Name the container `website`
- [x] Website should be accessible at `http://localhost:8080`
- [x] Ensure that container is removed when done
- [x] Map $PWD/websiteto /usr/share/nginx/html if you volume mount

## Solution
``` bash
    docker run -d --name website -v "$PWD/website:/usr/share/nginx/html" -p 8080:80 --rm nginx
```
- Structure: docker run -d --name <container_name> -v <volume> -p <port> --rm <image_name>

&#128073; Use `docker ps -a` to check if any container is running

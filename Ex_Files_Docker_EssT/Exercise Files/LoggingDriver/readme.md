## Logging Driver ##
- Logging driver is a way to send logs to a specific location

- To run this, use this command below:
``` bash
docker run --name test-container my-image
```

- To see the logs, use this command below:
``` bash
docker logs test-container
```

- We can find this log file in the location below:
``` bash
cd /var/lib/docker/containers/<container-id>/<container-id>-json.log
```

- To disable the logging driver, use this command below:
``` bash
docker run --log-driver none --name test-container my-image
```


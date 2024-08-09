FROM ubuntu
RUN apt -y update
RUN apt -y install stress
ENTRYPOINT [ "stress" ]

# Watch out the monitor during run this command:

# Stress run for 5 seconds and 4 CPU workers
# docker run --rm stress --cpu 4 --timeout 5

# Give each container 40% of CPU 
# docker run --rm --cpus 1.6 stress --cpu 4 --timeout 5
# The result is: the approximate of CPU utilization is not exactly 40% but it is around 40%

# Add cpu-quota and cpu-period to limit CPU utilization
# docker run --rm --cpu-quota 160000 --cpu-period 100000 stress --cpu 4 --timeout 15
# The result is: the approximate of CPU utilization is 40% exactly
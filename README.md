# Pi-Hole + Unbound on Docker
- This docker-compose runs the following 2 services
    - Pi-Hole ([pihole/pihole](https://hub.docker.com/r/pihole/pihole)) - Official from Pi-Hole
    - Unbound([artee666/unbound](https://hub.docker.com/r/artee666/unbound)) - Unbound as recursive resolver based on Alpine edge

Only ports from Pi-Hole are exposed to the host. Unbound resolver is accessed by Pi-Hole through new docker_pinet network.

Several environment variables are defined:

| Variable     | Description                                                          | Example       |
| ------------ | -------------------------------------------------------------------- | ------------- |
| PIHOLE_PWD   | Web password for the Pi-Hole                                         | 123456        |
| UNBOUND_IP   | IP for the UnBound from within the PINET_SUBNET                      | 172.20.0.99   |
| PINET_SUBNET | Network mask for the pinet                                           | 172.20.0.0/24 |
| DNS_IP       | IP address of some DNS server (could be another instance of Pi-Hole) | 1.1.1.1       |

These could be either set on the commandline: 

```PIHOLE_PWD=123456 UNBOUND_IP=172.20.0.99 PINET_SUBNET=172.20.0.0/24 DNS_IP=1.1.1.1 docker-compose up -d```

or put into `.env` file as:

```
PIHOLE_PWD=123456
UNBOUND_IP=172.20.0.99
PINET_SUBNET=172.20.0.0/24
DNS_IP=1.1.1.1
```

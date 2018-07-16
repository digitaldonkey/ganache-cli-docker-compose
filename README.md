# Truffle Ganache docker-compose

This docker-compose enables you to use [ganache-cli](https://github.com/trufflesuite/ganache-cli) with a **persistent data**. 


```bash
git clone https://github.com/digitaldonkey/ganache-cli-docker-compose.git
docker-compose up
```

Truffle Ganache client uses the direcrtory `ganache_data` to save its chain data. So any transactions made should be still available after restart. 


Your `truffle.js` config might look like 

```javascript
module.exports = {
  networks: {
    development: {
      host: '192.168.99.100',
      port: 8545,
      network_id: '5777'
    }
  }
}
```

### Is it running? 

```bash
docker-compose ps
docker ps
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS              PORTS                    NAMES
61fefe065a16        trufflesuite/ganache-cli:latest   "node ./build/cli.no…"   36 seconds ago      Up 5 seconds        0.0.0.0:8545->8545/tcp   ganachclidockercompose_node_1

docker ps
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS              PORTS                    NAMES
61fefe065a16        trufflesuite/ganache-cli:latest   "node ./build/cli.no…"   57 seconds ago      Up 26 seconds       0.0.0.0:8545->8545/tcp   ganachclidockercompose_node_1
```


### Can I connect to ethereum ganache?

```bash
ping dockerhost
PING dockerhost (192.168.99.100): 56 data bytes
64 bytes from 192.168.99.100: icmp_seq=0 ttl=64 time=0.314 ms

# Check port 8545
nmap 192.168.99.100 -p 8545
Starting Nmap 7.70 ( https://nmap.org ) at 2018-07-16 17:14 CEST
Nmap scan report for dockerhost (192.168.99.100)
Host is up (0.00049s latency).

PORT     STATE SERVICE
8545/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.04 seconds
```

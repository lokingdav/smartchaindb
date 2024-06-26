<!---
SmartchainDB Repository
SPDX-License-Identifier: (Apache-2.0 AND CC-BY-4.0)
Code is Apache-2.0 and docs are CC-BY-4.0
--->

# SmartchainDB Server

SmartchainDB is the blockchain database. This repository is for _SmartchainDB Server_.

## Preliminary setup

Preliminary setup stage is **necessary** for both Single-Node and Multi-Node configurations! 

Clone the `SmartchainDB` repo

```bash
git clone https://anonymous.4open.science/r/smartchaindb-0811/
```

Install Dependencies:
- Docker
- Docker Compose
- Tendermint
``` bash
chmod +x install_dependencies.sh
./install_dependencies
```
**IMPORTANT**! Make sure you that all dependencies have been properly installed.



## Single Node Setup (Local)! 

This is the guide on how to run the latest version of SmartchainDB Server on a single node.  When you are ready, fire up a terminal and run:


### Configure docker-compose file: 

There are two docker-compose files, one with tendermint `docker-compose-with-tendermint.yml` and one without tendermint component `docker-compose-without-tendermint.yml`. Only **ONE** docker compose file should be run at a time and should have `docker-compose.yml` filename. 

Execute the following steps:

1. Rename `docker-compose-with-tendermint.yml` to `docker-compose.yml`
2. Rename `docker-compose-without-tendermint.yml` to `docker-compose-without-tendermint.yml.bk1`. By appending .bk1, we ensure that only one configuration will be executed.

### Run all the components: SmartchainDB server, Tendermint, MongoDB in docker containers

``` bash
cd smartchaindb
sudo docker-compose up bigchaindb
```

### Accessing Your Node 

If you followed the above instructions, then your SmartchainDB Server should be accessible at `http://0.0.0.0:9984`

#### To destroy the node use command `sudo docker-compose down` in `smartchaindb` directory. 


## Multi Node Setup (cluster)! 

All nodes in the cluster (minimum of 4) must share some information with each other, so they can form a network. Every node need to copy and edit the configuration files. Each node will need to modify the `genesis.json` and `config.toml` files to include the other nodes in the network.

### Generate Node IDs and Public Keys:
- Ensure each node has Tendermint installed and initialized. 
    - Use `tendermint version` to check the proper version was installed. Should be `0.31.5-d2eab536`
    - Use ``` tendermint init``` to generate the public keys and node IDs for each Tendermint node.
-  Get node_id and public_key using commands ```tendermint show_node_id``` and ```tendermint show_validator```.

### Configure Networking:
- Configure the `genesis.json` and `config.toml` files for each Tendermint node to include the other nodes in the network.
    - Follow the example [HERE](https://docs.bigchaindb.com/en/latest/installation/network-setup/network-setup.html)

### Start SmartchainDB Server and MongoDB (on every node)
Run the command:
```bash
sudo docker-compose up bigchaindb -d
```

### Start Tendermint
Run the command:
```bash
tendermint node
```

Validate the cluster setup and ensure nodes are synchronized!

By following these steps, you can set up a robust cluster of SmartchainDB nodes. 
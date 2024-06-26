<!---
SmartchainDB Repository
SPDX-License-Identifier: (Apache-2.0 AND CC-BY-4.0)
Code is Apache-2.0 and docs are CC-BY-4.0
--->

<!---
[![Codecov branch](https://img.shields.io/codecov/c/github/smartchaindb/smartchaindb/master.svg)](https://codecov.io/github/smartchaindb/smartchaindb?branch=master)
[![Latest release](https://img.shields.io/github/release/smartchaindb/smartchaindb/all.svg)](https://github.com/smartchaindb/smartchaindb/releases)
[![Status on PyPI](https://img.shields.io/pypi/status/smartchaindb.svg)](https://pypi.org/project/SmartchainDB/)
[![Travis branch](https://img.shields.io/travis/smartchaindb/smartchaindb/master.svg)](https://travis-ci.com/smartchaindb/smartchaindb)
[![Documentation Status](https://readthedocs.org/projects/smartchaindb-server/badge/?version=latest)](https://docs.smartchaindb.com/projects/server/en/latest/)
[![Join the chat at https://gitter.im/smartchaindb/smartchaindb](https://badges.gitter.im/smartchaindb/smartchaindb.svg)](https://gitter.im/smartchaindb/smartchaindb?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
--->
# SmartchainDB Server

SmartchainDB is the blockchain database. This repository is for _SmartchainDB Server_.


## Run and Test SmartchainDB Server from the `master` Branch

This is the guide on how to run the latest version of SmartchainDB Server.  When you are ready, fire up a terminal and run:

```bash
git clone https://anonymous.4open.science/r/smartchaindb-0811/
cd smartchaindb
```

Install Dependencies:
- Docker
- Docker Compose
- Tendermint
``` bash
chmod +x install_dependencies.sh
./install_dependencies
```
IMPORTANT! Make sure you that all dependecies have been properly isntalled.

Configuration:
- Ensure each node has Tendermint installed and initialized. Use ``` tendermint init``` to initialize.
- Generate the public keys and node IDs for each Tendermint node using commands ```tendermint show_node_id``` and ```tendermint show_validator```.

Networking:
- Configure the `genesis.json` and `config.toml` files for each Tendermint node to include the other nodes in the network.
    - Follow [How to Set Up a BigchainDB Network](https://docs.bigchaindb.com/en/latest/installation/network-setup/network-setup.html) documentation

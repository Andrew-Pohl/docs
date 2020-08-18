---
description: A technical guide on how to run you own Validator node.
---

# How to run a Validator node

### Pre-Requisites
* An "always on" machine.

* An etherum node is required to listen to and relay transactions to the main etherum network. To do this you can either run your own geth or parity node or simply use a node provider such as [**<ins>Infura</ins>**](https://infura.io/) or [**<ins>getblocks</ins>**](https://getblock.io/#access).

### Hardware Requirements
* CPU - 2 cores
* Memory - 3GB+
* Storage - 30GB+ of high speed SSD storage
* Networking - for reliable operation >50mb/s up/down
* OS - Any unix based OS (recommended Ubuntu 18.04)

### Cloud providers
As mentioned in the Pre-Requisistes an always on machine with minimal down time is essential. Because of this we reccomend the use of cloud provides.

* [**<ins>AWS - t3a.medium</ins>**](https://aws.amazon.com/)
* [**<ins>AZURE - Standard B2ms</ins>**](https://azure.microsoft.com/)
* [**<ins>HETZNER - CPX21</ins>**](https://www.hetzner.com/cloud)
* [**<ins>OVH - ESSENTIAL</ins>**](https://www.ovhcloud.com/)

### Network configuration
Ensure that if using a firewall all the following ports are open
```text
| Priority     | Description                        | Port      | Protocol     | Source                      | Destination        | Action     |
|----------    |--------------------------------    |-------    |----------    |-------------------------    |----------------    |--------    |
| 1000         | ssh                                | 22        | TCP          | ip list comma-separated     | Any                | Allow      |
| 1001         | p2p                                | 30303     | TCP          | Any                         | Any                | Allow      |
| 1002         | p2p udp                            | 30303     | UDP          | Any                         | Any                | Allow      |
| 1003         | rpc                                | 8545      | TCP          | Any                         | Any                | Allow      |
```


### Using Quickstart for the first time

To make starting a node for the FuseNetwork as quick as possible, the _quickstart_ script can be used.

1. Download the script.
2. Download one of the example `.env` files located at the [examples folder](https://github.com/fuseio/fuse-network/tree/master/scripts/examples).
3. Modify the `.env` file according to the role/type of node you're running.
4. Start the script.

The script will make sure you have everything that is necessary, create a new account for you \(if needed\) and start the relevant containers \(based on the role/type of node\) with all requested arguments.

The script can be called multiple times without problems, so it checks what is already there and will at least update all service processes.

**Steps**

```text
$ wget -O quickstart.sh https://raw.githubusercontent.com/fuseio/fuse-network/master/scripts/quickstart.sh
$ chmod 777 quickstart.sh
$ wget -O .env https://raw.githubusercontent.com/fuseio/fuse-network/master/scripts/examples/.env.validator.example
```

Modify the followinf fields in the .env file
```text
• FOREIGN_RPC_URL - this should point to your eth end point
• PERMISSION_PREFIX - set this to sudo if needed to run as an elivated user
```
Once the env file has been updated you're ready to run the script

```text
$ sudo ./quickstart.sh
```

The script will prompt you for passwords for you wallet.

### Update using the quickstart

When the fuseapp or bridge gets updated it will require validators to update there nodes to the latest version. This is a simple process:

1. CD to the directory which you previously ran the quickstart script from
2. Over write the old quickstart
3. Run the quickstart

**Steps**

```text
$ sudo wget -O quickstart.sh https://raw.githubusercontent.com/fuseio/fuse-network/master/scripts/quickstart.sh
$ chmod 777 quickstart.sh
$ wget -O .env https://raw.githubusercontent.com/fuseio/fuse-network/master/scripts/examples/.env.validator.example
```